---
title: "Anisotropic Noise"
---
![](/images/591111c92d36ea/example1/2025-02-11_23h01_29.png)

ノードの詳しい説明は以下をご確認ください。
[Adobe 公式サイト](https://helpx.adobe.com/substance-3d-designer/substance-compositing-graphs/nodes-reference-for-substance-compositing-graphs/node-library/texture-generators/noises/anisotropic-noise.html)

## 解析率
50%

## 処理の大枠
![](/images/591111c92d36ea/example1/2025-02-15_08h00_02.png)
*『Anisotropic Noise』 の中身*

以下のように処理がされています。
| No. | ノード名                | 説明                     |
|----|------------------|---------------------|
| 1  | Pixel Processor  | 模様作成           |
| 2  | Directional Blur | ブラーをかける |
| 3  | Directional Blur | ブラーをかける |



&nbsp;
## 『Pixel Processor』　
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
"Y Amount" の機能だけに絞ると以下のようになります。
紫のフレームはもともとあったもの、
![](/images/591111c92d36ea/example1/2025-02-16_20h43_07.png)

10行の場合、ランダム
入力を "1" で割ったときのあまりは必ず "0~1" になります。

#### ① ランダムシード
ランダムシードというよりも、ただのランダムオフセットです。

&nbsp;
#### ② "Y Amount" の数だけ階調化
［2D View］ では "1" 以上の値はすべて白くなってしまいます。
視覚的にわかりやすくするために "Y Amount" で割ってみると以下のようになります。
![](/images/591111c92d36ea/example1/2025-02-16_17h31_17.png)


1. 0≦a＞1 のグラデーションに 20 をかける
2. 値が 0≦a＞20 になる
3. 『Floor』で小数点を切り捨て
4. 0~19 の整数だけになる



&nbsp;
#### ③ ランダムな値を生成
結論、細かい周期を限られたピクセル数でとりだして、ランダムを作成しています。


##### 『Cosine』で周期を作成
乗算を行わないとタイリングされた見た目になります。
1. 『Cosine』で周期を作成
2. 『Modulo』で小数点を取り出す（小数点は 0＜a＞1）
![](/images/591111c92d36ea/example1/2025-02-22_08h16_55.png)






##### 周期を細かく
『Cosine』だけだと規則的な見ためになるため、"12345.7" が乗算されています。
ピクセル数よりも圧倒的に細かい周期にすることで、取り出された値は「実質的なランダム」というつくりです。
![](/images/591111c92d36ea/example1/2025-02-22_19h07_08.png)


&nbsp;
### X軸のランダム
Y 軸とほとんど同じ処理です。異なる点は以下　のみです。
- vecotr2 から X が取り出されている
- 階調化の処理で "c_x_amount" が使われている。
![](/images/591111c92d36ea/example1/2025-02-23_07h28_13.png)



&nbsp;
### Y軸とX軸のランダム
緑の枠内が新しい要素です。
![](/images/591111c92d36ea/example1/2025-02-23_16h40_55.png)
![](/images/591111c92d36ea/example1/2025-02-23_16h39_44.png)

##### X 軸にランダムオフセット
Y 軸の階調ごとに X 座標のオフセットをかけています。
![](/images/591111c92d36ea/example1/2025-02-23_16h46_03.gif)

##### 色をランダムにする
各ブロックごとの色をランダム化しています。
『Float 2』の値に特別な意味はないと思います。

![](/images/591111c92d36ea/example1/2025-02-24_11h57_03.png)

これがないと、以下のように "X Amount" 分の色数しかない見た目になります。
![](/images/591111c92d36ea/example1/2025-02-23_16h47_41.png)



&nbsp;
### 「Rotate」
単純に『Swizzle Float2』で "size" と "pos" の x, y を入れ替えているだけです。
![](/images/591111c92d36ea/example1/Animation(2).gif)

![](/images/591111c92d36ea/example1/2025-02-24_12h05_21.png)

&nbsp;
## 2つの『Directional Blur』
### 結論
なぜ2つも使用しているのか分かりませんでした。


### 全体像
『Directional Blur』は2つとも以下のようなプロパティです。
![](/images/591111c92d36ea/example1/2025-02-23_18h15_06.png)


#### 「Intensity」
２つともほとんど同じ処理です。
また、1つ目の『Directional Blur』は未使用のノードも残されていました。
![](/images/591111c92d36ea/example1/2025-02-23_22h39_20.png)

![](/images/591111c92d36ea/example1/2025-02-23_22h40_36.png)

#### 「Angle」
2つとも同じ処理です。
処理としては、単純に［「Rotate」が有効のときに "90°" を返す］というものです。

「Angle」は "0~360°" を "0~1" で表します。
90 ÷ 360 = 0.25 であるため、"0.25" で "90°" を返していることになります。
![](/images/591111c92d36ea/example1/2025-02-23_18h21_54.png =250x)