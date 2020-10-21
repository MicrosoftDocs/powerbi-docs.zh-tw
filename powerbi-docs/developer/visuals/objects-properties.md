---
title: Power BI 視覺效果的物件和屬性
description: 此文章說明 Power BI 視覺效果的可自訂屬性。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: ae548abd0d579414a69b0d970213ff9d69ff2f08
ms.sourcegitcommit: eab5a02520c421a57019595c03e9ecfdb41d52ad
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/20/2020
ms.locfileid: "92256311"
---
# <a name="objects-and-properties-of-power-bi-visuals"></a>Power BI 視覺效果的物件和屬性

物件會描述與視覺效果相關聯的可自訂屬性。 一個物件可以有多個屬性，且每個屬性都有能描述該屬性將會是什麼的相關聯類型。 此文章提供物件及屬性類型的相關資訊。

`myCustomObject` 是用來參考 `dataView` 和 `enumerateObjectInstances` 內之物件的內部名稱。

```json
"objects": {
    "myCustomObject": {
        "displayName": "My Object Name",
        "properties": { ... }
    }
}
```

## <a name="display-name"></a>顯示名稱

`displayName` 是將會顯示在 [屬性] 窗格中的名稱。

## <a name="properties"></a>屬性

`properties` 是開發人員所定義的屬性對應。

```json
"properties": {
    "myFirstProperty": {
        "displayName": "firstPropertyName",
        "type": ValueTypeDescriptor | StructuralTypeDescriptor
    }
}
```

> [!NOTE]
> `show` 是啟用參數來切換物件的特殊屬性。

範例︰

```json
"properties": {
    "show": {
        "displayName": "My Property Switch",
        "type": {"bool": true}
    }
}
```

### <a name="property-types"></a>屬性類型

屬性類型有兩種類型：`ValueTypeDescriptor` 和 `StructuralTypeDescriptor`。

#### <a name="value-type-descriptor"></a>實值類型描述項

`ValueTypeDescriptor` 類型大多是基本類型，且通常作為靜態物件使用。

以下是一些常見的 `ValueTypeDescriptor`元素：

```typescript
export interface ValueTypeDescriptor {
    text?: boolean;
    numeric?: boolean;
    integer?: boolean;
    bool?: boolean;
}
```

#### <a name="structural-type-descriptor"></a>結構類型描述項

`StructuralTypeDescriptor` 類型主要用於資料繫結物件。
最常見的 `StructuralTypeDescriptor` 類型是 *fill*。

```typescript
export interface StructuralTypeDescriptor {
    fill?: FillTypeDescriptor;
}
```

## <a name="gradient-property"></a>漸層屬性

漸層屬性是無法設定為標準屬性的屬性。 相反地，您必須設定要替代色彩選擇器屬性 (*fill* 類型) 的規則。

下列程式碼會顯示範例：

```json
"properties": {
    "showAllDataPoints": {
        "displayName": "Show all",
        "displayNameKey": "Visual_DataPoint_Show_All",
        "type": {
            "bool": true
        }
    },
    "fill": {
        "displayName": "Fill",
        "displayNameKey": "Visual_Fill",
        "type": {
            "fill": {
                "solid": {
                    "color": true
                }
            }
        }
    },
    "fillRule": {
        "displayName": "Color saturation",
        "displayNameKey": "Visual_ColorSaturation",
        "type": {
            "fillRule": {}
        },
        "rule": {
            "inputRole": "Gradient",
            "output": {
                "property": "fill",
                    "selector": [
                        "Category"
                    ]
            }
        }
    }
}
```

請注意 *fill* 和 *fillRule* 屬性。 第一個是色彩選擇器，而第二個則是漸層的替代規則，其會在符合規則條件時 `visually` 取代「fill 屬性」。

*fill* 屬性與替代規則之間的這個連結，是在 *fillRule* 屬性的 `"rule"`>`"output"` 區段中設定。

`"Rule"`>`"InputRole"` 屬性會設定哪一個資料角色會觸發規則 (條件)。 在此範例中，如果資料角色 `"Gradient"` 包含資料，則會針對 `"fill"` 屬性套用規則。

您可以在下列程式碼中看到觸發 fill 規則 (`the last item`) 的資料角色範例：

```json
{
    "dataRoles": [
            {
                "name": "Category",
                "kind": "Grouping",
                "displayName": "Details",
                "displayNameKey": "Role_DisplayName_Details"
            },
            {
                "name": "Series",
                "kind": "Grouping",
                "displayName": "Legend",
                "displayNameKey": "Role_DisplayName_Legend"
            },
            {
                "name": "Gradient",
                "kind": "Measure",
                "displayName": "Color saturation",
                "displayNameKey": "Role_DisplayName_Gradient"
            }
    ]
}
```

## <a name="the-enumerateobjectinstances-method"></a>enumerateObjectInstances 方法

若要有效地使用物件，您必須在自訂視覺效果中使用稱為 `enumerateObjectInstances` 的函式。 此函式會在屬性窗格中填入物件，也會決定應在 dataView 內繫結物件的位置。  

一般設定如下所示：

```typescript
public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
    let objectName: string = options.objectName;
    let objectEnumeration: VisualObjectInstance[] = [];

    switch( objectName ) {
        case 'myCustomObject':
            objectEnumeration.push({
                objectName: objectName,
                properties: { ... },
                selector: { ... }
            });
            break;
    };

    return objectEnumeration;
}
```

### <a name="properties"></a>屬性

`enumerateObjectInstances` 中的屬性會反映您在功能中定義的屬性。 如需範例，請移至此文章結尾。

### <a name="objects-selector"></a>物件選取器

`enumerateObjectInstances` 中選取器會決定每個物件在 dataView 中的繫結位置。 有四個不同的選項。

#### <a name="static"></a>靜態

此物件會繫結至中繼資料 `dataviews[index].metadata.objects`，如這裡所示。

```typescript
selector: null
```

#### <a name="columns"></a>資料行

此物件會繫結到具有相符 `QueryName` 的資料行。

```typescript
selector: {
    metadata: 'QueryName'
}
```

#### <a name="selector"></a>選取器

此物件會繫結至您其建立 `selectionID` 的元素。 在此範例中，假設我們已針對某些 dataPoints 建立 `selectionID`，且我們會以迴圈方式執行它們。

```typescript
for (let dataPoint in dataPoints) {
    ...
    selector: dataPoint.selectionID.getSelector()
}
```

#### <a name="scope-identity"></a>範圍識別

此物件會繫結到群組交集處的特定值。 例如，如果您有類別 `["Jan", "Feb", "March", ...]` 和序列 `["Small", "Medium", "Large"]`，您可能想要在符合 `Large` 和 `Feb` 的值交集處有一個物件。 為了達到這個目的，您可以取得這兩個資料行的 `DataViewScopeIdentity`，將它們推送至 `identities` 變數，並將此語法與選取器搭配使用。

```typescript
selector: {
    data: <DataViewScopeIdentity[]>identities
}
```

##### <a name="example"></a>範例

下列範例會針對具有單一屬性 *fill* 的 customColor 物件，顯示單一 objectEnumeration 的可能外觀。 我們想要讓此物件以靜態方式繫結至 `dataViews[index].metadata.objects`，如下所示：

```typescript
objectEnumeration.push({
    objectName: "customColor",
    displayName: "Custom Color",
    properties: {
        fill: {
            solid: {
                color: dataPoint.color
            }
        }
    },
    selector: null
});
```
