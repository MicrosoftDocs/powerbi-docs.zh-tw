---
title: Power BI 報表的頁面顯示設定
description: 報告的頁面顯示設定和頁面檢視設定
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 05/29/2019
LocalizationGroup: Reports
ms.openlocfilehash: 9452a4a6340480bcb6c8b646c16125fe73f68235
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96393477"
---
# <a name="apply-page-display-settings-in-a-power-bi-report"></a>在 Power BI 報表中套用頁面顯示設定
我們了解保持報表版面配置像素完美的重要性。 有時候這會有點困難，因為您和您的同事可能會使用外觀比例和大小不同的螢幕來檢視這些報表。 

預設顯示檢視為 [調整成一頁]  ，而預設顯示大小為 **16:9**。 如果您想要鎖定為不同的外觀比例，或想要以不同的方式調整報表，有兩種工具可協助您：[頁面檢視]*_ 設定與 [頁面大小] 設定。


<iframe width="560" height="315" src="https://www.youtube.com/embed/5tg-OXzxe2g" frameborder="0" allowfullscreen></iframe>


## <a name="where-to-find-page-view-settings-in-the-power-bi-service-and-power-bi-desktop"></a>在 Power BI 服務和 Power BI Desktop 中何處可找到頁面檢視設定
頁面檢視設定可用於 Power BI 服務和 Power BI Desktop 中，但介面稍有不同。 下列各節說明您可以在每個 Power BI 工具中的何處找到 [檢視] 設定。

### <a name="in-power-bi-desktop"></a>在 Power BI Desktop 中
在報告檢視中，選取 [檢視]_* 索引標籤，以開啟頁面檢視設定與電話配置設定。

  ![Desktop 頁面檢視設定](media/power-bi-report-display-settings/power-bi-desktop-view-settings.png)

### <a name="in-the-power-bi-service-apppowerbicom"></a>在 Power BI 服務 (app.powerbi.com) 中
在 Power BI 服務中，開啟報表並從左上方功能表列選取 [檢視]  。

![服務頁面檢視設定](media/power-bi-report-display-settings/power-bi-change-page-view.png)

[閱讀檢視和編輯檢視](../consumer/end-user-reading-view.md)中都可使用頁面檢視設定。 在編輯檢視中，報表擁有者可以將頁面檢視設定指派給個別的報表頁面，而這些設定會隨報表一起儲存。 當同事在 [閱讀檢視] 中開啟該報告時，她看到的是以擁有者設定所顯示的報告頁面。 同事可以在閱讀檢視中，變更「某些」  **頁面檢視** 設定，但是在離開報表時不會儲存所做的變更。

## <a name="page-view-settings"></a>頁面檢視設定
第一組頁面檢視設定可控制報表頁面相對於瀏覽器視窗的顯示。 選擇如下：

* **符合一頁大小** (預設值)：縮放內容到最能符合頁面的程度
* **符合寬度**：縮放內容到符合頁面的寬度
* **實際大小**：內容以完整大小顯示

第二組頁面檢視設定可控制報表畫布上物件的位置。 選擇如下：

* **顯示格線**：開啟格線可協助您在報表畫布上放置物件。
* **貼齊格線**：搭配 **[顯示格線]** 使用，可在報表畫布上精確地放置和對齊物件。 
* **鎖定物件**：鎖定畫布上的所有物件，使其無法移動或調整大小。
* **選取範圍窗格**： **[選取]** 窗格會列出畫布上的所有物件。 您可以決定要顯示和隱藏的物件。

    ![選取窗格](media/power-bi-report-display-settings/power-bi-selection-pane.png)



## <a name="page-size-settings"></a>頁面大小設定
![變更 [頁面大小] 設定](media/power-bi-report-display-settings/power-bi-page-size.png)

只有報表擁有者可以使用 **[頁面大小]** 設定。 在 Power BI 服務 (app.powerbi.com) 中，這表示能夠在 [[編輯檢視]](../consumer/end-user-reading-view.md) 中開啟報表。 [頁面大小]  設定位於 [視覺效果]  窗格中，並可控制報表畫布的顯示比例和實際大小 (以像素為單位)：   

* 4:3 比例
* 16:9 比例 (預設值)
* Letter
* 自訂 (以像素為單位的高度和寬度)

## <a name="next-steps"></a>後續步驟
[Power BI Desktop 中的報表檢視](desktop-report-view.md)

[在您自己的 Power BI 報表中變更頁面檢視和頁面大小設定](../consumer/end-user-report-view.md)

深入了解 [Power BI 中的報表](../consumer/end-user-reports.md)

[Power BI 服務中的設計工具基本概念](../fundamentals/service-basic-concepts.md)

有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)
