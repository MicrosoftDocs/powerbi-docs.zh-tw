---
title: 使用 PowerShell 變更資料來源連接字串
description: 在 PowerShell 中使用 API 變更資料來源連接字串 - Power BI 報表伺服器。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 10/26/2020
ms.openlocfilehash: 4e1947abe0fa0f17e1db92619f0aa7fba5df5575
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415465"
---
# <a name="change-data-source-connection-strings-in-power-bi-reports-with-powershell---power-bi-report-server"></a>在 PowerShell 報表中使用 PowerShell 變更資料來源連接字串 - Power BI 報表伺服器


自 2020 年 10 月版的 Power BI 報表伺服器開始，我們會啟用 Power BI 報表的更新連線功能，以處理 DirectQuery 和重新整理。

> [!IMPORTANT]
> 這也是舊版設定方式的重大變更。 如果您正在使用 2020 年 10 月版以前的 Power BI 報表伺服器，請參閱[在 Power BI 報表中使用 PowerShell 變更資料來源連接字串 - 2020 年 10 月版以前的 Power BI 報表伺服器](connect-data-source-apis-pre-oct-2020.md)

## <a name="prerequisites"></a>先決條件：
- 下載 2020 年 10 月版的 [Power BI 報表伺服器和針對 Power BI 報表伺服器最佳化的 Power BI Desktop](https://powerbi.microsoft.com/report-server/)。
- 使用 2020 年 10 月版針對報表伺服器最佳化的 Power BI Desktop，儲存已啟用 [增強型資料集中繼資料] 的報表。
- 使用參數化連線的報表。 只有具有參數化連線和資料庫的報表才能在發佈後更新。
- 此範例使用 Reporting Services PowerShell 工具。 使用新的 REST API 可達到相同效果。

## <a name="create-a-report-with-parameterized-connections"></a>使用參數化連線建立報表
    
1. 建立伺服器的 SQL Server 連線。 在以下範例中，我們要連線到 localhost 的 ReportServer 資料庫，並從 ExecutionLog 提取資料。

    :::image type="content" source="media/connect-data-source-apis/sql-server-connect-database.png" alt-text="連線到 SQL Server 資料庫":::

    此時的 M 查詢如下：

    ```
    let
        Source = Sql.Database("localhost", "ReportServer"),
        dbo_ExecutionLog3 = Source{[Schema="dbo",Item="ExecutionLog3"]}[Data]
    in
        dbo_ExecutionLog3
    ```

2. 選取 Power Query 編輯器功能區中的 [管理參數]。

    :::image type="content" source="media/connect-data-source-apis/power-query-manage-parameters.png" alt-text="選取 [管理參數]":::

1.  建立 servername 和 databasename 的參數。

    :::image type="content" source="media/connect-data-source-apis/report-server-manage-parameters.png" alt-text="設定 servername 和 databasename 的 [管理參數]。":::


3. 編輯第一個連線的查詢，然後對應資料庫和 servername。

    :::image type="content" source="media/connect-data-source-apis/report-server-map-database-server.png" alt-text="對應伺服器和資料庫名稱":::

    現在查詢看起來如下：

    ```
    let
        Source = Sql.Database(ServerName, Databasename),
        dbo_ExecutionLog3 = Source{[Schema="dbo",Item="ExecutionLog3"]}[Data]
    in
        dbo_ExecutionLog3
    ```
    
    4. 將該報表發佈至伺服器。 在此範例中，報告名為 executionlogparameter。 下圖是資料來源管理頁面的範例。

    :::image type="content" source="media/connect-data-source-apis/report-server-manage-data-source-credentials.png" alt-text="資料來源管理頁面。":::

## <a name="update-parameters-using-the-powershell-tools"></a>使用 PowerShell 工具更新參數

1. 請遵循 [https://github.com/microsoft/ReportingServicesTools](https://github.com/microsoft/ReportingServicesTools) 的指示開啟 PowerShell 並安裝 Reporting Services 最新工具。
    
2.  若要取得報表的參數，請使用下列 PowerShell 呼叫以利用新的 REST DataModelParameters API：

    ```powershell
    Get-RsRestItemDataModelParameters '/executionlogparameter'

        Name         Value
        ----         -----
        ServerName   localhost
        Databasename ReportServer
    ```

3. 我們會將此呼叫的結果儲存在變數中：

    ```powershell
    $parameters = Get-RsRestItemDataModelParameters '/executionlogparameter'
    ```

4. 這個變數會使用我們必須變更的值予以更新。
5. 我們會將此呼叫的結果儲存在變數中：

    ```powershell
    $parameters[0].Value = 'myproductionserver'
    $parameters[1].Value = 'myproductiondatabase'
    ```

6. 使用更新後的值，我們即可使用 Commandlet `Set-RsRestItemDataModelParameters` 來更新伺服器中的值：

    ```powershell
    Set-RsRestItemDataModelParameters -RsItem '/executionlogparameter' -DataModelParameters $parameters
    ```

7. 更新參數之後，伺服器就會更新所有曾繫結至參數的資料來源。 回到 [編輯資料來源] 對話方塊，您應該能夠為更新後的伺服器和資料庫設定認證。

    :::image type="content" source="media/connect-data-source-apis/report-server-manage-executionlogparameter-dialog.png" alt-text="為更新後的伺服器和資料庫設定認證。":::

## <a name="next-steps"></a>後續步驟

[Power BI 報表伺服器中的分頁報表資料來源](connect-data-sources.md) 

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
