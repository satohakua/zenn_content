---
title: "Anisotropic Noise"
---
![](/images/591111c92d36ea/example1/2025-02-11_23h01_29.png)
![](/images/591111c92d36ea/example1/2025-02-15_08h00_02.png)
*Anisotropic Noise の中身*

以下のように処理がされているようです
1. Pixel　Processor
縞模様作成
1. Directional Blur
模様にブラーをかける

## Pixel　Processor　
### 全体像
![](/images/591111c92d36ea/example1/2025-02-16_10h45_16.png)
*Parameters*

&nbsp;
&nbsp;
「Output Size」「Per Pixel Function」でノードが組まれています。
![](/images/591111c92d36ea/example1/2025-02-16_10h49_28.png)
*［Output Size］*

![](/images/591111c92d36ea/example1/2025-02-15_08h18_20.png)
*［Per Pixel Function］*

### 要素ごとに解説


#### Y軸のラインのランダム
![](/images/591111c92d36ea/example1/2025-02-16_10h29_33.png)


「Y Amount」の機能だけに絞ると上記のようになります。




