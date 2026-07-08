# 磁通密度自動計算 - 補充說明

細心的讀者可能有注意到，在上章節的第八步，我們做了一次清除的動作，這個動作是因為如果重複創造一樣的名稱的時候，Maxwell會發生執行錯誤(如圖4-7)。但除了手動清除，有其他方法讓程式能自動順利執行嗎？

<figure><img src="../../../assets/image (71).png" alt=""><figcaption><p>圖4-7</p></figcaption></figure>

有的!\~\~

如下面筆者要介紹進階的功能：讓程式自動確認是否有存在相同的Named Expressions，利用這個函數，我們可以跳過上頁第八步的步驟，也不會有執行錯誤產生。

方法是利用DoesNameExpressionExists函數來判斷是否有重複的名稱，當系統判斷有重複名稱時，不執行場量運算，並利用AddWarningMessage函數跳出警告訊息。另外創建新的Named Expressions的時候，也可以用AddWarningMessage函數來做動作說明，讓程式動作更加明白清晰。

優化後的執行的結果可以參考圖4-8。

<figure><img src="../../../assets/image (64).png" alt=""><figcaption><p>圖4-8</p></figcaption></figure>

更新的程式碼也提供給讀者參考。讀者可以比較前後程式碼的差別。

```python
// B_sheet Calculation with AutoCheck
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
    expr_name = "B_Flux_A" + str(i)
    if oModule.DoesNamedExpressionExists(expr_name):
        warning = expr_name +" is existed in Fields Calculator."
        AddWarningMessage(warning)
    else:
        warning = "Create " + expr_name + " in the field calculator."
        AddWarningMessage(warning)
        oModule.EnterQty("B")
        oModule.EnterSurf(surf_name)
        oModule.CalcOp("NormalComponent")
        oModule.CalcOp("Integrate")
        oModule.EnterScalar(1)
        oModule.EnterSurf(surf_name)
        oModule.CalcOp("Integrate")
        oModule.CalcOp("/")   
        oModule.AddNamedExpression(expr_name, "Fields")
```



## _<mark style="color:blue;">**2023/03 updated.**</mark>_


