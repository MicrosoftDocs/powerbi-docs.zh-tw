---
title: 參考 Power Query 查詢
description: 參考 Power Query 查詢的指導方針。
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 11/30/2019
ms.openlocfilehash: 59ba1454b1409e13587d1c1bae75e06025fa72ea
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99087399"
---
# <a name="referencing-power-query-queries"></a>參考 Power Query 查詢

此文章以使用 Power BI Desktop 的資料模型製作人員為目標。 它提供的指導方針，適用於定義參考其他查詢的 Power Query 查詢。

讓我們清楚說明這是什麼意思：「當某個查詢參考第二個查詢時，就如同第二個查詢中的步驟與第一個中的結合而且先執行。」

請考慮數個查詢：**Query1** 的資料來源是 Web 服務，且其載入已停用。 **Query2**、**Query3** 與 **Query4** 都參考 **Query1**，且其輸出會載入至資料模型。

![此圖表顯示查詢相依性檢視，其中顯示上一段所述的查詢。](media/power-query-referenced-queries/query-dependencies-web-service.png)

當資料模型重新整理時，通常會假設 Power Query 是擷取 **Query1** 的結果，且參考查詢會重複使用它。 此想法不正確。 事實上，Power Query 會分別執行 **Query2**、**Query3** 與 **Query4**。

您可以想成 **Query1** 步驟內嵌在 **Query2** 中。 **Query3** 與 **Query4** 的情況也是如此。 下列圖表呈現更清楚的查詢執行方式。

![此圖表顯示查詢相依性檢視的修改版本，其中顯示 Query 2、Query 3 與 Query 4。](media/power-query-referenced-queries/query-dependencies-web-service-concept.png)

**Query1** 會執行三次。 多次執行可能會導致資料重新整理緩慢，並對資料來源造成負面影響。

在 **Query1** 中使用 [Table.Buffer](/powerquery-m/table-buffer) 函式，不會消除額外資料擷取。 此函式會在記憶體緩衝資料表。 而且，已緩衝的資料表只能在相同查詢執行中使用。 因此，在範例中，如果在執行 **Query2** 時緩衝 **Query1**，則在執行 **Query3** 與 **Query4** 時，會無法使用已緩衝的資料。 它們本身會再緩衝資料兩次。 (事實上，此結果可能會造成負面效能惡化，因為每個參考查詢都會緩衝該資料表。)

> [!NOTE]
> Power Query 快取架構很複雜，而且不是此文章的焦點。 Power Query 可以快取從資料來源擷取的資料。 不過，當它執行查詢時，可能會多次從資料來源擷取資料。

## <a name="recommendations"></a>建議

一般來說，我們建議您參考查詢，以避免在整個查詢中重複邏輯。 不過，如此文章所述，此設計方法可能造成資料重新整理變慢，且使資料來源負擔過重。

我們建議您改為建立[資料流程](../transform-model/dataflows/dataflows-introduction-self-service.md)。 使用資料流程可以改善資料重新整理時間，並降低對資料來源的影響。

您可以設計資料流程來封裝來源資料和轉換。 因為資料流程是 Power BI 服務中的持續性資料存放區，所以其資料擷取速度很快。 因此，即使參考查詢導致多個資料流程要求，資料重新整理時間仍可獲得改善。

在此範例中，如果將 **Query1** 重新設計為資料流程實體，則 **Query2**、**Query3** 與 **Query4** 可以將它作為資料來源使用。 若使用此設計，系統只會評估 **Query1** 的來源實體一次。

## <a name="next-steps"></a>後續步驟

如需本文的詳細資訊，請參閱下列資源：

- [Power BI 中的自助資料準備](../transform-model/dataflows/dataflows-introduction-self-service.md)
- [在 Power BI 中建立及使用資料流程](../transform-model/dataflows/dataflows-create.md)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com/)