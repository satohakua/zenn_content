---
title: "Cells 4 ※執筆中"
---
![](/images/591111c92d36ea/example2/2025-02-23_23h46_01.png)

ノードの詳しい説明は以下をご確認ください。
[Adobe 公式サイト](https://helpx.adobe.com/substance-3d-designer/substance-compositing-graphs/nodes-reference-for-substance-compositing-graphs/node-library/texture-generators/noises/cells-4.html)

## 解析率
60%

## 処理の大枠
![](/images/591111c92d36ea/example2/2025-03-02_19h57_10.png)
*『Cells 4』 のパラメーター*
![](/images/591111c92d36ea/example2/2025-03-02_16h09_44.png)
*『Cells 4』 の中身*

以下のように処理がされています。
| No. | ノード名                | 説明                     |
|----|------------------|---------------------|
| 1  | FX-Map  | 模様作成           |
| 1  | FX-Map  | 模様作成           |
| 2  | Distance | aa |
| 3  | Blend | どちらか片方だけ使用する（スイッチ） |


&nbsp;
## ２種類の『Distance』
これらの違いは、「Pixel Ratio」のみです。
![](/images/591111c92d36ea/example2/2025-03-02_16h25_48.png)


&nbsp;
## 『Blend』の中身
![](/images/591111c92d36ea/example2/2025-03-02_19h50_47.png)


「Blending Mode」が "Switch" になっています。
0 に近づくほど赤線が、1 に近づくほど青線が見えてきます。（lerp 処理）

今回は「Non Square Expansion」の "True" or "False" で "0" or "1" が選択されています。
よって、赤線と青線が片方ずつしか使用されません。
![](/images/591111c92d36ea/example2/2025-03-02_19h59_39.png)

&nbsp;
### 「FX-Map」の中身
|  | 上               | 下                     |
|----|------------------|---------------------|
| 全体像 | ![](/images/591111c92d36ea/example2/2025-03-02_20-32-13-400.png)  | 左に同じ  |
| Output Size  | ![](/images/591111c92d36ea/example2/2025-03-02_20-40-48-024.png)   | 左に同じ |
| 2  | Distance | aa |
| 3  | Blend | どちらか片方だけ使用する（スイッチ） |

### 全体像

![](/images/591111c92d36ea/example2/2025-03-02_20h20_33.png)
*［Parameters］*

#### 上
処理を並行するノードです。"変数の格納"と"出力処理"を別々で行う際に使われることが多いです。


#### 上下の違い
［Quadrant > Color / Luminounsity］
![](/images/591111c92d36ea/example1/2025-02-16_12h28_55.png)


&nbsp;
#### ランダムシード
X と Y で別々のランダムシードを設定しています。
また、その値を変数に格納し「Per Pixel Function」で使用しています。
![](/images/591111c92d36ea/example1/2025-02-16_15h53_09.png)




&nbsp;
## ２つの『Distance』
これらの違いは、「Pixel Ratio」のみです。
![](/images/591111c92d36ea/example2/2025-03-02_16h25_48.png)

### 処理内容
![](/images/591111c92d36ea/example2/2025-03-02_21h29_05.png)
上のインプットで


下のインプットで色付け


以下でも同じ結果です。
![](/images/591111c92d36ea/example2/2025-03-02_21h20_43.png)


&nbsp;
## 『Blend』の中身
![](/images/591111c92d36ea/example2/2025-03-02_19h50_47.png)


「Blending Mode」が "Switch" になっています。
0 に近づくほど赤線が、1 に近づくほど青線が見えてきます。（lerp 処理）

今回は「Non Square Expansion」の "True" or "False" で "0" or "1" が選択されています。
よって、赤線と青線が片方ずつしか使用されません。
![](/images/591111c92d36ea/example2/2025-03-02_19h59_39.png)