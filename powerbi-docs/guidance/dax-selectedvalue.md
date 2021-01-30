---
title: DAX：使用 SELECTEDVALUE 而非 VALUES
description: 有關何時使用 SELECTEDVALUE 函式的指導方針。
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 11/20/2019
ms.openlocfilehash: aa6c1c9c20a08eb8e30492642a12c74137795d85
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088365"
---
# <a name="dax-use-selectedvalue-instead-of-values"></a>DAX：使用 SELECTEDVALUE 而非 VALUES

身為數據建模者，有時候您可能需要撰寫 DAX 運算式來測試資料行是否依特定值接受篩選。

在舊版的 DAX 中，您需要藉由使用包含三個 DAX 函式的模式，以確保達成這項需求。 這些函式為 [IF](/dax/if-function-dax)、[HASONEVALUE](/dax/hasonevalue-function-dax) 與 [VALUES](/dax/values-function-dax)。 下列量值定義會提供範例。 其會計算銷售稅額，但僅計算對澳洲客戶的銷售。

```dax
Australian Sales Tax =
IF(
    HASONEVALUE(Customer[Country-Region]),
    IF(
        VALUES(Customer[Country-Region]) = "Australia",
        [Sales] * 0.10
    )
)
```

在此範例中，只有當單一值篩選 **Country-Region** 資料行時，HASONEVALUE 函式才會傳回 TRUE。 當為 TRUE 時，VALUES 函式會與常值文字 "Australia" 進行比較。 當 VALUES 函式傳回 TRUE 時，**Sales** 量值會乘以 0.10 (代表 10%)。 如果 HASONEVALUE 函式傳回 FALSE (因為有一個以上的值篩選資料行)，則第一個 IF 函式會傳回 BLANK。

使用 HASONEVALUE 是一種防禦性技巧。 這是必需的，因為可能會有多個值篩選 **Country-Region** 資料行。 在此情況下，VALUES 函式會傳回多個資料列的資料表。 而將多個資料列的資料表與純量值進行比較，則會產生錯誤。

## <a name="recommendation"></a>建議

建議您使用 [SELECTEDVALUE](/dax/selectedvalue-function) 函式。 此函式具有與本文中所述模式相同的結果，但更簡練且更有效率。

使用 SELECTEDVALUE 函式時，會重寫範例量值定義。

```dax
Australian Sales Tax =
IF(
    SELECTEDVALUE(Customer[Country-Region]) = "Australia",
    [Sales] * 0.10
)
```

> [!TIP]
> 您可以將「替代結果」  值傳遞至 SELECTEDVALUE 函式。 當沒有任何篩選 (或多個篩選) 套用至資料行時，就會傳回替代結果值。

## <a name="next-steps"></a>後續步驟

如需本文的詳細資訊，請參閱下列資源︰

- [資料分析運算式 (DAX) 參考](/dax/)
- 學習路徑：[在 Power BI Desktop 中使用 DAX](/learn/paths/dax-power-bi/) (英文)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com)