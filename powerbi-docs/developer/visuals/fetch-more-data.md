---
title: 從 Power BI 擷取更多資料
description: 此文章討論如何為 Power BI 視覺效果啟用大型資料集的分段擷取。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: b8be5b68603f818e26e7f731e4f163bc626b5053
ms.sourcegitcommit: 132b3f6ba6d2b1948ddc15969d64cf629f7fb280
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94483688"
---
# <a name="fetch-more-data-from-power-bi"></a>從 Power BI 擷取更多資料

此文章討論如何使用 `fetchMoreData` 方法載入更多資料，以克服 30-KB 資料點的硬性限制。 此方法以區塊形式提供資料。 若要改善效能，您可以將區塊大小設定為適合您使用案例的大小。

## <a name="limitations-of-fetchmoredata"></a>fetchMoreData 的限制

* 視窗大小範圍為 2 到 30,000。
* 資料檢視資料列總數最多為 1,048,576 個資料列。
* 在區段匯總模式中，資料檢視記憶體大小最多為 100 MB。

## <a name="enable-a-segmented-fetch-of-large-datasets"></a>啟用大型資料集的分段擷取

若為 `dataview` 區段模式，您可以在視覺效果的 *capabilities.json* 檔案中，為所需的 `dataViewMapping` 定義 `dataReductionAlgorithm` 的視窗大小。 `count` 會決定視窗大小，這會限制每個更新中可以附加至 `dataview` 的新資料列數目。

在 *capabilities.json* 檔案中新增下列程式碼：

```typescript
"dataViewMappings": [
    {
        "table": {
            "rows": {
                "for": {
                    "in": "values"
                },
                "dataReductionAlgorithm": {
                    "window": {
                        "count": 100
                    }
                }
            }
    }
]
```

新的區段會附加至現有 `dataview`，並提供給視覺效果作為 `update` 呼叫。

## <a name="usage-in-the-power-bi-visual"></a>Power BI 視覺效果中的使用方式

在 Power BI 中，您可以在預設的區段匯總模式或累加式更新模式中使用 `fetchMoreData`。 

### <a name="using-segments-aggregation-mode-default"></a>使用區段匯總模式 (預設)

在此模式中，提供給視覺效果的資料檢視會包含先前 `fetchMoreData requests` 所累積的所有資料。 因此，資料檢視大小理論上會隨著每次更新而增加。 例如，如果預期共有 100,000 個資料列，且視窗大小設定為 10,000，則第一次更新資料檢視應包含 10,000 個資料列，第二次更新資料檢視應包含 20,000 個資料列，依此類推。

藉由使用 `aggregateSegments = true` 呼叫 `fetchMoreData`，即可選取此模式。

您可以檢查 `dataView.metadata.segment` 的存在與否，以判斷資料是否存在：

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

您也可以藉由檢查 `options.operationKind`，來查看其是否為第一次更新或後續更新。 在下列程式碼中，`VisualDataChangeOperationKind.Create` 表示第一區段，而 `VisualDataChangeOperationKind.Append` 表示後續區段。

如需範例實作，請參閱下列程式碼片段：

```typescript
// CV update implementation
public update(options: VisualUpdateOptions) {
    // indicates this is the first segment of new data.
    if (options.operationKind == VisualDataChangeOperationKind.Create) {

    }

    // on second or subsequent segments:
    if (options.operationKind == VisualDataChangeOperationKind.Append) {

    }

    // complete update implementation
}
```

您可以從 UI 事件處理常式叫用 `fetchMoreData` 方法，如下所示：

```typescript
btn_click(){
{
    // check if more data is expected for the current data view
    if (dataView.metadata.segment) {
        //request for more data if available; as a response, Power BI will call update method
        let request_accepted: bool = this.host.fetchMoreData(true);
        // handle rejection
        if (!request_accepted) {
            // for example, when the 100 MB limit has been reached
        }
    }
}
```

作為呼叫 `this.host.fetchMoreData` 方法的回應，Power BI 會使用新資料區段呼叫視覺效果的 `update` 方法。

> [!NOTE]
> 為了避免用戶端記憶體限制，Power BI 目前將擷取資料總數限制為 100 MB。 當 `fetchMoreData()` 傳回 `false` 時，則表示已達到此限制。

### <a name="using-incremental-updates-mode"></a>使用累加式更新模式

使用此模式時，提供給視覺效果的資料檢視僅包含累加資料。 因此，資料檢視大小並不會超過已定義的視窗大小。 例如，如果預期共有 101,000 個資料列，且視窗大小設定為 10,000，則視覺效果會取得 10 次資料檢視大小為 10,000 的更新，以及一次資料檢視大小為 1,000 的更新。

藉由使用 `aggregateSegments = false` 呼叫 `fetchMoreData`，即可選取此模式。

您可以檢查 `dataView.metadata.segment` 的存在與否，以判斷資料是否存在：

```typescript
    public update(options: VisualUpdateOptions) {
        const dataView = options.dataViews[0];
        console.log(dataView.metadata.segment);
        // output: __proto__: Object
    }
```

您也可以藉由檢查 `options.operationKind`，來查看其是否為第一次更新或後續更新。 在下列程式碼中，`VisualDataChangeOperationKind.Create` 參考第一個區段，而 `VisualDataChangeOperationKind.Segment` 參考後續區段。

如需範例實作，請參閱下列程式碼片段：

```typescript
// CV update implementation
public update(options: VisualUpdateOptions) {
    // indicates this is the first segment of new data.
    if (options.operationKind == VisualDataChangeOperationKind.Create) {

    }

    // on second or subsequent segments:
    if (options.operationKind == VisualDataChangeOperationKind.Segment) {
        
    }

    // skip overlapping rows 
    const rowOffset = (dataView.table['lastMergeIndex'] === undefined) ? 0 : dataView.table['lastMergeIndex'] + 1;

    // Process incoming data
    for (var i = rowOffset; i < dataView.table.rows.length; i++) {
        var val = <number>(dataView.table.rows[i][0]); // Pick first column               
            
     }
     
    // complete update implementation
}
```

您可以從 UI 事件處理常式叫用 `fetchMoreData` 方法，如下所示：

```typescript
btn_click(){
{
    // check if more data is expected for the current data view
    if (dataView.metadata.segment) {
        //request for more data if available; as a response, Power BI will call update method
        let request_accepted: bool = this.host.fetchMoreData(false);
        // handle rejection
        if (!request_accepted) {
            // for example, when the 100 MB limit has been reached
        }
    }
}
```

作為呼叫 `this.host.fetchMoreData` 方法的回應，Power BI 會使用新資料區段呼叫視覺效果的 `update` 方法。

> [!NOTE]
> 儘管不同更新之間的資料檢視資料大部分為專有資料，但連續的資料檢視之間仍會有部分重疊。
> 若為資料表與類別資料對應，則前 N 個資料檢視資料列通常會包含從上一個資料檢視所複製而來的資料。
> N 值可以透過下列方式判斷：`(dataView.table['lastMergeIndex'] === undefined) ? 0 : dataView.table['lastMergeIndex'] + 1`