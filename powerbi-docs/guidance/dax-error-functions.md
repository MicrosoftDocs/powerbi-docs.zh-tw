---
title: DAX：誤差函數的適當用法
description: 有關何時使用 DAX 誤差函式的指導方針。
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 09/26/2019
ms.openlocfilehash: c0766a989ea3dbfe42620fd53b4c49d6144b4c5f
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088457"
---
# <a name="dax-appropriate-use-of-error-functions"></a>DAX：誤差函數的適當用法

身為資料模型製告者，當您撰寫可能引發評估階段錯誤的 DAX 運算式時，可以考慮使用兩個實用的 DAX 函式。

- [ISERROR](/dax/iserror-function-dax) 函式接受單一運算式，且會在該運算式導致錯誤時傳回 TRUE。
- [IFERROR](/dax/iferror-function-dax) 函式，它接受兩個運算式。 若第一個運算式導致錯誤，則會傳回第二個運算式的值。 它實際上是將 ISERROR 函式以巢狀方式放在 [IF](/dax/if-function-dax) 運算式中更最佳化的實作。

不過，雖然這些函式很有幫助，而且有助於撰寫容易了解的運算式，但它們也會大幅影響計算效能。 發生原因是因為這些函式會增加需要的儲存體引擎掃描數目。

大部分評估階段錯誤都是由於非預期的 BLANK 或零值，或無效的資料類型轉換。

## <a name="recommendations"></a>建議

最好避免使用 ISERROR 與 IFERROR 函式。 開發模型及撰寫運算式時，建議改為套用防禦性策略。 策略可以包括：

- **確定品質資料已載入到模型中：** 使用 Power Query 轉換來移除或取代無效或遺失的值。以及設定正確的資料類型。 Power Query 轉換也可以在發生錯誤 (例如無效的資料轉換) 時用來篩選列。

    資料品質也可以透過將模型資料行 **Is Nullable** 屬性設定為關閉 (這會在遇到 BLANK 時讓資料重新整理失敗) 來控制。 若發生此錯誤，因為成功重新整理而載入的資料將會維持在資料表中。
- **使用 IF 函式：** IF 函式邏輯測試運算式可判斷是否會發生錯誤結果。 請注意，就像 ISERROR 與 IFERROR 函式一樣，此函式也會導致額外的儲存體引擎掃描，但可能會比它們執行得更好，因為不需要引發錯誤。
- **使用容錯函式：** 某些 DAX 函式將會測試及補償錯誤情況。 這些函式可讓您輸入替代結果來取代將會傳回的結果。 [DIVIDE](/dax/divide-function-dax) 函式是一個這樣的範例。 如需有關此函式的其他指導方針，請參閱 [DAX：DIVIDE 函式與除法運算子 (/) 的比較](dax-divide-function-operator.md)一文。

## <a name="example"></a>範例

下列測量運算式會測試是否應該引發錯誤。 它在此範例中會傳回 BLANK (也就是當您沒有為 IF 函式提供 value-if-false 運算式的情況)。

```dax
Profit Margin
= IF(ISERROR([Profit] / [Sales]))
```

這個測量運算式的後續版本已透過使用 IFERROR 運算式取代 IF 與 ISERROR 函式來改進。

```dax
Profit Margin
= IFERROR([Profit] / [Sales], BLANK())
```

不過，這個最終版本的測量運算式可達到相同的結果，但效率更高且更簡潔。

```dax
Profit Margin
= DIVIDE([Profit], [Sales])
```

## <a name="next-steps"></a>後續步驟

如需本文的詳細資訊，請參閱下列資源︰

- [資料分析運算式 (DAX) 參考](/dax/)

- 學習路徑：[在 Power BI Desktop 中使用 DAX](/learn/paths/dax-power-bi/) (英文)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com)