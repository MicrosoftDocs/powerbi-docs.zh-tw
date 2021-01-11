---
title: 在 Power BI 內嵌式分析中，將色彩新增至您的 Power BI 視覺效果，以取得更佳的內嵌 BI 見解
description: 此文章說明如何將色彩新增至您的 Power BI 視覺效果，以及如何處理具有色彩之視覺效果的資料點。 使用 Power BI 內嵌式分析，以便取得更佳的內嵌 BI 見解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 03/27/2020
ms.openlocfilehash: e6b6fb1dbc1397b93ac12692c8610e6f36d0b8bf
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887975"
---
# <a name="add-colors-to-your-power-bi-visuals"></a>將色彩新增至您的 Power BI 視覺效果

此文章說明如何將色彩新增至您的視覺效果，以及如何處理色彩視覺效果的資料點。

`IVisualHost` 將色彩公開為其服務之一。
此文章中的範例程式碼會修改 [SampleBarChart 視覺效果](https://github.com/microsoft/PowerBI-visuals-sampleBarChart) \(英文\)。
如需原始程式碼，請參閱 [barChart.ts](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts) \(英文\)。

若要開始建立視覺效果，請參閱[開發 Power BI 圓形卡片視覺效果](develop-circle-card.md)。

## <a name="add-color-to-data-points"></a>將色彩新增至資料點

不同的色彩代表每個資料點。
將色彩新增至 `BarChartDataPoint` 介面，如下列範例所示：

```typescript
/**
 * Interface for BarChart data points.
 *
 * @interface
 * @property {number} value    - Data value for point.
 * @property {string} category - Corresponding category of data value.
 * @property {string} color    - Color corresponding to data point.
 */
interface BarChartDataPoint {
    value: number;
    category: string;
    color: string;
};
```

## <a name="use-the-color-palette-service"></a>使用調色盤服務

`colorPalette` 服務會管理視覺效果中所使用的色彩。
`IVisualHost` 上提供服務的執行個體。

在 `update` 方法中加以定義。

```typescript
constructor(options: VisualConstructorOptions) {
        this.host = options.host; // host: IVisualHost
        ...
    }

public update(options: VisualUpdateOptions) {

    let colorPalette: IColorPalette = host.colorPalette;
    ...
}
```

## <a name="assigning-color-to-data-points"></a>將色彩指派給資料點

接下來，指定 `dataPoints`。
在此範例中，每個 `dataPoints` 都包含值、類別與色彩。
`dataPoints` 也可以包含其他屬性。

在 `SampleBarChart` 中，`visualTransform` 方法會封裝 `dataPoints` 計算。
該方法是 [橫條圖] 檢視模型的一部分。
因為該方法會逐一查看 `visualTransform` 中的 `dataPoints` 計算，因此是指派色彩的理想位置，如下列程式碼所示：

```typescript

public update(options: VisualUpdateOptions) {
    ....
    let viewModel: BarChartViewModel = visualTransform(options, this.host);
    ....
}

function visualTransform(options: VisualUpdateOptions, host: IVisualHost): BarChartViewModel {
    let colorPalette: IColorPalette = host.colorPalette; // host: IVisualHost
    for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
        barChartDataPoints.push({
            category: category.values[i],
            value: dataValue.values[i],
            color: colorPalette.getColor(category.values[i]).value,
        });
    }
}
```

然後在 `update` 方法內的 [d3](https://d3js.org/) 選取項目 `barSelection` 上套用來自 `dataPoints` 的資料：

```typescript
// This code is actual for d3 v5
// in d3 v5 for this case we should use merge() after enter() and apply changes on barSelectionMerged
this.barSelection = this.barContainer
    .selectAll('.bar')
    .data(this.barDataPoints);

const barSelectionMerged = this.barSelection
    .enter()
    .append('rect')
    .merge(<any>this.barSelection);

barSelectionMerged.classed('bar', true);

barSelectionMerged
.attr("width", xScale.bandwidth())
.attr("height", d => height - yScale(<number>d.value))
.attr("y", d => yScale(<number>d.value))
.attr("x", d => xScale(d.category))
.style("fill", (dataPoint: BarChartDataPoint) => dataPoint.color)
.style("stroke", (dataPoint: BarChartDataPoint) => dataPoint.strokeColor)
.style("stroke-width", (dataPoint: BarChartDataPoint) => `${dataPoint.strokeWidth}px`);

this.barSelection
    .exit()
    .remove();
```

## <a name="next-steps"></a>後續步驟

若要深入了解 Power BI 視覺效果，請參閱 [Power BI 視覺效果的功能和屬性](capabilities.md)。

若要深入了解如何開發 Power BI 視覺效果，請參閱[如何針對 Power BI 視覺效果進行偵錯](visuals-how-to-debug.md)與[疑難排解 Power BI 視覺效果](power-bi-custom-visuals-troubleshoot.md)。
