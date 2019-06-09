---
title: GitHub Pages + Netlify DNS でカスタムドメイン
date: 2019-06-09T21:37:05.508Z
tags:
  - netlify
  - domain
  - githubpages
description: 「Netlifyでさくっとカスタムドメイン」の続き　GitHub Pagesにもカスタムドメインを設定する
---
[これ](https://5ebec.netlify.com/posts/netlify%E3%81%A7%E3%81%95%E3%81%8F%E3%81%A3%E3%81%A8%E3%82%AB%E3%82%B9%E3%82%BF%E3%83%A0%E3%83%89%E3%83%A1%E3%82%A4%E3%83%B3/)の続き

前回、カスタムネームサーバーを使用してDNSをNetlifyに移したのでGoogle DomainsのDNSからはカスタムリソースレコードの設定はできない

NetlifyのDomainsタブを開く

![netlify_domains_tab](/img/uploads/netlify_domains_tab.png)

DNS settingsのAdd new recordで  

Record type: ALIAS  
Name: @  
Value: *USERNAME*.github.io  

として、Saveする

![netlify_dns_settings](/img/uploads/netlify_dns_settings.png)

GitHub Pagesのレポジトリのページから Setting > Options > GitHub Pages > Custom domain にカスタムドメインを書いてSave

完成
