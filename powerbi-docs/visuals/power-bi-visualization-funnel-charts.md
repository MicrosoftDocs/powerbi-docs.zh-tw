---
title: 漏斗圖
description: Power BI 中的漏斗圖
author: msftrien
ms.reviewer: mihart
featuredvideoid: maTzOJSRB3g
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 05/05/2020
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: 2719127825dc94f1f1bd83fe4d36dc47dfc355f7
ms.sourcegitcommit: 5ccab484cf3532ae3a16acd5fc954b7947bd543a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2020
ms.locfileid: "93412893"
---
# <a name="create-and-use-funnel-charts"></a>建立和使用漏斗圖

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

漏斗圖幫您將有循序連接階段的線性程序視覺化。 例如，會分階段追蹤客戶的銷售漏斗圖：潛在客戶 (Lead) \> 合格的潛在客戶 (Lead) \> 潛在客戶 (Prospect) \> 合約 \> 關閉。  漏斗圖的圖形一看就能表達出您追蹤中程序的健全狀況。

漏斗圖的每個階段代表總數中所佔的百分比。 因此，在大部分情況下，漏斗圖形狀像漏斗 -- 第一階段最大，然後每個後續階段比前一階段小。  梨狀的漏斗圖也很實用，能識別出程序中的問題。  但通常第一階段，也就是「引入」階段佔最大部分。

![藍色範例漏斗圖](media/power-bi-visualization-funnel-charts/funnelplain.png)

> [!NOTE]
> 要與 Power BI 同事共用您的報表，必須雙方都擁有個人的 Power BI Pro 授權，或者將報表儲存在 Premium 容量中。    

## <a name="when-to-use-a-funnel-chart"></a>使用漏斗圖的時機
漏斗圖極適合：

* 當資料具有循序性，並至少通過 4 個以上的階段時。
* 當第一階段「項目」數目預期大於最後階段的數目時。
* 當您要分階段計算潛在項目 (營收/銷售額/成交量/等等) 時。
* 當您要計算及追蹤轉換率和留客率時。
* 當您要顯示線性程序中的瓶頸時。
* 當您要追蹤購物車的工作流程時。
* 當您要追蹤點選連結廣告/行銷活動的進度及成功與否時。

## <a name="working-with-funnel-charts"></a>使用漏斗圖
漏斗圖：

* 可以進行排序。
* 支援多個圖表。
* 可以在相同報表頁面上，藉由其他視覺效果反白顯示及交叉篩選。
* 可以在相同報表頁面上，用於反白顯示及交叉篩選其他視覺效果。
   > [!NOTE]
   > 觀賞這段影片，了解 Will 如何使用銷售與行銷範例來建立漏斗圖。 然後遵循影片下方的步驟，使用商機分析 .PBIX 範例檔案親自試試看
   > 
   > 
## <a name="prerequisite"></a>必要條件

本教學課程使用[商機分析範例 PBIX 檔案](https://download.microsoft.com/download/9/1/5/915ABCFA-7125-4D85-A7BD-05645BD95BD8/Opportunity%20Analysis%20Sample%20PBIX.pbix
)。

1. 從功能表列的左上方區段中，選取 [檔案]   > [開啟] 
   
2. 尋找您的 **商機分析範例 PBIX 檔案** 複本

1. 在報表檢視 ![報表檢視圖示的螢幕擷取畫面](media/power-bi-visualization-kpi/power-bi-report-view.png) 中開啟 **商機分析範例 PBIX 檔案** 。

1. 選取 ![黃色索引標籤的螢幕擷取畫面。](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) 新增頁面。


## <a name="create-a-basic-funnel-chart"></a>建立基本漏斗圖
觀賞這段影片，了解 Will 如何使用銷售與行銷範例來建立漏斗圖。

<iframe width="560" height="315" src="https://www.youtube.com/embed/qKRZPBnaUXM" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>


現在建立您自己的漏斗圖，其中可顯示每個銷售階段中擁有的商機數。

1. 從空白報告頁面開始，選取 [SalesStage]  \> [銷售階段]  欄位。
   
    ![選取 [銷售階段]](media/power-bi-visualization-funnel-charts/funnelselectfield-new.png)

1. 選取漏斗圖示 ![漏斗圖圖示](media/power-bi-visualization-funnel-charts/power-bi-funnel-icon.png) 將直條圖轉換成漏斗圖。

2. 從 [欄位]  窗格，選取 [事實]  \> [商機計數]  。
   
    ![建立漏斗圖](media/power-bi-visualization-funnel-charts/power-bi-funnel-2.png)
4. 暫留在列上會顯示豐富的資訊。
   
   * 階段名稱
   * 此階段目前商機數
   * 整體轉換率 (潛在客戶 %) 
   * 至下一階段 (也稱為下滑率)，是前一階段的 % (在本案例中是提案階段/解決方案階段)
     
     ![提案列的詳細資料](media/power-bi-visualization-funnel-charts/funnelhover-new.png)

6. [儲存報表](../create-reports/service-report-save.md)。

## <a name="highlighting-and-cross-filtering"></a>反白顯示和交叉篩選
如需使用 [篩選] 窗格的資訊，請參閱[將篩選加入報表](../create-reports/power-bi-report-add-filter.md)。

在漏斗圖中反白顯示列，會篩選報表頁面上的其他視覺效果，反之亦然。 如果要跟著做，請將其他一些視覺效果加入包含漏斗圖的報表頁面中。

1. 在漏斗圖中選取 [提案]  列。 這會交叉醒目提示頁面上的其他視覺效果。 使用 CTRL 進行多重選取。
   
   ![顯示視覺效果互動的短片](media/power-bi-visualization-funnel-charts/funnelchartnoowl.gif)
2. 若要設定視覺效果互相交叉醒目提示及交叉篩選之方式的喜好設定，請參閱[在 Power BI 中與視覺效果互動](../create-reports/service-reports-visual-interactions.md)

## <a name="next-steps"></a>後續步驟

[Power BI 中的量測計](power-bi-visualization-radial-gauge-charts.md)

[Power BI 中的視覺效果類型](power-bi-visualization-types-for-reports-and-q-and-a.md)



