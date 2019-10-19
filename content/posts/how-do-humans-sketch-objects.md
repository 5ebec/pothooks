---
title: [論文読み] How Do Human Sketch Objects?
date: 2019-10-18T02:17:49+09:00
tags:
  - paper
  - cv
  - differentiablerenderer
cover: /img/uploads/
description: ポイントベースのジオメトリ処理のための微分可能サーフェススプラッティング
markup: "mmark"
draft: true
---

* How Do Humans Sketch Objects? 
* Mathias Eitz, James Hays, Marc Alexa
* SIGGRAPH, 2012
* [PDF](http://cybertron.cg.tu-berlin.de/eitz/pdf/2012_siggraph_classifysketch.pdf)
* video  
[![](https://img.youtube.com/vi/zMzprmtJ6Ck/0.jpg)](https://www.youtube.com/watch?v=zMzprmtJ6Ck)

# What it is about
人間のスケッチのクラシフィケーション  
※ スケッチ = 熟練者が描いたものではない抽象的な絵(ピクトグラフ)

# Why it is worthy researching

 - 人間が物体をどのようにスケッチし、そのようなスケッチを人間とコンピューターがどれだけうまく認識できるかについての正式な研究はこれまでなかった．人間のスケッチに対する最初の大規模な調査．  
 - Amazon Mechanical Turk というクラウドソーシングサービスを利用してデータセットを生成している．
 - 人間の認識精度も Amazon Mechanical Turk を用いて得ている．
 - 学習モデルとしてkNN法，SVMを使用

# Key idea
データセット
![fig2](https://user-images.githubusercontent.com/38322494/67061239-b1b1fc00-f19a-11e9-8c71-0e01dcb36a78.png)
 - 250のカテゴリ:  
 日常生活で見かける，形状だけで認識可能なオブジェクトを網羅している  

補足:  
 LabelMe(アノテーションツール)のデータセットから最も頻繁に使用される1,000個のラベルを抽出し，重複(e.g. 車の側面と正面)や我々の基準に即していないラベルを手動で削除  
 これに Princeton Shape Benchmark と the Caltech 256 のデータセットのカテゴリを追加  
 最後にラボのメンバーにリストにないカテゴリを提案してもらう

 - 20,000個のスケッチ:  
 スケッチされたストロークの空間的パラメータと時間的順序を保存する  
 (ただし，この研究では時間的順序は使用されていない)  
 1カテゴリ毎に80個，合計20,000個のスケッチ


# How it is validated (experimental setup and results)
（その論文が提案している内容が正しいとする論拠）
![fig10](https://user-images.githubusercontent.com/38322494/67063550-22a8e200-f1a2-11e9-8161-1bc80112fc35.png)
56％の精度で未知のスケッチを識別することができている

![fig11](https://user-images.githubusercontent.com/38322494/67061287-d3ab7e80-f19a-11e9-9b80-f15c48fd6528.png)
人間と計算機の認識精度の違いを示すマトリックス  
赤: 人間の方が良い精度, 青: 計算機の方が良い精度  
0は省略している

![fig12](https://user-images.githubusercontent.com/38322494/67061303-db6b2300-f19a-11e9-910c-78fec2eeb13a.png)


# Limitation
人間は73.1%なので人間のほうが圧倒的に精度は高い

# What you thought
2012年の論文なので人間のほうが認識精度が高いという結果になっているが，現在はどのくらい精度が上がっているのか，他の論文を読んでみたい
