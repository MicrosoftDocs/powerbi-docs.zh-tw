---
title: 使用 PowerShell 變更資料來源連接字串 - Power BI 報表伺服器 2020 年 10 月前的版本
description: 在 PowerShell 中使用 API 變更資料來源連接字串 - Power BI 報表伺服器 2020 年 10 月前的版本。
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: how-to
ms.date: 10/26/2020
ms.author: maggies
ms.openlocfilehash: 9b4d31b2acc3ce7ec43bbd3fdb91df8e32c2e953
ms.sourcegitcommit: a5fa368abad54feb44a267fe26c383a731c7ec0d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93049394"
---
# <a name="change-data-source-connection-strings-in-power-bi-reports-with-powershell---power-bi-report-server-pre-october-2020"></a>在 Power BI 報表中使用 PowerShell 變更資料來源連接字串 - Power BI 報表伺服器 2020 年 10 月前的版本


您可以透過使用 PowerShell 與必要 API 互動，來變更 Power BI 報表伺服器中裝載之 Power BI 報表的資料來源連接字串。 

> [!IMPORTANT]
> 如果您正在使用 2020 年 10 月最新版 Power BI 報表伺服器，請參閱[在 Power BI 報表中使用 PowerShell 變更資料來源連接字串 - Power BI 報表伺服器](connect-data-source-apis.md)。

> [!NOTE]
> 此功能目前僅適用於 DirectQuery。 即將推出匯入和資料重新整理的支援。

1. 安裝 Power BI 報表伺服器 PowerShell commandlet。 在 [https://github.com/Microsoft/ReportingServicesTools](https://github.com/Microsoft/ReportingServicesTools) 尋找 commandlet 和安裝指示。 

    使用下列命令，直接從 [PowerShell 資源庫](https://www.powershellgallery.com/packages/ReportingServicesTools/) 安裝 `ReportingServicesTools` 模組。

    ```powershell
    Install-Module ReportingServicesTools
    ```

2. 透過 PowerShell commandlet，擷取 Power BI 檔案的現有資料來源資訊：

    ```powershell
    Get-RsRestItemDataSource -RsItem '/MyPbixReport'
    ```

    檢視 Power BI 報表中包含的第一個資料來源相關資訊： 

    ```powershell
    $dataSources[0]
    ```

3. 視需要更新連接和認證資訊。 如果更新連接字串，且資料來源會使用預存認證，您就必須提供帳戶密碼。 

    更新資料來源連接字串：

    ```powershell
    $dataSources[0].ConnectionString = 'data source=myCatalogServer;initial catalog=ReportServer;persist security info=False' 
    ```

    變更資料來源認證類型：

    ```powershell
    $dataSources[0].DataModelDataSource.AuthType = 'Integrated'
    ```

    變更資料來源使用者名稱/密碼：

    ```powershell
    $dataSources[0].DataModelDataSource.Username = 'domain\user'
    ```
    ```powershell
    $dataSources[0].DataModelDataSource.Secret = 'password'
    ```

4. 將更新的認證儲存回伺服器。

    ```powershell
    Set-RsRestItemDataSource -RsItem '/MyPbixReport' -RsItemType 'PowerBIReport' -DataSources $dataSources
    ```

## <a name="next-steps"></a>後續步驟

[Power BI 報表伺服器中的分頁報表資料來源](connect-data-sources.md) 

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
