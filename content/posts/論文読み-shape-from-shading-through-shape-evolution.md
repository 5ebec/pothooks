---
title: '[論文読み] Shape from Shading through Shape Evolution'
date: 2019-08-29T14:03:24.334Z
tags:
  - paper
description: '論文読み : Shape from Shading through Shape Evolution'
markup: mmark
---
* Shape from Shading through Shape Evolution
* Dawei Yang, Jia Deng
* CVPR, 2018
* [arXiv](https://arxiv.org/pdf/1712.02961.pdf), [SemanticScholar](https://www.semanticscholar.org/paper/Shape-from-Shading-Through-Shape-Evolution-Yang-Deng/d74a576cc311841c3ff8070262e928c090e41f59)

## What it is about

![](/img/uploads/screenshot-from-2019-08-30-00-56-44.png)

実画像のshape-from-shadingをDNNに学習させる際のデータとして、CGのシンプルなプリミティブを用いて作成されたshapeデータを用いる手法を提案。

既存手法では全て人手で作成されたデータを用いていた。

提案手法ではシンプルなプリミティブを組み合わせて複雑な形状データセットを適宜作成して、DNNの学習を行うことでデータ不足を解決。

## Why it is worthy researching

球や立方体などの単純なプリミティブを組み合わせて複雑な形状の集団を進化させデータを増やすことで、トレーニングの際には実画像は一切使っていないにも関わらず、実画像に対するshape-from-shadingにおいてSoTAを達成。ablation studyにより、提案手法の各モジュールの重要性を確認。MIT-Berkeleyで評価を行った。
(1) we propose an evolutionary algorithm to jointly evolve 3D shapes and train deep networks, which, to the best of our knowledge, is the first time this has been done.
(2) we demonstrate that a network trained this way can achieve state-of-theart performance on a real-world shape-from-shading benchmark, without using any external dataset of 3D shapes.

## Key idea

### 形状表現
![プリミティブの計算グラフ](/img/uploads/screenshot-from-2019-08-30-00-57-03.png)

![グラフ操作による形状変換](/img/uploads/screenshot-from-2019-08-30-00-57-16.png)

![グラフのマージによる形状結合](/img/uploads/screenshot-from-2019-08-30-00-57-23.png)

### 進化アルゴリズム
またバリデーションは実画像で行うため、実画像がもつ形状とかけ離れた形状を持つトレーニングデータは捨てられて行くため、合成画像に対する過学習を防ぐ。

ネットワークはstacked hourglass networkを使用。

## How it is validated (experimental setup and results)

![](/img/uploads/screenshot-from-2019-08-30-00-58-03.png)

## Limitations

## What you thought

プリミティブからデータを構築するごとにネットワークがファインチューニングされていくため、入力に対する最適な結果を見つけるためにはいくつかの重みで検証する必要がある？

## Papers to read before and after the work
