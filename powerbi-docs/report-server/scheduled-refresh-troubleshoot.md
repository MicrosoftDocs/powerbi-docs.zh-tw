---
title: 針對 Power BI 報表伺服器中排程的重新整理進行疑難排解
description: 本文會討論可用來針對 Power BI 報表伺服器中排程的重新整理之問題進行疑難排解的資源。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: troubleshooting
ms.date: 11/01/2017
ms.openlocfilehash: 8cb8bf4e6d67f01f7bbdc4370d8a60691dba5a63
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418271"
---
# <a name="troubleshoot-scheduled-refresh-in-power-bi-report-server"></a>針對 Power BI 報表伺服器中排程的重新整理進行疑難排解
本文會討論可用來針對 Power BI 報表伺服器中排程的重新整理之問題進行疑難排解的資源。

出現問題時，這篇文章會更新資訊以協助您。

## <a name="common-issues"></a>常見問題
以下是您在嘗試為報表排程重新整理時會遇到的較常見問題。 

### <a name="driver-related-problems"></a>驅動程式相關問題
連線到不同資料來源可能需要安裝協力廠商驅動程式，才能成功連線。 您不僅必須在使用 Power BI Desktop 所在的電腦上安裝它們，也必須確定驅動程式已安裝在報表伺服器上。

驅動程式可能同時有 32 位元和 64 位元。 請務必安裝 64 位元驅動程式，因為 Power BI 報表伺服器是 64 位元。

請洽詢製造商，以取得如何安裝和設定協力廠商驅動程式的詳細資料。

### <a name="memory-pressure"></a>記憶體壓力
當報表需要更多記憶體來處理及轉譯時，會發生記憶體壓力。 在報表上排程重新整理可能會要求電腦的大量記憶體。 特別是針對較大的報表。 記憶體壓力會導致報表失敗，報表伺服器本身也可能會當機。

如果您持續遇到記憶體壓力，試著查看報表伺服器相應放大部署，以便分散資源的負載。 您也可以定義指定報表伺服器用於使用 rsreportserver.config 內的 `IsDataModelRefreshService` 設定，進行資料重新整理。使用此設定，您可以定義一或多伺服器成為要在需求報表上處理的前端伺服器，讓另一組伺服器只用於排程的重新整理。

如需如何監視 Analysis Services 執行個體的詳細資訊，請參閱[監視 Analysis Services 執行個體](/sql/analysis-services/instances/monitor-an-analysis-services-instance)。

如需 Analysis Services 內記憶體設定的詳細資訊，請參閱[記憶體屬性](/sql/analysis-services/server-properties/memory-properties)。

### <a name="kerberos-configuration"></a>Kerberos 設定
連線到具有 Windows 認證的資料來源，可能需要設定 Kerberos 限制委派，才能成功連線。 如需如何設定 Kerberos 限制委派的詳細資訊，請參閱[設定 Kerberos 使用 Power BI 報表](configure-kerberos-powerbi-reports.md)。

## <a name="known-issues"></a>已知問題
已知問題的相關資訊在可用時會列在這裡。

## <a name="configuration-settings"></a>組態設定
下列設定可以用來影響排程的重新整理。 SQL Server Management Studio (SSMS) 中的設定集會套用到相應放大部署內的所有報表伺服器。 在 rsreportserver.config 中設定的設定適用於特定的伺服器。

**SSMS 中的設定：**

| 設定 | 描述 |
| --- | --- |
| MaxFileSizeMb |上傳報表的最大檔案大小。 預設值為 1000 MB (1 GB)。 最大值為 2000 MB (2 GB)。 |
| ModelCleanupCycleMinutes |定義檢查模型以從記憶體中收回的頻率。 預設值為 15 分鐘。 |
| ModelExpirationMinutes |定義根據最後使用和收回的時間，模型到期之前有多少時間。 預設值為 60 分鐘。 |
| ScheduleRefreshTimeoutMinutes |定義模式的資料重新整理需要多少時間。 預設值為 120 分鐘。 沒有上限。 |

**rsreportserver.config 中的設定：**

```xml
<Configuration>
    <Service>
        <PollingInterval>10</PollingInterval>
        <IsDataModelRefreshService>false</IsDataModelRefreshService>
        <MaxQueueThreads>0</MaxQueueThreads>
    </Service>
</Configuration>
```

## <a name="tools-for-troubleshooting"></a>疑難排解的工具
### <a name="logs-relevant-for-scheduled-refresh-of-power-bi-reports"></a>Power BI 報表排程的重新整理之相關記錄
保存排程的重新整理相關資訊的記錄檔是 RSPowerBI_ logs。 它們位於報表伺服器安裝位置的 LogFiles 資料夾中。 

```
C:\Program Files\Microsoft Power BI Report Server\PBIRS\LogFiles\RSPowerBI_*.log
```

**錯誤狀況**

```
2017-10-20 02:00:09.5188|ERROR|744|Error Processing Data Model Refresh: SessionId: e960c25e-ddd4-4763-aa78-0e5dceb53472, Status: Error Model can not be refreshed because not all the data sources are embedded, Exception Microsoft.PowerBI.ReportServer.AsServer.InvalidDataSourceException: Model can not be refreshed because not all the data sources are embedde
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.AnalysisServicesDataRefresh.CanModelRefresh(IEnumerable`1 dataSources)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<>c__DisplayClass7.<ExecuteActionWithLogging>b__5()
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<ExecuteFuncWithLogging>d__1`1.MoveNext()
```

**成功重新整理* _

```
2017-10-25 15:23:41.9370|INFO|6|Handling event with data: TimeEntered: 10/25/2017 8:23:41 PM, Type: Event, SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, EventType: DataModelRefresh
2017-10-25 15:23:41.9370|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Data Refresh.
2017-10-25 15:23:41.9370|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Retrieving PBIX AsDatabaseInfo.
2017-10-25 15:23:42.7134|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Verifying all the data sources are embedded.
2017-10-25 15:23:42.7134|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Verifying connection strings are valid.
2017-10-25 15:23:42.7134|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Streaming model to Analysis Server.
2017-10-25 15:23:42.7603|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Refreshing the model.
2017-10-25 15:23:51.5258|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Removing credentials from the model.
2017-10-25 15:23:51.6508|INFO|6|Processing Data Model Refresh: SessionId: 46d398db-0b1f-49d8-b7bd-c5461c07ec7a, Status: Starting Saving model to the catalog.
```

_ *認證不正確**

```
2017-10-20 08:22:01.5595|INFO|302|Processing Data Model Refresh: SessionId: 22cd9ec3-b21a-4eb1-81ae-15fac8d379ea, Status: Starting Refreshing the model.
2017-10-20 08:22:02.3758|ERROR|302|Error Processing Data Model Refresh: SessionId: 22cd9ec3-b21a-4eb1-81ae-15fac8d379ea, Status: Error Failed to refresh the model, Exception Microsoft.AnalysisServices.OperationException: Failed to save modifications to the server. Error returned: 'The credentials provided for the SQL source are invalid. (Source at rosecatalog;reportserver.). The exception was raised by the IDbCommand interface.
'.
   at Microsoft.AnalysisServices.Tabular.Model.SaveChanges(SaveOptions saveOptions)
   at Microsoft.PowerBI.ReportServer.AsServer.TOMWrapper.RefreshModel(Database database)
   at Microsoft.PowerBI.ReportServer.AsServer.AnalysisServicesServer.RefreshDatabase(String databaseName, IEnumerable`1 dataSources)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.AnalysisServicesDataRefresh.RefreshDatabase(AsDatabaseInfo asDatabaseInfo)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<>c__DisplayClass7.<ExecuteActionWithLogging>b__5()
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<ExecuteFuncWithLogging>d__1`1.MoveNext()
2017-10-20 08:22:02.4588|ERROR|302|Error Processing Data Model Refresh: SessionId: 22cd9ec3-b21a-4eb1-81ae-15fac8d379ea, Status: Error Failed Data Refresh, Exception Microsoft.AnalysisServices.OperationException: Failed to save modifications to the server. Error returned: 'The credentials provided for the SQL source are invalid. (Source at rosecatalog;reportserver.). The exception was raised by the IDbCommand interface.
'.
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.ExecuteActionWithLogging(Action methodToExecute, String description, String localizedDescription, String messageInFailure, RefreshInfo refreshInfo, DataAccessors dataAccessors, ReportEventType operation, Int64 size, Boolean isDataRetrieval, Boolean showInExecutionLog)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.AnalysisServicesDataRefresh.RefreshData(RefreshInfo refreshInfo)
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<>c__DisplayClass7.<ExecuteActionWithLogging>b__5()
   at Microsoft.PowerBI.ReportServer.WebHost.EventHandler.DataRefreshScope.<ExecuteFuncWithLogging>d__1`1.MoveNext()
```

#### <a name="enabling-verbose-logging"></a>啟用詳細資訊記錄
在 Power BI 報表伺服器中啟用詳細資訊記錄，與 SQL Server Reporting Services 相同。

1. 開啟 `<install directory>\PBIRS\ReportServer\bin\ReportingServicesService.exe.config`。
2. 在 `<system.diagnostics>` 底下，將 **DefaultTraceSwitch** 變更為 **4**。
3. 在 `<RStrace>` 底下，將 **Components** 變更為 **all:4**。 

### <a name="executionlog"></a>ExecutionLog
每當轉譯 Power BI 報表時，或執行排程重新整理計劃時，新項目會新增至資料庫中的執行記錄。 這些項目位於報表伺服器目錄資料庫內的 **ExecutionLog3** 檢視。

Power BI 報表的執行記錄項目與其他報表類型的項目不同。

* TimeRendering 資料行一律是 0。 Power BI 報表的轉譯會在瀏覽器中發生，而不是伺服器。
* 有 2 個要求類型和後續項目動作：
  * **Interactive**：每當檢視報表時。
    * **ASModelStream**：當資料模型從目錄串流至 Analysis Services 時。
    * **ConceptualSchema**：當使用者在檢視報表時按一下時。
    * **QueryData**：每當從用戶端要求資料時。
  * **Refresh Cache**：每當執行排程重新整理計劃時。
    * **ASModelStream**：每當資料模型從目錄串流至 Analysis Services 時。
    * **DataRefresh**：每當從一或多個資料來源重新整理資料時。
    * **SaveToCatalog**：每當資料模型儲存回目錄時。

## <a name="analysis-services"></a>Analysis Services
有時候您可能想要針對診斷問題修改 Analysis Services，或是調整記憶體限制。

> [!IMPORTANT]
> 這些設定會在您升級報表伺服器時隨時重設。 請務必保留一份變更的複本，並且視需要重新套用。
> 
> 

### <a name="install-location"></a>安裝位置
Power BI 報表伺服器的預設位置，Analysis Services 則是後續位置。

`C:\Program Files\Microsoft Power BI Report Server\PBIRS\ASEngine`

### <a name="configuring-analysis-services-settings-msmdsrvini"></a>設定 Analysis Services 設定 (msmdsrv.ini)
在 `<install directory>\PBIRS\ASEngine` 目錄中，您會發現 msmdsrv.ini  檔案，可以用來控制 Analysis Services 的不同設定。 當您開啟這個檔案時，您會立即了解此檔案沒有您對於 msmdsrv.ini 檔案預期的所有設定。 

這是因為 Power BI 報表伺服器所執行的實際 Analysis Services 處理程序是在 `<install directory>\PBIRS\ASEngine\workspaces` 中啟動。 在該資料夾中，您會看到您習慣的完整 msmdsrv.ini  檔案。 請勿修改工作區資料夾中的檔案，因為每當 Analysis Services 處理程序啟動時，它都會重寫。 如果您想要控制設定，請藉由修改 `<install directory>\PBIRS\ASEngine` 目錄中的 msmdsrv.ini 來完成這個操作。

每當 Analysis Services 處理程序啟動時，就會重設下列設定。 您對這些項目進行的任何變更將會被忽略。

* ConfigurationSettings\PrivateProcess
* ConfigurationSettings\DataDir
* ConfigurationSettings\LogDir
* ConfigurationSettings\TempDir
* ConfigurationSettings\BackupDir
* ConfigurationSettings\AllowedBrowsingFolders
* ConfigurationSettings\CrashReportsFolder
* ConfigurationSettings\ExtensionDir
* ConfigurationSettings\Port
* ConfigurationSettings\DeploymentMode
* ConfigurationSettings\ServerLocation
* ConfigurationSettings\TMCompatabilitySKU
* ConfigurationSettings\FlightRecorder\TraceDefinitionFile

### <a name="profiling-the-local-analysis-services-process"></a>分析本機 Analysis Services 處理程序
SQL Profiler 追蹤可以在本機 Analysis Services 處理程序上針對診斷目的執行。 若要連線至本機 Analysis Services 執行個體，請執行下列作業。

SQL Server Profiler 追蹤隨附於 [SQL Server Management Studio (SSMS) 下載](/sql/ssms/download-sql-server-management-studio-ssms)。

1. 以系統管理員身分啟動 **SQL Server Profiler**。
2. 選取 [新增追蹤]  按鈕。
3. 在 [連接至伺服器]  對話方塊中，選取 [Analysis Services]  ，然後輸入 **localhost:5132** 作為伺服器名稱。
4. 在 [追蹤屬性]  對話方塊中，選取您想要擷取的事件，然後選取 [執行]  。

## <a name="lock-pages-in-memory-windows-privilege"></a>鎖定記憶體中的分頁 Windows 權限
如果您發現您無法轉譯 Power BI 報表，將 **鎖定記憶體中的分頁** 權限指派給執行 Power BI 報表伺服器的服務帳戶，可能有幫助。 如需有關如何設定 **鎖定記憶體中的分頁** 的詳細資訊，請參閱 [指派給 Analysis Services 服務帳戶的 Windows 權限](/sql/analysis-services/instances/configure-service-accounts-analysis-services#bkmk_winpriv)。

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)