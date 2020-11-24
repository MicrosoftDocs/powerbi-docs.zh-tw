---
title: 在 Power BI 中使用相對時間交叉分析篩選器或篩選條件
description: 深入了解如何在 Power BI 中使用交叉分析篩選器或篩選條件來限制相對時間範圍。
author: maggiesMSFT
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 07/06/2020
ms.author: maggies
LocalizationGroup: Create reports
ms.openlocfilehash: a8268af76472c91474f2f67bc256fcc0ddcc9768
ms.sourcegitcommit: bd133cb1fcbf4f6f89066165ce065b8df2b47664
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94669216"
---
# <a name="use-a-relative-time-slicer-and-filter-in-power-bi"></a>在 Power BI 中使用相對時間交叉分析篩選器與篩選條件

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

隨著快速重新整理案例的出現，以較小時間範圍篩選的能力相當實用。 利用相對時間交叉分析篩選器或相對時間篩選條件，可將時間篩選條件套用到資料模型中的任何日期或時間資料行。 例如，您可使用相對時間交叉分析篩選器來只顯示過去一分鐘或一個小時內的影片檢視。 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time.gif" alt-text="相對時間範例的螢幕擷取畫面。":::

您不需要搭配[自動頁面重新整理](../create-reports/desktop-automatic-page-refresh.md)功能來使用此功能。 但是，許多相對時間案例相當適合與自動頁面重新整理功能搭配使用。  

> [!NOTE]
> 當在頁面或報表層級套用相對時間篩選條件或交叉分析篩選器時，所有該頁面上視覺效果或報表都會使用共用「錨點」  時間來篩選到完全一致的相同時間範圍。 因為視覺效果的執行時間可能會有些許不同，這個共用錨點時間可確保視覺效果在頁面或整個報表上都會同步。 如需詳細資訊，請閱讀本文的[錨點時間](#understanding-anchor-time)。

## <a name="create-a-relative-time-slicer-or-filter"></a>建立相對時間交叉分析篩選器或篩選條件

啟用此功能後，即可將日期或時間欄位拖放到交叉分析篩選器的欄位區，或是 [篩選條件] 窗格中的拖放區域。 

### <a name="create-a-slicer"></a>建立交叉分析篩選器

1. 將日期或時間欄位拖曳到畫布。

2. 選取 [交叉分析篩選器] 視覺效果類型。

    :::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-create-slicer.png" alt-text="建立時間交叉分析篩選器的螢幕擷取畫面。":::

### <a name="create-a-filter"></a>建立篩選
 
- 將日期或時間欄位拖曳到 [此視覺效果]、[此頁面] 或 [所有頁面] 的 [篩選條件] 窗格。

### <a name="set-relative-time"></a>設定相對時間 

接下來，您會將篩選條件類型變更為 [相對時間]。

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-set.png" alt-text="變更為相對時間的螢幕擷取畫面。":::
 
以下是其在交叉分析篩選器中的外觀：

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-slicer.png" alt-text="交叉分析篩選器中相對時間的螢幕擷取畫面。":::

以下是其在篩選條件卡中的外觀： 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-filter.png" alt-text="篩選中相對時間的螢幕擷取畫面。":::
 
使用這個新的篩選條件類型，即可根據 [最後]、[下一個] 或 [此時間期間] 篩選： 

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-last-next.png" alt-text="選擇 [最後]、[下一個] 或 [此時間期間] 的螢幕擷取畫面。":::
 
您可使用整數和時間單位來指定時間範圍：[分鐘] 或 [小時]。
 
:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-minutes-hours.png" alt-text="選擇分鐘或小時的螢幕擷取畫面。":::

若需要節省畫布上的空間，則亦可在 [篩選條件] 窗格中將相對時間篩選條件作為篩選條件卡建立。

:::image type="content" source="media/slicer-filter-relative-time/power-bi-relative-time-set-filter.png" alt-text="在篩選條件中改為設定相對時間的螢幕擷取畫面。":::
 
## <a name="understanding-anchor-time"></a>了解錨點時間

當篩選條件套用到頁面或是報表層級時，該頁面或報表上的所有視覺效果都會同步到相同且一致的時間範圍。 這些查詢其發行時間會相對於稱為「錨點時間」的時間。 錨點時間會自動在下列情況下重新整理：

- 初始頁面載入。
- 手動重新整理。
- 自動或偵測到變更的頁面重新整理。
- 模型產生變更。

### <a name="anchor-time-exceptions"></a>錨點時間例外狀況

- 直到將問與答視覺效果轉換成標準視覺效果為止，使用問與答視覺效果的相對時間篩選都不會相對於此錨點時間。 但是，其他 AI 視覺效果 (例如關鍵影響因素和分解樹狀結構) 都會與錨點時間同步。 
- 此外，除非有相對時間篩選條件，否則相對日期篩選條件或交叉分析篩選器也不會與錨點時間相對。 如果相對日期和相對時間篩選條件都位於相同頁面上，則相對日期篩選條件會遵循錨點時間。

## <a name="limitations-and-considerations"></a>限制與考量

目前相對時間交叉分析篩選器和篩選條件都適用下列限制與考量。

- **時區考量**：Power BI 中的資料模型不包含時區資訊。 模型可以儲存時間，但無法指出所在時區。 交叉分析篩選器和篩選條件一律以 UTC 時區為基礎。 若在報表中設定篩選條件，並將其傳送給不同時區的同事，則兩人會看到相同的資料。 除非您或您的同事位於 UTC 時區，否則雙方都必須將時間位移納入考量。 使用查詢編輯器將在本地時區中擷取到的資料轉換成 UTC。
- Power BI Desktop、Power BI 服務、Power BI Embedded 和 Power BI 行動應用程式都支援這個新的篩選條件類型。 不過，其不支援 [發行至 Web]。

- **查詢快取**：我們會使用用戶端快取。 假設您指定「最後 1 分鐘」，然後指定「最後 5 分鐘」，最後又回到「最後 1 分鐘」。 此時，除非重新整理頁面或頁面自動重新整理，否則會看到與其第一次執行時相同的結果。

## <a name="next-steps"></a>後續步驟

- [在 Power BI 中使用相對日期交叉分析篩選器和篩選條件](../visuals/desktop-slicer-filter-date-range.md)
- [Power BI 中的交叉分析篩選器](../visuals/power-bi-visualization-slicers.md)
