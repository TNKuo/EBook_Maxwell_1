---
description: 磁通密度是評估鐵芯是否飽和的重要參數。
---

# Flux Density of a Volume

## Flux Density Calculation

通過鐵芯體積的磁通量密度，計算方法請參考圖2-8。

<figure><img src="../assets/image (74).png" alt=""><figcaption><p>圖2-8</p></figcaption></figure>

請特別注意，這邊的案例是用Transient Solver做的計算，在此B向量的數值是實數(ex: \[Bx,By,Bz]=\[1,2,3])。

若模擬者使用的是Eddy Current Solver，向量內的數值會是複數(ex: \[Bx,By,Bz]=\[1+1j,2+2j,3+3j])。場量計算機會無法直接透過Normal來計算面法向量的分量，會需要先將向量內的數值透過複數運算(如圖2-9)，將數據轉換為實數向量，再使用Normal指令。看到這邊，讀者也可以回想上頁的渦流場面磁通量密度的計算，也是做了轉換計算，是相似的道理。

<figure><img src="../assets/image (54).png" alt="" width="563"><figcaption><p>圖2-9</p></figcaption></figure>

