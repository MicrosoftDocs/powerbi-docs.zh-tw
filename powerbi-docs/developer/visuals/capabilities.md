---
title: 取得更佳的內嵌式 BI 見解：Power BI 內嵌式分析中的 Power BI 視覺效果功能與屬性
description: 此文章說明 Power BI 視覺效果的功能和屬性。 使用 Power BI 內嵌式分析，取得更佳的內嵌 BI 見解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: e0fb17053ff8e6d17321994d515d8b69dbe8e22b
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888251"
---
# <a name="capabilities-and-properties-of-power-bi-visuals"></a>Power BI 視覺效果的功能和屬性 

您使用功能將視覺效果的相關資訊提供給主機。 功能模型上的所有屬性都是 `optional`。

視覺效果功能的根物件是 `dataRoles`、`dataViewMappings` 等。

```json
{
    "dataRoles": [ ... ],
    "dataViewMappings": [ ... ],
    "objects":  { ... },
    "supportsHighlight": true|false,
    "advancedEditModeSupport": 0|1|2,
    "sorting": { ... }
}

```

## <a name="define-the-data-fields-that-your-visual-expects-dataroles"></a>定義您視覺效果預期的資料欄位：dataRoles

若要定義可以繫結至資料的欄位，請使用 `dataRoles`。 `dataRoles` 接受定義所有必要屬性的 `DataViewRole` 物件陣列。

### <a name="properties"></a>屬性

* **name**：此資料欄位的內部名稱 (必須是唯一的)。
* **kind**：欄位種類：
    * `Grouping`：用來分組量值欄位的離散值。
    * `Measure`：數值資料值。
    * `GroupingOrMeasure`：可以當作分組或量值使用的值。
* **displayName**：在 [屬性] 窗格中顯示給使用者的名稱。
* **description**：欄位的簡短描述 (選擇性)。
* **requiredTypes**：此資料角色所需的資料類型。 任何不符合的值都會設定為 Null (選擇性)。
* **preferredTypes**：此資料角色慣用的資料類型 (選擇性)。

### <a name="valid-data-types-in-requiredtypes-and-preferredtypes"></a>requiredTypes 和 preferredTypes 中的有效資料類型

* **bool**：布林值
* **integer**：整數值
* **numeric**：數值
* **text**：文字值
* **geography**：地理資料

### <a name="example"></a>範例

```json
"dataRoles": [
    {
        "displayName": "My Category Data",
        "name": "myCategory",
        "kind": "Grouping",
        "requiredTypes": [
            {
                "text": true
            },
            {
                "numeric": true
            },
            {
                "integer": true
            }
        ],
        "preferredTypes": [
            {
                "text": true
            }
        ]
    },
    {
        "displayName": "My Measure Data",
        "name": "myMeasure",
        "kind": "Measure",
        "requiredTypes": [
            {
                "integer": true
            },
            {
                "numeric": true
            }
        ],
        "preferredTypes": [
            {
                "integer": true
            }
        ]
    },
    {
        "displayNameKey": "Visual_Location",
        "name": "Locations",
        "kind": "Measure",
        "displayName": "Locations",
        "requiredTypes": [
            {
                "geography": {
                    "address": true
                }
            },
            {
                "geography": {
                    "city": true
                }
            },
            {
                "geography": {
                    "continent": true
                }
            },
            {
                "geography": {
                    "country": true
                }
            },
            {
                "geography": {
                    "county": true
                }
            },
            {
                "geography": {
                    "place": true
                }
            },
            {
                "geography": {
                    "postalCode": true
                }
            },
            {
                "geography": {
                    "region": true
                }
            },
            {
                "geography": {
                    "stateOrProvince": true
                }
            }
        ]
    }
]
```

上述資料角色會建立顯示在下列影像中的欄位：

![資料角色欄位](media/capabilities/data-role-display.png)

## <a name="define-how-you-want-the-data-mapped-dataviewmappings"></a>定義您要對應資料的方式：dataViewMappings

DataViewMappings 屬性描述資料角色的相互關係，並可讓您指定其條件式需求。

大部分的視覺效果都提供單一對應，但您可以提供多個 dataViewMappings。 每個有效對應都會產生資料檢視。 

```json
"dataViewMappings": [
    {
        "conditions": [ ... ],
        "categorical": { ... },
        "table": { ... },
        "single": { ... },
        "matrix": { ... }
    }
]
```

如需詳細資訊，請參閱[了解 Power BI 視覺效果中的資料檢視對應](dataview-mappings.md)。

## <a name="define-property-pane-options-objects"></a>定義屬性窗格選項：objects

Objects 描述與視覺效果相關聯的可自訂屬性。 每個物件都可以有多個屬性，且每個屬性都有一個與其建立關聯的類型。 類型指的是屬性內容。 

```json
"objects": {
    "myCustomObject": {
        "displayName": "My Object Name",
        "properties": { ... }
    }
}
```

如需詳細資訊，請參閱 [Power BI 視覺效果的物件和屬性](objects-properties.md)。

## <a name="handle-partial-highlighting-supportshighlight"></a>處理部分醒目提示：supportsHighlight

根據預設，此值是設定為 `false`，表示當您選取頁面上的項目時，系統會自動篩選值。 此自動篩選功能會依序更新您的視覺效果，只顯示所選取的值。 如果您想要顯示完整的資料，但只醒目提示選取的項目，則您必須在 *capabilities.json* 檔案中將 `supportsHighlight` 設定為 `true`。

如需詳細資訊，請參閱[在 Power BI 視覺效果中醒目提示資料點](highlight.md)。

## <a name="handle-advanced-edit-mode-advancededitmodesupport"></a>處理進階編輯模式：advancedEditModeSupport

視覺效果可以宣告其進階編輯模式支援。 根據預設，除非在 *capabilities json* 檔案中另有說明，否則視覺效果不支援進階編輯模式。

如需詳細資訊，請參閱 [Power BI 視覺效果中的進階編輯模式](advanced-edit-mode.md)。

## <a name="data-sorting-options-for-visual-sorting"></a>視覺效果的資料排序選項：sorting

視覺效果可以透過其功能來定義其排序行為。 根據預設，除非在 *capabilities.json* 檔案中另有說明，否則視覺效果不支援修改其排序次序。

如需詳細資訊，請參閱 [Power BI 視覺效果的排序選項](sort-options.md)。
