---
title: 租用戶設定指引
description: Power BI 租用戶設定的指導。
author: paulinbar
ms.author: painbar
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/10/2020
ms.openlocfilehash: 66d721670f90efb17f6167aba3c074bdf6ea0ae1
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96394857"
---
# <a name="tenant-settings-guidance"></a>租用戶設定指引

本文旨在為負責在組織中設定 Power BI 環境的 Power BI 管理員提供指導。

特定的租用戶設定可能讓您組織面臨風險，我們針對這些設定提供指導，以協助改善 Power BI 體驗。 建議一律以符合您組織原則與程序的方式來設定租用戶。

[租用戶設定](../admin/service-admin-portal.md#tenant-settings)是在[管理員入口網站](https://app.powerbi.com/admin-portal/tenantSettings)中管理，並可由 [Power BI 服務管理員](../admin/service-admin-administering-power-bi-in-your-organization.md#administrator-roles-related-to-power-bi)進行設定。 有多項租用戶設定可以將功能限制於受限的使用者數量。 因此，建議您先熟悉設定，以規劃所需的安全性群組。 您可能會發現可將相同的安全性群組套用於多個設定。

## <a name="improve-power-bi-experience"></a>改善 Power BI 體驗

### <a name="publish-get-help-information"></a>發佈「取得說明」資訊

我們鼓勵您使用 [Microsoft Teams](/microsoftteams) 或其他共同作業平台來設定內部 Power BI 相關網站。 這些網站可用於儲存訓練文件、主持討論、提出授權要求或回應協助。

如果您這麼做，則建議接著為「整個組織」啟用 [發佈「取得協助」資訊] 設定。 此設定位於 [說明及支援設定] 群組中。 您可以為下列項目設定 URL：

- 訓練文件
- 討論論壇
- 授權要求
- 技術支援中心

這些 URL 會在 Power BI 說明功能表中提供連結。

> [!NOTE]
> 提供 **授權要求** URL，可防止個別使用者購買 Power BI Pro 授權。 而是改為將使用者導向至您的內部網站，並提供如何取得授權的相關資訊。 預設會啟用 [允許使用者試用 Power BI Pro] 設定，並將購買和試用體驗分開。 若要深入了解這些設定如何搭配使用，請參閱[允許使用者試用 Power BI Pro](../admin/service-admin-portal.md#allow-users-to-try-power-bi-pro)。
>
>

![Power B I Desktop 的螢幕擷取畫面，其中顯示 [說明及支援] 設定。](media/admin-tenant-settings/publish-get-help-information.png)

如需詳細資訊，請參閱[說明及支援設定](../admin/service-admin-portal.md#help-and-support-settings)。

## <a name="manage-risk"></a>管理風險
設定管理風險有助您在 Power BI 租用戶中建立治理原則。 不過，請注意，這些治理設定並不是安全性措施。 例如，若您停用 [匯出資料] 設定，Power BI 使用者介面即會移除此功能，以透過這種方式協助 Power BI 使用者在工作時遵循組織的治理原則，但這無法防止執意操作的使用者透過其他選項匯出資料。 從安全角度來看，不論 Power BI 使用者介面中是否提供這些功能，具有資料集讀取權限的 Power BI 使用者即有權查詢此資料集，並可以保存結果。
### <a name="receive-email-notification-service-outages-or-incidents"></a>接收服務中斷或事件的電子郵件通知

您可以選擇在租用戶受到服務中斷或事件的影響時收到電子郵件通知。 如此一來，您就可以主動回應事件。

建議您啟用 [接收電子郵件通知服務中斷或事件] 設定。 此設定位於 [說明及支援設定] 群組中。 指派一或多個「擁有郵件功能」的安全性群組。

![Power B I Desktop 的螢幕擷取畫面，其中顯示 [接收服務中斷或事件的電子郵件通知] 設定。](media/admin-tenant-settings/receive-email-notifications-for-service-outages-or-incidents.png)

### <a name="information-protection"></a>資訊保護

資訊保護可讓您在從 Power BI 服務匯出資料時實施保護設定 (例如加密或浮水印)。

有兩個與資訊保護相關的租用戶設定。 根據預設，這兩項設定已針對整個組織停用。

在您需要處理及保護敏感性資料時，建議您啟用這些設定。 如需詳細資訊，請參閱 [Power BI 中的資料保護](../admin/service-security-data-protection-overview.md)。

### <a name="create-workspaces"></a>建立工作區

您可以限制使用者建立工作區。 如此一來，您就可以管理在組織內建立的內容。

> [!NOTE]
> 目前，在舊工作區體驗與新工作區體驗之間有轉換週期。 此租用戶設定僅適用於新的體驗。

根據預設，[建立工作區] 設定已針對整個組織啟用。 此設定位於 [工作區設定] 群組中。

建議您指派一或多個安全性群組。 您可以授與「或拒絕」這些群組建立工作區的權限。

請務必在您的文件中包含指示，讓不具有工作區建立權限的使用者知道應如何要求新工作區。

![Power B I Desktop 的螢幕擷取畫面，其中顯示 [建立工作區] 設定。](media/admin-tenant-settings/create-workspaces.png)

### <a name="share-content-with-external-users"></a>與外部使用者共用內容

使用者可以與組織外部人員共用報表和儀表板。

根據預設，[與外部使用者共用內容] 設定已為整個組織啟用。 此設定位於 [匯出和共用設定] 群組中。

建議您指派一或多個安全性群組。 您可以授與「或拒絕」這些群組與外部使用者共用內容的權限。

![Power B I Desktop 的螢幕擷取畫面，其中顯示 [與外部使用者共用內容] 設定。](media/admin-tenant-settings/share-content-with-external-users.png)

### <a name="publish-to-web"></a>發行至 Web

[[發佈至 Web]](../collaborate-share/service-publish-to-web.md) 功能可讓您在 Web 上發佈公用報表。 如果使用不當，可能會有將機密資訊即時暴露於 Web 上的風險。

根據預設，[發佈至 Web] 設定已為整個組織啟用，但會限制非管理員使用者建立內嵌程式碼。 此設定位於 [匯出和共用設定] 群組中。

如果啟用此設定，建議您指派一或多個安全性群組。 您可以授與「或拒絕」這些群組發佈報表的權限。

此外，還有一個選項可以選擇內嵌程式碼的運作方式。 根據預設，此選項會設為 [只允許現有的程式碼]。 這表示系統會要求使用者與 Power BI 管理員連絡，才能建立內嵌程式碼。

![Power B I Desktop 的螢幕擷取畫面，其中顯示 [發佈至 Web] 設定。](media/admin-tenant-settings/publish-to-web.png)

我們也建議您定期檢閱[發佈至 Web 內嵌程式碼](https://app.powerbi.com/admin-portal/embedCodes)。 如果程式碼會導致發佈私人或機密資訊，請將其移除。

### <a name="export-data"></a>匯出資料

您可以限制使用者從儀表板磚或報表視覺效果匯出資料。

根據預設，[匯出資料] 設定已為整個組織啟用。 此設定位於 [匯出和共用設定] 群組中。

建議您指派一或多個安全性群組。 您可以授與「或拒絕」這些群組發佈報表的權限。

> [!IMPORTANT]
> 如果停用此設定，也會限制使用 [[使用 Excel 分析]](../collaborate-share/service-analyze-in-excel.md) 和 Power BI 服務 [[即時連線]](../connect-data/desktop-report-lifecycle-datasets.md#using-a-power-bi-service-live-connection-for-report-lifecycle-management) 功能。

![Power B I Desktop 的螢幕擷取畫面，其中顯示 [匯出資料] 設定。](media/admin-tenant-settings/export-data.png)

> [!NOTE]
> 如果要允許使用者匯出資料，您可以實施[資料保護](../admin/service-security-data-protection-overview.md)來增加一層防護。 設定後，即會禁止未經授權使用者匯出包含敏感度標籤的內容。

### <a name="allow-external-guest-users-to-edit-and-manage-content-in-the-organization"></a>允許外部來賓使用者編輯和管理組織中的內容

您可以允許外部來賓使用者編輯和管理 Power BI 內容。 如需詳細資訊，請參閱[使用 Azure AD B2B 將 Power BI 內容散發給外部來賓使用者](../admin/service-admin-azure-ad-b2b.md)。

根據預設，[允許外部來賓使用者編輯和管理組織中的內容] 設定已為整個組織停用。 此設定位於 [匯出和共用設定] 群組中。

如果需要授權外部使用者來編輯和管理內容，建議您指派一或多個安全性群組。 您可以授與「或拒絕」這些群組發佈報表的權限。

![Power B I Desktop 的螢幕擷取畫面，其中顯示 [允許外部來賓使用者編輯和管理組織中的內容] 設定。](media/admin-tenant-settings/allow-external-guest-users.png)

### <a name="developer-settings"></a>開發人員設定

[內嵌 Power BI 內容](../developer/embedded/embedding.md)有兩個相關的租用戶設定。 其中包括：

- 在應用程式中內嵌內容 (預設為啟用)
- 允許服務主體使用 Power BI API (預設為停用)

如果不想使用開發人員 API 來內嵌內容，建議您將其停用。 或至少設定要執行此作業的特定安全性群組。

![Power B I Desktop 的螢幕擷取畫面，其中顯示開發人員設定。](media/admin-tenant-settings/developer-settings.png)

## <a name="next-steps"></a>後續步驟

如需本文的詳細資訊，請參閱下列資源：

- [什麼是 Power BI 管理？](../admin/service-admin-administering-power-bi-in-your-organization.md)
- [在系統管理入口網站中管理 Power BI](../admin/service-admin-portal.md)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com)