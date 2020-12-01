---
title: 追蹤 Power BI 中的使用者活動
description: 了解您可以如何使用 Power BI 的活動記錄和稽核來監視和調查所 採取的動作。
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 08/20/2020
ms.author: kfollis
ms.custom: licensing support
LocalizationGroup: Administration
ms.openlocfilehash: 178b79ba4ae76288794f7bb67afba11c0595de7f
ms.sourcegitcommit: 9d033abd9c01a01bba132972497dda428d7d5c12
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95513841"
---
# <a name="track-user-activities-in-power-bi"></a>追蹤 Power BI 中的使用者活動

了解誰正在對 Power BI 租用戶的哪個項目採取什麼動作，可能對於幫助貴組織符合其需求 (如符合法規合規性與記錄管理) 而言極為重要。 透過 Power BI，您有兩個選項可用來追蹤使用者活動：[Power BI 活動記錄檔](#use-the-activity-log)與[整合稽核記錄檔](#use-the-audit-log)。 這些記錄檔都包含 [Power BI 審核資料](#operations-available-in-the-audit-and-activity-logs)的完整複本，但有幾個主要差異，如下表摘要所示。

| **整合稽核記錄檔** | **Power BI 活動記錄** |
| --- | --- |
| 除了 Power BI 審核事件以外，還包含來自 SharePoint Online、Exchange Online、Dynamics 365 和其他服務的事件。 | 只包含 Power BI 審核事件。 |
| 只有具備僅限檢視稽核記錄權限或稽核記錄權限的使用者才能存取，例如全域管理員和稽核員。 | 全域管理員和 Power BI 服務管理員可以存取。 |
| 全域管理員和稽核員可使用 Microsoft 365 資訊安全中心以及 Microsoft 365 合規性中心來搜尋整合稽核記錄檔。 | 目前沒有任何使用者介面可搜尋活動記錄。 |
| 全域管理員和稽核員可以使用 Microsoft 365 管理 API 和 Cmdlet 來下載稽核記錄項目。 | 全域管理員和 Power BI 服務管理員可以使用 Power BI REST API 和管理 Cmdlet 來下載活動記錄項目。 |
| 將審核資料保留 90 天 | 將活動資料保留 30 天 (公開預覽)。 |
| 即使將租用戶移至不同的 Azure 區域，仍會保留稽核資料。 | 將租用戶移至不同的 Azure 區域時，不會保留活動資料。 |


## <a name="use-the-activity-log"></a>使用活動記錄

> [!NOTE]
> Microsoft Cloud Deutschland 不支援活動記錄。 若要深入了解德國雲端的服務限制，請參閱[德國雲端客戶的 Power BI 常見問題](service-govde-faq.md)。


身為 Power BI 服務系統管理員，您可以使用以 Power BI 活動記錄為基礎的自訂報告來分析租用戶層級上所有 Power BI 資源使用情況。 您可以使用 REST API 或 PowerShell Cmdlet 來下載活動。 還可以依照日期範圍、使用者和活動類型來篩選活動資料。

### <a name="activity-log-requirements"></a>活動記錄需求

您必須符合這些需求才能存取 Power BI 活動記錄：

- 您必須是全域管理員或 Power BI 服務管理員。
- 您已在本機安裝 [Power BI 管理 Cmdlet](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt)，或使用 Azure Cloud Shell 中的 Power BI 管理 Cmdlet。

### <a name="activityevents-rest-api"></a>ActivityEvents REST API

您可以使用以 Power BI REST API 為基礎的系統管理應用程式，將活動事件匯出至 Blob 存放區或 SQL 資料庫。 接著，可以在所匯出資料之上建置自訂的使用情況報表。 在 **ActivityEvents** REST API 呼叫中，您必須指定開始日期和結束日期，並選擇性地依照活動類型或使用者識別碼選取活動。 因為活動記錄可能包含大量資料，所以 **ActivityEvents** API 目前只支援每個要求最多下載一天的資料。 換句話說，開始日期和結束日期必須指定同一天，如下列範例所示。 請確定您以 UTC 格式指定 DateTime 值。

```
https://api.powerbi.com/v1.0/myorg/admin/activityevents?startDateTime='2019-08-31T00:00:00'&endDateTime='2019-08-31T23:59:59'
```

如果項目數很大，則 **ActivityEvents** API 只會傳回大約 5,000 到 10,000 個項目和一個接續權杖。 使用接續權杖再次呼叫 **ActivityEvents** API，以取得下一批項目，依此類推，直到已擷取所有項目且不再收到接續權杖為止。 下列範例示範如何使用此接續權杖。

```
https://api.powerbi.com/v1.0/myorg/admin/activityevents?continuationToken='%2BRID%3ARthsAIwfWGcVAAAAAAAAAA%3D%3D%23RT%3A4%23TRC%3A20%23FPC%3AARUAAAAAAAAAFwAAAAAAAAA%3D'
```

不論傳回的項目數為何，如果結果包含接續權杖，請務必使用該權杖再次呼叫 API 來擷取剩餘的資料，直到不再傳回接續權杖為止。 呼叫甚至會在沒有任何事件項目的情況下傳回接續權杖。 下列範例示範如何使用回應中傳回的接續權杖來進行迴圈：

```
while(response.ContinuationToken != null)
{
   // Store the activity event results in a list for example
    completeListOfActivityEvents.AddRange(response.ActivityEventEntities);

    // Make another call to the API with continuation token
    response = GetPowerBIActivityEvents(response.ContinuationToken)
}
completeListOfActivityEvents.AddRange(response.ActivityEventEntities);
```
> [!NOTE]
> 所有事件最多可能需要 24 小時才會顯示，雖然完整的資料通常會更快提供使用。
>
>
若要深入了解如何使用 Power BI REST API (包含如何取得稽核活動事件的範例)，請參閱 Power BI REST API 參考中的[系統管理 - 取得活動事件](/rest/api/power-bi/admin/getactivityevents) (英文)。

### <a name="get-powerbiactivityevent-cmdlet"></a>Get-PowerBIActivityEvent Cmdlet

使用 PowerShell 的 Power BI 管理 Cmdlet 來下載活動事件。 **Get-PowerBIActivityEvent** Cmdlet 會自動處理接續權杖。 **Get-PowerBIActivityEvent** Cmdlet 會採用 StartDateTime 和 EndDateTime 參數，其限制與 **ActivityEvents** REST API 相同。 換句話說，開始日期和結束日期必須參考相同的日期值，因為您一次只能擷取一天的活動資料。

下列指令碼示範如何下載所有 Power BI 活動。 此命令會將 JSON 的結果轉換成 .NET 物件，以便直接存取個別的活動屬性。 這些範例會顯示一天中最可能的最小和最大時間戳記，確保不會遺漏任何事件。

```powershell
Login-PowerBI

$activities = Get-PowerBIActivityEvent -StartDateTime '2019-08-31T00:00:00' -EndDateTime '2019-08-31T23:59:59' | ConvertFrom-Json

$activities.Count
$activities[0]

```

### <a name="filter-activity-data"></a>篩選活動資料

您可以依照活動類型和使用者識別碼來篩選活動事件。 下列指令碼示範如何只下載 **ViewDashboard** 活動的事件資料。 如需所支援參數的詳細資訊，請使用 `Get-Help Get-PowerBIActivityEvent` 命令。

```powershell
Login-PowerBI

$activities = Get-PowerBIActivityEvent -StartDateTime '2019-08-31T00:00:00' -EndDateTime '2019-08-31T23:59:59' -ActivityType 'ViewDashboard' | ConvertFrom-Json

$activities.Count
$activities[0]

```

> [!NOTE]
> PowerShell 範例可有助了解如何篩選及擷取 Power BI 活動記錄事件。 如需詳細資訊，請參閱[存取 Power BI 活動記錄](../guidance/admin-activity-log.md)。

## <a name="use-the-audit-log"></a>使用稽核記錄

如果工作是要追蹤 Power BI 和 Microsoft 365 之間的使用者活動，則可在 Office 365 安全性與合規性中心內進行審核，或使用 PowerShell 來執行。 稽核需仰賴 Exchange Online 的功能，其會自動佈建以支援 Power BI。

您可以依日期範圍、使用者、儀表板、報表、資料集和活動類型來篩選稽核資料。 您也可以用 csv (逗號分隔值) 檔案來下載活動以便離線分析。

### <a name="audit-log-requirements"></a>稽核記錄需求

您必須符合這些需求才能存取稽核記錄：

- 您必須是全域管理員或已被指派 Exchange Online 中的「稽核記錄」或「僅供檢視稽核記錄」角色，才能存取稽核記錄。 根據預設，「法規遵循管理」和「組織管理」角色群組會隨附在 Exchange 系統管理中心的 [權限] 頁面上指派的這些角色。 如需可檢視稽核記錄的角色詳細資訊，請參閱[搜尋稽核記錄的要求](/microsoft-365/compliance/search-the-audit-log-in-security-and-compliance?view=o365-worldwide#requirements-to-search-the-audit-log)。

    若要提供稽核記錄存取權給非系統管理員帳戶，請將使用者新增為這些角色群組中其中一個角色群組的成員。 如果您想要以另一種方式執行，則可以在 Exchange 系統管理中心建立自訂角色群組，將「稽核記錄」或「僅供檢視稽核記錄」角色指派給這個群組，然後將非系統管理員帳戶新增至新的角色群組。 如需詳細資訊，請參閱[在 Exchange Online 中管理角色群組](/Exchange/permissions-exo/role-groups)。

    如果您無法從 Microsoft 365 系統管理中心存取 Exchange 系統管理中心，請前往 https://outlook.office365.com/ecp 並使用您的認證登入。

- 若您有稽核記錄的存取權，但並非全域系統管理員或 Power BI 服務系統管理員，則無法進入 Power BI 管理入口網站。 在此情況下，請直接連結到 [Office 365 安全性與合規性中心](https://sip.protection.office.com/#/unifiedauditlog)。

### <a name="access-your-audit-logs"></a>存取您的稽核記錄

若要存取記錄，請務必先在 Power BI 中啟用記錄功能。 如需詳細資訊，請參閱系統管理入口網站文件中的[稽核記錄](service-admin-portal.md#audit-logs)。 啟用稽核到能夠檢視稽核資料之間，可能有最多 48 小時的延遲。 若您未立即看到資料，請稍候再查看稽核記錄。 取得檢視稽核記錄的權限，以及能夠存取記錄的延遲可能相近。

Power BI 稽核記錄可直接透過 [Office 365 安全性與合規性中心](https://sip.protection.office.com/#/unifiedauditlog)取得。 此外，也有 Power BI 管理入口網站的連結：

1. 在 Power BI 中，選取右上角的 **齒輪圖示**，然後選取 [管理入口網站]。

   ![齒輪下拉式功能表已標示 [管理入口網站] 選項的螢幕擷取畫面。](media/service-admin-auditing/powerbi-admin.png)

1. 選取 [稽核記錄]。

1. 選取 [前往 Microsoft 365 系統管理中心]。

   ![已標示 [稽核記錄] 選項和 [前往 Microsoft 365 系統管理中心] 選項的管理入口網站螢幕擷取畫面。](media/service-admin-auditing/audit-log-o365-admin-center.png)

### <a name="search-only-power-bi-activities"></a>僅搜尋 Power BI 活動

您可以依照下列步驟將結果限制在僅 Power BI 活動。 如需活動清單，請參閱文章稍後的[已由 Power BI 稽核的活動](#operations-available-in-the-audit-and-activity-logs)清單。

1. 在 [稽核記錄搜尋] 頁面上，從 [搜尋] 下選取 [活動] 下拉式清單。

2. 選取 [Power BI 活動]。

   ![[審核記錄搜尋] 的螢幕擷取畫面，其中標示出 [Power BI 活動]。](media/service-admin-auditing/audit-log-search-filter-by-powerbi.png)

3. 在選取方塊之外的任何地方選取，將其關閉。

您的搜尋只會傳回 Power BI 活動。

### <a name="search-the-audit-logs-by-date"></a>依日期搜尋稽核記錄

您可以使用 [開始日期] 與 [結束日期] 欄位，依日期範圍搜尋記錄。 預設的選取範圍是過去七天。 顯示畫面會以國際標準時間 (UTC) 格式呈現日期和時間。 您可以指定的最大日期範圍是 90 天。 

如果選定的日期範圍超過 90 天，您會收到錯誤。 如果您使用最大的 90 天日期範圍，請選取目前時間作為 [開始日期]。 否則，您會收到錯誤，指出開始日期早於結束日期。 如果您已在過去 90 天內開啟稽核，日期範圍開始日期不能在開啟稽核的日期之前。

![[審核記錄搜尋] 的螢幕擷取畫面，其中標示出 [開始日期] 和 [結束日期] 選項。](media/service-admin-auditing/search-audit-log-by-date.png)

### <a name="search-the-audit-logs-by-users"></a>依使用者搜尋稽核記錄

您可以搜尋特定使用者所執行活動的稽核記錄項目。 請在 [使用者] 欄位中輸入一或多個使用者名稱。 使用者名稱看起來像電子郵件地址。 這是使用者用來登入 Power BI 的帳戶。 將此方塊保留空白，可傳回貴組織所有使用者 (和服務帳戶) 的項目。

![[審核記錄搜尋] 的螢幕擷取畫面，其中標示出 [使用者]。](media/service-admin-auditing/search-audit-log-by-user.png)

### <a name="view-search-results"></a>檢視搜尋結果

選取 [搜尋] 之後，即會載入搜尋結果。 幾分鐘後，它們就會顯示在 [結果] 下。 搜尋完成後時，顯示畫面會顯示找到的結果數目。 [稽核記錄搜尋] 最多顯示 1000 個事件。 如果有超過 1000 個事件符合搜尋準則，則應用程式會顯示最新的 1000 個事件。

#### <a name="view-the-main-results"></a>檢視主要結果

[結果] 區域具有由搜尋所傳回每個事件的下列資訊。 選取 [結果] 下的欄標題以排序結果。

| **資料行** | **定義** |
| --- | --- |
| 日期 |發生事件時的日期和時間 (UTC 格式)。 |
| IP 位址 |用於已記錄活動的裝置 IP 位址。 應用程式會以 IPv4 或 IPv6 位址格式顯示 IP 位址。 |
| 使用者 |執行觸發事件之動作的使用者 (或服務帳戶)。 |
| 活動 |使用者所執行的活動。 這個值對應至您在 [活動] 下拉式清單中選取的活動。 對於來自 Exchange 系統管理員稽核記錄的事件，此資料行中的值會是 Exchange Cmdlet。 |
| 項目 |因對應活動而建立或修改的物件。 例如，已檢視或已修改的檔案，或是已更新的使用者帳戶。 並非所有活動在此資料行中都具有值。 |
| 詳細資料 |關於活動的其他詳細資料。 同樣地，並非所有活動都有值。 |

#### <a name="view-the-details-for-an-event"></a>檢視事件的詳細資料

若要檢視事件的詳細資料，請選取搜尋結果清單中的事件記錄。 [詳細資料] 頁面隨即出現，其中包含事件記錄的詳細屬性。 [詳細資料] 頁面所顯示屬性取決於發生事件的 Microsoft 365 服務。

若要顯示這些詳細資料，請選取 [更多資訊]。 所有 Power BI 項目的 RecordType 屬性值都是 20。 如需有關其他屬性的詳細資訊，請參閱[稽核記錄中的詳細屬性](/office365/securitycompliance/detailed-properties-in-the-office-365-audit-log/)。

   ![稽核 [詳細資料] 對話方塊已標示 [詳細資料] 選項的螢幕擷取畫面。](media/service-admin-auditing/audit-details.png)

### <a name="export-search-results"></a>匯出搜尋結果

若要將 Power BI 稽核記錄匯出至 CSV 檔案，請遵循下列步驟執行。

1. 選取 [匯出結果]。

1. 選取 \[Save loaded results] \(儲存載入結果) 或 \[Download all results] \(下載所有結果)。

    ![[匯出結果] 選項的螢幕擷取畫面，其中標示出 [下載所有結果]。](media/service-admin-auditing/export-auditing-results.png)

### <a name="use-powershell-to-search-audit-logs"></a>使用 PowerShell 來搜尋稽核記錄

您也可以使用 PowerShell，依據您的登入存取稽核記錄。 下列範例顯示如何連線至 Exchange Online PowerShell，並接著使用 [Search-UnifiedAuditLog](/powershell/module/exchange/policy-and-compliance-audit/search-unifiedauditlog?view=exchange-ps/) 命令來提取 Power BI 稽核記錄項目。 若要執行該指令碼，系統管理員必須將適當的權限指派給您，如[稽核記錄需求](#audit-log-requirements)一節中所述。

```powershell
Set-ExecutionPolicy RemoteSigned

$UserCredential = Get-Credential

$Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection

Import-PSSession $Session
Search-UnifiedAuditLog -StartDate 9/11/2018 -EndDate 9/15/2018 -RecordType PowerBI -ResultSize 1000 | Format-Table | More
```

### <a name="use-powershell-to-export-audit-logs"></a>使用 PowerShell 來匯出稽核記錄錄

您也可以使用 PowerShell 來匯出稽核記錄搜尋的結果。 下列範例示範如何從 [Search-UnifiedAuditLog](/powershell/module/exchange/policy-and-compliance-audit/search-unifiedauditlog?view=exchange-ps/) 命令傳送，然後使用 [Export-Csv](/powershell/module/microsoft.powershell.utility/export-csv) Cmdlet 來匯出結果。 若要執行該指令碼，系統管理員必須將適當的權限指派給您，如[稽核記錄需求](#audit-log-requirements)一節中所述。

```powershell
$UserCredential = Get-Credential

$Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection

Import-PSSession $Session
Search-UnifiedAuditLog -StartDate 9/11/2019 -EndDate 9/15/2019 -RecordType PowerBI -ResultSize 5000 |
Export-Csv -Path "c:\temp\PowerBIAuditLog.csv" -NoTypeInformation

Remove-PSSession $Session
```

如需如何連線至 Exchange Online 的詳細資訊，請參閱[連線至 Exchange Online PowerShell](/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell/)。 如需搭配稽核記錄使用 PowerShell 的另一個範例，請參閱[使用 Power BI 稽核記錄與 PowerShell 來指派 Power BI Pro 授權](https://powerbi.microsoft.com/blog/using-power-bi-audit-log-and-powershell-to-assign-power-bi-pro-licenses/) \(英文\)。

## <a name="operations-available-in-the-audit-and-activity-logs"></a>稽核記錄和活動記錄中可用的作業

下列作業適用於稽核記錄和活動記錄。

| 易記名稱                                     | 作業名稱                              | 備忘稿                                  |
|---------------------------------------------------|---------------------------------------------|------------------------------------------|
| Excel 中存取 Power BI 的精選資料表 | AnalyzedByExternalApplication |    |
| 已將資料來源新增至 Power BI 閘道             | AddDatasourceToGateway                      |                                          |
| 已新增 Power BI 資料夾存取權                      | AddFolderAccess                             | 目前未使用                       |
| 已新增 Power BI 群組成員                      | AddGroupMembers                             |                                          |
| 系統管理員已將資料流程儲存體帳戶連結至租用戶 | AdminAttachedDataflowStorageAccountToTenant | 目前未使用                       |
| 已分析 Power BI 資料集                         | AnalyzedByExternalApplication               | 當使用者與服務互動時產生                                         |
| 已分析 Power BI 報表                          | AnalyzeInExcel                              |                                          |
| 已將工作區指派至部署管線                          | AssignWorkspaceToPipeline                              |                                          |
| 已附加資料流程儲存體帳戶                 | AttachedDataflowStorageAccount              |                                          |
| 已將 Power BI 資料集繫結至閘道                | BindToGateway                               |                                          |
| 已取消資料流程重新整理                        | CancelDataflowRefresh                       |                                          |
| 已變更容量狀態                            | ChangeCapacityState                         |                                          |
| 已變更容量使用者指派                  | UpdateCapacityUsersAssignment               |                                          |
| 已變更 Power BI 資料集連線              | SetAllConnections                           |                                          |
| 已變更 Power BI 閘道管理員                   | ChangeGatewayAdministrators                 |                                          |
| 已變更 Power BI 閘道資料來源使用者        | ChangeGatewayDatasourceUsers                |                                          |
| 已建立組織自訂視覺效果                          | InsertOrganizationalGalleryItem                                |                                          |
| 已建立組織 Power BI 內容套件      | CreateOrgApp                                |                                          |
| 已建立部署管線      | CreateAlmPipeline                                |                                          |
| 已建立 Power BI 應用程式                              | CreateApp                                   |                                          |
| 已建立 Power BI 儀表板                        | CreateDashboard                             |                                          |
| 已建立 Power BI 資料流程                         | CreateDataflow                              |                                          |
| 已建立 Power BI 資料集                          | CreateDataset                               |                                          |
| 已建立 Power BI 電子郵件訂用帳戶               | CreateEmailSubscription                     |                                          |
| 已建立 Power BI 資料夾                           | CreateFolder                                |                                          |
| 已建立 Power BI 閘道                          | CreateGateway                               |                                          |
| 已建立 Power BI 群組                            | CreateGroup                                 |                                          |
| 已建立 Power BI 報表                           | CreateReport <sup>1</sup>                                |                                          |
| 建立 Power BI 範本應用程式工作區 | CreateTemplateApp   |
| 建立 Power BI 範本應用程式安裝票證 | CreateTemplateAppInstallTicket |
| 建立 Power BI 範本應用程式套件 | CreateTemplateAppPackage |
| 自訂視覺效果要求的 Azure AD 存取權杖                           | GenerateCustomVisualAADAccessToken                                |                                          |
| 自訂視覺效果要求的 Office Web Apps 存取權杖                           | GenerateCustomVisualWACAccessToken                                |                                          |
| 已將資料流程移轉至外部儲存體帳戶     | DataflowMigratedToExternalStorageAccount    | 目前未使用                       |
| 已新增資料流程權限                        | DataflowPermissionsAdded                    | 目前未使用                       |
| 已移除資料流程權限                      | DataflowPermissionsRemoved                  | 目前未使用                       |
| 已刪除組織自訂視覺效果     | DeleteOrganizationalGalleryItem                                |                                          |
| 已刪除部署管線      | DeleteAlmPipeline                                |                                          |
| 已刪除組織 Power BI 內容套件      | DeleteOrgApp                                |                                          |
| 已刪除 Power BI 註解                          | DeleteComment                               |                                          |
| 已刪除 Power BI 儀表板                        | DeleteDashboard                             | 目前未使用                       |
| 已刪除 Power BI 資料流程                         | DeleteDataflow                              | 目前未使用                       |
| 已刪除 Power BI 資料集                          | DeleteDataset                               |                                          |
| 已刪除 Power BI 電子郵件訂用帳戶               | DeleteEmailSubscription                     |                                          |
| 已刪除 Power BI 資料夾                           | DeleteFolder                                |                                          |
| 已刪除 Power BI 資料夾存取權                    | DeleteFolderAccess                          | 目前未使用                       |
| 已刪除 Power BI 閘道                          | DeleteGateway                               |                                          |
| 已刪除 Power BI 群組                            | DeleteGroup                                 |                                          |
| 已刪除 Power BI 報表                           | DeleteReport                                |                                          |
| 已刪除 Power BI 範本應用程式工作區 | DeleteTemplateApp |
| 已刪除 Power BI 範本應用程式套件 | DeleteTemplateAppPackage |
| 已部署至管線階段                           | DeployAlmPipeline                                |                                          |
| 已探索到 Power BI 資料集資料來源          | GetDatasources                              |                                          |
| 下載 Power BI 報表                        | DownloadReport                              |                                          |
| 已編輯資料流程屬性                        | EditDataflowProperties                      |                                          |
| 已編輯 Power BI 認證權限          | EditCertificationPermission                 | 目前未使用                       |
| 已編輯 Power BI 儀表板                         | EditDashboard                               | 目前未使用                       |
| 已編輯 Power BI 資料集                           | EditDataset                                 |                                          |
| 已編輯 Power BI 資料集屬性                | EditDatasetProperties                       | 目前未使用                       |
| 已編輯 Power BI 報表                            | EditReport                                  |                                          |
| 已匯出 Power BI 資料流程                        | ExportDataflow                              |                                          |
| 已匯出 Power BI 報表視覺效果資料              | ExportReport                                |                                          |
| 已匯出 Power BI 磚資料                       | ExportTile                                  |                                          |
| 已解壓縮 Power BI 範本應用程式套件至工作區 | ExtractTemplateAppPackage |
| 無法新增資料流程權限                | FailedToAddDataflowPermissions              | 目前未使用                       |
| 無法移除資料流程權限             | FailedToRemoveDataflowPermissions           | 目前未使用                       |
| 已產生 Power BI 資料流程 SAS 權杖             | GenerateDataflowSasToken                    |                                          |
| 已產生 Power BI 內嵌權杖                    | GenerateEmbedToken                          |                                          |
| 產生螢幕擷取畫面                       | GenerateScreenshot |                     |
| 已將檔案匯入 Power BI                         | 匯入                                      |                                          |
| 已安裝 Power BI 應用程式                            | InstallApp                                  |                                          |
| 已安裝 Power BI 範本應用程式 | InstallTemplateApp |
| 已將工作區移轉至容量                  | MigrateWorkspaceIntoCapacity                |                                          |
| 已張貼 Power BI 註解                           | PostComment                                 |                                          |
| 已列印 Power BI 儀表板                        | PrintDashboard                              |                                          |
| 已列印 Power BI 報表頁面                      | PrintReport                                 |                                          |
| 已升級 Power BI 範本應用程式套件 | PromoteTemplateAppPackage |
| 已將 Power BI 報表發佈到 Web                  | PublishToWebReport <sup>2</sup>                         |                                          |
| 已發佈或更新的精選資料表 | UpdateFeaturedTables <sup>3</sup>   | |
| 已從金鑰保存庫收到 Power BI 資料流程密碼  | ReceiveDataflowSecretFromKeyVault           |                                          |
| 已從部署管線移除工作區         | UnassignWorkspaceFromPipeline                 |                                          |
| 已從 Power BI 閘道移除資料來源         | RemoveDatasourceFromGateway                 |                                          |
| 已移除 Power BI 群組成員                    | DeleteGroupMembers                          |                                          |
| 已從容量移除工作區                 | RemoveWorkspacesFromCapacity                |                                          |
| 已重新命名 Power BI 儀表板                        | RenameDashboard                             |                                          |
| 已要求 Power BI 資料流程重新整理               | RequestDataflowRefresh                      | 目前未使用                       |
| 已要求 Power BI 資料集重新整理                | RefreshDataset                              |                                          |
| 已擷取 Power BI 工作區                     | GetWorkspaces                               |                                          |
| 已套用敏感度標籤                         | SensitivityLabelApplied                     |                                          |
| 已變更敏感度標籤                         | SensitivityLabelChanged                     |                                          |
| 已移除敏感度標籤                         | SensitivityLabelRemoved                     |                                          |
| 設定工作區的資料流程儲存位置     | SetDataflowStorageLocationForWorkspace      |                                          |
| 對 Power BI 資料流程設定排定的重新整理        | SetScheduledRefreshOnDataflow               |                                          |
| 對 Power BI 資料集設定排定的重新整理         | SetScheduledRefresh                         |                                          |
| 已共用 Power BI 儀表板                         | ShareDashboard                              |                                          |
| 已共用 Power BI 報表                            | ShareReport                                 |                                          |
| 已啟動 Power BI 延長試用版                   | OptInForExtendedProTrial                    | 目前未使用                       |
| 已開始 Power BI 試用版                            | OptInForProTrial                            |                                          |
| 已接管 Power BI 資料來源                   | TakeOverDatasource                          |                                          |
| 已接管 Power BI 資料集                        | TakeOverDataset                             |                                          |
| 已接管 Power BI 資料流程                     | TookOverDataflow                             |                                          |
| 已解除發佈 Power BI 應用程式                          | UnpublishApp                                |                                          |
| 更新容量資源管控設定      | UpdateCapacityResourceGovernanceSettings    | 目前不在 Microsoft 365 系統管理中心內 |
| 已更新組織自訂視覺效果                     | UpdateOrganizationalGalleryItem                   |                                          |
| 已更新容量管理                            | UpdateCapacityAdmins                        |                                          |
| 已更新容量顯示名稱                     | UpdateCapacityDisplayName                   |                                          |
| 已更新資料流程的儲存體指派權限   | UpdatedDataflowStorageAssignmentPermissions |                                          |
| 已更新部署管線存取   | UpdateAlmPipelineAccess |                                          |
| 已更新安裝的 Power BI 範本應用程式參數 | UpdateInstalledTemplateAppParameters |
| 已更新部署管線設定   | SetConfigurationAlmPipeline |                                          |
| 已更新組織的 Power BI 設定          | UpdatedAdminFeatureSwitch                   |                                          |
| 已更新 Power BI 應用程式                              | UpdateApp                                   |                                          |
| 已更新 Power BI 資料流程                         | UpdateDataflow                              |                                          |
| 已更新 Power BI 資料集資料來源             | UpdateDatasources                           |                                          |
| 已更新 Power BI 資料集參數               | UpdateDatasetParameters                     |                                          |
| 已更新 Power BI 電子郵件訂用帳戶               | UpdateEmailSubscription                     |                                          |
| 已更新 Power BI 資料夾                           | UpdateFolder                                |                                          |
| 已更新 Power BI 資料夾存取權                    | UpdateFolderAccess                          |                                          |
| 已更新 Power BI 閘道資料來源認證  | UpdateDatasourceCredentials                 |                                          |
| 已更新 Power BI 範本應用程式設定 | UpdateTemplateAppSettings |
| 已更新 Power BI 範本應用程式測試存取權限 | UpdateTemplateAppTestPackagePermissions |
| 已檢視 Power BI 儀表板                         | ViewDashboard                               |                                          |
| 已檢視 Power BI 資料流程                          | ViewDataflow                                |                                          |
| 已檢視 Power BI 報表                            | ViewReport                                  |                                          |
| 已檢視 Power BI 磚                              | ViewTile                                    |                                          |
| 已檢視 Power BI 使用計量                     | ViewUsageMetrics                            |                                          |
|                                                   |                                             |                                          |

<sup>1</sup> 從 Power BI Desktop 發佈到服務是在服務中的 CreateReport 事件。

<sup>2</sup> PublishtoWebReport 指的是[發佈至 Web](../collaborate-share/service-publish-to-web.md) 功能。

<sup>3</sup> UpdateFeaturedTables 指的是 [Excel 中的 Power BI 精選資料表](../collaborate-share/service-excel-featured-tables.md)。

## <a name="next-steps"></a>後續步驟

- [什麼是 Power BI 管理？](service-admin-administering-power-bi-in-your-organization.md)
- [Power BI 管理入口網站](service-admin-portal.md)
- [存取 Power BI 活動記錄](../guidance/admin-activity-log.md)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com/)