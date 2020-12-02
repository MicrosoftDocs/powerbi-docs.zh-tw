---
title: 在 Microsoft Teams 中內嵌 Power BI 報表
description: 您可在 Microsoft Teams 的頻道和聊天中，輕鬆內嵌互動式 Power BI 報表。 .
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 09/21/2020
ms.openlocfilehash: 36973d52f94b806db860b739a84f0c94b2a8945d
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411854"
---
# <a name="embed-power-bi-content-in-microsoft-teams"></a>在 Microsoft Teams 中內嵌 Power BI 內容

您可在 Microsoft Teams 的頻道和聊天中，輕鬆內嵌互動式 Power BI 報表。 

## <a name="requirements"></a>需求

若要使用 Microsoft Teams 中的 [Power BI] 索引標籤，請確定下列項目：

- Microsoft Teams 具有 [Power BI] 索引標籤。
- 若要在具備 [Power BI] 索引標籤的 Microsoft Teams 中新增報表，則在裝載報表的工作區中至少必須具備「檢閱者」角色。 如需不同角色的相關資訊，請參閱[新工作區中的角色](service-new-workspaces.md#roles-in-the-new-workspaces)。
- 若要在 Microsoft Teams 的 [Power BI] 索引標籤中查看報表，使用者必須具備檢視報表的權限。
- 使用者必須是有權存取頻道和聊天的 Microsoft Teams 使用者。

如需 Power BI 和 Microsoft Teams 如何共同合作的背景資訊，包括其他需求，請參閱[在 Microsoft Teams 中使用 Power BI 共同作業](service-embed-report-microsoft-teams.md)。

## <a name="embed-a-report-in-microsoft-teams"></a>在 Microsoft Teams 中內嵌報表

遵循下列方式將報表內嵌到 Microsoft Teams 頻道或聊天中。

1. 在 Microsoft Teams 中開啟頻道或聊天，然後選取 **+** 圖示。

    ![將索引標籤新增到頻道或聊天的螢幕擷取畫面。](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-add.png)

1. 選取 [Power BI] 索引標籤。

    ![Microsoft Teams 索引標籤清單的螢幕擷取畫面，其中顯示 Power BI。](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-tab.png)

1. 使用提供的選項，從工作區或 Power BI 應用程式中選取報表。

    ![Microsoft Teams 設定其 [Power BI] 索引標籤的螢幕擷取畫面。](media/service-embed-report-microsoft-teams/service-embed-report-microsoft-teams-tab-settings.png)

1. 索引標籤名稱會自動更新以符合報表名稱的名稱，但您可以變更該名稱。

1. 選取 [儲存]。

### <a name="reports-you-can-embed-on-the-power-bi-tab"></a>可在 [Power BI] 索引標籤上內嵌的報表

您可以在 [Power BI] 索引標籤中，內嵌下列類型的報表：

- 互動式報表與編頁報表。
- [我的工作區] (全新的工作區體驗) 及傳統工作區中的報表。
- Power BI 應用程式中的報表。

## <a name="start-a-conversation"></a>開始交談

當您將 Power BI 報表索引標籤新增至 Microsoft Teams 時，Microsoft Teams 會自動為報表建立索引標籤交談。

- 選取右上角的 [顯示索引標籤交談] 圖示。

    ![顯示索引標籤交談圖示的螢幕擷取畫面。](media/service-embed-report-microsoft-teams/power-bi-teams-conversation-icon.png)

    第一個註解是報表的連結。 該 Microsoft Teams 頻道中的每個人都可以在交談中查看及討論報表。

    ![索引標籤交談的螢幕擷取畫面。](media/service-embed-report-microsoft-teams/power-bi-teams-conversation-tab.png)

## <a name="known-issues-and-limitations"></a>已知的問題及限制

- 在 Microsoft Teams 中，當您從 Power BI 報表中的視覺效果匯出資料時，資料會自動儲存到您的 [下載] 資料夾。 資料會儲存成名為「data (n).xlsx」的 Excel 檔案，其中，n 是您將資料匯出至相同資料夾的次數。
- Power BI 儀表板無法內嵌在 Microsoft Teams 的 [Power BI] 索引標籤中。
- Microsoft Teams 的 [Power BI] 索引標籤不支援 [URL 篩選](service-url-filters.md)。
- 在國家雲端中，無法使用新的 [Power BI] 索引標籤。 較舊的版本可能無法在 Power BI 應用程式中支援全新的工作區體驗或報表。
- 儲存索引標籤之後，即無法透過索引標籤設定來變更索引標籤名稱。 請使用 [重新命名] 選項加以變更。
- 如有其他問題，請參閱＜在 Microsoft Teams 中共同作業＞一文中的[＜已知問題和限制＞](service-collaborate-microsoft-teams.md#known-issues-and-limitations)一節。

## <a name="next-steps"></a>後續步驟

- [在 Microsoft Teams 中使用 Power BI 共同作業](service-collaborate-microsoft-teams.md)

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)。
