---
title: 在 Microsoft Teams 中使用 Power BI 共同作業
description: 隨著分散式工作人員成為常態，越來越多組織依賴 Microsoft Teams，以啟用遠端作業，並讓員工保持同步。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 12/14/2020
ms.openlocfilehash: 7c8fa59521be1cfc8bb25fb04c3904f257fb62be
ms.sourcegitcommit: 932f6856849c39e34229dc9a49fb9379c56a888a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97926699"
---
# <a name="collaborate-in-microsoft-teams-with-power-bi"></a>在 Microsoft Teams 中使用 Power BI 共同作業

隨著分散式工作人員成為常態，越來越多組織依賴 Microsoft Teams，以啟用遠端作業，並讓員工保持同步。本文會介紹數種可與 Microsoft Teams 頻道和聊天室中的互動式 Power BI 內容共用和共同作業的選項。 

- 使用 Microsoft Teams 的 [Power BI] 索引標籤，即可在 Microsoft Teams 頻道和聊天中[內嵌互動式報表](service-embed-report-microsoft-teams.md)。 [Power BI] 索引標籤可協助同事尋找小組資料，並討論小組頻道內的資料。 
- 當將報表、儀表板和應用程式的連結貼到 Microsoft Teams 訊息方塊時，請建立[連結預覽](service-teams-link-preview.md)。 連結預覽會顯示連結的相關資訊。 
- 在 Power BI 服務中檢視報表與儀表板時，使用[在 Microsoft Team 中聊天](service-share-report-teams.md)，即可在 Microsoft Teams 中快速開始交談。
- 可使用 [Microsoft Teams 中的 Power BI 應用程式](service-microsoft-teams-app.md)將基本的 Power BI 服務整體帶入 Microsoft Teams。
 
:::image type="content" source="media/service-collaborate-microsoft-teams/power-bi-embed-teams-report.png" alt-text="內嵌在 Microsoft Teams 頻道中的 Power B I 報表螢幕擷取畫面。":::

## <a name="requirements"></a>需求

一般而言，若要讓 Power BI 在 Microsoft Teams 中工作，請確定下列項目：

- 您擁有 Power BI Pro 授權，或報表包含於具備 Power BI 授權的 [Power BI Premium 容量 (EM 或 P SKU)](../admin/service-premium-what-is.md) 中。
- 使用者必須登入 Power BI 服務，才能啟用 Power BI 授權。
- 使用者符合使用 Microsoft Teams 中 [Power BI] 索引標籤的需求。

## <a name="grant-access-to-reports"></a>授與報告存取權

在 Microsoft Teams 中內嵌報表，或傳送項目的連結，不會自動為使用者授與檢視報表的權限。 您需要[允許使用者檢視 Power BI 中的報表](service-share-dashboards.md)。 您可以為小組使用 Microsoft 365 群組，讓此過程變得更簡單。

> [!IMPORTANT]
> 請務必檢閱可以看到 Power BI 服務內報表的成員，並將存取權授與未列出的成員。

確保小組中每位成員都有權存取報表的方式之一是將報表放在單一工作區中，並為小組授與 Microsoft 365 群組的存取權。

## <a name="share-with-external-users"></a>與外部使用者共用

您可整合 Teams 中的 Power BI 報表，並與外部使用者共用。 以下是要遵循的步驟。

1.  您需邀請外部使用者到組織，且外部使用者需接受邀請。 如需詳細資料，請參閱[使用 Azure Active Directory B2B 將 Power BI 內容散發給外部來賓使用者](../guidance/whitepaper-azure-b2b-power-bi.md)。
2.  將報表權限授與外部使用者。 建議個別指派權限。
3.  確定外部使用者已取得 Power BI 授權。 如果內容是在 Premium 容量中，則使用者只需要免費授權。 如果不是，則使用者可[註冊 Power BI Pro 的個人免費試用版](../fundamentals/service-self-service-signup-for-power-bi.md#sign-up-for-an-individual-trial-of-power-bi-pro)。

## <a name="known-issues-and-limitations"></a>已知的問題及限制

- Power BI 不支援 Microsoft Teams 所支援的相同當地語系化語言。 因此，您可能不會在內嵌報表中看到適當的當地語系化。
- Power BI 儀表板無法內嵌於 Microsoft Teams 的 [Power BI] 索引標籤中。
- 沒有 Power BI 授權或存取報表權限的使用者會看到「內容無法使用」訊息。
- 如果您使用 Internet Explorer 10，可能就會遇到問題。 <!--You can look at the [browsers support for Power BI](../fundamentals/power-bi-browsers.md) and for [Microsoft 365](https://products.office.com/office-system-requirements#Browsers-section). -->
- Microsoft Teams 的 [Power BI] 索引標籤不支援 [URL 篩選](service-url-filters.md)。
- 在國家雲端中，無法使用新的 [Power BI] 索引標籤。 較舊的版本可能無法在 Power BI 應用程式中支援全新的工作區體驗或報表。
- 儲存索引標籤之後，即無法透過索引標籤設定來變更索引標籤名稱。 請使用 [重新命名] 選項加以變更。
- 連結預覽服務不支援單一登入。
- 連結預覽在會議聊天或私人頻道中無法使用。

## <a name="microsoft-power-platform-in-microsoft-teams"></a>Microsoft Teams 中的 Microsoft Power Platform

其他 Microsoft Power Platform 應用程式也會與 Microsoft Teams 整合。

- [Power Platform 管理員體驗](/power-platform/admin/about-teams-environment) (英文)
- [Power Automate](/power-automate/teams/overview)
- [Power Apps](/powerapps/teams/overview)
- [Power Virtual Agents](/power-virtual-agents/)

## <a name="next-steps"></a>後續步驟

- [在 Microsoft Teams 中內嵌 Power BI 內容](service-embed-report-microsoft-teams.md)
- [在 Microsoft Teams 中取得 Power BI 連結預覽](service-teams-link-preview.md)
- [直接從 Power BI 服務在 Microsoft Teams 中聊天](service-share-report-teams.md)

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)。
