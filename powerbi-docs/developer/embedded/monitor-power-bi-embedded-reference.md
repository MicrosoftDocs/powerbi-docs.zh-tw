---
title: 監視 Power BI Embedded 資料參考
description: 當您監視 Power BI Embedded 時，需要重要的參考資料。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 01/14/2021
ms.openlocfilehash: fc6b9dd4d50d665211324d1b6c05e62468fc034d
ms.sourcegitcommit: 77912d4f6ef2a2b1ef8ffccc50691fe5b38ee97a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/22/2021
ms.locfileid: "98690739"
---
# <a name="monitoring-power-bi-embedded-data-reference"></a>監視 Power BI Embedded 資料參考

如需收集和分析監視資料的詳細資訊，請參閱 [監視 Power BI Embedded](monitor-power-bi-embedded.md) Power BI Embedded。

## <a name="metrics"></a>計量

此區段會列出針對 Power BI Embedded 收集的所有自動收集平臺計量。  

|度量類型 | 資源提供者/型別命名空間<br/> 和個別計量的連結 |
|-------|-----|
| 容量 | [PowerBIDedicated/容量](/azure/azure-monitor/platform/metrics-supported#microsoftpowerbidedicatedcapacities) |

### <a name="capacities"></a>容量

資源提供者和類型： [Microsoft. PowerBIDedicated/容量](/azure/azure-monitor/platform/metrics-supported#microsoftpowerbidedicatedcapacities)

| Name | Metric | 單位 | 描述 |
|:---|:-------|:-----|:------------|
|記憶體 (Gen1)  |memory_metric               |位元組        |記憶體。 A1、0-5 GB 代表 A1、GB （A2）、0-10 GB （適用于 A3）、0-25 GB （A4）、0-50 GB （A5）和 0-100 GB （A6）的範圍 0-3 GB。 僅支援 Power BI Embedded 代1資源。 |
|記憶體 ()  (Gen1 的資料集，)  |memory_thrashing_metric     |百分比      |記憶體猛移的平均值。 僅支援 Power BI Embedded 代1資源。 |
|QPU 高使用率 (Gen1)  |qpu_high_utilization_metric |Count        |QPU 前一分鐘的高使用率，1表示高 QPU 使用率，否則為0。 僅支援 Power BI Embedded 代1資源。 |
|查詢持續時間 (資料集)  (Gen1)  |QueryDuration               |毫秒 |上次間隔中的 DAX 查詢持續時間。 僅支援 Power BI Embedded 代1資源。 |
|查詢集區工作佇列長度 (資料集)  (Gen1)  |QueryPoolJobQueueLength     |Count        |查詢執行緒集區佇列中的作業數目。 僅支援 Power BI Embedded 代1資源。 |

## <a name="metric-dimensions"></a>度量維度

如需有關哪些計量維度的詳細資訊，請參閱 [多維度計量](/azure/azure-monitor/platform/data-platform-metrics#multi-dimensional-metrics)。

Power BI Embedded 沒有包含維度的任何計量。

## <a name="resource-logs"></a>資源記錄

此區段會列出您可以為 Power BI Embedded 收集的資源記錄類型。

如需參考，請參閱 [Azure 監視器中支援的所有資源記錄類別類型](/azure/azure-monitor/platform/resource-logs-schema)清單。

此區段會列出針對 Power BI Embedded 收集的所有資源記錄類別類型。  

|資源記錄類型 | 資源提供者/型別命名空間<br/> 和個別計量的連結 |
|-------|-----|
| 容量 | [PowerBIDedicated/容量](/azure/azure-monitor/platform/resource-logs-categories#microsoftpowerbidedicatedcapacities) |

## <a name="azure-monitor-logs-tables"></a>Azure 監視器記錄資料表

本節參考所有與 Power BI Embedded 相關的 Azure 監視器記錄 Kusto 資料表，並且可供 Log Analytics 查詢。

|資源類型 | 備註 |
|-------|-----|
| [Power BI Embedded](/azure/azure-monitor/reference/tables/tables-resourcetype#power-bi-embedded) |查看下表的清單 |

### <a name="power-bi-embedded"></a>Power BI Embedded

| 資料表 |  描述 |
|:---------|:-------------|------------------|
| [AzureActivity](/azure/azure-monitor/reference/tables/azureactivity) | Azure 活動記錄中的專案，可讓您深入瞭解在 Azure 中發生的任何訂用帳戶層級或管理群組層級事件。    |                             |                                                   | 
| [AzureDiagnostics](/azure/azure-monitor/reference/tables/azurediagnostics)   | 儲存使用 Azure 診斷模式之 Azure 服務的資源記錄。 資源記錄會描述 Azure 資源的內部作業。 |
| [AzureMetrics](/azure/azure-monitor/reference/tables/azuremetrics)   | Azure 服務發出的度量資料，可測量其健康情況和效能。 |

如需所有 Azure 監視器記錄檔/Log Analytics 資料表的參考，請參閱 [Azure 監視器記錄資料表參考](/azure/azure-monitor/reference/tables/tables-resourcetype)。

## <a name="activity-log"></a>活動記錄檔

您可以選取 [引擎]  和/或 [AllMetrics]  類別。

### <a name="engine"></a>引擎

引擎類別會指示資源記錄下列事件。 每個事件都有屬性。

|     活動名稱     |     事件描述     |
|----------------------------|----------------------------------------------------------------------------------|
|    稽核登入    |    記錄自開始追蹤以來連線到引擎事件的所有新連線。    |
|    工作階段初始化    |    記錄自開始追蹤以來的所有工作階段初始化事件。    |
|    Vertipaq 查詢開始    |    記錄自開始追蹤以來的所有 VertiPaq SE 查詢開始事件。    |
|    查詢開始    |    記錄自開始追蹤以來的所有查詢開始事件。    |
|    查詢結束    |    記錄自開始追蹤以來的所有查詢結束事件。    |
|    Vertipaq 查詢結束    |    記錄自開始追蹤以來的所有 Vertipaq 查詢結束事件。    |
|    稽核登出    |    記錄自開始追蹤以來的所有從引擎中斷連線事件。    |
|    錯誤    |    記錄自開始追蹤以來的所有引擎錯誤事件。    |

#### <a name="event-example"></a>事件範例

下表顯示事件範例。

| 屬性名稱 | Vertipaq 查詢結束範例 | 屬性描述 |
|---|---|---|
| EventClass | XM_SEQUERY_END | 「事件類別」是用來將事件分類。 |
| EventSubclass | 0 | 「事件子類別」提供有關每個事件類別的額外資訊。 (例如，0: VertiPaq 掃描) |
| RootActivityId | ff217fd2-611d-43c0-9c12-19e202a94f70 | 根活動識別碼。 |
| CurrentTime | 2018-04-06T18:30:11.9137358Z | 事件開始的時間 (當可用時)。 |
| StartTime | 2018-04-06T18:30:11.9137358Z | 事件開始的時間 (當可用時)。 |
| JobID | 0 | 進度的工作識別碼。 |
| ObjectID | 464 | 物件識別碼 |
| ObjectType | 802012 | ObjectType |
| EndTime | 2018-04-06T18:30:11.9137358Z | 事件結束的時間。 |
| 持續時間 | 0 | 事件花費的時間量 (毫秒)。 |
| SessionType | 使用者 | 工作階段類型 (引發作業的實體)。 |
| ProgressTotal | 0 | 整體進度。 |
| IntegerData | 0 | 整數資料。 |
| 嚴重性 | 0 | 例外狀況的嚴重性層級。 |
| Success | 1 | 1 = 成功。 0 = 失敗 (例如，1 表示權限檢查成功，而 0 表示該檢查失敗)。 |
| 錯誤 | 0 | 給定事件的錯誤號碼。 |
| ConnectionID | 3 | 唯一的連線識別碼。 |
| DatasetID | 5eaa550e-06ac-4adf-aba9-dbf0e8fd1527 | 資料集 (使用者的陳述式在其中執行) 的識別碼。 |
| SessionID | 3D063F66-A111-48EE-B960-141DEBDA8951 | 工作階段 GUID。 |
| SPID | 180 | 伺服器處理序識別碼。 這可唯一識別使用者工作階段。 這直接對應到 XML/A 所使用的工作階段 GUID。 |
| ClientProcessID | null | 用戶端應用程式的處理序識別碼。 |
| ApplicationName | null | 建立對伺服器連線之用戶端應用程式的名稱。 |
| CapacityName | pbi641fb41260f84aa2b778a85891ae2d97 | Power BI Embedded 容量資源的名稱。 |

### <a name="allmetrics"></a>AllMetrics

選取 [AllMetrics]  選項會記錄您可以搭配 Power BI Embedded 資源來使用之所有計量的資料。

下表列出可能會在活動記錄中建立之 Power BI Embedded 的相關作業。

## <a name="schemas"></a>結構描述

Power BI Embedded 使用 **Power BI 的專用** 架構。

## <a name="next-steps"></a>後續步驟

>[!div class="nextstepaction"]
>[監視 Azure Power BI Embedded](monitor-power-bi-embedded.md)

>[!div class="nextstepaction"]
>[Azure 資源診斷記錄](/azure/monitoring-and-diagnostics/monitoring-overview-of-diagnostic-logs)

>[!div class="nextstepaction"]
>[Set-AzureRmDiagnosticSetting](/powershell/module/azurerm.insights/Set-AzureRmDiagnosticSetting) \(英文\)