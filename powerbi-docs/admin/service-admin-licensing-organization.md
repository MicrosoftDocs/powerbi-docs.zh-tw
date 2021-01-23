---
title: 將 Power BI 授權提供給組織中的使用者
description: 概述 Power BI 中可用的各種不同使用者授權類型，以及管理員如何為其組織使用者購買和管理授權。
author: mihart
ms.author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 11/11/2020
ms.custom: licensing support
LocalizationGroup: Administration
ms.openlocfilehash: 0c13d0f54d18527e6b8614f40b5b15fd46187968
ms.sourcegitcommit: e8c3f327ac0fc73c118874a24d2601733f8f9e45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2021
ms.locfileid: "98718500"
---
# <a name="licensing-the-power-bi-service-for-users-in-your-organization"></a>將 Power BI 服務授權提供給組織中的使用者

使用者可在 Power BI 服務中執行的動作取決於每位使用者所擁有授權類型。 其授權所提供的存取層級取決於所要存取工作區是否為 Premium 工作區。 Power BI 服務的所有使用者都必須具備授權。

使用者可透過兩種方式取得授權。 使用者可以使用自助式註冊功能與其公司或學校帳戶，來取得自己的免費或 Pro 或 Premium Per User 授權。 或者，管理員可以取得 Power BI 授權，然後將授權指派給使用者。

此文章著重於從管理員觀點購買服務和個別使用者授權。 如需有關使用者如何取得自己授權的詳細資訊，請參閱[以個人身分註冊 Power BI](../fundamentals/service-self-service-signup-for-power-bi.md)。

## <a name="who-can-purchase-and-assign-licenses"></a>誰可以購買及指派授權？

您必須獲指派管理員角色，才能為您的組織購買或指派授權。 指派管理員角色時，會使用 Azure Active Directory 管理中心或 Microsoft 365 系統管理中心來指派。 下表顯示執行購買和授權相關工作所需的角色。 如需有關 Azure Active Directory 中管理員角色的詳細資訊，請參閱[在 Azure Active Directory 中檢視和指派管理員角色](/azure/active-directory/users-groups-roles/directory-manage-roles-portal) \(部分機器翻譯\)。 若要深入了解 Microsoft 365 中的系統管理員角色 (包括最佳做法)，請參閱[關於系統管理員角色](/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide)。

| 誰可以購買服務和授權？ | 誰可以管理使用者授權？ |
| --------------- | --------------- |
| 計費管理員 | 授權管理員 |
| 全域管理員 | 使用者管理員 |
|  | 全域管理員 |

這些角色可管理組織。 如需有關 Power BI 服務管理員角色的資訊，請參閱[了解 Power BI 服務管理員角色](service-admin-role.md)。

## <a name="get-power-bi-for-your-organization"></a>為您的組織取得 Power BI

如需價格的詳細資訊，請參閱[定價與產品比較](https://powerbi.microsoft.com/pricing/)。

全域管理員或計費管理員可以註冊 Power BI 服務，並為其組織中的使用者購買授權。 如果尚未做好購買準備，請選取 Power BI Pro 試用版。 您將獲得 25 個可使用一個月的授權。 如需有關如何註冊的逐步指示，請參閱[為組織取得 Power BI 訂用帳戶](service-admin-org-subscription.md)。

## <a name="about-self-service-sign-up"></a>關於自助式註冊

個別使用者可以使用其工作或學校帳戶來進行註冊，以取得自己的 Power BI 授權。 使用免費授權時，使用者可使用 [我的工作區] 來探索 Power BI 以檢視個人資料分析和視覺效果，但無法與其他使用者共用。 必要具備 Power BI Pro 授權，才能共用內容。 Power BI Premium 授權能解除僅能透過 Premium 與內容類型的存取鎖定。 Premium Per User Premium 授權會將這些功能的存取限制為僅供其他具有 Premium Per User 授權的使用者使用，而容量型 Premium 授權則允許具有免費授權的使用者存取任何內容，同時只有具有 Pro 授權的使用者可以建立內容。 如果組織使用商務雲端，則使用者可將其授權類型升級至 Pro 或直接註冊 Pro。 直接購買或升級至 Pro 並不適用於教育組織，或部署至 Azure Government、Azure 德國，或 Azure China 21Vianet 雲端的組織。

如果不想讓組織中的使用者使用自助式註冊，請參閱[啟用或停用自助式註冊](service-admin-disable-self-service.md)，以了解如何關閉此功能。

關閉自助式註冊，讓使用者無法瀏覽 Power BI 以進行資料視覺化和分析。 如果您封鎖個別註冊，則您可以為組織取得 Power BI (免費) 授權，並指派給所有使用者。 請遵循這些步驟，自動將 Power BI (免費) 授權指派給所有現有使用者：

1. 使用全域管理員或帳單管理員認證，登入 [Microsoft 365 系統管理中心](https://admin.microsoft.com)。
1. 從左側的側邊欄功能表中，選取 [帳單] > [購買服務]。
1. 搜尋或捲動以尋找 Power BI (免費) 供應項目。 選取該供應項目，然後選取 [立即取得]。
1. 輸入涵蓋您所有使用者所需的授權數目。
1. 選取 [自動將所有使用者指派為沒有授權的使用者]，然後簽出。

  ![Power BI 免費自動指派訂閱的螢幕擷取畫面，其中顯示自助式註冊。](media/service-admin-licensing-organization/m365-auto-assign.png)

如果您想要查看組織中哪些使用者可能已經具備授權，請參閱[檢視和管理使用者授權](service-admin-manage-licenses.md)以了解做法。

## <a name="license-types-and-capabilities"></a>授權類型與功能

有兩種 Power BI 個別使用者授權：免費的 Pro 與 Premium。 使用者需要哪種類型的授權，取決於內容的儲存位置、他們將與該內容互動的方式，以及該內容是否使用 Premium 功能。 內容可儲存在哪裡，會取決於您組織的[授權類型](#license-types)。

其中一種授權類型是 [Power BI Premium](service-admin-premium-purchase.md) 容量型授權，其可讓具備免費授權的使用者操作已指派給 Premium 容量之工作區中的內容。 在 Premium 容量之外，具備免費授權的使用者則只能使用 Power BI 服務來連線到資料，然後在 [我的工作區] 中建立報表和儀表板。 這些使用者無法與其他人共用內容，或將內容發佈至其他工作區。 若要深入了解工作區類型，請參閱[工作區類型](../consumer/end-user-workspaces.md#types-of-workspaces)。

具有免費及 Pro 個別使用者授權的 Power BI 授權，只能使用共用且受限的容量來處理內容。 如果內容儲存在該共用容量中，則獲指派 Power BI Pro 授權的使用者只能與其他 Power BI Pro 使用者共同作業。 他們可以取用其他使用者所共用的內容、將內容發佈到應用程式工作區、共用儀表板，以及訂閱儀表板和報表。  當工作區在 Premium 容量中時，Pro 使用者可將內容散發給沒有 Power BI Pro 授權的使用者。

使用 Premium Per User 授權時，由具有 Premium Per User 授權的使用者所建立的內容，除非特別將該內容放置於裝載在 Premium 容量上的工作區中，否則就只能與其他具有 Premium 授權的使用者共用。 下表摘要說明每個授權類型的基本功能。 如需每一授權類型的詳細功能可用性明細，請參閱[依授權類型排列的功能](../fundamentals/service-features-license-type.md)。

| 授權類型 | 工作區在共用容量中時的功能 | 工作區在 Premium 容量中時的額外功能 |
| --------- | ----------- | ----------- |
| Power BI (免費) | 存取我的工作區中的內容 | 取用與其共用的內容 |
| Power BI Pro | 將內容發佈到其他工作區、共用儀表板、訂閱儀表板和報表、與具備 Pro 授權的使用者共用 | 將內容散發給具備免費授權的使用者 |

## <a name="license-types"></a>授權類型

所有來自 Microsoft 的使用者型商業授權都是以 Azure Active Directory 身分識別為基礎。 若要使用 Power BI 服務，則必須使用 Azure Active Directory 支援的商業授權身分識別來登入。 您可以將 Power BI 新增至任何使用 Azure Active Directory 作為識別服務的 Microsoft 授權。 某些授權 (例如 Office 365 E5) 包含 Power BI Pro 授權，因此無須個別註冊 Power BI。

組織可使用兩種類型的 Power BI 授權：標準版與進階版。

使用標準的自助式 Power BI Pro 授權時，管理員可以指派個別使用者授權。 Power BI Pro 授權會針對每位使用者按月收費。 此授權類型可進行共同作業、發佈、共用以及特定分析。 內容會儲存到完全由 Microsoft 管理的共用儲存體容量。

Power BI Premium 授權會為組織配置容量。 Premium 適用於企業 BI、巨量資料分析及雲端與內部部署報告，可提供進階的管理和部署控制。 專用計算與儲存體資源是由您組織中的容量管理員所管理。 此專用環境有每月費用。 除了其他 Premium 優點之外，儲存在 Premium 容量中的內容還可供沒有 Power BI Pro 授權的使用者存取，以及散發給這些使用者。 必須至少有一位使用者獲指派 Power BI Pro 授權，才能使用 Premium，而內容建立者與開發人員則仍然需要 Power BI Pro 授權。

這兩種授權類型並不互斥。 您可以同時具備 Power BI Premium 和 Power BI Pro。 在此組態中，儲存在 Premium 容量中的內容可以與所有使用者共用，且共用容量也可供使用。 如需有關容量限制的資訊，請參閱[管理 Power BI 工作區中的資料儲存體](service-admin-manage-your-data-storage-in-power-bi.md)。

若要比較產品功能與定價，請參閱 [Power BI 定價](https://powerbi.microsoft.com/pricing)。

## <a name="guest-user-access"></a>來賓使用者存取權

您可能會想要將內容散發給組織外的使用者。 您可以透過邀請外部使用者以來賓身分檢視內容，與他們共用內容。 透過 Azure Active Directory 企業對企業 (Azure AD B2B) 可與外部來賓使用者進行共用。 若要與外部使用者共用，必須符合下列先決條件：

- 必須啟用與外部使用者共用內容的功能

- 來賓使用者必須具備可檢視共用內容的適當授權

如需有關來賓使用者存取權的詳細資訊，請參閱[使用 Azure AD B2B 將 Power BI 內容散發給外部來賓使用者](service-admin-azure-ad-b2b.md)。

## <a name="purchase-power-bi-pro-licenses"></a>購買 Power BI Pro 授權

身為管理員，您可以透過 Microsoft Office 365 或 Microsoft 合作夥伴購買 Power BI Pro 授權。 購買授權之後，您可以將它們指派給個別使用者。 如需詳細資訊，請參閱[購買及指派 Power BI Pro 授權](service-admin-purchasing-power-bi-pro.md)。

### <a name="power-bi-pro-license-expiration"></a>Power BI Pro 授權到期

在 Power BI Pro 授權到期後有一段寬限期。 若是屬於大量授權購買的授權，寬限期為 90 天。 如果您直接購買授權，則寬限期為 30 天。

Power BI Pro 具有與 Microsoft 365 相同的授權生命週期。 如需詳細資訊，請參閱[當 Microsoft 365 商務版訂閱結束時，我的資料與存取權會如何？](/microsoft-365/commerce/subscriptions/what-if-my-subscription-expires)。


## <a name="next-steps"></a>後續步驟

- [購買及指派 Power BI Pro 授權](service-admin-purchasing-power-bi-pro.md)
- [商務訂閱與計費文件](/microsoft-365/commerce/?view=o365-worldwide)
- [尋找已登入的 Power BI 使用者](service-admin-access-usage.md)
- 有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)


Power BI 已推出 Power BI Premium Gen2 作為預覽供應項目，其能透過對下列領域的改進來改善 Power BI Premium 體驗：
* 效能
* 每位使用者授權。 如需詳細資訊，請參閱「 [每位使用者的 PREMIUM 常見問題](service-premium-per-user-faq.md) 」。
* 範圍更大的擴縮
* 改善的計量
* 自動調整
* 降低管理負擔

如需 Power BI Premium Gen2 的詳細資訊，請參閱 [Power BI Premium 第 2 代 (預覽)](service-premium-what-is.md#power-bi-premium-generation-2-preview)。
