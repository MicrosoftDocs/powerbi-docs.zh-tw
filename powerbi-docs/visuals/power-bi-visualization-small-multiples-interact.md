---
title: 'Power BI (preview 中的小型倍數互動) '
description: 本文說明如何與小倍數或 trellising 互動。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 02/05/2021
LocalizationGroup: Visualizations
ms.openlocfilehash: 6d700d4a4bb7453f7630c76c5a3f265ee022e02a
ms.sourcegitcommit: f17acb16018752c234db6bff1f51f5130be12c58
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/06/2021
ms.locfileid: "99617307"
---
# <a name="interact-with-small-multiples-in-power-bi-preview"></a>Power BI (preview 中的小型倍數互動) 

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

小倍數（或 trellising）會將視覺效果分割成多個版本。 本文說明如何充分利用與其互動。

:::image type="content" source="media/power-bi-visualization-small-multiples/small-mulitple-sales-category-region.png" alt-text="類別和區域小型倍數的螢幕擷取畫面。":::

想要建立小型倍數嗎？ 請參閱 [Power BI (preview) 建立小型倍數 ](power-bi-visualization-small-multiples.md)。

## <a name="scroll-in-a-small-multiple"></a>在小倍數中滾動

小倍數可能包含多個可以容納在方格中的個別圖表。 如果是，您可以向下滾動以查看您的其餘類別。

針對具有許多類別目錄的類別 X 軸，您也會看到該軸每個複本的捲軸。 在該軸上滾動會將它們全部移動在一起。 如果您是使用滾輪，請按住 Shift 鍵以滾動類別軸。

## <a name="select-data-to-cross-highlight"></a>選取要交叉醒目提示的資料

您可以選取視覺效果的不同部分，以選取不同的資料子集。

### <a name="select-data-points"></a>選取資料點

將滑鼠停留在其中一個倍數的資料點上方，以顯示該倍數中的工具提示。 您也會看到折線圖的 X 軸上的輔助線。 選取該資料點以交叉醒目提示其他視覺效果（依軸值和小倍數類別），並將其他倍數變暗。

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-select-data-point.png" alt-text="選取小倍數中的資料點。":::

### <a name="select-a-categorical-axis-value"></a>選取類別目錄軸值

選取類別標籤，以交叉醒目提示該軸值的其他視覺效果。

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-select-category-axis.png" alt-text="選取小倍數中的類別目錄軸。":::

### <a name="select-a-title"></a>選取標題

選取多個專案的標題，以交叉醒目提示該 subheader.aboutdocs 中類別的其他視覺效果。

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-select-title.png" alt-text="選取小倍數中的標題。":::

### <a name="legend"></a>圖例

選取圖例類別以交叉醒目提示其他視覺效果，並交叉醒目提示其他倍數。

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-select-legend.png" alt-text="在小倍數的圖例中選取專案。":::


## <a name="sort"></a>Sort

使用新的排序功能，您可以一次排序視覺效果的多個層面。 依類別和每個倍數中的軸排序。 

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-sort.png" alt-text="排序小倍數。":::

## <a name="next-steps"></a>下一步

[在 Power BI (preview 中建立小型倍數) ](power-bi-visualization-small-multiples.md)
