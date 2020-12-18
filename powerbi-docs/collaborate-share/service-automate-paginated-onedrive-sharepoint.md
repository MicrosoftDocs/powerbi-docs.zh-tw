---
title: 將編頁報表儲存至商務用 OneDrive 或 SharePoint Online
description: 在本文中，您將使用 Power Automate 自動將 Power BI 編頁報表儲存至商務用 OneDrive 或 SharePoint Online 資料夾。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 11/17/2020
LocalizationGroup: Get started
ms.openlocfilehash: 6aaad48fb3e97aa6c1b4fc51834ee593a49a8192
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2020
ms.locfileid: "97097723"
---
# <a name="save-a-paginated-report-to-onedrive-for-business-or-sharepoint-online"></a>將編頁報表儲存至商務用 OneDrive 或 SharePoint Online

透過 [Power Automate](/power-automate/getting-started)，您可以將 Power BI 編頁報表以各種支援的格式自動匯出，並分散至各種案例。 在本文中，您將使用 Power Automate 自動將 Power BI 編頁報表儲存至商務用 OneDrive 或 SharePoint Online 資料夾。


:::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/paginated-onedrive-flow.png" alt-text="將編頁報表儲存至 OneDrive 或 SharePoint Online 的 Power Automate 流程螢幕擷取畫面":::

在尋找 Power BI 編頁報表的其他 Power Automate 範本嗎？ 請參閱[使用 Power Automate 匯出 Power BI 編頁報表](service-automate-paginated-integration.md)。 

## <a name="prerequisites"></a>Prerequisites  

若要遵循此做法，請確定您有：

- 您的 Power BI 租用戶中至少有一個工作區受保留容量所支援。 此容量可以是 A4/P1 – A6/P3 SKU 中的任何一個。 深入了解 [Power BI Premium 中編頁報表的保留容量](../admin/service-premium-what-is.md#paginated-reports)
- 存取 Power Automate 中的標準連接器，其隨附於任何 Office 365 訂閱。

## <a name="save-a-paginated-report-to-onedrive-for-business-or-a-sharepoint-online-folder"></a>將編頁報表儲存至商務用 OneDrive 或 SharePoint Online 資料夾 

透過任一範本，您會在商務用 OneDrive 或 SharePoint Online 資料夾中，以所需的格式設定編頁報表的定期匯出。 若這是您第一次在 Power Automate 流程中使用 [匯出至編頁報表的檔案] 動作，請參閱此必要條件。 

> [!NOTE]
> 下列步驟與影像會示範如何使用 **Save a Power BI paginated report to OneDrive for Business** (將 Power BI 編頁報表儲存至商務用 OneDrive) 範本來設定流程。 遵循相同的步驟，使用 **Save a Power BI paginated report to a SharePoint Online folder** (將 Power BI 編頁報表儲存至 SharePoint Online 資料夾) 範本來建立流程。 當選取您要匯出編頁報表的位置時，請選取 SharePoint Online 資料夾，而不是商務用 OneDrive 資料夾。 

1. 登入 Power Automate [flow.microsoft.com](https://flow.microsoft.com/)。 
1. 選取 [範本]，然後搜尋  **paginated reports** (編頁報表)。 

    :::image type="content" source="media/service-automate-paginated-integration/power-bi-paginate-automate.png" alt-text="Power Automate 的 Power BI 編頁報表範本螢幕擷取畫面。":::

1. 選取 [將 Power BI 編頁報表儲存至商務用 OneDrive] 或 [將 Power BI 編頁報表儲存至 SharePoint Online 資料夾]。 請確定您已登入 Power BI 與商務用 OneDrive (或 SharePoint Online)。

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-step1.png" alt-text="選取 Power BI 與商務用 OneDrive 範本的螢幕擷取畫面。":::
1. 選取 [繼續]  。  


1. 若要設定流程的定期，請選取 [頻率] 中的選項，然後輸入所需的 [間隔] 值。

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-2-recurrence.png" alt-text="選取流程的定期。":::

1. (選擇性) 選取 [顯示進階選項] 以設定其他 **定期** 參數，包括 **時區**、**開始時間**、**在這幾天內**、**在這幾小時內**，以及 **在這幾分鐘** 內。  

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-3-advanced-recurrence.png" alt-text="顯示定期的進階選項。":::

1. 在 [工作區] 方塊中，選取保留容量中的工作區。 在 [報表] 方塊中，選取您要匯出的所選工作區編頁報表。 在 [匯出格式] 方塊中，選取所需的匯出格式。 您可以選擇指定編頁報表的參數。 若要尋找參數的詳細描述，請參閱 [Power BI REST API 的連接器參考](/connectors/powerbi/#export-to-file-for-paginated-reports)。  

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-4-export-format.png" alt-text="選取編頁報表、工作區與匯出格式。":::

1. 在 [資料夾路徑] 中，選取您要匯出編頁報表的目標商務用 OneDrive 或 SharePoint Online 資料夾。

    :::image type="content" source="media/service-automate-paginated-onedrive-sharepoint/onedrive-template-5-create-file.png" alt-text="選取目的地並建立檔案。":::

1. Power Automate 會自動為您產生 **檔案名稱** 與 **檔案內容**。 您可以變更檔案名稱，但請保留動態產生的 **檔案內容** 值。 

1. 當您完成時，請選取 [下一步] ****  或 [儲存]。 Power Automate 會建立及評估流程，並讓您知道是否找到錯誤。 

1. 若發生錯誤，請選取 [編輯流程] ****  加以修正。 否則，請選取 [上一步] 箭頭以檢視流程詳細資料，並執行新流程。 

    當您執行此流程時，Power Automate 會將指定格式的編頁報表匯出至商務用 OneDrive 或 SharePoint Online。  

## <a name="next-steps"></a>後續步驟

- [使用 Power Automate 匯出 Power BI 編頁報表](service-automate-paginated-integration.md)
- [開始使用 Power Automate](/power-automate/getting-started/)
- 有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)
