---
title: 使用 Power Automate 匯出編頁報表
description: 了解如何建立匯出 Power BI 編頁報表的 Power Automate 流程。
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 11/17/2020
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: 7cc3969b735c64de39ac41fdc6acf2152c4cda35
ms.sourcegitcommit: 8afdd3601209636c9ab92d75f967d4ee0a2cab26
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2020
ms.locfileid: "95011943"
---
# <a name="export-power-bi-paginated-reports-with-power-automate"></a>使用 Power Automate 匯出 Power BI 編頁報表

透過 [Power Automate](/power-automate/getting-started)，您可以將 Power BI 編頁報表以各種支援的格式自動匯出，並分散至各種案例。 在本文中，您將了解要使用哪些範本來建置您自己的流程，以匯出您的編頁報表。  

## <a name="prerequisites"></a>Prerequisites  

若要遵循此做法，請確定您有：

- 您的 Power BI 租用戶中至少有一個工作區受保留容量所支援。 此容量可以是 A4/P1 – A6/P3 SKU 中的任何一個。 請前往 [Power BI Premium 中的保留容量](../admin/service-premium-what-is.md)閱讀更多內容。
- 存取 Power Automate 中的標準連接器，其隨附於任何 Office 365 訂閱。

## <a name="create-a-flow-from-a-template"></a>從範本建立流程 

1. 登入 Power Automate [flow.microsoft.com](https://flow.microsoft.com/)。 
1. 選取 [範本]，然後搜尋  **paginated reports** (編頁報表)。 

    :::image type="content" source="media/service-automate-paginated-integration/power-bi-paginate-automate.png" alt-text="Power Automate 的 Power BI 編頁報表範本螢幕擷取畫面。":::

## <a name="select-a-template"></a>選取範本 

從清單中選取範本，以透過逐步解說開始使用。  

- [將 Power BI 編頁報表儲存至商務用 OneDrive 或 SharePoint Online 資料夾](service-automate-paginated-onedrive-sharepoint.md)。  
- [匯出 SharePoint Online 中項目的 Power BI 編頁報表，或是 Excel 網頁版資料表中每個資料列的 Power BI 編頁報表](service-automate-paginated-excel-sharepoint-list.md)。
- 將 Power BI 編頁報表儲存到本機系統資料夾。

## <a name="next-steps"></a>後續步驟

- [編頁報表的 Power BI 匯出 API](../developer/embedded/export-paginated-report.md)
- [開始使用 Power Automate](/power-automate/getting-started/)
- 有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)
