---
title: 條件式格式設定
description: 了解如何將「設定格式化的條件」套用到您的 Power BI 視覺效果專案
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.topic: how-to
ms.subservice: powerbi-custom-visuals
ms.date: 10/27/2020
ms.openlocfilehash: 5243d1eda3fef2c7b82350fb0ca2669eb43c7623
ms.sourcegitcommit: b5365df7fc32b7c49f8a2bf2cf75b5edd6bda9b6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513823"
---
# <a name="add-conditional-formatting"></a>新增條件式格式設定

[設定格式化的條件](../../visuals/service-tips-and-tricks-for-color-formatting.md#conditional-formatting-for-visualizations)可讓報表建立者根據數值指定色彩在報表中的顯示方式。

此文章說明如何將「設定格式化的條件」功能新增到您的 Power BI 視覺效果。

「設定格式化的條件」只能套用到下列屬性類型：
* Color
* Text
* 圖示
* Web URL

## <a name="add-conditional-formatting-to-your-project"></a>將「設定格式化的條件」新增到您的專案

此節說明如何將「設定格式化的條件」新增到現有的 Power BI 視覺效果。 此文章中的範例程式碼是以 [SampleBarChart](https://github.com/microsoft/PowerBI-visuals-sampleBarChart) \(英文\) 視覺效果為基礎。 您可以在 [barChart.ts](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/master/src/barChart.ts) \(英文\) 中檢查原始程式碼。

### <a name="add-a-conditional-color-formatting-entry-in-the-format-pane"></a>在 [格式] 窗格中新增條件式色彩格式化項目

在此節中，您將了解如何將條件式色彩格式化項目新增到 [格式] 窗格中的資料點。

1. 您將會使用 `VisualObjectInstance` 中的 `propertyInstanceKind` 陣列，其是由 `powerbi-visuals-api` 公開。 第一個步驟是確認您的檔案包含此匯入：

    ```typescript
    import powerbiVisualsApi from "powerbi-visuals-api";
    ```

2. 若要指定適當的格式化類型 (*Constant*、*ConstantOrRule* 或 *Rule*)，您必須使用 `VisualEnumerationInstanceKinds` 列舉。 將下列匯入新增到您的檔案：

    ```typescript
    import VisualEnumerationInstanceKinds = powerbiVisualsApi.VisualEnumerationInstanceKinds;
    ```

3. 在 `propertyInstanceKind` 陣列下列出您想要支援「設定格式化的條件」的所有屬性。 在 `enumerateObjectInstances` 方法中定義這些屬性。

    ```typescript
    public enumerateObjectInstances(options: EnumerateVisualObjectInstancesOptions): VisualObjectInstanceEnumeration {
            …
            case 'colorSelector':
                …
                    objectEnumeration.push({
                        objectName: objectName,
                        displayName: barDataPoint.category,
                        properties: {
                            fill: {
                                solid: {
                                    color: barDataPoint.color
                                }
                            }
                        },
                        selector: dataViewWildcard.createDataViewWildcardSelector(dataViewWildcard.DataViewWildcardMatchingOption.InstancesAndTotals),
                        altConstantValueSelector: barDataPoint.selectionId.getSelector(),

                        // List your conditional formatting properties
                        propertyInstanceKind: {
                            fill: VisualEnumerationInstanceKinds.ConstantOrRule
                        }
                    });
                }
            …
    }

    ```

    `VisualEnumerationInstanceKinds.ConstantOrRule` 將會同時建立「設定格式化的條件」UI 項目與常數格式化 UI 元素。

    >[!div class="mx-imgBorder"]
    >![在 Power BI 中顯示之設定格式化的條件按鈕的螢幕擷取畫面，其位於一般色彩按鈕旁邊。](media/conditional-formatting/conditional-formatting-ui.png)

### <a name="define-how-conditional-formatting-behaves"></a>定義「設定格式化的條件」的行為

定義要如何將格式化套用到您的資料點。

使用在 `powerbi-visuals-utils-dataviewutils` 底下宣告的 `createDataViewWildcardSelector`，指定「設定格式化的條件」是要套用到例項、總計或兩者。 如需詳細資訊，請參閱 [DataViewWildcard](utils-dataview.md#)。

在 `enumerateObjectInstances` 中，對您想要套用「設定格式化的條件」的物件做出下列變更：

 * 以 `dataViewWildcard.createDataViewWildcardSelector(dataViewWildcardMatchingOption)` 呼叫取代 `selector` 值。 `DataViewWildcardMatchingOption` 會定義「設定格式化的條件」是要套用到例項、總計或兩者。

* 搭配先前針對 `selector` 屬性所定義的值來新增 `altConstantValueSelector` 屬性。

```typescript
case 'colorSelector':
         …
            objectEnumeration.push({
                objectName: objectName,
                displayName: barDataPoint.category,
                properties: {
                    fill: {
                        solid: {
                            color: barDataPoint.color
                        }
                    }
                },

                // Define whether the conditional formatting will apply to instances, totals, or both
                selector: dataViewWildcard.createDataViewWildcardSelector(dataViewWildcard.DataViewWildcardMatchingOption.InstancesAndTotals),

                // Add this property with the value previously defined for the selector property
                altConstantValueSelector: barDataPoint.selectionId.getSelector(),

                propertyInstanceKind: { 
                    fill: VisualEnumerationInstanceKinds.ConstantOrRule
                }
            });
        }

```

## <a name="next-steps"></a>後續步驟

檢閱 [DataViewUtils](utils-dataview.md) 一文。