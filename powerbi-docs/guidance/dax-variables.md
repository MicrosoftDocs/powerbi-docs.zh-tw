---
title: DAX：使用變數來改善公式
description: 在 DAX 運算式中使用變數的指導方針。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 11/23/2019
ms.openlocfilehash: 2448ac8b94465872e4224738162c6a252cafe56c
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96393592"
---
# <a name="dax-use-variables-to-improve-your-formulas"></a>DAX：使用變數來改善公式

身為資料建模者，撰寫某些 DAX 計算並對其偵錯可能非常具挑戰性。 複雜的計算需求通常需要撰寫複合或複雜的運算式。 複合運算式可能牽涉到使用許多巢狀函式，且可能重複使用運算式邏輯。

在 DAX 公式中使用變數可協助撰寫複雜且有效率的計算。 變數可以：

- [改善效能](#improve-performance)
- [改善可讀性](#improve-readability)
- [簡化偵錯](#simplify-debugging)
- [降低複雜度](#reduce-complexity)

在本文中，我們將使用年銷售成長 (YoY) 的範例量值來示範前三個優點。 (年銷售成長的公式為：期間銷售額 - 去年相同期間的較低銷售額，「除以」  去年相同期間的銷售額)

讓我們從下列量值定義開始。

```dax
Sales YoY Growth % =
DIVIDE(
    ([Sales] - CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))),
    CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))
)
```

此量值會產生正確的結果，但讓我們來進一步了解如何改善。

## <a name="improve-performance"></a>改善效能

請注意，該公式會重複計算「去年相同期間」的運算式。 這條公式很沒有效率，因為該公式需要 Power BI 評估相同的運算式兩次。 藉由使用變數，可讓此量值定義變得更有效率。

下列表示改善後的量值定義。 其會使用運算式，將「去年相同期間」的結果指派給名為 **SalesPriorYear** 的變數。 然後，該變數會在 RETURN 運算式中被使用兩次。

```dax
Sales YoY Growth % =
VAR SalesPriorYear =
    CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))
RETURN
    DIVIDE(([Sales] - SalesPriorYear), SalesPriorYear)
```

該量值會不斷地產生正確結果，並在大約一半的查詢時間內持續執行此動作。

## <a name="improve-readability"></a>改善可讀性

在先前的量值定義中，請注意，您所選擇的變數名稱能讓 RETURN 運算式變得更加容易理解。 這也讓該運算式更簡短且一看就懂。

## <a name="simplify-debugging"></a>簡化偵錯

變數也可以協助您對公式進行偵錯。 若要測試指派給變數的運算式，您可以暫時重寫 RETURN 運算式來輸出變數。

下列量值定義只會傳回 **SalesPriorYear** 變數。 請注意其如何將預定的 RETURN 運算式標記為註解。 這項技巧可讓您在完成偵錯後，再輕鬆地將運算式還原回來。

```dax
Sales YoY Growth % =
VAR SalesPriorYear =
    CALCULATE([Sales], PARALLELPERIOD('Date'[Date], -12, MONTH))
RETURN
    --DIVIDE(([Sales] - SalesPriorYear), SalesPriorYear)
    SalesPriorYear
```

## <a name="reduce-complexity"></a>降低複雜度

在舊版的 DAX 中，還未支援變數。 引進新篩選內容的複雜運算式，必須使用先前的 [EARLIER](/dax/earlier-function-dax) 或 [EARLIEST](/dax/earliest-function-dax) DAX 函式來參考外部篩選內容。 可惜的是，資料建模者們發現這些函式非常難以理解和使用。

變數一律會在您的 RETURN 運算式所套用的篩選之外接受評估。 基於上述理由，當您在修改過的篩選內容中使用變數時，其結果會與 EARLIEST 函式相同。 因此便不需要使用 EARLIER 或 EARLIEST 函式。 這表示您現在可以撰寫較不復雜且更容易理解的公式。

請考慮下列新增至 **Subcategory** 資料表中的計算結果欄定義。 其會根據 **Subcategory Sales** 資料行值，評估每個產品子類別的排名。

```dax
Subcategory Sales Rank =
COUNTROWS(
    FILTER(
        Subcategory,
        EARLIER(Subcategory[Subcategory Sales]) < Subcategory[Subcategory Sales]
    )
) + 1
```

EARLIER 函式是用來參考「目前資料列內容中」  的 **Subcategory Sales** 資料行值。

您可以使用變數 (而不是 EARLIER 函式) 來改善計算結果欄定義。 **CurrentSubcategorySales** 變數會將 **Subcategory Sales** 資料行值儲存在「目前資料列內容中」  ，而 RETURN 運算式會在修改過的篩選內容中使用該變數。

```dax
Subcategory Sales Rank =
VAR CurrentSubcategorySales = Subcategory[Subcategory Sales]
RETURN
    COUNTROWS(
        FILTER(
            Subcategory,
            CurrentSubcategorySales < Subcategory[Subcategory Sales]
        )
    ) + 1
```

## <a name="next-steps"></a>後續步驟

如需本文的詳細資訊，請參閱下列資源︰

- [資料分析運算式 (DAX) 參考](/dax/)
- [VAR](/dax/var-dax) DAX 一文
- 學習路徑：[在 Power BI Desktop 中使用 DAX](/learn/paths/dax-power-bi/) (英文)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com)