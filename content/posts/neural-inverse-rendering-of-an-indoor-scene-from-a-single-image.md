---
title: '[論文読み] Neural Inverse Rendering of an Indoor Scene from a Single Image'
date: 2019-06-11T19:32:18.204Z
tags:
  - paper
description: |
  単一画像からの屋内シーンのニューラルインバースレンダリング
---
* Neural Inverse Rendering of an Indoor Scene from a Single Image
* Soumyadip Sengupta, Jinwei Gu, Kihwan Kim, Guilin Liu, David W. Jacobs, Jan Kautz
* CVPR, 2019
* [arXiv](https://arxiv.org/abs/1901.02453v2), [SemanticScholar](https://www.semanticscholar.org/paper/Neural-Inverse-Rendering-of-an-Indoor-Scene-from-a-Sengupta-Gu/f78e5da29363342ebf04d011c4f756ed021a1a11)

# What it is about
 （なんの論文なのか）

単一画像からの屋内シーンのニューラルインバースレンダリング

### インバースレンダリングとは

![inverse_rendering](/img/uploads/inverserendering.png)

画像からシーンの物理的属性

* 物体形状
* 反射特性
* 光源分布

を推定することを目的としている．

# Why it is worthy researching
（その論文の価値は何、例えば完全に新しい問題を解いているとか、以前の手法の限界を乗り越えているとか）

![figure1](/img/uploads/figure1.png)

屋内シーンの単一画像を

* アルベド(外部からの入射光に対する反射光の比)
* 表面法線ベクトル(物体の幾何学的形状)
* 照明の環境マップ(光源分布)

の3つの属性に分解している．

今までの手法では，主に単一のオブジェクトに対して，またはシーン属性の１つのみを解決するものだった．
本稿では，屋内シーンの単一画像(即ち，シーンは限定されているが単一オブジェクトではない)に対してそれらのシーン属性を同時に解くことができる事ができる．

SUNCG-PBRという名のデータセットを作成している
このデータセットは以前のデータセットを大幅に改善したものである


# Key idea
（最も大事なアイディア）

![figure2](/img/uploads/figure2.png)

ラベル無しの実データから，self-supervised reconstruction loss という損失関数を使用して学習することが本稿のキーアイデア．\
Residual Appearance Renderer (RAR)によって可能としている．

### Self-supervised Learning

自己教師あり学習．\
教師なし学習の一つ．pretext tasks (関係なさそうなタスク) を学習することにより，本当に学習したいタスクで使える特徴表現を学習する．

### RAR (Residual Appearance Renderer)

![figure4](/img/uploads/figure4.png)

#### Residual Appearance

Direct Renderer によってモデル化できない

* inter-reflections (相互反射)
* cast shadows (投影)
* near-field lighting (近距離照明)
* realistic shading (リアルな陰影)

等の複雑な外観効果

これは物理ベースのレイトレーシング(光線追跡法)によるレンダリング方程式でしかシュミレーションできない．\
この方程式は微分不可能であり，学習ベースのフレームワークでは使用できない．

#### DR (Direct Renderer)

学習可能なパラメータを持たない閉形式(初等関数で表される式)

### self-supervised reconstruction loss

I:元画像，A:アルベド，L:環境マップ，N:法線　としている

![eq1](/img/uploads/eq1.png)

![eq2](/img/uploads/eq2.png)

以下の式が self-supervised reconstruction loss

![eq3](/img/uploads/eq3.png)



# How it is validated (experimental setup and results)

（その論文が提案している内容が正しいとする論拠）

表とか

# Limitations

（手法等が動く範囲や仮定．論文に書かれていることだけではなく，自分の研究にとっての制約も考えること）

# What you thought

（読んでて考えたこと、思いついたこと）

# Papers to read before and after the work

この論文を引用している論文

* CVPR2019: [Putting Humans in a Scene: Learning Affordance in 3D Indoor Environments](https://arxiv.org/abs/1903.05690)

参考文献

* ECCV2018: [CGIntrinsics: Better Intrinsic Image Decomposition Through Physically-Based Rendering](https://arxiv.org/abs/1808.08601)
* CVPR2018: [SfSNet: Learning Shape, Reflectance and Illuminance of Faces 'in the Wild'](https://www.semanticscholar.org/paper/SfSNet%3A-Learning-Shape%2C-Reflectance-and-Illuminance-Sengupta-Kanazawa/074619ffc19894c13974321d4b31144acc212f91)
* CVPR2017: [Physically-Based Rendering for Indoor Scene Understanding Using Convolutional Neural Networks](https://www.semanticscholar.org/paper/Physically-Based-Rendering-for-Indoor-Scene-Using-Zhang-Song/5b8d3a05d6f25158fff84bc4ef64fd12d92abc2f)
* CVPR2017: [Semantic Scene Completion from a Single Depth Image](https://www.semanticscholar.org/paper/Semantic-Scene-Completion-from-a-Single-Depth-Image-Song-Yu/8a05db7a75c65ee61c3ca7a6e5401b946166290d)

- - -

**この記事の参考文献**
https://arxiv.org/abs/1901.02453v2\
http://omilab.naist.jp/~mukaigawa/papers/CVIM-145-9.pdf\
https://www.slideshare.net/MasakazuIwamura/revised-on-18-july-2018/77
