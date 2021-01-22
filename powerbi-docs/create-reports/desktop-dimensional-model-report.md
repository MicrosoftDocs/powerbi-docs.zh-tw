---
title: 教學課程：將維度模型轉變為令人驚豔的 Power BI Desktop 報表
description: 在本教學課程中，只需要 20 分鐘，就能從頭到尾將維度模型打造為美觀的報表。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: tutorial
ms.date: 01/19/2021
LocalizationGroup: Reports
ms.openlocfilehash: 03eac7aefdebb31eac353c969db2bf8810173395
ms.sourcegitcommit: 77912d4f6ef2a2b1ef8ffccc50691fe5b38ee97a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/22/2021
ms.locfileid: "98687345"
---
# <a name="tutorial-from-dimensional-model-to-stunning-report-in-power-bi-desktop"></a>教學課程：將維度模型轉變為令人驚豔的 Power BI Desktop 報表 

在本教學課程中，您只需要 45 分鐘，就能從頭到尾將維度模型打造為美觀的報表。

您任職於 AdventureWorks，您的經理想要查看最新一份銷售數字報表。 其要求的執行摘要需包含以下內容： 

- 2019 年 2 月中哪一天的銷售量最高？ 
- 公司在哪個國家/地區取得了最大成功？ 
- 公司應該繼續投資哪些產品類別及哪種轉銷商業務？ 

使用 [AdventureWorks Sales 範例 Excel 活頁簿](https://github.com/microsoft/powerbi-desktop-samples/blob/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.xlsx)，即可隨時建置這份報表。 完成後的報表看起來會像是這樣。 

:::image type="content" source="media/desktop-dimensional-model-report/adventureworks-finished-report.png" alt-text="完成的 AdventureWorks 報表。":::

想查看已完成的產品嗎？ 您也可以下載[已完成的 Power BI .pbix 檔案](https://github.com/microsoft/powerbi-desktop-samples/blob/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.pbix)。

讓我們開始吧！ 

在本教學課程中，您將了解如何：

> [!div class="checklist"]
> * 使用轉換來準備資料
> * 建置包含標題、三種視覺效果和交叉分析篩選器的報表
> * 將報表發佈至 Power BI 服務並與同事共用

## <a name="prerequisites"></a>必要條件

- 在開始之前，您需要[下載 Power BI Desktop](../fundamentals/desktop-get-the-desktop.md)。 
- 如果打算將報表發佈至 Power BI 服務且尚未註冊，請[註冊免費試用](../fundamentals/service-self-service-signup-for-power-bi.md)。 

## <a name="get-data-download-the-sample"></a>取得資料：下載範例 

1. 下載 [AdventureWorks Sales 範例 Excel 活頁簿](https://github.com/microsoft/powerbi-desktop-samples/blob/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.xlsx)。 

1. 開啟 Power BI Desktop。 

1. 在 [常用] 功能區的 [資料] 區段中，選取 [Excel]。 

1. 巡覽至儲存範例活頁簿的位置，然後選取 [開啟]。 

## <a name="prepare-your-data"></a>準備資料 

在 [導覽器] 窗格中，您可選擇 [轉換] **   或 [載入] **   資料。 [導覽器] 可供預覽資料，以便確認資料範圍是否正確。 數值資料類型會以斜體顯示。 在本教學課程中，我們要先轉換資料再加以載入。

選取所有資料表，然後選擇 [轉換資料] **** 。 請務必不要選取標記有 *_data* 的工作表。 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-load-tables.png" alt-text="在 [導覽器] 中載入資料表。":::

請檢查資料行資料類型是否與下表中的類型相符。 若要讓 Power BI 為您偵測資料類型，請選取查詢，然後選取一或多個資料行。 在 [ **轉換** ] 索引標籤上，選取 [偵測 **資料類型**]。 若要對偵測到的資料類型進行任何變更，請在 [ **首頁** ] 索引標籤上選取 [ **資料類型**]，然後從資料表中選取適當的資料類型。

:::image type="content" source="media/desktop-dimensional-model-report/power-query-change-data-types.png" alt-text="檢查資料行的資料類型。":::


|查詢  |資料行  |資料類型  |
|---------|---------|---------|
|客戶  |  CustomerKey | 整數 |
|Date | DateKey |    整數     |
|     | Date | Date      |
|     | MonthKey  | 整數 |
|產品  | ProductKey | 整數  | 
|     | Standard Cost | 十進位數字  | 
|     | List Price | 十進位數字  | 
|Reseller  | ResellerKey | 整數  | 
|Sales   | SalesOrderLineKey | 整數  | 
|     | ResellerKey  | 整數  | 
|     | CustomerKey | 整數  | 
|     | ProductKey  | 整數  | 
|     | OrderDateKey | 整數  | 
|     | DueDateKey  | 整數  | 
|     | ShipDateKey | 整數  | 
|     | SalesTerritoryKey | 整數  | 
|     | Order Quantity   | 整數  | 
|     | 單價  | 十進位數字  | 
|     | 擴充量  | 十進位數字  | 
|     | Unit Price Discount Pct | 百分比  | 
|     | 產品標準成本 | 十進位數字  | 
|     | 產品總成本 | 十進位數字  | 
|     | 銷售量 | 十進位數字  | 
| SalesTerritory  | SalesTerritoryKey | 整數  | 
|  SalesOrder   |  SalesOrderLineKey | 整數  | 

返回 [常用] ****   索引標籤，選取 [關閉並套用] **** 。 

:::image type="content" source="media/desktop-dimensional-model-report/power-query-close-and-apply.png" alt-text="Power Query [關閉並套用] 按鈕。":::

## <a name="model-your-data"></a>製作資料模型 

您載入的資料就快準備好用於報表了。 讓我們檢查資料模型，並進行一些變更。 

選取左側的 [模型檢視]。 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-select-model-view.png" alt-text="選取 Power BI Desktop 中的模型檢視":::。

您的資料模型應看似下圖，每個資料表都包含在方塊中。 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-data-model-1.png" alt-text="由此資料模型開始。":::

### <a name="create-relationships"></a>建立關聯性

此模型是您會在資料倉儲中看到的典型「星型結構描述」：其外觀與星型相當類似。 星型的中心是事實資料表， 而周圍的資料表稱為維度資料表，其與事實資料表具有關聯性。 事實資料表包含銷售交易的數值資訊，例如銷售額與產品標準成本。 這些維度會提供內容，讓您得以分析其他項目： 

- 已銷售哪些產品... 
- 銷售給哪些客戶... 
- 經由哪些轉銷商... 
- 在哪個銷售領域。  

如果您仔細看，就會發現除了 Date 資料表以外，所有維度資料表都與事實資料表具有關聯性。 現在讓我們為 Date 資料表新增一些關聯性。 將 Date 資料表的 DateKey 拖曳至 Sales 資料表的 OrderDateKey。 您現在已經在 Date 與 Sales 之間建立了所謂的「一對多」關聯性，如下圖線條兩端 **1** 與星號 * (即多數) 所示。  

此為「一對多」關聯性，因為指定日期會有一或多筆銷售訂單。 如果每個日期只有一筆銷售訂單，則會是「一對一」關聯性。 線條中間的小箭號表示「交叉篩選的方向」。 這表示您可使用 Date 資料表中的值來篩選 Sales 資料表，以便您依關聯性分析銷售訂單的下單日期。  

:::image type="content" source="media/desktop-dimensional-model-report/desktop-date-sales-relationship.png" alt-text="Sales 和 Date 資料表之間的關聯性。":::

Sales 資料表包含更多與銷售訂單日期相關的詳細資訊，例如「到期日」和「出貨日期」。 讓我們拖曳下列欄位來為 Date 資料表新增另外兩個關聯性： 

- 拖曳 DateKey 至 DueDateKey 
- 拖曳 DateKey 至 ShipDateKey 
    
:::image type="content" source="media/desktop-dimensional-model-report/desktop-date-sales-relationships-done.png" alt-text="Sales 與 Date 資料表之間的三個關聯性。":::

您會注意到 OrderDateKey 上的第一個關聯性為作用中 (以實線表示)。 其他兩個關聯性則為非作用中 (以虛線表示)。 Power BI 預設會使用作用中關聯性來建立銷售與日期的關聯性。 因此，SalesAmount 的總和是依訂單日期來計算，而非「到期日」或「出貨日期」。 您可影響此行為。 請參閱本教學課程稍後的[為報表加分：撰寫 DAX 量值](#extra-credit-write-a-measure-in-dax)。

### <a name="hide-key-columns"></a>隱藏索引鍵資料行

典型的星型結構描述包含數個索引鍵，用於維持事實與維度之間的關聯性。 一般而言，我們並不想在報表中使用任何索引鍵資料行。 讓我們隱藏索引鍵資料行，讓欄位清單顯示較少的欄位，以便資料模型更容易使用。 

檢視所有資料表，並隱藏所有名稱結尾為 *Key* 的資料行： 

選取資料行旁邊的 **眼睛** 圖示，然後選擇 [在報表檢視中隱藏]。

:::image type="content" source="media/desktop-dimensional-model-report/desktop-column-visible.png" alt-text="具有眼睛圖示的可見資料行。":::

您也可以在 [屬性] 窗格中，選取資料行旁邊的 **眼睛** 圖示。

經隱藏欄位會具有在眼睛上加上了一條斜線的圖示。 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-column-hidden.png" alt-text="具有隱藏眼睛圖示的欄位。":::
 
請隱藏下列欄位。

|資料表  |資料行  |
|---------|---------|
|客戶  | CustomerKey |
|Date     | DateKey |
|     | MonthKey |
|產品     | ProductKey  |
|Reseller   | ResellerKey  |
|Sales     | CustomerKey  |
|     | DueDateKey |
|     | OrderDateKey |
|     | ProductKey |
|     | ResellerKey        |
|     | SalesOrderLineKey        |
|     | SalesTerritoryKey        |
|     | ShipDateKey        |
| SalesOrder    | SalesOrderLineKey |
| SalesTerritory  | SalesTerritoryKey |

您的資料模型現在看起來應該類似以下資料模型，其 Sales 資料表與其他所有資料表皆具有關聯性，且隱藏了所有索引鍵欄位： 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-data-model-2-hidden-columns.png" alt-text="隱藏了索引鍵資料行的資料模型。":::

### <a name="create-hierarchies"></a>建立階層

因為隱藏了資料行，所以現在可更輕鬆地使用資料模型，我們可新增幾個「階層」，讓模型更容易使用。 階層可供更輕鬆地在群組之間巡覽。 例如，城市包含於州或省之中，而州或省則包含於國家或地區之中。 

建立下列階層。 

1. 以滑鼠右鍵按一下階層中的最高層級，或位於分類最頂端的欄位，然後選擇 [建立階層]。 

1. 在 [屬性] 窗格中，設定階層的 [名稱]，並設定層級。 

1. 接著 [套用層級變更]。 

    :::image type="content" source="media/desktop-dimensional-model-report/desktop-hierarchy-properties.png" alt-text="階層的 [屬性] 窗格。":::

您也可以在新增階層後，在 [屬性] 窗格中為階層的層級重新命名。 您必須在 Date 資料表中，為會計階層的年度與季度層級重新命名。 

以下是所需建立的階層。

| 資料表 |階層名稱 |等級  |
|---------|---------|---------|
|客戶     | [地理位置]   | 國家/地區  |
|     | | State-Province  |
|     |         | City |
|Row4     |         | 郵遞區號 |
|Row5     |         | 客戶   |
|Date     | 會計  | 年度 (會計年度)  |
|     |         | 季度 (會計季度) |
|     |         | 月 |
|     |         | Date |
| Product  | 產品 | 類別 |
|     |         | 子類別 |
|     |         | 型號 |
|     |         | Product |
| Reseller   | [地理位置] | 國家/地區 |
|     |         | State-Province |
|     |         | City  |
|     |         | 郵遞區號  |
|     |         | Reseller |
| SalesOrder  | 銷售訂單 | Sales Order |
|     |         | 銷售單明細行 |
| SalesTerritory    | 銷售領域 | Group |
|     |         | Country |
|     |         | 區域 |
 
您的資料模型現在看起來應該像下列資料模型， 其具有相同資料表，但每個維度資料表都包含一個階層： 

:::image type="content" source="media/desktop-dimensional-model-report/desktop-data-model-3-added-hierarchies.png" alt-text="維度資料表包含階層的資料模型。":::

### <a name="rename-tables"></a>重新命名資料表

重新命名 [屬性] 窗格中的下列資料表以完成模型： 

|舊資料表名稱  |新資料表名稱  |
|---------|---------|
|SalesTerritory    |  Sales Territory   |
|SalesOrder  |  Sales Order   |

這是必要步驟，因為 Excel 資料表名稱不能包含空格。

現在您已完成最終的資料模型。

:::image type="content" source="media/desktop-dimensional-model-report/desktop-data-model-4-renamed-tables.png" alt-text="完成的資料模型，且已重新命名資料表。":::

## <a name="extra-credit-write-a-measure-in-dax"></a>為報表加分：撰寫 DAX 量值 

使用 DAX 公式語言撰寫「量值」，對於資料模型化而言相當有幫助。 [在 Power BI 文件中，DAX 是一門大學問](/dax/)。 現在，我們要撰寫基本量值，依據銷售訂單上的到期日 (而非預設的訂單日期) 計算總銷售額。 此量值會使用 [USERELATIONSHIP 函式](/dax/userelationship-function-dax)，在量值範圍內啟動 DueDate 上 Sales 與 Date 之間的關聯性， 然後使用 [CALCULATE](/dax/calculate-function-dax) 加總該範圍中的銷售金額。

1. 選取左側的 [資料檢視]。 

    :::image type="content" source="media/desktop-dimensional-model-report/desktop-open-data-view.png" alt-text="選取左側的 [資料檢視]。":::

1. 在 [欄位] 清單中選取 Sales 資料表。

    :::image type="content" source="media/desktop-dimensional-model-report/desktop-select-sales-table.png" alt-text="在 [欄位] 清單中選取 Sales 資料表。":::

1. 在 [常用] ****   功能區中，選取 [新增量值] **** 。 

1. 選取或鍵入此量值，以依據銷售訂單上的到期日 (而非預設的訂單日期) 來計算總銷售額：

    ```dax
    Sales Amount by Due Date = CALCULATE(SUM(Sales[Sales Amount]), USERELATIONSHIP(Sales[DueDateKey],'Date'[DateKey]))
    ```

1. 選取核取記號加以認可。 

    :::image type="content" source="media/desktop-dimensional-model-report/desktop-adding-a-dax-measure.png" alt-text="選取核取記號以認可 DAX 量值。":::

## <a name="build-your-report"></a>建立報表 

既然已將資料模型化，您現在可開始建立報表。 前往 [報表檢視]。 在右側的 [欄位] 窗格中，您會看到所建立資料模型的欄位。

讓我們一次使用一個視覺效果來完成建置報表。 

:::image type="content" source="media/desktop-dimensional-model-report/adventureworks-finished-report-with-numbers.png" alt-text="完成的報表，每個視覺效果均帶有數字標記":::

### <a name="visual-1-add-a-title"></a>視覺效果 1：新增標題 

1. 在 [插入] 功能區中，選取 [文字方塊]。 鍵入 "Executive Summary – Finance Report" (執行摘要 - 銷售報表)。 

1. 選取您輸入的文字。 將字型大小設定為 **20** 及 **粗體**。 

    :::image type="content" source="media/desktop-dimensional-model-report/executive-summary-text-box.png" alt-text="將執行摘要文字格式化。":::

1. 在 [視覺效果] 窗格中，將 [背景] 切換為 [關閉]。 

1. 將方塊大小調整為一行。 

### <a name="visual-2-sales-amount-by-date"></a>視覺效果 2：依日期的銷售額 

下一步，您要建立折線圖來查看哪一個月份和年份具有最高銷售額。

1. 從 [欄位] 窗格，將 **Sales Amount** 欄位從 **Sales** 資料表拖曳至報表畫布上的空白區域。 根據預設，Power BI 會顯示直條圖，並包含 Sales Amount 資料行。 

1. 將 **Month** 欄位從 **Date** 資料表中的 **會計** 階層拖曳到直條圖。 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-year.png" alt-text="建立包含每年度資料行的直條圖。":::

1. 在 [視覺效果] 窗格的 [欄位] 區段中，移除 **Year** 與 **Quarter** 欄位： 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-year-remove-year-and-quarter.png" alt-text="在 [視覺效果] 窗格的 [欄位] 區段中，移除 Year 與 Quarter 欄位。":::

1. 在 [視覺效果] 窗格中，將視覺效果類型變更為 [區域圖]。 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-year-change-to-area.png" alt-text="將直條圖變更為區域圖。":::

1. 如果已在稍早的為報表加分中新增 DAX 量值，請一併將其新增至 [值]。 
1. 依序開啟 [格式] 窗格和 [資料色彩]，然後將 [依截止日期的銷售額] 變更為對比度較高的色彩，例如紅色。

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-year-add-DAX-measure.png" alt-text="[依到期日的銷售額] 的區域圖。":::

    如您所見，依到期日的銷售額會稍稍低於銷售額。 這證明其使用於 Sales 與 Date 資料表之間使用 DueDateKey 的關聯性。 

 

### <a name="visual-3-order-quantity-by-reseller-country"></a>視覺效果 3：依轉售商國家/地區的訂單數量 

現在，我們要建立地圖來查看轉售商在哪個國家/地區有最高的訂單數量。

1. 從 [欄位] 窗格中，將 **Country-Region** 欄位從 **Reseller** 資料表拖曳至報表畫布上的空白區域。 Power BI 會建立地圖。 

1. 將 **Order Quantity** 欄位從 **Sales** 資料表拖曳到地圖上。 請確定 **Country-Region** 位於 [位置] 中，且 **Order Quantity** 也位於 [大小] 中。 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-order-quantity-by-reseller-country.png" alt-text="依國家/地區的訂單數量地圖。":::

### <a name="visual-4-sales-amount-by-product-category-and-reseller-business-type"></a>視覺效果 4：依產品類別與轉售商業務類型的銷售額 

接下來，我們要建立直條圖，調查哪些產品是由哪種轉銷商業務所銷售。

1. 將所建立的兩個圖表拖曳至畫布上半部以並排顯示。 為畫布左側預留一些空間。 

1. 選取報表畫布下半部的空白區域。 

1. 在 [欄位] 窗格中，從 **Sales** 選取 **Sales Amount**、從 **Product** 選取 **Product Category**，然後從 **Reseller** 選取 **Business Type**。
    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-product-category-field-well.png" alt-text="檢查 [類別目錄] 和 [商務類型] 是在 [資料列]，而 [銷售金額] 是 [值]":::
    
    Power BI 會自動建立群組直條圖。 將視覺效果變更為 [矩陣]： 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-product-category-change-to-matrix.png" alt-text="將群組直條圖變更為矩陣。":::

1. 在已選取矩陣的情況下，在 [篩選] 窗格中，於 **Business Type** 下 [選取所有]，然後清除 [不適用] 方塊。 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-product-category-filter-not-applicable.png" alt-text="篩選出不適用的業務類型。":::

1. 拖曳矩陣，使其寬度足以填滿上方兩個圖表下的空間。 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-product-category-increase-width.png" alt-text="加寬矩陣以填滿報表。":::

1. 在矩陣的 [格式化] 窗格中，開啟 [條件式格式設定] 區段，然後開啟 [資料橫條]。 選取 [進階控制]，然後為正值橫條設定較淡的色彩。 選取 [確定]。 

1. 增加 [銷售量] 資料行的寬度，使其涵蓋整個區域，方法是拖曳矩陣。

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-amount-by-product-category-add-databars.png" alt-text="包含 Sales Amount 資料橫條的矩陣。":::

看起來自行車的整體銷售額較高，而加值型轉銷商賣出最多輛自行車，緊接在後的則是大型零售商店。 在零件方面，大型零售商店銷售的銷售量則高於加值型轉銷商。 

 

### <a name="visual-5-fiscal-calendar-slicer"></a>視覺效果 5：會計日曆交叉分析篩選器 

交叉分析篩選器是一項很重要的工具，可將報表頁面上視覺效果篩選為特定的選取項目。 在本案例中，我們可建立交叉分析篩選器，將範圍縮小至每月、每季和每年的績效。 

1. 在 [欄位] 窗格中，從 **Date** 資料表中選取 [會計] 階層，然後將其拖曳至畫布左邊的空白區域。 

1. 在 [視覺效果] 窗格中選擇 [交叉分析篩選器]。 

    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-add-fiscal-calendar-slicer.png" alt-text="新增報表銷售日曆交叉分析篩選器。":::

1. 在 [視覺效果] 窗格的 [欄位] 區段中，移除 **Quarter** 與 **Date**，只留下 **Year** 與 **Month**。 
 
    :::image type="content" source="media/desktop-dimensional-model-report/report-sales-add-fiscal-calendar-slicer-remove-quarter-and-date.png" alt-text="從會計交叉分析篩選器中移除 Quarter 與 Date。":::

現在，如果您的經理只想查看特定月份資料，即可使用交叉分析篩選器在年份或每年的特定月份之間進行切換。 

## <a name="extra-credit-format-the-report"></a>為報表加分：將報表格式化 

如果想要用一些清爽的格式來讓報表變得更加精緻，以下有幾個簡單的步驟。 

### <a name="theme"></a>佈景主題 

- 在 [檢視] ****   功能區上，選取 [主題]，然後將主題變更為 [主管] **** 。 

    :::image type="content" source="media/desktop-dimensional-model-report/formatting-report-change-theme.png" alt-text="選擇 [主管] 主題。":::

### <a name="spruce-up-the-visuals"></a>裝飾視覺效果 

在 [視覺效果] 窗格的 [格式] ****   索引標籤上進行下列變更。 

:::image type="content" source="media/desktop-dimensional-model-report/formatting-report-formatting-pane.png" alt-text="[視覺效果] 窗格中 [格式] 索引標籤的螢幕擷取畫面。":::

**視覺效果 2：依日期的銷售額**

1. 選取 [Visual 2, Sales Amount by Date]。 
1. 在 [標題] ****   區段中，如果未新增 DAX 量值，則請將 [標題] **** 文字變更為 "Sales Amount by Order Date" (依訂單日期的銷售額)。 

    如果已新增 DAX 量值，請將 [標題文字] 變更為 "Sales Amount by Order Date / Due Date" (依訂單日期/到期日的銷售額)。 

1. 將 [文字] 大小設定為 [16 pt] **** 。 
1. 將 [陰影] ****   切換為 [開啟] **** 。 

**視覺效果 3：依轉售商國家/地區的訂單數量**

1. 選取 [Visual 3, Order Quantity by Reseller Country]。 
1. 在 [地圖樣式] ****   區段中，將 [主題] ****   變更為 [灰階] **** 。 
1. 在 [標題] ****   區段中，將 [標題文字] 變更為 "Order Quantity by Reseller Country" (依轉售商國家/地區的訂單數量)。
1. 將 [文字大小]  設定為 [16 pt] **** 。 
1. 將 [陰影] ****   切換為 [開啟] **** 。  

**視覺效果 4：依產品類別與轉售商業務類型的銷售額**

1. 選取 [Visual 4, Sales Amount by Product Category and Reseller Business Type]。 
1. 在 [標題] ****   區段中，將 [標題文字] 變更為 "Sales Amount by Product Category and Reseller Business Type" (依產品類別與轉售商業務類型的銷售額)。
1. 將 [文字大小]  設定為 [16 pt] **** 。 
1. 將 [陰影] ****   切換為 [開啟] **** 。 

**視覺效果 5：會計日曆交叉分析篩選器**

1. 選取 [Visual 5, Fiscal calendar slicer]。
1. 在 [選取控制項] ****   區段中，將 [顯示「全選」選項] **** 切換為 [開啟] **** 。 
1. 在 [交叉分析篩選器標題] ****   區段中，將 [文字大小]  設定為 [16 pt] **** 。 

### <a name="add-a-background-shape-for-the-title"></a>新增標題的背景圖形 

1. 在 [插入] **** 功能區上，選取 [圖形]  ****  > [矩形] **** 。 
1. 將圖形放在頁面頂端，並延展為符合頁面寬度和標題的高度。 
1. 在 [格式化圖形] ****   窗格的 [行] ****   區段中，將 [透明度] ****   變更為 [100%] **** 。 
1. 在 [填滿] ****   區段中，將 [填滿色彩] ****   變更為 [主題色彩 5 #6B91C9 (藍色)] **** 。 
1. 在 [格式] ****   索引標籤上，選取 [下移一層] ****  >[移到最下層] **** 。 
1. 選取視覺效果 1 中的文字 (即標題)，然後將 [字型色彩] 變更為 [白色] **** 。 

## <a name="finished-report"></a>已完成的報表 

選取交叉分析篩選器中的 [FY2019]。

:::image type="content" source="media/desktop-dimensional-model-report/adventureworks-finished-report.png" alt-text="最後完成的報表。":::

總而言之，這份報表能夠回答經理最關心的問題： 

- 2019 年 2 月中哪一天的銷售量最高？ 
    2 月 25 日，銷售額為美金 $253,915.47 元。 

- 公司在哪個國家/地區取得了最大成功？ 
    美國，其訂單數量為 132,748 件。 

- 公司應該繼續投資哪些產品類別及哪種轉銷商業務？ 
    公司應該繼續投資自行車類別，以及加值型轉銷商與大型零售商店轉銷商等業務。 

## <a name="save-your-report"></a>儲存報表 

- 在 [檔案] ****   功能表上，選取 [儲存] **** 。 


## <a name="publish-to-the-power-bi-service-to-share"></a>發佈至 Power BI 服務與其他人共用 

若要與經理和同事共用報表，請將報表發佈至 Power BI 服務。 當與擁有 Power BI 帳戶的同事共用時，其可與報表互動，但無法儲存變更。

1. 在 Power BI Desktop 的 [常用] ****   功能區中，選取 [發佈] **** 。 
1. 您可能需要登入 Power BI 服務。 如果還沒有帳戶，請 [註冊免費試用版](https://app.powerbi.com/signupredirect?pbi_source=web)。 

1. 在 Power BI 服務 > [選取] **** 中，選取目的地 (例如我的工作區)。 

1. 選取 [在 Power BI 中開啟 <檔案名稱>] **** 。 已完成的報表會隨即在瀏覽器中開啟。 

1. 選取報表頂端的 [共用] ****  ，與其他人共用報表。

## <a name="next-steps"></a>後續步驟 

- 下載[已完成的 Power BI .pbix 檔案](https://github.com/microsoft/powerbi-desktop-samples/blob/main/AdventureWorks%20Sales%20Sample/AdventureWorks%20Sales.pbix)
- 深入了解 [Power BI Desktop 中的 DAX 與資料模型](/learn/modules/dax-power-bi-models/)

有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)
