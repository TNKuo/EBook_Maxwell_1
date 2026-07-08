---
description: 上節介紹的自動生成磁通密度計算，不只可以用AEDT呼叫。如果用戶有在使用PyAEDT做開發，也能把此計算加入當中做使用。
---

# 磁通密度自動計算(加入PyAEDT中使用)

## 磁通密度計算結合PyAEDT

延續第四節的介紹，筆者進階將磁通密度計算結合到DCL的自動化設計分析，使用PyAEDT<mark style="color:orange;">(註4)</mark>做編成。利用前面的技巧，把DC電抗器鐵芯的截面用Field Calculator，寫入PyAEDT中，自動生成模擬檔案與執行計算，最後生成報告檔。

<figure><img src="../../assets/image (46).png" alt=""><figcaption><p>圖4-7</p></figcaption></figure>

磁通密度的計算如圖4-8，使用自動計算的技巧。

<figure><img src="../../assets/image (13).png" alt="" width="563"><figcaption><p>圖4-8</p></figcaption></figure>

## PyAEDT

使用PyAEDT，有許多的優點。除了一鍵自動化模擬與生成報告，使用者亦可以選擇不把AEDT GUI打開，除了能節省前處理模組的License使用，並且縮短模擬時間。因為打開AEDT GUI是非常耗費電腦系統資源的工作，運用背景模式執行模擬，能有效提高模擬效率。

使用PyAEDT模擬的過程，筆者整理成如圖4-9的GIF動畫給讀者參考。在模擬的過程中，不會打開AEDT GUI介面，打開工作管理員可以看到AEDT在背景運算。執行過程中，PyAEDT會自動創建模擬的AEDT檔案，自動擷取模擬結果匯出至Excel中，最後能自動生成報告。

<figure><img src="../../assets/2023-07-09_PyAEDT DCL design.gif" alt=""><figcaption><p>圖4-9</p></figcaption></figure>

PyAEDT執行完成後，設計者能直接獲得生成的報告檔案。

自動生成結果報告，不僅減低人為報告出錯的機率，也能提供固定的報告統一格式，更免去截圖與整理報告的時間。可謂是一本萬利、好處多多。

<figure><img src="../../assets/image (70).png" alt=""><figcaption><p>圖4-10</p></figcaption></figure>

PyAEDT能進一步結合Ansys OptiSLang，做最佳化設計與自動串聯流程應用，讓設計一氣呵成且一鍵生成。經過流程化的設計與簡單的版面規劃與圖面設計優化後，最後筆者這個設計案例的報表如圖4-11所示。

<figure><img src="../../assets/image (77).png" alt=""><figcaption><p>圖4-11</p></figcaption></figure>



<mark style="color:orange;">註4: 欲安裝PyAEDT和Python的主程式，其流程對初階使用者稍微繁瑣且複雜，但Ansys已經在2023年提供免費的程式包，讓使用者輕鬆安裝，詳情請參考</mark>[PyAEDT安裝](https://eeman.gitbook.io/maxwell-tools/pyaedt)<mark style="color:orange;">。</mark>


