---
title: 在 Power BI 內嵌式分析的 Power BI 視覺效果中轉譯事件，以取得更佳的內嵌 BI 見解
description: Power BI 視覺效果可以通知 Power BI 它們已準備好匯出至 Power Point 或 PDF。 使用 Power BI 內嵌式分析，以便取得更佳的內嵌 BI 見解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: 77ed686b78a96717193e594e9f846d4204d8b5e8
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97885077"
---
# <a name="render-events-in-power-bi-visuals"></a>在 Power BI 視覺效果中轉譯事件

新的 API 是由三種方法 (`started`、`finished` 或 `failed`) 所組成，這些方法應在轉譯期間呼叫。

當轉譯開始時，Power BI 視覺效果程式碼會呼叫 `renderingStarted` 方法來指出已啟動轉譯處理序。

如果轉譯成功完成，Power BI 視覺效果程式碼會立即呼叫 `renderingFinished` 方法，以通知接聽程式 (主要是「匯出為 PDF」和「匯出至 PowerPoint」) 視覺效果的影像已準備好進行匯出。

如果在該處理序期間發生問題，Power BI 視覺效果便無法順利轉譯。 為了通知接聽程式轉譯處理序尚未完成，Power BI 視覺效果程式碼應呼叫 `renderingFailed` 方法。 這個方法也會提供選擇性字串以提供失敗的原因。

## <a name="usage"></a>使用方式

```typescript
export interface IVisualHost extends extensibility.IVisualHost {
    eventService: IVisualEventService ;
}

/**
 * An interface for reporting rendering events
 */
export interface IVisualEventService {
    /**
     * Should be called just before the actual rendering starts, 
     * usually at the start of the update method
     *
     * @param options - the visual update options received as an update parameter
     */
    renderingStarted(options: VisualUpdateOptions): void;

    /**
     * Should be called immediately after rendering finishes successfully
     * 
     * @param options - the visual update options received as an update parameter
     */
    renderingFinished(options: VisualUpdateOptions): void;

    /**
     * Called when rendering fails, with an optional reason string
     * 
     * @param options - the visual update options received as an update parameter
     * @param reason - the optional failure reason string
     */
    renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```

### <a name="sample-the-visual-displays-no-animations"></a>範例：視覺效果未顯示任何動畫

```typescript
    export class Visual implements IVisual {
        ...
        private events: IVisualEventService;
        ...

        constructor(options: VisualConstructorOptions) {
            ...
            this.events = options.host.eventService;
            ...
        }

        public update(options: VisualUpdateOptions) {
            this.events.renderingStarted(options);
            ...
            this.events.renderingFinished(options);
        }
```

### <a name="sample-the-visual-displays-animations"></a>範例：視覺效果顯示動畫

如果視覺效果具有用於轉譯的動畫或非同步函式，則應在動畫之後或在非同步函式內呼叫 `renderingFinished` 方法。

```typescript
    export class Visual implements IVisual {
        ...
        private events: IVisualEventService;
        private element: HTMLElement;
        ...

        constructor(options: VisualConstructorOptions) {
            ...
            this.events = options.host.eventService;
            this.element = options.element;
            ...
        }

        public update(options: VisualUpdateOptions) {
            this.events.renderingStarted(options);
            ...
            // Learn more at https://github.com/d3/d3-transition/blob/master/README.md#transition_end
            d3.select(this.element).transition().duration(100).style("opacity","0").end().then(() => {
                // renderingFinished called after transition end
                this.events.renderingFinished(options);
            });
        }
```

## <a name="rendering-events-for-visual-certification"></a>視覺效果認證的轉譯事件

視覺效果認證的其中一個需求，是視覺效果的轉譯事件支援。 如需詳細資訊，請參閱[認證需求](power-bi-custom-visuals-certified.md#certification-requirements)。