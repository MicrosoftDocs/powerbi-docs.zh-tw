---
title: 取得更佳的內嵌式 BI 見解：Power BI 內嵌式分析的 Power BI 視覺效果高對比模式支援
description: 此文章說明如何將高對比模式支援新增至 Power BI 視覺效果。 使用 Power BI 內嵌式分析，取得更佳的內嵌式 BI 見解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: f55427511a76fc65b3ae6b3933dca68ef742039c
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97889194"
---
# <a name="high-contrast-mode-support-in-power-bi-visuals"></a>Power BI 視覺效果中的高對比模式支援

Windows [高對比] 設定會透過顯示更相異的色彩，讓您更容易看清楚文字與應用程式。 此文章說明如何將高對比模式支援新增至 Power BI 視覺效果。 如需詳細資訊，請參閱 [Power BI 中的高對比支援](https://powerbi.microsoft.com/blog/power-bi-desktop-june-2018-feature-summary/#highContrast) \(英文\)。

若要檢視高對比支援的實作，請移至 [PowerBI-visuals-sampleBarChart 視覺效果存放庫](https://github.com/Microsoft/PowerBI-visuals-sampleBarChart/commit/61011c82b66ca0d3321868f1d089c65101ca42e6) \(英文\)。

## <a name="on-initialization"></a>初始化時

`options.host` 的 colorPalette 成員有數個高對比模式的屬性。 使用這些屬性來判斷高對比模式是否為使用中，以及在使用中的情況下要使用哪些色彩。

### <a name="detect-that-power-bi-is-in-high-contrast-mode"></a>偵測到 Power BI 處於高對比模式

如果 `host.colorPalette.isHighContrast` 為 `true`，則高對比模式為使用中，且視覺效果應據此繪製本身。

### <a name="get-high-contrast-colors"></a>取得高對比色彩

在高對比模式中，您的視覺效果應該將其本身限制為下列設定：

* **前景** 色彩用來繪製任何線條、圖示、文字和框線，或填滿圖形。
* **背景** 色彩用於背景，作為外框圖形的填滿色彩。
* **前景 - 已選取** 色彩用來表示選取的或使用中的元素。
* **超連結** 色彩僅用於超連結文字。

> [!NOTE]
> 如果需要次要色彩，前景色彩可能會與某些不透明度搭配使用 (Power BI 的原生視覺效果使用 40% 不透明度)。 請謹慎使用此功能，讓視覺效果詳細資料易於查看。

在初始化期間，您可以儲存下列值：

```typescript
private isHighContrast: boolean;

private foregroundColor: string;
private backgroundColor: string;
private foregroundSelectedColor: string;
private hyperlinkColor: string;
//...

constructor(options: VisualConstructorOptions) {
    this.host = options.host;
    let colorPalette: ISandboxExtendedColorPalette = host.colorPalette;
    //...
    this.isHighContrast = colorPalette.isHighContrast;
    if (this.isHighContrast) {
        this.foregroundColor = colorPalette.foreground.value;
        this.backgroundColor = colorPalette.background.value;
        this.foregroundSelectedColor = colorPalette.foregroundSelected.value;
        this.hyperlinkColor = colorPalette.hyperlink.value;
    }
```

或者，您可以在初始化期間儲存 `host` 物件，並在更新期間存取相關的 `colorPalette` 屬性。

## <a name="on-update"></a>在更新時

高對比支援的特定實作會因視覺效果而異，且取決於圖形設計的詳細資料。 為了在色彩有限的情況下讓重要詳細資料更容易區別，高對比模式通常會要求使用與預設模式稍有不同的設計。

Power BI 原生視覺效果會遵循這些指導方針：

* 所有資料點都會使用相同的色彩 (前景)。
* 所有文字、軸、箭號、線條等都會使用前景色彩。
* 粗圖形會繪製為外框，並使用粗筆觸 (至少兩個像素) 和背景色彩填滿。
* 當資料點相關時，它們會以不同的標記圖形來區分，而資料線條則是以不同的虛線來區分。
* 醒目提示資料元素時，所有其他元素都會將其不透明度變更為 40%。
* 若為交叉分析篩選器，使用中篩選元素會使用前景選取的色彩。

例如在下列範例橫條圖中，所有橫條都會以兩個像素的粗前景外框和背景填滿來繪製。 請比較它使用預設色彩與使用幾個高對比主題的外觀：

![使用標準色彩的範例橫條圖](media/high-contrast-support/hc-samplebarchart-standard.png)
![使用*深色 #2* 色彩主題的範例橫條圖](media/high-contrast-support/hc-samplebarchart-dark2.png)
![使用*白色*色彩主題的範例橫條圖](media/high-contrast-support/hc-samplebarchart-white.png)

下一節會說明 `visualTransform` 函式中為了支援高對比而變更的一個地方。 它會作為更新期間轉譯的一部分進行呼叫。

### <a name="before"></a>之前

```typescript
for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
    let defaultColor: Fill = {
        solid: {
            color: colorPalette.getColor(category.values[i] + '').value
        }
    };

    barChartDataPoints.push({
        category: category.values[i] + '',
        value: dataValue.values[i],
        color: getCategoricalObjectValue<Fill>(category, i, 'colorSelector', 'fill', defaultColor).solid.color,
        selectionId: host.createSelectionIdBuilder()
            .withCategory(category, i)
            .createSelectionId()
    });
}
```

### <a name="after"></a>After

```typescript
for (let i = 0, len = Math.max(category.values.length, dataValue.values.length); i < len; i++) {
    const color: string = getColumnColorByIndex(category, i, colorPalette);

    const selectionId: ISelectionId = host.createSelectionIdBuilder()
        .withCategory(category, i)
        .createSelectionId();

    barChartDataPoints.push({
        color,
        strokeColor,
        strokeWidth,
        selectionId,
        value: dataValue.values[i],
        category: `${category.values[i]}`,
    });
}

//...

function getColumnColorByIndex(
    category: DataViewCategoryColumn,
    index: number,
    colorPalette: ISandboxExtendedColorPalette,
): string {
    if (colorPalette.isHighContrast) {
        return colorPalette.background.value;
    }

    const defaultColor: Fill = {
        solid: {
            color: colorPalette.getColor(`${category.values[index]}`).value,
        }
    };

    return getCategoricalObjectValue<Fill>(category, index, 'colorSelector', 'fill', defaultColor).solid.color;
}
```
