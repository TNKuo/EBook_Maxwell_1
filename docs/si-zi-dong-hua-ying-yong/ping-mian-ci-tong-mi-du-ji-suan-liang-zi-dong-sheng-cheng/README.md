---
description: 當想要計算的量很多的時候，一個一個的輸入場量計算機非常耗時。這個章節要教使用者如何用自動化的技巧去生成場量計算。
---

# 平面磁通密度計算量自動生成

## 自動化應用

本篇介紹的方法是利用IronPython<mark style="color:orange;">(註 3)</mark>來做自動化應用，讀者也可以利用這樣的技巧到其他的應用當中。

以一個例子來做應用介紹，如圖4-1，如果在一個磁性元件中有四個想要做磁通計算的面，那要如何自動生成磁通密度面的計算呢？下面我們拆分成六個步驟給讀者參考。

為了方便後面程式化，這邊用來做積分的面物件，我們統一取名並給予係數，如B\_Flux\_Density\_A1、B\_Flux\_Density\_A2、...。

<figure><img src="../../assets/image (4).png" alt=""><figcaption><p>圖4-1</p></figcaption></figure>

首先第一步是打開錄製的功能，第二步再輸入想要錄製的檔名，此時 Record Script 按鍵狀態會變成 Stop Recording。

<figure><img src="../../assets/image (26).png" alt=""><figcaption><p>圖4-2</p></figcaption></figure>

第三步，打開場量計算機，請參考第二章節 [Flux Density of a sheet](https://eeman.gitbook.io/fields-calculator-of-maxwell/er-chang-liang-ji-suan-ji-fan-li/flux-density-of-a-sheet) 的步驟。依目前預想要做的一個幾何執行一次。完成後，第四步結束錄製。

<figure><img src="../../assets/image (29).png" alt=""><figcaption><p>圖4-3</p></figcaption></figure>

第五步，把剛剛錄製的檔案從檔案總管中打開，如圖4-4所示。這邊有一個重要的技巧是要把Python檔案中的 <mark style="color:red;">**S**</mark>etActiveProject 改成 <mark style="color:green;">**G**</mark>etActiveProject 以及 <mark style="color:red;">**S**</mark>etActiveDesign 改成 <mark style="color:green;">**G**</mark>etActiveDesign。然後再把其括號中的內容清除。讓執行Script在執行的時候自動抓取目前的Project和Design。

<figure><img src="../../assets/image (47).png" alt=""><figcaption><p>圖4-4</p></figcaption></figure>

第六步，修改Python內容，把檔案的執行內容改成For迴圈形式，針對目前的檔名做迴圈。第七步，再把檔案做存檔。

<figure><img src="../../assets/image (35).png" alt=""><figcaption><p>圖4-5</p></figcaption></figure>

第八步，將第三步做的內容作清除。第九步，選擇並執行剛剛的執行檔。最後可以自動的生成sheet的計算場量。由此自動化，當所要計算的場量數量多的時候，可以有效的節省設定時間。甚至後續類似的專案也可以一直使用。

<figure><img src="../../assets/image (41).png" alt=""><figcaption><p>圖4-6</p></figcaption></figure>

## 程式碼

最後提供此範例的程式碼給讀者參考。

```python
// B_sheet Calculation
# ----------------------------------------------
# Script Recorded by Ansys Electronics Desktop Version 2023.1.0
# 16:20:28  Mar 16, 2023
# ----------------------------------------------
import ScriptEnv
ScriptEnv.Initialize("Ansoft.ElectronicsDesktop")
oDesktop.RestoreWindow()
oProject = oDesktop.GetActiveProject()
oDesign = oProject.GetActiveDesign()
oModule = oDesign.GetModule("FieldsReporter")


for i in range(1,5):
    surf_name = "B_Flux_Density_A" + str(i)
    oModule.EnterQty("B")
    oModule.EnterSurf(surf_name)
    oModule.CalcOp("NormalComponent")
    oModule.CalcOp("Integrate")
    oModule.EnterScalar(1)
    oModule.EnterSurf(surf_name)
    oModule.CalcOp("Integrate")
    oModule.CalcOp("/")
    expr_name = "B_Flux_A" + str(i)
    oModule.AddNamedExpression(expr_name, "Fields")
```

<mark style="color:orange;">註 3：IronPython 是一個在 .NET 框架上實現的 Python 解釋器，它可以直接使用 .NET 平台上的類庫和模塊。IronPython 具有與 Python 相同的語法和功能，但是它的實現方式和執行環境不同，可以讓 Python 程序直接運行在 .NET 框架上。另一種是常用的是CPython，兩者的比較可以參考</mark> [_<mark style="color:green;">**IronPython vs CPython**</mark>_](https://lin-ming-chih.gitbook.io/aedt-scripting-1/dao-lun/jiao-ben-kai-fa-kuang-jia-bi-jiao)<mark style="color:orange;">。</mark>



##

