---
title: 取得更佳的內嵌式 BI 見解：Power BI 內嵌式分析中的 Power BI 視覺效果 [分析] 窗格
description: 此文章說明如何在 Power BI 視覺效果中建立動態參考線。 使用 Power BI 內嵌式分析，取得更佳的內嵌式 BI 見解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: dd3d3a8a3553dc9c3ab8c2867c6fee319ad74a07
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97889148"
---
# <a name="the-analytics-pane-in-power-bi-visuals"></a>Power BI 視覺效果中的 [分析] 窗格

[分析] 窗格是在 2018 年 11 月[引入原生視覺效果](../../transform-model/desktop-analytics-pane.md)。
此文章討論使用 API v2.5.0 的 Power BI 視覺效果如何能在 [分析] 窗格中呈現及管理其屬性。

![[分析] 窗格](media/analytics-pane/visualization-pane-analytics-tab.png)

## <a name="manage-the-analytics-pane"></a>管理 [分析] 窗格

如同您在 [[格式] 窗格](./custom-visual-develop-tutorial-format-options.md) \(部分機器翻譯\) 中管理屬性，您藉由在物件的 *capabilities.json* 檔案中定義視覺效果，來管理 [分析] 窗格。

[分析] 窗格的差異如下：

* 在物件的定義底下，您新增值為 2 的 **objectCategory** 欄位。

    > [!NOTE]
    > 選擇性的 `objectCategory` 欄位是在 API 2.5.0 中引進的。 它會定義物件所控制的視覺效果層面 (1 = 格式、2 = 分析)。 `Formatting` 是用於外觀及操作、色彩、軸、標籤等元素。 `Analytics` 是用於預測、趨勢線、參考線和圖形等元素。
    >
    > 如果未指定值，`objectCategory` 預設為 "Formatting"。

* 物件必須有下列兩個屬性：
    * `bool` 類型的 `show`，其預設值為 `false`。
    * 型別 `displayName` 的 `text`。 您選擇的預設值會變成執行個體的初始顯示名稱。

```json
{
  "objects": {
    "YourAnalyticsPropertiesCard": {
      "displayName": "Your analytics properties card's name",
      "objectCategory": 2,
      "properties": {
        "show": {
          "type": {
            "bool": true
          }
        },
        "displayName": {
          "type": {
            "text": true
          }
        },
      ... //any other properties for your Analytics card
      }
    }
  ...
  }
}
```

您可以使用定義 **Format** 物件的相同方式來定義其他屬性。 如同在 [格式] 窗格中，您也可以列舉物件。

## <a name="known-limitations-and-issues-of-the-analytics-pane"></a>[分析] 窗格的已知限制和問題

* [分析] 窗格尚未支援多個執行個體。 物件只能有靜態 (即 "selector": null) 的[選取器](https://microsoft.github.io/PowerBI-visuals/docs/concepts/objects-and-properties/#selector)，且 Power BI 視覺效果不能有使用者定義的多個卡片執行個體。
* 類型為 `integer` 的屬性不會正確顯示。 因應措施是改為使用 `numeric` 類型。

> [!NOTE]
> * [分析] 窗格僅適用於新增資訊或闡明所呈現資訊的物件 (例如，說明重要趨勢的動態參考線)。
> * 控制視覺效果外觀及操作 (也就是格式設定) 的任何選項，都應該限制在 [格式化] 窗格中。