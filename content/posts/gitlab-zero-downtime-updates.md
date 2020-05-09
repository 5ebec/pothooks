---
title: GitLabのアップデート & Zero downtime updates & Slack通知
slug: gitlab-zero-downtime-updates
date: 2020-05-08T12:44:50.822Z
cover: /img/uploads/gitlab-up-to-date.png
tags:
  - gitlab
  - slack
description: |-
  重い腰を上げてGitLabをアップデートした．  
  そのついでにZero downtime updatesに対応させた．
markup: blackfriday
---
バイト先でGitLabをGCP上にホスティングしているのだが，GitLabのアップデートが暫くされていなかったので，やった．

ついでにZero downtime updates(GitLabインスタンスをオフラインにすることなくGitLabを新しいバージョンにアップグレード出来る方法)に対応したシェルスクリプトを書いた．

## 新しいGPG Keyの入手

とりあえずLinuxインスタンスにSSH接続して以下を実行
```bash
$ sudo apt-get update && sudo apt-get install gitlab-ee
```
したがうまくいかなかった．

[2020/04/06にGitLab OmnibusのGPG Keyが更新されていた](https://docs.gitlab.com/omnibus/update/package_signatures.html#fetching-new-keys-after-2020-04-06)ようなので新しい鍵を取得．
```bash
$ curl https://packages.gitlab.com/gpg.key -o /tmp/omnibus_gitlab_gpg.key
$ sudo apt-key add /tmp/omnibus_gitlab_gpg.key
```
再び`$ sudo apt-get install gitlab-ee`を実行したが`No space left on device`と言われたので
```bash
$ sudo apt-get autoremove
```
を実行．

## Zero downtime updates
以下のシェルスクリプトを`gitlab-update.sh`に書いた．

と言っても殆どこれを参考にしています🙇↓  
[【2019年版】GitLab CE/EEのゼロダウンタイムアップグレード](https://qiita.com/ynott/items/7e3d730d12a09e7fdd8b)

```bash:gitlab-update.sh
#!/bin/bash

export LANG=en_US.UTF-8
SLACK_WEBHOOK_API_URL=xxxxx

# check update
sudo apt update

# get versions
GITLAB_VERSIONS=$(apt-cache policy gitlab-ee | grep -1 Installed | sed -r 's/(^  )//' | grep -v "gitlab-ee:")
INSTALLED_VERSION=$(echo $GITLAB_VERSIONS | sed -r 's/Installed: (.*?) Candidate: .*/\1/g')
CANDIDATE_VERSION=$(echo $GITLAB_VERSIONS | sed -r 's/Installed: .* Candidate: (.*?)/\1/g')

# check if you can upgrade
if [ "$INSTALLED_VERSION" = "$CANDIDATE_VERSION" ];
then
   echo "Installed: $INSTALLED_VERSION is equal Candidate: $CANDIDATE_VERSION"
   echo "Exit"
   exit 0;
fi

echo "Installed: $INSTALLED_VERSION"
echo "Candidate: $CANDIDATE_VERSION"
echo "Update version"

sudo apt-get install gitlab-ee
sudo apt-mark unhold gitlab-ee
sudo SKIP_POST_DEPLOYMENT_MIGRATIONS=true sudo gitlab-ctl reconfigure
sudo gitlab-rake db:migrate
sudo gitlab-ctl hup puma
sudo gitlab-ctl restart sidekiq
MSG="{
        \"blocks\": [
                {
                        \"type\": \"section\",
                        \"text\": {
                                \"type\": \"mrkdwn\",
                                \"text\": \"*Update GitLab version* :tada: \"
                        }
                },
                {
                        \"type\": \"section\",
                        \"text\": {
                                \"type\": \"plain_text\",
                                \"text\": \"${INSTALLED_VERSION} → ${CANDIDATE_VERSION}\"
                        }
                }
        ]
}"
curl -X POST -H 'Content-type: application/json' --data "$MSG" $SLACK_WEBHOOK_API_URL
sudo apt-mark hold gitlab-ee
```
更新通知はSlackに飛ぶようにした．

以下のコマンドを実行して完了
```bash
$ chmod +x gitlab-update.sh
```

次回以降のアップデートは
```bash
$ ./gitlab-update.sh
```
で完了する．

