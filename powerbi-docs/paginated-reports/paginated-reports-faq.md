---
title: Power BI 中的編頁報表：常見問題集
description: 此文章將回答有關編頁報表的常見問題集。 這些報表均為已高度格式化且具完美像素的輸出，並已基於列印或產生 PDF 用途進行最佳化。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 10/19/2020
ms.openlocfilehash: 7cba43ff6339ce890ca2f4f1744282648eaf877b
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/04/2020
ms.locfileid: "93297908"
---
# <a name="paginated-reports-in-power-bi-faq"></a>Power BI 中的編頁報表：常見問題集 

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

此文章將回答有關編頁報表的常見問題集。 這些報表均為已高度格式化且具完美像素的輸出，並已基於列印或產生 PDF 用途進行最佳化。 它們稱為「編頁」，因為已將它們格式化，使其可適當地符合多個頁面。 編頁報表會以 SQL Server Reporting Services 中的 RDL 報表技術為基礎。 

此文章將回答人們關於 Power BI Premium 中的編頁報表，以及關於報表產生器 (此為用來製作編頁報表的單獨工具) 的許多常見問題。 您需要 Power BI Pro 授權，才能將報表發佈至服務。 只要工作區位於 Power BI Premium 容量，即可在 [我的工作區] 或工作區中發佈及共用編頁報表。 

## <a name="administration"></a>系統管理

### <a name="what-size-premium-capacity-do-i-need-for-paginated-reports"></a>我需要針對編頁報表使用何種大小的 Premium 容量？

編頁報表工作負載可在 P1 - P3 SKU 上使用。  您也可以針對內嵌或/開發案例搭配 A4 – A6 SKU 使用它。

### <a name="what-is-the-maximum-memory-threshold-i-can-put-for-paginated-reports-in-my-capacity"></a>我可以在容量中針對編頁報表放置的記憶體閾值上限為何？

您可以為此工作負載使用最多 100% 的記憶體。

### <a name="how-does-user-access-work-for-paginated-reports"></a>使用者存取如何針對編頁報表運作？

對於編頁報表的使用者存取，與 Power BI 服務中對於所有其他內容的使用者存取相同。 

### <a name="how-do-i-turn-onoff-my-paginated-reports-workload"></a>如何開啟/關閉我的編頁報表工作負載？

容量管理員可以在容量管理員入口網站頁面中，啟用或停用編頁報表工作負載。  根據預設，對於您建立的任何新容量，將開啟工作負載，但直到您上傳第一個編頁報表才會耗用記憶體。  

### <a name="how-can-i-monitor-usage-of-paginated-reports-in-my-tenant"></a>如何在租用戶中監視編頁報表的使用情況？

稽核記錄檔會在下列事件下方詳述此報表類型的使用方式：

- 檢視 Power BI 報表
- 刪除 Power BI 報表
- 建立 Power BI 報表
- 下載 Power BI 報表

相對於 Power BI 報表，ReportType 欄位含有可識別已編頁的值 "PaginatedReport"。

此外，稽核記錄還會針對編頁報表提供下列事件：

- 已將 Power BI 資料集繫結至閘道
- 探索 Power BI 資料來源
- TakeOverDatasource

### <a name="can-i-monitor-this-workload-through-the-premium-capacity-monitoring-app"></a>我可以透過 Premium 容量監視應用程式來監視此工作負載嗎？

您可以透過新索引標籤使用監視功能，其中含有您 Power BI 資料集擁有的相同相關詳細資料。

### <a name="do-i-need-a-pro-license-to-create-and-publish-paginated-reports"></a>我需要 Pro 授權，才能建立並發佈報表嗎？

無需 Pro 授權，您即可將編頁報表上傳至「我的工作區」，前提是它在「進階容量」中。  若為其他工作區，您必須具有 Pro 授權，才能編寫內容並將其發佈給它們。 即使沒有 Pro 授權，我們也鼓勵您下載並使用 Power BI 報表產生器，但若沒有此授權，無法發佈您建立的編頁報表。 

### <a name="what-if-i-have-a-paginated-report-in-a-workspace-and-the-paginated-report-workload-is-turned-off"></a>如果我在工作區中具有編頁報表，而編頁報表工作負載已關閉，該怎麼辦？

您會收到錯誤訊息，而且在重新開啟工作負載之前，將無法檢視報表。 您仍然可以從工作區刪除報表。

### <a name="what-is-the-default-memory-for-each-of-the-premium-skus-that-support-paginated-reports"></a>針對支援編頁報表的每個進階 SKU 預設記憶體為何？

適用於編頁報表之每個 Premium SKU 中的預設記憶體：

- **P1/A4** ：20% 預設值；10% 最小值
- **P2/A5** ：20% 預設值；5% 最小值
- **P3/A6** ：20% 預設值；2.5% 最小值

Power BI 管理員可在管理入口網站中修改預設的記憶體百分比上限。 請參閱 [容量設定] 索引標籤上 [Power BI Premium] 下方的 [編頁報表] 工作負載區段。

:::image type="content" source="media/paginated-reports-faq/paginated-reports-capacity-settings.png" alt-text="[編頁報表容量設定] 索引標籤":::

## <a name="general"></a>一般

### <a name="when-should-i-use-a-paginated-report-vs-a-power-bi-report"></a>何時應使用編頁報表與 Power BI 報表？

如果案例需要已高度格式化且具完美像素的輸出，並已基於列印或產生 PDF 用途進行最佳化，則最適合使用編頁報表。  損益表就是一個您可能想要建立來作為編頁報表之報表類型的良好範例。  

Power BI 報表已針對探索和互動進行最佳化。  銷售報表可讓不同的銷售人員針對其特定區域/產業/客戶，在同一份報表中為資料進行配量，並查看數字如何變化，而此報表最好透過 Power BI 報表來提供。

如需詳細資訊，請參閱[何時使用 Power BI 中的編頁報表](../guidance/report-paginated-or-power-bi.md)。

### <a name="the-documentation-says-power-bi-report-builder-is-the-preferred-authoring-tool-can-i-create-paginated-reports-in-sql-server-data-tools-for-power-bi"></a>此文件指出 Power BI 報表產生器是優先選用的編寫工具。 我可以在適用於 Power BI 的 SQL Server Data Tools 中建立編頁報表嗎？

是，但 Power BI 服務僅允許您一次上傳單一項目；因此，尚不支援作者搭配 SQL Server Data Tools (SSDT) 使用的許多案例。 請參閱稍後可在此常見問題集中取得的完整[不支援功能清單](#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi)。  

### <a name="what-versions-of-report-builder-do-you-support"></a>您支援哪些版本的報表產生器？

我們發行了 Power BI Report Builder，作為 Power BI 服務中編頁報表的主要編寫工具。 從 Microsoft 下載中心安裝 [Power BI 報表產生器](https://aka.ms/pbireportbuilder)。

### <a name="how-do-i-move-existing-reports-i-have-saved-in-sql-server-reporting-services-to-power-bi"></a>如何將已儲存於 SQL Server Reporting Services 中的現有報表移至 Power BI？

GitHub 上的專案現在支援將內容從 SQL Server Reporting Services 移轉至 Power BI。  請在此檢視詳細資料和下載工具：[https://github.com/microsoft/RdlMigration](https://github.com/microsoft/RdlMigration)

### <a name="can-i-open-reports-and-publish-directly-to-the-service"></a>我可以開啟報表並直接發佈至服務嗎？

是。 我們已新增以下支援：從 Power BI Report Builder 開啟報表，並將其直接發佈至服務。

### <a name="what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi"></a>在 Power BI 中，目前尚未支援 SSRS 中的哪些編頁報表功能？

編頁報表目前不支援下列項目：

- 共用資料來源
- 共用資料集
- 鑽研並按一下以連結到其他報表
- 連結的報表
- 自訂字型

如果您嘗試上傳的檔案具有 Power BI 服務中不支援的功能 (切換/排序以外的功能)，就會收到錯誤訊息。

### <a name="what-data-sources-do-you-support-currently-for-paginated-reports"></a>您目前針對編頁報告支援哪些資料來源？

如需資料來源清單，請參閱 [Power BI 編頁報表支援的資料來源](paginated-reports-data-sources.md)一文。 

### <a name="what-authentication-methods-do-you-support"></a>您支援哪些驗證方法？

我們支援 Azure Analysis Services、Azure SQL Database 和 Power BI 資料來源的 SSO。  我們也支援 Azure SQL Database 和 Azure Analysis Services 的 OAuth。  若為其他資料來源，您目前必須在入口網站或閘道中，將使用者名稱和密碼與資料來源一起儲存。  

### <a name="can-i-use-a-power-bi-dataset-as-a-data-source-for-my-paginated-report"></a>我可以使用 Power BI 資料集作為編頁報表的資料來源嗎？

可以，我們支援 Power BI 資料集作為編頁報表的資料來源。

### <a name="can-i-use-stored-procedures-through-the-gateway"></a>我可以透過閘道使用預存程序嗎？

是，SQL Server 資料來源支援透過閘道使用預存程序，那些使用參數的也包含在內。

### <a name="what-export-formats-are-available-for-my-report-in-the-power-bi-service"></a>在 Power BI 服務中，哪些匯出格式可供我的報表使用？

您可以匯出至 Microsoft Excel、Microsoft Word、Microsoft PowerPoint、PDF、.CSV、XML 和 MHTML。

### <a name="can-i-print-paginated-reports"></a>我可以列印編頁報表嗎？

可以，編頁報表亦可使用列印功能，包括全新和改善的列印預覽體驗。 

### <a name="are-e-mail-subscriptions-available-for-paginated-reports"></a>可以針對編頁報表提供電子郵件訂閱嗎？

可以，編頁報表完全支援電子郵件訂閱，而且這些訂閱支援六個不同的檔案格式和參數值。

### <a name="can-i-run-custom-code-in-my-report"></a>我可以在報表中執行自訂程式碼嗎？

是，我們支援在報表中執行程式碼的功能，就像您可以在 SSRS 中所做的。

### <a name="can-i-use-power-bi-embedded-to-embed-my-paginated-reports-into-an-app-im-hosting"></a>我可以使用 Power BI Embedded，將編頁報表內嵌到我代管的應用程式嗎？

SaaS 內嵌 (包括安全內嵌支援) 已可供使用。 對於 PaaS 內嵌，請參閱[為客戶將 Power BI 編頁報表內嵌至應用程式](../developer/embedded/embed-paginated-reports-customers.md)教學課程。

### <a name="can-i-drill-through-from-a-power-bi-report-to-a-paginated-report"></a>我可以從 Power BI 報表鑽研至編頁報表嗎？

是，這可透過搭配您的編頁報表使用 URL 參數來完成。

### <a name="can-i-share-my-paginated-report-content-through-a-power-bi-app"></a>我可以透過 Power BI 應用程式共用編頁報表的內容嗎？

可以，支援使用來自 v1 與 v2 工作區的應用程式部署編頁報表。 

### <a name="will-other-report-specific-features-in-power-bi-like-pinning-report-tiles-to-dashboards-work-with-paginated-reports"></a>Power BI 中的其他報表特定功能 (例如，將報表磚釘選到儀表板) 可搭配編頁報表來運作嗎？

我們計畫要讓報表盡可能地支援服務中相同的主要案例。  在理想的情況下，雖然用來製作這些內容的工具不同，但從取用者觀點來看，這只是其在入口網站清單中的另一份報表。 取用者不在意建立報表的方式；其可完成所需的作業。  此功能同位有個很好的範例就是計劃性的註解支援。 儘管功能本身針對每個報表類型的運作方式可能稍有不同，但您還是能夠針對這兩者使用註解。

### <a name="is-there-a-report-viewer-control-for-paginated-reports-in-the-power-bi-service"></a>Power BI 服務中是否有適用於編頁報表的報表檢視器控制項？

否，目前尚未提供報表檢視器控制項。

### <a name="can-you-search-for-paginated-reports-from-the-new-home-experience-in-the-power-bi-service"></a>您可以從 Power BI 服務中的新 [常用] 體驗搜尋編頁報表嗎？

可以，您目前可以從 [首頁] 搜尋編頁報表。  您也可以在新 [首頁] 體驗的其他部分中看見它們。

## <a name="considerations-and-troubleshooting"></a>考量與疑難排解
使用分頁報表的日期時間欄位時，請記住以下事項。

- 目前有一些與日期時間參數相關的全球化限制。 無論您在 Power BI 報表產生器中如何設計日期時間，都會以美國格式 (MM/DD/YYYY) 來擷取 Power BI 服務中的所有日期時間參數。

在 Power BI 服務中檢視編頁報表時，工作階段可能會逾時，並向使用者顯示下列通知：

:::image type="content" source="media/paginated-reports-faq/expired-session-notification.png" alt-text="編頁報表工作階段已過期通知":::

- 工作階段將會在下列情況中逾時：停止活動 60 分鐘之後、在裝置已遭鎖定或處於非使用中狀態之前，或當報表未顯示於瀏覽器的使用中索引標籤內時。

## <a name="next-steps"></a>後續步驟

- [從 Microsoft 下載中心安裝 Power BI 報表產生器](https://aka.ms/pbireportbuilder)
- [教學課程：建立編頁報表](paginated-reports-quickstart-aw.md)
