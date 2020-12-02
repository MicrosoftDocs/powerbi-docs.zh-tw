---
title: 卡片視覺效果 (也稱為大數字磚)
description: 在 Power BI 中建立卡片視覺效果
author: mihart
ms.author: mihart
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 05/05/2020
LocalizationGroup: Visualizations
ms.openlocfilehash: f1d4a5b2d69c6d0b2d8cbec8d48e2be00b5a0f78
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96409945"
---
# <a name="create-card-visualizations"></a>建立卡片視覺效果

[!INCLUDE[consumer-appliesto-nyyn](../includes/consumer-appliesto-nyyn.md)]

[!INCLUDE [power-bi-visuals-desktop-banner](../includes/power-bi-visuals-desktop-banner.md)]

有時您在 Power BI 儀表板或報告中追蹤的最重要項目是一個單一數字，例如總銷售額、歷年的市佔率，或總商機。 這類型的視覺效果稱為「卡片」  。 幾乎所有的原生 Power BI 視覺效果，都可以使用報告編輯器或 [問與答] 來建立卡片。

![卡片視覺效果](media/power-bi-visualization-card/pbi-opptuntiescard.png)

> [!NOTE]
> 要與 Power BI 同事共用您的報表，必須雙方都擁有個人的 Power BI Pro 授權，或者將報表儲存在 Premium 容量中。

## <a name="prerequisite"></a>必要條件

本教學課程使用[零售分析範例 PBIX 檔案](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)

1. 從功能表列的左上方區段中，選取 [檔案]  \> [開啟] 
   
2. 尋找您的 **零售分析範例 PBIX 檔案** 複本

1. 在報表檢視 ![報表檢視圖示的螢幕擷取畫面](media/power-bi-visualization-kpi/power-bi-report-view.png) 中開啟 **零售分析範例 PBIX 檔案**。

1. 選取 ![黃色索引標籤的螢幕擷取畫面。](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) 新增頁面。

## <a name="option-1-create-a-card-using-the-report-editor"></a>選項 1：使用報告編輯器建立卡片

建立卡片的第一種方法，是使用 Power BI Desktop 中的報表編輯器。

1. 從空白報告頁面開始，選取 [門市]  \> [開張門市計數]  欄位。

    Power BI 會以一個數字建立直條圖。

   ![範例號碼標題圖](media/power-bi-visualization-card/pbi-overview-chart.png)

2. 在 [視覺效果] 窗格中選取卡片圖示。

   ![範例號碼標題卡](media/power-bi-visualization-card/power-bi-card-visualization.png)

您現在已成功使用報表編輯器建立卡片。 以下是使用問與答問題方塊來建立卡片的第二個選項。

## <a name="option-2-create-a-card-from-the-qa-question-box"></a>選項 2：從問與答問題方塊建立卡片
問與答問題方塊是您在建立卡片時使用的另一個選項。 您可以在 Power BI Desktop 報表檢視中取得問與答問題方塊。

1. 從空白報表頁面開始

1. 在視窗頂端，選取 **詢問問題** 圖示。 

    Power BI 將會為您的問題建立卡片和方塊。 

   ![詢問問題圖示位置](media/power-bi-visualization-card/power-bi-q-and-a-overview.png)

2. 例如，在問題方塊中鍵入「Tina 的總銷售額」。

    問題方塊可透過建議與重新陳述來協助您，而且最後會顯示總數。  

   ![問題方塊範例](media/power-bi-visualization-card/power-bi-q-and-a-box.png)

   ![來自問題方法的卡片範例](media/power-bi-visualization-card/power-bi-q-and-a-card.png)

您現在已成功建立包含問與答問題方塊的卡片。 以下步驟可讓您針對特定需求將卡片格式化。

## <a name="format-a-card"></a>格式化卡片
您有變更標籤、文字、色彩等等的許多選項。 學習的最佳方法是建立卡片，然後探索 [格式化] 窗格。 以下是幾個可用的格式化選項。 

在報表中與卡片互動時，可使用 [格式化] 窗格。 

1. 從選取油漆滾筒圖示開始，開啟 [格式化] 窗格。 

    ![凸顯油漆滾筒外框的卡片](media/power-bi-visualization-card/power-bi-format-card-2.png)

2. 選取卡片，展開 [資料標籤]  並變更色彩、大小和字型系列。 如果您有數千個存放區，則可以使用 [顯示單位]  以千為單位顯示存放區數目，並控制小數位數。 例如，125.8K 而不是 125,832.00。

    ![含資料格式範例的卡片](media/power-bi-visualization-card/power-bi-card-format-2.png)

3.  展開 [類別目錄標籤]  並變更色彩和大小。

    ![含類別範例的卡片](media/power-bi-visualization-card/power-bi-card-format-category.png)

4. 展開 [背景]  並移動滑桿至 [開啟]。  現在您可以變更背景色彩和透明度。

    ![滑桿已設為 ON](media/power-bi-visualization-card/power-bi-format-color-2.png)

5. 繼續探索格式化選項，直到您的卡片完全符合您的喜好。 

## <a name="considerations-and-troubleshooting"></a>考量與疑難排解

如果完全看不到問題方塊，請連絡您的 Power BI 系統管理員。

## <a name="next-steps"></a>後續步驟
[Power BI 中的組合圖](power-bi-visualization-combo-chart.md)

[Power BI 中的視覺效果類型](power-bi-visualization-types-for-reports-and-q-and-a.md)
