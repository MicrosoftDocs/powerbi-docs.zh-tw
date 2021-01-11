---
title: Power BI 內嵌式分析中，用於取得更佳內嵌 BI 見解的 supportsMultiVisualSelection 功能
description: 此文章說明如何使用 Power BI 視覺效果中的 supportsMultiVisualSelection 功能與其需求。 使用 Power BI 內嵌式分析，以便取得更佳的內嵌 BI 見解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 04/30/2020
ms.openlocfilehash: 9e6b17a4576f2354a5cbecc0c3a965a5611784ee
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887929"
---
# <a name="use-the-supportsmultivisualselection-feature"></a>使用 supportsMultiVisualSelection 功能

`supportsMultiVisualSelection` 功能可讓您在報表的多個視覺效果中使用選取項目。

## <a name="example"></a>範例

在具有多個視覺效果的報表中，選取兩個值，將那些值套用至其他視覺效果。 例如，在[零售分析範例](../../create-reports/sample-retail-analysis.md)中，在一個視覺效果中選取 [Fashions Direct]。 選取 Ctrl，然後選取另一個視覺效果中的 [Jan]。 在報表中，您的選取項目會套用至其他支援此功能使用方式的視覺效果。 其他視覺效果現在的範圍是 **Fashions Direct** 與 **Jan**。

## <a name="requirements"></a>需求

此功能需要 API 3.2.0 版或更高版本。

您無法將此功能套用至影像視覺效果。 您無法將其套用至一些進階視覺效果，例如重要驅動程式、分解樹狀結構、問與答視覺效果、文字方塊和量測計圖表。

## <a name="usage"></a>使用量

若要使用 `supportsMultiVisualSelection` 功能，請將下列程式碼加入至您視覺效果的 `capabilities.json` 檔案。

```json
    {   
            ...
        "supportsMultiVisualSelection": true
            ...
    }
```

## <a name="next-steps"></a>後續步驟

若要了解 Power BI 概念，請參閱 [Power BI 中的視覺效果](power-bi-visuals-concept.md)。

若要嘗試進行 Power BI 開發，請參閱[開發 Power BI 圓形卡片](develop-circle-card.md)。
