---
title: DAX：資料行和量值參考
description: 在 DAX 運算式中參考資料行和量值的指導。
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 12/18/2019
ms.openlocfilehash: 3d9f4ea374783b90705a8ec5644d67ddc5d1168b
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088526"
---
# <a name="dax-column-and-measure-references"></a>DAX：資料行和量值參考

作為資料模組工具，DAX 運算式會參考模型資料行和量值。 資料行和量值一律會與模型資料表建立關聯，但這些關聯並不相同。 因此，對於您在運算式中參考資料行和量值的方式，我們有不同的建議。

## <a name="columns"></a>行

資料行是資料表層級物件，且資料行名稱在資料表中必須是唯一的。 因此，可能會在您的模型中多次使用相同資料行名稱，前提是這些資料行名稱屬於不同資料表。 還有另一項規則：資料行名稱不能與存在於同一資料表中的量值名稱或階層名稱相同。

一般來說，DAX 不會強制使用資料行的「完整」  參考。 完整參考表示資料表名稱位在資料行名稱之前。

以下是只使用資料行名稱參考的計算資料行定義範例。 **Sales** 和 **Cost** 資料行都屬於名為 **Orders** 的資料表。

```dax
Profit = [Sales] - [Cost]
```

相同定義可以使用完整的資料行參考加以改寫。

```dax
Profit = Orders[Sales] - Orders[Cost]
```

不過，有時候當 Power BI 偵測到語意不明確時，您必須使用完整的資料行參考。 在輸入公式時，系統會發出紅色曲線和錯誤訊息等警示。 此外，某些 DAX 函式 (例如 [LOOKUPVALUE](/dax/lookupvalue-function-dax) DAX 函式) 需要使用完整的資料行。

我們建議您一律完整限定資料行參考。 [建議](#recommendations)一節中會提供這些原因。

## <a name="measures"></a>量值

量值是模型層級物件。 基於這個理由，量值名稱在模型內必須是唯一的。 不過，在 [欄位]  窗格中，報表作者會看到每個與單一模型資料表建立關聯的量值。 此關聯是基於外觀原因而設定，您可以透過設定量值的 [主資料表]  屬性來進行設定。 如需詳細資訊，請參閱 [Power BI Desktop 中的量值 (組織您的量值)](../transform-model/desktop-measures.md#organizing-your-measures)。

您可以在運算式中使用完整的量值。 DAX Intellisense 甚至會提供建議。 不過，這並非必要，也不是建議的做法。 如果您變更量值的主資料表，任何使用其完整量值參考的運算式都會中斷。 接著，您必須編輯每個中斷的公式，以移除 (或更新) 量值參考。

我們建議您絕對不要限定量值參考。 [建議](#recommendations)一節中會提供這些原因。

## <a name="recommendations"></a>建議

我們的建議簡單易記：

- 一律使用完整的資料行參考
- 絕對不要使用完整的量值參考

原因如下：

- **公式輸入**：將會接受運算式，因為不會有任何待解決的不明確參考。 此外，對於需要完整資料行參考的 DAX 函式，您也會符合其需求。
- **健全性**：即使您變更了量值主資料表屬性，運算式仍會繼續運作。
- **可讀性**：運算式既快速又容易了解，您可以根據參考是否完整來快速判斷其是資料行或量值。

## <a name="next-steps"></a>後續步驟

如需本文的詳細資訊，請參閱下列資源︰

- [資料分析運算式 (DAX) 參考](/dax/)
- 學習路徑：[在 Power BI Desktop 中使用 DAX](/learn/paths/dax-power-bi/) (英文)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com)