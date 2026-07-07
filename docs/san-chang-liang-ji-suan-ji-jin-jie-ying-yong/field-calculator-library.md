---
description: 在第二章節的介紹了場量計算機計算，這邊筆者介紹加速場量計算機使用的方法。除了本節的方法，讀者亦可參考第四章節的自動生成，都能有效提升模擬速度。
---

# Field Calculator Library

## Field Calculator Library使用

本節介紹當想要一次輸入多個面磁場密度計算的時候，如何利用Field Calculator Library的方法。

如圖3-13，我們可以一次創建多個面磁場密度計算，這邊以兩個面來做示範。讀者可以自行延伸這個應用。

<figure><img src="../assets/image (45).png" alt=""><figcaption><p>圖3-13</p></figcaption></figure>

執行的第一步是打開場量計算機，參考第二章節 [Flux Density of a sheet](https://eeman.gitbook.io/fields-calculator-of-maxwell/er-chang-liang-ji-suan-ji-fan-li/flux-density-of-a-sheet) 的步驟。依目前預想要做的一個幾何執行一次。

<figure><img src="../assets/image (63).png" alt=""><figcaption><p>圖3-14</p></figcaption></figure>

第二及第三步，將製作的場量選取，並另存一個附檔名為clc的檔案。

<figure><img src="../assets/image (53).png" alt=""><figcaption><p>圖3-15</p></figcaption></figure>

第四步，把剛剛另存的檔案打開並編輯，把第一次做的場量計算複製。把裡面的命名做修改，將計算量與幾何名稱修改成欲計算的幾何名稱及變數。

<figure><img src="../assets/image (37).png" alt=""><figcaption><p>圖3-16</p></figcaption></figure>

最後由Field calculator中的載入功能，把剛剛編輯的檔案載入，就可以得到第二組的變數。當多組變數的時候，多複製幾個再做修改，就可以節省輸入的場量計算機的時間了。

<figure><img src="../assets/image (30).png" alt=""><figcaption><p>圖3-17</p></figcaption></figure>


