---
title: 適用於 Power BI 的 Azure 安全性基準
description: Power BI 的安全性基準提供程式指引和資源，可用來實作 Azure 安全性效能評定中所指定的安全性建議。
author: mbaldwin
ms.author: margoc
ms.service: powerbi
ms.subservice: pbi-security
ms.topic: conceptual
ms.date: 11/20/2020
ms.custom: subject-security-benchmark
ms.openlocfilehash: a76c7f9d205fe47322768a514a1e5d89a36a2306
ms.sourcegitcommit: 1cad78595cca1175b82c04458803764ac36e5e37
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2021
ms.locfileid: "98565754"
---
# <a name="azure-security-baseline-for-power-bi"></a>適用於 Power BI 的 Azure 安全性基準

此安全性基準會將 [Azure 安全性效能評定 2.0 版](/azure/security/benchmarks/overview)的指引套用至 Power BI。 Azure 安全性基準提供如何在 Azure 上保護雲端解決方案的建議。 此內容是依照 Azure 安全性效能評定所定義的 **安全性控制項**，以及適用於 Power BI 的相關指引來分組。 不適用於 Power BI 的 **控制項** 已遭排除。

若要了解 Power BI 如何完全對應到 Azure 安全性效能評定，請參閱[完整的 Power BI 安全性基準對應檔](https://github.com/MicrosoftDocs/SecurityBenchmarks/tree/master/Azure%20Offer%20Security%20Baselines)。

## <a name="network-security"></a>網路安全性

如需詳細資訊，請參閱 [Azure 安全性效能評定：網路安全性](/azure/security/benchmarks/security-controls-v2-network-security)。

### <a name="ns-3-establish-private-network-access-to-azure-services"></a>NS-3：建立 Azure 服務的私人網路存取

**指引**：Power BI 支援將您的 Power BI 租用戶連線到 Private Link 端點，並停用公用網際網路存取。

- [使用私人連結存取 Power BI](../admin/service-security-private-links.md)

**Azure 資訊安全中心監視**：不適用

**責任**：共用

## <a name="identity-management"></a>身分識別管理

如需詳細資訊，請參閱 [Azure 安全性效能評定：身分識別管理](/azure/security/benchmarks/security-controls-v2-identity-management)。

### <a name="im-1-standardize-azure-active-directory-as-the-central-identity-and-authentication-system"></a>IM-1：將 Azure Active Directory 標準化為中央身分識別與驗證系統

**指引**：Power BI 已與 Azure Active Directory (Azure AD) 整合，後者是 Azure 的預設身分識別與存取權管理服務。 您應該在 Azure AD 上標準化，以控管組織的身分識別與存取權管理。

保護 Azure AD 在組織的雲端安全性實務中，應具有較高的優先順序。 Azure AD 提供身分識別安全分數，協助您評定相對於 Microsoft 最佳做法建議的身分識別安全性狀態。 請使用此分數來測量設定符合最佳做法建議的程度，並改善您的安全性狀態。

注意:Azure AD 支援外部身分識別，可讓沒有 Microsoft 帳戶的使用者使用其外部身分識別登入其應用程式和資源。

- [Azure Active Directory 中的租用](/azure/active-directory/develop/single-and-multi-tenant-apps)

- [如何建立及設定 Azure AD 執行個體](/azure/active-directory/fundamentals/active-directory-access-create-new-tenant)

- [使用應用程式的外部識別提供者](/azure/active-directory/b2b/identity-providers) (機器翻譯)

- [Azure Active Directory 中的身分識別安全分數為何](/azure/active-directory/fundamentals/identity-secure-score) (機器翻譯)

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

### <a name="im-2-manage-application-identities-securely-and-automatically"></a>IM-2：安全且自動地管理應用程式識別碼

**指引**：Power BI 和 Power BI Embedded 支援使用服務主體。 在 Key Vault 中儲存用於加密或存取 Power BI 的任何服務主體認證，將適當的存取原則指派給保存庫，並定期檢閱存取權限。

使用服務主體將 Premium 工作區與資料集工作自動化 https://docs.microsoft.com/power-bi/admin/service-premium-service-principal

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

### <a name="im-3-use-azure-ad-single-sign-on-sso-for-application-access"></a>IM-3：使用 Azure AD 單一登入 (SSO) 進行應用程式存取

**指引**：Power BI 會使用 Azure Active Directory，為 Azure 資源、雲端應用程式及內部部署應用程式提供身分識別與存取權管理。 這包括企業身分識別 (例如員工)，以及外部身分識別 (例如合作夥伴、廠商和供應商)。 這可讓單一登入 (SSO) 管理及保護內部部署和雲端中的組織資料與資源存取。 請將您的所有使用者、應用程式和裝置連線到 Azure AD，以進行順暢且安全的存取，並提供更高的可見度和控制。

- [了解 Azure AD 的應用程式 SSO](/azure/active-directory/manage-apps/what-is-single-sign-on)

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

### <a name="im-4-use-strong-authentication-controls-for-all-azure-active-directory-based-access"></a>IM-4：針對所有以 Azure Active Directory 為基礎的存取，使用增強式驗證控制項

**指引**：Power BI 已與 Azure AD 整合，可透過多重要素驗證 (MFA) 和增強式無密碼方法來支援增強式驗證控制項。
- 多重要素驗證 - 啟用 Azure AD MFA，並遵循 Azure 資訊安全中心身分識別與存取權管理建議，以取得 MFA 設定中的一些最佳做法。 MFA 可以根據登入條件和風險因素，在所有、選取使用者或每個使用者層級上施行。
- 無密碼驗證 – 有三種無密碼驗證選項可供使用：Windows Hello 企業版、Microsoft Authenticator 應用程式和內部部署驗證方法 (例如智慧卡)。

對於系統管理員和特殊權限使用者，請確保使用最高層級的增強式驗證，然後向其他使用者推出適當的增強式驗證原則。

注意:只有在 Azure AD 中啟用的使用者帳戶才能施行 MFA。 Power BI 服務主體不支援使用 MFA。

- [如何在 Azure 中啟用 MFA](/azure/active-directory/authentication/howto-mfa-getstarted)

- [Azure Active Directory 的無密碼驗證選項簡介](/azure/active-directory/authentication/concept-authentication-passwordless) (機器翻譯)

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

### <a name="im-5-monitor-and-alert-on-account-anomalies"></a>IM-5：監視及警示帳戶異常

**指引**：定義 Microsoft Cloud App Security 中可獨立設定範圍的異常偵測原則，使其僅適用於想要包含的使用者和群組。 這些異常偵測原則有助於偵測及監視與使用者存取和使用 Power BI 相關的行為異常。

- [在 Power BI 中使用 Microsoft Cloud App Security 控制措施](../admin/service-security-using-microsoft-cloud-app-security-controls.md)

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

### <a name="im-6-restrict-azure-resource-access-based-on-conditions"></a>IM-6：根據條件限制 Azure 資源存取

**指引**：Power BI 支援根據使用者定義的條件使用 Azure AD 條件式存取，以進行更細微的存取控制，例如來自特定 IP 範圍的使用者登入將需要使用 MFA 進行登入。 細微的驗證工作階段管理原則也可用於不同的使用案例。

- [Azure 條件式存取概觀](/azure/active-directory/conditional-access/overview)

- [一般條件式存取原則](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) (機器翻譯)

- [使用條件式存取來設定驗證工作階段管理](/azure/active-directory/conditional-access/howto-conditional-access-session-lifetime) (機器翻譯)

- [在 Power BI 中使用 Microsoft Cloud App Security 控制措施](../admin/service-security-using-microsoft-cloud-app-security-controls.md)

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

### <a name="im-7-eliminate-unintended-credential-exposure"></a>IM-7：消除非預期的認證暴露

**指引**：針對 Power BI Embedded 應用程式，建議您實作認證掃描器來識別程式碼內的認證。 認證掃描器也有助於將探索到的認證移至更安全的位置，例如 Azure Key Vault。

在 Key Vault 中儲存用於加密或存取 Power BI 的任何加密金鑰或服務主體認證，將適當的存取原則指派給保存庫，並定期檢閱存取權限。
 
針對 GitHub，您可以使用原生祕密掃描功能來識別程式碼內的認證或其他形式的祕密。

- [攜帶您自己的加密金鑰以用於 Power BI](../admin/service-encryption-byok.md)

 
如何設定認證
- [掃描器](https://secdevtools.azurewebsites.net/helpcredscan.html) 

- [GitHub 祕密掃描](https://docs.github.com/github/administering-a-repository/about-secret-scanning) (英文)

**Azure 資訊安全中心監視**：不適用

**責任**：共用

## <a name="privileged-access"></a>特殊權限存取

如需詳細資訊，請參閱 [Azure 安全性效能評定：特殊權限存取](/azure/security/benchmarks/security-controls-v2-privileged-access)。

### <a name="pa-1-protect-and-limit-highly-privileged-users"></a>PA-1：保護及限制高權限使用者

**指引**：為了降低風險並遵循最低權限的準則，建議您將 Power BI 系統管理員的成員資格保留給少數人。 具有這些特殊權限的使用者可能會存取及修改組織的所有管理功能。 全域管理員 (透過 Microsoft 365 或 Azure Active Directory) 也會在 Power BI 服務中隱含擁有系統管理員權限。

Power BI 具有以下高權限帳戶：
- 全域系統管理員
- 帳單系統管理員
- 授權管理員
- 使用者系統管理員
- Power BI 系統管理員
- Power BI Premium 容量系統管理員
- Power BI Embedded 容量系統管理員

Power BI 支援 Azure AD 中的工作階段原則來啟用條件式存取原則，並透過 Cloud App Security 服務路由傳送 Power BI 中使用的工作階段。

使用 M365 Privileged Access Management，啟用 Power BI 系統管理員帳戶的 Just-In-Time (JIT) 特殊權限存取。

- [與 Power BI 相關的系統管理員角色](../admin/service-admin-administering-power-bi-in-your-organization.md#administrator-roles-related-to-power-bi)

- [M365 Privileged Access Management](/microsoft-365/compliance/privileged-access-management-overview?amp;preserve-view=true&view=o365-worldwide)

- [Power BI 中的 Cloud App Security 控制措施](../admin/service-security-using-microsoft-cloud-app-security-controls.md)

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

### <a name="pa-2-restrict-administrative-access-to-business-critical-systems"></a>PA-2：限制對業務關鍵系統的系統管理存取

**指引**：限制對 Power BI 具有更高權限存取權的高權限帳戶或角色數目。

您可以使用[此處](/microsoft-365/compliance/privileged-access-management-overview?amp;preserve-view=true&view=o365-worldwide)的 M365 Privileged Access Management 指引來啟用 Just-In-Time (JIT) 特殊權限存取。

如需其他詳細資料，請參閱[此處](https://aka.ms/PBIEnterpriseDeploymentWP)的 Power BI 企業部署文件第 183 頁。

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

### <a name="pa-3-review-and-reconcile-user-access-regularly"></a>PA-3：定期檢閱及協調使用者存取

**指引**：身為 Power BI 服務系統管理員，您可以使用以 Power BI 活動記錄為基礎的自訂報告來分析租用戶層級上所有 Power BI 資源使用情況。 您可以使用 REST API 或 PowerShell Cmdlet 來下載活動。 還可以依照日期範圍、使用者和活動類型來篩選活動資料。

您必須符合這些需求才能存取 Power BI 活動記錄：
- 您必須是全域管理員或 Power BI 服務管理員。
- 您已在本機安裝 [Power BI 管理 Cmdlet](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt)，或使用 Azure Cloud Shell 中的 Power BI 管理 Cmdlet。

符合這些需求之後，您就可以遵循下列指引來追蹤 Power BI 內的使用者活動：

- [追蹤 Power BI 中的使用者活動](../admin/service-admin-auditing.md)

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

### <a name="pa-4-set-up-emergency-access-in-azure-ad"></a>PA-4：在 Azure AD 中設定緊急存取

**指引**：Power BI 已與 Azure Active Directory 和 M365 整合，可管理其資源。 為了避免不小心鎖定您的 M365 租用戶或 Azure AD 組織，請設定緊急存取帳戶，以便在無法使用一般系統管理帳戶時用於存取。 緊急存取帳戶通常具有高權限，不應將其指派給特定個人。 緊急存取帳戶僅限用於無法使用一般系統管理帳戶的緊急或「急用」狀況。

您應該確保緊急存取帳戶的認證 (例如密碼、憑證或智慧卡) 受到保護，而且只有在緊急情況下有權使用這些認證的個人才會知道。

- [在 Azure AD 中管理緊急存取帳戶](/azure/active-directory/users-groups-roles/directory-emergency-access)

- [保護您的 M365 帳戶](/microsoft-365/campaigns/m365-campaigns-protect-admin-accounts) (機器翻譯)

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

### <a name="pa-6-use-privileged-access-workstations"></a>PA-6：使用特殊權限存取工作站

**指引**：安全、隔離的工作站對於敏感性角色 (例如系統管理員、開發人員及重要服務操作員) 的安全性來說至關重要。 針對與管理 Power BI 相關的系統管理工作，使用高度安全的使用者工作站和/或 Azure Bastion。 請使用 Azure Active Directory、Microsoft Defender 進階威脅防護 (ATP) 和/或 Microsoft Intune，以部署安全且受控的使用者工作站來進行系統管理工作。 受保護的工作站可以集中管理以施行安全設定，包括增強式驗證、軟體和硬體基準、受限的邏輯和網路存取。

了解特殊權限存取
- [工作站](/azure/active-directory/devices/concept-azure-managed-workstation) (機器翻譯)

- [部署特殊權限存取工作站](/azure/active-directory/devices/howto-azure-managed-workstation) (機器翻譯)

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

## <a name="data-protection"></a>資料保護

如需詳細資訊，請參閱 [Azure 安全性效能評定：資料保護](/azure/security/benchmarks/security-controls-v2-data-protection)。

### <a name="dp-1-discovery-classify-and-label-sensitive-data"></a>DP-1：探索、分類及標記敏感性資料

**指引**：在報表、儀表板、資料集和資料流程上使用 Microsoft 資訊保護敏感度標籤，以保護敏感性內容，防止未經授權的資料存取和外洩。

使用 Microsoft 資訊保護敏感度標籤，可在 Power BI 服務中分類及標示您的報表、儀表板、資料集和資料流程，以及在將內容從 Power BI 服務匯出至 Excel、PowerPoint 和 PDF 檔案時，保護敏感性內容以防止未經授權的資料存取和外洩。

- [如何在 Power BI 中套用敏感度標籤](../admin/service-security-apply-data-sensitivity-labels.md)

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

### <a name="dp-2-protect-sensitive-data"></a>DP-2：保護敏感性資料

**指引**：Power BI 已與 Microsoft 資訊保護敏感度標籤整合，以提供敏感性資料保護。 如需詳細資料，請參閱 [Power BI 中的 Microsoft 資訊保護敏感度標籤](../admin/service-security-sensitivity-label-overview.md)

Power BI 可讓服務使用者攜帶自己的金鑰來保護待用資料。 如需詳細資料，請參閱[攜帶您自己的加密金鑰以用於 Power BI](../admin/service-encryption-byok.md)

客戶可以選擇將資料來源保留在內部部署環境，並運用直接查詢或 Live Connect 與內部部署的資料閘道，將資料暴露於雲端服務的風險降到最低。 如需詳細資料，請參閱[什麼是內部部署的資料閘道？](/data-integration/gateway/service-gateway-onprem)

Power BI 支援資料列層級安全性。 如需詳細資料，請參閱 [Power BI 的資料列層級安全性 (RLS)](../admin/service-admin-rls.md)。 請注意，RLS 甚至可以套用至直接查詢資料來源，在此情況下，PBIX 檔案會作為安全性啟用 Proxy。

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

### <a name="dp-3-monitor-for-unauthorized-transfer-of-sensitive-data"></a>DP-3：監視未經授權的敏感性資料傳輸

**指引**：使用適用於 Power BI 的 Microsoft Cloud App Security 支援，可以部分達成此控制項。

使用 Cloud App Security 搭配 Power BI，有利於保護 Power BI 報表、資料和服務免於遭到非預期的外洩或入侵。 利用 Cloud App Security，您可以使用 Azure Active Directory (Azure AD) 的即時工作階段控制項，針對組織的資料建立條件式存取原則，以協助確保 Power BI 分析的安全。 設定好這些原則後，系統管理員就可以監視使用者的存取和活動、執行即時風險分析，以及設定標籤特定控制項。

使用
- [Power BI 中的 Microsoft Cloud App Security 控制項](../admin/service-security-using-microsoft-cloud-app-security-controls.md)

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

### <a name="dp-4-encrypt-sensitive-information-in-transit"></a>DP-4：加密傳輸中的敏感性資訊

**指引**：對於 HTTP 流量，確保任何連線到您 Power BI 資源的用戶端和資料來源都可以交涉 TLS v1.2 或更新版本。

- [強制使用 TLS 版本](../admin/service-admin-power-bi-security.md#enforcing-tls-version-usage)

- [TLS 安全性的資訊](/security/engineering/solving-tls1-problem)

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

### <a name="dp-5-encrypt-sensitive-data-at-rest"></a>DP-5：將敏感性待用資料加密

**指引**：Power BI 會加密「待用」與「處理中」的資料。 根據預設，Power BI 會使用 Microsoft 管理的金鑰來為您加密資料。 組織可以選擇使用自己的金鑰，加密使用者在 Power BI 間待用的內容，從報表影像到 Premium 容量中的匯入資料集。

- [在 Power BI 中使用自備金鑰](../admin/service-encryption-byok.md)

**Azure 資訊安全中心監視**：不適用

**責任**：共用

## <a name="asset-management"></a>資產管理

如需詳細資訊，請參閱 [Azure 安全性效能評定：資產管理](/azure/security/benchmarks/security-controls-v2-asset-management)。

### <a name="am-1-ensure-security-team-has-visibility-into-risks-for-assets"></a>AM-1：確保安全性小組能夠看到資產的風險

**指引**：搭配您的 Power BI Office 稽核記錄使用 Azure Sentinel，以確保您的安全性小組能夠看到 Power BI 資產的風險。

- [將 Office 365 記錄連線到 Azure Sentinel](/azure/sentinel/connect-office-365) (機器翻譯)

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

### <a name="am-2-ensure-security-team-has-access-to-asset-inventory-and-metadata"></a>AM-2：確保安全性小組可以存取資產清查和中繼資料

**指引**：確保安全性小組可以存取 Power BI Embedded 資源的持續更新清查。 安全性小組通常需要進行這項清查，以評估其組織對新興風險的潛在暴露程度，並作為持續安全性改進的輸入。 

Azure Resource Graph 可以查詢及探索您訂用帳戶中的所有 Power BI Embedded 資源。  

使用標記和 Azure 中的其他中繼資料 (名稱、描述及類別)，根據組織的分類法以邏輯方式組織資產。  

- [如何使用 Azure Resource Graph Explorer 建立查詢](/azure/governance/resource-graph/first-query-portal)

- [資源命名與標記決策指南](/azure/cloud-adoption-framework/decision-guides/resource-tagging/?toc=%2fazure%2fazure-resource-manager%2fmanagement%2ftoc.json)

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

### <a name="am-3-use-only-approved-azure-services"></a>AM-3：僅使用已核准的 Azure 服務

**指引**：Power BI 支援適用於 Power BI Embedded 的 Azure Resource Manager 架構部署，而且您可以使用自訂原則定義透過 Azure 原則來限制其資源部署。

使用 Azure 原則可稽核及限制使用者能夠在環境中佈建的服務。 使用 Azure Resource Graph 則可查詢及探索其訂用帳戶內的資源。 您也可以使用 Azure 監視器來建立規則，以在偵測到未核准的服務時觸發警示。

- [如何設定和管理 Azure 原則](/azure/governance/policy/tutorials/create-and-manage)

如何使用下列項目拒絕特定資源類型
- [Azure 原則](/azure/governance/policy/samples/built-in-policies#general)

如何使用下列 Azure 項目建立查詢
- [Resource Graph 總管](/azure/governance/resource-graph/first-query-portal)

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

## <a name="logging-and-threat-detection"></a>記錄與威脅偵測

如需詳細資訊，請參閱 [Azure 安全性效能評定：記錄與威脅偵測](/azure/security/benchmarks/security-controls-v2-logging-threat-detection)。

### <a name="lt-2-enable-threat-detection-for-azure-identity-and-access-management"></a>LT-2：啟用 Azure 身分識別與存取權管理的威脅偵測

**指引**：將任何記錄從 Power BI 轉送到您的 SIEM，這可用來設定自訂威脅偵測。 此外，請在 Power BI 中使用 Microsoft Cloud App Security (MCAS) 控制項，以使用[此處](../admin/service-security-using-microsoft-cloud-app-security-controls.md)的指南來啟用異常偵測。

- [追蹤 Power BI 中的使用者活動](../admin/service-admin-auditing.md)

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

### <a name="lt-3-enable-logging-for-azure-network-activities"></a>LT-3：啟用 Azure 網路活動的記錄功能

**指引**：Power BI 是完全受控的 SaaS 供應項目，而且基礎網路設定和記錄是 Microsoft 的責任。 針對利用 Private Link 的客戶，可以設定一些記錄和監視功能。

- [Private Link 記錄和監視](/azure/private-link/private-link-overview#logging-and-monitoring)

**Azure 資訊安全中心監視**：不適用

**責任**：共用

### <a name="lt-4-enable-logging-for-azure-resources"></a>LT-4：啟用 Azure 資源的記錄功能

**指引**：透過 Power BI，您有兩個選項可用來追蹤使用者活動：Power BI 活動記錄與整合稽核記錄。 這些記錄都包含 Power BI 審核資料的完整複本，但有幾個主要差異，如以下摘要所示。
 
整合稽核記錄：

 
- 除了 Power BI 審核事件以外，還包含來自 SharePoint Online、Exchange Online、Dynamics 365 和其他服務的事件。

 
- 只有具備僅限檢視稽核記錄權限或稽核記錄權限的使用者才能存取，例如全域管理員和稽核員。

 
- 全域管理員和稽核員可使用 Microsoft 365 資訊安全中心以及 Microsoft 365 合規性中心來搜尋整合稽核記錄。

 
- 全域管理員和稽核員可以使用 Microsoft 365 管理 API 和 Cmdlet 來下載稽核記錄項目。

 
- 將審核資料保留 90 天。

 
- 即使將租用戶移至不同的 Azure 區域，仍會保留稽核資料。
 
Power BI 活動記錄：

 
- 只包含 Power BI 審核事件。

 
 
- 全域管理員和 Power BI 服務管理員可以存取。

 
- 目前沒有任何使用者介面可搜尋活動記錄。

 
- 全域管理員和 Power BI 服務管理員可以使用 Power BI REST API 和管理 Cmdlet 來下載活動記錄項目。

 
- 將活動資料保留 30 天。

 
- 將租用戶移至不同的 Azure 區域時，不會保留活動資料。

- [Power BI 稽核資料](../admin/service-admin-auditing.md#operations-available-in-the-audit-and-activity-logs)

- [Power BI 活動記錄](../admin/service-admin-auditing.md#use-the-activity-log)

- [Power BI 稽核記錄](../admin/service-admin-auditing.md#use-the-audit-log)

**Azure 資訊安全中心監視**：不適用

**責任**：共用

### <a name="lt-5-centralize-security-log-management-and-analysis"></a>LT-5：將安全性記錄的管理與分析集中

**指引**：Power BI 會將記錄集中在兩個位置：Power BI 活動記錄和整合稽核記錄。 這些記錄都包含 Power BI 審核資料的完整複本，但有幾個主要差異，如以下摘要所示。
 

整合稽核記錄：

- 除了 Power BI 審核事件以外，還包含來自 SharePoint Online、Exchange Online、Dynamics 365 和其他服務的事件。

- 只有具備僅限檢視稽核記錄權限或稽核記錄權限的使用者才能存取，例如全域管理員和稽核員。

- 全域管理員和稽核員可使用 Microsoft 365 資訊安全中心以及 Microsoft 365 合規性中心來搜尋整合稽核記錄檔。

- 全域管理員和稽核員可以使用 Microsoft 365 管理 API 和 Cmdlet 來下載稽核記錄項目。

- 將審核資料保留 90 天。

- 即使將租用戶移至不同的 Azure 區域，仍會保留稽核資料。

 

Power BI 活動記錄：

- 只包含 Power BI 審核事件。

- 全域管理員和 Power BI 服務管理員可以存取。

- 目前沒有任何使用者介面可搜尋活動記錄。

- 全域管理員和 Power BI 服務管理員可以使用 Power BI REST API 和管理 Cmdlet 來下載活動記錄項目。

- 將活動資料保留 30 天。

- 將租用戶移至不同的 Azure 區域時，不會保留活動資料。

- [Power BI 稽核資料](../admin/service-admin-auditing.md#operations-available-in-the-audit-and-activity-logs)

- [Power BI 活動記錄](../admin/service-admin-auditing.md#use-the-activity-log)

- [Power BI 稽核記錄](../admin/service-admin-auditing.md#use-the-audit-log)

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

### <a name="lt-6-configure-log-storage-retention"></a>LT-6：設定記錄儲存保留期

**指引**：根據您的合規性、法規和商務需求，為您的 Office 稽核記錄設定儲存保留原則。

- [Office 稽核記錄保留原則](/microsoft-365/compliance/audit-log-retention-policies)

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

## <a name="incident-response"></a>事件回應

如需詳細資訊，請參閱 [Azure 安全性效能評定：事件回應](/azure/security/benchmarks/security-controls-v2-incident-response)。

### <a name="ir-1-preparation--update-incident-response-process-for-azure"></a>IR-1：準備 – 更新 Azure 的事件回應流程

**指引**：確定您的組織具有回應安全性事件的流程、已更新 Azure 的這些處理序，而且會定期執行以確保就緒。

- [在企業環境中實作安全性](/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud) (機器翻譯)

- [事件回應參考指南](/microsoft-365/downloads/IR-Reference-Guide.pdf) (英文)

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

### <a name="ir-2-preparation--setup-incident-notification"></a>IR-2：準備 – 設定事件通知

**指引**：在 Azure 資訊安全中心中設定安全性事件連絡人資訊。 當 Microsoft 安全回應中心 (MSRC) 發現您的資料已遭非法或未經授權的合作對象存取時，Microsoft 會使用此連絡人資訊來與您連絡。 您也可以選擇根據事件回應需求，在不同的 Azure 服務中自訂事件警示和通知。 

- [如何設定 Azure 資訊安全中心安全性連絡人](/azure/security-center/security-center-provide-security-contact-details)

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

### <a name="ir-3-detection-and-analysis--create-incidents-based-on-high-quality-alerts"></a>IR-3：偵測與分析 – 根據高品質警示建立事件

**指引**：確定您具有建立高品質警示並測量警示品質的流程。 這可讓您從過去的事件吸取教訓，並為分析師設定警示優先順序，這樣他們就不會浪費時間在誤報上。

監視 Microsoft Cloud App Security 中與 Power BI 相關的警示。 您可以根據過去事件的經驗、已驗證的社區來源，以及設計成透過融合和相互關聯不同信號來源以產生和清除警示的工具，來建置高品質警示。

- [在 Cloud App Security 中監視警示](/cloud-app-security/monitor-alerts)

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

### <a name="ir-4-detection-and-analysis--investigate-an-incident"></a>IR-4：偵測與分析 – 調查事件

**指引**：為組織製作事件回應指南。 定期進行練習以測試系統的事件回應功能。 找出弱點和落差，並視需要修訂計畫。

請確定有書面的事件回應計畫，其中定義人員的所有角色，以及從偵測到事件後檢討的事件處理/管理階段。

- [Microsoft 威脅防護中的事件概觀](/microsoft-365/security/mtp/incidents-overview) (機器翻譯)

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

### <a name="ir-5-detection-and-analysis--prioritize-incidents"></a>IR-5：偵測與分析 – 設定事件的優先順序

**指引**：根據警示嚴重性和資產敏感度為分析師提供內容，來協助判斷要優先關注的事件。 

 
Microsoft 威脅防護會套用相互關聯分析，並將來自不同產品的所有相關警示和調查彙總成一個事件。 鑑於 Microsoft 威脅防護在整個資產和產品套件中的端對端可見度，Microsoft 威脅防護還會針對只能識別為惡意的活動觸發唯一警示。 藉由這麼做，Microsoft 威脅防護可說明更廣泛的攻擊案例，讓安全性作業分析師能夠了解並因應整個組織的複雜威脅。

- [設定 Microsoft 威脅防護中的事件優先順序](/microsoft-365/security/mtp/incident-queue?amp;preserve-view=true&view=o365-worldwide) (機器翻譯)

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

### <a name="ir-6-containment-eradication-and-recovery--automate-the-incident-handling"></a>IR-6：圍堵、根除及復原 – 將事件處理自動化

**指引**：將手動重複的工作自動化，以縮短回應時間並降低分析師的負擔。 手動工作需要較長的時間來執行，進而降低每個事件的速度，以及減少分析師可以處理的事件數目。 手動工作還會使分析師更加疲勞，這會增加造成延遲的人為錯誤風險，並降低分析師有效地專注處理複雜工作的能力。  
 
使用 Microsoft 威脅防護中的工作流程自動化功能，可自動觸發調查和補救，以回應傳入的安全性警示。 
 
- [Microsoft 威脅防護中的自動化調查和回應](/microsoft-365/security/mtp/mtp-autoir) (機器翻譯)

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

## <a name="posture-and-vulnerability-management"></a>狀況和弱點管理

如需詳細資訊，請參閱 [Azure 安全性效能評定：狀況和弱點管理](/azure/security/benchmarks/security-controls-v2-posture-vulnerability-management)。

### <a name="pv-1-establish-secure-configurations-for-azure-services"></a>PV-1：建立 Azure 服務的安全設定 

**指引**：使用適用於組織和安全性工作的設定來設定您的 Power BI 服務。 應謹慎考慮存取服務的設定、內容，以及工作區和應用程式的安全性。 請參閱 Power BI 企業部署白皮書中的 Power BI 安全性和資料保護。

- [企業部署白皮書](https://aka.ms/PBIEnterpriseDeploymentWP) (英文)

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

### <a name="pv-2-sustain-secure-configurations-for-azure-services"></a>PV-2：維持 Azure 服務的安全設定

**指引**：使用 Power BI 系統管理 REST API 來監視您的 Power BI 執行個體。

- [Power BI 系統管理 REST API](/rest/api/power-bi/admin) (英文)

- [Power BI 企業部署白皮書](https://aka.ms/PBIEnterpriseDeploymentWP)

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

### <a name="pv-8-conduct-regular-attack-simulation"></a>PV-8：執行一般攻擊模擬

**指引**：如有需要，請對您的 Azure 資源執行滲透測試或紅隊活動，並確保補救所有重要的安全性結果。

請遵循 Microsoft 雲端滲透測試參與規則，以確保您的滲透測試不會違反 Microsoft 原則。 針對 Microsoft 管理的雲端基礎結構、服務和應用程式，使用 Microsoft 對於紅隊和即時網站滲透測試的策略和執行方法。

- [Azure 中的滲透測試](/azure/security/fundamentals/pen-testing) (機器翻譯)

- [滲透測試運作規則](https://www.microsoft.com/msrc/pentest-rules-of-engagement?rtc=1)

- [Microsoft Cloud Red Teaming](https://gallery.technet.microsoft.com/Cloud-Red-Teaming-b837392e)

**Azure 資訊安全中心監視**：不適用

**責任**：共用

## <a name="backup-and-recovery"></a>備份及修復

如需詳細資訊，請參閱 [Azure 安全性效能評定：備份和復原](/azure/security/benchmarks/security-controls-v2-backup-recovery)。

### <a name="br-3-validate-all-backups-including-customer-managed-keys"></a>BR-3：驗證所有備份，包括客戶自控金鑰

**指引**：如果您使用 Power BI 中的自備金鑰 (BYOK) 功能，則需要定期驗證您是否可以存取和還原客戶自控金鑰。

- [Power BI 中的 BYOK](../admin/service-encryption-byok.md)

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

### <a name="br-4-mitigate-risk-of-lost-keys"></a>BR-4：降低遺失金鑰的風險

**指引**：如果您使用 Power BI 中的自備金鑰 (BYOK) 功能，則必須確定已使用下列 Power BI 文件中的 BYOK 指引設定控制客戶自控金鑰的 Key Vault。 請啟用 Azure Key Vault 中的虛刪除和清除保護，以防止金鑰遭到意外或惡意刪除。

- [Power BI 中的 BYOK](../admin/service-encryption-byok.md)

- [如何在 Key Vault 中啟用虛刪除和清除保護](/azure/storage/blobs/storage-blob-soft-delete?tabs=azure-portal) (機器翻譯)

若為閘道金鑰資源，請確保您遵循下列閘道修復金鑰文件中的指引。

- [內部部署的資料閘道修復金鑰](/data-integration/gateway/service-gateway-recovery-key)

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

## <a name="governance-and-strategy"></a>控管與策略

如需詳細資訊，請參閱 [Azure 安全性效能評定：治理和策略](/azure/security/benchmarks/security-controls-v2-governance-strategy)。

### <a name="gs-1-define-asset-management-and-data-protection-strategy"></a>GS-1：定義資產管理和資料保護策略 

**指引**：務必記載並傳達明確的策略，以持續監視及保護系統和資料。 請優先探索、評估、保護及監視業務關鍵資料和系統。 

此策略應該包含下列項目的已記載指引、原則和標準： 

-   符合商業風險的資料分類標準

-   安全性組織對風險和資產清查的可見度 

-   安全性組織核准 Azure 服務以供使用的程序 

-   資產在其生命週期中的安全性

-   符合組織資料分類的必要存取控制策略

-   使用 Azure 原生和協力廠商資料保護功能

-   傳輸中和待用使用案例的資料加密需求

-   適當的密碼編譯標準

如需詳細資訊，請參閱下列參考資料：
- [Azure 安全性架構建議 - 儲存體、資料和加密](/azure/architecture/framework/security/storage-data-encryption?amp;bc=%2fsecurity%2fcompass%2fbreadcrumb%2ftoc.json&toc=%2fsecurity%2fcompass%2ftoc.json) (機器翻譯)

- [Azure 安全性基礎觀念 - Azure 資料安全性、加密和儲存體](/azure/security/fundamentals/encryption-overview) (機器翻譯)

- [雲端採用架構 - Azure 資料安全性和加密最佳做法](/azure/security/fundamentals/data-encryption-best-practices?amp;bc=%2fazure%2fcloud-adoption-framework%2f_bread%2ftoc.json&toc=%2fazure%2fcloud-adoption-framework%2ftoc.json) (機器翻譯)

- [Azure 安全性效能評定 - 資產管理](/azure/security/benchmarks/security-controls-v2-asset-management)

- [Azure 安全性效能評定 - 資料保護](/azure/security/benchmarks/security-controls-v2-data-protection)

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

### <a name="gs-2-define-enterprise-segmentation-strategy"></a>GS-2：定義企業分割策略 

**指引**：使用身分識別、網路、應用程式、訂用帳戶、管理群組和其他控制項的組合，建立企業範圍的策略來分割對產的存取。

審慎權衡安全性區隔的需求，以及需要與彼此通訊並存取資料的啟用每日作業需求。

確保在各種控制項類型上一致地實作分割策略，這些控制項類型包括網路安全性、身分識別和存取模型，以及應用程式權限/存取模型與人力流程控制。

- [Azure 中的分割策略指引 (影片)](/security/compass/microsoft-security-compass-introduction#azure-components-and-reference-model-2151) (機器翻譯)

- [Azure 中的分割策略指引 (文件)](/security/compass/governance#enterprise-segmentation-strategy) (機器翻譯)

- [使用企業分割策略來調整網路分割](/security/compass/network-security-containment#align-network-segmentation-with-enterprise-segmentation-strategy) (機器翻譯)

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

### <a name="gs-3-define-security-posture-management-strategy"></a>GS-3：定義安全性狀態管理策略

**指引**：持續測量並降低個別資產及其裝載環境的風險。 優先處理高價值資產和高度公開的攻擊面，例如已發佈的應用程式、網路輸入和輸出點、使用者和系統管理員端點等等。

- [Azure 安全性效能評定 - 狀態和弱點管理](/azure/security/benchmarks/security-controls-v2-posture-vulnerability-management)

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

### <a name="gs-4-align-organization-roles-responsibilities-and-accountabilities"></a>GS-4：協調組織角色、責任及權責

**指引**：務必為安全性組織中的角色和責任記載並傳達清楚的策略。 優先為安全性決策提供清楚的權責、讓每個人熟知共同責任模型，並讓技術團隊熟知保護雲端的技術。

- [Azure 安全性最佳做法 1 – 人員：讓小組熟知雲端安全性旅程](/azure/cloud-adoption-framework/security/security-top-10#1-people-educate-teams-about-the-cloud-security-journey) (機器翻譯)

- [Azure 安全性最佳做法 2 - 人員：讓小組熟知雲端安全性技術](/azure/cloud-adoption-framework/security/security-top-10#2-people-educate-teams-on-cloud-security-technology) (機器翻譯)

- [Azure 安全性最佳做法 3 - 流程：指派雲端安全性決策的權責](/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud) (機器翻譯)

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

### <a name="gs-5-define-network-security-strategy"></a>GS-5：定義網路安全性策略

**指引**：建立 Azure 網路安全性方法，作為組織整體安全性存取控制策略的一部分。  

此策略應該包含下列項目的已記載指引、原則和標準： 

-   集中式網路管理和安全性責任

-   與企業分割策略一致的虛擬網路分割模型

-   不同威脅和攻擊案例的補救策略

-   網際網路邊緣和輸入與輸出策略

-   混合式雲端和內部部署互連能力策略

-   最新的網路安全性成品 (例如網路圖、參考網路架構)

如需詳細資訊，請參閱下列參考資料：
- [Azure 安全性最佳做法 11 - 架構。單一整合的安全性策略](/azure/cloud-adoption-framework/security/security-top-10#11-architecture-establish-a-single-unified-security-strategy) (機器翻譯)

- [Azure 安全性效能評定 - 網路安全性](/azure/security/benchmarks/security-controls-v2-network-security)

- [Azure 網路安全性概觀](/azure/security/fundamentals/network-overview)

- [企業網路架構策略](/azure/cloud-adoption-framework/ready/enterprise-scale/architecture) (機器翻譯)

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

### <a name="gs-6-define-identity-and-privileged-access-strategy"></a>GS-6：定義身分識別和特殊權限存取策略

**指引**：建立 Azure 身分識別和特殊權限存取方法，作為組織整體安全性存取控制策略的一部分。  

此策略應該包含下列項目的已記載指引、原則和標準： 

-   集中式身分識別和驗證系統，以及其與其他內部和外部身分識別系統的互連能力

-   不同使用案例和條件中的增強式驗證方法

-   高權限使用者的保護

-   異常使用者活動監視和處理  

-   使用者身分識別、存取權檢閱與核對流程

如需詳細資訊，請參閱下列參考資料：

- [Azure 安全性效能評定 - 身分識別管理](/azure/security/benchmarks/security-controls-v2-identity-management)

- [Azure 安全性效能評定 - 特殊權限存取](/azure/security/benchmarks/security-controls-v2-privileged-access)

- [Azure 安全性最佳做法 11 - 架構。單一整合的安全性策略](/azure/cloud-adoption-framework/security/security-top-10#11-architecture-establish-a-single-unified-security-strategy) (機器翻譯)

- [Azure 身分識別管理安全性概觀](/azure/security/fundamentals/identity-management-overview)

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

### <a name="gs-7-define-logging-and-threat-response-strategy"></a>GS-7：定義記錄和威脅回應策略

**指引**：建立記錄和威脅回應策略，以快速偵測威脅並進行補救，同時符合合規性需求。 優先為分析師提供高品質警示和順暢體驗，讓他們能夠專注處理威脅，而非整合和手動步驟。 

此策略應該包含下列項目的已記載指引、原則和標準： 

-   安全性作業 (SecOps) 組織的角色和責任 

-   妥善定義且與 NIST 或其他產業架構一致的事件回應流程 

-   記錄擷取和保留，以支援威脅偵測、事件回應及合規性需求

-   使用 SIEM、原生 Azure 功能及其他來源，集中顯示及相互關聯威脅的相關資訊 

-   與客戶、供應商和相關公開合作對象之間的溝通和通知計畫

-   使用 Azure 原生和協力廠商平台進行事件處理，例如記錄和威脅偵測、鑑定，以及攻擊補救和根除

-   處理事件和事件後活動的流程，例如吸取的經驗和證據保留

如需詳細資訊，請參閱下列參考資料：

- [Azure 安全性效能評定 - 記錄與威脅偵測](/azure/security/benchmarks/security-controls-v2-logging-threat-detection)

- [Azure 安全性效能評定 - 事件回應](/azure/security/benchmarks/security-controls-v2-incident-response)

- [Azure 安全性最佳做法 4 - 流程。更新雲端的事件回應流程](/azure/cloud-adoption-framework/security/security-top-10#4-process-update-incident-response-ir-processes-for-cloud) (機器翻譯)

- [Azure 採用架構、記錄與報告決策指南](/azure/cloud-adoption-framework/decision-guides/logging-and-reporting/)

- [Azure 企業規模、管理與監視](/azure/cloud-adoption-framework/ready/enterprise-scale/management-and-monitoring) (機器翻譯)

**Azure 資訊安全中心監視**：不適用

**責任**：客戶

## <a name="next-steps"></a>後續步驟

- 請參閱 [Azure 安全性效能評定 V2 概觀](/azure/security/benchmarks/overview)
- 深入了解 [Azure 資訊安全性基準](/azure/security/benchmarks/security-baselines-overview)