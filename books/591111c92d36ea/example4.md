---
title: "Quantize Grayscale"
---
![](/images/591111c92d36ea/example4/2025-05-06-15-15-01.png)

ノードの詳しい説明は以下をご確認ください。
[Adobe 公式サイト](https://helpx.adobe.com/substance-3d-designer/substance-compositing-graphs/nodes-reference-for-substance-compositing-graphs/node-library/filters/adjustments/quantize-grayscale.html)

## 解析率
40%

## 処理の大枠
![](/images/591111c92d36ea/example4/2025-05-06-15-16-54.png)
*『Quantize Grayscale』 のパラメーター*
![](/images/591111c92d36ea/example4/2025-05-06-15-17-38.png)
*『Quantize Grayscale』 の中身*



## 階調化
以下で『p_steps』分だけ階調化されます。
![](/images/591111c92d36ea/example4/2025-05-06-19-43-08.png)

&nbsp;
『Sample Gray』の値は "0~1" です。
例えばこれを "4倍" し、『Floor』で小数点を切り捨てると以下のようになります。
上が切り捨て後で、下がもともとの数値です。
| 0 | 1      | 2     | 3    | 4   |
|----|------------------|---------------------|---------------------|---------------------|
| 0≦a＞0.25|0.25≦a＞0.5 | 0.5≦a＞0.75 |0.75≦a＞1 | a=1 |

&nbsp;
これだけだと元の値が "1" の箇所だけ不自然になります。
よって、"0" 以上の最低値を加算します。
先程の表で言う "0.25" を加算することで解決しています。

| 階調化だけ | 最低値を加算      |
|----|------------------|
| ![](/images/591111c92d36ea/example4/2025-05-06-20-06-00.png) | ![](/images/591111c92d36ea/example4/2025-05-06-20-05-44.png) |


&nbsp;
## なじませる
![](/images/591111c92d36ea/example4/Animation_00.gif =300x)

&nbsp;
以下の青枠が "なじませる処理" 、その他の部分が先程の "階調化の処理" です。
![](/images/591111c92d36ea/example4/2025-05-06-20-37-55.png)


なじませる処理では以下の画像が作られています。
これを下の処理に
![](/images/591111c92d36ea/example4/2025-05-06-22-44-59.png =300x)

