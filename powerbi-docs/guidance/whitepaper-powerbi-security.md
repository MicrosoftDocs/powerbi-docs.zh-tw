---
title: Power BI 安全性技術白皮書
description: 本白皮書將討論並描述 Power BI 的安全性架構和執行
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 02/11/2021
LocalizationGroup: Conceptual
ms.openlocfilehash: 655fde0ef19c15f368cb2219498bb26d4411d5d3
ms.sourcegitcommit: fb408dfd39943dbec990a16bcf204671beb4f0aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/18/2021
ms.locfileid: "100655676"
---
# <a name="power-bi-security-white-paper"></a>Power BI 安全性技術白皮書

**摘要：** Power BI 是 Microsoft 提供的線上軟體服務 (*SaaS* 或軟體即服務) 供應專案，可讓您輕鬆快速地建立自助商業智慧儀表板、報表、資料集和視覺效果。 使用 Power BI，您可以連線到許多不同的資料來源、結合與塑造來自這些連線的資料，然後建立與其他人共用的報表和儀表板。

**寫入器：** Yitzhak Kesselman、Paddy Osborne、Matt Neely、Tony Bencic、Srinivasan Turuvekere、Cristian Petculescu、Adi Regev、Naveen Sivaraj、Ben Glastein、Evgeny Tshiorny、Arthi Ramasubramanian Iyer、Sid Jayadevan、Ronald Chang、Ori Eduar、Anton Fritz、Idan Sheinberg、Ron Gilad、Sagiv Hadaya、Paul Inbar、Igor Uzhviev、Michael Roth、Jaime Tarquino、Gennady pat、Orion Yury、Berezansky Maya、Shenhav Romit、Chattopadhyay Yariv、Maimon Bogdan、crivat 著

**技術審核者：** Cristian Petculescu、Amir Netz、Sergei Gundorov

**適用于：** Power BI SaaS、Power BI Desktop、Power BI Premium、Power BI Embedded 分析、Power BI 行動版

> [!NOTE]
> 您可以從瀏覽器中選取 [ **列印** ]，然後選取 [ **另存為 PDF**]，來儲存或列印此白皮書。

## <a name="introduction"></a>簡介

Power BI 是 Microsoft 提供的線上軟體服務 (稱為 *SaaS* 或軟體即服務)，讓您輕鬆快速地建立自助商業智慧儀表板、報表、資料集和視覺效果。 使用 Power BI，您可以連線到許多不同的資料來源、結合與塑造來自這些連線的資料，然後建立與其他人共用的報表和儀表板。

世界迅速改變了;組織正在進行加速的數位轉型，我們發現遠端工作的成長大幅增加、客戶對線上服務的需求增加，以及在營運和業務決策方面增加了先進技術的使用。 而且這一切都是由雲端提供技術支援。

當轉換至雲端時，從 trickle 變更為大量，並以其所附的新公開介面區，越來越多的公司會詢問 *我的資料在雲端中的安全性如何？* 以及有 *哪些端對端保護可用來防止機密資料洩漏？* 對於通常會在企業中處理某些最策略性資訊的 BI 平臺，這些問題都是雙重重要的。

數十年來，BI 安全性模型的基本基礎-物件層級和資料列層級安全性，但仍很重要，因此顯然不再足夠提供雲端時代所需的安全性類型。 相反地，組織必須尋找其商業智慧資料的雲端原生、多層式深度防禦安全性解決方案。

Power BI 的設計，可為數據提供領先業界的完整和 hermetic 保護。 產品已獲得業界最高的安全性分類，現今許多國家安全機關、金融機構以及醫療保健提供者 entrust 其最機密資訊。

一切都是從基礎開始。 在提早2000s 期間，Microsoft 進行了大規模的投資以解決其安全性弱點，而在下列數十年中，我們建立了非常強大的安全性堆疊，與機器晶片內部的 bios 核心相同，並延伸至使用者體驗。 這些深度投資會持續，而今日超過3500的 Microsoft 工程師會參與建立和強化 Microsoft 的安全性堆疊，並主動解決不斷變動的威脅範圍。 有了數十億部電腦、數兆個的登入，以及無數 zettabytes 的資訊，以獲得 Microsoft 的保護，公司現在在技術產業中擁有最先進的安全性堆疊，並且廣泛地視為對抗惡意執行者的全球領導者。

Power BI 是以這個非常強大的基礎為基礎。 它會使用向 Azure 提供的相同安全性堆疊來提供和保護全球最敏感的資料，並與 Microsoft 365 的最先進資訊保護和相容性工具整合。 在這些上，它會透過多層式安全性措施提供安全性，進而產生端對端的保護，以處理雲端時代的獨特挑戰。

為了提供可保護機密資產的端對端解決方案，產品小組需要針對多個同時進行的客戶解決問題：
* *如何控制誰可以連線、連接的來源，以及它們的連線方式？* *如何控制連接？*
* *如何儲存資料？* *加密方式為何？* *我的資料有哪些控制項？*
* *如何? 控制及保護我的機密資料？* *如何? 確保此資料不會在組織外部洩漏？*
* *如何? audit 誰進行了哪些作業？* *如果服務上有可疑的活動，如何? 會快速反應嗎？*

本文提供上述所有問題的完整解答。 它一開始會概述服務架構，並說明系統中的主要流程如何運作。 接著，它會繼續描述使用者如何向 Power BI 進行驗證、如何建立資料連線，以及 Power BI 如何透過服務儲存和移動資料。 最後一節討論的安全性功能，可讓您以服務系統管理員身分保護您最寶貴的資產。

Power BI 服務受 [Microsoft Online Services 條款](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=31)和 [Microsoft 隱私權聲明](https://www.microsoft.com/privacystatement/OnlineServices/Default.aspx)制約管轄。 如需資料處理的位置，請參閱 [Microsoft Online Services 條款](http://www.microsoftvolumelicensing.com/Downloader.aspx?DocumentId=9555) 中的資料處理詞彙位置，以及 [資料保護](https://www.microsoft.com/download/details.aspx?id=101581)增補。 [Microsoft 信任中心](https://www.microsoft.com/trustcenter)是 Power BI 有關合規性資訊的主要資源。 Power BI 小組致力於為客戶創造最新的創新和生產力。 深入瞭解 [Microsoft 合規性供應](/compliance/regulatory/offering-home)專案的合規性。

Power BI 服務遵循安全性開發生命週期 (SDL) ，這是支援安全性保證和合規性需求的嚴格安全性作法。 SDL 可協助開發人員藉由減少軟體弱點的數量和嚴重性來建立更安全的軟體，同時降低開發成本。 深入瞭解 [Microsoft 安全性開發週期實務](https://www.microsoft.com/securityengineering/sdl/practices)。

## <a name="power-bi-architecture"></a>Power BI 架構

Power BI 服務是以 Azure 為基礎，這是 Microsoft 的 [雲端運算平臺](https://azure.microsoft.com/overview/what-is-azure/)。 Power BI 目前部署在世界各地的許多資料中心，向這些資料中心服務的客戶提供許多主動部署，以及作為每個主動部署備份使用之同等數目的被動部署。

![WFE 和後端](media/whitepaper-powerbi-security/powerbi-security-whitepaper_01.png)

### <a name="web-front-end-cluster-wfe"></a>Web 前端叢集 (WFE) 

WFE 叢集會為使用者的瀏覽器提供網站負載的初始 HTML 網頁內容，以及管理 Power BI 的初始連接和驗證程式、使用 Azure Active Directory (Azure AD) 來驗證用戶端，以及提供權杖，供後續用戶端連線至 Power BI 後端服務。

![WFE 叢集](media/whitepaper-powerbi-security/powerbi-security-whitepaper_02.png)

WFE 叢集是由在 [Azure App Service 環境](/azure/app-service/environment/intro)中執行的 ASP.NET 網站所組成。 當使用者嘗試連線到 Power BI 服務時，用戶端的 DNS 服務可能會與 Azure 流量管理員進行通訊，以找出最適當的 (通常最接近 Power BI 部署) datacenter。 如需此程式的詳細資訊，請參閱 [Azure 流量管理員的效能流量路由方法](/azure/traffic-manager/traffic-manager-routing-methods#performance-traffic-routing-method)。

指派給使用者的 WFE 叢集會管理登入和驗證順序 (本文稍後所述) 並在驗證成功後取得 Azure AD 存取權杖。 WFE 叢集中的 ASP.NET 元件會剖析權杖，以判斷使用者所屬的組織，然後查閱 Power BI 的全域服務。 WFE 會對瀏覽器指定要裝載組織租使用者的後端叢集。 使用者通過驗證後，客戶資料的後續用戶端互動就會直接與後端或高階叢集進行互動，而不需要 WFE 成為這些要求的 intermediator。

靜態資源（例如 **.js*、**.css* 和影像檔）大多儲存在 Azure 的內容傳遞網路上， (CDN) 並直接由瀏覽器取出。 請注意，主權政府叢集部署是此規則的例外狀況，而且基於合規性理由，將會略過 CDN，並改為使用來自符合規範區域的 WFE 叢集來裝載靜態內容。

### <a name="power-bi-back-end-cluster-be"></a>Power BI 後端叢集 () 

後端叢集是 Power BI 中所有可用功能的骨幹。 它包含數個由 Web 前端和 API 用戶端取用的服務端點，以及背景工作服務、資料庫、快取和其他各種元件。

後端可在大部分的 Azure 區域中使用，並在新的區域中部署。 單一 Azure 區域會裝載一或多個後端叢集，以在單一叢集的垂直和水準調整限制用盡時，允許無限制的 Power BI 服務水準調整。

每個後端叢集都可設定狀態，並裝載所有指派給該叢集的租使用者的所有資料。 包含特定租使用者之資料的叢集，稱為租使用者的主叢集中。 經過驗證的使用者的主要叢集資訊是由全域服務所提供，且由 Web 前端用來將要求路由傳送至租使用者的家用叢集。

每個後端叢集都是由多個虛擬機器所組成，並結合到多個調整規模的調整集來執行特定工作、可設定狀態的資源，例如 SQL 資料庫、儲存體帳戶、服務匯流排、快取，以及其他必要的雲端元件。

租使用者中繼資料和資料會儲存在叢集限制內，但在相同 Azure 地理位置的配對 Azure 區域中，將資料複寫到次要後端叢集。 次要後端叢集可做為容錯移轉叢集，以防發生區域中斷，而且在任何時候都是被動的。

除了可從公用網際網路存取的兩個元件之外，在叢集虛擬網路內的不同電腦上執行的微服務可提供後端功能。
* 閘道器服務
* Azure API 管理

![後端叢集](media/whitepaper-powerbi-security/powerbi-security-whitepaper_03.png)

### <a name="power-bi-premium-infrastructure"></a>Power BI Premium 基礎結構

Power BI Premium 為需要 Premium Power BI 功能（例如資料流程、編頁報表、AI 等）的訂閱者提供服務。當客戶註冊 Power BI Premium 訂用帳戶時，就會透過 Azure Resource Manager 建立 Premium 容量。

Power BI Premium 容量是裝載在與一般 Power BI 後端無關的後端叢集中，請參閱上述) 。 這可提供更佳的隔離、資源配置、可支援性、安全性隔離，以及 Premium 供應專案的擴充性。

下圖說明 Power BI Premium 基礎結構的架構：

![Power BI Premium](media/whitepaper-powerbi-security/powerbi-security-whitepaper_05.png)

Power BI Premium 基礎結構的連線可以透過數種方式來完成，視使用者案例而定。 Power BI Premium 用戶端可以是使用者的瀏覽器、一般 Power BI 後端、透過 XMLA 用戶端的直接連線、ARM Api 等等。

Azure 區域中的 Power BI Premium 基礎結構包含多個 Power BI Premium 叢集 (最小值為一個) 。 大部分的高階資源都會封裝在叢集內 (例如，計算) ，而且有一些常見的區域資源 (例如中繼資料儲存) 。 Premium 基礎結構可讓您透過兩種方式達到區域中的水準擴充性：在叢集內增加資源，以及（或）視需要新增更多的叢集 (如果叢集資源已接近) 的限制。

每個叢集的骨幹都是 [虛擬機器擴展集 ](/azure/virtual-machine-scale-sets/overview) 所管理的計算資源 (VMSS) 和 [Azure Service Fabric](/azure/service-fabric/service-fabric-overview)。 VMSS 和 Service Fabric 可在使用量增加時快速且輕鬆地增加計算節點，並協調 Power BI Premium 服務和應用程式的部署、管理和監視。

有許多資源可確保安全可靠的基礎結構：負載平衡器、虛擬網路、網路安全性群組、服務匯流排、儲存體等等。Power BI Premium 所需的任何秘密、金鑰和憑證都是以獨佔方式 [Azure Key Vault](/azure/key-vault/general/basic-concepts) 管理。 任何驗證都是透過與 Azure AD 的獨立整合來完成。

任何 Power BI Premium 基礎結構的要求都會先移至前端節點，這些都是外部連線唯一可用的節點。 其餘的資源會隱藏在虛擬網路後方。 前端節點會驗證要求、處理要求，或將它轉送至適當的資源 (例如，後端節點) 。

後端節點提供大部分的 Power BI Premium 功能和功能。

### <a name="power-bi-mobile"></a>Power BI 行動版

Power BI 行動版是專為三個主要行動平臺設計的應用程式集合： Android、iOS 和 Windows (UWP) 。 Power BI 行動版應用程式的安全性考慮可分為兩種類別：
* 裝置通訊
* 裝置上的應用程式和資料

針對裝置通訊，所有 Power BI 行動版的應用程式都會與 Power BI 服務通訊，並使用瀏覽器所使用的相同連線和驗證順序，如本白皮書稍早的詳細說明。 適用于 iOS 和 Android 的 Power BI 行動裝置應用程式會在應用程式本身內出現瀏覽器會話，而 Windows mobile 應用程式則會帶出訊息代理程式來建立與登入程式) Power BI (的通道。

下表根據行動裝置平臺，顯示以憑證為基礎的驗證 (CBA) 支援 Power BI 行動版：


|CBA 支援  |iOS  |Android  |Windows  |
|---------|---------|---------|---------|
|Power BI (登入服務)    |支援         |支援         |不支援         |
|SSRS ADFS 內部內部部署 (連接到 SSRS 伺服器)      |不支援         |支援         |不支援         |
|SSRS 應用程式 Proxy     |支援         |支援         |不支援         |

Power BI 行動版應用程式會主動與 Power BI 服務通訊。 遙測用於收集行動應用程式使用量統計資料和類似資料，這些資料會傳輸至用來監視使用量和活動的服務;不會使用遙測傳送任何客戶資料。

Power BI 的應用程式會將資料儲存在可協助使用應用程式的裝置上：
* 使用業界標準的安全性措施，Azure AD 和重新整理權杖儲存在裝置上的安全機制中。
* 使用者設定)  (機碼值組的資料和設定會快取在裝置上的儲存體中，而且可以由作業系統加密。 在 iOS 中，這會在使用者設定密碼時自動完成。 在 Android 中，您可以在設定中設定。 在 Windows 中，它是使用 BitLocker 完成的。
* 針對 Android 和 iOS 應用程式，系統會將使用者設定)  (機碼值組的資料和設定快取到沙箱和內部儲存體（僅供應用程式存取）中的裝置上的儲存體。 針對 Windows 應用程式，只有使用者 (和系統管理員) 可以存取資料。
* 使用者會明確啟用或停用地理位置。 如果啟用，地理位置資料就不會儲存在裝置上，也不會與 Microsoft 共用。
* 使用者會明確啟用或停用通知。 啟用時，Android 和 iOS 不支援通知的地理資料落地需求。

藉由透過 Microsoft Intune （提供行動裝置和應用程式管理的軟體服務）套用檔案層級加密，可以增強資料加密。 有 Power BI 行動版的三個平臺都支援 Intune。 啟用和設定 Intune 後，將會加密行動裝置上的資料，且 Power BI 應用程式本身不能安裝在 SD 卡上。 [深入瞭解 Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune)。

Windows 應用程式也支援 [Windows 資訊保護 (WIP) ](/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip)。

為了執行 SSO，某些與權杖型驗證相關的安全儲存體值適用于其他 Microsoft 第一方應用程式 (例如 Microsoft Authenticator) ，並由 Azure Active Directory Authentication Library (ADAL) SDK 來管理。  

Power BI 行動版快取的資料會在移除應用程式、使用者登出 Power BI 行動版，或使用者無法登入 (（例如權杖到期事件或密碼變更) 之後）時刪除。 資料快取包括先前從 Power BI 行動版應用程式存取的儀表板和報表。

Power BI 行動版不會存取裝置上的其他應用程式資料夾或檔案。

適用于 iOS 和 Android 的 Power BI 應用程式可讓您藉由設定其他識別來保護資料，例如提供臉部識別碼、觸控識別碼或 iOS 密碼，以及適用于 Android 的生物特徵辨識資料 (指紋識別碼) 。 [深入瞭解其他識別](../consumer/mobile/mobile-native-secure-access.md)。

## <a name="authentication-to-the-power-bi-service"></a>Power BI 服務的驗證

Power BI 服務的使用者驗證包含一系列的要求、回應，並在使用者的瀏覽器和 Power BI 服務或 Power BI 所使用的 Azure 服務之間重新導向。 該順序說明 Power BI 中的使用者驗證程式，其遵循 [Azure Active Directory 的驗證碼授與流程](/azure/active-directory/develop/v2-oauth2-auth-code-flow)。 如需組織的使用者驗證模型選項 (登入模型) 的詳細資訊，請參閱 [選擇 Microsoft 365 的登入模型](https://www.microsoft.com/en-us/microsoft-365/blog/2014/05/13/choosing-a-sign-in-model-for-office-365/)。

### <a name="authentication-sequence"></a>驗證順序

Power BI 服務的使用者驗證順序會如下列步驟所述，如下列步驟所述，如下圖所示。

1. 使用者可以從瀏覽器起始與 Power BI 服務的連線，方法是在網址列中輸入 Power BI 位址，或從 Power BI 登陸頁面 (選取 [登 *入* ] https://powerbi.microsoft.com) 。 連線是使用 TLS 1.2 和 HTTPS 來建立，而瀏覽器和 Power BI 服務之間所有後續的通訊則使用 HTTPS。

1. Azure 流量管理員會檢查使用者的 DNS 記錄，以判斷最適當的 (通常最接近) 部署 Power BI 的資料中心，並使用應傳送給使用者之 WFE 叢集的 IP 位址來回應 DNS。

1. WFE 接著會將使用者重新導向至 Microsoft Online Services 登入頁面。

1. 在使用者經過驗證之後，登入頁面會將使用者重新導向至先前以驗證碼判斷的最接近 Power BI 服務 WFE 叢集。

1. WFE 叢集會使用驗證碼來檢查 Azure AD 服務，以取得 Azure AD 安全性權杖。 當 Azure AD 傳回成功的使用者驗證並傳回 Azure AD 安全性權杖時，WFE 叢集會查閱 Power BI 全域服務，此服務會維護一份租使用者及其 Power BI 後端叢集位置的清單，並判斷哪一個 Power BI 後端服務叢集包含使用者的租使用者。 WFE 叢集接著會將應用程式頁面傳回給使用者的瀏覽器，其中包含其作業所需的會話、存取和路由資訊。

1. 現在，當用戶端的瀏覽器需要客戶資料時，它會使用授權標頭中的 Azure AD 存取權杖將要求傳送至後端叢集位址。 Power BI 後端叢集會讀取 Azure AD 存取權杖並驗證簽章，以確定要求的身分識別是有效的。 [Azure AD 存取權杖的預設存留期為1小時](/azure/active-directory/develop/active-directory-configurable-token-lifetimes#configurable-token-lifetime-properties-after-the-retirement)，而若要維護目前的會話，使用者的瀏覽器會定期要求更新存取權杖，然後才會到期。

![驗證順序](media/whitepaper-powerbi-security/powerbi-security-whitepaper_08.png)

## <a name="data-residency"></a>資料存留處

除非檔中另有說明，否則 Power BI 會將客戶資料儲存在 Azure 地理位置（當 [Azure AD 租](/office365/enterprise/subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings) 使用者第一次註冊 Power BI 服務時所指派）。 Azure AD 租使用者會裝載使用者和應用程式的身分識別、群組，以及與組織及其安全性相關的其他相關資訊。 

將選取作為 Azure AD 租使用者設定一部分的國家或地區，對應至 Power BI 部署所在的最適合 Azure 地理位置，即可為租使用者資料儲存體指派 Azure 地理位置。 進行這項判斷之後，所有 Power BI 客戶資料都會儲存在此選取的 Azure 地理位置 (也稱為「主要 *地區* 」) ，除非組織使用多地理位置部署。

### <a name="multiple-geographies-multi-geo"></a>多地理位置 (多地理位置) 

某些組織有全球存在，而且可能需要在多個 Azure 地理位置 Power BI 服務。 例如，企業可能會在美國總部擁有總公司，但也可能在其他地理區域（例如澳大利亞）中進行業務。 在這種情況下，企業可能會要求某些 Power BI 資料仍會保留在遠端區域中的待用部分，以符合當地法規。 Power BI 服務的這項功能稱為 *多地理* 位置。

系統會託管指派給多地理位置工作區的查詢執行層、查詢快取和成品資料，並保留在 Azure 地理位置的遠端容量中。 不過，某些成品中繼資料（例如報表結構）可能會保留在租使用者的主要地理位置中。 此外，即使是裝載在多地理區域 Premium 容量中的工作區，某些資料傳輸和處理仍可能會發生在租使用者的家庭地理位置中。

如需有關建立和管理跨多個 Azure 地理位置的 Power BI 部署的詳細資訊，請參閱 [設定 Power BI Premium 的多地理位置支援](../admin/service-admin-premium-multi-geo.md) 。

### <a name="regions-and-datacenters"></a>區域和資料中心

Power BI 服務可在特定 Azure 地理位置中使用，如 [Microsoft 信任中心](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location)所述。 如需資料的儲存位置和使用方式的詳細資訊，請參閱 [Microsoft 信任中心](https://www.microsoft.com/TrustCenter/Transparency/default.aspx#_You_know_where)。 關於待用客戶資料位置的承諾會以 [Microsoft Online Services 條款](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=31)的資料處理條款來指定。

Microsoft 也提供主權實體的資料中心。 如需國家/地區雲端的 Power BI 服務可用性詳細資訊，請參閱 [Power BI 國家/地區雲端](https://powerbi.microsoft.com/clouds/)。 

## <a name="data-handling"></a>資料處理

本節將概述儲存、處理和傳輸客戶資料時 Power BI 資料處理做法。

### <a name="data-at-rest"></a>待用資料

Power BI 會使用兩種主要資料儲存體資源類型：
* Azure 儲存體
* Azure SQL Database

在大部分的案例中，會使用 Azure 儲存體來保存 Power BI 成品的資料，而 Azure SQL database 會用來保存成品中繼資料。 

依預設，會使用 Microsoft 管理的金鑰來加密 Power BI 保存的所有資料。 Azure SQL database 中儲存的客戶資料會使用 [AZURE sql 的透明資料加密 (TDE) ](/azure/sql-database/transparent-data-encryption-azure-sql) 技術進行完整加密。 Azure Blob 儲存體中儲存的客戶資料會使用 [Azure 儲存體加密](/azure/storage/common/storage-service-encryption)來加密。

組織可以選擇性地利用 Power BI Premium 使用自己的金鑰來加密匯入資料集的待用資料。 這種方法通常稱為攜帶您自己的金鑰 (BYOK)。 利用 BYOK 有助於確保即使在服務操作員發生錯誤的情況下，也不會公開客戶資料，因為使用透明的服務端加密無法輕易達成此目的。 如需詳細資訊，請參閱 [攜帶您自己的加密金鑰以取得 Power BI](../admin/service-encryption-byok.md) 。

Power BI 資料集允許各種不同的資料來源連接模式，以判斷資料來源資料是否保存在服務中。

|資料集模式 (種類)    |保存在 Power BI 中的資料 |
|----------------------|---------------------------|
|匯入                |Yes |
|直接查詢          |No |
|Live connect          |No |
|複合             |如果包含匯入資料來源 |
|串流             |如果設定為保存 |

無論使用的資料集模式為何，Power BI 可能會暫時快取任何抓取的資料，以將查詢和報告載入效能優化。

### <a name="data-in-processing"></a>處理中的資料

當有一或多個使用者在互動式案例中主動使用資料，或背景進程（例如重新整理）觸及此資料時，資料正在進行處理。 Power BI 將主動處理的資料載入一或多個服務工作負載的記憶體空間中。 為了加速工作負載所需的功能，記憶體中處理的資料不會加密。

### <a name="data-in-transit"></a>資料傳輸中
Power BI 需要使用 TLS 1.2 或更高版本來加密所有傳入的 HTTP 流量。 任何嘗試使用具有 TLS 1.1 或更低版本之服務的要求都會遭到拒絕。

## <a name="authentication-to-data-sources"></a>對資料來源的驗證

連接至資料來源時，使用者可以選擇將資料的複本匯入 Power BI 或直接連接到資料來源。 

在匯入的案例中，使用者會根據使用者的登入建立連線，並使用認證來存取資料。 將資料集發佈至 Power BI 服務之後，Power BI 一律會使用此使用者的認證來匯入資料。 匯入資料之後，在報表和儀表板中查看資料並不會存取基礎資料來源。 Power BI 針對選取的資料來源支援單一登入驗證。 如果連接已設定為使用單一登入，則會使用資料集擁有者的認證來連接到資料來源。

如果資料來源是使用預先設定的認證直接連接，則在任何使用者流覽資料時，會使用預先設定的認證來連接到資料來源。 如果資料來源是使用單一登入直接連接，當使用者流覽資料時，就會使用目前使用者的認證來連接到資料來源。 搭配單一登入使用時，可以在資料來源上執行資料列層級安全性 (RLS) 。 這可讓使用者只看到他們有權存取的資料。 當連線到雲端中的資料來源時，會使用 Azure AD authentication 進行單一登入;針對內部內部部署資料來源，支援 Kerberos、安全性聲明標記語言 (SAML) 和 Azure AD。

如果資料來源是 Azure Analysis Services 或內部部署 Analysis Services，而且已設定 RLS，則 Power BI 服務會套用該資料列層級安全性，而沒有足夠認證的使用者可以存取基礎資料 (這可能是儀表板、報表或其他資料成品中所使用的查詢) 將不會看到他們沒有足夠許可權的資料。

## <a name="premium-features"></a>Premium 功能

### <a name="dataflows-architecture"></a>資料流程架構

資料流程可讓使用者設定後端資料處理作業，以從 polymorphous 資料來源中提取資料、對資料執行轉換邏輯，然後將它放在目標模型中，以便在各種不同的報表轉譯技術中使用。 在工作區中具有成員、參與者或系統管理員角色的任何使用者，都可以建立資料流程。 檢視器角色中的使用者可能會查看資料流程所處理的資料，但可能不會對其組合進行變更。 一旦撰寫資料流程之後，工作區的任何成員、參與者或系統管理員都可以排程重新整理，以及藉由取得其擁有權來查看和編輯資料流程。

每個已設定的資料來源都會系結至用來存取該資料來源的用戶端技術。 存取它們所需的認證結構是為了符合資料來源的必要執行詳細資料而形成。 當資料正在進行時，Power Query 服務會套用轉換邏輯。 針對 premium 資料流程，Power Query 服務會在後端節點中執行。 您可以直接從雲端來源或透過內部部署安裝的閘道提取資料。 當直接從雲端來源提取至服務或閘道時，傳輸會使用用戶端技術特定的保護方法（如果適用）。 當資料從閘道傳輸到雲端服務時，就會加密。 請參閱上面的 [處理中資料](#data-in-processing) 一節。

當客戶指定的資料來源需要認證才能存取時，資料流程的擁有者/建立者會在撰寫期間提供它們。 它們是使用標準的全產品認證儲存體進行儲存。 請參閱上述的「 [資料來源驗證](#authentication-to-data-sources) 」一節。 使用者可以設定各種方法來優化資料持續性和存取。 根據預設，資料會放在 Power BI 擁有與受保護的儲存體帳戶中。 Blob 儲存體容器上已啟用儲存體加密，以保護待用資料。 請參閱下面的待用 [資料](#data-at-rest) 一節。 不過，使用者可以設定自己的儲存體帳戶與其專屬的 Azure 訂用帳戶相關聯。 當您這樣做時，會將該儲存體帳戶的存取權授與 Power BI 服務主體，讓它可以在重新整理時寫入資料。 在此情況下，儲存體資源擁有者會負責在設定的 ADLS 儲存體帳戶上設定加密。 資料一律會使用加密傳送至 Blob 儲存體。

由於存取儲存體帳戶的效能對某些資料而言可能是最理想的，因此使用者也可以選擇使用 Power BI 裝載的計算引擎來提高效能。 在此情況下，資料會儲存在 SQL 資料庫中，而此資料庫可透過後端 Power BI 系統存取來存取 DirectQuery。 資料一律會在檔案系統上加密。 如果使用者提供金鑰來加密儲存在 SQL database 中的資料，該金鑰將用來對它進行雙向加密。

使用 DirectQuery 進行查詢時，會使用加密的傳輸通訊協定 HTTPS 來存取 API。 DirectQuery 的所有次要或間接使用都是由先前所述的相同存取控制所控制。 由於資料流程一律系結至工作區，因此資料的存取一律會由該工作區中的使用者角色進行閘道。 使用者至少必須具有讀取權限，才能透過任何方式來查詢資料。

當 Power BI Desktop 用來存取資料流程中的資料時，它必須先使用 Azure AD 驗證使用者，以判斷使用者是否有足夠的許可權來查看資料。 如果是，則會取得 SaS 金鑰，並使用加密的傳輸通訊協定 HTTPS 直接存取儲存體。

管線中的資料處理會發出 Office 365 審核事件。 其中有些事件將會捕捉安全性和隱私權相關的作業。

### <a name="paginated-reports"></a>編頁報表

編頁報表是設計用來進行列印或共用。 這些報表稱為「編頁」，因為已將其格式化，可適當地符合頁面。 即使資料表跨越多個頁面，它們也會在資料表中顯示所有資料。 這些報表也稱為「完美像素」，因為您可完全控制其報表頁面版面配置。

編頁報表支援以 Microsoft Visual Basic .NET 撰寫的豐富且功能強大的運算式。 在整個 Power BI Report Builder 的編頁報表中會廣泛利用運算式來擷取、計算、顯示、分組、排序、篩選、參數化和格式化資料。

運算式是由報表的作者所建立，可存取 .NET framework 的廣泛功能範圍。 編頁報表的處理和執行是在沙箱內執行。

 ( .rdl) 的編頁報表定義會儲存在 Power BI 中，以及發行和/或轉譯使用者需要驗證和授權的編頁報表，就像上述 [Power BI 服務的驗證](#authentication-to-the-power-bi-service) 一節中所述。

在驗證期間取得的 Azure AD 權杖，是用來直接從瀏覽器向 Power BI Premium 叢集進行通訊。

針對 Premium Gen1，每一個租使用者的容量都有一個沙箱，而且會由指派給容量的工作區共用。

![編頁報表 Gen 1](media/whitepaper-powerbi-security/powerbi-security-whitepaper-paginated-reports-gen1.png)

針對 Premium Gen2 (在預覽) 中，會為每個報表轉譯建立個別和專屬的暫時沙箱，以提供使用者之間較高層級的隔離。

![編頁報表 Gen 2](media/whitepaper-powerbi-security/powerbi-security-whitepaper-paginated-reports-gen2.png)

編頁報表可以存取一組廣泛的資料來源，作為報表轉譯的一部分。 沙箱不會直接與任何資料來源通訊，而是會與受信任的進程通訊以要求資料，然後受信任的程式會將所需的認證附加至連接。 如此一來，沙箱永遠無法存取任何認證或秘密。 

為了支援 Bing maps 之類的功能或 Azure Functions 的呼叫，沙箱確實可以存取網際網路。

### <a name="power-bi-embedded-analytics"></a>Power BI 內嵌式分析

獨立軟體廠商 (Isv) 和解決方案提供者有兩種主要模式可在其 web 應用程式和入口網站中內嵌 Power BI 構件： [為您的組織內嵌](../developer/embedded/embed-sample-for-your-organization.md) ，並 [為客戶進行內嵌](../developer/embedded/embed-sample-for-customers.md)。 成品會內嵌至應用程式或入口網站中的 iframe。 Iframe 不允許從外部 web 應用程式或入口網站讀取或寫入資料，而 iframe 的通訊則是使用 Power BI 的用戶端 SDK （使用 POST 訊息）來完成。

在 [您組織](../developer/embedded/embed-sample-for-your-organization.md) 的內嵌案例中，Azure AD 使用者透過其企業及其所自訂的入口網站來存取自己的 Power BI 內容。 本白皮書中所述的所有 Power BI 原則和功能（例如資料列層級安全性 (RLS) ）都會自動套用至所有使用者，不論他們是透過 [Power BI 入口網站](https://app.powerbi.com/) 或透過自訂入口網站存取 Power BI。

在 [適用于您客戶](../developer/embedded/embed-sample-for-customers.md) 案例的內嵌中，isv 通常擁有 Power BI 租使用者和 Power BI 成品 (儀表板、報表、資料集等 ) 。 ISV 後端服務會負責驗證其使用者，並決定哪些成品和哪些存取層級適用于該使用者。 ISV 原則決策會在 Power BI 所產生的 [內嵌權杖](/rest/api/power-bi/embedtoken) 中進行加密，並傳遞至 isv 後端，以根據 isv 的商務邏輯進一步散發給終端使用者。 使用瀏覽器或其他用戶端應用程式的終端使用者無法解密或修改內嵌權杖。 用戶端 Sdk （例如 [Power BI 用戶端 api](/javascript/api/overview/powerbi/) ）會自動將加密的內嵌權杖附加至 Power BI 的要求，作為 *授權：要改用 embedtoken* 標頭。 根據此標頭，Power BI 將會強制執行所有原則 (例如存取或 RLS) 在產生期間所指定的完全相同。

為了啟用內嵌和自動化，以及產生上面所述的內嵌權杖，Power BI 會公開一組豐富的 [REST api](/rest/api/power-bi/embedtoken)。 這些 Power BI REST Api 支援使用者 [委派](/azure/active-directory/develop/v2-permissions-and-consent) 和 [服務主體](../admin/service-premium-service-principal.md) Azure AD 驗證和授權的方法。

Power BI 內嵌式分析及其 REST Api 支援本文中所述的所有 Power BI 網路隔離功能：例如， [服務](#service-tags) 標籤和 [私用連結](#private-link-integration)。

### <a name="ai-features"></a>AI 功能

Power BI 目前在產品中支援兩種廣泛的 AI 功能類別： AI 視覺效果和 AI 擴充。 視覺效果層級的 AI 功能包括關鍵影響因素、分解樹狀結構、智慧型敘述、異常偵測、R 視覺效果、Python 視覺效果、叢集、預測、Q&A、Quick-Insights 等功能。AI 擴充功能包括 AutoML、AzureML、CognitiveServices、R/Python 轉換等功能。 

現今所述的大部分功能現在都可在共用和 Premium 工作區中受到支援。 不過，只有在 Premium 工作區中才支援 AutoML 和 CognitiveServices，因為 IP 有限制。 現在，透過 Power BI 中的 AutoML 整合，使用者可以建立及定型自訂 ML 模型， (例如預測、分類、回歸等 ) 並加以套用，以在將資料載入 Premium 工作區中定義的資料流程時取得預測。 此外，Power BI 使用者可以套用數個 CognitiveServices Api （例如 >microsoft.azure.cognitiveservices.language.textanalytics 和 ImageTagging）來轉換資料，然後再將資料載入至 Premium 工作區中定義的資料流程/資料集。 

高階 AI 擴充功能最適合視為無狀態 AI 函式/轉換的集合，可供 Power BI 資料集或資料流程所使用的資料整合管線中 Power BI 使用者使用。 請注意，這些函數也可以從 Power BI 服務中目前的資料流程/資料集撰寫環境中存取，並 Power BI Desktop。 這些 AI 函數/轉換一律會在 Premium 工作區/容量中執行。 這些函式在 Power BI 中會顯示為數據源，而這些資料來源需要使用 AI 函式之 Power BI 使用者的 Azure AD token。 這些 AI 資料來源很特殊，因為它們不會呈現任何自己的資料，而且只會提供這些函式/轉換。 在執行期間，這些功能不會對其他服務進行任何輸出呼叫，以傳輸客戶的資料。 讓我們個別查看高階案例，以瞭解通訊模式以及相關的安全性相關詳細資料。 

為了定型和套用 AutoML 模型，Power BI 使用 Azure AutoML SDK，並在客戶的 Power BI 容量中執行所有訓練。 在定型反復專案期間，Power BI 會呼叫測試 AzureML 服務，為目前的反復專案選取適當的模型和超參數。 在此輸出呼叫中，只會傳送先前反覆運算中的相關實驗中繼資料 (例如精確度、ml 演算法、演算法參數等 ) 。 AutoML 訓練會產生 ONNX 模型並定型報表資料，然後將資料儲存在資料流程中。 之後 Power BI 的使用者可以接著將定型的 ML 模型套用為轉換，以依排程讓 ML 模型。 針對 >microsoft.azure.cognitiveservices.language.textanalytics 和 ImageTagging Api，Power BI 不會直接呼叫 CognitiveServices 服務 Api，而是使用內部 SDK 來執行 Power BI Premium 容量中的 Api。 目前 Power BI 資料流程和資料集都支援這些 Api。 在 Power BI Desktop 中撰寫資料集時，如果使用者可以存取 Premium Power BI 工作區，則只能存取此功能。 因此，系統會提示客戶提供其 Azure AD 認證。 

## <a name="network-isolation"></a>網路隔離

本節將概述 Power BI 的 advanced security 功能。 某些功能具有特定的授權需求。 請參閱下列各節以取得詳細資料。

### <a name="service-tags"></a>服務標籤

服務標籤代表來自指定 Azure 服務的一組 IP 位址前置詞。 它有助於將頻繁更新網路安全性規則的複雜性降至最低。 客戶可以使用服務標籤來定義 [網路安全性群組](/azure/virtual-network/security-overview#security-rules) 或 [Azure 防火牆](/azure/firewall/service-tags)上的網路存取控制。 客戶在建立安全性規則時，可以使用服務標籤來取代特定的 IP 位址。 藉由指定服務標籤名稱 (例如，在規則的適當來源或目的地)  (中使用 PowerBI) ，客戶可以允許或拒絕對應服務的流量。 Microsoft 會管理服務標籤包含的位址前置詞，並隨著位址變更自動更新服務標籤。

### <a name="private-link-integration"></a>Private Link 整合

Azure 網路功能提供 Azure Private Link 功能，可讓 Power BI 透過 Azure 網路私人端點提供安全的存取。 使用 Azure Private Link 和私人端點時，資料流量會使用 Microsoft 的骨幹網路基礎結構私下傳送，因此資料不會跨越網際網路。

Private Link 可確保 Power BI 使用者在 Power BI 服務中的資源時，會使用 Microsoft 私人網路骨幹。

使用 Private Link 搭配 Power BI 可提供下列優點：
* Private Link 可確保流量會透過 Azure 骨幹流向 Azure 雲端式資源的私人端點。
* 從非 Azure 基礎的基礎結構（例如內部部署存取）隔離網路流量，會要求客戶必須設定 ExpressRoute 或虛擬私人網路 (VPN) 。

如需其他資訊，請參閱 [存取 Power BI 的私用連結](../admin/service-security-private-links.md) 。

### <a name="vnet-connectivity-preview---coming-soon"></a> (預覽的 VNet 連線能力-即將推出) 

雖然 Private Link 整合功能提供對 Power BI 的安全輸入連線，但 VNet 連線能力功能可讓您從 Power BI 到 VNet 內的資料來源，進行安全的輸出連線。 

 (Microsoft 管理) 的 VNet 閘道，可避免安裝和監視內部部署資料閘道的額外負荷，以連接到與 VNet 相關聯的資料來源。 不過，它們仍會遵循管理安全性與資料來源的熟悉程式，就像使用內部部署資料閘道一樣。

以下概述當您與使用 VNet 閘道連接到 VNet 中的資料來源 Power BI 報表進行互動時，會發生什麼事：

1. Power BI 的雲端服務 (或其他支援的雲端服務之一) 開始查詢，並將查詢、資料來源詳細資料和認證傳送給 Power Platform VNet 服務 (PP VNet) 。

1. PP VNet 服務接著會安全地將執行 VNet 閘道的容器插入子網中。 此容器現在可以連接到可從這個子網記憶體取的資料服務。

1. PP VNet 服務接著會將查詢、資料來源詳細資料和認證傳送給 VNet 閘道。 

1. VNet 閘道會取得查詢，並使用這些認證連接到資料來源。

1. 接著會將查詢傳送至資料來源以供執行。

1. 執行之後，結果會傳送至 VNet 閘道，而 PP VNet 服務會將資料從容器安全地推送至 Power BI 的雲端服務。

這項功能很快就會提供公開預覽。

### <a name="service-principals"></a>服務主體

Power BI 支援使用服務主體。 儲存用於加密或存取 Key Vault 中 Power BI 的任何服務主體認證、指派適當的存取原則至保存庫，以及定期檢查存取權限。

如需其他詳細資料，請參閱 [使用服務主體自動化 Premium 工作區和資料集工作](../admin/service-premium-service-principal.md) 。

## <a name="data-loss-prevention-dlp"></a>資料遺失防止 (DLP) 

### <a name="microsoft-365-sensitivity-labels"></a>Microsoft 365 敏感度標籤

Power BI 與 Microsoft 資訊保護的深度整合 (MIP) 敏感度標籤，可讓組織針對 DLP 原則管理、跨 Office 套件進行審核和合規性的單一整合式解決方案。

在 Power BI 中啟用敏感度標籤時：
* 您可以使用 Office 和 Azure 範疇中使用的相同熟悉的 Microsoft 資訊保護敏感度標籤，來分類及標記 Power BI 服務 (GA) 和 Power BI Desktop (preview) 中的敏感性資料。 
* 即使將 Power BI 的內容匯出至 Excel、PowerPoint、PDF 或 *.pbix* 檔案，也可以強制執行治理原則，以協助確保資料即使在離開 Power BI 時仍受到保護。
* 當 MIP 標籤套用至桌面上的 *.pbix* 檔案時，可以根據 mip 標籤原則加密 *.pbix* 檔案，以確保只有獲得授權的使用者可以編輯這個檔案。
* 您可以輕鬆地分類和保護 *.pbix* 檔案，就像是使用 Excel、Word 和 PowerPoint 檔案來完成一樣。 只要按兩下滑鼠，就可以根據檔的敏感度層級來標記檔案，甚至在包含商務機密資料的情況下，將檔案加密。
* Excel 活頁簿在連接至 Power BI (預覽) 時，會自動繼承敏感度標籤，讓您可以在 Excel 中分析 Power BI 資料集時，維持端對端分類並套用保護。
* Power BI 報表和儀表板上套用的敏感度標籤將會顯示在 Power BI iOS 和 Android 行動裝置應用程式中。
* 當 Power BI 報表內嵌于小組、SharePoint 或安全網站 (預覽) 時，敏感度標籤將會保存。 這可協助組織在內嵌 Power BI 內容時，在匯出時維持分類和保護。
* 在 Power BI 服務中建立新內容時的標籤繼承，可確保在資料集的資料 Power BI 服務集上套用的標籤會套用到在資料集上建立的新內容。 
* [Power BI 系統管理員掃描 api](/rest/api/power-bi/admin/workspaceinfo_getscanresult) 可以解壓縮 Power BI 成品的敏感度標籤，讓 Power BI 和 InfoSec 系統管理員可以監視 Power BI 服務中的標籤，並產生執行報告。 
* Power BI 確定只有獲得授權的使用者可以變更或移除 Power BI 服務中具有保護設定的標籤。 
* 即將推出
    * Power BI 管理 Api 來套用 MIP 標籤，讓中央小組以程式設計的方式為 Power BI 服務中的內容加上標籤。  
    * 系統管理員可以在 Power BI 服務 (preview) 中強制套用具有強制標籤原則的新內容或已編輯內容的標籤。
    * Power BI 服務內的自動下游構件標記。 套用或變更資料集上的標籤時，標籤會自動套用至所有連線到此成品的下游內容。

如需其他詳細資料，請參閱 [Power BI 中的 Microsoft 資訊保護敏感度標籤檔](../admin/service-security-sensitivity-label-overview.md) 。

### <a name="microsoft-cloud-app-security-mcas-for-power-bi"></a>適用于 Power BI 的 Microsoft Cloud App Security (MCAS) 

Microsoft Cloud App Security 是全球領先的雲端存取安全性代理程式之一，在 Gartner 的 Cloud Access Security Broker (CASB) 市場的魔術象限中，名為領導者。 Cloud app security 可用來保護雲端應用程式的使用。 它可讓組織即時監視和控制有風險的 Power BI 會話，例如從非受控裝置存取使用者。 安全性系統管理員可以定義原則來控制使用者動作，例如下載具有敏感性資訊的報表。

有了 Cloud App Security，組織就可以得到下列 DLP 功能： 
* 設定即時控制項，在 Power BI 中強制執行具風險的使用者會話。 例如，如果使用者從其國家/地區以外的地方連線到 Power BI，就可以透過 Cloud App Security 的即時控制項來監視會話，並可立即封鎖具有風險的動作，例如下載標記為「高度機密」敏感度標籤的資料。
* 使用 Cloud App Security 的活動記錄調查 Power BI 的使用者活動。 Cloud App Security 活動記錄包含在 Office 365 audit 記錄檔中所捕捉的 Power BI 活動，其中包含所有使用者和系統管理員活動的相關資訊，以及適用于相關活動（例如套用、變更和移除標籤）的敏感度標籤資訊。 系統管理員可以利用 Cloud App Security 的 advanced 濾波器和快速動作來進行有效的問題調查。 
* 建立自訂原則，以警示 Power BI 中的可疑使用者活動。 您可以利用 Cloud App Security 的活動原則功能，來定義您自己的自訂規則，以協助您偵測偏離此標準的使用者行為，甚至可能會自動採取行動（如果看似危險）。
* 使用 Cloud App Security 內建的異常偵測。 Cloud App Security 的異常偵測原則提供現成可用的使用者行為分析和機器學習服務，讓您準備好開始在雲端環境中執行先進的威脅偵測。 當異常偵測原則識別可疑的行為時，會觸發安全性警示。 
* Cloud App Security 入口網站中 Power BI 管理員角色。 Cloud App Security 提供應用程式專屬的系統管理員角色，可用來授與 Power BI 管理員在入口網站中存取 Power BI 相關資料所需的許可權，例如警示、有風險的使用者、活動記錄和其他 Power BI 相關資訊。

如需其他詳細資料，請參閱 [Power BI 中的使用 Microsoft Cloud App Security 控制項](../admin/service-security-using-microsoft-cloud-app-security-controls.md) 。

## <a name="preview-security-features"></a>預覽安全性功能

本主題列出預計在2021年3月發行的功能。 因為本主題列出可能尚未發行的功能，所以 **傳遞時程表可能會變更，且預計的功能可能會在2021年3月之後發行，或可能完全不會發行**。 如需有關預覽的詳細資訊，請參閱 [線上服務條款](https://www.microsoft.com/licensing/product-licensing/products)。

### <a name="bring-your-own-log-analytics-byola"></a>整合您自己的 Log Analytics (BYOLA) 

攜帶您自己的 Log Analytics 可讓 Power BI 和 Azure Log Analytics 之間進行整合。 這項整合包括 Azure Log Analytics 的先進分析引擎、互動式查詢語言，以及內建的機器學習結構。

## <a name="power-bi-security-questions-and-answers"></a>Power BI 安全性問題和解答

下列問題是 Power BI 常見的安全性問題和回答。 這些都是根據新增至這份白皮書的時間進行組織，讓您能夠在這份白皮書更新時快速找到新的問題和解答。 最新的問題會新增至此清單的結尾。

**使用 Power BI 時，使用者如何連線至資料來源並存取？**

* Power BI 可為每位使用者提供雲端認證或透過個人閘道的連線，管理資料來源的認證。 內部部署資料閘道所管理的資料來源可以跨企業共用，而這些資料來源的許可權可以由閘道系統管理員管理。設定資料集時，允許使用者從其個人存放區選取認證，或使用內部部署資料閘道來使用共用認證。

    在匯入案例中，使用者會根據使用者的登入建立連接，並使用認證來存取資料。 將資料集發佈至 Power BI 服務之後，Power BI 一律會使用此使用者的認證來匯入資料。 匯入資料之後，在報表和儀表板中查看資料並不會存取基礎資料來源。 Power BI 針對選取的資料來源支援單一登入驗證。 如果連接已設定為使用單一登入，則會使用資料集擁有者的認證來與資料來源連接。

    針對使用 DirectQuery 連接的報表，資料來源會使用預先設定的認證直接連接，而預先設定的認證會在任何使用者流覽資料時用來連接到資料來源。 如果資料來源是使用單一登入直接連接，當使用者流覽資料時，就會使用目前使用者的認證來連接到資料來源。 使用 with single sign-on 時，資料列層級安全性 (RLS) 可在資料來源上執行，這可讓使用者查看他們有權存取的資料。 當連線到雲端中的資料來源時，會使用 Azure AD authentication 進行單一登入;針對內部部署資料來源，支援 Kerberos、SAML 和 Azure AD。  

    使用 Kerberos 連接時，使用者的 UPN 會傳遞至閘道，並使用 Kerberos 限制委派，而使用者會被模擬並連接至個別的資料來源。 SAP Hana 資料來源的閘道上也支援 SAML。 如需詳細資訊，請 [流覽閘道的單一登入](../connect-data/service-gateway-sso-overview.md)。

    如果資料來源是 Azure Analysis Services 或內部部署 Analysis Services 並已設定資料列層級安全性 (RLS) ，則 Power BI 服務會套用該資料列層級安全性，而沒有足夠認證可存取基礎資料的使用者（可能是儀表板、報表或其他資料成品中所使用的查詢） (將不會看到使用者沒有足夠許可權的資料。

    [使用 Power BI 的資料列層級安全性](../admin/service-admin-rls.md) 可用來限制指定使用者的資料存取。 篩選準則會限制資料列層級的資料存取，您可以在角色中定義篩選。  

**Power BI 如何傳輸資料？**

* 只有當客戶選擇的資料來源不支援 HTTPS) 從資料來源連接到 Power BI 服務時，Power BI 所要求和傳輸的所有資料都會使用 HTTPS (在傳輸中加密。 會建立與資料提供者之間的安全連線，且唯有在建立該連線後，資料才能周遊網路。

**Power BI 如何快取報表、儀表板或模型資料，且其是否安全？**

* 存取資料來源時，Power BI 服務會遵循本檔稍早的「 [資料來源驗證](#authentication-to-data-sources) 」一節中所述的程式。

**用戶端是在本機快取網頁資料嗎？**

* 瀏覽器用戶端存取 Power BI 時，Power BI Web 伺服器會將 *Cache-Control* 指示詞設定為 *no-store*。 *no-store* 指示詞會指示瀏覽器不快取使用者正在檢視的網頁，而不是將網頁儲存在用戶端的快取資料夾中。

**什麼是以角色為基礎的安全性、共用報表或儀表板，以及資料連線？如何在資料存取、儀表板視圖、報表存取或重新整理方面運作？**

* 針對已啟用 **非角色層級安全性 (RLS)** 的資料來源，如果透過 Power BI 與其他使用者共用儀表板、報表或資料模型，則該資料即可供與其共用的使用者檢視和互動。 Power BI 「不會」針對資料的原始來源重新驗證使用者；資料一旦上傳至 Power BI 後，對來源資料進行驗證的使用者需負責管理哪些其他使用者和群組可以檢視資料。

  當資料連線到支援 **RLS** 的資料來源（例如 Analysis Services 資料來源）時，只會在 Power BI 中快取儀表板資料。 每次在 Power BI 中檢視或存取報表或資料集 (使用支援 RLS 之資料來源的資料) 時，Power BI 服務都會存取資料來源，根據使用者的認證來取得資料；如果有足夠的權限，則資料會為載入至該使用者的報表或資料模型中。 如果驗證失敗，使用者會看到錯誤。

  如需詳細資訊，請參閱本檔稍早的「 [資料來源驗證](#authentication-to-data-sources) 」一節。

**我們的使用者會隨時連線到相同的資料來源，其中有些需要與網域認證不同的認證。如何避免在每次建立資料連線時都必須輸入這些認證？**

* Power BI 提供 [Power BI Personal Gateway](../connect-data/service-gateway-personal-mode.md)，此功能可讓使用者為多個不同的資料來源建立認證，並在後續存取每個資料來源時自動使用這些認證。 如需詳細資訊，請參閱 [Power BI Personal Gateway](../connect-data/service-gateway-personal-mode.md)。

**內部部署資料閘道和個人閘道會使用哪些埠？是否有任何功能變數名稱需要允許進行連接？**

* 您可以從下列連結取得此問題的詳細解答： [閘道埠](/data-integration/gateway/service-gateway-communication#ports)

**使用內部部署資料閘道時，如何使用修復金鑰以及它們儲存在哪裡？什麼是安全的認證管理？**

* 在閘道安裝和設定期間，系統管理員會鍵入閘道 **修復金鑰**。 該 **修復金鑰** 是用來產生強式 AES 對稱金鑰。 同時也會建立 RSA 非對稱金鑰。

    這些產生的金鑰 (RSA 和 AES) 會儲存在本機電腦上的檔案中。 此外，該檔案也會受到加密。 只有該特定的 Windows 電腦，以及該特定的閘道服務帳戶，才能解密該檔案的內容。

    當使用者在 Power BI 服務 UI 中輸入資料來源認證時，認證會使用瀏覽器中的公開金鑰進行加密。 閘道會使用 RSA 私密金鑰來解密認證，並使用 AES 對稱金鑰重新加密，然後將資料儲存在 Power BI 服務中。 使用此程序，Power BI 服務永遠無法存取未加密的資料。

**內部部署資料閘道會使用哪些通訊協定？如何確保安全？**

* 閘道支援下列兩種通訊協定：

  - AMQP 1.0 – TCP + TLS：此通訊協定需要開啟埠443、5671-5672 和9350-9354 以進行傳出通訊。 此通訊協定為優先選項，因為具有較低的通訊額外負荷。

  - HTTPS – Websocket over HTTPS + TLS：此通訊協定僅使用埠443。 WebSocket 由單一 HTTP 連線訊息啟動。 一旦建立通道後，通訊本質上為 TCP + TLS。 您可以藉由修改內部 [部署閘道文章](/data-integration/gateway/service-gateway-communication#force-https-communication-with-azure-service-bus)中所述的設定，來強制閘道使用此通訊協定。

**Power BI 中 Azure CDN 的角色是什麼？**

* 如先前所述，Power BI 使用 Azure 內容傳遞網路 (CDN)，以根據地理的地區設定有效率地散發必要的靜態內容和檔案給使用者。 為了探索進一步的詳細資料，Power BI 服務會使用多個 CDN，透過公用網際網路有效率地將必要的靜態內容和檔案散發給使用者。 這些靜態檔案包括產品下載 (例如 Power BI Desktop、內部部署資料閘道或來自不同獨立服務提供者的 Power BI 應用程式)、用來起始及建立任何與 Power BI 服務後續連線的瀏覽器設定檔，以及初始的安全 Power BI 登入頁面。

  根據初始連線至 Power BI 服務期間提供的資訊，使用者瀏覽器會連絡指定的 Azure CDN (對某些檔案則是 WFE) 下載指定通用檔案的集合，其為啟用瀏覽器與 Power BI 服務互動所需的檔案。 然後，瀏覽器頁面會包含 Azure AD 的權杖、會話資訊、相關聯的後端叢集位置，以及從 Azure CDN 和 WFE 叢集下載的檔案集合（在 Power BI 服務瀏覽器會話期間）。

**針對 Power BI 視覺效果，Microsoft 是否會在將專案發行至資源庫之前，執行自訂視覺效果程式碼的任何安全性或隱私權評量？**

* 不會。 客戶應負責檢閱自訂視覺效果程式碼，並判斷程式碼是否可靠。 因為所有自訂視覺效果程式碼都會在沙箱環境內執行，所以自訂視覺效果中的不當程式碼並不會對 Power BI 服務的其他部分造成影響。

**有其他 Power BI 視覺效果會在客戶網路外傳送資訊嗎？**

* 是。 Bing 地圖服務和 ESRI 視覺效果會因使用這些服務的視覺效果而在 Power BI 服務外傳輸資料。

**針對範本應用程式，Microsoft 是否會在將專案發行至資源庫之前，對範本應用程式執行任何安全性或隱私權評定？**
* 不會。 應用程式發行者負責處理內容，而客戶必須負責審查並判斷是否信任範本應用程式發行者。 

**是否有範本應用程式可以將資訊傳送到客戶網路之外？**
* 是。 客戶必須負責檢查發行者的隱私權原則，並判斷是否要在租使用者上安裝範本應用程式。 發行者負責告知客戶應用程式的行為和功能。

**什麼是資料主權？我們可以在位於特定地理位置的資料中心布建租使用者，以確保資料不會離開國家/地區框線？**

* 特定地理位置中的某些客戶可在國家/地區雲端中建立租用戶，其中的資料儲存和處理會和所有其他資料中心分開。 因為有獨立的資料信任者代表 Microsoft 負責運作國家/地區雲端 Power BI 服務，所以國家/地區雲端的安全性類型稍有不同。

  此外，客戶也可以在特定區域中設定租使用者。 不過，這類租使用者沒有 Microsoft 的個別資料信任者。 國家/地區雲端和正式運作之商用 Power BI 服務的定價不同。 如需國家/地區雲端的 Power BI 服務可用性詳細資訊，請參閱 [Power BI 國家/地區雲端](https://powerbi.microsoft.com/clouds/)。

**Microsoft 如何針對擁有 Power BI Premium 訂用帳戶的客戶來處理連接？這些連線與針對非 Premium Power BI 服務所建立的連線有何不同？**

* 針對具有 Power BI Premium 訂用帳戶的客戶所建立的連線，會使用 Azure AD 來啟用存取控制和授權，以實行 [Azure 企業對企業 (B2B) ](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) 授權程式。 Power BI 會處理來自 Power BI Premium 訂閱者到 Power BI Premium 資源的連線，與任何其他 Azure AD 使用者無異。

## <a name="feedback-and-suggestions"></a>意見反應和建議

歡迎提供意見反應。 我們有興趣聽取您對於本白皮書的改進、新增或說明的任何建議，或其他與 Power BI 相關的內容。 將您的建議傳送至 [pbiss@microsoft.com](mailto:pbiss@microsoft.com) 。

## <a name="additional-resources"></a>其他資源

如需更多有關 Power BI 的資訊，請參閱以下資源。

* [開始使用 Power BI Desktop](../fundamentals/desktop-getting-started.md)
* [Power BI REST API - Overview](/rest/api/power-bi/) (Power BI REST API - 概觀)
* [Power BI API reference](/rest/api/power-bi/) (Power BI API 參考)
* [On-premises data gateway (內部部署資料閘道)](../connect-data/service-gateway-onprem.md)
* [Power BI 國家/地區雲端](https://powerbi.microsoft.com/clouds/)
* [Power BI Premium](https://aka.ms/pbipremiumwhitepaper)
* [Power BI 中閘道的單一登入 (SSO) 概觀](../connect-data/service-gateway-sso-overview.md)
