---
title: "Anisotropic Noise"
---
![](/images/591111c92d36ea/example1/2025-02-11_23h01_29.png)

ノードの詳しい説明は以下をご確認ください。
[Adobe 公式サイト](https://helpx.adobe.com/substance-3d-designer/substance-compositing-graphs/nodes-reference-for-substance-compositing-graphs/node-library/texture-generators/noises/anisotropic-noise.html)


## 処理の大枠
![](/images/591111c92d36ea/example1/2025-02-15_08h00_02.png)
*Anisotropic Noise の中身*

以下のように処理がされているようです。
1. Pixel Processor
縞模様作成
1. Directional Blur
模様にブラーをかける
1. Directional Blur
模様にブラーをかける


&nbsp;
&nbsp;
## Pixel Processor　
### 全体像
![](/images/591111c92d36ea/example1/2025-02-16_10h45_16.png)
*［Parameters］*

&nbsp;
&nbsp;
「Output Size」「Per Pixel Function」でノードが組まれています。
![](/images/591111c92d36ea/example1/2025-02-16_10h49_28.png)
*「Output Size」*

![](/images/591111c92d36ea/example1/2025-02-15_08h18_20.png)
*「Per Pixel Function」*

:::message
ノードが多いため、以降で機能ごとに解読します。
:::


&nbsp;
### 「Output Size」の中身
#### 『Sequence』
処理を並行するノードです。"変数の格納"と"出力処理"を別々で行う際に使われることが多いです。


#### ライン数
「X_Amount」「Y_Amount」に負の値が入力されても問題ないように『Absolute』で必ず正の数が返されるようになっています。
また、その値を変数に格納し「Per Pixel Function」で使用しています。
![](/images/591111c92d36ea/example1/2025-02-16_12h28_55.png)


&nbsp;
#### ランダムシード
X と Y で別々のランダムシードを設定しています。
また、その値を変数に格納し「Per Pixel Function」で使用しています。
![](/images/591111c92d36ea/example1/2025-02-16_15h53_09.png)


「Per Pixel Function」で『Random』を使用するとピクセル全てにランダムな値が振り当てられてしまいます。
よって、 ピクセル全体で同じランダム値を使用する場合は「Output Size」で変数に格納するのが良さそうです。
![](/images/591111c92d36ea/example1/2025-02-16_16h40_00.png)


&nbsp;
### Y軸のランダム
「Y Amount」の機能だけに絞ると以下のようになります。
![](/images/591111c92d36ea/example1/2025-02-16_20h43_07.png)

10行の場合、ランダム
入力を "1" で割ったときのあまりは必ず "0~1" になります。


#### ① "Y Amount" の数だけ階調化
［2D View］ では "1" 以上の値はすべて白くなってしまいます。
視覚的にわかりやすくするために "Y Amount" で割ってみると以下のようになります。
![](/images/591111c92d36ea/example1/2025-02-16_17h31_17.png)

#### ランダムな値を生成


&nbsp;
## Directional Blur