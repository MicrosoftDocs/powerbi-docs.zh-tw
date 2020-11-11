---
title: 在 Power BI 中使用功能區圖表
description: 在 Power BI Desktop 中建立和使用功能區圖表
author: msftrien
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 05/05/2019
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: e89712dea5d9f932669141d8fe4129727166a342
ms.sourcegitcommit: 5ccab484cf3532ae3a16acd5fc954b7947bd543a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2020
ms.locfileid: "93413101"
---
# <a name="create-ribbon-charts-in-power-bi"></a>在 Power BI 中建立功能區圖表

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]    

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

您可建立功能區圖表來視覺化資料，並快速找出哪個資料類別具有最高的等級 (最大值)。 功能區圖表適合顯示等級變更，最高等級 (值) 一律顯示於每個時段的最上方。 

![螢幕擷取畫面顯示具有依年與季度顯示之音訊、行動電話與其他類別資料的緞帶圖。](media/desktop-ribbon-charts/ribbon-charts-01.png)

> [!NOTE]
> 若要與 Power BI 同事共用報表，必須兩人都擁有個人的 Power BI Pro 授權，或將報表儲存在 Premium 容量中。 請參閱[共用報告](../collaborate-share/service-share-reports.md)。

## <a name="prerequisites"></a>必要條件

本教學課程使用[零售分析範例 PBIX 檔案](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)。

1. 從功能表列的左上方區段中，選取 [檔案] > [開啟]
   
2. 尋找您的 **零售分析範例 PBIX 檔案** 複本

1. 在報表檢視 ![報表檢視圖示的螢幕擷取畫面](media/power-bi-visualization-kpi/power-bi-report-view.png) 中開啟 **零售分析範例 PBIX 檔案** 。

1. 選取 ![黃色索引標籤的螢幕擷取畫面。](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) 新增頁面。

## <a name="create-a-ribbon-chart"></a>建立功能區圖表

1. 若要建立功能區圖表，請從 [視覺效果] 畫面選取 [功能區圖表]。

    ![視覺效果範本](media/desktop-ribbon-charts/power-bi-template.png)

    功能區圖表會透過使用功能區，連接視覺化時間連續體的資料類別，可讓您看到在整個圖表 X 軸 (通常為時間軸) 的範圍中，某個類別的等級為何。

2. 選取 [軸]、[圖例] 和 [值] 的欄位。  在本例中，我們已選取：[商店] > [OpenDate]、[項目] > [類別] 和 [銷售] > [今年銷售額] > [值]。  

    ![選取的欄位](media/desktop-ribbon-charts/power-bi-ribbon-values.png)

    因為資料集只包含一年的資料，所以我們從 [軸] 移除了 [年份] 和 [季度] 欄位。

3. 功能區圖表會顯示每個月份的順位。 請注意順位隨時間變化的方式。 例如，二月到三月時，「家居」類別從第二位移至第四位。

    ![螢幕擷取畫面顯示您建立的緞帶圖，緞帶圖中顯示一些資料的圖說文字。](media/desktop-ribbon-charts/power-bi-ribbon.png)

## <a name="format-a-ribbon-chart"></a>格式化功能區圖表
當您建立功能區圖表時，您可以在 [視覺效果] 窗格的 [格式] 區段中，使用格式設定的選項。 功能區圖表的格式設定選項類似於堆疊直條圖的選項，但有功能區特有的額外格式設定選項。

![顯螢幕擷取畫面示已選取的格式圖示與已展開的緞帶區域。](media/desktop-ribbon-charts/power-bi-format-ribbon.png)

功能區圖表的這些格式設定選項可讓您進行調整。

* **間距** 可讓您調整多少空白字元出現在功能區之間。 數字是資料行最大高度的百分比。
* **符合數列色彩** 可讓您讓功能區色彩符合數列色彩。 當設定為 [關閉] 時，功能區是灰色。
* **透明度** 指定功能區的透明程度，預設值為 30。
* **框線** 可讓您在功能區的上方和底部放置深色框線。 根據預設，框線會關閉。

由於功能區圖表沒有 Y 軸標籤，因此您可能想要新增資料標籤。 從 [格式化] 窗格中，選取 [資料標籤]。 

![資料標籤的格式化選項](media/desktop-ribbon-charts/power-bi-labels.png)

設定資料標籤的格式化選項。 在此範例中，我們已將文字色彩設定為白色，並將顯示單位設為千。

![螢幕擷取畫面顯示您的最終格式化緞帶圖。](media/desktop-ribbon-charts/power-bi-data-labels.png)

## <a name="next-steps"></a>後續步驟

[Power BI 中的散佈圖與泡泡圖](power-bi-visualization-scatter.md)

[Power BI 中的視覺效果類型](power-bi-visualization-types-for-reports-and-q-and-a.md)
