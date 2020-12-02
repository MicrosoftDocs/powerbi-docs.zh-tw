---
title: Power BI 服務中的報表
description: Power BI 服務中的報表，適用於商務使用者
author: mihart
ms.author: mihart
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: pbi-explore
ms.topic: how-to
ms.date: 10/09/2020
LocalizationGroup: Reports
ms.openlocfilehash: 152d3ee87afe93fdfbe19060a42f013ec83f2d2a
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96389706"
---
# <a name="reports-in-power-bi"></a>Power BI 中的報表

[!INCLUDE[consumer-appliesto-yynn](../includes/consumer-appliesto-yyn.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

Power BI 報表是一種資料集的多角度檢視，可透過視覺效果表示該資料集不同的尋找結果和見解。  報表可以具備單一視覺效果，或是充滿視覺效果的頁面。 取決於您的作業角色，您可能會是「設計」  報表的人員。 您也可能是「取用」或使用報表的「商務使用者」。 本文適用於「商務使用者」。

## <a name="the-parts-of-a-report"></a>報表的元件

![報表頁面的螢幕擷取畫面。](./media/end-user-reports/power-bi-report.png)

A. 此報表有六個頁面 (或索引標籤)，且您目前正在檢視 [情感]  頁面。    
B. 在此頁面上，有五個不同的視覺效果和頁面標題。    
C. [篩選]  窗格會顯示已將單一篩選套用至所有報表頁面。 若要摺疊 [篩選] 窗格，請選取箭號 ( **>** )。    
D. Power BI 橫幅會顯示報表的名稱和上次更新日期。 選取箭號可開啟功能表，也會顯示報表擁有者名稱。    
E。 動作列包含您可以對這份報告採取的動作。  例如，您可以新增註解、檢視書籤，或從報表匯出資料。  選取 [更多選項]  (...) 以顯示額外報表功能的清單。    

若不熟悉 Power BI，請參閱 [Power BI 服務商務使用者的基本概念](end-user-basic-concepts.md)來打好基礎。 報表可供在行動裝置上檢視、共用及加上標註。 如需詳細資訊，請參閱[探索 Power BI 行動裝置應用程式中的報表](mobile/mobile-reports-in-the-mobile-apps.md)。

## <a name="advantages-of-reports"></a>報表的優點

Power BI 根據單一資料集建立報表。 報表「設計師」會在報表中建立視覺效果來代表一部分資訊。 視覺效果不是靜態的。  它們會在基礎資料變更時更新。 您可以在深入了解資料時與視覺效果和篩選條件互動來探索見解並尋找答案。 與儀表板相同，但報表尤其具有極高的互動性和自訂性。 您可以使用報表來執行的工作範圍，將取決於報表「設計師」指派的角色與權限。

### <a name="safely-interact-with-content"></a>安全地與內容互動

在您探索並透過篩選、配量、訂閱和匯出等方式與內容互動時，您都不會破壞報表。 您的工作不會影響基礎資料集或原始共用內容。 這適用於儀表板、報表和應用程式。

> [!NOTE]
> 請記住，您不會對資料造成傷害。 Power BI 服務是進行探索及實驗而無須擔心破壞某些項目的絕佳位置。

### <a name="save-your-changes-or-revert-to-the-default-settings"></a>儲存您的變更或還原至預設設定

這並不表示您無法儲存變更。 您可以儲存變更，只是這些變更只會影響您的內容檢視。 若要還原至報表的原始預設檢視，請選取 [重設為預設]  。

![[還原為預設值] 圖示的螢幕擷取畫面。](./media/end-user-reports/power-bi-reset.png)

## <a name="dashboards-versus-reports"></a>儀表板與報表

[儀表板](end-user-dashboards.md)經常與報表混淆，因為它們也是填滿視覺效果的畫布。 但兩者還是有一些主要差異。  

| **功能** | **儀表板** | **報表** |
| --- | --- | --- |
| 頁面 |一個頁面 |一或多個頁面 |
| 資料來源 |每個儀表板一或多份報表以及一或多個資料集 |每份報表單一資料集 |
| 篩選 |無法篩選或配量 |有多種不同方法可篩選、反白顯示及配量 |
| 設定警示 |可以在儀表板滿足特定條件時，建立電子郵件警示 |否 |
| 功能 |可將一個儀表板設為您的「精選」儀表板 |無法建立精選報表 |
| 可以看到基礎資料集的資料表和欄位 |否。 可以匯出資料，但看不到儀表板本身的資料集資料表和欄位 |有。 可以看到您有查看權限的資料集資料表和欄位 |
| 自訂 |否  |可以篩選、匯出、檢視相關內容、新增書籤、產生 QR 代碼、在 Excel 中分析等 |

<!--| Available in Power BI Desktop |No |Yes, can create and view reports in Desktop |
| Pinning |Can pin existing visuals (tiles) only from current dashboard to your other dashboards |Can pin visuals (as tiles) to any of your dashboards. Can pin entire report pages to any of your dashboards. | -->

## <a name="report-designers-and-report-users"></a>報表設計師與報表使用者

根據您的角色，您可能會是建立自行使用報表或與同事共用報表的「設計師」  。 您會想要了解如何建立及共用報表。

或者，您可能會是接收其他人報表的「商務使用者」。 您會想要了解如何理解及與報表互動。 若為報表「商務使用者」，則這些連結便適合您：

* 請從 [Power BI 服務導覽](end-user-basic-concepts.md)開始，了解可在何處找到報表和報表工具。
* 了解如何[開啟報表](end-user-report-open.md)，以及[商務使用者可進行的所有互動](end-user-reading-view.md)。
* 使用其中一個的[範例](../create-reports/sample-tutorial-connect-to-the-samples.md)導覽來熟悉報表。  
* 若要查看報表正在使用哪些資料集，以及哪些儀表板顯示來自報的視覺效果 (「釘選」  )，請參閱[在 Power BI 服務中檢視相關內容](end-user-related.md)。

> [!TIP]
> 如果這裡找不到您要的內容，請使用左側的＜目錄＞來瀏覽所有「報表」  文章。

## <a name="next-steps"></a>後續步驟

[開啟並檢視報表](end-user-report-open.md)    
[Power BI 服務中的儀表板](end-user-dashboards.md)

