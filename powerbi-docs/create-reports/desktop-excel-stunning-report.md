---
title: 教學課程：將 Excel 活頁簿轉變為令人驚豔的 Power BI Desktop 報表
description: 本教學課程會說明如何使用 Excel 活頁簿快速建立令人驚豔的報表。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: tutorial
ms.date: 10/13/2020
LocalizationGroup: Data from files
ms.openlocfilehash: b984c0f6ebee6cdcc9982956701f3a112be74ab7
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96413188"
---
# <a name="tutorial-from-excel-workbook-to-stunning-report-in-power-bi-desktop"></a>教學課程：將 Excel 活頁簿轉變為令人驚豔的 Power BI Desktop 報表

在本教學課程中，只需要短短 20 分鐘就能打造出美觀的報表！ 

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-excel-formatted-report.png" alt-text="已完成 Power BI 報表的螢幕擷取畫面。"::: 

您的經理想要查看最新一份銷售數字報表。 其要求執行摘要需包含以下內容： 

- 哪一個月份和年份有最大收益？ 
- 公司在哪個地區取得了最大成功 (依國家/地區)？ 
- 公司應該繼續投資哪項產品及哪個市場？ 

使用範例財務活頁簿即可立即建置這份報表。 完成後的報表看起來會像是這樣。 讓我們開始吧！ 

在本教學課程中，您將了解如何：

> [!div class="checklist"]
> * 以兩種不同的方式下載範例資料
> * 使用轉換來準備資料
> * 建置包含標題、三種視覺效果和交叉分析篩選器的報表
> * 將報表發佈至 Power BI 服務並與同事共用

## <a name="prerequisites"></a>必要條件

- 在開始之前，您需要[下載 Power BI Desktop](https://powerbi.microsoft.com/desktop/)。
- 如果打算將報表發佈至 Power BI 服務且尚未註冊，請[註冊免費試用](https://app.powerbi.com/signupredirect?pbi_source=web)。

## <a name="get-data"></a>取得資料 

您可以使用兩種方法之一來取得此教學課程的資料。

### <a name="get-data-in-power-bi-desktop"></a>在 Power BI Desktop 中取得資料

當您開啟 Power BI Desktop 時，從空白畫布選取 [嘗試範例資料集]。

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-desktop-canvas-sample-dataset.png" alt-text="畫布上 [嘗試範例資料集] 的螢幕擷取畫面。"::: 

如果您已從 Power BI Desktop 登陸此教學課程，請繼續並選擇 [載入資料]。

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-two-ways-load-data.png" alt-text="[使用範例資料的兩種方式] > [載入資料] 的螢幕擷取畫面。":::

### <a name="download-the-sample"></a>下載範例

您也可以直接下載範例活頁簿。 

1. 下載[財務範例 Excel 活頁簿](https://go.microsoft.com/fwlink/?LinkID=521962)。
1. 開啟 Power BI Desktop。
1. 在 [常用] 功能區的 [資料] 區段中，選取 [Excel]。
1. 巡覽至儲存範例活頁簿的位置，然後選取 [開啟]。

## <a name="prepare-your-data"></a>準備資料 

在 [導覽器] 中，您可選擇「轉換」或「載入」資料。 [導覽器] 可供預覽資料，以便確認資料範圍是否正確。 數值資料類型會以斜體顯示。 如果需要進行變更，請在載入前轉換資料。 為了讓視覺效果更容易供之後閱讀，我們現在想要轉換資料。 當執行每次轉換時，您會看見轉換新增至 [套用的步驟] 中 [查詢設定] 底下的清單 

1. 選取 [Financials] 資料表，然後選擇 [轉換資料]。 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-financial-navigator.png" alt-text="Power BI 導覽器內財務範例資料的螢幕擷取畫面。"::: 

1. 選取 [Units Sold] 資料行。 在 [常用] 索引標籤上，選取 [資料類型]，然後選取 [整數]。 選擇 [取代目前的] 來變更資料行類型。 

    使用者最常執行的資料清除步驟就是變更資料類型。 在此範例中，售出單位數為十進位格式。 但 0.2 或 0.5 的售出單位數並沒有什麼意義，是吧？ 因此我們要將其變更為整數。 

    :::image type="content" source="media/desktop-excel-stunning-report/power-query-whole-number.png" alt-text="將十進位數變更為整數的螢幕擷取畫面。"::: 

1. 選取 [Segment] 資料行。 在 [轉換] 索引標籤上，選取 [格式]，然後選取 [大寫]。

    我們也想要讓市場區隔在圖表中更加明顯。 因此我們要將 [Segment] 資料行格式化。 

     :::image type="content" source="media/desktop-excel-stunning-report/power-query-upper-case.png" alt-text="將小寫變更為大寫標題的螢幕擷取畫面。":::

1. 現在我們要將 [Month Name] 的資料行名稱縮短為 [Month]。 按兩下 [Month Name] 資料行，然後重新命名為 [Month]。  

     :::image type="content" source="media/desktop-excel-stunning-report/power-query-month-name.png" alt-text="縮短資料行名稱的螢幕擷取畫面。":::

1. 在 [Product] 資料行中，選取下拉式清單並取消勾選 [Montana] 的方塊。 

     我們知道 Montana 產品已於上個月終止，因此想要在報表中篩選掉此資料，以避免產生混淆。 

     :::image type="content" source="media/desktop-excel-stunning-report/power-query-montana.png" alt-text="刪除 Montana 值的螢幕擷取畫面。":::

1. 您會看見每次轉換皆已新增至 [套用的步驟] 中 [查詢設定] 底下的清單。

    :::image type="content" source="media/desktop-excel-stunning-report/power-query-applied-steps.png" alt-text="已套用步驟清單的螢幕擷取畫面。":::

1. 回到 [常用] 索引標籤，選取 [關閉並套用]。 我們幾乎已經完成建置報表所需準備的資料了。 

    您有在 [欄位] 清單中看到 Sigma 符號嗎？ Power BI 偵測到這些欄位為數值， 並同時以行事曆符號標示出日期欄位。

     :::image type="content" source="media/desktop-excel-stunning-report/power-bi-fields-list-sigmas-date.png" alt-text="具有數值欄位和日期欄位的 [欄位] 清單其螢幕擷取畫面。":::

### <a name="extra-credit-write-a-measure-in-dax"></a>為報表加分：撰寫 DAX 量值

使用 *DAX* 公式語言撰寫「量值」，對於資料模型化而言相當有幫助。 在 Power BI 文件中，DAX 是一門大學問。 現在，我們要撰寫基本量值，並聯結兩個資料表。 

1. 選取左側的 [資料檢視]。 
 
    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-data-view.png" alt-text="資料檢視圖示的螢幕擷取畫面。":::

1. 從 [常用] 功能區中選取 [新增資料表]。 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-new-table.png" alt-text="新增資料表圖示的螢幕擷取畫面。":::

1. 鍵入此量值，以產生介於 2013 年 1 月 1 日到 2014 年 12 月 31 日之間的 [Calendar] 資料表。  

    `Calendar = CALENDAR(DATE(2013,01,01),Date(2014,12,31))` 

2. 選取核取記號加以認可。

     :::image type="content" source="media/desktop-excel-stunning-report/power-bi-dax-expression.png" alt-text="DAX 運算式的螢幕擷取畫面。":::

1. 現在選取左側的 [模型檢視]。 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-model-view.png" alt-text="模型檢視圖示的螢幕擷取畫面。":::

1. 將 [Date] 欄位從 [Financials] 資料表拖曳至 [行事曆] 資料表中的 [Date] 欄位以聯結資料表，在兩者之間建立「關聯性」。  

     :::image type="content" source="media/desktop-excel-stunning-report/power-bi-date-relationship.png" alt-text="[Date] 欄位關聯性的螢幕擷取畫面。":::

## <a name="build-your-report"></a>建立報表 

既然已轉換並載入資料，現在即可開始建立報表。 在右側的 [欄位] 窗格中，您會看到所建立資料模型的欄位。 

讓我們一次使用一個視覺效果來完成建置報表。 

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-report-by-numbers.png" alt-text="報表中所有項目的螢幕擷取畫面，按編號。":::

### <a name="visual-1-add-a-title"></a>視覺效果 1：新增標題 

1. 在 [插入] 功能區中，選取 [文字方塊]。 鍵入 "Executive Summary – Finance Report" (執行摘要 - 財務報表)。 
1. 選取您輸入的文字。 將字型大小設為 20 及粗體。 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-title-executive-summary.png" alt-text="格式化標題的螢幕擷取畫面。":::

1. 在 [視覺效果] 窗格中，將 [背景] 切換為 [關閉]。 
1. 將方塊大小調整為一行。 

### <a name="visual-2-profit-by-date"></a>視覺效果 2：依日期的收益 

現在，您要建立折線圖來查看哪一個月份和年份具有最高收益。 

1. 從 [欄位] 窗格中，將 [Profit] 欄位拖曳至報表畫布上的空白區域。 根據預設，Power BI 會顯示直條圖，並包含 [Profit] 資料行。 
1. 將 [Date] 欄位拖曳至相同的視覺效果。 Power BI 會更新直條圖，以顯示兩年的收益。

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-column-year.png" alt-text="收益直條圖的螢幕擷取畫面。":::

1. 在 [視覺效果] 窗格的 [欄位] 區段中，選取 [軸] 值中的下拉式功能表。 將 [Date] 的 [日期階層] 變更為 [日期]。

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-date-hierarchy.png" alt-text="將 [日期階層] 變更為 [日期] 的螢幕擷取畫面。":::

    Power BI 會更新直條圖，以顯示每個月的收益。

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-column-month.png" alt-text="依月份的直條圖螢幕擷取畫面。":::

1. 在 [視覺效果] 窗格中，將視覺效果類型變更為 [折線圖]。 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-profit-date-line-chart.png" alt-text="將直條圖變更為橫條圖的螢幕擷取畫面。":::

    現在即可輕鬆看到 2014 年 12 月具有最大收益。

### <a name="visual-3-profit-by-country"></a>視覺效果 3：依國家/地區分類的收益 

建立地圖以查看哪一個國家/地區擁有最高收益。

1. 從 [欄位] 窗格中，將 [Country] 欄位拖曳至報表畫布上的空白區域，以建立地圖。
1. 將 [Profit] 欄位拖曳至地圖。

    Power BI 會建立地圖視覺與泡泡，代表每個地點相對的收益。 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-map-visual.png" alt-text="建立地圖圖表的螢幕擷取畫面。":::

    歐洲的表現似乎比北美洲好。 

### <a name="visual-4-sales-by-product-and-segment"></a>視覺效果 4：依產品和區段的銷售額 

建立橫條圖，以決定要投資的公司和市場。

1. 將所建立的兩個圖表拖曳至畫布上半部以並排顯示。 為畫布左側預留一些空間。 
1. 選取報表畫布下半部的空白區域。 

1. 在 [欄位] 窗格中，選取 [Sales]、[Product] 及 [Segment] 欄位。 

    Power BI 會自動建立群組直條圖。 

1. 拖曳圖表，使其寬度足以填滿上方兩個圖表下的空間。

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-clustered-column-chart.png" alt-text="群組直條圖的螢幕擷取畫面。":::

    公司似乎應該繼續投資 Paseo 產品，並以小型企業和政府部門作為目標。  

### <a name="visual-5-year-slicer"></a>視覺效果 5：年交叉分析篩選器 

交叉分析篩選器是一項很重要的工具，可將報表頁面上視覺效果篩選為特定的選取項目。 在此範例中，我們可建立交叉分析篩選器，將範圍縮小至每月和每年的績效。  

1. 在 [欄位] 窗格中，選取 [Date] 欄位，並拖曳至畫布左側的空白區域。 
2. 在 [視覺效果] 窗格中選擇 [交叉分析篩選器]。 
3. 在 [視覺效果] 窗格的 [欄位] 區段中，選取 [欄位] 中的下拉式功能表。 移除 [季] 和 [日]，只保留 [年] 和 [月]。 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-date-hierarchy-trim.png" alt-text="變更 [日期] 階層的螢幕擷取畫面。":::

4. 展開每一年並調整視覺效果的大小，以顯示所有月份。

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-hierarchy-date-slicer.png" alt-text="日日期階層交叉分析篩選器的螢幕擷取畫面。":::

現在，如果經理只想查看 2013 年的資料，您可使用交叉分析篩選器在年份或每年的特定月份之間進行切換。 

### <a name="extra-credit-format-the-report"></a>為報表加分：將報表格式化

如果想要用一些清爽的格式來讓報表變得更加精緻，以下有幾個簡單的步驟。 

**佈景主題**

- 在 [檢視] 功能區上，將主題變更為 [高階主管]。  

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-theme-executive.png" alt-text="選取 [高階主管] 主題的螢幕擷取畫面。"::: 

**裝飾視覺效果** 

在 [視覺效果] 窗格的 [格式] 索引標籤上進行下列變更。

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-format-tab-visualizations.png" alt-text="[視覺效果] 窗格中 [格式] 索引標籤的螢幕擷取畫面。":::

1. 選取 [視覺效果 2]。 在 [標題] 區段中，將 [標題文字] 變更為 "Profit by Month and Year" (月收益與年收益) 並將 [文字大小] 變更為 [16 pt]。 將 [陰影] 切換為 [開啟]。 

1. 選取 [視覺效果 3]。 在 [地圖樣式] 區段中，將 [主題] 變更為 [灰階]。 在 [標題] 區段中，將標題的 [文字大小] 變更為 [16 pt]。 將 [陰影] 切換為 [開啟]。

1. 選取 [視覺效果 4]。 在 [標題] 區段中，將標題的 [文字大小] 變更為 [16 pt]。 將 [陰影] 切換為 [開啟]。

1. 選取 [視覺效果 5]。 在 [選取控制項] 區段中，將 [顯示「全選」選項] 切換為 [開啟]。 在 [交叉分析篩選器標題] 區段中，將 [文字大小] 增加至 [16 pt]。 

**新增標題的背景圖形**

1. 在 [插入] 功能區中，選取 [圖形] > [矩形]。 將圖形放在頁面頂端，並延展為符合頁面寬度和標題的高度。 
1. 在 [設定圖形格式] 窗格的 [行] 區段中，將 [透明度] 變更為 [100%]。 
1. 在 [填滿] 區段中，將 [填滿色彩] 變更為 [主題色彩 5 #6B91C9] (藍色)。 

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-theme-color-5.png" alt-text="主題色彩 5 的螢幕擷取畫面。":::

1. 在 [格式] 索引標籤上，選取 [下移一層] > [移到最下層]。 
1. 選取 [Visual 1] 中的文字 (即標題)，然後將字型色彩變更為 [白色]。 

**新增視覺效果 2 和 3 的背景圖形**

1. 在 [插入] 功能區中，選取 [圖形] > [矩形]，並將其延展為視覺效果 2 與 3 的寬度與高度。 
1. 在 [設定圖形格式] 窗格的 [行] 區段中，將 [透明度] 變更為 [100%]。 
1. 在 [格式] 索引標籤上，選取 [下移一層] > [移到最下層]。 

### <a name="finished-report"></a>已完成的報表

以下是已完成報表的精美外觀：  

:::image type="content" source="media/desktop-excel-stunning-report/power-bi-excel-formatted-report.png" alt-text="已完成格式化報表的螢幕擷取畫面。":::

總而言之，這份報表能夠回答經理最關心的問題： 

- 哪一個月份和年份有最大收益？ 

    2014 年 12 月 

- 公司在哪個國家/地區取得了最大成功？ 

    在歐洲，特別是法國和德國。 

- 公司應該繼續投資哪項產品及哪個市場？ 

    公司應該繼續投資 Paseo 產品，並以小型企業和政府部門作為目標。 

## <a name="save-your-report"></a>儲存報表

- 在 [檔案] 功能表上，選取 [儲存]。

## <a name="publish-to-the-power-bi-service-to-share"></a>發佈至 Power BI 服務與其他人共用 

若要與經理和同事共用報表，請將報表發佈至 Power BI 服務。 當與擁有 Power BI 帳戶的同事共用時，其可與報表互動，但無法儲存變更。 

1. 在 Power BI Desktop 的 [常用] 功能區上，選取 [發佈]。 

    您可能需要登入 Power BI 服務。 如果還沒有帳戶，你可[註冊免費試用](https://app.powerbi.com/signupredirect?pbi_source=web)。

1. 在 Power BI 服務 > [選取] 中選取一個目的地，例如 [我的工作區]。
1. 選取 [在 Power BI 中開啟 <檔案名稱>]。

    :::image type="content" source="media/desktop-excel-stunning-report/open-power-bi.png" alt-text="在 Power BI 服務中開啟報表的螢幕擷取畫面。":::

    已完成的報表會隨即在瀏覽器中開啟。

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-excel-report-service.png" alt-text="Power BI 服務中您已完成 Power BI 報表的螢幕擷取畫面。"::: 

1. 選取報表頂端的 [共用]，與其他人共用報表。

    :::image type="content" source="media/desktop-excel-stunning-report/power-bi-share-report.png" alt-text="從 Power BI 服務共用報表的螢幕擷取畫面。":::

## <a name="next-steps"></a>後續步驟

- [教學課程：分析 Excel 和 OData 摘要的銷售資料](../connect-data/desktop-tutorial-analyzing-sales-data-from-excel-and-an-odata-feed.md)

有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)。
