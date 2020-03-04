---
title: Power BI 報表伺服器的新功能
description: 了解 Power BI 報表伺服器的新功能。 本文涵蓋主要功能範圍，並會隨著新項目發行而更新。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 02/27/2020
ms.openlocfilehash: 251f89dd031d9a2bda146266308dc528f05eddb2
ms.sourcegitcommit: ec4d2d0f52d737e8e0583f6a7b16e6fd87382510
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2020
ms.locfileid: "77782442"
---
# <a name="whats-new-in-power-bi-report-server"></a>Power BI 報表伺服器的新功能

了解 Power BI 報表伺服器中的新功能，以及針對 Power BI 報表伺服器最佳化的 Power BI Desktop 中的新功能。 本文涵蓋主要功能範圍，且會隨著每個新版本而更新。

下載 [Power BI 報表伺服器和針對 Power BI 報表伺服器最佳化的 Power BI Desktop](https://powerbi.microsoft.com/report-server/)。

如需相關的 Power BI「新功能」資訊，請參閱︰

* [Power BI 服務的新功能](../service-whats-new.md)
* [Power BI Desktop 的新功能](../desktop-latest-update.md)
* [Power BI 行動裝置 App 的新功能](../consumer/mobile/mobile-whats-new-in-the-mobile-apps.md)

## <a name="january-2020"></a>2020 年 1 月

如需詳細資訊，請參閱 Power BI 報表伺服器 2020 年 1 月的部落格文章。

### <a name="power-bi-desktop-optimized-for-power-bi-report-server"></a>針對 Power BI 報表伺服器最佳化的 Power BI Desktop

此版本引進許多新功能，例如按鈕的條件式格式化、資料分析改善，以及 KPI 和表格視覺效果的更多格式設定。 以下是更新的摘要清單：

**報告**

- 將資料表資料行或矩陣值設定為自訂 URL
- KPI 視覺效果格式設定
- 篩選窗格體驗更新

**分析**

- 有條件地格式化按鈕
- 載入更多分析見解
- 新的 DAX 函式：季度

**資料準備**

- 資料分析改善

**其他**

- 新檔案格式：.pbids
- 模型化作業的效能改善

**報告**

將資料表資料行或矩陣值設定為自訂 URL 

您可以將資料表資料行或矩陣值設定為自訂 URL。 您可在 [格式化] 窗格中的 [設定格式化的條件] 卡片底下找到此新選項。

KPI 視覺效果格式設定 

在本月的版本中，KPI 有新的格式設定選項：

- 指標文字格式設定 (字型家族、色彩和對齊)
- 趨勢軸透明度
- 目標和距離文字格式設定 (標籤文字、字型家族、色彩和大小)
- 距離文字格式設定 (標籤文字、正方向、字型家族、色彩和大小)
- 新增有格式設定的日期標籤 (字型家族、色彩和大小)

您可以有條件地設定其中一些新的格式化選項：

- 指標字型色彩
- 目標字型色彩和目標距離字型色彩
- 良好/不良/中性狀態色彩
- 日期字型色彩

篩選窗格體驗更新 

我們已經簡化將目前報表轉換到新窗格的程序，作為[最新版本](https://powerbi.microsoft.com/blog/power-bi-report-server-september-2019-feature-summary/#filterPane)新篩選體驗公開推出的一部分。 當您第一次開啟 [Power BI 報表伺服器] 時，您會看到篩選窗格自動更新對話方塊。 在報表伺服器中，這些更新也包含橫幅，當報表必須移轉到新體驗時會顯示。

**分析**

按鈕的條件式格式設定 

這些條件式格式設定更新全部都與按鈕相關。 您現在可以動態地設定下列屬性的格式設定：

- 按鈕文字字型色彩
- 按鈕文字
- 圖示線條色彩
- 外框色彩
- 填滿色彩
- 按鈕工具提示 (在動作卡片底下)

載入更多分析見解 

執行「分析」功能來尋找資料中的見解 (例如說明增加) 時，我們只會在一段時間內執行機器學習模型，以及時顯示見解。 如果有大量資料要分析，在初始逾時後，您現在可以選擇繼續執行分析。

*新的 DAX 函式：Quarter*

這個月，我們有新的 DAX 函式：Quarter。 Quarter 函式會傳回對應到指定日期的季度。

**資料準備**

資料分析改善 

這個月，我們在 Power Query 編輯器中的資料分析功能引進幾個重要改善，包括：

- 除了現有的 [依值] 準則外，[資料行設定檔] 窗格值散發視覺效果 (特定是依資料行類型) 的組成多重群組選項。
- 文字：依文字長度 (字元數)。
- 編號：依符號 (正/負) 和同位 (奇/偶)。
- 日期/日期時間：依年、月、日、當年週次、當週的星期幾、上午/下午時間，以及一天內的小時。
- 針對其他資料類型有更多，例如，邏輯 True/False。

篩選選項 

在 [資料行設定檔] 散發窗格中，您已經可以利用數種類型特定的群組準則。 現在，當群組準則已套用時，您也可以從分佈圖中每個值的圖說文字內篩選。 例如，您可以從日期/日期時間資料行的 [資料設定檔] 窗格中，排除落在指定月份的所有值。

**其他**

新檔案格式：.pbids 

這個月，我們推出新檔案格式：.pbids，簡化組織中報表建立者的「取得資料」體驗。 我們建議系統管理員為常用的連線建立這些檔案。

當報表建立者開啟 .pbids 檔案時，Power BI Desktop 會提示您進行驗證，以連線到檔案中指定的資料來源。 然後，使用者選取要載入模型中的資料表。 他們可能也需要選取資料庫 (如果檔案中未指定的話)。 報表建立者可以從該處開始建立視覺效果。

《Power BI Desktop 中的資料來源》一文的[使用 .pbids 檔案來取得資料](../desktop-data-sources.md#using-pbids-files-to-get-data)小節中，可找到詳細資訊和範例。

模型化作業的效能改善 

我們已在 Analysis Services 引擎中改善效能，以加速模型化作業，例如，新增量值或計算結果欄，以及建立關聯性。 您所看到的改善數量取決於模型，但對於某些客戶，我們看到開啟檔案和新增量值等動作有 20 倍效能改進。

這就是 2020 年 1 月 Power BI 報表伺服器版本的所有新功能。 請繼續傳送意見反應，別忘了[投票給您想要在 Power BI](https://ideas.powerbi.com/forums/265200-power-bi) \(英文\) 中看到的功能。

### <a name="power-bi-report-server"></a>Power BI 報表伺服器

#### <a name="export-to-excel-from-power-bi-reports"></a>從 Power BI 報表匯出至 Excel

Power BI 報表伺服器中的從 Power BI 報表匯出至 Excel，現在的運作方式與從 Power BI 服務中的從 Power BI 報表匯出至 Excel 相同。 您可以直接匯出至 Excel .xlsx 格式，匯出限制為 150 K 個資料列。

#### <a name="azure-sql-managed-instance-support"></a>Azure SQL 受控執行個體支援

您現在可以在裝載於 VM 或資料中心的 Azure SQL 受控執行個體 (MI) 中，裝載用於 Power BI 報表伺服器的資料庫目錄。 僅支援使用資料庫認證來連線到 SQL MI。

#### <a name="power-bi-premium-dataset-support"></a>Power BI Premium 資料集支援

您可以使用 Microsoft 報表產生器或 SQL Server Data Tools (SSDT) 連線到 Power BI 資料集。 然後您可以使用 SQL Server Analysis Services 連線能力，將這些報表發佈到 Power BI 報表伺服器。 使用者必須使用預存 Windows 使用者名稱和密碼來啟用此情節。

#### <a name="alttext-alternative-text-support-for-report-elements"></a>報表元素的 AltText (替代文字) 支援

撰寫報表時，您可以使用工具提示來指定報表上每個元素的文字。 螢幕助讀程式技術將會使用這些工具提示。

#### <a name="azure-active-directory-application-proxy-support"></a>Azure Active Directory 應用程式 Proxy 支援

若使用 Azure Active Directory 應用程式 Proxy，您就不再需要管理自己的 Web 應用程式 Proxy，以允許透過 Web 或行動裝置應用程式進行安全存取。 如需詳細資訊，請參閱[透過 Azure Active Directory 的應用程式 Proxy 遠端存取內部部署應用程式](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy) \(部分機器翻譯\)。

#### <a name="custom-headers"></a>自訂標頭

針對符合所指定 RegEx 模式的 URL 設定標頭值。 使用者可以使用有效的 XML 來更新自訂標頭值，以設定所選要求 URL 的標頭值。 系統管理員可以在 XML 中新增任意數目的標頭。 如需詳細資訊，請參閱 Reporting Services＜伺服器屬性進階頁面＞  一文中的[CustomHeaders](/sql/reporting-services/tools/server-properties-advanced-page-reporting-services#customheaders)。

#### <a name="transparent-database-encryption"></a>透明資料庫加密

Power BI 報表伺服器現在支援 Power BI 報表伺服器目錄資料庫 (Enterprise 與標準版本) 的透明資料庫加密。

#### <a name="power-bi-visuals-api"></a>Power BI 視覺效果 API

此版本隨附的 API 版本為 2.6。

#### <a name="microsoft-report-builder-update"></a>Microsoft 報表產生器更新

新發行的報表產生器版本與 2016、2017 和 2019 版 Reporting Services 完全相容。 其也與所有已發行和支援的 Power BI 報表伺服器版本相容。

## <a name="september-2019"></a>2019 年 9 月

如需所有新功能的詳細資料，請參閱 [Power BI Report Server September 2019](https://powerbi.microsoft.com/blog/power-bi-report-server-september-2019-feature-summary/) (Power BI 報表伺服器 2019 年 9 月) 部落格文章。

Power BI 報表伺服器的 2019 年 9 月更新包含了許多 Power BI 報表功能。 以下是一些重點：

- **交叉分析篩選器的視覺效果層級篩選**：您可以將視覺效果層級篩選新增至交叉分析篩選器。 它的運作方式就像任何其他視覺效果層級的篩選一樣，但只是篩選交叉分析篩選器本身，而不是其他視覺效果。 這項篩選對於篩選出空白，或您要使用量值篩選時很有用。
- **資料表和矩陣的圖示集**使用 KPI 圖示，您可以設定規則，以在資料表和矩陣中顯示不同的圖示集，類似於 Excel 中的圖示集。
- **群組視覺效果**現在，您可以在報表頁面上將視覺效果、圖形、文字方塊、影像及按鈕群組在一起，就像在 PowerPoint 中一樣。 當您將物件群組在一起時，可以一起移動這些物件並調整其大小。 群組可讓您更輕鬆地在每個頁面上有許多物件的報表中工作。
- **新的預設佈景主題**為了與新的佈景主題 JSON 選項一起使用，我們正在更新可用於報表的佈景主題，以及變更新報表的預設佈景主題。 新預設佈景主題會更妥善地配合 Microsoft 的設計語言，並遵循視覺效果的最佳設計做法。 
- **更新的窗格設計**：我們重新整理了大部分的介面。 我們已將所有窗格、頁尾和檢視切換器更新為較淺的色彩、已更新間距，並引進了新的圖示。 新設計是重新整理整個介面的第一個步驟。

以下是完整的功能清單。 

### <a name="reporting"></a>報告

- 更新的窗格設計
- 交叉分析篩選器的視覺效果層級篩選
- 效能分析程式窗格的排序
- 視覺效果標頭工具提示
- 資料表和矩陣總計標籤自訂
- 階層交叉分析篩選器的同步交叉分析篩選器支援
- 跨視覺效果的一致字型大小
- 資料表和矩陣的圖示集
- 依規則的條件式格式設定百分比支援
- 新的篩選窗格現已正式推出
- 在散佈圖上使用播放軸時的資料色彩支援
- 使用相對日期和下拉式交叉分析篩選器時的效能改善
- 群組視覺效果
- 佈景主題中的色彩和文字類別
- 新的預設佈景主題

### <a name="analytics"></a>分析

- 自訂格式字串
- 格式設定選項的條件式格式設定更新

    - 視覺效果背景和標題色彩
    - 卡片色彩
    - 量測計填滿和色彩
    - 替代文字
    - 框線色彩

- 條件式格式設定警告
- 鑽研可探索性改善
- 新的 DAX 運算式：REMOVEFILTERS 和 CONVERT
- 新的 DAX 比較運算子：==

### <a name="data-preparation"></a>資料準備

- M Intellisense 的改善
- 新的轉換：依位置分割資料行
- 從資料分析複製到剪貼簿


## <a name="may-2019"></a>2019 年 5 月

### <a name="power-bi-desktop-for-power-bi-report-server"></a>適用於 Power BI 報表伺服器的 Power BI Desktop

如需所有新功能的詳細資料，請參閱 [Power BI Report Server May 2019](https://powerbi.microsoft.com/blog/power-bi-report-server-update-may-2019/) (Power BI 報表伺服器 2019 年 5 月) 部落格文章。

以下是此版本的一些重點：

#### <a name="performance-analyzer"></a>效能分析器 

如果您的報表執行速度比預期慢，請嘗試使用 Power BI Desktop 中的效能分析器。 當您予以啟動時，它會建立一個記錄檔，其中包含您在報表中所採取之每個動作的相關資訊。 深入了解[效能分析器](../desktop-performance-analyzer.md)。

#### <a name="new-modeling-view"></a>新的模型檢視

在 Power BI Desktop 的新模型檢視中，您可以檢視並處理包含許多資料表的複雜資料集。 重點包括多個圖表配置，以及資料行、量值和資料表的大量編輯。 深入了解[模型檢視](../desktop-modeling-view.md)。

#### <a name="accessible-visual-interaction"></a>無障礙的視覺效果互動

您現在可以使用鍵盤導覽來存取許多內建視覺效果上的資料點。 深入了解 [Power BI 報表的協助工具](../desktop-accessibility.md)。

#### <a name="conditional-formatting-titles-and-web-url-actions"></a>條件式格式設定標題和 Web URL 動作

Power BI 報表是互動式報表。 很明顯，報表中的標題會是動態的，用來反映報表的目前狀態。 您可以使用相同的運算式繫結格式設定，讓按鈕、圖形與影像的 URL 成為動態項目。 深入了解[以運算式為基礎的標題](../desktop-conditional-format-visual-titles.md)。

#### <a name="cross-highlight-by-axis-labels"></a>依軸標籤的交叉醒目提示

選取視覺效果中的軸類別標籤，以交叉醒目提示頁面上的其他項目，就像您在視覺效果中選取資料點一樣。 深入了解[交叉醒目提示](../power-bi-reports-filters-and-highlighting.md#ad-hoc-highlighting)。

#### <a name="all-the-new-features"></a>所有新功能

以下是所有新功能的清單：

#### <a name="reporting"></a>報告

- 折線圖單一點上的交叉醒目提示 
- 標題的自動換行 
- 更新預設視覺效果互動以交叉篩選
- 視覺效果框線的圓角 
- 單選交叉分析篩選器  
- 針對 Bing 地圖的熱度圖支援  
- 依軸標籤的交叉醒目提示  
- 預設工具提示格式設定  
- 針對按鈕、圖形與影像的靜態 Web URL 支援  
- 頁面對齊選項   
- 選取窗格改善  
- 無障礙的視覺效果互動  
- 視覺效果標題的條件式格式設定  
- 按鈕、圖形與影像的 Web URL 動作條件式格式設定
- 效能分析器窗格
- 資料表和矩陣的鍵盤導覽
- 程式行資料標籤位置控制項
- KPI 視覺效果指示器文字大小控制項

#### <a name="analytics"></a>分析

- 將日期顯示為階層的功能現已正式推出  

#### <a name="modeling"></a>模型化

- 新的模型檢視現已正式推出
- 新的 DAX 函數
- ALLSELECTED DAX 函式的更新
- 停用新報表的自動日期資料表

### <a name="power-bi-report-server"></a>Power BI 報表伺服器

#### <a name="support-for-trusted-visuals"></a>受信任視覺效果的支援

我們已將受信任視覺效果的支援新增至 Power BI 報表伺服器。 目前我們支援 Mapbox 和 PowerOn 視覺效果。 此版本不支援 ESRI、Visio 和 PowerApps。)

#### <a name="improved-security-features"></a>改善的安全性功能

**RestrictedResourceMimeTypeForUpload**，系統管理員可用來指定以逗號分隔的禁用 mime 類型清單，例如 text/html。

## <a name="january-2019"></a>2019 年 1 月

Power BI 報表中支援下列功能：

[**資料列層級安全性**](row-level-security-report-server.md)：在 Power BI 報表伺服器中設定資料列層級安全性 (RLS) 可以限制指定使用者的資料存取權。 篩選會限制資料列層級的資料存取，您可以在角色中定義篩選。

[**展開及摺疊矩陣資料列標頭**](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2018-feature-summary/#expandCollapse)：我們新增了展開及摺疊個別資料列標頭的能力，這是詢問度最高的視覺效果功能。

[**在 .pbix 檔案之間複製並貼上**](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2018-feature-summary/#copyPaste)：您可以在 .pbix 檔案之間複製視覺效果，您可從視覺效果的操作功能表，也可使用標準 CTRL+C 鍵盤快速鍵來複製，然後使用 CTRL+V 鍵，貼入另一份報表。

[**智慧對齊輔助線**](https://powerbi.microsoft.com/blog/power-bi-desktop-december-2018-feature-summary/#smartGuides)：當您在報表頁面上移動物件時，會看到智慧對齊輔助線 (如同您在 PowerPoint 中看到的一樣)，可協助您對齊頁面上的所有物件。 當您在頁面上拖曳物件或調整其大小時，都會看到智慧輔助線。 當您將某物件移近另一個物件時，它會貼齊該物件。

**協助工具功能**：要列出的協助工具功能非常多，例如[欄位清單窗格協助工具支援](https://powerbi.microsoft.com/blog/power-bi-desktop-december-2018-feature-summary/#fieldList)。 欄位清單窗格完全可供存取。 您只需要使用鍵盤和螢幕助讀程式即可瀏覽窗格，並可使用操作功能表將欄位新增到報表頁面。

#### <a name="custom-visuals"></a>自訂視覺效果

- 此版本隨附的 API 版本為 2.3。

### <a name="administrator-settings"></a>系統管理員設定

系統管理員可以在伺服器陣列的 SSMS 進階屬性中設定下列屬性：

**AllowedResourceExtensionsForUpload**：設定可上傳到報表伺服器之資源的延伸模組。 內建檔案類型 (像是 &ast;.rdl 和 &ast;.pbix) 的延伸模組不需要包含在內。 預設為「&ast;、&ast;.xml、&ast;.xsd、&ast;.xsl、&ast;.png、&ast;.gif、&ast;.jpg、&ast;.tif、&ast;.jpeg、&ast;.tiff、&ast;.bmp、&ast;.pdf、&ast;.svg、&ast;.rtf、&ast;.txt、&ast;.doc、&ast;.docx、&ast;.pps、&ast;.ppt、&ast;.pptx」。 

**SupportedHyperlinkSchemes**：設定允許對可轉譯超連結動作定義的 URI 配置逗點分隔清單，或設定 "&ast;" 啟用所有超連結配置。 例如，設定 "http, https" 會允許 "https://www.contoso.com" 的超連結， 但是會移除 “mailto:bill@contoso.com” 或 “javascript:window.open(‘ www.contoso.com’, ‘_blank’)” 的超連結。 預設為 "&ast;"。

## <a name="august-2018"></a>2018 年 8 月

2018 年 8 月，我們在針對 Power BI 報表伺服器最佳化的 Power BI Desktop 版本中新增了許多功能。 這些功能可依區域細分如下：

- [報告](#reporting)
- [分析](#analytics)
- [模型](#modeling)

### <a name="highlights-of-the-august-2018-release"></a>2018 年 8 月版本重點

在這整個很長的新功能清單中，以下是特別值得關注的功能。 如需詳細資訊，請參閱我們的[部落格文章](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/)。

#### <a name="report-theming"></a>報表佈景主題

Power BI 報表伺服器的 2018 年 8 月版本已新增報表佈景主題，可讓您快速以色彩標示整個報表，以符合某個佈景主題或公司商標。 當您匯入佈景主題時，您所有的圖表都會自動更新以使用佈景主題色彩，而且您可以從調色盤存取佈景主題色彩。 您可以使用 [切換佈景主題]  按鈕下的 [匯入佈景主題]  選項來上傳佈景主題檔案。

佈景主題檔案是 JSON 檔案，其中包含您想要我們在您的報表中使用的所有色彩，以及您想要套用至視覺效果的任何預設格式。
以下是簡單的範例 JSON 佈景主題，只會更新報表的預設色彩：

```json
{
"name": "waveform",
"dataColors": [ "#31B6FD", "#4584D3", "#5BD078", "#A5D028", "#F5C040", "#05E0DB", "#3153FD", "#4C45D3", "#5BD0B0", "#54D028", "#D0F540", "#057BE0" ],
"background":"#FFFFFF",
"foreground": "#F2F2F2",
"tableAccent":"#5BD078"
}
```

#### <a name="conditional-formatting-by-a-different-field"></a>依據不同欄位的條件式格式設定

條件式格式設定的其中一項明顯改進，就是在您的模型中依不同欄位格式化資料行的功能。

#### <a name="conditional-formatting-by-values"></a>依據值的條件式格式設定

另一個新的條件式格式設定類型是 [依欄位值格式化]  。 [依欄位值格式化] 可讓您使用指定色彩的量值或資料行，透過十六進位碼或名稱，將該色彩套用至背景或字型色彩。

#### <a name="report-page-tooltips"></a>報表頁面工具提示

Power BI 報表伺服器的 2018 年 8 月更新包含報表頁面工具提示功能。 這項功能可讓您設計報表頁面，以作為您報表中其他視覺效果的自訂工具提示。

#### <a name="log-axis-improvements"></a>對數座標軸改進

我們已大幅改進笛卡兒圖表中的對數座標軸。 當您的資料完全為正值或完全為負值時，您現在應該能夠針對任何笛卡兒圖表 (包括組合圖) 的數值座標軸選取對數刻度。

#### <a name="sap-hana-sso-direct-query"></a>SAP HANA SSO Direct Query

SAP HANA SSO Direct Query 對 Kerberos 的支援現在於 Power BI 報表中正式運作。

>[!Note]
>只有在將 SAP HANA 視為您已在 Power BI Desktop 中建立之報表的關聯式資料來源時，才支援此案例。  若要在 Power BI Desktop 中啟用這項功能，請在 DirectQuery 功能表的 [選項] 下，核取 [將 SAP HANA 視為關聯來源]，然後按一下 [確定]。

#### <a name="custom-visuals"></a>自訂視覺效果

- 此版本隨附的 API 版本為 1.13.0。

- 現在，自訂視覺效果可以回復為與目前伺服器 API 版本相容的舊版 (如果有的話)。

### <a name="reporting"></a>報告 

- [報表佈景主題](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#theming)
- [觸發動作的按鈕](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#buttons)
- [組合圖線條樣式](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#comboLines)
- [改善視覺效果的預設排序方式](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#sort)
- [數值交叉分析篩選器](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#numericSlicer)
- [進階交叉分析篩選器同步](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicerSync)
- [對數座標軸改進](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#logAxis)
- [漏斗圖的資料標籤選項](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#funnelChart)
- [設定線條筆觸寬度為零](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#lineStroke)
- [報表的高對比支援](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#highContrast)
- [環圈圖半徑控制項](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#donutRadius)
- [圓形圖和環圈圖的詳細資料標籤定位控制項](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#detailLabels)
- [分別為組合圖中的每個量值格式化資料標籤](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#comboLabels)
- [具有更大彈性且格式化的新視覺效果標題](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#visualHeader)
- [背景圖案格式化](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#wallpaper)
- [資料表和矩陣的工具提示](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#tableTooltips)
- [關閉視覺效果的工具提示](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#tooltips)
- [交叉分析篩選器協助工具](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicerAccessibility)
- [格式化窗格改進](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#formattingPane)
- [對於折線圖和組合圖的梯線圖支援](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#steppedLine)
- [排序體驗改進](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#sorting)
- [透過匯出為 PDF 列印報表 (在 Power BI Desktop 中)](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#print)
- [建立書籤群組](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#bookmarks)
- [交叉分析篩選器重新計算陳述式](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#slicer)
- [報表頁面工具提示](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#reportPageTooltips)

### <a name="analytics"></a>分析

- [新的 DAX 函式：COMBINEVALUES()](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#combineValues)
- [量值鑽研](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#measureDrillthrough)
- [依據不同欄位的條件式格式設定](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#conditionalFormattingField)
- [依據值的條件式格式設定](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#conditionalFormattingValue)

### <a name="modeling"></a>模型化

- [資料檢視中的篩選和排序](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#filterAndSort)
- [改善的地區設定篩選](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#locale)
- [量值的資料類別](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#dataCategory)
- [統計 DAX 函數](https://powerbi.microsoft.com/blog/power-bi-report-server-update-august-2018/#dax)

## <a name="may-2018"></a>2018 年 5 月

### <a name="configure-power-bi-ios-mobile-apps-for-report-servers-remotely"></a>針對報表伺服器遠端設定 Power BI iOS 行動應用程式

身為 IT 系統管理員，您現在可以使用您組織的 MDM 工具來遠端設定 Power BI iOS 行動裝置應用程式對報表伺服器的存取。 如需詳細資料，請參閱[從遠端設定 Power BI iOS 行動裝置應用程式對報表伺服器的存取權](configure-powerbi-mobile-apps-remote.md)。

## <a name="march-2018"></a>2018 年 3 月

2018 年 3 月，我們在針對 Power BI 報表伺服器最佳化的 Power BI Desktop 版本中新增了許多功能。 這些功能可依區域細分如下：

- [視覺效果](#visuals-updates)
- [報告](#reporting)
- [分析](#analytics)
- [效能](#performance)
- [報表伺服器](#report-server)
- [其他](#other-improvements)

### <a name="highlights-of-the-march-2018-release"></a>2018 年 3 月版本重點

在這整個很長的新功能清單中，以下是特別值得關注的功能。

#### <a name="rule-based-conditional-formatting-for-table-and-matrix"></a>[資料表和矩陣之以規則為基礎的條件式格式設定](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#conditionalFormatting)

建立規則，根據您資料表或矩陣中的特定商務邏輯，來視情況著色資料行的背景或字型色彩。

#### <a name="show-and-hide-pages"></a>[顯示和隱藏頁面](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#hidePages)

您希望讀者可存取您的報表，但某些頁面尚未完成。 現在您可以隱藏這些頁面，直到就緒為止。 或者，您可以從一般瀏覽隱藏頁面，而且讀者可以透過書籤或鑽研到達頁面。

#### <a name="bookmarking"></a>[標記書籤](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#bookmarking)

標記書籤是指建立書籤，透過您報表中的資料來述說故事。

- [書籤的交叉醒目提示](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkCrossHighlighting)：書籤會維持並顯示報表書頁面在您建立書籤時的交叉醒目提示狀態。
- [更多書籤彈性](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#bookmarkFlexibility)：書籤會反映您在報表中設定的屬性，而且只會影響您選擇的視覺效果。

#### <a name="multi-select-data-points-across-multiple-charts"></a>[跨多個圖表複選資料點](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#crosshighlight)

在多個圖表中選取多個資料點，並將交叉篩選套用至整個頁面。

#### <a name="sync-slicers-across-multiple-pages-of-your-report"></a>[跨報表的多個頁面同步交叉分析篩選器](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#syncSlicers)

交叉分析篩選器可套用至一個、兩個或多個報表頁面。

#### <a name="quick-measures"></a>[快速量值](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#quickMeasures) 

根據資料表中的現有量值和數值資料行，建立新的量值。

#### <a name="drilling-down-filters-other-visuals"></a>[向下切入篩選其他視覺效果](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#drillFiltersOtherVisuals)

當您在某個視覺效果的指定類別中向下切入時，您可以讓它依該相同的類別篩選頁面上的所有視覺效果。

### <a name="visuals-updates"></a>視覺效果更新

- [資料表和矩陣的資料格對齊](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#alignment)
- [顯示資料表和矩陣資料行的單位和精確度控制](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#displayUnits)
- [橫條圖和直條圖的資料標籤溢位](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#overflow)
- [控制笛卡兒座標和地圖視覺效果的資料標籤背景色彩](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#dataLabelBackground)
- [橫條/直條邊框間距控制項](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#padding)
- [增加用於圖表中軸標籤的面積](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#axisSize)
- [從 X 和 Y 軸群組的散佈圖視覺效果](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#scatterChart)
- [根據緯度和經度之地圖的高密度取樣](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#highDensityMaps)
- [回應式交叉分析篩選器](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#responsive)
- [新增相對日期交叉分析篩選器的錨點日期](https://powerbi.microsoft.com/blog/power-bi-desktop-january-2018-feature-summary/#anchorDate)

### <a name="reporting"></a>報告

- [關閉報表讀取模式的視覺效果標頭](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#visualHeader)
- [慢速資料來源的報表選項](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#slowDataSource)
- [改善的預設視覺效果放置](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#visualPlacement)
- [透過選取窗格控制視覺效果排序](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#selectionPane)
- [鎖定報表上的物件](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#lock)
- [搜尋格式設定和分析窗格](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#search)
- [欄位屬性窗格和欄位描述](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#fieldPropertiesPane)

### <a name="analytics"></a>分析

- [UTCNOW() 和 UTCTODAY()](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#utcDAX)
- [標記自訂日期資料表](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#customDateTable)
- [鑽研篩選其他視覺效果](https://powerbi.microsoft.com/blog/power-bi-desktop-december-feature-summary/#drillFiltersOtherVisuals)
- [多列卡片之多維度 AS 模型的資料格層級格式](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#cellLevelFormatting)

### <a name="performance"></a>效能

- [篩選效能提升](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#filtering)
- [DirectQuery 效能改善](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#dqPerf)
- [開啟和儲存效能改善](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#savePerf)
- [[顯示沒有資料的項目] 改善](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#showItemsWithNoData)

### <a name="report-server"></a>報表伺服器

#### <a name="export-to-accessible-pdf"></a>匯出至可存取的 PDF

當您將編頁報表 (RDL) 匯出至 PDF 時，您現在可以取得可存取/標記的 PDF 檔案。 雖然其大小更大，但更方便螢幕助讀程式和其他輔助技術讀取和巡覽。 您可以將 **AccessiblePDF** 裝置資訊設定設為 **True**，來啟用可存取的 PDF。 請參閱 [PDF 裝置資訊設定](https://docs.microsoft.com/sql/reporting-services/pdf-device-information-settings)和[變更裝置資訊設定](https://docs.microsoft.com/sql/reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config#changing-device-information-settings)。

### <a name="other-improvements"></a>其他功能改進

- [從範例新增資料行改善](https://powerbi.microsoft.com/blog/power-bi-desktop-november-2017-feature-summary/#addColumnFromExamples)
- [諮詢服務快速連結](https://powerbi.microsoft.com/blog/power-bi-desktop-february-2018-feature-summary/#consultingServices)
- [改善的錯誤報告](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#errors)
- [檢視之前發生的錯誤](https://powerbi.microsoft.com/blog/power-bi-desktop-march-2018-feature-summary/#viewErrors)

## <a name="october-2017"></a>2017年 10 月

### <a name="power-bi-report-data-sources"></a>Power BI 報表資料來源

Power BI 報表伺服器中的 Power BI 報表可以連線到各種資料來源。 您可以匯入資料及排程資料重新整理，或使用 DirectQuery 或即時連線到 SQL Server Analysis Services，直接進行查詢。 請參閱支援排程重新整理的資料來源清單，以及支援「Power BI 報表伺服器中 Power BI 報表資料來源」中 DirectQuery 的資料來源清單。

### <a name="scheduled-data-refresh-for-imported-data"></a>針對匯入的資料排程資料重新整理

在 Power BI 報表伺服器中，您可以設定排程資料重新整理，讓 Power BI 報表中的資料保持與內嵌模型的最新狀態，而不是即時連線或 DirectQuery。 若使用內嵌模型，您會匯入資料，所以會與原始資料來源中斷連線。 它必須更新以將資料保持在最新狀態，排程重新整理是執行此作業的一種方式。 深入了解「Power BI 報表伺服器中 Power BI 報表的排程重新整理」。

### <a name="editing-power-bi-reports-from-the-server"></a>編輯來自伺服器的 Power BI 報表

您可以從伺服器開啟和編輯 Power BI 報表 (.pbix) 檔案，但是您會回到您上傳的原始檔案。 **如果資料已由伺服器重新整理，當您第一次開啟檔案時，不會重新整理資料**。 您必須手動在本機重新整理，才能看到變更。

### <a name="large-file-uploaddownload"></a>大型檔案上傳/下載

您可以上傳最大 2 GB 大小的檔案，但是預設情況下，在 SQL Server Management Studio (SSMS) 的報表伺服器設定中，這項限制設為 1 GB。  這些檔案會儲存在資料庫中，如同適用於 SharePoint 一般，不需要 SQL Server 目錄的特殊設定。  

### <a name="accessing-shared-datasets-as-odata-feeds"></a>存取共用資料集作為 OData 摘要

您可以從 Power BI Desktop 使用 OData 摘要存取共用資料集。 如需詳細資訊，請參閱[在 Power BI 報表伺服器中存取共用資料集作為 OData 摘要](access-dataset-odata.md)。

### <a name="scale-out"></a>相應放大

這個版本支援相應放大。使用負載平衡器並設定伺服器親和性，以獲得最佳體驗。 案例尚未針對相應放大最佳化，因此您會看到模型可能會在多個節點之間複寫。 沒有網路負載平衡器和黏性工作階段，案例也能夠運作。 不過，您不只會看到因為模型載入 N 次導致各節點記憶體過度使用，也會看到因為每次模型在要求之間觸及新節點都會串流，導致連線之間的效能變慢。  

### <a name="administrator-settings"></a>系統管理員設定

系統管理員可以在伺服器陣列的 SSMS 進階屬性中設定下列屬性：

* EnableCustomVisuals：True/False
* EnablePowerBIReportEmbeddedModels：True/False
* EnablePowerBIReportExportData：True/False
* MaxFileSizeMb：預設值現在為 1000
* ModelCleanupCycleMinutes：檢查並從記憶體收回模型的頻率
* ModelExpirationMinutes：模型到期並收回的時間長度 (根據最後一次使用)
* ScheduleRefreshTimeoutMinutes：模型的資料重新整理可以花多長的時間。 預設為 2 小時。  沒有硬性上限。

**設定檔 rsreportserver.config**

```xml
<Configuration>
  <Service>
    <PollingInterval>10</PollingInterval>
    <IsDataModelRefreshService>false</IsDataModelRefreshService>
    <MaxQueueThreads>0</MaxQueueThreads>
  </Service>
</Configuration>
```

### <a name="developer-api"></a>開發人員 API

針對 SSRS 2017 引進的開發人員 API (REST API) 已針對 Power BI 報表伺服器擴充，以與 Excel 檔案和 .pbix 檔案搭配運作。 一個可能的使用案例是以程式設計方式從伺服器下載檔案、重新整理，然後重新發佈。 舉例來說，這是重新整理 Excel 活頁簿與 PowerPivot 模型的唯一方式。

有適用於大型檔案的個別新 API，它會在 Power BI 報表伺服器版本的 Swagger 中更新。 

### <a name="sql-server-analysis-services-ssas-and-the-power-bi-report-server-memory-footprint"></a>SQL Server Analysis Services (SSAS) 和 Power BI 報表伺服器記憶體使用量

Power BI 報表伺服器現在於內部裝載 SQL Server Analysis Services (SSAS)。 這不是排程重新整理特有的。 裝載 SSAS 會大幅擴充報表伺服器記憶體使用量。 AS.ini 設定檔可以在伺服器節點上使用，因此如果您熟悉 SSAS，也許會想要更新設定，包括最大記憶體限制和磁碟快取等等。如需詳細資訊，請參閱 [Analysis Services 中的伺服器屬性](https://docs.microsoft.com/sql/analysis-services/server-properties/server-properties-in-analysis-services)。

### <a name="viewing-and-interacting-with-excel-workbooks"></a>檢視 Excel 活頁簿並與之互動

Excel 和 Power BI 包含產業中特有的工具組合。 此外，它們可讓商務分析師更輕鬆地收集、塑形、分析並以視覺化方式探索其資料。 除了在入口網站中檢視 Power BI 報表之外，商務使用者現在也可以在 Power BI 報表伺服器中執行與 Excel 活頁簿相同的作業，讓他們有一個位置可以發佈和檢視其自助 Microsoft BI 內容。

我們已發佈[如何將 Office Online Server (OOS) 新增至 Power BI 報表伺服器 Preview 環境的逐步解說](excel-oos.md)。 具有大量授權帳戶的客戶可以免費從大量授權服務中心下載 OOS，並且具有僅限檢視功能。 設定之後，使用者可以檢視 Excel 活頁簿，並與之互動，而 Excel 活頁簿：

* 沒有任何外部資料來源相依性
* 即時連線至外部 SQL Server Analysis Services 資料來源
* 具有 PowerPivot 資料模型

### <a name="support-for-new-table-and-matrix-visuals"></a>新資料表和矩陣視覺效果的支援

Power BI 報表伺服器現在支援新的 Power BI 資料表和矩陣視覺效果。 若要使用這些視覺效果來建立報表，您需要 2017 年 10 月版本的已更新 Power BI Desktop 版本。 它無法與 Power BI Desktop (2017 年 6 月) 版本並存安裝。 如需最新版本的 Power BI Desktop，請在 [Power BI 報表伺服器下載分頁](https://powerbi.microsoft.com/report-server/)上選取 [進階下載選項]  。

## <a name="june-2017"></a>2017 年 6 月

* Power BI 報表伺服器正式推出 (GA)。

## <a name="may-2017"></a>2017 年 5 月

* Power BI 報表伺服器預覽版已正式運作
* 可在內部發行 Power BI 報表
  * 支援自訂視覺效果
  * **Analysis Services 即時連線**的支援必須等待更多資料來源。
  * Power BI 行動裝置應用程式已更新，以顯示 Power BI 報表伺服器裝載的 Power BI 報表
* 增強報表中使用註解的共同作業

## <a name="next-steps"></a>後續步驟

請查看下列來源掌握 Power BI 報表伺服器新功能的最新消息。

* [Microsoft Power BI 部落格](https://powerbi.microsoft.com/blog/)
* [Guy in a Cube YouTube 頻道](https://aka.ms/guyinacube)

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
