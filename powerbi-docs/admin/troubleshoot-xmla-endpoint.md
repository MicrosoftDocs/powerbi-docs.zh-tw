---
title: 在 Power BI Premium (預覽) 中針對 XMLA 端點連線能力進行疑難排解
description: 描述如何透過 Power BI Premium 中的 XMLA 端點，針對連線能力進行疑難排解。
author: minewiskan
ms.author: owend
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: troubleshooting
ms.date: 07/28/2020
ms.custom: seodec18, css_fy20Q4
LocalizationGroup: Premium
ms.openlocfilehash: bd2b8c4af1fc36fabc863aa1c67ed5af40265de2
ms.sourcegitcommit: 9350f994b7f18b0a52a2e9f8f8f8e472c342ea42
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90854073"
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

[Refresh 命令 (TMSL)](/analysis-services/tmsl/refresh-command-tmsl) 中的覆寫，可供使用者選擇不同磁碟分割查詢定義或重新整理作業的資料來源定義。 目前，Power BI Premium 中**不支援覆寫**。 Power BI Premium 中不允許「非正規繫結」錯誤。 如需其他資訊，請參閱產品文件中的「XMLA 讀取/寫入支援」。 」錯誤訊息。

## <a name="see-also"></a>另請參閱

[與 XMLA 端點的資料集連線能力](service-premium-connect-tools.md)   
[使用服務主體將 Premium 工作區與資料集工作自動化](service-premium-service-principal.md)   
[針對「使用 Excel 分析」進行疑難排解](../collaborate-share/desktop-troubleshooting-analyze-in-excel.md)   
[表格式模型解決方案部署](/analysis-services/deployment/tabular-model-solution-deployment?view=power-bi-premium-current)