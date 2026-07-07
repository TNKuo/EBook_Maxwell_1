---
description: >-
  導體損耗 (Conductor Loss)
  是電磁學與電力傳輸中最廣泛的統稱。如果我們將電流看作一群帶著光芒的小精靈，在金屬通道（不管是變壓器的銅片還是電路板的走線）中努力搬運能量時，因為各種阻力而摩擦生熱、消耗掉的體力，這就是導體損耗。
---

# Conductor Loss

在能量傳輸的過程中，損耗主要以兩種常見的形式出現：

🌳 1. 長途跋涉的疲勞：Wire Loss / Cable Loss (線損 / 電纜損耗)：這是 Conductor Loss 的「專屬道路版」。當電流走在連接設備的長長電線或電纜上時，因為路途遙遠、沿路遇到電阻與電感等阻力而流失的能量，我們稱為 Wire Loss。簡而言之，Wire Loss 就是 Conductor Loss 在實體線路上的具體表現。

🌀 2. 魔法微風的惡作劇：Eddy Current Loss (渦流損耗)：這是一種由交變磁場引起的特殊 Conductor Loss。當交變磁場像魔法微風般吹過金屬導體時，會讓部分電子迷失方向，不再往前走，反而手牽手在導體內部跑起了一圈又一圈的「渦電流」。這些原地打轉的電子互相碰撞，會產生大量的額外熱能。

簡單來說： Conductor Loss 是一個大家族；發生在實體電線上的叫 Wire Loss，而因為磁場變化在導體內部瘋狂打轉發熱的，就是 Eddy Current Loss。

## Wire Loss

在電力傳輸分配系統與電子設備中，電線或電纜的損耗會直接影響系統的效率與可靠性。當電流通過線纜時，部分電能會轉化為熱能和電磁場能量。線損的大小取決於以下關鍵因素：

* 幾何尺寸： 導體的直徑或橫截面積。
* 材料特性： 導體的電阻率。
* 運作條件： 電流大小、電流密度與環境溫度。

💡 改善對策： 採用低電阻率的材料、增加導體橫截面積以降低電流密度。此外，搭配更有效的散熱技術，確保線纜溫度維持在安全範圍，能進一步提升整體系統的效率與壽命。

## 模擬軟體中的線損計算 (以場量計算機為例)

Wire Loss與Eddy Current Loss 除了使用Maxwell中預設的計算值，同樣可以用場量計算機來計算，得到線損後可以利用電流來反算電阻值；也可以直接用Ohmic-Loss來直接求得損耗。<mark style="color:$primary;background-color:red;">**這對需要求得單一導體的損耗特別有用，特別是沒有支援個別導體損耗的求解器。**</mark>

以下示範兩種使用場量計算機的計算設定方法：

方法一：首先是Eddy Current 求解器做的範例介紹，我們利用J場量和導電率來求得線損。這邊假設導體的導電率是4670000 Siemens/m。讀者可以使用場量計算機求解後再和程式所求的線損來做比較，驗證正確性。

<figure><img src="../assets/image (11).png" alt=""><figcaption><p>圖2-13</p></figcaption></figure>

方法二：是更為簡單的使用Ohmic-Loss作法，在此我們用暫態求解器來示範。

只要針對目標導體執行OhmicLoss的體積分，即可精準求得該導體的損耗瓦數。如果模型中包含多個不同的導體（例如多層繞組）需要個別計算，可以善用[開頭介紹的List Function](https://eemans-organization.gitbook.io/field-calculator-of-maxwell/er-chang-liang-ji-suan-ji-fan-li/volume-and-surface-area) 來進行一次性處理，大幅提升計算的效率。

<figure><img src="../assets/image (2).png" alt=""><figcaption><p>圖2-14</p></figcaption></figure>

