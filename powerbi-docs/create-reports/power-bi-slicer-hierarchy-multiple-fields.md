---
title: 新增多個欄位到階層交叉分析篩選器
description: 了解如何建立在階層中包含多個欄位的階層交叉分析篩選器。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 07/06/2020
LocalizationGroup: Create reports
ms.openlocfilehash: cadb8d45af40c91e7008e771f2a52ef2ea508341
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96393454"
---
# <a name="add-multiple-fields-to-a-hierarchy-slicer"></a>新增多個欄位到階層交叉分析篩選器

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

若要在單一交叉分析篩選器中篩選多個相關欄位，您可以透過建置所謂的「階層」交叉分析篩選器來完成此動作。 您可以在 Power BI Desktop 或 Power BI 服務中建立這些交叉分析篩選器。

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy.png" alt-text="Power BI 中階層交叉分析篩選器的螢幕擷取畫面。":::

當您將多個欄位新增至交叉分析篩選器時，該交叉分析篩選器預設會顯示箭號，或在可展開以顯示下一個層級項目的項目旁邊顯示「＞形箭號」。

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-arrow.png" alt-text="Power BI 中階層交叉分析篩選器下拉式清單的螢幕擷取畫面。":::
 
 
當您為項目選取一個或多個子系時，您會看到最上層項目的半選取圓形。
 
:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-semi-selected.png" alt-text="Power BI 中單選階層交叉分析篩選器的螢幕擷取畫面。":::

## <a name="format-the-slicer"></a>設定交叉分析篩選器的格式

交叉分析篩選器的行為尚未變更。 您也可以將交叉分析篩選器設定為您所要的風格。 例如，您可以將其設定為單選模式。 或者，您可以在清單與下拉式清單之間切換。 

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-dropdown.png" alt-text="階層交叉分析篩選器已格式化為下拉式交叉分析篩選器的螢幕擷取畫面。":::

您也可以進行下列格式變更。

### <a name="change-the-title"></a>變更標題

您可以編輯任何交叉分析篩選器的標題，但是此功能特別適用於階層交叉分析篩選器。 根據預設，階層交叉分析篩選器的名稱是階層中欄位名稱的清單。

在此範例中，交叉分析篩選器的標題會列出階層中的三個欄位：類型、平台與名稱。

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-title.png" alt-text="具有 [類型]、[平台] 與 [名稱] 欄位之階層交叉分析篩選器的螢幕擷取畫面。":::

若要變更名稱，請選取交叉分析篩選器，然後選取 [格式] 窗格。 在 [交叉分析篩選器標頭] 下，您會在 [標題文字] 方塊中看見交叉分析篩選器的目前名稱。

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-edit-title.png" alt-text="具有目前標題之 [格式] 窗格的螢幕擷取畫面。":::

選取文字並加入新的名稱。

:::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-new-title.png" alt-text="階層交叉分析篩選器之新標題的螢幕擷取畫面。":::


### <a name="change-the-expandcollapse-icon"></a>變更展開/摺疊圖示

階層交叉分析篩選器有一些其他格式設定選項。 您可以將展開/摺疊圖示從預設箭頭變更為加號/減號或插入號。

1. 選取交叉分析篩選器，然後選取 [格式]。
1. 展開 [項目]，然後選取 [展開/摺疊圖示]。
1. 選擇 [＞形箭號]、[加號/減號] 或 [插入號]。
 
    :::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-hierarchy-caret.png" alt-text="為階層交叉分析篩選器選取展開/摺疊圖示的螢幕擷取畫面。":::
 
### <a name="change-the-indentation"></a>變更縮排

如果您報表上的空間緊湊，您可以減少子項目縮排量。 根據預設，縮排為 15 個像素，但您可以增加或減少縮排。 

1. 選取交叉分析篩選器，然後選取 [格式]。
1. 展開 [項目]，然後將 [逐步的配置縮排] 往較小或較大的方向拖曳。 您也可以直接在方塊中輸入數字。

    :::image type="content" source="media/power-bi-slicer-hierarchy-multiple-fields/power-bi-slicer-indentation.png" alt-text="設定階層交叉分析篩選器縮排的螢幕擷取畫面。":::

## <a name="next-steps"></a>後續步驟

- [Power BI 中的交叉分析篩選器](../visuals/power-bi-visualization-slicers.md)
- 有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)