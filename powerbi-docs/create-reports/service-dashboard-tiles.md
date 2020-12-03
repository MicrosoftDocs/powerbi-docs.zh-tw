---
title: Power BI 設計工具的儀表板磚簡介
description: 本文描述 Power BI 中的儀表板磚，其中包括從 SQL Server Reporting Services (SSRS) 報表建立的磚。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 04/17/2020
LocalizationGroup: Dashboards
ms.openlocfilehash: 56f00568b22d236b498446065cf97ff565993e7a
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418229"
---
# <a name="intro-to-dashboard-tiles-for-power-bi-designers"></a>Power BI 設計工具的儀表板磚簡介

圖格是您釘選到儀表板的資料快照。 您可以從報表、資料集、儀表板、問與答方塊、Excel 和 SQL Server Reporting Services (SSRS) 報表等來建立磚。  這個螢幕擷取畫面顯示許多釘選到儀表板的不同磚。

![Power BI 儀表板](media/service-dashboard-tiles/power-bi-dashboard.png)

儀表板和儀表板磚是 Power BI 服務的功能，而不是 Power BI Desktop 的功能。 您無法在行動裝置上建立儀表板，但可以在該處[檢視和共用](../consumer/mobile/mobile-apps-view-dashboard.md)儀表板。

除了釘選磚，您也可以使用[新增磚](service-dashboard-add-widget.md)控制項直接在儀表板上建立獨立的磚。 獨立磚包括：文字方塊、影像、視訊、串流資料和 Web 內容。

需要協助以了解構成 Power BI 的建置組塊嗎？ 請參閱 [Power BI 服務中的設計工具基本概念](../fundamentals/service-basic-concepts.md)。

> [!NOTE]
> 如果用來建立圖格的原始視覺效果有了變更，也不會改變圖格。  例如，如果您已從報表釘選折線圖，然後將折線圖變更為長條圖，則儀表板磚仍會顯示折線圖。 資料會重新整理，但視覺效果類型不會。
> 
> 

## <a name="pin-a-tile"></a>釘選磚
有很多不同的方式，可以將磚新增 (釘選) 至儀表板。 您可以從下列位置釘選磚：

* [Power BI 問與答](service-dashboard-pin-tile-from-q-and-a.md)
* [報表](service-dashboard-pin-tile-from-report.md)
* [其他儀表板](service-pin-tile-to-another-dashboard.md)
* [商務用 OneDrive 上的 Excel 活頁簿](service-dashboard-pin-tile-from-excel.md)
* [Quick Insights (深入資訊摘要)](service-insights.md)
* [Power BI 報表伺服器或 SQL Server Reporting Services 中的內部部署編頁報表](/sql/reporting-services/pin-reporting-services-items-to-power-bi-dashboards)

您可以使用[新增磚](service-dashboard-add-widget.md)控制項，直接在儀表板上建立影像、文字方塊、影片、串流資料和 Web 內容的獨立磚。

  ![新增磚圖示](media/service-dashboard-tiles/add_widgetnew.png)

## <a name="interact-with-tiles-on-a-dashboard"></a>與儀表板上的圖格互動
將磚新增至儀表板之後，您可以移動和調整其大小，或變更其外觀和行為。

### <a name="move-and-resize-a-tile"></a>移動和調整圖格大小
抓取磚並[在儀表板上移動](service-dashboard-edit-tile.md)。 將滑鼠暫留並選取控點 ![磚控點](media/service-dashboard-tiles/resize-handle.jpg) 以調整磚大小。

### <a name="hover-over-a-tile-to-change-the-appearance-and-behavior"></a>將滑鼠暫留在圖格上以變更其外觀和行為
1. 將滑鼠暫留在磚上以顯示省略符號。
   
    ![磚省略符號](media/service-dashboard-tiles/ellipses_new.png)
2. 選取省略符號以開啟磚動作功能表。
   
    ![省略符號圖示](media/service-dashboard-tiles/power-bi-tile-menu.png)
   
    從這裡您可以：
   
     * [將註解新增至儀表板](../consumer/end-user-comment.md)。
     * [開啟用來建立此磚的報表](../consumer/end-user-reports.md)。  
     * [在焦點模式中檢視](../consumer/end-user-focus.md)。   
     * [匯出磚中所使用的資料](../visuals/power-bi-visualization-export-data.md)。
     * [編輯標題和子標題並新增超連結](service-dashboard-edit-tile.md)。 
     * [執行見解](service-insights.md)。 
     * [將磚釘選到另一個儀表板](service-pin-tile-to-another-dashboard.md)。
     * [刪除磚](service-dashboard-edit-tile.md)。

3. 若要關閉動作功能表，請選取儀表板中的空白區域。

### <a name="select-a-tile"></a>選取磚
當您選取磚時，接下來情況取決於您建立該磚的方式。 否則，選取磚會帶您前往建立此磚所使用的報表、Excel Online 活頁簿、內部部署 Reporting Services 報表或問與答問題。 或者，如果有[自訂連結](service-dashboard-edit-tile.md)，則選取磚會帶您前往該連結。

> [!NOTE]
> 使用 [新增磚] 直接在儀表板上建立的影片磚為例外。 選取影片磚 (以此方式建立) 會直接在儀表板上播放影片。   
> 
> 

## <a name="considerations-and-troubleshooting"></a>考量與疑難排解

* 如未儲存建立視覺效果所用的報表，則選取該磚不會執行任何動作。
* 如果磚是從 Excel Online 的活頁簿建立，您至少需要該活頁簿的讀取權限。 否則，選取磚並不會在 Excel Online 中開啟活頁簿。
* 假設您使用 [新增磚] 直接在儀表板上建立磚，並為其設定自訂超連結。 如此一來，在您選取標題、子標題或磚時，就會開啟該 URL。 否則，當您選取針對影像、Web 程式碼或文字方塊直接在儀表板上建立的磚時，預設不會有任何反應。
* 您可以從 Power BI 報表伺服器或 SQL Server Reporting Services 的內部部署編頁報表建立磚。 如果您無權存取內部部署報表，則選取磚時會帶您前往一個頁面，指出您沒有存取權 (rsAccessDenied)。
* 假設您選取從 Power BI 報表伺服器或 SQL Server Reporting Services 的內部部署編頁報表建立的磚。 如果您無權存取報表伺服器所在的網路，則選取從該編頁報表建立的磚時會帶您前往一個頁面，指出找不到伺服器 (HTTP 404)。 您的裝置需要報表伺服器的網路存取權，才能檢視報表。
* 如果用來建立磚的原始視覺效果有了變更，也不會改變磚。 例如，您從報表釘選折線圖之後，將折線圖變更為長條圖，儀表板磚會繼續顯示折線圖。 資料會重新整理，但視覺效果類型不會。

## <a name="next-steps"></a>後續步驟
- [建立儀表板的卡片 (大型數字磚)](../visuals/power-bi-visualization-card.md)
- [Power BI 設計工具的儀表板簡介](service-dashboards.md)  
- [Power BI 的資料重新整理](../connect-data/refresh-data.md)
- [Power BI 服務中的設計工具基本概念](../fundamentals/service-basic-concepts.md)
- [Integrating Power BI tiles into Office documents](https://powerbi.microsoft.com/blog/integrating-power-bi-tiles-into-office-documents/) (將 Power BI 磚整合到 Office 文件中)
- [將 Reporting Services 項目釘選到 Power BI 儀表板](/sql/reporting-services/pin-reporting-services-items-to-power-bi-dashboards)

有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)。