---
title: DAX：避免將 BLANK 轉換成值
description: 避免將 BLANK 轉換成值的相關指導。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 11/24/2019
ms.openlocfilehash: 20686615c58015040349138ffd49b544c5dac70a
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96394259"
---
# <a name="dax-avoid-converting-blanks-to-values"></a>DAX：避免將 BLANK 轉換成值

身為資料建模者，您在撰寫量值運算式時，可能會遇到無法傳回有意義值的情況。 在這些情況下，您可能想要改為傳回某個值 (例如零)。 我們建議您仔細判斷這種設計是否有效率且實用。

請考慮下列將 BLANK 結果明確轉換為零的量值定義。

```dax
Sales (No Blank) =
IF(
    ISBLANK([Sales]),
    0,
    [Sales]
)
```

請考慮另一個也會將 BLANK 結果轉換為零的量值定義。

```dax
Profit Margin =
DIVIDE([Profit], [Sales], 0)
```

[DIVIDE](/dax/divide-function-dax) 函式會將 **Profit** 量值 (收益) 除以 **Sales** 量值。 如果結果為零或 BLANK，則會傳回第三個引數 (選擇性的替代結果)。 在此範例中，由於零會作為替代結果傳遞，因此量值一律會傳回值。

這些量值設計沒有效率，因而導致報表設計不佳。

當這些量值設計新增至報表視覺效果時，Power BI 會嘗試擷取篩選內容中的所有群組。 評估和擷取大型查詢結果通常會導致報表呈現速度變慢。 每個範例量值都會有效地將稀疏計算轉換成密集計算，進而迫使 Power BI 使用比所需更多的記憶體。

此外，太多群組通常會造成報表使用者負擔過重。

讓我們看看當 **Profit Margin** 量值新增至資料表視覺效果 (依客戶進行分組) 時所發生的情況。

![Power B I Desktop 的螢幕擷取畫面，其中顯示每位客戶皆擁有一個資料列的資料其資料表視覺效果。 Sales 值為 BLANK，且 Profit Margin 值為零/美分。 ](media/dax-avoid-converting-blank/table-visual-poor.png)

資料表視覺效果會顯示大量的資料列。 (事實上，此模型中有 18,484 位客戶，因此資料表會嘗試顯示所有客戶。)請注意，檢視中的客戶尚未達成任何銷售額。 不過，由於 **Profit Margin** 量值一律會傳回值，因此予以顯示。

> [!NOTE]
> 當視覺效果中有太多資料點要顯示時，Power BI 可能會使用資料縮減策略來移除或彙總大型查詢結果。 如需詳細資訊，請參閱[依視覺效果類型區分的資料點限制和策略](../visuals/power-bi-data-points.md)。

讓我們看看當 **Profit Margin** 量值定義經改善時所發生的情況。 現在，只有在 **Sales** 量值不是 BLANK (或零) 時，才會傳回值。

```dax
Profit Margin =
DIVIDE([Profit], [Sales])
```

資料表視覺效果現在只會顯示目前篩選內容中已進行銷售的客戶。 改善的量值可讓報表使用者擁有更有效率且更實用的體驗。

![Power B I Desktop 的螢幕擷取畫面，其中顯示已篩選內容資料的資料表視覺效果。](media/dax-avoid-converting-blank/table-visual-good.png)

> [!TIP]
> 如有必要，您可以藉由啟用 [[顯示沒有資料的項目]](../create-reports/desktop-show-items-no-data.md) 選項，將視覺效果設定為顯示篩選內容中的所有群組 (傳回值或 BLANK)。

## <a name="recommendation"></a>建議

如果無法傳回有意義的值，則建議讓量值傳回 BLANK。

這種設計方式很有效率，可以讓 Power BI 更快地呈現報表。 此外，傳回 BLANK 較佳的原因是因為當摘要為 BLANK 時，報表視覺效果預設會排除群組。

## <a name="next-steps"></a>後續步驟

如需本文的詳細資訊，請參閱下列資源︰

- [資料分析運算式 (DAX) 參考](/dax/)
- 學習路徑：[在 Power BI Desktop 中使用 DAX](/learn/paths/dax-power-bi/) (英文)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com)