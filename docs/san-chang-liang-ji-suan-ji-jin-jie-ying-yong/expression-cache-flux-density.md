# Expression Cache (Flux Density)

## Expression Cache

前面筆者介紹了場量計算機的用法，但是對於大部分的場量，實際上需要事先儲存場量資訊才能做後處理計算。所以這邊想和讀者分享一個實用的方法，就是標題的Expression Cache。<mark style="color:red;">**利用Expression Cache，可以不需要儲存場量也能做到參數的計算，大幅減少硬碟儲存的空間。**</mark>

<mark style="color:purple;">Expression Cache的概念是在每一個時間點計算後，先用場量計算機計算再把結果存到Cache中，場量的全部資訊就不需要儲存。</mark>

## Flux Density using Expression Cache&#x20;

筆者下面以Flux Density的計算來做為範例，此範例是用Transient solver作分析。如圖3-7，我們用內建的範例取半電路作分析。

<figure><img src="../../assets/image (24).png" alt=""><figcaption><p>圖3-7</p></figcaption></figure>

因為想要計算整體鐵芯的磁通分布，所以用前面介紹的Creat List方法，把鐵芯作群組列表。如圖3-8。

<figure><img src="../../assets/image (22).png" alt=""><figcaption><p>圖3-8</p></figcaption></figure>

再把磁通的計算用場量計算機做參數方程式，如圖3-9。

<figure><img src="../../assets/image (9).png" alt=""><figcaption><p>圖3-9</p></figcaption></figure>

下一步就是這邊想要介紹的Expression Cache重點。我們打開從左邊的分析設定，選擇上面的選單的第五項 Expression Cache。接著按Add的按鍵，找到剛剛建立的Calculator Expression B\_Core，選取並加入計算。

接著調整計算時間，請參考讀者自己案例的Time step或是自定義的時間做輸入。如圖3-10。

<figure><img src="../../assets/image (17).png" alt=""><figcaption><p>圖3-10</p></figcaption></figure>

最後在Report的地方新增剛剛所要計算的磁通曲線，而且重要的是，在這模擬中我們沒有儲存場量資訊，大大的減少硬碟讀取和模擬時間。

<figure><img src="../../assets/image (93).png" alt=""><figcaption><p>圖3-11</p></figcaption></figure>

## B Field with positive and negative changes

在計算B場的時候，因為在場處理器中，使用了Mag函數，所以無法觀測到正負號。但如果想要看到隨激勵源變化的磁通，就可以利用此節所教的技巧，<mark style="color:green;">用Expression Cache計算出B場，再由Reort中做計算後處理。</mark>以此節案例為例，此變壓器中有一二次側的電流，我們可以加總一二次側的電流與匝數的乘積：<mark style="background-color:orange;">`(InputCurrent(pri)*4+InputCurrent(sec)*2)/abs(InputCurrent(pri)*4+InputCurrent(sec)*2)`</mark>  取得其方向(正負號)。

如圖3-12所示。

<figure><img src="../../assets/image (94).png" alt=""><figcaption><p>圖3-12</p></figcaption></figure>

由此就可以畫出隨激勵源變化有正負號的B場。



