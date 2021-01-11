---
title: 取得更佳的內嵌式 BI 見解：在 Power BI 內嵌式分析中，為 Power BI 視覺效果新增書籤支援
description: Power BI 視覺效果得以處理。 使用 Power BI 內嵌式分析，取得更佳的內嵌式 BI 見解。 書籤切換
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: 6a4f0e8ad8890e85db54e8d77a2ec19bb0d02ea8
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97889102"
---
# <a name="add-bookmark-support-for-power-bi-visuals"></a>新增 Power BI 視覺效果的書籤支援

您可以使用 Power BI 報表書籤來擷取已設定的報表頁面檢視、視覺效果的選取項目狀態和篩選狀態。 但它需要從 Power BI 視覺效果執行其他動作，以支援書籤並正確地回應變更。

如需書籤的詳細資訊，請參閱[在 Power BI 中使用書籤來共用深入解析並建立故事](../../create-reports/desktop-bookmarks.md) \(部分機器翻譯\)。

## <a name="report-bookmarks-support-in-your-visual"></a>視覺效果中的報表書籤支援

如果您的視覺效果與其他視覺效果互動、選取資料點或篩選其他視覺效果，則必須從屬性還原狀態。

## <a name="add-report-bookmarks-support"></a>新增報表書籤支援

1. 安裝 (或更新) 必要的公用程式，[powerbi-visuals-utils-interactivityutils](https://github.com/Microsoft/PowerBI-visuals-utils-interactivityutils/) \(英文\) 3.0.0 版或更新版本。 它包含要使用狀態選取項目或篩選進行操作的其他類別。 篩選視覺效果和任何使用 `InteractivityService` 的視覺效果都需要它。

2. 將視覺效果 API 更新為 1.11.0 版，以在 `SelectionManager` 的執行個體中使用 `registerOnSelectCallback`。 使用一般 `SelectionManager` 而不是 `InteractivityService` 的非篩選視覺效果需要這麼做。

### <a name="how-power-bi-visuals-interact-with-power-bi-in-report-bookmarks"></a>Power BI 視覺效果如何在報表書籤中與 Power BI 互動

讓我們考慮下列情節：您想在報表頁面中建立數個書籤，且每個書籤中的選取項目狀態都不同。

首先，您會選取視覺效果中的資料點。 視覺效果可藉由將選取項目傳遞至主機來與 Power BI 和其他視覺效果互動。 然後，您在 [書籤] 窗格中選取 [新增]，Power BI 就會將目前的選取項目儲存為新書籤。

當您變更選取項目並新增書籤時，就會重複發生此狀況。 建立書籤後，您可以在書籤之間切換。

當您選取書籤時，Power BI 會還原已儲存的篩選或選取項目狀態，並將它傳遞至視覺效果。 其他視覺效果會根據儲存在書籤中的狀態進行醒目提示或篩選。 Power BI 主機負責此動作。 您的視覺效果負責正確反映新選取項目狀態 (例如，變更所呈現資料點的色彩)。

新的選取項目狀態會透過 `update` 方法傳達給視覺效果。 `options` 引數包含特殊屬性：`options.jsonFilters`。 它是 JSONFilter 屬性，可以包含 `Advanced Filter` 和 `Tuple Filter`。

視覺效果應還原篩選值，以顯示所選取書籤的視覺效果狀態。 或者，如果視覺效果僅使用選取項目，您可以使用 ISelectionManager 的特殊回呼函式呼叫已註冊 `registerOnSelectCallback` 方法。

### <a name="visuals-with-selection"></a>含有選取項目的視覺效果

如果您的視覺效果使用[選取項目](https://github.com/Microsoft/PowerBI-visuals/blob/master/Tutorial/Selection.md) \(英文\) 與其他視覺效果互動，您可以透過下列兩種方式之一來新增書簽：

* 如果視覺效果尚未使用 [InteractivityService](https://github.com/microsoft/powerbi-visuals-utils-interactivityutils/blob/master/src/interactivityService.ts) \(英文\)，您可以使用 `FilterManager.restoreSelectionIds` 方法。

* 如果視覺效果已經使用 [InteractivityService](https://github.com/microsoft/powerbi-visuals-utils-interactivityutils/blob/master/src/interactivityService.ts) \(英文\) 來管理選取項目，您應該使用 `InteractivityService` 執行個體中的 `applySelectionFromFilter` 方法。

#### <a name="use-iselectionmanagerregisteronselectcallback"></a>使用 ISelectionManager.registerOnSelectCallback

當您選取書籤時，Power BI 會使用對應的選取項目來呼叫視覺效果 `callback` 方法。 

```typescript
this.selectionManager.registerOnSelectCallback(
    (ids: ISelectionId[]) => {
        //called when a selection was set by Power BI
    });
);
```

假設您的視覺效果中有一個資料點是在 [visualTransform](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts#L74) 方法中建立的。

而且 `datapoints` 看起來像這樣：

```typescript
visualDataPoints.push({
    category: categorical.categories[0].values[i],
    color: getCategoricalObjectValue<Fill>(categorical.categories[0], i, 'colorSelector', 'fill', defaultColor).solid.color,
    selectionId: host.createSelectionIdBuilder()
        .withCategory(categorical.categories[0], i)
        .createSelectionId(),
    selected: false
});
```

您現在使用 `visualDataPoints` 作為資料點，並將 `ids` 陣列傳遞至 `callback` 函式。

此時，視覺效果應該將 `ISelectionId[]` 陣列與 `visualDataPoints` 陣列中的選取項目進行比較，並將對應的資料點標記為已選取。

```typescript
this.selectionManager.registerOnSelectCallback(
    (ids: ISelectionId[]) => {
        visualDataPoints.forEach(dataPoint => {
            ids.forEach(bookmarkSelection => {
                if (bookmarkSelection.equals(dataPoint.selectionId)) {
                    dataPoint.selected = true;
                }
            });
        });
    });
);
```

在您更新資料點之後，它們會反映儲存在 `filter` 物件中的目前選取項目狀態。 然後，在呈現資料點時，自訂視覺效果的選取項目狀態會符合書籤的狀態。

### <a name="use-interactivityservice-for-control-selections-in-the-visual"></a>使用 InteractivityService 來控制視覺效果中的選取項目

如果您的視覺效果使用 `InteractivityService`，則不需要執行任何其他動作來支援視覺效果中的書籤。

當您選取書簽時，公用程式會處理視覺效果的選取狀態。

### <a name="visuals-with-a-filter"></a>含有篩選的視覺效果

假設視覺效果會建立依日期範圍的資料篩選。 您使用 `startDate` 和 `endDate` 作為範圍的開始和結束。

視覺效果會建立一個進階篩選並呼叫主機方法 `applyJsonFilter`，以依據相關條件來篩選資料。

目標是用於篩選的資料表。

```typescript
import { AdvancedFilter } from "powerbi-models";

const filter: IAdvancedFilter = new AdvancedFilter(
    target,
    "And",
    {
        operator: "GreaterThanOrEqual",
        value: startDate
            ? startDate.toJSON()
            : null
    },
    {
        operator: "LessThanOrEqual",
        value: endDate
            ? endDate.toJSON()
            : null
    });

this.host.applyJsonFilter(
    filter,
    "general",
    "filter",
    (startDate && endDate)
        ? FilterAction.merge
        : FilterAction.remove
);
```

每當您選取書籤時，自訂視覺效果就會收到 `update` 呼叫。

自訂視覺效果應檢查物件中的篩選：

```typescript
const filter: IAdvancedFilter = FilterManager.restoreFilter(
    && options.jsonFilters
    && options.jsonFilters[0] as any
) as IAdvancedFilter;
```

如果 `filter` 物件不是 Null，則視覺效果應從物件還原篩選條件：

```typescript
const jsonFilters: AdvancedFilter = this.options.jsonFilters as AdvancedFilter[];

if (jsonFilters
    && jsonFilters[0]
    && jsonFilters[0].conditions
    && jsonFilters[0].conditions[0]
    && jsonFilters[0].conditions[1]
) {
    const startDate: Date = new Date(`${jsonFilters[0].conditions[0].value}`);
    const endDate: Date = new Date(`${jsonFilters[0].conditions[1].value}`);

    // apply restored conditions
} else {
    // apply default settings
}
```

之後，視覺效果應變更其內部狀態，以反映目前的條件。 內部狀態包括資料點和視覺效果物件 (線條、矩形等等)。

> [!IMPORTANT]
> 在報表書籤案例中，視覺效果不應呼叫 `applyJsonFilter` 來篩選其他視覺效果。 它們將會已經由 Power BI 篩選。

時間軸交叉分析篩選器視覺效果會將範圍選取器變更為對應的資料範圍。

如需詳細資訊，請參閱[時間軸交叉分析篩選器存放庫](https://github.com/Microsoft/powerbi-visuals-timeline/commit/606f1152f59f82b5b5a367ff3b117372d129e597?diff=unified#diff-b6ef9a9ac3a3225f8bd0de84bee0a0df)。

### <a name="filter-the-state-to-save-visual-properties-in-bookmarks"></a>篩選狀態以在書籤中儲存視覺效果屬性

`filterState` 屬性可讓屬性成為篩選的一部分。 視覺效果可以在書籤中儲存各種值。

若要將屬性值儲存為篩選狀態，請在 *capabilities.json* 檔案中，將物件屬性標示為 `"filterState": true`。

例如，時間軸交叉分析篩選器會將 `Granularity` 屬性值儲存在篩選中。 它能讓目前的細微性，隨著您變更書籤而變更。

如需詳細資訊，請參閱[時間軸交叉分析篩選器存放庫](https://github.com/microsoft/powerbi-visuals-timeline/commit/8b7d82dd23cd2bd71817f1bc5d1e1732347a185e#diff-290828b604cfa62f1cb310f2e90c52fdR334)。