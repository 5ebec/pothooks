---
title: macOSで初期状態からのセットアップ
date: 2019-09-26T14:50:50.378Z
tags:
  - macOS
  - setup
description: |-
  新しいMacを買ったときとか，macOSをファクトリーリセットしたい衝動に駆られたときに

  2019/09/26
markup: mmark
---
# バックアップ

#### mackup の cfg

`.mackup.cfg`  

```
[applications_to_sync]
atom
bash
blender
curl
docker
git
goland
heroku
ipython
iterm2
julia
jupyter
mackup
macosx
magnet
npm
pip
prezto
pycharm
skim
spark
spotify
ssh
terminal
tmux
vim
wireshark
xcode
zsh
nvim
brewfile
```

`.mackup/nvim.cfg`

```
[application]
name = nvim

[configuration_files]
.config/nvim
.nvimrc
.nvim
```

`.mackup/brewfile.cfg`

```
[application]
name = Brewfile

[configuration_files]
.Brewfile
Brewfile
```

#### シェル実行

```shell
$ brew bundle dump --global
$ mackup backup
```

# 起動直後

流れに沿ってデスクトップが表示されるところまで行く

# システム環境設定

#### 一般

* スクロールバーのクリック時: クリックされた場所にジャンプ  
* 書類をとじるときに変更内容を保持するかどうかを確認  

#### Dock

* ウィンドウをアプリケーションアイコンにしまう

#### セキュリティとプライバシー

* 一般
  * Apple Watch でこの Mac のロックを解除できるようにする
* ファイアウォール
  * ファイアウォールをオンにする

#### 内蔵 Retina ディスプレイ

* ディスプレイ
  * 解像度: 変更 > スペースを拡大
  * 輝度を自動調整

#### 省エネルギー

* バッテリー
  * ディスプレイをオフにするまでの時間: 5分
* 電源アダプタ
  * 電源アダプタに接続中に Power Nap をオンにする

#### キーボード

* キーボード
  * キーのリピート: 最速
  * リピート入力認識までの時間: 最短
  * 環境光が暗い場合にキーボードの輝度を調整
  * 修飾キー… > Caps Lock キー: Control
* ショートカット
  * Launchpad を表示: Control+Shift+L
  * デスクトップ \[Num] へ切り替え

#### トラックパッド

* クリック: 弱い
* 起動の速さ: 中心から1つ右

#### サウンド

* メニューバーに音量を表示

#### 共有

* コンピュータ名: (変更する)

#### ユーザーとグループ

左下の鍵をクリック > 自分のアイコンを右クリック > 詳細オプション… > ログインシェル: `/bin/zsh`

#### Siri

* メニューバーに Siri を表示

#### 日付と時刻

* 秒を表示
* 日付を表示

#### Time Machine

* バックアップを自動生成
* Time Machine をメニューバーに表示

#### アクセスビリティ

* ディスプレイ
  * 視差効果を減らす



# Homebrew

[Homebrew](https://brew.sh/) をインストールする  

```shell
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

#### Dropbox, mackup をインストール

```shell
$ brew install mackup
$ brew cask install dropbox
```

#### Dropbox

起動してログイン

#### mackup

```shell
$ mackup restore
```

#### Homebrew Package のインストール

```shell
$ brew bundle --global
```

