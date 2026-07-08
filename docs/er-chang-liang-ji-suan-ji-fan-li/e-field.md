---
description: E場（E field）是指電場，它是描述空間中電場強度的物理量。
---

# E Field

## 電場強度

一個電荷在一個電場中運動時，它受到的力是由該點的電場強度所決定的。電場是一個向量場，其方向是指向正電荷運動方向所指向的方向，其大小則取決於電場源的強度、電荷的數量以及它們之間的距離。

E場通常由一個電場源產生，例如一個帶電粒子或一個電荷分布。在空間中的任何一點，E場的強度可以通過測量該點的靜電場強度來確定。在SI單位制中，E場的單位是牛頓/庫仑（N/C），其中1牛頓/庫倫等於1伏/米（V/m）。

E場是電動勢（電壓）的梯度，它描述了單位電量受到的力。在電場中移動的電荷會受到力的作用，這個力的大小取決於電荷的大小和電場強度。E場廣泛應用於電學、電子學、電磁學和許多其他相關領域，如電路理論、無線電通訊、雷達、光學和粒子物理學等。



在Maxwell中，利用DC Conduction Solver進行電場的絕緣分析。如圖2-18，E場的分布可以在軟體中繪圖。

<figure><img src="../../assets/image (32).png" alt="" width="563"><figcaption><p>圖2-18</p></figcaption></figure>

E場的矩形繪製圖，我們先在3D檔案中繪製想要看的E場延伸分布線Polyline1。接著在Report中，選擇Calculator Expressions -> Mag\_E。然後在Geometry選擇Polyline1。我們就可以畫出沿著分布線看到的E場大小值。如圖2-18。

<figure><img src="../../assets/image (33).png" alt=""><figcaption><p>圖2-19</p></figcaption></figure>



延伸電場計算的說明。筆者以兩面金屬中間是FR4的介質層，演示如何用場處理器來計算電場的垂直分量。如圖2-20，筆者使用一個線的物件，將它畫在介質層靠近金屬側的部分(<mark style="color:orange;">註 2</mark>)。

<figure><img src="../../assets/image (79).png" alt=""><figcaption><p>圖2-20</p></figcaption></figure>

電場在線段上的垂直分量計算分法如圖2-21。計算完後，在Report中創造一個新報告，裡面的Geometry選擇計算的線段，並從Calculator Expressions選Etangent就可以畫出電場的垂直分量。

<figure><img src="../../assets/image (52).png" alt=""><figcaption><p>圖2-21</p></figcaption></figure>

<mark style="color:orange;">註 2: 不畫在金屬側的原因是因為金屬是超良好導體，畫線段在金屬側會沒辦法在2D上面作圖。</mark>


