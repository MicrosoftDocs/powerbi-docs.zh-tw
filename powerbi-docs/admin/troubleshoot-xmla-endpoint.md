---
title: 針對 Power BI 中的 XMLA 端點連線進行疑難排解
description: 描述如何透過 Power BI Premium 中的 XMLA 端點，針對連線能力進行疑難排解。
author: Minewiskan
ms.author: kfollis
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: troubleshooting
ms.date: 02/02/2021
ms.custom: seodec18, css_fy20Q4
LocalizationGroup: Premium
ms.openlocfilehash: 98bc3da33f38974f3dfcb9e155111e7d16e6c069
ms.sourcegitcommit: f7330dabb9cd8bce90bb2efec3e3273a11578f10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2021
ms.locfileid: "99494457"
---
# <a name="troubleshoot-xmla-endpoint-connectivity"></a>針對 XMLA 端點連線能力進行疑難排解

Power BI Premium 中的 XMLA 端點依賴原生的 Analysis Services 通訊協定來存取 Power BI 資料集。 因此，XMLA 端點疑難排解會與針對一般 Analysis Services 連線進行疑難排解大致相同。 不過，某些特定於 Power BI 特定相依性的相關差異也適用。

## <a name="before-you-begin"></a>開始之前

針對 XMLA 端點案例進行疑難排解之前，請務必檢閱[使用 XMLA 端點連線至資料集](service-premium-connect-tools.md)中所涵蓋的基本概念。 其中涵蓋最常見的 XMLA 端點使用案例。 其他 Power BI 疑難排解指南 (例如[針對閘道進行疑難排解 - Power BI](../connect-data/service-gateway-onprem-tshoot.md) 與[針對「使用 Excel 分析」進行疑難排解](../collaborate-share/desktop-troubleshooting-analyze-in-excel.md)) 也很有幫助。

## <a name="enabling-the-xmla-endpoint"></a>啟用 XMLA 端點

您可以同時在 Power BI Premium 和 Power BI Embedded 容量上啟用 XMLA 端點。 在較小的容量 (例如，只有 2.5 GB 記憶體的 A1 容量) 中，您可能會在嘗試將 XMLA 端點設定為 [讀取/寫入]，然後選取 [套用] 時，於 [容量設定] 中遇到錯誤。 此錯誤表示「您的工作負載設定發生問題。 請於稍後重試。」

以下是數個可嘗試的事項：

- 將容量上其他服務的記憶體耗用量 (例如資料流程) 限制為 40% (或更少)，或完全停用不必要的服務。  
- 將容量升級到較大的 SKU。 例如，從 A1 升級到 A3 容量即可解決此設定問題，而不需停用資料流程。

請記住，您也必須在 Power BI 管理入口網站中，啟用租用戶層級的[匯出資料設定](service-premium-connect-tools.md#security)。 [使用 Excel 分析] 功能也需要此設定。

## <a name="establishing-a-client-connection"></a>建立用戶端連線

啟用 XMLA 端點之後，在容量上測試與工作區的連線能力是個不錯的主意。 若要深入了解，請參閱[連線到 Premium 工作區](service-premium-connect-tools.md#connecting-to-a-premium-workspace)。 此外，請務必閱讀[連線需求](service-premium-connect-tools.md#connection-requirements)一節，以取得有關目前 XMLA 連線能力限制的實用秘訣和資訊。

### <a name="connecting-with-a-service-principal"></a>使用服務主體連線

如果您已啟用租用戶設定，以允許服務主體使用 Power BI API (如[啟用服務主體](service-premium-service-principal.md#enable-service-principals)中所述)，您就能夠使用服務主體連線到 XMLA 端點。 請記住，服務主體在工作區或資料集層級上，需要具有與一般使用者相同層級的存取權限。

若要使用服務主體，請務必在連接字串中指定應用程式身分識別資訊，如下所示：

- `User ID=<app:appid@tenantid>`
- `Password=<application secret>`

例如：

`Data Source=powerbi://api.powerbi.com/v1.0/myorg/Contoso;Initial Catalog=PowerBI_Dataset;User ID=app:91ab91bb-6b32-4f6d-8bbc-97a0f9f8906b@19373176-316e-4dc7-834c-328902628ad4;Password=6drX...;`

如果您收到下列錯誤：

「因為帳戶資訊不完整，所以我們無法連線到資料集。 針對服務主體，確定您會使用格式應用程式，一起指定租用戶識別碼與應用程式識別碼：\<appId>@\<tenantId>，然後再試一次。」

確定您會使用正確的格式，一起指定租用戶識別碼與應用程式識別碼。

指定應用程式識別碼但不指定租用戶識別碼也同樣有效。 不過，在此情況下，您必須以實際的租用戶識別碼取代資料來源 URL 中的 `myorg` 別名。 Power BI 接著可在正確的租用戶中尋找服務主體。 但最佳做法是使用 `myorg` 別名，並在使用者識別碼參數中，一起指定租用戶識別碼和應用程式識別碼。

### <a name="connecting-with-azure-active-directory-b2b"></a>使用 Azure Active Directory B2B 連線

透過支援 Power BI 中的 Azure Active Directory (Azure AD) 企業對企業 (B2B)，您可以為外部來賓使用者提供透過 XMLA 端點存取資料集的權限。 請確定已在 Power BI 管理入口網站中，啟用[與外部使用者共用內容](service-admin-portal.md#export-and-sharing-settings)設定。 若要深入了解，請參閱[使用 Azure AD B2B 將 Power BI 內容散發給外部來賓使用者](service-admin-azure-ad-b2b.md)。

## <a name="deploying-a-dataset"></a>部署資料集

您可以將 Visual Studio (SSDT) 中的表格式模型專案部署至 Power BI Premium 工作區，就像部署至 Azure Analysis Services 一樣。 不過，部署至 Power BI Premium 工作區時，還有一些額外考量。 請務必檢閱《使用 XMLA 端點連線至資料集》一文中的[從 Visual Studio (SSDT) 部署模型專案](service-premium-connect-tools.md#deploy-model-projects-from-visual-studio-ssdt)一節。

### <a name="deploying-a-new-model"></a>部署新模型

在預設設定中，Visual Studio 會在部署作業期間嘗試處理模型，以便將來自資料來源的資料載入到資料集。 如[從 Visual Studio (SSDT) 部署模型專案](service-premium-connect-tools.md#deploy-model-projects-from-visual-studio-ssdt)中所述，此作業可能會失敗，因為無法在部署作業期間指定資料來源認證。 相反地，如果您尚未針對任何現有資料集定義資料來源的認證，您就必須使用 Power BI 使用者介面 ([資料集] > [設定] > [資料來源認證] > [編輯認證])，在資料集設定中指定資料來源認證。 定義資料來源認證之後，Power BI 就可以在中繼資料部署成功且已建立資料集之後，針對任何新的資料集自動將認證套用到此資料來源。

如果 Power BI 無法將您的新資料集繫結至資料來源認證，您將會收到錯誤，指出「無法處理資料庫。 理由：無法將修改儲存到伺服器。」 錯誤碼為 "DMTS_DatasourceHasNoCredentialError"，如下所示：

:::image type="content" source="media/troubleshoot-xmla-endpoint/deploy-refresh-error.png" alt-text="模型部署錯誤":::

若要避免處理失敗，請將 [部署選項] > [處理選項] 設定為 [不處理]，如下圖所示。 Visual Studio 接著就只會部署中繼資料。 然後，您可以設定資料來源認證，並在 Power BI 使用者介面中，針對資料集按一下 [立即重新整理]。 如需對處理問題進行疑難排解的相關資訊，請參閱此文章稍後的[重新整理資料集](#refreshing-a-dataset)一節。

:::image type="content" source="media/troubleshoot-xmla-endpoint/do-not-process.png" alt-text="[不處理] 選項":::

### <a name="new-project-from-an-existing-dataset"></a>從現有資料集新增專案

不支援從 Power BI Premium 工作區上的現有資料集匯入中繼資料，以在 Visual Studio 中建立新的表格式專案。 不過，您可以使用 SQL Server Management Studio 來連線到資料集、編寫中繼資料的指令碼，然後在其他表格式專案中重複使用。

## <a name="migrating-a-dataset-to-power-bi"></a>將資料集移轉至 Power BI

建議您為表格式模型指定 1500 (或更高) 相容性層級。 此相容性層級支援大部分的功能和資料來源類型。 較新的相容性層級會與較早的層級回溯相容。

### <a name="supported-data-providers"></a>支援的資料提供者

在 1500 相容性層級上，Power BI 支援下列資料來源類型：

- 提供者資料來源 (模型中繼資料中含有連接字串的舊版)。
- 結構化資料來源 (透過 1400 相容性層級引進)。
- 資料來源的內嵌 M 宣告 (因為 Power BI Desktop 會宣告這類資料來源)。

建議您使用結構化資料來源，Visual Studio 預設會在進行匯入資料流程時建立這類來源。 不過，如果您正打算將現有模型移轉到 Power BI 以使用提供者資料來源，請確定提供者資料來源依賴支援的資料提供者。 特別是 Microsoft OLE DB Driver for SQL Server 和任何協力廠商 ODBC 驅動程式。 針對 OLE DB Driver for SQL Server，您必須將資料來源定義切換到 .NET Framework Data Provider For SQL Server。 對於可能無法在 Power BI 服務中使用的協力廠商 ODBC 驅動程式，您必須改為切換到結構化資料來源定義。

此外，也建議您在 SQL Server 資料來源定義中，以 .NET Framework Data Provider for SQL Server 取代已過期的 Microsoft OLE DB Driver for SQL Server (SQLNCLI11)。

下表提供 .NET Framework Data Provider for SQL Server 連接字串範例，可用來取代 OLE DB Driver for SQL Server 的對應連接字串。

|OLE DB Driver for SQL Server  |.NET Framework Data Provider for SQL Server   |
|---------|---------|
|`Provider=SQLNCLI11;Data Source=sqldb.database.windows.net;Initial Catalog=AdventureWorksDW;Trusted_Connection=yes;`    |   `Data Source=sqldb.database.windows.net;Initial Catalog=AdventureWorksDW2016;Integrated Security=SSPI;Encrypt=true;TrustServerCertificate=false`       |

### <a name="cross-referencing-partition-sources"></a>交互參照分割區來源

就像有多個資料來源類型，表格式模型也可以包含多個分割區來源類型，以將資料匯入到資料表。 具體而言，分割區可以使用查詢分割區來源或 M 分割區來源。 這些分割區來源類型接著就能參考提供者資料來源或結構化資料來源。 儘管 Azure Analysis Services 中的表格式模型支援交互參照這些不同的資料來源和分割區類型，Power BI 還是會強制執行更嚴格的關聯性。 查詢分割區來源必須參考提供者資料來源，而 M 分割區來源必須參考結構化資料來源。 Power BI 中不支援其他組合。 如果您想要移轉交互參照資料集，下表描述支援的設定：  

|資料來源   |分割區來源   |註解   |已在使用 XMLA 端點的 Power BI Premium 中支援   |
|---------|---------|---------|---------|
|提供者資料來源      |   查詢分割區來源      |   AS 引擎會使用卡匣型連線堆疊來存取資料來源。       |     是     |
|提供者資料來源      |   M 分割區來源       |   AS 引擎會將提供者資料來源轉譯為一般結構化資料來源，然後使用混搭引擎來匯入資料。       |    否     |
|結構化資料來源      |     查詢分割區來源     |    AS 引擎會將分割區來源上的原生查詢包裝成 M 運算式，然後使用混搭引擎來匯入資料。      |    否     |
|結構化資料來源      |    M 分割區來源      |     AS 引擎會使用混搭引擎來匯入資料。     |   是      |

## <a name="refreshing-a-dataset"></a>重新整理資料集

XMLA 端點可讓您針對表格式模型以及 Power BI Desktop 中建立的資料集，執行重新整理作業。 若要支援後者，請確定您指定的是增強的儲存格式設定。 如果您想要使用 XMLA 端點來執行處理或其他讀取/寫入作業，則需要此設定。 您可以在 Power BI Desktop 的 [預覽功能] 底下找到此設定。 設定之後，再次將您的 PBIX 解決方案發佈到您的 Power BI Premium 工作區。  

如果您針對不含已增強中繼資料的模型，透過 XMLA 端點執行重新整理，Power BI 會傳回下列錯誤：「只有 Power BI Premium 中屬性 'DefaultPowerBIDataSourceVersion' 設定為 'PowerBI_V3' 的模型才支援此作業。」

### <a name="data-sources-and-impersonation"></a>資料來源和模擬

您可以為提供者資料來源定義的模擬設定與 Power BI 無關。 Power BI 會使用以資料集設定為基礎的不同機制來管理資料來源認證。 基於這個理由，如果您要建立提供者資料來源，請務必選取 [服務帳戶]。

:::image type="content" source="media/troubleshoot-xmla-endpoint/impersonate-services-account.png" alt-text="模擬服務帳戶":::

### <a name="fine-grained-processing"></a>更精細的處理

在 Power BI 中觸發已排程的重新整理或視需要重新整理時，Power BI 通常會重新整理整個資料集。 在許多情況下，以更有選擇性的方式再次執行重新整理會更有效率。 您可以在 SQL Server Management Studio (SSMS) 中 (如下所示)，或是使用協力廠商工具或指令碼，來執行更精細的處理工作。

:::image type="content" source="media/troubleshoot-xmla-endpoint/process-tables.png" alt-text="在 SSMS 中處理資料表":::

### <a name="overrides-in-refresh-tmsl-command"></a>Refresh TMSL 命令中的覆寫

[Refresh 命令 (TMSL)](/analysis-services/tmsl/refresh-command-tmsl) 中的覆寫，可供使用者選擇不同磁碟分割查詢定義或重新整理作業的資料來源定義。 目前，Power BI Premium 中 **不支援覆寫**。 Power BI Premium 中不允許「非正規繫結」錯誤。 如需其他資訊，請參閱產品文件中的「XMLA 讀取/寫入支援」。 」錯誤訊息。

## <a name="errors-in-ssms---premium-gen-2"></a>SSMS 中的錯誤 - Premium Gen 2

### <a name="query-execution"></a>查詢執行

連線到 [Premium Gen2](service-premium-what-is.md#power-bi-premium-generation-2-preview) 容量中的工作區時，SQL Server Management Studio 可能會顯示下列錯誤：

```
Executing the query ...
Error -1052311437:
```

發生此錯誤的原因，是因為使用 SSMS v18.7.1 安裝的用戶端程式庫不支援工作階段追蹤。 此錯誤已在 SSMS 18.8 與更新版本中解決。 [下載最新的 SSMS](/sql/ssms/download-sql-server-management-studio-ssms)。

### <a name="refresh-operations"></a>重新整理作業

使用 SSMS v18.7.1 或更低版本，在 Premium Gen2 容量中的資料集上執行長時間執行 (> 1 分鐘) 的重新整理作業時，SSMS 可能會顯示類似下列的錯誤，即使重新整理作業成功也一樣：

```
Executing the query ...
Error -1052311437:
The remote server returned an error: (400) Bad Request.

Technical Details:
RootActivityId: 3716c0f7-3d01-4595-8061-e6b2bd9f3428
Date (UTC): 11/13/2020 7:57:16 PM
Run complete
```

這是由用戶端程式庫中的已知問題所引發，其中系統並未正確追蹤重新整理要求的狀態。 此錯誤已在 SSMS 18.8 與更新版本中解決。 [下載最新的 SSMS](/sql/ssms/download-sql-server-management-studio-ssms)。

## <a name="editing-role-memberships-in-ssms"></a>在 SSMS 中編輯角色成員資格

當使用 SQL Server Management Studio (SSMS) v18.8 編輯資料集的角色成員資格時，SSMS 可能會顯示下列錯誤：

```
Failed to save modifications to the server. 
Error returned: ‘Metadata change of current operation cannot be resolved, please check the command or try again later.’ 
```

這是因為應用程式服務 REST API 中的已知問題所致。 這將會在即將推出的版本中解決。 在此同時，若要解決此錯誤，請在 [角色屬性] 中按一下 [指令碼]，然後輸入下列 TMSL 命令並加以執行：

```json
{ 
  "createOrReplace": { 
    "object": { 
      "database": "AdventureWorks", 
      "role": "Role" 
    }, 
    "role": { 
      "name": "Role", 
      "modelPermission": "read", 
      "members": [ 
        { 
          "memberName": "xxxx", 
          "identityProvider": "AzureAD" 
        }, 
        { 
          "memberName": “xxxx” 
          "identityProvider": "AzureAD" 
        } 
      ] 
    } 
  } 
} 
```

## <a name="publish-error---live-connected-dataset"></a>發佈錯誤 - 即時連線的資料集

當利用 Analysis Services 連接器重新發佈即時連線的資料集時，可能會顯示下列錯誤：

:::image type="content" source="media/troubleshoot-xmla-endpoint/couldnt-publish-to-power-bi.png" alt-text="無法發佈至 Power BI 錯誤。":::

如錯誤訊息中所述，若要解決此問題，請刪除或重新命名現有的資料集。 也請務必重新發佈與此報表有關的任何應用程式。 如有必要，下游使用者也應收到更新具有新報表位址之任何書籤的通知，以確定他們可以存取最新的報表。  

## <a name="workspaceserver-alias"></a>工作區/伺服器別名

不同於 Azure Analysis Services，Power BI Premium 工作區 **不支援** 伺服器名稱 [別名](/azure/analysis-services/analysis-services-server-alias)。 

## <a name="dataset-refresh-through-the-xmla-endpoint"></a>透過 XMLA 端點重新整理資料集

上次重新整理日期與時間會顯示在 Power BI 中的幾處位置，例如報表ˇ與清單中的 [已重新整理] 資料行、[資料集詳細資料]、[資料集設定]，以及 [資料集重新整理記錄]。 目前，Power BI 中所顯示重新整理日期與時間 **不** 包含使用 TMSL/TOM、SSMS 或協力廠商工具來透過 XMLA 端點執行的重新整理作業。

## <a name="discover_m_expressions"></a>DISCOVER_M_EXPRESSIONS 

使用 XMLA 端點的 Power BI 中，目前不支援 DMV DISCOVER_M_EXPRESSIONS 資料管理檢視 (DMV) 。 應用程式可以使用表格式物件模型 (TOM) 來取得資料模型所使用的 M 運算式。

## <a name="see-also"></a>另請參閱

[使用 XMLA 端點連線至資料集](service-premium-connect-tools.md)  
[使用服務主體將 Premium 工作區與資料集工作自動化](service-premium-service-principal.md)  
[對 [使用 Excel 分析] 進行疑難排解](../collaborate-share/desktop-troubleshooting-analyze-in-excel.md)  
[表格式模型解決方案部署](/analysis-services/deployment/tabular-model-solution-deployment?view=power-bi-premium-current&preserve-view=true)
