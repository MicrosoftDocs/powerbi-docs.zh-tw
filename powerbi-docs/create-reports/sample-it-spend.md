---
title: Power BI 的 IT 支出分析範例教學
description: Power BI 的 IT 支出分析範例教學
author: maggiesMSFT
ms.author: maggies
ms.reviewer: amac
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 07/05/2019
LocalizationGroup: Samples
ms.openlocfilehash: cdde0e702333feed54637c72fa3193052fde139f
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96414959"
---
# <a name="it-spend-analysis-sample-for-power-bi-take-a-tour"></a>Power BI 的 IT 支出分析範例教學

IT 支出分析範例內容套件包含儀表板、報表和資料集，用來分析 IT 部門的計劃與實際成本。 這項比較可幫助我們了解公司的年度計畫是否得當，並可針對大大偏離計畫的領域進行調查。 此範例中的公司，會經歷一年一度的計畫週期，然後按季產出新的最新估計 (LE) 來協助分析 IT 支出於會計年度的變化。

![IT 支出分析範例的儀表板](media/sample-it-spend/it1.png)

此範例是系列中的一部分，說明您可如何使用 Power BI 的商業導向資料、報表與儀表板。 它是由 [obviEnce](http://www.obvience.com/) 使用真實資料 (已匿名化) 所建立。 資料會以數種格式提供：內容套件、.pbix Power BI Desktop 檔案，或 Excel 活頁簿。 請參閱 [Power BI 範例](sample-datasets.md)。 

此教學課程探索 Power BI 服務中的 IT 支出分析範例內容套件。 因為 Power BI Desktop 和服務中報表的使用體驗皆非常類似，因此您也可以在 Power BI Desktop 中使用範例 .pbix 檔案來進行教學課程。 

您不需要 Power BI 授權，即可在 Power BI Desktop 中瀏覽範例。 如果您沒有 Power BI Pro 授權，則可以將範例儲存到 Power BI 服務中的 [我的工作區]。 

## <a name="get-the-sample"></a>取得範例

 您必須先將範例下載為[內容套件](#get-the-content-pack-for-this-sample)、[.pbix 檔案](#get-the-pbix-file-for-this-sample)或 [Excel 活頁簿](#get-the-excel-workbook-for-this-sample)，才能使用範例。

### <a name="get-the-content-pack-for-this-sample"></a>取得此範例的內容套件

1. 開啟 Power BI 服務 (app.powerbi.com) 並登入，然後開啟您要儲存範例的工作區。

   如果您沒有 Power BI Pro 授權，則可以將範例儲存到 [我的工作區]。

2. 在左下角選取 [取得資料]  。
   
   ![選取 [取得資料]](media/sample-datasets/power-bi-get-data.png)
3. 在顯示的 [取得資料]  頁面上，選取 [範例]  。
   
4. 選取 [IT 支出分析範例]  ，然後選擇 [連線]  。  
  
   ![連線至範例](media/sample-it-spend/it-connect.png)
   
5. Power BI 會匯入內容套件，然後將新儀表板、報表和資料集新增至您目前的工作區。
   
   ![IT 支出分析範例項目](media/sample-it-spend/it-spend-analysis-sample-entry.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>取得此範例的 .pbix 檔案

或者，您可以將 IT 支出分析範例下載為 [.pbix](https://download.microsoft.com/download/E/9/8/E98CEB6D-CEBB-41CF-BA2B-1A1D61B27D87/IT%20Spend%20Analysis%20Sample%20PBIX.pbix) 檔案，其設計目的是要用於 Power BI Desktop。

### <a name="get-the-excel-workbook-for-this-sample"></a>取得此範例的 Excel 活頁簿

如果您想要檢視此範例的資料來源，其也有可用的 [Excel 活頁簿](https://go.microsoft.com/fwlink/?LinkId=529783) 格式。 活頁簿包含的 Power View 工作表可供您檢視及修改。 若要查看未經處理資料，請啟用「資料分析」增益集，然後選取 [Power Pivot] > [管理]  。 若要啟用 Power View 和 Power Pivot 增益集，請參閱[在 Excel 中探索 Excel 範例](sample-datasets.md#explore-excel-samples-inside-excel)以了解詳情。

## <a name="it-spend-analysis-sample-dashboard"></a>IT 支出分析範例的儀表板
儀表板左邊有兩個數字的圖格，[浮動計畫 %]  和 [最新估計差異 % 第 3 季]  ，針對計畫與最新一季估計 (LE3 = 最新第 3 季估計) 的表現提供概觀。 整體上我們落後計畫 6%。 讓我們一起從時間點、地點及商品類別來了解造成此差異的原因。

## <a name="ytd-it-spend-trend-analysis-page"></a>[YTD IT 支出趨勢分析] 頁面
當您選取 [依銷售區域的 Var 方案 %]  儀表板圖格時，它會顯示 IT 支出分析範例報表的 [YTD IT 支出趨勢分析]  頁面。 我們可以一眼看出我們在美國和歐洲有正差異，而在加拿大、拉丁美洲和澳洲有負差異。 美國約為 6% 正差異，而澳洲則約為 7% 負差異。

![依銷售區域的 Var 方案 %](media/sample-it-spend/it2.png)

不過，如果只看此圖表就做出結論恐怕會產生誤導。 我們必須看看實際金額才能洞悉狀況。

1. 在 [依銷售區域的 Var 方案 %]  圖表中選取 [澳洲和紐西蘭]  ，然後觀察 [依 IT 領域的 Var 方案]  圖表。

   ![[YTD IT 支出趨勢分析] 頁面](media/sample-it-spend/it3.png)
2. 現在請選取 **美國**。 請注意，在我們的整體支出中，澳洲和紐西蘭相較於美國只占極小部分。

    接下來，讓我們來探討美國的哪一類商品造成差異。

## <a name="ask-questions-of-the-data"></a>針對資料提問
1. 選取導覽窗格頂端的 [IT 費用分析範例]  ，返回範例儀表板。
2. 選取 [詢問資料相關問題]  。
3. 從左側的 [入門問題]  清單，選取 [何謂依 IT 領域的方案]  。

   ![依 IT 領域的方案圖表](media/sample-it-spend/it-area-chart.png)

4. 在問與答方塊中，清除先前的項目，並輸入 *show IT areas, var plan % and var le3 % bar chart*。

   ![依 IT 領域的 Var 方案 % 和 Var LE3 % 圖表](media/sample-it-spend/it4.png)

   在第一個 IT 領域，也就是 **基礎結構** 中，請注意，初始的浮動方案與最新估計的浮動方案之間的百分比已有巨大差異。

## <a name="ytd-spend-by-cost-elements-page"></a>[依成本項目的 YTD 支出] 頁面

1. 返回儀表板，並查看 [浮動方案 %、浮動最新估計 % - 第 3 季]  儀表板圖格。

   ![Var 方案 %、Var LE3 圖格](media/sample-it-spend/it5.png)

   請注意，基礎結構區域凸顯出對方案有很大的正差異。

1. 選取此圖格以開啟報表，並檢視 [依成本項目的 YTD 支出]  頁面。
2. 選取左下方 [依 IT 領域的 Var 方案 % 和 Var LE3 %]  圖表中的 [基礎結構]  長條，並觀察左下方 [依銷售區域的 Var 方案 %]  中的方案值。

    ![[依成本項目的 YTD 支出] 頁面](media/sample-it-spend/it6.png)
3. 依序在 [成本項目群組]  交叉分析篩選器中選取每個名稱，來尋找差異最大的成本項目。
4. 在選取 [其他]  的情況下，選取 [IT 領域]  交叉分析篩選器中的 [基礎結構]  ，並選取 [IT 子領域]  交叉分析篩選器中的子領域，找出差異最大的子領域。  

   請注意，[網路]  的大差異。 顯然公司決定提供員工電話服務做為福利，即使這項措施未經規劃也一樣。

## <a name="plan-variance-analysis-page"></a>[方案變異分析] 頁面

1. 選取頁面底部的 [方案變異分析]  索引標籤。

2. 在左側的 [依業務區域的 Var 方案和 Var 方案 %]  圖表中，選取 [基礎結構]  欄，反白顯示頁面其他部分的基礎結構業務區域值。

    ![[方案變異分析] 頁面](media/sample-it-spend/it7.png)

   請注意，在 [依月份和業務區域的 Var 方案 %]  圖表中，礎結構業務區域在二月開始正差異。 另外也請注意在與所有其他業務區域相較之下，該業務區域的方案差異值如何隨國家/地區產生變化。 

3. 使用右側的 [ IT 領域]  和 [IT 子領域]  交叉分析篩選器，來篩選頁面其餘部分的值，而不是探索資料。 

## <a name="edit-the-report"></a>編輯報表
選取左上角的 [編輯報表]  ，並在 [編輯檢視] 中探索：

* 檢視頁面如何組成、每個圖表中的欄位，以及頁面上的篩選條件。
* 根據相同的資料新增頁面和圖表。
* 變更每個圖表的視覺效果類型。
* 將感興趣的圖表釘選至儀表板。

## <a name="next-steps-connect-to-your-data"></a>下一步：連接到您的資料
您可以在此環境盡情嘗試，因為您可以選擇不儲存您的變更。 但如果儲存了變更，您也可以隨時選取 [取得資料]  以取得此範例的新複本。

希望此教學已讓您了解 Power BI 儀表板、問與答和報表能夠如何提供範例資料的見解。 現在輪到您了，請連接到您自己的資料。 您可以透過 Power BI 連接到各式各樣的資料來源。 若要深入了解，請參閱[開始使用 Power BI 服務](../fundamentals/service-get-started.md)。
