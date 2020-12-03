---
title: Power BI Desktop 中的查詢折疊指導方針
description: 在 Power BI Desktop 中達到 Power Query 查詢折疊的指導方針。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 11/09/2019
ms.openlocfilehash: 5e2ec32f3eeaff224256f0a84d2a5c23d3e882a5
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96419306"
---
# <a name="query-folding-guidance-in-power-bi-desktop"></a>Power BI Desktop 中的查詢折疊指導方針

本文適用於在 Power BI Desktop 中開發模型的製造資料模型者。 其中提供有關何時及如何達成 Power Query 查詢折疊的最佳做法指導方針。

_查詢折疊_ 是 Power Query 查詢的一項功能，可產生單一查詢陳述式來擷取和轉換來源資料。 如需詳細資訊，請參閱 [Power Query 查詢折疊](/power-query/power-query-folding)。

## <a name="guidance"></a>指引

根據模型模式，查詢摺疊指導方針會有所不同。

針對 **DirectQuery** 或 **雙重** 儲存模式資料表，Power Query 查詢必須達成查詢折疊。

針對 **匯入** 資料表，可能可以達成查詢折疊。 當查詢是以關聯式來源為基礎且可建構單一 SELECT 陳述式時，則確保進行查詢折疊有助於達成「最佳資料重新整理效能」  。 如果 Power Query 混搭引擎仍然必須處理轉換，則您應該致力於將其所需執行的工作減到最少，特別是針對大型資料集。

下列項目符號清單提供特定指導方針。

- **盡可能將最多處理委派給資料來源**：當無法折疊 Power Query 查詢的所有步驟時，找出防止查詢折疊的步驟。 可能的話，請將後續步驟移到較前面的順序，以便將其納入查詢折疊中。 請注意，Power Query 混搭引擎可能具有足夠的智慧，能夠在產生來源查詢時重新排序查詢步驟。

    針對關聯式資料來源，如果防止查詢折疊之步驟可在單一 SELECT 陳述式中或在預存程序的程序性邏輯內達成，請考慮使用原生 SQL 查詢，如下所述。

- **使用原生 SQL 查詢**：當 Power Query 查詢從關聯式來源擷取資料時，某些來源可以使用原生 SQL 查詢。 該查詢事實上可以是任何有效的陳述式，包括預存程序執行。 如果陳述式產生多個結果集，則只會傳回第一個結果集。 參數可以在陳述式中宣告，且建議您使用 [Value.NativeQuery](/powerquery-m/value-nativequery) M 函式。 此函式的設計訴求是要安全便利地傳遞參數值。 請務必了解 Power Query 混搭引擎無法折疊後續查詢步驟，因此您應該在原生查詢陳述式中包含所有 (或最多的) 轉換邏輯。

    使用原生 SQL 查詢時，有兩個需要謹記在心的重要考量：

    - 針對 DirectQuery 模型資料表，查詢必須是 SELECT 陳述式，且無法使用通用資料表運算式 (CTE) 或預存程序。
    - 累加式重新整理無法使用原生 SQL 查詢。 因此會強制 Power Query 混搭引擎擷取所有來源資料列，然後套用篩選來判斷累加的變更。

    > [!IMPORTANT]
    > 原生 SQL 查詢可能會比擷取資料達成更多目的。 您可以執行 (可能很多次) 任何有效的陳述式，包括修改或刪除資料的陳述式。 請務必套用最低權限原則，以確保用來存取資料庫的帳戶只具有必要資料的讀取權限。

- **準備和轉換來源中的資料**：當您發現無法折疊某些 Power Query 查詢步驟時，可能可以在資料來源中套用轉換。 透過撰寫以邏輯方式轉換來源資料的資料庫檢視即可完成轉換。 或者，在 Power BI 進行查詢之前，藉由實際準備資料並將其具體化來完成。 關聯式資料倉儲是備妥資料的絕佳範例，通常是由預先整合的組織資料來源所組成。

## <a name="next-steps"></a>後續步驟

如需本文的詳細資訊，請參閱下列資源︰

- Power Query [查詢摺疊](/power-query/power-query-folding)概念文章
- [Power BI Premium 中的累加式重新整理](../admin/service-premium-incremental-refresh.md)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
