---
title: 2段組みPDFをスマホで読みやすくする
date: 2019-10-18T07:17:12.803Z
tags:
  - paper
  - pdf
description: k2pdfopt という pdf2pdf の最強ツール
markup: mmark
---
[k2pdfopt](https://www.willus.com/k2pdfopt/)

CLIのオプションは以下を参考に
[List of command-line options](https://www.willus.com/k2pdfopt/help/options.shtml)

スマホ用
```shell
$ ./k2pdfopt -ui- -n -w 8.5in -h 11.0in -om 0.1,0.1,0.1,0.1 -wrap -c -col 2 <input.pdf>
```

タブレット用(右に余白を作り，書き込むスペースを用意)
```shell
.$ /k2pdfopt -ui- -n -w 8.5in -h 11.0in -om 0.1,0.1,4.0,0.1 -wrap -c -col 2 <input.pdf>
```

文字のみ
```shell
$ ./k2pdfopt -ui- -n -w 8.5in -h 11.0in -om 0.1,0.1,0.1,0.1 -to -col 2 <input.pdf>
```
