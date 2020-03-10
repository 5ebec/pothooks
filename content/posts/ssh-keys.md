---
title: ssh keys
date: 2019-10-08T18:05:23.939Z
tags:
  - ssh
description: 何回やっても覚えられないので自分用に
markup: blackfriday
---
## クライアント側

`~/.ssh/` で

```shell
ssh-keygen -t rsa -b 4096 -N [pass] -f [file_name] -C [comment(file_nameなど)]
```
## サーバー側
`authorized_keys` に `[file_name].pub` をコピペ
