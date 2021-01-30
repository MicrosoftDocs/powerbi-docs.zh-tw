---
title: DAX：避免使用 FILTER 作為篩選引數
description: 使用 FILTER 函式作文篩選引數的指導。
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 12/30/2019
ms.openlocfilehash: 74ddac5a3ac2fa5e6e0fae9f3fdf5c7f79ba22d3
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088572"
---
# <a name="dax-avoid-using-filter-as-a-filter-argument"></a>DAX：避免使用 FILTER 作為篩選引數

身為資料建模者，您通常會撰寫需要在修改過篩選內容中評估的 DAX 運算式。 例如，您可以撰寫量值定義來計算「高利潤產品」的銷售。 我們將在本文稍後說明這項計算。

> [!NOTE]
> 本文特別適合將篩選條件套用至「匯入」資料表的模型計算。

[CALCULATE](/dax/calculate-function-dax) 和 [CALCULATETABLE](/dax/calculatetable-function-dax) DAX 函式是重要且有用的函式。 其可讓您撰寫可移除或新增篩選條件的計算，或修改關聯性路徑。 其做法是傳遞篩選引數，也就是布林運算式、資料表運算式或特殊篩選函式。 我們只會討論本文中的布林值和資料表運算式。

請考慮下列量值定義，其會使用資料表運算式來計算紅色產品銷售額。 其會取代可能套用至 **Product** 資料表的任何篩選條件。

```dax
Red Sales =
CALCULATE(
    [Sales],
    FILTER('Product', 'Product'[Color] = "Red")
)
```

CALCULATE 函式會接受 [FILTER](/dax/filter-function-dax) DAX 函式所傳回的資料表運算式，這會針對 **Product** 資料表的每個資料列評估其篩選運算式。 其會達到正確的結果，也就是紅色產品的銷售結果。 不過，使用布林運算式可以更有效率地達成此目的。

以下是已改良的量值定義，其使用布林運算式，而不是資料表運算式。 [KEEPFILTERS](/dax/keepfilters-function-dax) DAX 函式可確保套用至 **Color** 資料行的任何現有篩選都會保留，不會遭到覆寫。

```dax
Red Sales =
CALCULATE(
    [Sales],
    KEEPFILTERS('Product'[Color] = "Red")
)
```

我們建議您盡可能將篩選引數當作布林運算式傳遞。 這是因為「匯入」模型資料表位於記憶體內部資料行存放區。 其會進行明確最佳化，以這種方式有效地篩選資料行。

不過，當布林運算式當作篩選引數使用時適用下列限制。 其：

- 無法比較資料行與其他資料行
- 無法參考量值
- 無法使用巢狀 CALCULATE 函式
- 無法使用可掃描或傳回資料表的函式

這表示您必須使用資料表運算式，以符合更複雜的篩選需求。

現在考慮使用不同的量值定義。

```dax
High Margin Product Sales =
CALCULATE(
    [Sales],
    FILTER(
        'Product',
        'Product'[ListPrice] > 'Product'[StandardCost] * 2
    )
)
```

「高利潤產品」  的定義就是其定價超過其標準成本兩倍的產品。 在此範例中，可以使用 FILTER 函式。 這是因為篩選運算式對布林運算式而言太複雜。

以下還有一個範例。 這次的需求是要計算銷售額，但只限於已達到收益的月份。

```dax
Sales for Profitable Months =
CALCULATE(
    [Sales],
    FILTER(
        VALUES('Date'[Month]),
        [Profit] > 0)
    )
)
```

在此範例中，也必須使用 FILTER 函式。 這是因為其需要評估 **收益** 量值，以排除未達到收益的月份。 當布林運算式當作篩選引數使用時，不可能使用量值。

## <a name="recommendations"></a>建議

為了達到最佳效能，建議您盡可能使用布林運算式作為篩選引數。

因此，只有在必要時才使用 FILTER 函式。 您可以使用該函式來執行篩選複雜資料行比較。 這些資料行比較可能涉及：

- 量值
- 其他資料行
- 使用 [OR](/dax/or-function-dax) DAX 函式，或 OR 邏輯運算子 (||)

## <a name="next-steps"></a>後續步驟

如需本文的詳細資訊，請參閱下列資源︰

- [資料分析運算式 (DAX) 參考](/dax/)
- [篩選函式 (DAX)](/dax/filter-function-dax)
- 學習路徑：[在 Power BI Desktop 中使用 DAX](/learn/paths/dax-power-bi/) (英文)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com)