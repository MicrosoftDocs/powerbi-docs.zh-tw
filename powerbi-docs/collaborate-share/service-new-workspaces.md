---
title: 在 Power BI 中組織新工作區中的工作
description: 了解新的工作區，這些工作區是為了提供重要計量給組織而建立的儀表板和報告集合。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: conceptual
ms.date: 10/21/2020
ms.custom: contperfq4
LocalizationGroup: Share your work
ms.openlocfilehash: 43af5a2ea924ababdba7b328b814045b75be5316
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411739"
---
# <a name="organize-work-in-the-new-workspaces-in-power-bi"></a>在 Power BI 中組織新工作區中的工作

「工作區」是要與同事共同作業來建立儀表板、報表、資料集和編頁報表集合的地方。 新的工作區體驗可協助您更妥善管理內容的存取。 本文描述新的工作區，以及它們與傳統工作區有何不同。  如同傳統工作區一樣，您仍然使用它們來建立和散發應用程式。 

準備好建立新工作區了嗎？ 請閱讀[建立新的工作區體驗](service-create-the-new-workspaces.md)。

:::image type="content" source="media/service-new-workspaces/power-bi-workspace-opportunity.png" alt-text="Power BI 新工作區體驗":::

新的升級工作區可以與現有的傳統工作區共存。 新的工作區體驗是預設工作區類型。 您仍可基於 Microsoft 365 群組視需要建立並使用[傳統工作區](service-create-workspaces.md)。 準備好移轉傳統工作區了嗎？ 如需詳細資訊，請參閱[將傳統工作區升級至 Power BI 中的新工作區](service-upgrade-workspaces.md)。

## <a name="new-and-classic-workspace-differences"></a>新工作區和傳統工作區的差異

我們使用新的工作區重新設計了一些功能。 以下為主要差異。

- **建立新工作區不會如傳統工作區一般建立 Microsoft 365 群組**。 所有新工作區管理都是在 Power BI 中進行，而不是 Office 365。 如有需要，仍可透過 Microsoft 365 群組來管理使用者對內容的存取權。 您只需在工作區存取清單中新增 Microsoft 365 群組即可。
- **使用更精細的工作區角色**，在新工作區中進行更有彈性的權限管理。  在傳統工作區中，您只能將個人新增至成員和系統管理員清單。 
- **將使用者群組指派給工作區角色**：在新工作區中，您可將多個 Active Directory 安全性群組、通訊群組清單或 Microsoft 365 群組新增至這些角色，以更輕鬆地進行使用者管理。 
- **連絡人清單**：在新的工作區中，您可以指定接收工作區活動相關通知的人員。
- **建立範本應用程式**：您只能在新的工作區中建立「範本應用程式」。 範本應用程式是您可以散發給組織外部客戶的應用程式。 然後，這些客戶可以使用您的範本應用程式連線到自己的資料。 深入了解[範本應用程式](../connect-data/service-template-apps-overview.md)。
- **共用資料集**：若要在特定工作區之外共用資料集，您必須將包含資料集的報表儲存到其中一個新的工作區。 您無法從傳統工作區共用資料集。 深入了解[共用資料集](../connect-data/service-datasets-across-workspaces.md)。
- **組織內容套件**：您會在傳統工作區中建立及使用組織內容套件。 您無法在新工作區中建立或取用它們。 應用程式和範本應用程式會取代新工作區中的組織內容套件。

本文會更詳細地說明這些功能。

> [!NOTE]
> Power BI 會繼續列出您所屬的所有 Microsoft 365 群組。 這可避免變更現有的工作流程。

### <a name="features-that-work-differently"></a>運作方式不同的功能

在新工作區中，某些功能的運作方式不同。 這些差異是根據我們從客戶處收到的意見反應刻意進行的。 這些差異可讓您以更有彈性的方式來與工作區共同作業。

- **授權強制執行**：將報表發佈至新工作區體驗，會強制執行現有的授權規則。 在新工作區中共同作業或與 Power BI 服務中其他使用者共用內容的使用者需要 Power BI Pro 授權。 如果使用者沒有 Pro 授權，即會看到錯誤：「只有具備 Power BI Pro 授權的使用者才能發佈至這個工作區」。
- **[成員可再次共用] 設定**：新工作區中的參與者角色會取代傳統工作區中的 [成員可再次共用] 設定。
- **唯讀工作區**：新工作區中的檢視人員角色會取代將傳統工作區的唯讀存取權授與使用者。 檢視人員角色允許您對新工作區中的內容具有類似的唯讀存取權。
- 如果工作區位於 Power BI Premium 容量中，則 **沒有 Pro 授權的使用者** 可存取新工作區，但使用者必須具有檢視人員角色。
- **允許使用者匯出資料**：如果具有檢視人員角色的使用者對該工作區中的資料集具有建置權限，則即使是在新工作區中具有檢視人員角色的使用者也可匯出資料。 深入閱讀[資料集的建置權限](../connect-data/service-datasets-build-permissions.md)。
- 新工作區中沒有 [離開工作區] 按鈕。

### <a name="workspace-contact-list"></a>工作區連絡人清單

新的 [連絡人清單] 功能可讓您指定哪些使用者會收到新工作區中發生問題的通知。 根據預設，新工作區中指定為工作區系統管理員的任何使用者或群組都會收到通知。 您可以新增至該清單。 連絡人清單中的使用者或群組也會列在新工作區的使用者介面 (UI) 中，工作區使用者就知道要聯絡的連絡人。 

閱讀[如何建立工作區連絡人清單](service-create-the-new-workspaces.md#create-a-contact-list)。

### <a name="workspace-onedrive"></a>工作區 OneDrive

如先前所述，當您建立其中一個新工作區時，Power BI 不會在幕後建立 Microsoft 365 群組。 儘管如此，讓 OneDrive 與新工作區建立關聯也會很有用。 您可以利用新工作區中的工作區 OneDrive 功能來設定 Microsoft 365 群組，其 SharePoint 文件庫的檔案儲存體可供工作區使用者使用。 您會在 Power BI 外部建立群組。
 
Power BI 不會針對具有新工作區存取權的使用者或群組，在 Microsoft 365 群組成員資格與權限之間進行同步處理。 您可以同步處理：透過相同的 Microsoft 365 群組來管理工作區存取，而您會在此設定中設定該群組的檔案儲存體。 

閱讀[如何設定工作區 OneDrive](service-create-the-new-workspaces.md#set-a-workspace-onedrive)。  

## <a name="roles-in-the-new-workspaces"></a>新工作區中的角色

角色能讓您管理哪些人員可在工作區中做什麼，因此小組可以共同作業。 新的工作區可供將角色指派給個人和使用者群組：安全性群組、Microsoft 365 群組，以及通訊群組清單。 

若要授與新工作區的存取權，請將使用者群組或個人指派至其中一個工作區角色：系統管理員、成員、參與者或檢視者。 使用者群組中的每個人，都會取得已指派的角色。 如果某個人屬於數個使用者群組，則其會取得所指派角色提供的最高層級權限。 如果巢狀處理使用者群組，則所有包含的使用者都具有權限。 除了檢視和互動功能以外，所有這些功能都需要 Power BI Pro 授權。 如需詳細資訊，請閱讀本文中的[授權](#licenses)。

[!INCLUDE [power-bi-workspace-roles-table](../includes/power-bi-workspace-roles-table.md)]

> [!NOTE]
> - 您可以將使用者指派給角色 (不論是單獨或是在群組中)，即使他們無法使用角色也一樣。 換句話說，您可以將沒有 Power BI Pro 授權的使用者指派給需要授權的角色。 如需詳細資料，請參閱本文中的[授權](#licenses)。
> - 若要強制執行[資料列層級安全性 (RLS)](../admin/service-admin-rls.md)，讓使用者瀏覽工作區中的內容，請使用檢視者角色。 您也可以強制執行 RLS，而不需要提供新工作區的存取權。 將[應用程式發佈](service-create-distribute-apps.md)並加以散發給這些使用者，或使用[「共用」來散發內容](service-share-dashboards.md)給他們。

## <a name="licensing-and-administering"></a>授權與系統管理

### <a name="licenses"></a>授權
如果其中一個新的工作區在共用容量中，您新增至其中的每個人員都需要 Power BI Pro 授權。 這些使用者可以在新工作區的儀表板和報告上共同作業。 如果您想要將內容散發給貴組織內的其他人，可以將 Power BI Pro 授權指派給這些使用者，或將工作區置於 Power BI Premium 容量中。

當新工作區在 Power BI Premium 容量中時，具有檢視者角色的使用者可以存取工作區，即使他們沒有 Power BI Pro 授權也一樣。 不過，如果您將較高的角色 (例如，管理員、成員或參與者) 指派給這些使用者，系統就會在使用者嘗試存取工作區時，提示啟動 Pro 試用版。 如果您想要沒有 Pro 授權的使用者使用檢視人員角色，請確定他們不會同時具有其他工作區角色，不論是個人或做為使用者群組的一部分。

將報告發佈至新工作區體驗會更嚴格地強制執行現有的授權規則。 如果您嘗試在沒有 Pro 授權的情況下，從 Power BI Desktop 或其他用戶端工具進行發佈，則您會看到「只有具備 Power BI Pro 授權的使用者可以發佈到此工作區」錯誤。

> [!NOTE]
> Power BI 美國政府版本並未以「免費」授權形式提供。 如需授權詳細資訊，請參閱[適用於美國政府客戶的 Power BI](../admin/service-govus-overview.md)。

### <a name="guest-users"></a>來賓使用者

根據預設，[Azure AD B2B 來賓使用者](../admin/service-admin-azure-ad-b2b.md)無法存取工作區。 Power BI 系統管理員可以[允許外部來賓使用者編輯及管理組織中的內容](../admin/service-admin-azure-ad-b2b.md#guest-users-who-can-edit-and-manage-content)。 已啟用的來賓使用者可以存取其具有權限的工作區。

### <a name="administering-new-workspace-experience-workspaces"></a>管理新的工作區體驗工作區

對於新工作區體驗工作區的管理位於 Power BI 管理入口網站中。 Power BI 管理員會決定組織中的哪些人可以建立工作區和發佈應用程式。 在＜管理入口網站＞一文中，了解如何[管理使用者建立工作區的能力](../admin/service-admin-portal.md#create-the-new-workspaces)。 

管理員也可以查看組織中所有工作區的狀態。 管理員可以管理、復原，甚至刪除工作區。 在＜管理入口網站＞一文中，了解如何[管理工作區本身](../admin/service-admin-portal.md#workspaces)。

### <a name="auditing"></a>稽核

Power BI 會稽核新工作區體驗工作區的下列活動。

| 易記名稱 | 作業名稱 |
|---|---|
| 已建立 Power BI 資料夾 | CreateFolder |
| 已刪除 Power BI 資料夾 | DeleteFolder |
| 已更新 Power BI 資料夾 | UpdateFolder |
| 已更新 Power BI 資料夾存取權| UpdateFolderAccess |

深入閱讀 [Power BI 稽核](../admin/service-admin-auditing.md)。

## <a name="limitations-and-considerations"></a>限制與考量

要注意的限制：

- 工作區可包含最多 1,000 個資料集，或每個資料集 1,000 個報表。 
- 擁有 Power BI Pro 授權的人員可以是工作區數目上限為 1,000 的成員。
- 不支援 Power BI Publisher for Excel。

## <a name="frequently-asked-questions"></a>常見問題集

**新的工作區體驗是否會影響現有內容的連結？**

不會。 新的工作區體驗不會影響傳統工作區中現有項目的連結。 正式運作 (GA) 的新工作區體驗會變更您建立的預設工作區，但不會變更現有工作區。 

**現有的工作區是否升級至正式運作的新工作區體驗？**

不會。 新的工作區體驗 GA 只會將預設工作區類型變更為新的工作區體驗。 基於 Microsoft 365 群組的現有傳統工作區維持不變。

**是否仍會針對 Microsoft 365 群組自動建立工作區？**

是。 由於我們同時支援這兩種類型的工作區，因此，會繼續在工作區清單中列出您有權存取的所有 Microsoft 365 群組。

## <a name="next-steps"></a>後續步驟

* [在 Power BI 中建立新的工作區](service-create-the-new-workspaces.md)
* [建立傳統工作區](service-create-workspaces.md)
* [在 Power BI 中安裝和使用應用程式](service-create-distribute-apps.md)
* 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)

