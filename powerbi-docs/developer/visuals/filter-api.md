---
title: 取得更佳的內嵌式 BI 見解：Power BI 內嵌式分析中 Power BI 視覺效果的視覺效果篩選 API
description: 此文章討論 Power BI 視覺效果如何篩選其他視覺效果。 使用 Power BI 內嵌式分析，取得更佳的內嵌式 BI 見解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: c03c64c2835ff8bf0b0f1ad3bd555da94aaf3126
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888734"
---
# <a name="the-visual-filters-api-in-power-bi-visuals"></a>Power BI 視覺效果中的視覺效果篩選 API

視覺效果篩選 API 可讓您篩選 Power BI 視覺效果中的資料。 與其他選取項目的主要差異在於，儘管其他視覺效果支援醒目提示，其他視覺效果仍會以任何方式進行篩選。

若要啟用視覺效果的篩選，它應在 *capabilities.json* 程式碼的 `general` 區段中包含 `filter` 物件。

```json
"objects": {
        "general": {
            "displayName": "General",
            "displayNameKey": "formattingGeneral",
            "properties": {
                "filter": {
                    "type": {
                        "filter": true
                    }
                }
            }
        }
    }
```

視覺效果篩選 API 介面於 [powerbi-models](https://www.npmjs.com/package/powerbi-models) \(英文\) 套件中提供。 此套件也包含用來建立篩選執行個體的類別。

```cmd
npm install powerbi-models --save
```

如果您是使用該工具的較舊 (早於 3.x.x) 版本，您應該在視覺效果套件中包含 `powerbi-models`。 如需詳細資訊，請參閱[將進階篩選 API 新增至自訂視覺效果](https://github.com/Microsoft/powerbi-visuals-sampleslicer/blob/master/doc/AddingAdvancedFilterAPI.md) \(英文\) 這個簡短指南。

所有篩選都會擴充 `IFilter` 介面，如下列程式碼所示：

```typescript
export interface IFilter {
    $schema: string;
    target: IFilterTarget;
}
```
其中：
* `target` 是資料來源上的資料表資料行。

## <a name="the-basic-filter-api"></a>基本篩選 API

基本篩選介面如下列程式碼所示：

```typescript
export interface IBasicFilter extends IFilter {
    operator: BasicFilterOperators;
    values: (string | number | boolean)[];
}
```

其中：
* `operator` 是具有 *In*、*NotIn* 及 *All* 值的列舉。
* `values` 是條件的值。

基本篩選的範例：

```typescript
let basicFilter = {
    target: {
        column: "Col1"
    },
    operator: "In",
    values: [1,2,3]
}
```

此篩選準表示「給我 `col1` 等於 1、2 或 3 值的所有資料列」。

SQL 對等項目是：

```sql
SELECT * FROM table WHERE col1 IN ( 1 , 2 , 3 )
```

若要建立篩選，您可以使用 `powerbi-models` 中的 BasicFilter 類別。

如果您是使用較舊版本的工具，您應該使用 `window['powerbi-models']` 來在視窗物件中取得模型的執行個體，如下列程式碼所示：

```javascript
let categories: DataViewCategoricalColumn = this.dataView.categorical.categories[0];

let target: IFilterColumnTarget = {
    table: categories.source.queryName.substr(0, categories.source.queryName.indexOf('.')),
    column: categories.source.displayName
};

let values = [ 1, 2, 3 ];

let filter: IBasicFilter = new window['powerbi-models'].BasicFilter(target, "In", values);
```

視覺效果會在提供給建構函式中視覺效果的 IVisualHost 主機介面上，使用 applyJsonFilter() 方法來叫用篩選。

```typescript
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

## <a name="the-advanced-filter-api"></a>進階篩選 API

[進階篩選 API](https://github.com/Microsoft/powerbi-models) \(英文\) 可根據多個準則 (例如 *LessThan*、*Contains*、*Is*、*IsBlank* 等) 來啟用複雜的交叉視覺效果資料點選取及篩選查詢。

此篩選是在視覺效果 API 1.7.0 中引進。

進階篩選 API 也需要具有 `table` 和 `column` 名稱的 `target`。 但是進階篩選 API 運算子為 *And* 和 *Or*。 

此外，篩選會搭配介面使用條件，而不是值：

```typescript
interface IAdvancedFilterCondition {
    value: (string | number | boolean);
    operator: AdvancedFilterConditionOperators;
}
```

`operator` 參數的條件運算子為 *None*、*LessThan*、*LessThanOrEqual*、*GreaterThan*、*GreaterThanOrEqual*、*Contains*、*DoesNotContain*、*StartsWith*、*DoesNotStartWith*、*Is*、*IsNot*、*IsBlank*，以及 "IsNotBlank"。

```javascript
let categories: DataViewCategoricalColumn = this.dataView.categorical.categories[0];

let target: IFilterColumnTarget = {
    table: categories.source.queryName.substr(0, categories.source.queryName.indexOf('.')), // table
    column: categories.source.displayName // col1
};

let conditions: IAdvancedFilterCondition[] = [];

conditions.push({
    operator: "LessThan",
    value: 0
});

let filter: IAdvancedFilter = new window['powerbi-models'].AdvancedFilter(target, "And", conditions);

// invoke the filter
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

SQL 對等項目是：

```sql
SELECT * FROM table WHERE col1 < 0;
```

如需使用進階篩選 API 的完整範例程式碼，請移至 [Sampleslicer 視覺效果存放庫](https://github.com/Microsoft/powerbi-visuals-sampleslicer) \(英文\)。

## <a name="the-tuple-filter-api-multi-column-filter"></a>Tuple 篩選 API (多個資料行篩選)

Tuple 篩選 API 是在視覺效果 API 2.3.0 中引進。 Tuple 篩選 API 類似於基本篩選，但它可讓您針對數個資料行和資料表定義條件。

篩選介面如下列程式碼所示： 

```typescript
interface ITupleFilter extends IFilter {
    $schema: string;
    filterType: FilterType;
    operator: TupleFilterOperators;
    target: ITupleFilterTarget;
    values: TupleValueType[];
}
```

其中：
* `target` 是包含資料表名稱的資料行陣列：

    ```typescript
    declare type ITupleFilterTarget = IFilterTarget[];
    ```

  篩選可以處理來自不同資料表的資料行。

* `$schema` 是 https://powerbi.com/product/schema#tuple \(英文\)。

* `filterType` 是 *FilterType.Tuple*。

* `operator` 可允許僅在 *In* 運算子中使用。

* `values` 是值 Tuple 的陣列，其中每個 Tuple 都代表一個允許的目標資料行值組合。 

```typescript
declare type TupleValueType = ITupleElementValue[];

interface ITupleElementValue {
    value: PrimitiveValueType
}
```

完整範例：

```typescript
let target: ITupleFilterTarget = [
    {
        table: "DataTable",
        column: "Team"
    },
    {
        table: "DataTable",
        column: "Value"
    }
];

let values = [
    [
        // the first column combination value (or the column tuple/vector value) that the filter will pass through
        {
            value: "Team1" // the value for the `Team` column of the `DataTable` table
        },
        {
            value: 5 // the value for the `Value` column of the `DataTable` table
        }
    ],
    [
        // the second column combination value (or the column tuple/vector value) that the filter will pass through
        {
            value: "Team2" // the value for `Team` column of `DataTable` table
        },
        {
            value: 6 // the value for `Value` column of `DataTable` table
        }
    ]
];

let filter: ITupleFilter = {
    $schema: "https://powerbi.com/product/schema#tuple",
    filterType: FilterType.Tuple,
    operator: "In",
    target: target,
    values: values
}

// invoke the filter
visualHost.applyJsonFilter(filter, "general", "filter", FilterAction.merge);
```

> [!IMPORTANT]
> 資料行名稱和條件值會區分順序。

SQL 對等項目是：

```sql
SELECT * FROM DataTable WHERE ( Team = "Team1" AND Value = 5 ) OR ( Team = "Team2" AND Value = 6 );
```  

## <a name="restore-the-json-filter-from-the-data-view"></a>從資料檢視還原 JSON 篩選

從 API 2.2.0 版開始，您可以從 *VisualUpdateOptions* 還原 JSON 篩選，如下列程式碼所示：

```typescript
export interface VisualUpdateOptions extends extensibility.VisualUpdateOptions {
    viewport: IViewport;
    dataViews: DataView[];
    type: VisualUpdateType;
    viewMode?: ViewMode;
    editMode?: EditMode;
    operationKind?: VisualDataChangeOperationKind;
    jsonFilters?: IFilter[];
}
```

當您切換書籤時，Power BI 會呼叫視覺效果的 `update` 方法，然後視覺效果會取得相對應的 `filter` 物件。 如需詳細資訊，請參閱[新增 Power BI 視覺效果的書籤支援](bookmarks-support.md)。

### <a name="sample-json-filter"></a>範例 JSON 篩選

下圖顯示一些範例 JSON 篩選程式碼：

![JSON 篩選程式碼](media/filter-api/json-filter.png)

### <a name="clear-the-json-filter"></a>清除 JSON 篩選

篩選 API 會將篩選的 `null` 值接受為「重設」或「清除」。

```typescript
// invoke the filter
visualHost.applyJsonFilter(null, "general", "filter", FilterAction.merge);
```
