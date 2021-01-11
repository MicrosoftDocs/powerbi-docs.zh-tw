---
title: 取得更佳的內嵌式 BI 見解：Power BI 內嵌式分析中 Power BI 視覺效果的測試公用程式使用方式簡介
description: 本文描述如何使用測試公用程式來簡化 Power BI 視覺單元測試中模擬和特定方法的使用方式。 使用 Power BI 內嵌式分析，取得更佳的內嵌式 BI 見解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 02/14/2020
ms.openlocfilehash: 4b2a846f4905c4cb28fe92043cf3c71750b40f11
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888044"
---
# <a name="power-bi-visuals-test-utils"></a>Power BI 視覺效果測試公用程式

本文可協助您安裝、匯入並使用 Power BI 視覺效果測試公用程式。 這些測試公用程式可用於單元測試，並包含如資料檢視、選取項目和色彩結構描述等項目的模擬和方法。

## <a name="requirements"></a>規格需求

若要使用此套件，則必須安裝下列項目：

* [node.js](https://nodejs.org)，建議使用 LTS 版本
* [npm](https://www.npmjs.com/)，版本 3.0.0 或更新版本
* [PowerBI-visuals-tools](https://github.com/Microsoft/PowerBI-visuals-tools) 套件

## <a name="installation"></a>安裝

若要安裝測試公用程式，並將其相依性新增至 *package.json*，請在 Power BI 視覺效果目錄執行下列命令：

```bash
npm install powerbi-visuals-utils-testutils --save
```

下列提供測試公用程式公用 API 的描述與範例。

## <a name="visualbuilderbase"></a>VisualBuilderBase

於 **VisualBuilder** 在單元測試中使用，最常使用的方法為 `build`、`update` 和 `updateRenderTimeout`。 

`build` 方法會傳回已建立的視覺效果執行個體。

若要檢查貯體和格式選項的變更，則需要 `enumerateObjectInstances` 和 `updateEnumerateObjectInstancesRenderTimeout` 方法。

```typescript
abstract class VisualBuilderBase<T extends IVisual> {
    element: JQuery;
    viewport: IViewport;
    visualHost: IVisualHost;
    protected visual: T;
    constructor(width?: number, height?: number, guid?: string, element?: JQuery);
    protected abstract build(options: VisualConstructorOptions): T;
     nit(): void;
    destroy(): void;
    update(dataView: DataView[] | DataView): void;
    updateRenderTimeout(dataViews: DataView[] | DataView, fn: Function, timeout?: number): number;
    updateEnumerateObjectInstancesRenderTimeout(dataViews: DataView[] | DataView, options: EnumerateVisualObjectInstancesOptions, fn: (enumeration: VisualObjectInstance[]) => void, timeout?: number): number;
    updateFlushAllD3Transitions(dataViews: DataView[] | DataView): void;
    updateflushAllD3TransitionsRenderTimeout(dataViews: DataView[] | DataView, fn: Function, timeout?: number): number;
    enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstance[];
}
```

> [!NOTE]
> 如需進一步範例，請參閱 [VisualBuilderBase 單元測試撰寫](./unit-tests-introduction.md#create-a-visual-instance-builder)和 [VisualBuilderBase 實際使用案例](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/test/visualBuilder.ts)。

## <a name="dataviewbuilder"></a>DataViewBuilder

由 **TestDataViewBuilder** 使用，此模組可提供在 `createCategoricalDataViewBuilder` 方法中使用的 **CategoricalDataViewBuilder** 類別， 其也會指定在單元測試中使用模擬 **DataView** 時所需的介面和方法。

* `withValues` 會新增靜態序列欄，`withGroupedValues` 則會新增動態序列欄

  請勿在視覺效果 **DataViewCategorical** 中同時套用動態數列和靜態序列。 您只能在 **DataViewCategorical** 查詢中才能同時使用這兩種序列，**DataViewTransform** 會將這兩種序列分割為不同的視覺效果 **DataViewCategorical** 物件。

* `build` 會傳回具有中繼資料和 DataViewCategorical 的 DataView

  如果參數的組合不合法 (例如，在建立視覺效果 **DataView** 時同時包含動態和靜態序列)，則 `build` 會傳回 **Undefined**。

```typescript
class CategoricalDataViewBuilder implements IDataViewBuilderCategorical {
    withCategory(options: DataViewBuilderCategoryColumnOptions): IDataViewBuilderCategorical;
    withCategories(categories: DataViewCategoryColumn[]): IDataViewBuilderCategorical;
    withValues(options: DataViewBuilderValuesOptions): IDataViewBuilderCategorical;
    withGroupedValues(options: DataViewBuilderGroupedValuesOptions): IDataViewBuilderCategorical;
    build(): DataView;
}

function createCategoricalDataViewBuilder(): IDataViewBuilderCategorical;
```

## <a name="testdataviewbuilder"></a>TestDataViewBuilder

用於在單元測試中建立 **VisualData**。 當放置資料於資料欄位貯體時，Power BI 會根據該筆資料產生類別目錄 **DataView** 物件。 **TestDataViewBuilder** 有助於為建立類別目錄 **DataView** 進行模擬。

```typescript
abstract class TestDataViewBuilder {
    static DataViewName: string;
    private aggregateFunction;
    static setDefaultQueryName(source: DataViewMetadataColumn): DataViewMetadataColumn;
    static getDataViewBuilderColumnIdentitySources(options: TestDataViewBuilderColumnOptions[] | TestDataViewBuilderColumnOptions): DataViewBuilderColumnIdentitySource[];
    static getValuesTable(categories?: DataViewCategoryColumn[], values?: DataViewValueColumn[]): any[][];
    static createDataViewBuilderColumnOptions(categoriesColumns: (TestDataViewBuilderCategoryColumnOptions | TestDataViewBuilderCategoryColumnOptions[])[], valuesColumns: (DataViewBuilderValuesColumnOptions | DataViewBuilderValuesColumnOptions[])[], filter?: (options: TestDataViewBuilderColumnOptions) => boolean, customizeColumns?: CustomizeColumnFn): DataViewBuilderAllColumnOptions;
    static setUpDataViewBuilderColumnOptions(options: DataViewBuilderAllColumnOptions, aggregateFunction: (array: number[]) => number): DataViewBuilderAllColumnOptions;
    static setUpDataView(dataView: DataView, options: DataViewBuilderAllColumnOptions): DataView;
    protected createCategoricalDataViewBuilder(categoriesColumns: (TestDataViewBuilderCategoryColumnOptions | TestDataViewBuilderCategoryColumnOptions[])[], valuesColumns: (DataViewBuilderValuesColumnOptions | DataViewBuilderValuesColumnOptions[])[], columnNames: string[], customizeColumns?: CustomizeColumnFn): IDataViewBuilderCategorical;
    abstract getDataView(columnNames?: string[]): DataView;
}
```

  下列會列出建立 `testDataView` 時最常使用的介面：

  ```typescript
  interface TestDataViewBuilderColumnOptions extends DataViewBuilderColumnOptions {
      values: any[];
  }

  interface TestDataViewBuilderCategoryColumnOptions extends TestDataViewBuilderColumnOptions {
      objects?: DataViewObjects[];
      isGroup?: boolean;
  }

  interface DataViewBuilderColumnOptions {
      source: DataViewMetadataColumn;
  }

  interface DataViewBuilderSeriesData {
      values: PrimitiveValue[];
      highlights?: PrimitiveValue[];
      /** Client-computed maximum value for a column. */
      maxLocal?: any;
      /** Client-computed maximum value for a column. */
      minLocal?: any;
  }

  interface DataViewBuilderColumnIdentitySource {
      fields: any[];
      identities?: CustomVisualOpaqueIdentity[];
  }
  ```
   
> [!NOTE]
> 如需進一步的範例，請參閱 [TestDataViewBuilder 單元測試撰寫](./unit-tests-introduction.md#how-to-add-static-data-for-unit-tests)和 [TestDataViewBuilder 實際使用案例](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/test/visualData.ts)。

## <a name="mocks"></a>模擬

### <a name="mockivisualhost"></a>MockIVisualHost

執行 **IVisualHost**，以測試不含外部相依性的 Power BI 視覺效果，例如 Power BI Framework。

實用方法包括 `createSelectionIdBuilder`、`createSelectionManager`、`createLocalizationManager` 以及 getter 屬性。

```typescript
import powerbi from "powerbi-visuals-api";

import VisualObjectInstancesToPersist = powerbi.VisualObjectInstancesToPersist;
import ISelectionIdBuilder = powerbi.visuals.ISelectionIdBuilder;
import ISelectionManager = powerbi.extensibility.ISelectionManager;
import IColorPalette = powerbi.extensibility.IColorPalette;
import IVisualEventService = powerbi.extensibility.IVisualEventService;
import ITooltipService = powerbi.extensibility.ITooltipService;
import IVisualHost = powerbi.extensibility.visual.IVisualHost;

class MockIVisualHost implements IVisualHost {
      constructor(
          colorPalette?: IColorPalette,
          selectionManager?: ISelectionManager,
          tooltipServiceInstance?: ITooltipService,
          localeInstance?: MockILocale,
          allowInteractionsInstance?: MockIAllowInteractions,
          localizationManager?: powerbi.extensibility.ILocalizationManager,
          telemetryService?: powerbi.extensibility.ITelemetryService,
          authService?: powerbi.extensibility.IAuthenticationService,
          storageService?: ILocalVisualStorageService,
          eventService?: IVisualEventService);
      createSelectionIdBuilder(): ISelectionIdBuilder;
      createSelectionManager(): ISelectionManager;
      createLocalizationManager(): ILocalizationManager;
      colorPalette: IColorPalette;
      locale: string;
      telemetry: ITelemetryService;
      tooltipService: ITooltipService;
      allowInteractios: boolean;
      storageService: ILocalVisualStorageService;
      eventService: IVisualEventService;
      persistProperties(changes: VisualObjectInstancesToPersist): void;
}
```
   
- `createVisualHost` 會建立並傳回 **IVisualHost** 的執行個體，這實際上為 **MockIVisualHost**
  ```typescript
  function createVisualHost(locale?: Object, allowInteractions?: boolean, colors?: IColorInfo[], isEnabled?: boolean, displayNames?: any, token?: string): IVisualHost;
  ```

    範例
    ```typescript
    import { createVisualHost } from "powerbi-visuals-utils-testutils"

    let host: IVisualHost = createVisualHost();
    ```

> [!IMPORTANT]
> **MockIVisualHost** 是 **IVisualHost** 的假執行，且只應與單元測試搭配使用。

### <a name="mockicolorpalette"></a>MockIColorPalette

執行 **IColorPalette** 以測試不含外部相依性的 Power BI 視覺效果，例如 Power BI Framework。

**MockIColorPalette** 會提供實用的屬性，以便在單元測試中檢查色彩結構描述或高對比模式。

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import IColorPalette = powerbi.extensibility.ISandboxExtendedColorPalette;
  import IColorInfo = powerbi.IColorInfo;

  class MockIColorPalette implements IColorPalette {
      constructor(colors?: IColorInfo[]);
      getColor(key: string): IColorInfo;
      reset(): IColorPalette;
      isHighContrastMode: boolean;
      foreground: {value: string};
      foregroundLight: {value: string};
      ...
      background: {value: string};
      backgroundLight: {value: string};
      ...
      shapeStroke: {value: string};
  }
  ```
  - `createColorPalette` 會建立並傳回 **IColorPalette** 的執行個體，這實際上為 **MockIColorPalette**
    ```typescript
    function createColorPalette(colors?: IColorInfo[]): IColorPalette;
    ```

    範例
    ```typescript
    import { createColorPalette } from "powerbi-visuals-utils-testutils"

    let colorPalette: IColorPalette = createColorPalette();
    ```
    
> [!IMPORTANT]
> **MockIColorPalette** 是 **IColorPalette** 的假執行，且只應與單元測試搭配使用。

### <a name="mockiselectionid"></a>MockISelectionId

執行 **ISelectionId** 以測試不含外部相依性的 Power BI 視覺效果，例如 Power BI Framework。

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import Selector = powerbi.data.Selector;
  import ISelectionId = powerbi.visuals.ISelectionId;

  class MockISelectionId implements ISelectionId {
      constructor(key: string);
      equals(other: ISelectionId): boolean;
      includes(other: ISelectionId, ignoreHighlight?: boolean): boolean;
      getKey(): string;
      getSelector(): Selector;
      getSelectorsByColumn(): Selector;
      hasIdentity(): boolean;
  }
  ```

  - `createSelectionId` 會建立並傳回 **ISelectionId** 的執行個體，這實際上為 **MockISelectionId**
    ```typescript
    function createSelectionId(key?: string): ISelectionId;
    ```

    範例
    ```typescript
    import { createColorPalette } from "powerbi-visuals-utils-testutils"

    let selectionId: ISelectionId = createSelectionId();
    ```
    
> [!NOTE]
> **MockISelectionId** 是 **ISelectionId** 的假執行，且只應與單元測試搭配使用。

### <a name="mockiselectionidbuilder"></a>MockISelectionIdBuilder

執行 **ISelectionIdBuilder** 以測試不含外部相依性的 Power BI 視覺效果，例如 Power BI Framework。 

  ```typescript
  import DataViewCategoryColumn = powerbi.DataViewCategoryColumn;
  import DataViewValueColumn = powerbi.DataViewValueColumn;
  import DataViewValueColumnGroup = powerbi.DataViewValueColumnGroup;
  import DataViewValueColumns = powerbi.DataViewValueColumns;
  import ISelectionIdBuilder = powerbi.visuals.ISelectionIdBuilder;
  import ISelectionId = powerbi.visuals.ISelectionId;

  class MockISelectionIdBuilder implements ISelectionIdBuilder {
      withCategory(categoryColumn: DataViewCategoryColumn, index: number): this;
      withSeries(seriesColumn: DataViewValueColumns, valueColumn: DataViewValueColumn | DataViewValueColumnGroup): this;
      withMeasure(measureId: string): this;
      createSelectionId(): ISelectionId;
      withMatrixNode(matrixNode: DataViewMatrixNode, levels: DataViewHierarchyLevel[]): this;
      withTable(table: DataViewTable, rowIndex: number): this;
  }
  ```

  - `createSelectionIdBuilder` 會建立並傳回 **ISelectionIdBuilder** 的執行個體，這實際上為 **MockISelectionIdBuilder**
    ```typescript
    function createSelectionIdBuilder(): ISelectionIdBuilder;
    ```

    範例
    ```typescript
    import { selectionIdBuilder } from "powerbi-visuals-utils-testutils";

    let selectionIdBuilder = createSelectionIdBuilder();
    ```

> [!NOTE]
> **MockISelectionIdBuilder** 是 **ISelectionIdBuilder** 的假執行，且只應與單元測試搭配使用。

### <a name="mockiselectionmanager"></a>MockISelectionManager

執行 **ISelectionManager** 以測試不含外部相依性的 Power BI 視覺效果，例如 Power BI Framework。 

  ```typescript
  import powerbi from "powerbi-visuals-api";
  import IPromise = powerbi.IPromise;
  import ISelectionId = powerbi.visuals.ISelectionId;
  import ISelectionManager = powerbi.extensibility.ISelectionManager;

  class MockISelectionManager implements ISelectionManager {
      select(selectionId: ISelectionId | ISelectionId[], multiSelect?: boolean): IPromise<ISelectionId[]>;
      hasSelection(): boolean;
      clear(): IPromise<{}>;
      getSelectionIds(): ISelectionId[];
      containsSelection(id: ISelectionId): boolean;
      showContextMenu(selectionId: ISelectionId, position: IPoint): IPromise<{}>;
      registerOnSelectCallback(callback: (ids: ISelectionId[]) => void): void;
      simutateSelection(selections: ISelectionId[]): void;
  }
  ```

  - `createSelectionManager` 會建立並傳回 **ISelectionManager** 的執行個體，這實際上為 **MockISelectionManager**
    ```typescript
    function createSelectionManager(): ISelectionManager
    ```

    範例
    ```typescript
    import { createSelectionManager } from "powerbi-visuals-utils-testutils";

    let selectionManager: ISelectionManager = createSelectionManager();
    ```

> [!NOTE]
> **MockISelectionManager** 是 **ISelectionManager** 的假執行，且只應與單元測試搭配使用。

### <a name="mockilocale"></a>MockILocale

  設定地區，並在單元測試過程中針對需求進行變更。
  ```typescript
  class MockILocale {
      constructor(locales?: Object): void; // Default locales are en-US and ru-RU 
      locale(key: string): void;// setter property
      locale(): string; // getter property
  }
  ```
  - `createLocale` 會建立並傳回 **MockILocale** 的執行個體
    ```typescript
    funciton createLocale(locales?: Object): MockILocale;
    ```

### <a name="mockitooltipservice"></a><a id="mockitooltipservice"></a> MockITooltipService
模擬 `TooltipService`，並在單元測試程序中針對需求對其呼叫。
  ```typescript
  class MockITooltipService implements ITooltipService {
      constructor(isEnabled: boolean = true);
      enabled(): boolean;
      show(options: TooltipShowOptions): void;
      move(options: TooltipMoveOptions): void;
      hide(options: TooltipHideOptions): void;
  }
  ```
  - `createTooltipService` 會建立並傳回 **MockITooltipService** 的執行個體
    ```typescript
    function createTooltipService(isEnabled?: boolean): ITooltipService;
    ```

### <a name="mockiallowinteractions"></a>MockIAllowInteractions

```typescript
export class MockIAllowInteractions {
    constructor(public isEnabled?: boolean); // false by default
}
```
  - `createAllowInteractions` 會建立並傳回 **MockIAllowInteractions** 的執行個體
    ```typescript
    function createAllowInteractions(isEnabled?: boolean): MockIAllowInteractions;
    ```

### <a name="mockilocalizationmanager"></a><a id="mockilocalizationmanager"></a> MockILocalizationManager
提供單元測試中所需的 **LocalizationManager** 基本功能。
```typescript
class MockILocalizationManager implements ILocalizationManager {
    constructor(displayNames: {[key: string]: string});
    getDisplayName(key: string): string; // returns default or setted displayNames for localized elements
}
```
  - `createLocalizationManager` 會建立並傳回 **ILocalizationManager** 的執行個體，這實際上為 **MockILocalizationManager**
    ```typescript
    function createLocalizationManager(displayNames?: any): ILocalizationManager;
    ```

    範例
    ```typescript
    import { createLocalizationManager } from "powerbi-visuals-utils-testutils";
    let localizationManagerMock: ILocalizationManager = createLocalizationManager();
    ```

### <a name="mockitelemetryservice"></a>MockITelemetryService
模擬 **TelemetryService** 使用方式。
```typescript
class MockITelemetryService implements ITelemetryService {
    instanceId: string;
    trace(veType: powerbi.VisualEventType, payload?: string) {
    }
}
```
  建立 `MockITelemetryService`
    ```typescript
    function createTelemetryService(): ITelemetryService;
    ```
### <a name="mockiauthenticationservice"></a>MockIAuthenticationService
藉由提供模擬的 AAD 權杖，以模擬 **AuthenticationService** 的工作。
```typescript
class MockIAuthenticationService implements IAuthenticationService  {
    constructor(token: string);
    getAADToken(visualId?: string): powerbi.IPromise<string>
}
```
  - `createAuthenticationService` 會建立並傳回 **IAuthenticationService** 的執行個體，這實際上為 **MockIAuthenticationService**
    ```typescript
    function createAuthenticationService(token?: string): IAuthenticationService;
    ```

### <a name="mockistorageservice"></a>MockIStorageService
允許使用與 **LocalStorage** 具有相同行為的 **ILocalVisualStorageService**。
```typescript
class MockIStorageService implements ILocalVisualStorageService {
  get(key: string): IPromise<string>;
  set(key: string, data: string): IPromise<number>;
  remove(key: string): void;
}
```
  - `createStorageService` 會建立並傳回 **ILocalVisualStorageService** 的執行個體，這實際上為 **MockIStorageService**
    ```typescript
    function createStorageService(): ILocalVisualStorageService;
    ```

### <a name="mockieventservice"></a>MockIEventService
```typescript
import powerbi from "powerbi-visuals-api";
import IVisualEventService = powerbi.extensibility.IVisualEventService;
import VisualUpdateOptions = powerbi.extensibility.VisualUpdateOptions;

class MockIEventService implements IVisualEventService {
      renderingStarted(options: VisualUpdateOptions): void;
      renderingFinished(options: VisualUpdateOptions): void;
      renderingFailed(options: VisualUpdateOptions, reason?: string): void;
}
```
  - `createEventService` 會建立並傳回 **IVisualEventService** 的執行個體，這實際上為 **MockIEventService**
    ```typescript
    function createEventService(): IVisualEventService;
    ```

## <a name="utils"></a>公用程式

公用程式包含 Power BI 視覺效果單元測試的 Helper 方法，包括與色彩、數字以及事件相關的協助程式。

- `renderTimeout` 會傳回逾時
  ```typescript
  function renderTimeout(fn: Function, timeout: number = DefaultWaitForRender): number
  ```

- `testDom` 可協助設定單元測試中的固件
  ```typescript
  function testDom(height: number | string, width: number | string): JQuery
  ```
  範例
  ```typescript
  import { testDom }  from "powerbi-visuals-utils-testutils";
  describe("testDom", () => {
      it("should return an element", () => {
          let element: JQuery = testDom(500, 500);
          expect(element.get(0)).toBeDefined();
      });
  });
  ```

### <a name="color-related-helper-methods"></a>與色彩相關的 Helper 方法

- `getSolidColorStructuralObject`
  ```typescript
  function getSolidColorStructuralObject(color: string): any
  ```
  其傳回下列結構：

  ```json
  { solid: { color: color } }
  ```

- `assertColorsMatch` 會比較從輸入字串剖析的 **RgbColor** 物件
  ```typescript
  function assertColorsMatch(actual: string, expected: string, invert: boolean = false): boolean
  ```

- `parseColorString` 會剖析輸入字串中的色彩，並在指定的介面 **RgbColor** 中將其傳回
  ```typescript
  function parseColorString(color: string): RgbColor
  ```

### <a name="number-related-helper-methods"></a>與數字相關的 Helper 方法

- `getRandomNumbers` 會使用 min 和 max 值來產生隨機數字。 您可指定 `exceptionList` 並提供可變更結果的函式。
  ```typescript
  function getRandomNumber(
      min: number,
      max: number,
      exceptionList?: number[],
      changeResult: (value: any) => number = x => x): number
  ```

- `getRandomNumbers` 會提供 `getRandomNumber` 方法所產生的隨機數字陣列，其中包含指定的 min 和 max 值
  ```typescript
  function getRandomNumbers(count: number, min: number = 0, max: number = 1): number[]
  ```

### <a name="event-related-helper-methods"></a>與事件相關的 Helper 方法
下列方法是針對單元測試中的網頁事件模擬所撰寫。

- `clickElement` 會模擬指定項目上的點擊
  ```typescript
  function clickElement(element: JQuery, ctrlKey: boolean = false): void
  ```

- `createTouch` 會傳回 **Touch** 物件，以協助模擬觸控事件
  ```typescript
  function createTouch(x: number, y: number, element: JQuery, id: number = 0): Touch
  ```

- `createTouchesList` 會傳回模擬的 **Touch** 事件清單
  ```typescript
  function createTouchesList(touches: Touch[]): TouchList
  ```

- `createContextMenuEvent` 會傳回 **MouseEvent**
  ```typescript
  function createContextMenuEvent(x: number, y: number): MouseEvent
  ```

- `createMouseEvent` 會建立並傳回 **MouseEvent**
  ```typescript
  function createMouseEvent(
      mouseEventType: MouseEventType,
      eventType: ClickEventType,
      x: number,
      y: number,
      button: number = 0): MouseEvent
  ```

- `createTouchEndEvent`
  ```typescript
  function createTouchEndEvent(touchList?: TouchList): UIEvent
  ```

- `createTouchMoveEvent`
  ```typescript
  function createTouchMoveEvent(touchList?: TouchList): UIEvent
  ```

- `createTouchStartEvent`
  ```typescript
  function createTouchStartEvent(touchList?: TouchList): UIEvent
  ```

### <a name="d3-event-related-helper-methods"></a>與 D3 事件相關的 Helper 方法

下列方法可用來模擬單元測試中的 D3 事件。

- `flushAllD3Transitions` 會強制完成所有 D3 轉換

  ```typescript
  function flushAllD3Transitions()
  ```
  
  > [!NOTE]
  > 一般而言，在瞬間延遲 (< 10 毫秒) 後會執行零延遲的轉換，但如果瀏覽器將頁面轉譯兩次，則可能會造成短暫的閃爍。 當第一個事件迴圈結束之後，會再次出現在第一個計時器回呼上。
  >
  > 這些閃爍在 IE 上且具有大量的網頁檢視時較明顯，不建議用於 iOS。
  > 
  > 藉由清除第一個事件迴圈結尾的計時器佇列，您可立即執行任何零延遲轉換，以避免發生閃爍。

下列方法也包含在其中：
```typescript
function d3Click(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseUp(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseDown(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseOver(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseMove(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3MouseOut(element: JQuery, x: number, y: number, eventType?: ClickEventType, button?: number): void
function d3KeyEvent(element: JQuery, typeArg: string, keyArg: string, keyCode: number): void
function d3TouchStart(element: JQuery, touchList?: TouchList): void
function d3TouchMove(element: JQuery, touchList?: TouchList): void
function d3TouchEnd(element: JQuery, touchList?: TouchList): void
function d3ContextMenu(element: JQuery, x: number, y: number): void
```

### <a name="helper-interfaces"></a>Helper 介面
Helper 函式中會使用下列介面和列舉。

```typescript
interface RgbColor {
    R: number;
    G: number;
    B: number;
    A?: number; 
}

enum ClickEventType {
    Default = 0,
    CtrlKey = 1,
    AltKey = 2,
    ShiftKey = 4,
    MetaKey = 8,
}

enum MouseEventType {
    click,
    mousedown,
    mouseup,
    mouseover,
    mousemove,
    mouseout,
}
```

## <a name="next-steps"></a>後續步驟

若要撰寫以 webpack 為基礎的 Power BI 視覺效果的單元測試，以及使用 `karma` 和 `jasmine` 的單元測試，請參閱[教學課程：新增 Power BI 視覺效果專案的單元測試](./unit-tests-introduction.md)此範例。
