---
title: 系統管理員適用的 PowerShell Cmdlet、REST API 和 .NET 用戶端程式庫
description: 了解透過指令碼和程式設計 API 管理 Power BI 的方式。
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/09/2019
LocalizationGroup: Administration
ms.openlocfilehash: 6afc49e0d2fe67c89d906d4715959892868b0027
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96408082"
---
# <a name="powershell-cmdlets-rest-apis-and-net-client-library-for-power-bi-administration"></a>Power BI 系統管理員適用的 PowerShell Cmdlet、REST API 和 .NET 用戶端程式庫
Power BI 可讓系統管理員使用 PowerShell Cmdlet 撰寫一般工作的指令碼。 其同時公開 REST API 並提供 .NET 用戶端程式庫來開發管理解決方案。 本主題說明 Cmdlet 清單以及對應的 API 和 REST API 端點。 如需詳細資訊，請參閱：

- PowerShell [下載](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt/)和[文件](/powershell/power-bi/overview?view=powerbi-ps)
- REST API [文件](/rest/api/power-bi/admin)
- .NET 用戶端程式庫[下載](https://www.nuget.org/packages/Microsoft.PowerBI.Api/)

> 下列 Cmdlet 須搭配 `-Scope Organization` 呼叫，才能用來對租用戶進行管理。

| **Cmdlet 名稱** | **別名** | **API** | **REST API 端點** | **描述** |
| --- | --- | --- | --- | --- |
| `Get-PowerBIDatasource` | N/A | `Datasets_GetDataSourcesAsAdmin` | /v1.0/myorg/admin/datasets/{datasetkey}/datasources | 取得指定資料集的資料來源。 |
| `Get-PowerBIDataset` | N/A | `Datasets_GetDatasetsAsAdmin` | /v1.0/myorg/admin/datasets | 取得 Power BI 租用戶中的完整資料集清單。 |
| `Get-PowerBIWorkspace` | `Get-PowerBIGroup` | `Groups_GetGroupsAsAdmin` | /v1.0/myorg/admin/groups | 取得 Power BI 租用戶中的完整工作區清單。 |
| `Add-PowerBIWorkspaceUser` | `Add-PowerBIGroupUser` | `Groups_AddUserAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/users | 將使用者新增為指定工作區的成員。 |
| `Remove-PowerBIWorkspaceUser` | `Remove-PowerBIGroupUser` | `Groups_DeleteUserAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/users/{user} | 從指定工作區的成員資格清單中移除使用者。 |
| `Restore-PowerBIWorkspace` |`Restore-PowerBIGroup` | `Groups_RestoreDeletedGroupAsAdmin` | /v1.0/myorg/admin/groups/{groupId}/restore | 還原已刪除的工作區。 |
| `Set-PowerBIWorkspace` |`Set-PowerBIGroup` | `Groups_UpdateGroupAsAdmin` | /v1.0/myorg/admin/groups/{groupId} | 更新指定工作區的屬性。 |
| `Get-PowerBIDataset -WorkspaceId` | N/A | `Groups_GetDatasetsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/datasets | 取得指定工作區內的資料集。 |
| `Get-PowerBIReport` | N/A | `Reports_GetReportsAsAdmin` | /v1.0/myorg/admin/reports | 取得 Power BI 租用戶中的完整報表清單。 |
| `Get-PowerBIDashboard` | N/A | `Dashboards_GetDashboardsAsAdmin` | /v1.0/myorg/admin/dashboards | 取得 Power BI 租用戶中的完整儀表板清單。 |
| `Get-PowerBIDashboard -WorkspaceId` | N/A | `Groups_GetDashboardsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/dashboards | 取得指定工作區內的儀表板。 |
| `Get-PowerBITile` | `Get-PowerBIDashboardTile` | `Dashboards_GetTilesAsAdmin` | /v1.0/myorg/admin/dashboards/{dashboard\_id}/tiles | 取得指定儀表板的圖格。 |
| `Get-PowerBIReport` | N/A | `Groups_GetReportsAsAdmin` | /v1.0/myorg/admin/groups/{group\_id}/reports | 取得指定工作區內的報表。 |
| `Get-PowerBIImport` | N/A | `Imports_GetImportsAsAdmin` | /v1.0/myorg/admin/imports | 取得 Power BI 租用戶中的完整匯入清單。 |
| `Connect-PowerBIServiceAccount` | `Login-PowerBI` &  `Login-PowerBIServiceAccount` | N/A | N/A | 登入 Power BI 並啟動工作階段。 |
| `Disconnect-PowerBIServiceAccount` | `Logout-PowerBI` & `Logout-PowerBIServiceAccount` | N/A | N/A | 登出 Power BI 並關閉現有工作階段。 |
| `Invoke-PowerBIRestMethod`| N/A | N/A | N/A | 將任意 REST API 呼叫傳送給 Power BI。 |
| `Get-PowerBIAccessToken`| N/A | N/A | N/A | 取得工作階段中的 Power BI 存取權杖。 |
| `Resolve-PowerBIError`| N/A | N/A | N/A | 取得 Cmdlet 呼叫失敗的詳細錯誤資訊。 |