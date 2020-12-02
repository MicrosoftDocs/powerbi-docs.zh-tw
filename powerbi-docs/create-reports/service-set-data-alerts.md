---
title: 在 Power BI 服務中設定資料警示
description: 了解如何在 Microsoft Power BI 服務中設定儀表板，以在資料變更超出您所設定的限制時通知您。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: JbL2-HJ8clE
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 04/02/2020
LocalizationGroup: Dashboards
ms.openlocfilehash: cce9e351d468289b37f000159f846a5b2942b36a
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96387727"
---
# <a name="data-alerts-in-the-power-bi-service"></a>Power BI 服務中的資料警示

設定警示，以在儀表板中的資料變更時超出您所設定的限制時通知您。

您可在 [我的工作區] 中的磚上設定警示。 如果有人共用位於 [Premium 容量](../admin/service-premium-what-is.md)中的儀表板，您也可以設定警示。 如果有 Power BI Pro 授權，您也可以在任何其他工作區的磚上設定警示。 只可在從報表視覺效果釘選的磚上，為量測計、KPI 和卡片設定警示。 可以對您從報表釘選到儀表板的串流資料集上所建立視覺效果設定警示。 但不可對使用 [新增磚]   > [自訂串流資料]  直接在儀表板上所建立串流磚設定警示。

即使將儀表板分享給他人共用，仍只有您才能查看您所設定的警示。 即使儀表板擁有者也看不到您在其儀表板檢視上設定的警示。 資料警示會在平台之間完全同步處理；請在 [ Power BI 行動裝置應用程式](../consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md)和 Power BI 服務中設定和檢視資料警示。 其不適用於 Power BI Desktop。 您甚至可以使用 Power Automate 來自動化並整合警示。 您可以在 [Power Automate 和 Power BI](../collaborate-share/service-flow-integration.md) 一文中親身試用。

![磚](media/service-set-data-alerts/powerbi-alert-types-new.png)

> [!WARNING]
> 資料驅動的警示通知會提供資料的相關資訊。 如果您在行動裝置上檢視 Power BI 資料，而該裝置遺失或遭竊，建議您使用 Power BI 服務關閉所有資料驅動警示規則。

## <a name="set-data-alerts-in-the-power-bi-service"></a>在 Power BI 服務中設定資料警示

觀看 Amanda 在儀表板上將某些警示新增至磚。 然後遵循影片下方的逐步指示親自試試看。

<iframe width="560" height="315" src="https://www.youtube.com/embed/JbL2-HJ8clE" frameborder="0" allowfullscreen></iframe>

此範例使用零售版 Analysis 範例儀表板。 若要跟著做，請[取得零售分析範例](sample-retail-analysis.md#get-the-content-pack-for-this-sample)。

1. 啟動儀表板。 從 [商店數總計]  磚，選取省略符號。

   ![[商店數總計] 磚](media/service-set-data-alerts/powerbi-card.png)

1. 選取鈴鐺圖示 ![警示圖示](media/service-set-data-alerts/power-bi-bell-icon.png)，以為 [商店數總計]  新增一或多個警示。

1. 若要開始，請選取 [+ 新增警示規則]  ，確定已將 [作用中]  滑桿設為 [開啟]  ，並為您的警示提供標題。 磚可幫助您輕鬆地辨識警示。

   ![顯示 [管理警示] 視窗的螢幕擷取畫面，其中已彈出 [新增警示規則]、[總商店警示]，以及 [警示標題]。](media/service-set-data-alerts/powerbi-alert-title.png)

1. 向下捲動並輸入警示的詳細資料。  在此範例中，您將會建立警示，每天一次在商店數總計超過 100 家時通知您。

   ![在 [管理警示] 視窗中設定 [臨界值]](media/service-set-data-alerts/power-bi-set-alert-details.png)

    警示會出現在您的 **通知中心** 內。 如果您選取此核取方塊，Power BI 也會傳送警示的相關電子郵件給您。

1. 選取 [儲存並關閉]  。

## <a name="receiving-alerts"></a>接收警示

當追蹤的資料達到您所設定其中一個閾值時，會出現一些連鎖反應。 首先，Power BI 會檢查自上次警示起，是否已超過 1 小時或 24 小時 (取決於您選取的選項)。 如果資料超過閾值，您將會收到警示。

接下來，Power BI 會傳送警示到您的 **通知中心**，並選擇性寄送電子郵件。 每個警示都包含資料的直接連結。 選取連結可以查看相關的磚，您可以在其中探索、共用以及深入了解。  

* 您如有設定傳送電子郵件警示，將會在收件匣中看到類似如下所述的狀況。

   ![警示電子郵件](media/service-set-data-alerts/powerbi-alerts-email.png)

* Power BI 會在您的 **通知中心** 新增一則訊息，並將新的警示圖示加入適用的磚 。

   ![Power BI 服務中的通知圖示](media/service-set-data-alerts/powerbi-alert-notifications.png)

* 您的 **通知中心** 會顯示警示詳細資料。

    ![讀取警示](media/service-set-data-alerts/powerbi-alert-notification.png)

   > [!NOTE]
   > 警示只對重新整理的資料有作用。 當資料重新整理時，Power BI 會檢查該資料有無設定警示。 若資料已達警示閾值，Power BI 會觸發警示。

## <a name="managing-alerts"></a>管理警示

有許多方式可以管理您的警示：

* 從儀表板磚。

* 從 Power BI 的 [設定] 功能表。

* 在 [Power BI 行動裝置應用程式](../consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md)的磚上。

### <a name="from-the-dashboard-tile"></a>從儀表板磚

1. 如果您需要變更或移除磚的警示，請選取鈴鐺圖示 ![警示圖示](media/service-set-data-alerts/power-bi-bell-icon.png)，以重新開啟 [管理警示] 視窗。

    Power BI 會顯示您為該磚設定的警示。

    ![顯示 [管理警示] 視窗的螢幕擷取畫面。](media/service-set-data-alerts/powerbi-see-alerts.png)

1. 若要修改警示，請選取警示名稱左側的箭號。

    ![警示名稱旁的箭號](media/service-set-data-alerts/powerbi-see-alerts-arrow.png)

1. 若要刪除警示，請選取警示名稱右側的垃圾桶。

      ![已選取垃圾桶圖示](media/service-set-data-alerts/powerbi-see-alerts-delete.png)

### <a name="from-the-power-bi-settings-menu"></a>從 Power BI 的 [設定] 功能表

1. 從 Power BI 功能表列選取齒輪圖示並選取 [設定]  。

    ![齒輪圖示](media/service-set-data-alerts/powerbi-gear-icon.png).

1. 選取 [設定]  下的 [警示]  。

    ![[設定] 視窗的 [警示] 索引標籤](media/service-set-data-alerts/powerbi-alert-settings.png)

1. 您可以在此處開啟及關閉警示、開啟 [管理警示]  視窗執行變更，或是刪除警示。

## <a name="considerations-and-troubleshooting"></a>考量與疑難排解

* 具有日期/時間量值的卡片磚不支援警示。
* 警示只適用於數值資料類型。
* 警示只對重新整理的資料有作用。 警示對於靜態資料毫無作用。
* 如果建置 KPI、卡片或量測計報表視覺效果，然後將該視覺效果釘選到儀表板，則警示只對串流資料集有作用。


## <a name="next-steps"></a>後續步驟

* [建立包含資料警示的 Power Automate](../collaborate-share/service-flow-integration.md)。

* [在行動裝置上設定資料警示](../consumer/mobile/mobile-set-data-alerts-in-the-mobile-apps.md)。

* [Power BI 是什麼？](../fundamentals/power-bi-overview.md)

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
