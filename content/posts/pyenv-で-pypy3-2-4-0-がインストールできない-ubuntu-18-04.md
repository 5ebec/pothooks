---
title: pyenv で PyPy3 (2.4.0) がインストールできない (Ubuntu 18.04)
date: 2019-06-28T23:55:22.716Z
tags:
  - python pyenv ubuntu
description: |
  Ubuntu 18.04 の pyenv で PyPy3 (2.4.0) がインストールできなかったときの解決策
markup: mmark
---
pyenvでPyPy3-2.4.0をインストールしようとしたらこんなエラーがでた
```shell
Downloading pypy3-2.4-linux_x86_64-portable.tar.bz2...
-> https://bitbucket.org/squeaky/portable-pypy/downloads/pypy3-2.4-linux_x86_64-portable.tar.bz2
Installing pypy3-2.4-linux_x86_64-portable...
Installing pip from https://bootstrap.pypa.io/get-pip.py...
error: failed to install pip via get-pip.py

BUILD FAILED (Ubuntu 18.04 using python-build 1.2.12-2-geb68ec94)

Inspect or clean up the working tree at /tmp/python-build.20190629085104.1440
Results logged to /tmp/python-build.20190629085104.1440.log

Last 10 log lines:
/tmp/python-build.20190629085104.1440 ~
/tmp/python-build.20190629085104.1440/pypy3-2.4-linux_x86_64-portable /tmp/python-build.20190629085104.1440 ~
Traceback (most recent call last):
  File "get-pip.py", line 21492, in <module>
    main()
  File "get-pip.py", line 197, in main
    bootstrap(tmpdir=tmpdir)
  File "get-pip.py", line 82, in bootstrap
    import pip._internal
zipimport.ZipImportError: Python 3.4 or later is required
```

