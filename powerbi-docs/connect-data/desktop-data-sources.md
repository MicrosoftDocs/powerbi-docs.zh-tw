---
title: Power BI Desktop 中的資料來源
description: Power BI Desktop 中的資料來源
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 12/10/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 038d0fc4b136f89db290010289d24ee41454c9ea
ms.sourcegitcommit: 772c65b7b440ab082510bf3f64b871d19139d451
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2020
ms.locfileid: "97353327"
---
# <a name="data-sources-in-power-bi-desktop"></a>Power BI Desktop 中的資料來源

有了 Power BI Desktop，您可以從許多不同來源連接至資料。 如需可用資料來源的完整清單，請參閱 [Power BI 資料來源](power-bi-data-sources.md)。

您可以使用 [首頁] 功能區連接到資料。 若要顯示 [最常見] 資料類型功能表，請選取 [取得資料] 按鈕標籤或向下箭號。

![[最常見] 資料類型功能表，Power BI Desktop 中的 [取得資料]](media/desktop-data-sources/data-sources-01.png)

若要移至 [取得資料] 對話方塊，請顯示 [最常見] 資料類型功能表，然後選取 [更多]。 您也可以透過直接選取 [取得資料] 圖示，叫出 [取得資料] 對話方塊 (並略過 [最常見] 功能表)。

![[取得資料] 按鈕，Power BI Desktop](media/desktop-data-sources/data-sources-02.png)

> [!NOTE]
> Power BI 小組會持續將可用的資料來源擴充到 Power BI Desktop 與 Power BI 服務。 因此，您經常會看到舊版工作進行中的資料來源標示為 **Beta** 或「預覽」。 任何標示為「搶鮮版 (Beta)」 或「預覽」的資料來源，受到的支援與功能都有限制，而且不應該用在生產環境。 此外，任何為 Power BI Desktop 標記為「搶鮮版 (Beta)」或「預覽」的資料來源都無法在公開推出 (GA) 前於 Power BI 服務或其他 Microsoft 服務中使用。

> [!NOTE]
> Power BI Desktop 有許多資料連接器需要 Internet Explorer 10 (或更新版本) 才能進行驗證。 


## <a name="data-sources"></a>資料來源

[取得資料] 對話方塊會組織下列類別中的資料類型：

* 全部
* 檔案
* 資料庫
* Power Platform
* Azure
* 線上服務
* 其他

[全部]  類別包含所有類別的所有資料連線類型。

### <a name="file-data-sources"></a>檔案資料來源

[檔案]  類別提供下列資料連線：

* Excel
* 文字/CSV
* XML
* JSON
* 資料夾
* PDF
* SharePoint 資料夾

下圖顯示 [檔案]  的 [取得資料] 視窗。

![檔案資料來源，[取得資料] 對話方塊，Power BI Desktop](media/desktop-data-sources/data-sources-03.png)

### <a name="database-data-sources"></a>資料庫資料來源

[資料庫]  類別提供下列資料連線：

* SQL Server 資料庫
* Access 資料庫
* SQL Server Analysis Services 資料庫
* Oracle 資料庫
* IBM Db2 資料庫
* IBM Informix 資料庫 (搶鮮版 (Beta))
* IBM Netezza
* MySQL 資料庫
* PostgreSQL 資料庫
* Sybase 資料庫
* Teradata 資料庫
* SAP HANA 資料庫
* SAP Business Warehouse 應用程式伺服器
* SAP Business Warehouse 訊息伺服器
* Amazon Redshift
* Impala
* Google BigQuery
* Vertica
* Snowflake
* Essbase
* AtScale Cube
* Data Virtuality LDW (搶鮮版 (Beta))
* Denodo
* Dremio
* Exasol
* Indexima
* InterSystems IRIS (搶鮮版 (Beta))
* Jethro (搶鮮版 (Beta))
* Kyligence
* Linkar PICK Style / MultiValue Databases (搶鮮版 (Beta))
* MariaDB (搶鮮版 (Beta))
* MarkLogic
* BI 連接器
* Actian (搶鮮版 (Beta))

> [!NOTE]
> 某些資料庫連接器的啟用方式為選取 **[檔案] > [選項和設定] > [選項]** ，然後選取 [預覽功能] 並啟用該連接器。 如果您沒有看到上述連接器，但想要加以使用，請檢查您的 [預覽功能] 設定。 亦請注意，任何標示為 *Beta* 或「預覽」的資料來源，受到的支援和功能都有限制，不應該用在生產環境。

下圖顯示 [資料庫]  的 [取得資料] 視窗。

![資料庫資料來源，[取得資料] 對話方塊，Power BI Desktop](media/desktop-data-sources/data-sources-04.png)

### <a name="power-platform-data-sources"></a>Power Platform 資料來源

**Power Platform** 類別提供下列資料連線：

* Power BI 資料集
* Power BI 資料流程
* Microsoft Dataverse
* Power Platform 資料流程 (搶鮮版 (Beta))

下圖顯示 **Power Platform** 的 [取得資料] 視窗。

![Power Platform 資料來源，[取得資料] 對話方塊，Power BI Desktop](media/desktop-data-sources/data-sources-05.png)

### <a name="azure-data-sources"></a>Azure 資料來源

[Azure]  類別提供下列資料連線：

* Azure SQL Database
* Azure Synapse Analytics (SQL DW)
* Azure Analysis Services 資料庫
* 適用於 PostgreSQL 的 Azure 資料庫
* Azure Blob 儲存體
* Azure 表格儲存體
* Azure Cosmos DB
* Azure 資料總管 (Kusto)
* Azure Data Lake Storage Gen2
* Azure Data Lake Storage Gen1
* Azure HDInsight (HDFS)
* Azure HDInsight Spark
* HDInsight 互動式查詢
* Azure 成本管理
* Azure Databricks
* Azure 時間序列深入解析 (Beta)


下圖顯示 [Azure]  的 [取得資料] 視窗。

![Azure 資料來源，[取得資料] 對話方塊，Power BI Desktop](media/desktop-data-sources/data-sources-06.png)

### <a name="online-services-data-sources"></a>線上服務資料來源

[線上服務] 類別提供下列資料連線：

* SharePoint Online 清單
* Microsoft Exchange Online
* Dynamics 365 (線上)
* Dynamics NAV
* Dynamics 365 Business Central
* Dynamics 365 Business Central (內部部署)
* Microsoft Azure 使用量見解 (搶鮮版 (Beta))
* Azure DevOps (僅限 Boards)
* Azure DevOps Server (僅限 Boards)
* Salesforce 物件
* Salesforce 報表
* Google Analytics
* Adobe Analytics
* appFigures (搶鮮版 (Beta))
* Data.World - 取得資料集 (搶鮮版 (Beta))
* GitHub (Beta)
* LinkedIn Sales Navigator (搶鮮版 (Beta))
* Merketo (搶鮮版 (Beta))
* Mixpanel (搶鮮版 (Beta))
* Planview Enterprise One - PRM (搶鮮版 (Beta))
* QuickBooks Online (搶鮮版 (Beta))
* Smartsheet
* SparkPost (搶鮮版 (Beta))
* SweetIQ (搶鮮版 (Beta))
* Planview Enterprise One - CTM (搶鮮版 (Beta))
* Twilio (搶鮮版 (Beta))
* Zendesk (搶鮮版 (Beta))
* Asana (搶鮮版 (Beta))
* Dynamics 365 Customer Insights (搶鮮版 (Beta))
* Emigo 資料來源
* Entersoft 商務套件 (搶鮮版 (Beta))
* FactSet Analytics
* Palantir Foundry
* 企業 App Store
* Intune 資料倉儲 (搶鮮版 (Beta))
* Microsoft Graph 安全性 搶鮮版 (Beta)
* Projectplace for Power BI
* Product Insights (搶鮮版 (Beta))
* Quick Base
* Spigit (搶鮮版 (Beta))
* TeamDesk (搶鮮版 (Beta))
* Webtrends 分析 (搶鮮版 (Beta))
* Witivio (搶鮮版 (Beta))
* 工作場所分析 (搶鮮版 (Beta))
* Zoho Creator (搶鮮版 (Beta))
* eWay-CRM (搶鮮版 (Beta))
* Hexagon PPM 智慧型 API


下圖顯示 [線上服務] 的 [取得資料] 視窗。

![線上服務資料來源，[取得資料] 對話方塊，Power BI Desktop](media/desktop-data-sources/data-sources-07.png)

### <a name="other-data-sources"></a>其他資料來源

[其他]  類別提供下列資料連線：

* Web
* SharePoint 清單
* OData 摘要
* Active Directory
* Microsoft Exchange
* Hadoop 檔案 (HDFS)
* Spark
* Hive LLAP
* R 指令碼
* Python 指令碼
* ODBC
* OLE DB
* Acterys：模型自動化與規劃 (搶鮮版 (Beta))
* Automation Anywhere (搶鮮版 (Beta))
* Solver
* Cherwell (搶鮮版 (Beta))
* Cognite Data Fusion (搶鮮版 (Beta))
* FHIR
* Information Grid (搶鮮版 (Beta))
* Jamf Pro (搶鮮版 (Beta))
* MicroStrategy for Power BI
* Paxata
* QubolePresto (搶鮮版 (Beta))
* Roamler (搶鮮版 (Beta))
* Shortcuts 商業見解 (搶鮮版 (Beta))
* Siteimprove (搶鮮版 (Beta))
* SurveyMonkey 搶鮮版 (Beta)
* Tenforce (Smart)List
* TIBCO(R) Data Virtualization (搶鮮版 (Beta))
* Vena (搶鮮版 (Beta))
* Vessel 見解 (搶鮮版 (Beta))
* Zucchetti HR Infinity (搶鮮版 (Beta))
* Anaplan Connector v1.0 (搶鮮版 (Beta))
* Starburst Enterprise Presto (搶鮮版 (Beta))
* 空白查詢



下圖顯示 [其他]  的 [取得資料] 視窗。

![Power BI Desktop 中的其他資料來源](media/desktop-data-sources/data-sources-08.png)

> [!NOTE]
> 目前無法連線至使用 Azure Active Directory 保護的自訂資料來源。

### <a name="template-apps"></a>範本應用程式

您可以透過選取 [取得資料] 視窗底部附近的 [範本應用程式] 連結來尋找您組織的範本應用程式。 

![Power BI Desktop 中 [其他資料來源] 的 [取得資料] 對話方塊](media/desktop-data-sources/data-sources-12.png)

可用的範本應用程式可能會根據您的組織而有所不同。

## <a name="connecting-to-a-data-source"></a>連線到資料來源

若要連接至資料來源，請從 [取得資料]  視窗選取資料來源，然後選取 [連接] 。 在下圖中，從 [其他]  資料連線類別選取了 [Web]  。

![連線到網路，[取得資料] 對話方塊，Power BI Desktop](media/desktop-data-sources/data-sources-08.png)

隨即會顯示資料連線類型特有的連線視窗。 如果需要認證，將提示您提供它們。 下圖顯示輸入 URL 以連接到 Web 資料來源。

![輸入 URL，[從 Web] 對話方塊，Power BI Desktop](media/desktop-data-sources/datasources-fromwebbox.png)

輸入 URL 或資源連線資訊，然後選取 [確定]。 Power BI Desktop 會建立資料來源的連線，並在 [導覽器] 中呈現可用的資料來源。

![[群組] 對話方塊，Power BI Desktop](media/desktop-data-sources/datasources-fromnavigatordialog.png)

若要載入資料，請從 [導覽器] 窗格底端選取 [載入] 按鈕。 若要在載入資料之前先轉換或編輯 Power Query 編輯器中的查詢，請選取 [轉換資料] 按鈕。

這就是連接到 Power BI Desktop 中資料來源的全部資訊！ 嘗試連接到我們持續增加的資料來源，並經常回來查看，我們隨時會增加新的來源。

## <a name="using-pbids-files-to-get-data"></a>使用 PBIDS 檔案來取得資料

PBIDS 檔案是具有特定結構的 Power BI Desktop 檔案，而且它們具有 .PBIDS 副檔名，以識別它是 Power BI 資料來源檔案。

您可以建立 PBIDS 檔案以簡化組織中新報表建立者或初學者的 **取得資料** 體驗。 如果您從現有的報表建立 PBIDS 檔案，建立報表的初學者便能更輕鬆地從從相同的資料建置新報表。

當作者開啟 PBIDS 檔案時，Power BI Desktop 會開啟並提示使用者提供認證來進行驗證，並連線到檔案中指定的資料來源。 [瀏覽] 對話方塊隨即出現，而且使用者必須從該資料來源選取要載入至模型的資料表。 如果未在 PBIDS 檔案中指定的話，使用者可能也需要選取資料庫與連線模式。

之後，使用者可以開始建置視覺效果，或選取 [最近的來源] 以將一組新的資料表載入模型中。

PBIDS 檔案目前在一個檔案中只支援一個資料來源。 指定一個以上的資料來源會導致錯誤。


### <a name="how-to-create-a-pbids-connection-file"></a>如何建立 PBIDS 連線檔案

如果您的現有 Power BI Desktop (.PBIX) 已連線到您感興趣的資料，則只要將這些連線檔案從 Power BI Desktop 匯出即可。 建議您使用此方法，因為可以從 Desktop 自動產生 PBIDS 檔案。 此外，您仍然可以在文字編輯器中編輯或手動建立檔案。 

若要建立 PBIDS 檔案，請選取 [檔案] > [選項及設定] > [資料來源設定]：

![[資料來源設定] 功能表選項](media/desktop-data-sources/data-sources-09.png)

在出現的對話方塊中，選取您想要匯出為 PBIDS 的資料來源，然後選取 [匯出 PBIDS]。

![[資料來源設定] 對話方塊](media/desktop-data-sources/data-sources-10.png)

當您選取 [匯出 PBIDS] 按鈕時，Power BI Desktop 會產生 PBIDS 檔案，您可以將其重新命名並儲存在目錄中，並與其他人共用。 您也可以在文字編輯器中開啟檔案，並進一步修改檔案，包括在檔案本身指定連線模式，如下圖所示。 

![使用文字編輯器修改 PBIDS 檔案](media/desktop-data-sources/data-sources-11.png)

如果您想要手動在文字編輯器中建立 PBIDS 檔案，則必須指定單一連線的必要輸入，並以 PBIDS 副檔名儲存檔案。 (選擇性) 您也可以將連線模式指定為 DirectQuery 或 Import。 若檔案中缺少 **mode** 或為 Null，則會提示在 Power BI Desktop 中開啟檔案的使用者選取 [DirectQuery] 或 [匯入]。


### <a name="pbids-file-examples"></a>PBIDS 檔案範例

此節提供一些來自常用資料來源的範例。 PBIDS 檔案類型只支援 Power BI Desktop 中也支援的資料連線，但有下列例外：Wiki URL、Live Connect 與空白查詢。

PBIDS 檔案不包含驗證資訊與資料表和結構描述資訊。  

下列程式碼片段顯示數個常見的 PBIDS 檔案範例，但它們並不完整。 針對其他資料來源，您可以參考[資料來源參考 (DSR) 格式，以取得通訊協定和位址資訊 ](/azure/data-catalog/data-catalog-dsr#data-source-reference-specification) \(部分機器翻譯\)。

若您編輯或手動建立連線檔案，這些範例只是為了方便起見，它們並不完整，而且不包含 DSR 格式的所有支援連接器。

#### <a name="azure-as"></a>Azure AS

```json
{ 
    "version": "0.1", 
    "connections": [ 
    { 
        "details": { 
        "protocol": "analysis-services", 
        "address": { 
            "server": "server-here" 
        }, 
        } 
    } 
    ] 
}
```

#### <a name="folder"></a>資料夾

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "folder", 
        "address": { 
            "path": "folder-path-here" 
        } 
      } 
    } 
  ] 
} 
```

#### <a name="odata"></a>OData

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "odata", 
        "address": { 
            "url": "URL-here" 
        } 
      } 
    } 
  ] 
} 
```

#### <a name="sap-bw"></a>SAP BW

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "sap-bw-olap", 
        "address": { 
          "server": "server-name-here", 
          "systemNumber": "system-number-here", 
          "clientId": "client-id-here" 
        }, 
      } 
    } 
  ] 
} 
```

#### <a name="sap-hana"></a>SAP Hana

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "sap-hana-sql", 
        "address": { 
          "server": "server-name-here:port-here" 
        }, 
      } 
    } 
  ] 
} 
```

#### <a name="sharepoint-list"></a>SharePoint 清單

URL 必須指向 SharePoint 網站本身，而不是網站內的清單。 使用者會取得一個導覽器，讓他們能夠從該網站選取一或多個清單，其中每個都成為模型中的資料表。

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "sharepoint-list", 
        "address": { 
          "url": "URL-here" 
        }, 
       } 
    } 
  ] 
} 
```

#### <a name="sql-server"></a>SQL Server

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "tds", 
        "address": { 
          "server": "server-name-here", 
          "database": "db-name-here (optional) "
        } 
      }, 
      "options": {}, 
      "mode": "DirectQuery" 
    } 
  ] 
} 
```

#### <a name="text-file"></a>文字檔

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "file", 
        "address": { 
            "path": "path-here" 
        } 
      } 
    } 
  ] 
} 
```

#### <a name="web"></a>Web

```json
{ 
  "version": "0.1", 
  "connections": [ 
    { 
      "details": { 
        "protocol": "http", 
        "address": { 
            "url": "URL-here" 
        } 
      } 
    } 
  ] 
} 
```

#### <a name="dataflow"></a>資料流程

```json
{
  "version": "0.1",
  "connections": [
    {
      "details": {
        "protocol": "powerbi-dataflows",
        "address": {
          "workspace":"workspace id (Guid)",
          "dataflow":"optional dataflow id (Guid)",
          "entity":"optional entity name"
        }
       }
    }
  ]
}
```

## <a name="next-steps"></a>後續步驟

您可以使用 Power BI Desktop 執行各種作業。 如需有關其功能的詳細資訊，請參閱下列資源：

* [Power BI Desktop 是什麼？](../fundamentals/desktop-what-is-desktop.md)
* [Power BI Desktop 的查詢概觀](../transform-model/desktop-query-overview.md)
* [Power BI Desktop 中的資料類型](desktop-data-types.md)
* [使用 Power BI Desktop 合併資料並使其成形](desktop-shape-and-combine-data.md)
* [Power BI Desktop 中的常見查詢工作](../transform-model/desktop-common-query-tasks.md)