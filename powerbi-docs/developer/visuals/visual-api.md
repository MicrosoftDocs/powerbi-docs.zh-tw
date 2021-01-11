---
title: 取得更佳的內嵌式 BI 見解：Power BI 內嵌式分析中的視覺效果 API
description: 本文描述如何使用 Power BI 視覺效果的 IVisual API。 使用 Power BI 內嵌式分析，取得更佳的內嵌式 BI 見解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/19/2020
ms.openlocfilehash: 7b81ecfa1b97b202b6c1ff306cf858f2ea00acde
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888527"
---
# <a name="visual-api"></a>視覺效果 API
所有視覺效果均以實作 `IVisual` 介面的類別開始。 您可以將該類別命名為任何想要的名稱，只要有一個實作 `IVisual` 介面的類別即可。

> [!NOTE]
> 視覺效果類別名稱必須符合 *pbiviz.json* 檔案中定義的內容。

請參閱包含下列應實作之方法的範例視覺效果類別：

* `constructor`，用來初始化視覺效果狀態的標準建構函式
* `update`，用來更新視覺效果的資料
* `enumerateObjectInstances`，用來傳回物件以填入 [屬性] 窗格 (格式設定選項)，您可以視需要加以修改
* `destroy`，用於清除的標準解構函式

```typescript
class MyVisual implements IVisual {
    
    constructor(options: VisualConstructorOptions) {
        //one time setup code goes here (called once)
    }
    
    public update(options: VisualUpdateOptions): void {
        //code to update your visual goes here (called on all view or data changes)
    }

    public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
        //returns objects to populate the property pane (called for each object defined in capabilities)
    }
    
    public destroy(): void {
        //one time cleanup code goes here (called once)
    }
}
```

## <a name="constructor"></a>建構函式

當視覺效果具現化時，會呼叫視覺效果類別的建構函式。 其可以用於視覺效果所需的任何設定作業。

```typescript
constructor(options: VisualConstructorOptions)
```

**VisualConstructorOptions**

* `element: HTMLElement`，這是將包含視覺效果之 DOM 元素的參考
* `host: IVisualHost`，可用於與視覺效果主機 (Power BI) 互動的屬性和服務集合

   `IVisualHost` 包含下列服務：

   ```typescript
   export interface IVisualHost extends extensibility.IVisualHost {
       createSelectionIdBuilder: () => visuals.ISelectionIdBuilder;
       : () => ISelectionManager;
       colorPalette: ISandboxExtendedColorPalette;
       persistProperties: (changes: VisualObjectInstancesToPersist) => void;
       applyJsonFilter: (filter: IFilter[] | IFilter, objectName: string, propertyName: string, action: FilterAction) => void;
       tooltipService: ITooltipService;
       telemetry: ITelemetryService;
       authenticationService: IAuthenticationService;
       locale: string;
       allowInteractions: boolean;
       launchUrl: (url: string) => void;
       fetchMoreData: () => boolean;
       instanceId: string;
       refreshHostData: () => void;
       createLocalizationManager: () => ILocalizationManager;
       storageService: ILocalVisualStorageService;
       eventService: IVisualEventService;
       switchFocusModeState: (on: boolean) => void;
   }
   ```
   * `createSelectionIdBuilder`，產生並儲存視覺效果中可選取項目的中繼資料
   * `createSelectionManager`，建立通訊橋接器，用來在選取項目狀態變更時通知視覺效果的主機，請參閱[選取項目 API](./selection-api.md)。
   * `createLocalizationManager`，產生管理員以協助[當地語系化](./localization.md)
   * `allowInteractions: boolean`，布林值旗標，其會提示視覺效果是否應為互動式
   * `applyJsonFilter`，套用特定的篩選類型，請參閱[篩選 API](./filter-api.md)
   * `persistProperties`，允許使用者保存屬性，並連同視覺效果定義一起儲存，以便在下一次重新載入時使用
   * `eventService`，傳回 [事件服務](./event-service.md)，以支援 **轉譯** 事件
   * `storageService`，傳回服務，以協助在視覺效果中使用[本機儲存體](./local-storage.md)
   * `authenticationService`，產生服務以協助使用者驗證
   * `tooltipService`，傳回[工具提示服務](./add-tooltips.md)，以協助在視覺效果中使用工具提示
   * `launchUrl`，協助在下一個索引標籤中[啟動 URL](./launch-url.md)
   * `locale`，傳回地區設定字串，請參閱[當地語系化](./localization.md)
   * `instanceId`，傳回用來識別目前視覺效果執行個體的字串
   * `colorPalette`，傳回將色彩套用至資料所需的 colorPalette
   * `fetchMoreData`，支援使用比標準限制 (1K 個資料列) 更多的資料
   * `switchFocusModeState`，協助變更焦點模式狀態

## <a name="update"></a>update

所有視覺效果都必須實作公用更新方法，每當資料或主機環境發生變更時，就會加以呼叫。

```typescript
public update(options: VisualUpdateOptions): void
```

**VisualUpdateOptions**

* `viewport: IViewport`，應在其中轉譯視覺效果的檢視區維度
* `dataViews: DataView[]`，dataview 物件，其中包含轉譯視覺效果所需的所有資料 (您的視覺效果通常會使用 DataView 底下的類別目錄屬性)
* `type: VisualUpdateType`，用於指示此更新類型的旗標 ([資料] | [調整大小] | [檢視模式] | [樣式] | [ResizeEnd])
* `viewMode: ViewMode`，用於指示視覺效果檢視模式的旗標 ([檢視] | [編輯] | [InFocusEdit])
* `editMode: EditMode`，用於指示視覺效果編輯模式的旗標 ([預設] | [進階]) (如果視覺效果支援 **AdvancedEditMode**，則只有在將 **editMode** 設定為 [進階] 時，才應轉譯其進階 UI 控制項，請參閱 [AdvancedEditMode](./advanced-edit-mode.md))
* `operationKind?: VisualDataChangeOperationKind`，用於指示資料變更類型的旗標 ([建立] | [附加])
* `jsonFilters?: IFilter[]`，套用的 json 篩選條件集合
* `isInFocus?: boolean`，用於指示視覺效果是否處於焦點模式的旗標
    
## <a name="enumerateobjectinstances-optional"></a>enumerateObjectInstances `optional`

此方法會針對功能中列出的每個物件進行呼叫。 使用選項 (目前只有名稱) 時，您會傳回 `VisualObjectInstanceEnumeration`，其中包含如何顯示此屬性的相關資訊。

```typescript
enumerateObjectInstances(options:EnumerateVisualObjectInstancesOptions):VisualObjectInstanceEnumeration
```

**EnumerateVisualObjectInstancesOptions**

* `objectName: string`，物件的名稱

## <a name="destroy-optional"></a>destroy `optional`

卸載視覺效果時，會呼叫 destroy 函式，該函式可用於清除工作 (例如移除事件接聽程式)。

``` typescript
public destroy(): void
```

> [!Note]
> Power BI 通常不會呼叫 `destroy`，因為移除包含視覺效果的整個 IFrame 會更快。
