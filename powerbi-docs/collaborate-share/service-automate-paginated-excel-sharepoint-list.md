---
title: 匯出 Excel 網頁版資料表或 SharePoint 清單中每個資料列的編頁報表
description: 在本文中，您將使用 Power Automate 自動匯出 Excel 網頁版資料表或 SharePoint Online 清單中每個資料列的編頁報表。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 11/17/2020
LocalizationGroup: Get started
ms.openlocfilehash: 74d61d40c4447f2649f5cce5fbcdcba68cd31afe
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96407990"
---
# <a name="export-a-paginated-report-for-each-row-in-an-excel-online-table-or-sharepoint-list"></a>匯出 Excel 網頁版資料表或 SharePoint 清單中每個資料列的編頁報表

透過 [Power Automate](/power-automate/getting-started)，您可以將 Power BI 編頁報表以各種支援的格式自動匯出，並分散至各種案例。 在本文中，您將使用 Power Automate 範本，自動設定單一或多個編頁報表的週期性匯出。 您將以所需的格式匯出 Excel 網頁版資料表或 SharePoint Online 清單中的每個資料列。 您可以將匯出的編頁報表分散至商務用 OneDrive 或 SharePoint Online 網站，或是透過 Office 365 Outlook 以電子郵件傳送。

:::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-overview.png" alt-text="使用 Excel 網頁版資料表匯出編頁報表。":::

Excel 網頁版資料表或 SharePoint Online 清單中的每個資料列都可以代表單一使用者，以訂閱基礎來接收編頁報表。 相反地，每個資料列也可以代表您要分散的唯一編頁報表。 您的資料表或清單需要有指定如何分散報表的資料行 (無論是 OneDrive、SharePoint Online 或 Outlook)。 Power Automate 流程會在其 Switch 陳述式中使用此資料行。

在尋找 Power BI 編頁報表的其他 Power Automate 範本嗎？ 請參閱[使用 Power Automate 匯出 Power BI 編頁報表](service-automate-paginated-integration.md)。

## <a name="prerequisites"></a>Prerequisites  

若要遵循此做法，請確定您有：

- 您的 Power BI 租用戶中至少有一個工作區受保留容量所支援。 此容量可以是 A4/P1 – A6/P3 SKU 中的任何一個。 請前往 [Power BI Premium 中的保留容量](../admin/service-premium-what-is.md)閱讀更多內容。
- 存取 Power Automate 中的標準連接器，其隨附於任何 Office 365 訂閱。
- 若您正在使用 Excel 網頁版資料表，則必須將其格式化為 Excel 中的資料表。 若要深入了解，請參閱[建立資料表](https://support.microsoft.com/office/create-a-table-in-excel-bf0ce08b-d012-42ec-8ecf-a2259c9faf3f)。

## <a name="export-a-paginated-report-for-each-row-in-a-table-or-list"></a>匯出資料表或清單中每個資料列的編頁報表

> [!NOTE]
> 下列步驟與影像會示範如何使用 **Export a Power BI paginated report for each row in an Excel Online table** (為 Excel Online 資料表中的各個資料列匯出 Power BI 編頁報表) 範本來設定流程。 您可以遵循相同的步驟，使用 **Export a Power BI paginated report for items in a SharePoint Online list** (為 SharePoint Online 中的項目匯出 Power BI 編頁報表) 範本來建立流程。 SharePoint Online 清單會包含如何匯出編頁報表的相關資訊，而不是 Excel Online 資料表。  

1. 登入 Power Automate [flow.microsoft.com](https://flow.microsoft.com/)。 
1. 選取 [範本]，然後搜尋  **paginated reports** (編頁報表)。 

    :::image type="content" source="media/service-automate-paginated-integration/power-bi-paginate-automate.png" alt-text="Power Automate 的 Power BI 編頁報表範本螢幕擷取畫面。":::

1. 選取 **Export a Power BI paginated report for each row in an Excel Online table** (為 Excel 網頁版資料表中的各個資料列匯出 Power BI 編頁報表) 或 **Export a Power BI paginated report for items in a SharePoint Online list** (為 SharePoint Online 中的項目匯出 Power BI 編頁報表) 範本。 請確定您已登入 Excel 網頁版、Power BI、商務用 OneDrive、SharePoint Online，以及 Office 365 Outlook。 選取 [繼續]  。  

   :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-excel-online-1.png" alt-text="匯出 Excel 網頁版資料表中每個資料列的 Power BI 編頁報表。":::

1. 若要設定流程的定期，請選取 [頻率] 中的選項，然後輸入所需的 [間隔] 值。

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-recurrence-2.png" alt-text="選取流程的定期。":::

1. (選擇性) 選取 [顯示進階選項] 以設定其他 **定期** 參數，包括 **時區**、**開始時間**、**在這幾天內**、**在這幾小時內**，以及 **在這幾分鐘** 內。

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-advanced-recurrence-3.png" alt-text="您可以選取進階定期選項。":::

1. 在 [位置] 方塊中，選取 [商務用 OneDrive] 或儲存您的 Excel 網頁版資料表或 SharePoint Online 清單所在的 [SharePoint Online 網站]。 然後從下拉式清單中選取 [文件庫]。

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-location-4.png" alt-text="選取 Excel 網頁版資料表的位置。":::

1. 在 [檔案] 方塊中選取 Excel 網頁版檔案或 SharePoint Online 清單。 從 [資料表] 方塊的下拉式清單中，選取資料表或清單的名稱。 
 
    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-file-table-5.png" alt-text="選取 Excel 網頁版檔案與資料表的名稱。":::

    > [!TIP]
    > 如需了解如何將資料格式化為 Excel 中的資料表，請參閱[建立資料表](https://support.microsoft.com/office/create-a-table-in-excel-bf0ce08b-d012-42ec-8ecf-a2259c9faf3f)。 

1. 將要用於檔案名稱的變數初始化。 您可以保留或修改 [名稱] 與 [值] 的預設值，但要保留 [類型] 等於 [字串]。  

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-name-type-6.png" alt-text="填寫 [名稱] 與 [值]，並保留 [類型] 等於 [字串]。":::

1. 在 [套用到每個] 中，[從上一個步驟選取輸出] 方塊會根據預設設定為 **值**。 此設定會逐一查看 Excel 網頁版資料表或 SharePoint Online 清單中每個資料列 [套用到每個] 中所包含的動作。  

1. 在 [工作區] 方塊中，選取專用容量中的工作區。 在 [報表] 方塊中，選取您要匯出的所選工作區編頁報表。 若您從下拉式清單中設定 [輸入自訂值]，您可以將 [工作區] 與 [報表] 設定為等於 Excel 網頁版資料表或 SharePoint Online 清單中的資料行。 這些資料行應分別包含「工作區識別碼」與「報表識別碼」。  

1. 從下拉式清單中選取 [匯出格式]，或將其設定為等於包含所需匯出格式的 Excel 網頁版資料表資料行。 例如 PDF、DOCX 或 PPTX。 您可以選擇指定編頁報表的參數。 若要尋找參數的詳細描述，請參閱 [Power BI Rest API 的連接器參考](/connectors/powerbi/#export-to-file-for-paginated-reports)。

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-export-format-9.png" alt-text="填寫 [匯出至編頁報表的檔案]。":::

1. 匯出之後，在 [值] 方塊中輸入編頁報表的名稱。 請務必輸入副檔名。 您可以靜態設定，例如 .pdf、.docx 或 .pptx。 或是透過選取 Excel 資料表中對應到所需匯出格式的資料行以動態設定。 

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-output-value-10.png" alt-text="選取報表的名稱與副檔名。":::

1. 在 [切換] 動作中，將 Excel 網頁版資料表中對應到所需傳遞方法的資料行填入 [開啟] 方塊：[OneDrive]、[SharePoint]，或 [電子郵件]。 

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-switch-11.png" alt-text="在 [切換] 中，將 Excel 網頁版資料表中的資料行填入 [開啟] 方塊。":::

1. 在 [案例]、[案例 2] 與 [案例 3] 中，輸入在上一個步驟中所選 Excel 網頁版資料表資料行中出現的值。  

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-case-1-2-3-12.png" alt-text="輸入 [案例]、[案例 2] 與 [案例 3] 的值。":::

1. 若您要將編頁報表儲存至 OneDrive，請選取要儲存的 **資料夾路徑**。  

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-case-onedrive-13.png" alt-text="若您要儲存到 OneDrive。":::

1. 若您要將編頁報表儲存至 SharePoint Online，請輸入 **網站位址**，以及儲存該報表的 **資料夾路徑**。 

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-case-sharepoint-14.png" alt-text="若您要將編頁報表儲存至 SharePoint Online。":::

1. 若您要透過 Outlook 以電子郵件傳送編頁報表，請填入 [收件人]、[主旨]，以及 [本文]  方塊。 這些方塊可能會包含靜態內容，或是包含 Excel 網頁版資料表或 SharePoint Online 清單中的動態內容。 Power Automate 會自動將您的編頁報表附加到此電子郵件。  

    :::image type="content" source="media/service-automate-paginated-excel-sharepoint-list/excel-template-case-email-15.png" alt-text="若您是透過 Outlook 以電子郵件傳送編頁報表。":::

1. 當您完成時，請選取 [下一步] ****  或 [儲存]。 Power Automate 會建立及評估流程，並讓您知道是否找到錯誤。 

1. 若發生錯誤，請選取 [編輯流程] ****  加以修正。 否則，請選取 [返回] 箭頭以檢視流程詳細資料，並執行新流程。 


## <a name="next-steps"></a>後續步驟

- [使用 Power Automate 匯出 Power BI 編頁報表](service-automate-paginated-integration.md)
- [開始使用 Power Automate](/power-automate/getting-started/)
- 有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)

