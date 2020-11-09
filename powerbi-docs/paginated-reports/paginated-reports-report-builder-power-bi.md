---
title: 什麼是 Power BI Premium 中的編頁報表？
description: 編頁報表目前可在 Power BI 服務中使用。 長期以來，其一直是 SQL Server Reporting Services 中的標準報告格式。 這些報表可以被列印或共用。 您可以完全控制報表的版面配置。 例如，即使資料表跨越多個頁面，它們也會在資料表中顯示所有資料。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: jXTiYJKw1Rs
ms.service: powerbi
ms.subservice: report-builder
ms.topic: overview
ms.date: 10/16/2020
ms.openlocfilehash: 2c136f4d81a9cb1c1904c3a06b58271391c76c23
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/04/2020
ms.locfileid: "93297753"
---
# <a name="what-are-paginated-reports-in-power-bi-premium"></a>什麼是 Power BI Premium 中的編頁報表？

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

*編頁報表* 是設計用來進行列印或共用。 這些報表稱為「編頁」，因為已將其格式化，可適當地符合頁面。 即使資料表跨越多個頁面，它們也會在資料表中顯示所有資料。 它們亦稱為「完美像素」，因為您可以完全控制其報表頁面配置。 Power BI 報表產生器是撰寫 Power BI 服務編頁報表的獨立工具。 

如已準備好開始，以下是一些快速連結：

- [從 Microsoft 下載中心安裝 Power BI 報表產生器](https://aka.ms/pbireportbuilder)
- [教學課程：建立編頁報表](paginated-reports-quickstart-aw.md)
- [範例 Power BI 編頁報表](paginated-reports-samples.md)
- 正在尋找 Power BI 報表伺服器或 SQL Server Reporting Services 報表產生器的相關資訊嗎？ 請改參閱[安裝報表產生器 - Power BI 報表伺服器](../report-server/install-report-builder.md)。

編頁報表通常會有許多頁面。 例如，此報表有 563 頁。 每頁都有精確的版面配置，每個發票一頁並重複頁首和頁尾。

![分頁](media/paginated-reports-report-builder-power-bi/power-bi-paginated-wwi-report-page.png)

您可在報表產生器中預覽報表，然後將其發佈至 Power BI 服務 (app.powerbi.com) 中。 您需要 Power BI Pro 授權，才能將報表發佈至服務。 只要工作區位於 Power BI Premium 容量，即可在 [我的工作區] 或工作區中發佈及共用編頁報表。 此外，Power BI 系統管理員需要在 Power BI 管理入口網站的 [Premium 容量區段](../admin/service-admin-premium-workloads.md#paginated-reports)中啟用分頁報表。 

## <a name="compare-power-bi-reports-and-paginated-reports"></a>比較 Power BI 報表和編頁報表

編頁報表的主要優點是能夠列印資料表中的所有資料 (不論多久)。 您在 Power BI 報表中放置資料表的圖片。 您會在頁面的資料表中看到其部分資料列，且可以使用捲軸來查看其餘部分。 如果列印該頁面或將其匯出成 PDF，則唯一列印的資料列就是在頁面上看到的。 

現在假設將相同的資料表放在編頁報表中。 將其列印或匯出成 PDF 時，編頁報表會有所需的所有頁數，可列印該資料表中的每個資料列。 

在下列影片中，Microsoft 最具價值的專家 - 資料平台 Peter Myers，以及主要專案經理 Chris Finlan 會示範如何以這兩種報表格式來列印類似的資料表。 

<iframe width="560" height="315" src="https://www.youtube.com/embed/jXTiYJKw1Rs?list=PL1N57mwBHtN1icIhpjQOaRL8r9G-wytpT" frameborder="0" allowfullscreen></iframe>

這段影片是以八個模組為基礎的影片課程一部分，[一天中的 Power BI 編頁報表](../learning-catalog/paginated-reports-online-course.md)。 這堂課程的設計旨在讓您 (報表作者) 具備建立、發佈及散發 Power BI 編頁報表所需的技術知識。

## <a name="create-reports-in-power-bi-report-builder"></a>在 Power BI 報表產生器中建立報表

分頁報表有自己的設計工具，也就是 Power BI 報表產生器。 這是一種新工具，會和您先前用來建立 Power BI 報表伺服器或 SQL Server Reporting Services (SSRS) 分頁報表的工具共用相同的基礎。 實際上，您為 SSRS 2016 和 2017 或 Power BI 報表伺服器內部部署建立的編頁報表是與 Power BI 服務相容的。 Power BI 服務維持回溯相容性，因此您可以繼續向前進行報表，並且可以升級任何舊版的編頁報表。 並非所有報表功能都能在啟動時使用。 如需詳細資料，請參閱本文中的[限制與考量](#limitations-and-considerations)。
     
## <a name="report-from-a-variety-of-data-sources"></a>來自各種資料來源的報表

單一的編頁報表可以包含許多不同的資料來源。 與 Power BI 報表不同，它沒有基礎資料模型。 針對 Power BI 服務中編頁報表的初始版本，您可以在報表本身中建立內嵌的資料來源和資料集。 目前，您無法使用共用資料來源或共用資料集。 您可以在本機電腦上的報表產生器中建立報表。 如果報表連接至內部部署資料，則在將報表上傳至 Power BI 服務之後，您需要建立閘道並重新導向資料連線。 以下是您此時可以連線到的資料來源：

- Azure SQL Database 和資料倉儲 (透過基本和 oAuth)
- Azure Analysis Services (透過 SSO)
- 透過閘道的 SQL Server
- 透過閘道的 SQL Server Analysis Services
- Power BI 資料集
- Oracle
- Teradata

## <a name="design-your-report"></a>設計報表  

### <a name="create-paginated-reports-with-matrix-chart-and-free-form-layouts"></a>使用矩陣、圖表和自由形式配置建立編頁報表

資料表報表適用於資料行型的資料。 矩陣報表 (如交叉分析或樞紐分析表報表) 很適合用於摘要資料。 圖表報表能以圖形化格式呈現資料，而自由形式的「清單」報表則可以呈現幾乎所有其他類型的資料 (例如發票)。 
  
您可以從其中一個報表產生器精靈開始。 資料表、矩陣和圖表精靈將引導您建立內嵌的資料來源連線和內嵌的資料集。 然後拖放欄位以建立資料集查詢、選取配置和樣式，並自訂報表。  
  
使用地圖精靈，可以建立根據地理或幾何背景顯示彙總資料的報表。 地圖資料可以是來自 Transact-SQL 查詢或美國環境系統研究所公司(ESRI) 形狀檔的空間資料。 您還可以加入 Microsoft Bing 地圖底圖背景。  

### <a name="add-more-to-your-report"></a>新增其他項目至您的報表

透過篩選、分組和排序資料，或是加入公式和運算式來修改資料。 加入圖表、量測計、走勢圖和指標，以視覺格式摘要資料。  使用參數和篩選來篩選自訂檢視的資料。 內嵌或參考影像與其他資源，包括外部內容。  

編頁報表中的所有內容 (從報表本身到每個文字方塊、影像、資料表和圖表) 都有一系列屬性，您可以設定這些屬性以使報表看起來完全符合您的要求。

## <a name="creating-a-report-definition"></a>建立報表定義

在設計編頁報表時，您實際上是在建立報表定義。 它不包含資料。 它會指定要取得資料的位置、要取得哪些資料，以及如何顯示資料。 當您執行報表時，報表處理器會採用您所指定的報表定義、擷取資料，並結合報表配置來產生報表。 您可以將報表定義上傳至 Power BI 服務 (`https://app.powerbi.com`) 中，也可以上載到 [我的工作區] 或是與同事共用的工作區。 如果報表資料來源位於內部部署，則在上傳報表之後，您可以將資料來源連線重新導向為通過閘道。 

## <a name="view-your-paginated-report"></a>檢視您的編頁報表
您可以在瀏覽器中以及 Power BI 行動裝置應用程式中查看 Power BI 服務中的編頁報表。 從 Power BI 服務中，您可以將報表匯出為多種格式，例如 HTML、MHTML、PDF、XML、CSV、TIFF、Word 和 Excel。 您也可以與其他人共用它。  

## <a name="create-a-subscription-to-your-report"></a>建立您報表的訂閱

您現在可以為您自己和其他人設定 Power BI 服務中分頁報表的電子郵件訂閱。 在一般情況下，流程與訂閱 Power BI 服務中的報表與儀表板相同。 在訂閱設定中，選擇您希望收到電子郵件的頻率：每天、每週或每小時。 訂閱會包含整個報表輸出的 PDF 附件。

如需詳細資料，請參閱[為您自己和其他人訂閱 Power BI 服務中的分頁報表](../consumer/paginated-reports-subscriptions.md)一文。 

## <a name="limitations-and-considerations"></a>限制與考量

以下是初始版本中不支援的一些其他功能：

- 將報表頁面或視覺效果釘選到 Power BI 儀表板。 您仍然可以從位於 Power BI 報表伺服器或 Reporting Services 報表伺服器上的內部部署編頁報表，將視覺效果釘選到 Power BI 儀表板。 請參閱[將 Reporting Services 項目釘選至 Power BI 儀表板](/sql/reporting-services/pin-reporting-services-items-to-power-bi-dashboards)以取得更多資訊。
- 文件對應。
- 鑽研報表。  請考慮使用 URL 參數搭配編頁報表來鑽研案例。
- 共用的資料來源和共用資料集。

 
## <a name="next-steps"></a>後續步驟

- [從 Microsoft 下載中心安裝 Power BI 報表產生器](https://aka.ms/pbireportbuilder)
- [教學課程：建立編頁報表](paginated-reports-quickstart-aw.md)
- [線上課程：Power BI 編頁報表一日上手](../learning-catalog/paginated-reports-online-course.md)
- [範例 Power BI 編頁報表](paginated-reports-samples.md)
- [直接在編頁報表中輸入資料](paginated-reports-enter-data.md)
- [教學課程：為客戶將 Power BI 編頁報表內嵌至應用程式](../developer/embedded/embed-paginated-reports-customers.md)