# UI 組件封裝與導入規劃

規劃草案｜2026-10-26

本次規劃只處理淺色模式。公司色碼、尺寸及 @company/ui 名稱均為示意，正式範圍、人力與工期另行確認。

## 頁次索引

| 頁次 | 主題 |
| --- | --- |
| 1 | UI 組件封裝與導入規劃 |
| 2 | 六個階段的執行順序 |
| 3 | 第一階段：盤點頁面與首波範圍 |
| 4 | 第二階段：建立可重複使用的設計規範 |
| 5 | 設計與實作的迭代方式 |
| 6 | 第三階段：公司設計與既有技術對接 |
| 7 | 第四階段：依共用需求封裝組件 |
| 8 | 第四階段：代表頁驗證與試用 |
| 9 | 第五階段：發布共用套件與 Demo |
| 10 | 第六階段：新案導入與持續維護 |
| 11 | 各階段交付與建議分工 |
| 12 | 里程碑與下一步安排 |
| 13 | 附錄：程式交付內容與對照方式 |
| 14 | 附錄：主管可能關心的問題 |
| 15 | Element Plus 全域樣式變數 |
| 16 | 公司樣式設定與技術對照 |
| 17 | Backtop 樣式變數完整地圖 |
| 18 | 直接使用 Element Plus |
| 19 | AppButton 的封裝實作 |
| 20 | 頁面改用 AppButton |
| 21 | npm 套件的目錄結構 |
| 22 | 新專案安裝與使用套件 |

## 第 1 頁：UI 組件封裝與導入規劃

設計規範、共用程式與專案應用的執行順序

### 講稿

本次報告說明 UI 組件封裝要依序完成哪些工作，以及各階段會產出什麼。UI 組件可理解為畫面上重複出現的按鈕、輸入欄位、表格等零件。我們會先整理共同設計，再把設計落實成可重複使用的程式，透過實際頁面試用後，才發布供其他專案安裝。此份為建議規劃，尚未代表已完成進度、核定時程或效益承諾。

## 第 2 頁：六個階段的執行順序

每一階段都有可檢視的產出，設計與實作持續互相校正

- 01：範圍盤點：代表頁、優先組件

- 02：設計規範：Figma、樣式與狀態

- 03：技術對接：設計與程式對照

- 04：封裝與試用：共用組件、驗證頁

- 05：套件發布：npm、Demo 與文件

- 06：導入與維護：新案套用、版本管理

> 首波先完成一組可實際使用的頁面與組件，再擴充涵蓋範圍

### 講稿

整體依序分成六個階段。首先確認我們要解決哪些重複畫面，其次確立設計規範，再研究現有技術如何承接設計。接著封裝與試用，確認足以共用後才正式發布套件，最後安排新專案導入與後續維護。階段之間有依賴，但不是要等全部設計完才寫程式。代表頁、設計與實作可以小批次往返，讓問題早點浮現。

## 第 3 頁：第一階段：盤點頁面與首波範圍

以實際需求決定要共用的內容

### 要做的工作

- **盤點常用頁面**：例如查詢清單、新增／編輯表單、資料明細

- **找出重複元素**：按鈕、欄位、提示、表格、分頁與頁面配置

- **安排首波優先順序**：依使用頻率、差異程度及導入需求選擇

### 交付與完成條件

- **交付物**：代表頁清單、優先組件清單、適用範圍

- **完成條件**：BA／PM、設計與前端對首波範圍有共同認知

- **範圍界線**：先支援 Vue／Nuxt 新案，舊 MVC 另評估整合

> 建議先選「查詢清單＋編輯表單」作為第一組試點，實際頁面待確認

### 講稿

這一步先確認要做哪些共用內容。建議選擇能同時涵蓋表格、查詢條件、輸入欄位和操作按鈕的代表頁，避免只完成漂亮的單一按鈕，卻沒有驗證整頁如何組合。首波頁面只是建議，應由 BA／PM 提供真實情境，設計與前端共同盤點。這裡先界定 Vue／Nuxt 的使用範圍，既有 MVC 是否嵌入 Vue、另做樣式實作或維持原狀，必須依專案評估。

## 第 4 頁：第二階段：建立可重複使用的設計規範

在 Figma 同時整理頁面、組件與全域樣式設定

### 設計內容

- **頁面與配置**：常用頁面、欄位排列、區塊間距、不同螢幕尺寸

- **組件規格**：類型、大小、屬性及各種互動狀態

- **全域設定**：顏色、字級、行高、間距、圓角與陰影

### 系統化管理

- **Figma 共用資產**：使用組件、變體、變數與文字樣式管理

- **可延伸的例頁**：提供 BA／PM 可組合參考的範例與使用原則

- **交付與完成條件**：首波頁面與狀態有規格，設計可重複套用並供實作

> 變數如同共用設定：調整一次，引用該設定的設計即可同步調整

### 講稿

Figma 的工作不只畫常用頁面，也要從頁面抽出可重複使用的組件，以及控制整體外觀的設定。組件需要說清楚大小、類型與狀態，像是輸入欄位錯誤時怎麼呈現、按鈕送出中是否停用。文字排版可搭配文字樣式管理，不需要把所有設定硬塞進變數。例頁也能作為 AI 輔助產稿的參考，但仍需依規格檢查。Figma 變數與程式設定的對照和同步流程，需要另外建立。
來源：https://help.figma.com/hc/en-us/articles/15339657135383-Guide-to-variables-in-Figma

## 第 5 頁：設計與實作的迭代方式

以小批次頁面確認規則，每一輪都同步更新設計與程式

- 代表頁：用真實情境提出畫面需求

- 設計規範：抽出共同組件與樣式設定

- 程式試作：確認現有技術可以承接

- 共同校對：BA／PM、設計與前端確認差異

> 校對發現缺口時，回到頁面與規格修正，再進行下一輪試作

### 講稿

執行上採用反覆迭代的方式。先畫代表頁，抽出共同規則，再以程式試作，最後共同校對。校對時可能發現規格漏了錯誤狀態，也可能發現現有組件無法直接支援某種互動，這時就回到頁面與規格修正。每一輪確認後保留對應版本，才能知道哪些規格已經可以實作。用迭代描述這個過程比較容易理解，也能避免主管誤以為整套設計必須一次定案。

## 第 6 頁：第三階段：公司設計與既有技術對接

Nuxt、Element Plus、Tailwind 分別負責不同工作

- 公司共用層：公司樣式設定、共用組件與頁面範例

- Element Plus：提供按鈕、欄位、表格等基礎組件

- Tailwind：協助間距、配置與不同螢幕尺寸的排版

- Nuxt／Vue：承載頁面、路由與組件運作

- 公司設定與技術變數的對照表

- 全域及各組件的樣式變數盤點

- 相容性與樣式衝突的驗證結果

> 頁面配置與全域樣式分開管理，避免以單一設定檔承擔所有責任

### 講稿

可以把 Nuxt／Vue 理解為應用程式的基礎架構，Element Plus 是可利用的現成組件，Tailwind 協助排版，公司共用層則決定這些零件要呈現的外觀與使用方式。圖中是責任分層，不是程式依賴鏈。前端先盤點 Element Plus 的全域及各組件 CSS／SCSS 變數，把公司設計對應進去，再確認 Tailwind 的 reset 與樣式載入順序。若採用 Tailwind v4，其處理流程與 Element Plus 的 Sass 主題編譯應分開規劃。完成條件是代表頁中的設定與組件樣式能一起正常運作。
來源：https://element-plus.org/en-US/guide/theming
來源：https://tailwindcss.com/docs/preflight
來源：https://tailwindcss.com/docs/compatibility

## 第 7 頁：第四階段：依共用需求封裝組件

在 Element Plus 基礎上落實公司規格

### 先調整樣式設定

- **可用設定完成的差異**：顏色、字級、圓角、尺寸與部分狀態樣式

- **建立對照關係**：公司樣式名稱對應 Element Plus 等技術設定

- **留下例外紀錄**：設定無法涵蓋的部分，再評估局部樣式調整

### 再封裝需要共用的行為

- **共用規格**：統一預設值、欄位標籤、提示與操作介面

- **保留擴充方式**：定義可設定屬性、事件與內容插槽

- **控制封裝範圍**：由專案處理業務 API、權限判斷與特定流程

> 交付物：首波共用組件、使用介面說明與對應範例

### 講稿

封裝可理解為把現成零件整理成公司容易使用的版本。有些差異只需要改主題變數，不必額外包一層。有穩定的共用行為時，再建立公司組件，例如統一欄位標籤、提示與預設值。必要時才調整局部樣式，並記錄原因。保留屬性、事件與插槽等合理擴充方式，避免組件只能支援單一頁面。業務 API、權限與特定審核流程仍由專案負責，讓 UI 組件維持可重用性。
來源：https://element-plus.org/en-US/guide/theming

## 第 8 頁：第四階段：代表頁驗證與試用

初期可先在試點專案中驗證，確認穩定後再集中發布

- 設計一致：尺寸、間距、顏色與規格相符

- 互動完整：錯誤、停用、載入中等狀態正常

- 操作可用：鍵盤、焦點、標籤及螢幕尺寸檢核

- 可重複使用：跨頁套用，無須複製修改組件原始碼

> 完成條件：代表頁驗收通過，並確認哪些內容足以成為共用規格

### 講稿

原先提到完成度不足時先留在各專案內，方向合理，建議再指定一個試點與來源，避免每個專案各自修改成不同版本。初期保留清楚的模組邊界與變更紀錄，待實際驗證後再抽出。驗證涵蓋設計、互動、操作與跨頁重用，對容易反覆出錯的行為建立必要的自動化檢查。完成條件不應只有畫面能顯示，也要能在第二個情境使用，並清楚區分共用規格與專案例外。

## 第 9 頁：第五階段：發布共用套件與 Demo

npm 套件是讓專案安裝指定版本的交付方式

### 整理並發布套件

- **輸出共用內容**：樣式設定、主題 CSS、共用組件與型別

- **訂定相容範圍**：Vue、Element Plus 與相關工具的版本要求

- **建立發布方式**：公司核准的套件來源、發布權限與版本紀錄

### 以 Demo 證明可以導入

- **獨立安裝**：Demo 從套件來源安裝，驗證公開使用介面

- **提供可參考頁面**：展示查詢、表單及各組件狀態

- **提供導入文件**：安裝步驟、範例、限制與升級方式

> 完成條件：獨立 Demo 可安裝指定版本並建置成功，畫面與互動驗收通過

### 講稿

npm 可以理解為前端的套件交付機制，概念上類似 .NET 透過 NuGet 安裝共用函式庫。實際可使用公司核准的內部 registry 或私有套件來源，不代表必須公開發布。Demo 從正式交付的套件安裝，而不是直接引用試點專案的原始碼，才能證明其他專案可依文件使用。發布前還需確認依賴版本、CSS 如何載入、字型及圖示來源，以及發生問題如何退回已知版本。

## 第 10 頁：第六階段：新案導入與持續維護

共用資產透過專案使用逐步擴充

### 專案導入

- **新案套用**：依文件安裝、引用主題並組合頁面

- **記錄落差**：收集缺少的狀態、組件與專案例外

- **觀察實際成效**：記錄導入工時、重複修改及 UI 缺失

### 維護與升級

- **指定維護窗口**：有人負責規格收斂、問題處理與發布

- **同步設計與程式**：每次變更更新對照表、範例與版本紀錄

- **專案自行安排升級**：先測試再升版，問題時可退回指定版本

> 共用套件發布新版後，各專案依測試結果安排導入，避免未驗證的同步變更

### 講稿

共用套件要在有人使用後持續維護。專案固定相依版本，套件更新時先查看變更內容並驗證，再安排升級，不能假設中央修改後所有系統都應立即跟進。針對新增需求，由維護窗口判斷是否具共通性。效益可以觀察重複頁面的開發與修改時間、UI 驗收缺失、實際採用範圍及升級成本。先取得試點資料，再訂目標，避免沒有基準就承諾節省比例。

## 第 11 頁：各階段交付與建議分工

主責協調各方完成交付，實際人員與投入量另行確認

| 階段 | 主要交付物 | 建議主責／協作 |
| --- | --- | --- |
| 01 範圍盤點 | 代表頁與優先組件清單 | BA／PM、設計、前端共同確認 |
| 02 設計規範 | Figma 規範、狀態與例頁 | 設計主責，BA／PM 與前端校對 |
| 03 技術對接 | 變數對照、技術試作與限制 | 前端主責，設計協作 |
| 04 封裝與試用 | 共用組件、代表頁驗證結果 | 前端主責，設計與試點團隊驗收 |
| 05 套件發布 | npm 版本、Demo 與導入文件 | 前端主責，平台／資安依需要協作 |
| 06 導入與維護 | 導入紀錄、版本與問題管理 | 專案團隊導入，共用資產窗口維護 |

> 每次交付均保留版本與驗收紀錄，讓後續專案知道可以採用哪些內容

### 講稿

這張表用來說明設計與程式不是由單一角色獨立完成。BA／PM 提供真實情境與使用需求，設計負責外觀與互動規格，前端負責技術對接與封裝，試點團隊協助確認是否真的可用。發布所需的套件來源與權限，可由平台或相關窗口協作。這是建議的角色分工，沒有預設現有組織配置，也沒有指定尚未確認的人員。

## 第 12 頁：里程碑與下一步安排

先確認首波範圍與驗收方式，再依試作結果估算工期

- M1：首波設計可實作：代表頁、組件與狀態規格完成校對

- M2：共用組件可使用：代表頁驗收通過，跨頁重用成立

- M3：套件可交付：Demo 獨立安裝、建置與導入文件完成

- M4：實際專案可採用：完成試點導入，確認維護與升級流程

> 下一步確認：試點頁面與專案、首波組件範圍、各階段窗口及驗收人員

### 講稿

建議先用四個可檢視的里程碑管理工作，而不是現在就給出缺少依據的完成日期。第一個里程碑確認設計可實作，第二個確認組件可用，第三個確認可作為套件交付，第四個確認實際專案可採用。若首波範圍太大，就縮小批次，而不是跳過試用與驗收。人力、組件數量、現有資產及試點專案確認後，再依試作結果估算時程。這份簡報不將建議規劃視為已核定計畫。

## 第 13 頁：附錄：程式交付內容與對照方式

供技術追問時參考，名稱為示意，實際結構依試作確認

| 交付項目 | 內容與使用方式 |
| --- | --- |
| 公司樣式設定 | 以具語意的名稱管理色彩、字級與間距，例如「主要操作色」 |
| 技術對照表 | Figma 名稱、公司設定、Element Plus 變數與適用組件互相對照 |
| 主題與基礎 CSS | 輸出可載入的樣式，記錄層級、載入順序與例外規則 |
| 共用組件與型別 | 提供明確的屬性、事件、內容插槽及使用限制 |
| Nuxt 整合入口 | 依需要提供安裝方式或模組，與可重用的 Vue 組件分開 |
| Demo 與文件 | 用發布後的套件組合代表頁，提供安裝、驗證及升級說明 |

> Tailwind 樣式交付方式須明訂：預先輸出 CSS，或由使用專案明確設定掃描來源

### 講稿

公司層的設定以語意命名，例如主要操作色，而不是只綁定某一個工具的變數名稱。對照表也記錄來源版本、維護人及驗證頁。Element Plus 提供 CSS 與 SCSS 主題變數，但版型寬度與頁面布局仍要自行規劃。若使用 Tailwind，不能假設消費專案會自動掃描 node_modules 中的 class，可以預先輸出必要 CSS，或文件化來源掃描設定，並驗證動態 class 的處理。Nuxt 專屬依賴應放在整合層，降低 Vue 組件的耦合。
來源：https://element-plus.org/en-US/guide/theming
來源：https://tailwindcss.com/docs/detecting-classes-in-source-files
來源：https://tailwindcss.com/docs/compatibility

## 第 14 頁：附錄：主管可能關心的問題

適用範圍、建置成本與效益的說明

**已有 Element Plus，為何還要封裝？**

它提供基礎功能，我們補上公司設計、統一預設值與可重複使用的規格。

**既有 .NET MVC 可以直接使用嗎？**

Vue 組件需評估前端整合方式。設計規範可共用，程式導入要逐案確認。

**套件更新會影響所有專案嗎？**

各專案固定使用版本，測試通過後再安排升級，並保留回退方式。

**何時可以看到效益？**

代表頁階段即可檢視一致性與重用情形，節省工時需由試點資料比較。

**AI 能直接依設計產出正式頁面嗎？**

規範與範例可協助產稿，正式交付仍需檢查組件使用、互動與設計一致性。

### 講稿

補充說明時可依長官關心的問題選用，不需要逐題朗讀。封裝有持續維護成本，包含設計與程式同步、相依工具升級、缺陷修正及導入支援。第一版建議優先支援常用頁面，效益應用實際導入資料判斷。AI 可以協助產稿與重複工作，但不保證設計稿可自動轉成符合公司規格的正式頁面。既有 MVC 的相容性屬於專案整合問題，不能以共用設計規範直接推論其程式可以直接安裝。

## 第 15 頁：Element Plus 全域樣式變數

按用途分類，先盤點常用設定，其餘變數依需求擴充

| 分類 | 實際變數舉例 | 影響範圍 |
| --- | --- | --- |
| 品牌與狀態色 | --el-color-primary；--el-color-success、--el-color-danger、… | 主要操作、成功與警示 |
| 文字色 | --el-text-color-primary；--el-text-color-regular、… | 標題、一般文字 |
| 文字排版 | --el-font-size-base；--el-font-family、… | 預設字級、字型 |
| 邊框與圓角 | --el-border-color；--el-border-radius-base、… | 分隔線、控制項圓角 |
| 背景與陰影 | --el-bg-color-page；--el-box-shadow-light、… | 頁面底色、浮層陰影 |

> 這些是可共用的外觀設定，頁面配置仍需另外規劃

### 講稿

CSS 變數可理解為樣式用的設定名稱。例如 --el-color-primary 控制主要色，--el-font-size-base 控制預設字級。實際影響哪些部位，要看各組件有沒有引用該變數。全域設定可讓多個組件採用一致的外觀，但不能取代頁面配置設計，也不能保證所有組件的每個細節都受同一個變數控制。這裡列幾個大分類，其餘以省略號表示。
來源與範圍：Element Plus 2.11.5 原始碼及官方主題文件。這是報告用示例，不代表公司已核定規範或已使用此版本。公司色碼、尺寸與 @company/ui 套件名稱均為示意。
https://github.com/element-plus/element-plus/blob/2.11.5/packages/theme-chalk/src/common/var.scss
https://github.com/element-plus/element-plus/blob/2.11.5/packages/theme-chalk/src/button.scss
https://github.com/element-plus/element-plus/blob/2.11.5/packages/theme-chalk/src/mixins/_button.scss
https://element-plus.org/en-US/guide/theming

以下程式為精簡示例；省略的頁面上下文與完整設定列於講稿。
本次規劃只處理淺色模式，暗色模式不在範圍內。

## 第 16 頁：公司樣式設定與技術對照

公司設定保存設計意義，對接檔負責轉成 Element Plus 使用的名稱

### styles/tokens.css（節錄）

```css
:root {
  --app-primary: #006B64;
  --app-primary-hover: #197B75;
  --app-font-size: 14px;
  --app-radius: 6px;
  /* ... */
}
```

### styles/element-plus.css（節錄）

```css
:root {
  --el-color-primary:
    var(--app-primary);
  --el-color-primary-light-3:
    var(--app-primary-hover);
  --el-font-size-base:
    var(--app-font-size);
  --el-border-radius-base:
    var(--app-radius);
  /* ... */
}
```

> 示意色碼與尺寸；完整主題還需對應停用色、按下色等狀態設定

### 講稿

左側是公司維護的樣式設定，右側是與 Element Plus 的對照。設計若把圓角從 6px 改成 8px，可修改公司設定，再由引用關係套用。Figma 與 CSS 之間仍需建立匯出或同步流程，不能因為兩邊名稱相同就視為已經自動同步。本例 light-3 對應公司核定的 hover 色，不主張色碼依 Element Plus 的預設公式計算。完整檔另列在講稿，包含 light-5／7／8／9 及 dark-2 等，避免只改主要色留下舊色階。載入順序為 Element Plus 基礎 CSS、公司 tokens、Element Plus 對接檔，再載入公司組件 CSS。
來源與範圍：Element Plus 2.11.5 原始碼及官方主題文件。這是報告用示例，不代表公司已核定規範或已使用此版本。公司色碼、尺寸與 @company/ui 套件名稱均為示意。
https://github.com/element-plus/element-plus/blob/2.11.5/packages/theme-chalk/src/common/var.scss
https://github.com/element-plus/element-plus/blob/2.11.5/packages/theme-chalk/src/button.scss
https://github.com/element-plus/element-plus/blob/2.11.5/packages/theme-chalk/src/mixins/_button.scss
https://element-plus.org/en-US/guide/theming

以下程式為精簡示例；省略的頁面上下文與完整設定列於講稿。
本頁公司色碼為淺色模式示意。

## 第 17 頁：Backtop 樣式變數完整地圖

Element Plus 2.11.5 原廠淺色預設；依 CSS 屬性逐層追溯到實際值

```text
<el-backtop />
|
+-- background-color
|   `-- --el-backtop-bg-color
|       `-- --el-bg-color-overlay = #ffffff
|
+-- color
|   `-- --el-backtop-text-color
|       `-- --el-color-primary = #409eff
|           `-- SVG path: fill="currentColor"
|
+-- :hover background-color
|   `-- --el-backtop-hover-bg-color
|       `-- --el-border-color-extra-light = #f2f6fc
|
`-- box-shadow
    `-- --el-box-shadow-lighter
        `-- 0px 0px 6px rgba(0, 0, 0, .12)
```

> 組件有自己的變數，並引用全域設定；這張地圖用來判斷應該調整哪一層

### 講稿

本頁依提供的追溯樹整理，只保留淺色模式。完整列出 Backtop 的背景色、圖示文字色、滑鼠移入背景與陰影。background-color 引用 --el-backtop-bg-color，再引用 --el-bg-color-overlay，預設為 #ffffff。color 引用 --el-backtop-text-color，再引用 --el-color-primary，預設為 #409eff；內建 SVG path 以 currentColor 使用該顏色。hover 背景由 --el-backtop-hover-bg-color 對應 --el-border-color-extra-light，預設 #f2f6fc。陰影直接引用 --el-box-shadow-lighter，淺色預設為 0px 0px 6px rgba(0,0,0,.12)。這張是樣式變數的完整追溯範圍，不列出定位、尺寸等固定 CSS 屬性。全部數值以 Element Plus 2.11.5 的 el-backtop.css 與 index.css 核對，屬原廠預設，與前頁公司主題的示意色碼分開理解。
來源：https://github.com/element-plus/element-plus/blob/2.11.5/packages/theme-chalk/src/backtop.scss
來源：https://github.com/element-plus/element-plus/blob/2.11.5/packages/theme-chalk/src/common/var.scss

## 第 18 頁：直接使用 Element Plus

假設已載入相同的公司主題，頁面仍需自行設定常用按鈕行為

### pages/Apply.vue（節錄）

```vue
<script setup lang="ts">
import { ElButton } from 'element-plus'
</script>
<template>
  <ElButton type="primary" native-type="button"
    class="submit-button" :loading="saving"
    :disabled="saving || !canSubmit"
    @click="submit">送出申請</ElButton>
</template>
<style scoped>
.submit-button {
  min-height: 36px; padding: 0 16px;
}
</style>
```

```text
project/
|-- pages/
|   `-- Apply.vue
|-- styles/
|   |-- tokens.css
|   `-- element-plus.css
`-- nuxt.config.ts
```

> 直接使用也能套用公司主題；是否再封裝，取決於有沒有重複的規格與行為

### 講稿

這裡先排除「只有封裝才可以改主題」的誤解。直接使用 Element Plus 一樣可以套用上一個案例的主題。頁面同時要重複寫 primary、native-type、loading 時 disabled 及按鈕尺寸。若許多頁面都需要同一組規則，才有抽成共用組件的價值。頁面中的 saving、canSubmit、submit 分別表示送出中、業務上是否允許送出及送出流程，完整上下文見講稿。僅使用一次且沒有共通規格的組件，可以先維持直接使用。
來源與範圍：Element Plus 2.11.5 原始碼及官方主題文件。這是報告用示例，不代表公司已核定規範或已使用此版本。公司色碼、尺寸與 @company/ui 套件名稱均為示意。
https://github.com/element-plus/element-plus/blob/2.11.5/packages/theme-chalk/src/common/var.scss
https://github.com/element-plus/element-plus/blob/2.11.5/packages/theme-chalk/src/button.scss
https://github.com/element-plus/element-plus/blob/2.11.5/packages/theme-chalk/src/mixins/_button.scss
https://element-plus.org/en-US/guide/theming

以下程式為精簡示例；省略的頁面上下文與完整設定列於講稿。
目錄中的 styles 保存共用主題，頁面內的 submit-button 樣式是封裝前需要自行維護的設定。

## 第 19 頁：AppButton 的封裝實作

components/AppButton.vue，先提供一個範圍明確的共用組件

### 宣告常用屬性

```vue
<script setup lang="ts">
import { ElButton } from 'element-plus'
defineOptions({ inheritAttrs: false })
withDefaults(defineProps<{
  loading?: boolean
  disabled?: boolean
}>(), {
  loading: false,
  disabled: false
})
</script>
```

### 內部仍使用 Element Plus

```vue
<template>
  <ElButton v-bind="$attrs"
    class="app-button"
    type="primary"
    native-type="button"
    :loading="loading"
    :disabled="disabled || loading">
    <slot />
  </ElButton>
</template>
```

> 統一主要按鈕的預設與載入行為，送出 API 與業務資格仍由頁面負責

### 講稿

AppButton 是本案例的「公司主要操作按鈕」，不是完整替代 Element Plus 的全部按鈕類型。內部固定 primary 與 native-type=button，loading 時停用，避免各頁重複設定。以 inheritAttrs:false 搭配 v-bind="$attrs" 把外部的 click 監聽與 aria-label 等轉交給內部按鈕。固定設定寫在 v-bind 之後，讓公司預設不被同名的一般屬性覆蓋。預設 slot 提供按鈕文字。這個版本沒有包辦所有插槽與 expose 方法，也沒有混入 API 或權限規則。原本按鈕的鍵盤與焦點行為由 Element Plus 提供，仍需導入驗證。
https://vuejs.org/guide/components/attrs.html
https://element-plus.org/en-US/component/button

以下程式為精簡示例；省略的頁面上下文與完整設定列於講稿。

## 第 20 頁：頁面改用 AppButton

頁面保留業務資料與事件，共用樣式集中在獨立檔案

### pages/Apply.vue（節錄）

```vue
<script setup lang="ts">
import AppButton
  from '../components/AppButton.vue'
</script>
<template>
  <AppButton :loading="saving"
    :disabled="!canSubmit" @click="submit">
    送出申請
  </AppButton>
</template>
```

```text
project/
|-- components/
|   `-- AppButton.vue
|-- styles/
|   |-- tokens.css
|   |-- element-plus.css
|   |-- button.css
|   `-- index.css
|-- pages/
|   `-- Apply.vue
`-- nuxt.config.ts
```

> 後續調整共同尺寸或載入規則時，可集中修改公司組件與樣式檔

### 講稿

封裝後，頁面仍傳 saving、canSubmit 並實作 submit，但省去固定類型、重複尺寸與 disabled||loading 的處理。共用 CSS 以 .app-button.el-button 設定 min-height:var(--app-control-height) 及左右 padding，主題仍由 tokens 與對接檔控制。試點階段先放在同一專案也可以，文件需指定唯一維護來源。這個案例只封裝主要操作按鈕，未聲稱所有 Element Plus 組件都必須再包一層。
來源與範圍：Element Plus 2.11.5 原始碼及官方主題文件。這是報告用示例，不代表公司已核定規範或已使用此版本。公司色碼、尺寸與 @company/ui 套件名稱均為示意。
https://github.com/element-plus/element-plus/blob/2.11.5/packages/theme-chalk/src/common/var.scss
https://github.com/element-plus/element-plus/blob/2.11.5/packages/theme-chalk/src/button.scss
https://github.com/element-plus/element-plus/blob/2.11.5/packages/theme-chalk/src/mixins/_button.scss
https://element-plus.org/en-US/guide/theming

以下程式為精簡示例；省略的頁面上下文與完整設定列於講稿。

## 第 21 頁：npm 套件的目錄結構

把已驗證的共用檔案移到 @company/ui，再建置成可發布內容

```text
app-ui/
|-- src/
|   |-- components/
|   |   `-- AppButton.vue
|   |-- styles/
|   |   |-- tokens.css
|   |   |-- element-plus.css
|   |   |-- button.css
|   |   `-- index.css
|   `-- index.ts
|-- package.json
|-- vite.config.ts
|-- tsconfig.build.json
`-- ...
```

```text
app-ui/dist/
|-- components/
|   `-- AppButton.vue.d.ts
|-- index.js
|-- index.d.ts
|-- style.css
|-- tokens.css
`-- element-plus.css

// src/index.ts
export { default as AppButton }
  from './components/AppButton.vue'
```

> 原始碼編譯為 dist，package.json 定義組件與 CSS 的對外入口

### 講稿

這張表就是原始碼與建置輸出的檔案地圖。src/index.ts 匯出 AppButton，建置工具把 .vue 編譯為 JavaScript，型別工具產出 .d.ts，CSS 則獨立交付。package.json 的 exports 定義使用者可以引用哪些入口，Vue 與 Element Plus 列為 peerDependencies，與使用專案共用，不打包另一份進來。Nuxt 保留在應用層，這個單一按鈕套件不依賴 Nuxt。完整最小示例包含 build 設定，示例版本固定 Element Plus 2.11.5，實務上相容範圍要經驗證後再開放。npmjs 私有套件需要對應帳號／組織權限及支援方案，使用 restricted，不是 package.json 的 private:true。
https://docs.npmjs.com/creating-and-publishing-private-packages/
https://docs.npmjs.com/cli/v11/configuring-npm/package-json/

以下程式為精簡示例；省略的頁面上下文與完整設定列於講稿。
目錄樹保留原始碼及建置輸出的主要結構，其餘以 ... 表示。src/index.ts 同時載入樣式並匯出 AppButton；本頁只節錄組件匯出，完整設定列於講稿。

## 第 22 頁：新專案安裝與使用套件

使用端只改組件來源，共用規格由指定套件版本提供

### 安裝、全域 CSS 與專案目錄

```vue
npm install --save-exact @company/ui@0.1.0

// nuxt.config.ts
export default defineNuxtConfig({ css: [
  'element-plus/dist/index.css',
  '@company/ui/style.css'
] })

// project/
// |-- nuxt.config.ts
// `-- pages/Apply.vue
```

### pages/Apply.vue（節錄）

```vue
<script setup lang="ts">
import { AppButton }
  from '@company/ui'
</script>
<template>
  <AppButton :loading="saving"
    :disabled="!canSubmit"
    @click="submit">
    送出申請
  </AppButton>
</template>
```

> 套件來源與權限完成設定後即可安裝；本次提供發布示例，尚未實際發布

### 講稿

新專案安裝可取得權限的指定版本。Nuxt 的 css 陣列先載入 Element Plus，再載入公司 style.css，該檔已包含 tokens、對照檔與公司按鈕樣式，避免缺少主題。元件在 script setup 明確 import，不預設自動註冊。直接安裝 @company/ui 時，使用專案也要有符合相容範圍的 Vue 與 Element Plus。安裝後可用與原頁相同的 saving、canSubmit 及 submit。實際 npmjs 發布需換成公司擁有的 scope，完成登入、權限及驗收後再執行；這裡只示範，不進行發布。若公司採內部 registry，可維持套件結構並調整來源設定。
https://docs.npmjs.com/creating-and-publishing-private-packages/

以下程式為精簡示例；省略的頁面上下文與完整設定列於講稿。

# 完整程式與交付設定

## 完整最小範例檔案

下列為可編譯的最小套件示例。正式交付仍需確認相容範圍與組件規格。

### src/styles/tokens.css

```css
:root {
  --app-primary: #006B64;
  --app-primary-hover: #197B75;
  --app-primary-active: #00564F;
  --app-primary-disabled: #80B5B2;
  --app-primary-light-7: #B3D3D0;
  --app-primary-light-8: #CCE1DF;
  --app-primary-light-9: #E6F0EF;
  --app-text: #213744;
  --app-font-size: 14px;
  --app-radius: 6px;
  --app-control-height: 36px;
  --app-control-padding-x: 16px;
}
```

### src/styles/element-plus.css

```css
:root {
  --el-color-primary: var(--app-primary);
  --el-color-primary-light-3: var(--app-primary-hover);
  --el-color-primary-light-5: var(--app-primary-disabled);
  --el-color-primary-light-7: var(--app-primary-light-7);
  --el-color-primary-light-8: var(--app-primary-light-8);
  --el-color-primary-light-9: var(--app-primary-light-9);
  --el-color-primary-dark-2: var(--app-primary-active);
  --el-text-color-primary: var(--app-text);
  --el-font-size-base: var(--app-font-size);
  --el-border-radius-base: var(--app-radius);
}
```

### src/styles/button.css

```css
.app-button.el-button {
  min-height: var(--app-control-height);
  padding: 0 var(--app-control-padding-x);
}
```

### src/styles/index.css

```css
@import './tokens.css';
@import './element-plus.css';
@import './button.css';
```

### src/components/AppButton.vue

```vue
<script setup lang="ts">
import { ElButton } from 'element-plus'
defineOptions({ inheritAttrs: false })
withDefaults(defineProps<{
  loading?: boolean
  disabled?: boolean
}>(), { loading: false, disabled: false })
</script>

<template>
  <ElButton v-bind="$attrs" class="app-button"
    type="primary" native-type="button"
    :loading="loading"
    :disabled="disabled || loading">
    <slot />
  </ElButton>
</template>
```

### src/index.ts

```ts
import './styles/index.css'
export { default as AppButton } from './components/AppButton.vue'
```

### vite.config.ts

```ts
import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'
import { copyFileSync } from 'node:fs'

export default defineConfig({
  plugins: [vue(), {
    name: 'copy-theme-css',
    closeBundle() {
      for (const name of ['tokens', 'element-plus']) {
        copyFileSync(`src/styles/${name}.css`, `dist/${name}.css`)
      }
    }
  }],
  build: {
    lib: {
      entry: 'src/index.ts',
      formats: ['es'],
      fileName: 'index',
      cssFileName: 'style'
    },
    rollupOptions: { external: ['vue', 'element-plus'] }
  }
})
```

### tsconfig.build.json

```json
{
  "compilerOptions": {
    "target": "ES2022",
    "module": "ESNext",
    "moduleResolution": "Bundler",
    "strict": true,
    "skipLibCheck": true,
    "declaration": true,
    "emitDeclarationOnly": true,
    "outDir": "dist",
    "rootDir": "src",
    "lib": [
      "ES2022",
      "DOM"
    ]
  },
  "include": [
    "src/**/*.ts",
    "src/**/*.vue"
  ]
}
```

### package.json

```json
{
  "name": "@company/ui",
  "version": "0.1.0",
  "type": "module",
  "files": [
    "dist"
  ],
  "types": "./dist/index.d.ts",
  "exports": {
    ".": {
      "types": "./dist/index.d.ts",
      "import": "./dist/index.js"
    },
    "./style.css": "./dist/style.css",
    "./tokens.css": "./dist/tokens.css",
    "./element-plus.css": "./dist/element-plus.css"
  },
  "sideEffects": [
    "**/*.css"
  ],
  "scripts": {
    "build": "vite build && vue-tsc -p tsconfig.build.json"
  },
  "peerDependencies": {
    "vue": "^3.5.0",
    "element-plus": "2.11.5"
  },
  "devDependencies": {
    "vue": "3.5.22",
    "element-plus": "2.11.5",
    "vite": "7.1.7",
    "@vitejs/plugin-vue": "6.0.1",
    "typescript": "5.9.3",
    "vue-tsc": "3.1.1"
  },
  "publishConfig": {
    "registry": "https://registry.npmjs.org/",
    "access": "restricted"
  }
}
```

## 頁面的完整業務上下文

前述 Apply.vue 節錄省略以下程式，封裝前後均由頁面持有。`submit` 中才呼叫實際 API，UI 套件不包含業務 API。

```ts
import { ref } from 'vue'
const saving = ref(false)
const canSubmit = ref(true) // 依實際業務資格計算
async function submit() {
  if (saving.value || !canSubmit.value) return
  saving.value = true
  try {
    await sendApplication() // 由專案實作
  } finally {
    saving.value = false
  }
}
```

## 安裝、建置與發布順序

1. 開發者安裝套件開發所需相依：`npm install`。
2. 執行 `npm run build`，產出 JS、型別與 CSS。
3. 先執行 `npm pack --dry-run` 檢視發布檔案，再用 `npm pack` 產出本地套件，供獨立 Demo 安裝驗證。
4. 確認 npmjs scope、組織權限、私有套件方案與登入方式。
5. 驗證及授權完成後，才在套件目錄執行 `npm publish --access restricted`。這是流程示例，本次沒有執行發布。
6. 使用端安裝 `npm install --save-exact @company/ui@0.1.0`，並依範例載入 CSS 與 import 組件。

`publishConfig.access = restricted` 表示 npmjs 的私有發布方式。`private: true` 的作用是阻止發布，不能用它代表私有套件。公司的內部 registry 可採同樣的 npm 套件格式，另行設定來源。

完整全域設定仍需依首波組件補齊，並實際檢查狀態色、對比度、鍵盤操作與套件導入結果。


## 來源

- [Element Plus 主題設定](https://element-plus.org/en-US/guide/theming)
- [Element Plus 2.11.5 全域及組件設定](https://github.com/element-plus/element-plus/blob/2.11.5/packages/theme-chalk/src/common/var.scss)
- [Element Plus 2.11.5 Button 樣式](https://github.com/element-plus/element-plus/blob/2.11.5/packages/theme-chalk/src/button.scss)
- [Element Plus 2.11.5 Button 狀態對照](https://github.com/element-plus/element-plus/blob/2.11.5/packages/theme-chalk/src/mixins/_button.scss)
- [Vue 屬性與事件轉交](https://vuejs.org/guide/components/attrs.html)
- [npm 私有套件](https://docs.npmjs.com/creating-and-publishing-private-packages/)
- [npm package.json](https://docs.npmjs.com/cli/v11/configuring-npm/package-json/)

`--el-color-primary-dark-2` 是主要色較深一階的色階名稱，用於淺色模式的按下狀態，與暗色模式無關。此份範例沒有加入暗色模式的設定或切換流程。
