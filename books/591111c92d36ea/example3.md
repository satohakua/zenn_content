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
![](/images/591111c92d36ea/example3/2025-05-04-09-21-18.png)

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