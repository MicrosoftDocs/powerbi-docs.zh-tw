---
title: 監視 Power BI Embedded
description: 從這裡開始瞭解如何監視 Power BI Embedded。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 01/14/2021
ms.openlocfilehash: 1b8ebbd7913bc5763f9f4dd8576fbc4783e8d531
ms.sourcegitcommit: 77912d4f6ef2a2b1ef8ffccc50691fe5b38ee97a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/22/2021
ms.locfileid: "98690735"
---
# <a name="monitor-power-bi-embedded"></a>監視 Power BI Embedded

當您有依賴 Azure 資源的重要應用程式和商務程序時，您會想要監視這些資源的可用性、效能和操作。 本文說明 Power BI Embedded 所產生的監視資料，以及您可以如何使用 Azure 監視器的功能來分析此資料併發出警示。

## <a name="monitor-overview"></a>監視概觀

每個 *Power BI Embedded* 實例的 Azure 入口網站中的 [**總覽**] 頁面包含下列資訊：

* **資源群組**-實例所屬的 [資源群組](/azure/azure-resource-manager/management/overview#resource-groups)
* **狀態** -Power BI Embedded 實例的狀態
* **位置** -Power BI Embedded 實例的位置
* **資源名稱** -Power BI Embedded 實例的名稱
* **Sku** -Power BI Embedded 實例正在使用的 sku
* **訂** 用帳戶名稱-您的 Power BI Embedded 實例訂用帳戶名稱
* **訂** 用帳戶 id-您的 Power BI Embedded 實例訂用帳戶識別碼

## <a name="what-is-azure-monitor"></a>Azure 監視器是什麼？

*Power BI Embedded* 使用 [Azure 監視器](/azure/azure-monitor/overview)來建立監視資料，這是 Azure 中的完整堆疊監視服務，除了其他雲端和內部部署中的資源之外，還提供一組完整的功能來監視您的 azure 資源。

請從 [使用 Azure 監視器來監視 Azure 資源](/azure/azure-monitor/insights/monitor-azure-resource)的文章開始，其中說明下列概念：

- Azure 監視器是什麼？
- 與監視相關聯的成本
- 在 Azure 中收集的監視資料
- 設定資料收集
- Azure 中用來分析和警示監視資料的標準工具

下列各節將說明針對 Power BI Embedded 所收集的特定資料，並提供使用 Azure 工具來設定資料收集和分析此資料的範例。

## <a name="monitoring-data"></a>監視資料

Power BI Embedded 會收集與 [azure 資源監視資料](/azure/azure-monitor/insights/monitor-azure-resource#monitoring-data-from-Azure-resources)中所述的其他 Azure 資源相同的監視資料類型。

如需 Power BI Embedded 所建立的計量和記錄計量的詳細資訊，請參閱 [監視 *Power BI Embedded* 資料參考](monitor-power-bi-embedded-reference.md) 。

## <a name="collection-and-routing"></a>收集和路由

系統會自動收集和儲存平臺計量和活動記錄檔，但是可以使用診斷設定將其路由至其他位置。  

在您建立診斷設定並將其路由傳送至一或多個位置之前，不會收集並儲存資源記錄。

如需使用 Azure 入口網站、CLI 或 PowerShell 建立診斷設定的詳細程式，請參閱 [建立診斷設定以收集 Azure 中的平臺記錄和計量](/azure/azure-monitor/platform/diagnostic-settings) 。 當您建立診斷設定時，可以指定要收集的記錄類別。 *Power BI Embedded* 的類別列在 [Power BI Embedded 監視資料參考](monitor-power-bi-embedded-reference.md#resource-logs)中。

### <a name="using-powershell-to-enable-diagnostics"></a>使用 PowerShell 來啟用診斷

若要使用 PowerShell 啟用計量和診斷記錄，請使用下列命令。 若要深入瞭解如何使用 PowerShell 來啟用診斷，請參閱 [使用 powershell 在 Azure 監視器中建立和設定 Log Analytics 工作區](/azure/azure-monitor/platform/powershell-workspace-configuration)。

* 若要啟用儲存體帳戶中診斷記錄的儲存體，請使用下列命令：

    ```powershell
    Set-AzureRmDiagnosticSetting -ResourceId [your resource id] -StorageAccountId [your storage account id] -Enabled $true
    ```
    儲存體帳戶識別碼是您想要將記錄檔傳送至該儲存體帳戶的資源識別碼。

* 若要將診斷記錄檔串流至事件中樞，請使用此命令：

    ```powershell
    Set-AzureRmDiagnosticSetting -ResourceId [your resource id] -ServiceBusRuleId [your service bus rule id] -Enabled $true
    ```
* Azure 服務匯流排規則識別碼是此格式的字串︰

    ```powershell
    {service bus resource ID}/authorizationrules/{key name}
    ```

* 若要將診斷記錄檔傳送到 Log Analytics 工作區，請使用此命令：

    ```powershell
        Set-AzureRmDiagnosticSetting -ResourceId [your resource id] -WorkspaceId [resource id of the log analytics workspace] -Enabled $true
    ```

* 您可以使用下列命令取得 Log Analytics 工作區的資源識別碼：

    ```powershell
    (Get-AzureRmOperationalInsightsWorkspace).ResourceId
    ```

您可以結合這些參數來啟用多個輸出選項。

下列各節將討論您可以收集的計量和記錄。

## <a name="analyzing-metrics"></a>分析計量

您可以從 [ **Azure 監視器**] 功能表開啟 [**計量**]，以使用計量瀏覽器來分析來自其他 Azure 服務的計量 *Power BI Embedded* 計量。 如需使用此工具的詳細資訊，請參閱[開始使用 Azure 計量瀏覽器](/azure/azure-monitor/platform/metrics-getting-started)。

如需針對 Power BI Embedded 收集的平臺度量清單，請參閱 [監視 *Power BI Embedded* 資料參考度量](monitor-power-bi-embedded-reference.md#metrics)  

如需參考，您可以查看 [Azure 監視器中支援的所有資源計量](/azure/azure-monitor/platform/metrics-supported)清單。

## <a name="analyzing-logs"></a>分析記錄

Azure 監視器記錄檔中的資料會儲存在資料表中，其中每個資料表都有自己的唯一屬性集。  

Azure 監視器中的所有資源記錄都有相同的欄位，後面接著服務特定的欄位。 一般架構 [Azure 監視器資源記錄架構](https://docs.microsoft.com/azure/azure-monitor/platform/diagnostic-logs-schema#top-level-resource-logs-schema) 中所述，Power BI Embedded 資源記錄的架構可在 [Power BI Embedded 資料參考](monitor-power-bi-embedded-reference.md#schemas)中找到。

[活動記錄](/azure/azure-monitor/platform/activity-log)是可讓您深入瞭解訂用帳戶層級事件的平臺登入 Azure。 您可以單獨加以查看，或將它路由傳送至 Azure 監視器記錄檔，您可以在其中使用 Log Analytics 來進行更複雜的查詢。  

如需針對 Power BI Embedded 收集的資源記錄類型清單，請參閱 [監視 Power BI Embedded 資料參考](monitor-power-bi-embedded-reference.md#resource-logs)  

如需 Log Analytics Azure 監視器記錄和可查詢的資料表清單，請參閱 [監視 Power BI Embedded 資料參考](monitor-power-bi-embedded-reference.md#azure-monitor-logs-tables)  

### <a name="sample-kusto-queries"></a>範例 Kusto 查詢

> [!IMPORTANT]
> 當您從 [Power BI Embedded] 功能表選取 [ **記錄** ] 時，會開啟 Log Analytics，並將查詢範圍設定為目前的 Power BI Embedded 資源。 這表示記錄查詢只會包含來自該資源的資料。 如果您想要執行包含來自其他 Azure 服務之其他 Power BI Embedded 資源或資料之資料的查詢，請從 [ **Azure 監視器**] 功能表中選取 [**記錄**]。 如需詳細資訊，請參閱 [Azure 監視器 Log Analytics 中的記錄查詢範圍和時間範圍](/azure/azure-monitor/log-query/scope/)。

以下是監視 Power BI Embedded 的查詢範例。

* 這是在五分鐘內完成的查詢， (300000 毫秒) 。

    ```Kusto
        search *
        | where Type == "AzureDiagnostics"
        | where ( OperationName == "QueryEnd" )
        | where toint(Duration_s) < 300000   
    ```
* 識別容量名稱。

    ```Kusto
        search *
        | where Type == "AzureDiagnostics"
        | where ( OperationName == "QueryEnd" )
        | where toint(Duration_s) < 300000   
    ```

## <a name="alerts"></a>警示

當您在監視資料中找到重要的條件時，Azure 監視器警示會主動通知您。 它們可讓您識別並解決您的系統中的問題，然後客戶才會注意到這些問題。 您可以設定 [計量](/azure/azure-monitor/platform/alerts-metric-overview)、 [記錄](/azure/azure-monitor/platform/alerts-unified-log)和 [活動記錄](/azure/azure-monitor/platform/activity-log-alerts)的警示。

## <a name="next-steps"></a>後續步驟

您可以深入了解 Azure 資源診斷記錄。

>[!div class="nextstepaction"]
>[監視 Power BI Embedded 資料參考](monitor-power-bi-embedded-reference.md)

>[!div class="nextstepaction"]
>[使用 Azure 監視器監視 Azure 資源](/azure/azure-monitor/insights/monitor-azure-resource)