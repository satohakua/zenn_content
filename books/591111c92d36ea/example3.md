---
title: "Cells 4 "
---
![](/images/591111c92d36ea/example3/2025-02-23_23h46_01.png)

ノードの詳しい説明は以下をご確認ください。
[Adobe 公式サイト](https://helpx.adobe.com/substance-3d-designer/substance-compositing-graphs/nodes-reference-for-substance-compositing-graphs/node-library/texture-generators/noises/cells-4.html)

## 解析率
40%

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
また、「Non Square Expansion」に関する処理も省きます。
![](/images/591111c92d36ea/example3/2025-05-03_11h41_39.png)


&nbsp;
## FX-Map
このノードでは以下のような「つぶつぶ模様」が生成されています。
![](/images/591111c92d36ea/example3/image-1.png) 


### Output Size
「Output Size」自体の処理はしていません。
『FX-Map』内で使用する変数の準備をしています。
![](/images/591111c92d36ea/example3/2025-05-06-09-39-37.png)
*「Output Size」 の中身*

![](/images/591111c92d36ea/example3/2025-05-06-12-35-46.png)
*『Non-Square Output Size』 の中身*


### Iterate
![](/images/591111c92d36ea/example3/2025-05-03_11h51_01.png)  
*『Iterate』 のパラメーター*
![](/images/591111c92d36ea/example3/2025-05-06-11-48-10.png)
*「Iterations」 の中身*

常に奇数回数で実行されるようになっています。
これは、今回の処理が "Scale = 4" のときが "Scale = 5" の端が半分見える状態で拡大しているからです。
| Scale = 3 | Scale = 4      | Scale = 5      |
|----|------------------|---------------------|
| ![](/images/591111c92d36ea/example3/2025-05-06-11-35-25.png) |![](/images/591111c92d36ea/example3/2025-05-06-11-34-41.png) | ![](/images/591111c92d36ea/example3/2025-05-06-11-35-12.png) |



### Switch
![](/images/591111c92d36ea/example3/2025-05-03_11h58_27.png)
*『Switch』 のパラメーター*


## Quadrant
1ピクセルの大きさの正方形を作る
![](/images/591111c92d36ea/example3/2025-05-03_12h11_52.png) 

### Color / Luminosity
色をランダムに設定
![](/images/591111c92d36ea/example3/2025-05-05-13-17-39.png)


### Branch Offset
![](/images/591111c92d36ea/example3/2025-05-05-15-17-22.png)

&nbsp;
『current_position』だけだと以下のように整列します。
ここに『disorder』でランダムなオフセット値を加算します。
![](/images/591111c92d36ea/example3/2025-05-05-13-20-23.png)

&nbsp;
#### disorder
![](/images/591111c92d36ea/example3/2025-05-05-15-06-15.png)
*ノード郡*
&nbsp;
『Cartesian』に "移動量" と "移動方向" を入力し、ランダムなオフセット値を算出しています。
![](/images/591111c92d36ea/example3/2025-05-05-14-20-19.png)

&nbsp;
コメントで『-1 or 1 を返す』とありますが、"1" のみ返ってきます。
よって、その処理を完全に省いても問題なく動作します。
![](/images/591111c92d36ea/example3/2025-05-05-14-48-16.png)

&nbsp;
また、以下でコメントの動作を実現できます。
![](/images/591111c92d36ea/example3/2025-05-05-14-52-19.png)


### Pattern Size
 ![](/images/591111c92d36ea/example3/2025-05-03_12h17_41.png)


正方形の大きさを設定。
1ピクセル程度の小さい正方形にするために［『scale』÷ 解像度］をしていると思われます。



## Distance
入力されたピクセルを円形に拡大しています。
拡大幅を大きくすると『Cells 4』のアウトプットが完成します。
![](/images/591111c92d36ea/example3/Animation_00.gif)

&nbsp;
「Mask Input」が名前の通りマスク情報。
「Source Input」がカラー情報です。
"白~黒" の粒粒の "色情報" と "それらのマスク" が入力されているため、明度が
様々な領域ができています。
![](/images/591111c92d36ea/example3/2025-05-06-12-49-27.png)