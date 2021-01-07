---
title: 直接從 Power BI 服務在 Microsoft Teams 中聊天
description: 您可從 Power BI 服務，直接將 Power BI 儀表板和報表共用到 Microsoft Teams。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
LocalizationGroup: Share your work
ms.date: 01/04/2020
ms.openlocfilehash: 63ea4772610bd7112823f38c66abced1f0654b77
ms.sourcegitcommit: 932f6856849c39e34229dc9a49fb9379c56a888a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97926932"
---
# <a name="chat-in-microsoft-teams-directly-from-the-power-bi-service"></a>直接從 Power BI 服務在 Microsoft Teams 中聊天

您可以直接從 Power BI 服務，與 Microsoft Teams 聊聊有關 Power BI 儀表板、報表與視覺效果的內容。 當您在 Power BI 服務中檢視報表與儀表板時，使用 [在 Teams 中聊天] 功能可快速開始交談。

## <a name="requirements"></a>需求

若要在 Power BI 中使用 [在 Teams 中聊天] 功能，請確定您的 Power BI 系統管理員尚未在 Power BI 管理入口網站中停用 [共用到 Teams] 租用戶設定。 此設定可供組織隱藏 [在 Teams 中聊天] 按鈕。 如需詳細資料，請參閱 [Power BI 管理入口網站](../admin/service-admin-portal.md#share-to-teams)一文。

如需 Power BI 和 Microsoft Teams 如何共同合作的背景資訊，包括其他需求，請參閱[在 Microsoft Teams 中使用 Power BI 共同作業](service-collaborate-microsoft-teams.md)。

## <a name="chat-about-power-bi-content-in-microsoft-teams"></a>在 Microsoft Teams 中聊聊有關 Power BI 的內容

請遵循下列步驟，以共用 Power BI 服務中報表、儀表板和視覺效果的連結，並聊聊有關 Microsoft Teams 頻道與聊天的內容。

1. 請選擇下列選項的其中一個：

   * 儀表板或報表動作列中的 [在 Teams 中聊天]：

       ![動作列中 [在 Teams 中聊天] 按鈕的螢幕擷取畫面。](media/service-share-report-teams/service-teams-share-to-teams-action-bar-button.png)
    
   * 單一視覺效果操作功能表中的 [在 Teams 中聊天]：
    
      ![視覺效果操作功能表中 [在 Teams 中聊天] 按鈕的螢幕擷取畫面。](media/service-share-report-teams/service-teams-share-to-teams-visual-context-menu.png)

1. 在 [共用至 Microsoft Teams] 對話方塊中，選取您想要傳送連結的小組或頻道。 您可以視需要輸入訊息。 系統可能要求您先登入 Microsoft Teams。

    ![包含資訊和訊息之 [共用到 Microsoft Teams] 對話方塊的螢幕擷取畫面。](media/service-share-report-teams/service-teams-share-to-teams-dialog.png)

1. 選取 [共用] 以傳送連結。
    
1. 此連結會新增至現有的交談，或啟動新的交談。

    ![包含 Power BI 項目連結的 Microsoft Teams 交談其螢幕擷取畫面。](media/service-share-report-teams/service-teams-share-to-teams-deep-link.png)

1. 選取該連結，即會在 Power BI 服務中開啟該項目。

1. 如果您使用適用於特定視覺效果的關聯式功能表，則當報表開啟時，就會將視覺效果反白顯示。

    ![醒目提示特定視覺效果的已開啟 Power BI 報表其螢幕擷取畫面。](media/service-share-report-teams/service-teams-share-to-teams-spotlight-visual.png)


## <a name="known-issues-and-limitations"></a>已知的問題及限制

- 沒有 Power BI 授權或存取報表權限的使用者會看到「內容無法使用」訊息。
- 若瀏覽器使用嚴格的隱私權設定，[在 Teams 中聊天] 按鈕可能就無法正常運作。 如果對話方塊未正確開啟，請使用 [遇到問題了嗎?嘗試在新視窗中開啟] 選項。
- [在 Teams 中聊天] 不包含連結預覽。
- 連結預覽與 [在 Teams 中聊天] 不會將檢視項目的權限授與使用者。 權限必須個別管理。
- 當報表作者將視覺效果的 [更多選項] 設定為 [關閉] 時，即無法使用視覺效果操作功能表中的 [在 Teams 中聊天] 按鈕。
- 如有其他問題，請參閱＜在 Microsoft Teams 中共同作業＞一文中的[＜已知問題和限制＞](service-collaborate-microsoft-teams.md#known-issues-and-limitations)一節。

## <a name="next-steps"></a>後續步驟

- [在 Microsoft Teams 中使用 Power BI 共同作業](service-collaborate-microsoft-teams.md)

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)。
