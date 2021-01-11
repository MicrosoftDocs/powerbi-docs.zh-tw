---
title: Power BI 內嵌式分析中，用於取得更佳內嵌 BI 見解的 Power BI 視覺效果互動功能公用程式
description: 本文描述如何使用互動功能公用程式，將選取項目新增至 Power BI 視覺效果中。 使用 Power BI 內嵌式分析，以便取得更佳的內嵌 BI 見解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 02/24/2020
ms.openlocfilehash: 533cf90ed9192a8d9e595cdea6320207b841b559
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887768"
---
# <a name="power-bi-visuals-interactivity-utils"></a>Power BI 互動功能公用程式

Interactivity 公用程式 (`InteractivityUtils`) 是一組函式與類別，可用來簡化交叉選取和交叉篩選實作。

> [!NOTE]
> 互動功能公用程式的新更新僅支援最新版本的工具 (3.x.x 與更新版本)。

## <a name="installation"></a>安裝

1. 若要安裝套件，請在具有目前 Power BI 視覺效果專案的目錄中執行下列命令。

    ```bash
    npm install powerbi-visuals-utils-interactivityutils --save
    ```

2. 如果您使用的是 3.0 版或更新版本或工具，請安裝 `powerbi-models` 以解決相依性。

    ```bash
    npm install powerbi-models --save
    ```

3. 若要使用互動功能公用程式，請在 Power BI 視覺效果原始程式碼中匯入必要元件。

    ```typescript
    import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";
    ```

### <a name="including-the-css-files"></a>包含 CSS 檔案

若要將套件與您的 Power BI 視覺效果搭配使用，請將下列 CSS 檔案匯入您的 `.less` 檔案。

`node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css`

將 CSS 檔案作為 `.less` 檔案匯入，因為 Power BI 視覺效果工具會包裝外部 CSS 規則。

```less
@import (less) "node_modules/powerbi-visuals-utils-interactivityutils/lib/index.css";
```

## <a name="selectabledatapoint-properties"></a>SelectableDataPoint 屬性

通常資料點會包含選取項目和值。 該介面會擴充 `SelectableDataPoint` 介面。

`SelectableDataPoint` 已包含屬性，如下所述。

```typescript
  /** Flag for identifying that a data point was selected */
  selected: boolean;

  /** Identity for identifying the selectable data point for selection purposes */
  identity: powerbi.extensibility.ISelectionId;

  /*
   * A specific identity for when data points exist at a finer granularity than
   * selection is performed.  For example, if your data points select based
   * only on series, even if they exist as category/series intersections.
   */

  specificIdentity?: powerbi.extensibility.ISelectionId;
```

## <a name="defining-an-interface-for-data-points"></a>定義資料點的介面

1. 建立互動功能公用程式的執行個體，並將物件另存為視覺效果的屬性

    ```typescript
    export class Visual implements IVisual {
      // ...
      private interactivity: interactivityBaseService.IInteractivityService<VisualDataPoint>;
      // ...
      constructor(options: VisualConstructorOptions) {
          // ...
          this.interactivity = interactivitySelectionService.createInteractivitySelectionService(this.host);
          // ...
      }
    }
    ```

    ```typescript
    import { interactivitySelectionService } from "powerbi-visuals-utils-interactivityutils";

    export interface VisualDataPoint extends interactivitySelectionService.SelectableDataPoint {
        value: powerbi.PrimitiveValue;
    }
    ```

2. 延伸基底行為類別。

    > [!NOTE]
    > [互動功能公用程式的 5.6.x 版本](https://www.npmjs.com/package/powerbi-visuals-utils-interactivityutils/v/5.6.0) \(英文\) 中引進了 `BaseBehavior`。 如果您使用舊版本，請從下列範例建立行為類別。

3. 定義行為類別選項的介面。

    ```typescript
    import { SelectableDataPoint } from "./interactivitySelectionService";

    import {
        IBehaviorOptions,
        BaseDataPoint
    } from "./interactivityBaseService";

    export interface BaseBehaviorOptions<SelectableDataPointType extends BaseDataPoint> extends IBehaviorOptions<SelectableDataPointType> {

    /** d3 selection object of the main elements on the chart */
    elementsSelection: Selection<any, SelectableDataPoint, any, any>;

    /** d3 selection object of some elements on backgroup, to hadle click of reset selection */
    clearCatcherSelection: d3.Selection<any, any, any, any>;
    }
    ```

4. 定義 `visual behavior` 的類別。 或者，擴充 `BaseBehavior` 類別。

    **定義 `visual behavior` 的類別**

    該類別負責處理 `click` `contextmenu` 滑鼠事件。

    當使用者按一下資料元素時，視覺效果會呼叫選取項目處理常式來選取資料點。 如果使用者按一下視覺效果的背景元素，則會呼叫清除選取項目處理常式。

    類別有下列對應的方法：
    * `bindClick`
    * `bindClearCatcher`
    * `bindContextMenu`.

    ```typescript
    export class Behavior<SelectableDataPointType extends BaseDataPoint> implements IInteractiveBehavior {

        /** d3 selection object of main elements in the chart */
        protected options: BaseBehaviorOptions<SelectableDataPointType>;
        protected selectionHandler: ISelectionHandler;
    
        protected bindClick() {
          // ...
        }
    
        protected bindClearCatcher() {
          // ...
        }
    
        protected bindContextMenu() {
          // ...
        }
    
        public bindEvents(
            options: BaseBehaviorOptions<SelectableDataPointType>,
            selectionHandler: ISelectionHandler): void {
          // ...
        }
    
        public renderSelection(hasSelection: boolean): void {
          // ...
        }
    }
    ```

    **擴充 `BaseBehavior` 類別**

    ```typescript
    import powerbi from "powerbi-visuals-api";
    import { interactivitySelectionService, baseBehavior } from "powerbi-visuals-utils-interactivityutils";

    export interface VisualDataPoint extends interactivitySelectionService.SelectableDataPoint {
        value: powerbi.PrimitiveValue;
    }

    export class Behavior extends baseBehavior.BaseBehavior<VisualDataPoint> {
      // ...
    }
    ```

5. 若要處理元素上的點擊，請呼叫 *d3* 選取項目物件 `on` 方法。 這也適用於 `elementsSelection` 與 `clearCatcherSelection`。

    ```typescript
    protected bindClick() {
      const {
          elementsSelection
      } = this.options;
    
      elementsSelection.on("click", (datum) => {
          const mouseEvent: MouseEvent = getEvent() as MouseEvent || window.event as MouseEvent;
          mouseEvent && this.selectionHandler.handleSelection(
              datum,
              mouseEvent.ctrlKey);
      });
    }
    ```

6. 為 `contextmenu` 事件新增類似的處理常式，以呼叫選取項目管理員的 `showContextMenu` 方法。

    ```typescript
    protected bindContextMenu() {
        const {
            elementsSelection
        } = this.options;
    
        elementsSelection.on("contextmenu", (datum) => {
            const event: MouseEvent = (getEvent() as MouseEvent) || window.event as MouseEvent;
            if (event) {
                this.selectionHandler.handleContextMenu(
                    datum,
                    {
                        x: event.clientX,
                        y: event.clientY
                    });
                event.preventDefault();
            }
        });
    }
    ```

7. 為將函式指派給處理常式，互動功能公用程式會呼叫 `bindEvents` 方法。 將下列呼叫新增至 `bindEvents` 方法︰
    * `bindClick`
    * `bindClearCatcher`
    * `bindContextMenu`

    ```typescript
      public bindEvents(
          options: BaseBehaviorOptions<SelectableDataPointType>,
          selectionHandler: ISelectionHandler): void {

          this.options = options;
          this.selectionHandler = selectionHandler;

          this.bindClick();
          this.bindClearCatcher();
          this.bindContextMenu();
      }
    ```

8. `renderSelection` 方法負責更新圖表中元素的視覺效果狀態。 以下是 `renderSelection` 的範例實作。

    ```typescript
    public renderSelection(hasSelection: boolean): void {
        this.options.elementsSelection.style("opacity", (category: any) => {
            if (category.selected) {
                return 0.5;
            } else {
                return 1;
            }
        });
    }
    ```

9. 最後一個步驟是建立 `visual behavior` 的執行個體，以及呼叫互動功能公用程式執行個體的 `bind` 方法。

    ```typescript
    this.interactivity.bind(<BaseBehaviorOptions<VisualDataPoint>>{
        behavior: this.behavior,
        dataPoints: this.categories,
        clearCatcherSelection: select(this.target),
        elementsSelection: selectionMerge
    });
    ```

    * `selectionMerge` 是 *d3* 選取項目物件，代表視覺效果所有可選取的元素。
    * `select(this.target)` 是 *d3* 選取項目物件，代表視覺效果的主要 DOM 元素。
    * `this.categories` 是具有元素的資料點，其中介面為 `VisualDataPoint` 或 `categories: VisualDataPoint[];`。
    * `this.behavior` 是新的 `visual behavior` 執行個體，這是在視覺效果的建構函式中建立的，如下所示。

      ```typescript
      export class Visual implements IVisual {
        // ...
        constructor(options: VisualConstructorOptions) {
            // ...
            this.behavior = new Behavior();
        }
        // ...
      }
      ```
## <a name="next-steps"></a>後續步驟

* [了解如何處理書籤切換上的選擇](bookmarks-support.md#visuals-with-selection)

* [了解如何為視覺效果資料點新增操作功能表](context-menu.md)

* [了解如何使用選取項目管理員將選取項目新增至 Power BI 視覺效果中](selection-api.md)
