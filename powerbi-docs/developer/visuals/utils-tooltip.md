---
title: 取得更佳的內嵌式 BI 見解：Power BI 內嵌式分析中 Power BI 視覺效果的工具提示公用程式使用簡介
description: 本文描述如何使用工具提示公用程式，來簡化 Power BI 視覺效果的工具提示自訂流程。 使用 Power BI 內嵌式分析，取得更佳的內嵌式 BI 見解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 02/14/2020
ms.openlocfilehash: b2ddc85d9ba2530dc394b4106d72b4af702bd9b4
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888642"
---
# <a name="tooltip-utils"></a>工具提示公用程式
此文章將協助您安裝、匯入及使用工具提示公用程式。 此公用程式適用於 Power BI 視覺效果中的任何工具提示自訂。

## <a name="requirements"></a>規格需求
若要使用該套件，您應該具有下列項目：
* [node.js](https://nodejs.org) (我們建議使用最新的 LTS 版本)
* [npm](https://www.npmjs.com/) (支援的最低版本為 3.0.0)
* [PowerBI-visuals-tools](https://www.npmjs.com/package/powerbi-visuals-tools) 所建立的自訂視覺效果

## <a name="installation"></a>安裝

若要安裝套件，您應該在具有目前視覺效果的目錄中執行下列命令：

```bash
npm install powerbi-visuals-utils-tooltiputils --save
```
此命令會安裝套件，並作為相依性將套件新增到您的 ```package.json```

## <a name="usage"></a>使用方式

> 《使用指南》說明套件的公用 API。 您會發現套件每個公用介面的描述與一些範例。

此套件提供建立 `TooltipServiceWrapper` 與方法以協助處理工具提示動作的方式。 其使用工具提示介面 - `ITooltipServiceWrapper`、`TooltipEventArgs`、`TooltipEnabledDataPoint`。 

此外，其也具有與行動裝置應用程式開發相關的特定方法 (觸控事件處理常式)：`touchEndEventName`、`touchStartEventName`、`usePointerEvents`。

`TooltipServiceWrapper` 提供最簡單的方式來操作工具提示。

此模組提供下列介面與函式：
* [ITooltipServiceWrapper](#itooltipservicewrapper)
  * [addTooltip](#itooltipservicewrapperaddtooltip)
  * [hide](#itooltipservicewrapperhide)

* [介面](#interfaces)
  * [TooltipEventArgs](#tooltipeventargs)
  * [TooltipEnabledDataPoint](#tooltipenableddatapoint)
  * [TooltipServiceWrapperOptions](#tooltipservicewrapperoptions)
* [觸控事件](#touch-events)

### `createTooltipServiceWrapper`
此函式會建立 ITooltipServiceWrapper 的執行個體。

```typescript
function createTooltipServiceWrapper(tooltipService: ITooltipService, rootElement: Element, handleTouchDelay?: number,  getEventMethod?: () => MouseEvent): ITooltipServiceWrapper;
```

您可以在 [IVisualHost](https://github.com/microsoft/PowerBI-visuals-tools/blob/master/templates/visuals/.api/v2.6.0/PowerBI-visuals.d.ts#L1335) 中找到 ```ITooltipService```。

**範例**

```typescript
import { createTooltipServiceWrapper } from "powerbi-visuals-utils-tooltiputils";

export class YourVisual implements IVisual {
    // implementation of IVisual.

    constructor(options: VisualConstructorOptions) {
        createTooltipServiceWrapper(
            options.host.tooltipService,
            options.element);

        // returns: an instance of ITooltipServiceWrapper.
    }
}
```

您可以參閱[這裡](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L391)的自訂視覺效果範例程式碼。

### `ITooltipServiceWrapper`
此介面說明 TooltipService 的公用方法。

```typescript
interface ITooltipServiceWrapper {
    addTooltip<T>(selection: d3.Selection<any, any, any, any>, getTooltipInfoDelegate: (args: TooltipEventArgs<T>) => powerbi.extensibility.VisualTooltipDataItem[], getDataPointIdentity?: (args: TooltipEventArgs<T>) => powerbi.visuals.ISelectionId, reloadTooltipDataOnMouseMove?: boolean): void;
    hide(): void;
}
```

#### `ITooltipServiceWrapper.addTooltip`

此方法會將工具提示加入至目前的選取範圍。

```typescript
addTooltip<T>(selection: d3.Selection<any>, getTooltipInfoDelegate: (args: TooltipEventArgs<T>) => VisualTooltipDataItem[], getDataPointIdentity?: (args: TooltipEventArgs<T>) => ISelectionId, reloadTooltipDataOnMouseMove?: boolean): void;
```

**範例**

```typescript
import { createTooltipServiceWrapper, TooltipEventArgs, ITooltipServiceWrapper, TooltipEnabledDataPoint } from "powerbi-visuals-utils-tooltiputils";

let bodyElement = d3.select("body");

let element = bodyElement
    .append("div")
    .style({
        "background-color": "green",
        "width": "150px",
        "height": "150px"
    })
    .classed("visual", true)
    .data([{
        tooltipInfo: [{
            displayName: "Power BI",
            value: 2016
        }]
    }]);

let tooltipServiceWrapper: ITooltipServiceWrapper = createTooltipServiceWrapper(tooltipService, bodyElement.get(0)); // tooltipService is from the IVisualHost.

tooltipServiceWrapper.addTooltip<TooltipEnabledDataPoint>(element, (eventArgs: TooltipEventArgs<TooltipEnabledDataPoint>) => {
    return eventArgs.data.tooltipInfo;
});

// You will see a tooltip if you mouseover the element.
```

您可以參閱[這裡](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L2931)的自訂視覺效果範例程式碼。

另請注意甘特圖自訂視覺效果中的工具提示自訂範例 (在[這裡](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L573-L648))

### `ITooltipServiceWrapper.hide`

此方法會隱藏工具提示。

```typescript
hide(): void;
```

**範例**

```typescript
import {createTooltipServiceWrapper} from "powerbi-visuals-utils-tooltiputils";

let tooltipServiceWrapper = createTooltipServiceWrapper(options.host.tooltipService, options.element); // options are from the VisualConstructorOptions.

tooltipServiceWrapper.hide();
```
### `Interfaces`
在建立 TooltipServiceWrapper 與其使用方式時，會使用此介面。 此外，在上一個主題 (在[這裡](#itooltipservicewrapperaddtooltip)) 中也提及它們。

#### `TooltipEventArgs`
```typescript
interface TooltipEventArgs<TData> {
    data: TData;
    coordinates: number[];
    elementCoordinates: number[];
    context: HTMLElement;
    isTouchEvent: boolean;
}
```

#### `TooltipEnabledDataPoint`
```typescript
interface TooltipEnabledDataPoint {
    tooltipInfo?: powerbi.extensibility.VisualTooltipDataItem[];
}
```

#### `TooltipServiceWrapperOptions`
```typescript
interface TooltipServiceWrapperOptions {
    tooltipService: ITooltipService;
    rootElement: Element;
    handleTouchDelay: number;
    getEventMethod?: () => MouseEvent;
```

### `Touch events`

現在，工具提示公用程式能夠處理數個觸控事件，這對於行動裝置應用程式開發來講非常有幫助。

#### `touchStartEventName`
```typescript
function touchStartEventName(): string
```
此方法會傳回觸控開始事件名稱。

#### `touchEndEventName`
```typescript
function touchEndEventName(): string
```
此方法會傳回觸控開始事件名稱。

#### `usePointerEvents`
```typescript
function usePointerEvents(): boolean
```
此方法會傳回目前的 touchStart 事件是否與指標相關。
