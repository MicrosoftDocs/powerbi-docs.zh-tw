---
title: 購買及指派 Power BI Pro 授權
description: 了解如何購買及指派 Power BI Pro 使用者授權給使用者，讓他們可以在 Power BI 服務中存取內容並與其他人共同作業。
author: mihart
ms.author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 04/08/2020
ms.custom: licensing support
LocalizationGroup: Administration
ms.openlocfilehash: 0184e549911afb784e06b1ee829bf113ff97e067
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99086295"
---
# <a name="purchase-and-assign-power-bi-pro-user-licenses"></a>購買及指派 Power BI Pro 使用者授權

>[!IMPORTANT]
>此文章適用於管理員。 您是否為已準備好升級至 Power BI Pro 授權的使用者？ 直接前往[開始使用 Power BI Pro](https://go.microsoft.com/fwlink/?LinkId=2106428&clcid=0x409&cmpid=pbidocs-purchasing-power-bi-pro) 以設定您的帳戶。

Power BI Pro 是一種個別使用者授權，可讓使用者讀取其他使用者在 Power BI 服務中發佈的報表與儀表板，以及與它們互動。 擁有此授權類型的使用者可以與其他 Power BI Pro 使用者共用內容和共同作業。 只有 Power BI Pro 使用者才能發佈或和其他使用者共用內容，或取用由其他使用者建立的內容，除非是由 Power BI Premium 容量裝載該內容。 如需有關可用之授權與訂用帳戶類型的詳細資訊，請參閱[組織中的 Power BI 授權](service-admin-licensing-organization.md)。

## <a name="purchase-power-bi-pro-user-licenses"></a>購買 Power BI Pro 使用者授權

此文章說明如何在 Microsoft 365 系統管理中心內購買 Power BI Pro 使用者授權。 購買授權之後，您可以在 Microsoft 365 系統管理中心或 Azure 入口網站中將其指派給使用者。

> [!NOTE]
> 自 2020 年 1 月 14 日起，商業雲端客戶可使用 Power Platform 產品 (Power BI、Power Apps 和 Power Automate) 的自助式購買、訂閱和授權管理功能。 如需詳細資訊，請參閱[自助式購買常見問題集](/microsoft-365/commerce/subscriptions/self-service-purchase-faq) \(部分機器翻譯\)。 若要啟用或停用自助式購買功能，請參閱[啟用或停用自助式註冊與購買](./service-admin-disable-self-service.md)。

### <a name="prerequisites"></a>必要條件

若要在 Microsoft 365 系統管理中心內購買和指派授權，您必須是 Microsoft 365 中[全域管理員或計費管理員](https://support.office.com/article/about-office-365-admin-roles-da585eea-f576-4f55-a1e0-87090b6aaa9d)角色的成員。

若要在 Azure 入口網站中指派授權，您必須是 Power BI 針對 Azure Active Directory 查閱所使用 Azure 訂用帳戶的擁有者。

### <a name="purchase-licenses-in-microsoft-365"></a>在 Microsoft 365 中購買授權

> [!NOTE]
> 如果您通常是透過大量授權合約 (例如 Enterprise 合約) 購買授權，並且想要收到發票，而不是使用信用卡或銀行帳戶購買，則必須以不同的方式提交訂單。 請與您的 Microsoft 轉銷商合作，或透過大量授權服務中心來新增或移除授權。 如需詳細資訊，請參閱[管理訂閱授權](/microsoft-365/commerce/licenses/buy-licenses)。

請遵循下列步驟以在 Microsoft 365 系統管理中心內購買 Power BI Pro 授權：

1. 登入 [MIcrosoft 365 系統管理中心](https://admin.microsoft.com)。

2. 在導覽功能表上，選取 [計費] > [購買服務]。

3. 搜尋或捲動以找出您想要購買的訂用帳戶。 您會在靠近頁面底部的 [您可能會有興趣的其他類別] 底下看到 [Power BI]。 選取連結以檢視可供您的組織使用的 Power BI 訂用帳戶。

4. 選取 [Power BI Pro]。

5. 在 [購買服務] 頁面上，選取 [購買]。

6. 根據您希望使用的付款方式，選擇 [按月支付] 或 [支付全年費用]。

7. 在 [您想要多少使用者?] 底下，輸入要購買的授權數目，然後選取 [立即結帳] 以完成交易。

8. 若要確認您的購買，請前往 [計費] > [產品與服務] 並尋找 [Power BI Pro]。

9. 之後若要新增更多授權，請在 [產品與服務] 頁面上找出 [Power BI Pro]，然後選取 [新增/移除授權]。


## <a name="assign-licenses-in-the-microsoft-365-admin-center"></a>在 Microsoft 365 系統管理中心內指派授權

如需在 Microsoft 365 系統管理中心指派授權的資訊，請參閱[將授權指派給使用者](/office365/admin/manage/assign-licenses-to-users)。

若是來賓使用者，請參閱[在 [授權] 頁面上將授權指派給使用者](/office365/admin/manage/assign-licenses-to-users#assign-licenses-to-users-on-the-licenses-page)。 將 Pro 授權指派給來賓使用者之前，請連絡您的 Microsoft 帳戶代表，以確保您符合 Microsoft 合約條款的規範。

## <a name="assign-licenses-in-the-azure-portal"></a>在 Azure 入口網站中指派授權

按照以下步驟操作，將 Power BI Pro 授權指派給個別使用者帳戶：

1. 登入 [Azure 入口網站](https://portal.azure.com/)。

2. 搜尋並選取 [Azure Active Directory]。

3. 在 [Azure Active Directory] 資源功能表中的 [管理]，選取 [授權]。

4. 從 [授權 - 概觀] 資源功能表中選取 [所有產品]，然後選取 [Power BI Pro]，以顯示授權使用者的清單。

5. 從命令列選取 [+ 指派]。 在 [指派授權] 頁面上，先選擇使用者，然後選取 [指派選項] 開啟所選使用者帳戶的 Power BI Pro 授權。

## <a name="next-steps"></a>後續步驟

- [組織中的 Power BI 授權](service-admin-licensing-organization.md)

 - [尋找已登入的 Power BI 使用者](service-admin-access-usage.md)

 - [以個人身分註冊 Power BI](../fundamentals/service-self-service-signup-for-power-bi.md)

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)