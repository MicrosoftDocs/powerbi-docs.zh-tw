---
title: DAX：使用 COUNTROWS 而非 COUNT
description: 有關何時使用 COUNTROWS 函式的指導方針。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 11/23/2019
ms.openlocfilehash: 1a2b8c6450cfd855a0018fb64dd385a0db6e350f
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96394190"
---
# <a name="dax-use-countrows-instead-of-count"></a>DAX：使用 COUNTROWS 而非 COUNT

身為資料建模者，有時候您可能需要撰寫可計算資料表資料列的 DAX 運算式。 而該資料表可能為模型資料表或傳回資料表的運算式。

您的需求可透過兩種方式來達成。 您可以使用 [COUNT](/dax/count-function-dax) 函式來計算資料行值，也可以使用 [COUNTROWS](/dax/countrows-function-dax) 函式來計算資料表資料列。 只要計算的資料行不包含 BLANK，則這兩個函式就會有相同的結果。

下列量值定義會提供範例。 其會計算 **OrderDate** 資料行值的數目。

```dax
Sales Orders =
COUNT(Sales[OrderDate])
```

假設 **Sales** 資料表的資料粒度為每筆銷售訂單有一個資料列，且 **OrderDate** 資料行不包含 BLANK，則該量值便會傳回正確的結果。

不過，下列量值定義會提供更佳的解決方案。

```dax
Sales Orders =
COUNTROWS(Sales)
```

第二個量值定義較佳的原因有三個：

- 效率更高，因此效能會更好。
- 該量值定義不會考慮資料表中的任何資料行所包含的 BLANK。
- 公式的目的因其名稱可一目瞭然而更加清楚。

## <a name="recommendation"></a>建議

當您想要計算資料表資料列時，建議您一律使用 COUNTROWS 函式。

## <a name="next-steps"></a>後續步驟

如需本文的詳細資訊，請參閱下列資源︰

- [資料分析運算式 (DAX) 參考](/dax/)
- 學習路徑：[在 Power BI Desktop 中使用 DAX](/learn/paths/dax-power-bi/) (英文)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com)