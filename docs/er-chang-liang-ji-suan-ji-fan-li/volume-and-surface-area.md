---
description: 體積和表面積常常是設計所需的資訊，透過場計算機可以算出目前設計的體積或表面積的大小。
---

# Volume & Surface Area

## Volume

單一物件的體積計算方式，在Maxwell中利用計算機的積分功能來執行，請參考圖2-1。有趣的是，如果我們把scalar換成2的時候，體積就會變兩倍。如上面案例，聰明的讀者可以思考其他的衍伸用法。



<figure><img src="../assets/image (21).png" alt=""><figcaption><p>圖2-1</p></figcaption></figure>

## List Function

上面介紹了單一物件的體積計算。但實務上，會需要計算單一材料的體積，這要怎麼在軟體中實現呢？圖2-2就介紹了這方法，我們可以利用List的功能，把想要的材料先做選取，這邊是以鐵芯來做舉例。選擇了個別的鐵芯，再把選取的鐵芯製作成List，最後改名成Core\_Tota&#x6C;_。_

<figure><img src="../assets/image (65).png" alt=""><figcaption><p>圖2-2</p></figcaption></figure>

完成後，就可以在計算機的Geometry裡面看到Core\_Total的選項了，如圖2-3。這樣想要計算材料總體積，是不是方便許多呢？

<figure><img src="../assets/image (55).png" alt=""><figcaption><p>圖2-3</p></figcaption></figure>

## Surface

物體的表面積也可以用類似的作法來實現，利用Face List的技巧，再用場計算機可以得到物體表面積大小。細部作法請參考圖2-4。

<figure><img src="../assets/image (83).png" alt=""><figcaption><p>圖2-4</p></figcaption></figure>

