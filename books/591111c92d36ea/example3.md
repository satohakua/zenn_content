---
title: "Cells 4 ※執筆中"
---
![](/images/591111c92d36ea/example3/2025-02-23_23h46_01.png)

ノードの詳しい説明は以下をご確認ください。
[Adobe 公式サイト](https://helpx.adobe.com/substance-3d-designer/substance-compositing-graphs/nodes-reference-for-substance-compositing-graphs/node-library/texture-generators/noises/cells-4.html)

## 解析率
60%

## 処理の大枠
![](/images/591111c92d36ea/example3/2025-03-02_19h57_10.png)
*『Cells 4』 のパラメーター*
![](/images/591111c92d36ea/example3/2025-03-02_16h09_44.png)
*『Cells 4』 の中身*


上下で2通りの処理があり、『Blend』でその切替を行っています。

## ２通りの処理
長方形の場合に補正するか否かです。
そして、パラメータの違いは『Distance』の「Pixel Ratio」のみです。
![](/images/591111c92d36ea/example3/2025-05-03_08h13_53.png)



&nbsp;
## 『Blend』の中身
「Blending Mode」が "Switch" になっています。
"0" に近づくほど Foreground が、"1" に近づくほど Background が見えてきます。（lerp 処理）
![](/images/591111c92d36ea/example3/2025-03-02_19h50_47.png)
*一般的なノードツールの "IF" や "Switch" と同じ*


今回は「Non Square Expansion」の "True" or "False" で "0" or "1" が選択されています。
よって、Foreground と Background が片方ずつしか使用されません。
![](/images/591111c92d36ea/example3/Animation_aa.gif)


&nbsp;
## メイン処理
以下が最小構成です。 
![](/images/591111c92d36ea/example3/2025-05-03_11h17_30.png)

ただ、複雑なパラメーター入力が必要なければ『FX-Map』は1つでも動作します。
わかりやすいため、まずはこの構成で解読します。
![](/images/591111c92d36ea/example3/2025-05-03_11h41_39.png)



### 全体像

このノードでは以下のような「つぶつぶ模様」が生成されています。
『Distance』の


&nbsp;
## FX-Map
このノードでは以下のような「つぶつぶ模様」が生成されています。

![](/images/591111c92d36ea/example3/image-1.png) 
| ノード名 | パラメーター          | 中身                     |
|----|------------------|---------------------|
| FX-Map | ![](/images/591111c92d36ea/example3/2025-05-03_12h11_52.png)  | ![](/images/591111c92d36ea/example3/2025-05-03_11h48_06.png) |
| Iterate | ![](/images/591111c92d36ea/example3/2025-05-03_11h51_01.png)  | ![](/images/591111c92d36ea/example3/2025-05-03_11h55_15.png) |
| Switch  | ![](/images/591111c92d36ea/example3/2025-05-03_11h58_27.png) | ![](/images/591111c92d36ea/example3/2025-05-03_12h08_54.png) |
| Quadrant | ![](/images/591111c92d36ea/example3/2025-05-03_12h11_52.png) | ![](/images/591111c92d36ea/example3/2025-05-03_12h17_41.png) ![](/images/591111c92d36ea/example3/2025-05-03_12h18_39.png)  |


### Iterate

### Switch




## Quadrant
1ピクセルの大きさの正方形を作る
![](/images/591111c92d36ea/example3/2025-05-03_12h11_52.png) 

### Color / Luminosity
色をランダムに設定
![](/images/591111c92d36ea/example3/2025-05-05-13-17-39.png)


### Branch Offset
![](/images/591111c92d36ea/example3/2025-05-05-15-17-22.png)

&nbsp;
『current_position』だけだと以下のようになります。
![](/images/591111c92d36ea/example3/2025-05-05-13-20-23.png)

&nbsp;
#### disorder
ポジションに方向と角度のランダムな値を入力しています。
![](/images/591111c92d36ea/example3/2025-05-05-15-06-15.png)
![](/images/591111c92d36ea/example3/2025-05-05-14-20-19.png)

コメントで『-1 or 1 を返す』とありますが、"1" のみ返ってきます。
![](/images/591111c92d36ea/example3/2025-05-05-14-48-16.png)

よって、その処理を完全に省いても問題なく動作します。
![](/images/591111c92d36ea/example3/2025-05-05-15-04-58.png)

また、以下でコメントの動作を実現できます。
![](/images/591111c92d36ea/example3/2025-05-05-14-52-19.png)


### Pattern
 ![](/images/591111c92d36ea/example3/2025-05-03_12h17_41.png)


正方形の大きさを設定。
解像度の最小値を
