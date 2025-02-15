---
title: "Anisotropic Noise"
---
# Anisotropic Noise
![](/images/591111c92d36ea/example1/2025-02-11_23h01_29.png)
![](/images/591111c92d36ea/example1/2025-02-15_08h00_02.png)
*［Anisotropic Noise 中身］*

以下のように処理がされているようです
1. Pixel　Processor
縞模様作成
1. Directional Blur
模様にブラーをかける

#### Pixel　Processor　
![](/images/591111c92d36ea/example1/2025-02-15_08h18_20.png)



思った以上に複雑そうなのが出てきました。
ノードを整え、「rotate」を省くと以下のようになります。



![](/images/591111c92d36ea/example1/2025-02-16_05h05_18.png)

