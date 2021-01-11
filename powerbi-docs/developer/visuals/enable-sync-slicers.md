---
title: 在 Power BI 內嵌式分析的 Power BI 視覺效果中，啟用用於取得更佳內嵌 BI 見解的同步交叉分析篩選器功能
description: 此文章說明如何將同步交叉分析篩選器功能新增至 Power BI 視覺效果。 使用 Power BI 內嵌式分析，以便取得更佳的內嵌 BI 見解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: bd69e05bba3e9449f9fb6f07bd9625dfb1ea0c08
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97885261"
---
# <a name="sync-slicers-in-power-bi-visuals"></a>Power BI 中的同步交叉分析篩選器

若要支援[同步交叉分析篩選器](../../visuals/power-bi-visualization-slicers.md)功能，您的自訂交叉分析篩選器視覺效果必須使用 API 1.13.0 版或更新版本。

此外，您也必須啟用 *capabilities.json* 檔案中的選項，如下列程式碼所示：

```json
{
    ...
    "supportsHighlight": true,
    "suppressDefaultTitle": true,
    "supportsSynchronizingFilterState": true,
    "sorting": {
        "default": {}
    }
}
```

更新 *capabilities.json* 檔案之後，當您選取您的自訂交叉分析篩選器視覺效果時，就能檢視 [同步交叉分析篩選器] 選項窗格。

> [!NOTE]
> 同步交叉分析篩選器功能不支援多個欄位。 如果交叉分析篩選器有多個欄位 (**Category** 或 **Measure**)，系統會停用該功能。

![[同步交叉分析篩選器] 窗格](media/enable-sync-slicers/sync-slicers-panel.png)

在 [同步交叉分析篩選器] 窗格中，您可以看到交叉分析篩選器可見度及其篩選可以套用至數個報表頁面。