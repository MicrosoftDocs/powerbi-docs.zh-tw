---
title: Power BI Desktop 中的複合模型指引
description: 適用於開發複合模型的指引。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 12/24/2019
ms.openlocfilehash: e4ddc487f81835edfdc5ad8a4074a91204ee0336
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97884778"
---
# <a name="composite-model-guidance-in-power-bi-desktop"></a>Power BI Desktop 中的複合模型指引

此文章適用於開發 Power BI 複合模型的資料模型製作人員。 其描述複合模型使用案例，並提供設計指引。 具體而言，本指引能協助您判斷複合模型是否適用於您的解決方案。 如果是，則此文章也能協助您設計最佳模型。

> [!NOTE]
> 此文章並未涵蓋複合模型的簡介。 如果您尚未完全熟悉複合模型，建議您先閱讀[在 Power BI Desktop 中使用複合模型](../transform-model/desktop-composite-models.md)一文。
>
> 由於複合模型至少會包含一個 DirectQuery 來源，您也應該徹底了解[模型關聯性](../transform-model/desktop-relationships-understand.md)、[DirectQuery 模型](../connect-data/desktop-directquery-about.md)，以及 [DirectQuery 模型設計指引](directquery-model-guidance.md)。

## <a name="composite-model-use-cases"></a>複合模型使用案例

可能的話，最好在 [匯入] 模式中開發模型。 此模式能提供最佳的設計彈性，以及最佳的效能。

不過，匯入模型並無法解決與大量資料相關，或是報告近即時資料相關的挑戰。 在上述案例中，您可以考慮使用 DirectQuery 模型，前提是您的資料必須儲存在 [DirectQuery 模式所支援的](../connect-data/power-bi-data-sources.md)單一資料來源中。

此外，您可以在下列情況下考慮開發複合模型。

- 您的模型可能是 DirectQuery 模型，但您想要提升效能。 在複合模型中，可以透過針對每個資料表設定適當的儲存體來改善效能。 您也可以新增[彙總](../transform-model/desktop-aggregations.md)。 此文章稍後會討論上述這兩個最佳化方式。
- 您想要將 DirectQuery 模型與其他資料結合，那些資料必須匯入模型中。 匯入的資料可能是從不同的資料來源，或是從計算資料表載入。
- 您想要將兩個或更多的 DirectQuery 資料來源結合成單一模型。

> [!NOTE]
> 複合模型無法結合即時連線來源或 DirectQuery 分析資料庫來源。 即時連線來源會包含[外部裝載的模型](../connect-data/service-datasets-understand.md#external-hosted-models)，以及 Power BI 資料集。 DirectQuery 分析資料庫來源包含 SAP Business Warehouse，以及 SAP HANA。

## <a name="optimize-model-design"></a>最佳化模型設計

複合模型可以透過設定資料表[儲存模式](../transform-model/desktop-storage-mode.md)，以及新增[彙總](../transform-model/desktop-aggregations.md)來最佳化。

### <a name="table-storage-mode"></a>資料表儲存體模式

在複合模示中，您可以設定每個資料表 (計算資料表除外) 的儲存模式：

- **DirectQuery**：建議您針對代表大量資料，或是需要傳遞近即時結果的資料表設定此模式。 資料永遠不會匯入這些資料表中。 通常，這些資料表將會是事實類型的資料表，也就是用於摘要的資料表。
- **匯入**：建議您針對維度類型的資料表 (也就是用於篩選及分組的資料表) 設定此模式。 事實上，這是以 DirectQuery 模式不支援的來源為基礎之資料表的唯一選項。 計算資料表一律是匯入資料表。
- **雙重**：建議您在維度類型資料表有機會與來自相同來源的 DirectQuery 事實類型資料表一起查詢時，針對維度類型資料表設定此模式。

Power BI 查詢複合模型時，會有數個可能的案例：

- **僅查詢匯入或雙重資料表**：所有資料都是從模型快取擷取。 這將能提供最快的效能。 此案例常見於由篩選或交叉分析篩選器視覺效果所查詢的維度類型資料表。
- **查詢來自相同來源的雙重資料表或 DirectQuery 資料表**：所有資料都是透過將一或多個原生查詢傳送至 DirectQuery 來源來擷取。 這將能提供最快的效能，特別是在來源資料表上存在適當的索引時。 此案例常見於會對雙重維度類型資料表和 DirectQuery 事實類型資料表進行關聯的查詢。 這些查詢為「來源群組內部」，因此所有一對一或一對多關聯性都會評估為[一般關聯性](../transform-model/desktop-relationships-understand.md#regular-relationships)。
- **所有其他查詢**：這些查詢涉及跨來源群組關聯性。 這可能是因為匯入資料表與 DirectQuery 資料表相關聯，或是因為雙重資料表與來自不同來源的 DirectQuery 資料表相關聯 (在此情況下其會表現出匯入資料表的行為)。 所有關聯性都會評估為[受限關聯性](../transform-model/desktop-relationships-understand.md#limited-relationships)。 這也代表套用到非 DirectQuery 資料表的群組必須以虛擬資料表的形式傳送到 DirectQuery 來源。 在此情況下，原生查詢可能會沒有效率，特別是針對大型群組集合。 此外，這也可能會在原生查詢中公開敏感性資料。

總而言之，我們建議您︰

- 仔細考慮複合模型是否為正確的解決方案；其雖然允許針對不同資料來源進行模型層級整合，但也會引進設計複雜度及其可能會帶來的後果
- 在資料表為儲存大量資料的事實資料表，或是需要傳遞近即時結果的情況下，請將儲存模式設定為 [DirectQuery] 
- 在資料表為維度類型資料表，且會搭配以相同來源為基礎的 **DirectQuery** 事實類型資料表一起查詢的情況下，請將儲存模式設定為 [雙重] 
- 設定適當的重新整理頻率，來將雙重資料表 (以及任何相依的計算資料表) 的模型快取與來源資料庫保持同步
- 致力於確保資料來源 (包括模型快取) 之間的資料完整性；受限關聯性將會在相關的資料行值不相符時排除資料列
- 搭配適當的索引將 DirectQuery 資料來源最佳化，以取得有效率的聯結、篩選及分組
- 如果原生查詢具有被攔截的風險，請不要將敏感性資料載入匯入或雙重資料表。如需詳細資訊，請參閱[在 Power BI Desktop 中使用複合模型 (安全性影響)](../transform-model/desktop-composite-models.md#security-implications)

### <a name="aggregations"></a>彙總

您可以將彙總新增到複合模型中的 DirectQuery 資料表。 彙總會快取在模型中，因此其行為會與匯入資料表相同 (雖然無法將其作為模型資料表使用)。 其目的是為了改善「更高細微度」查詢的效能。 如需詳細資訊，請參閱 [Power BI Desktop 中的彙總](../transform-model/desktop-aggregations.md)。

我們建議彙總資料表遵循這個基本規則：其資料列應該要至少比基礎資料表少 10 倍。 例如，如果基礎資料表儲存 10 億個資料列，則彙總資料表便不應該超過 1 億個資料列。 這個規則可確保在取得足夠的效能提升，以及在建立及維護彙總資料表的成本之間取得適當的平衡。

## <a name="next-steps"></a>後續步驟

如需本文的詳細資訊，請參閱下列資源：

- [在 Power BI Desktop 中使用複合模型](../transform-model/desktop-composite-models.md)
- [Power BI Desktop 中的模型關聯性](../transform-model/desktop-relationships-understand.md)
- [Power BI Desktop 中的 DirectQuery 模型](../connect-data/desktop-directquery-about.md)
- [在 Power BI Desktop 中使用 DirectQuery](../connect-data/desktop-use-directquery.md)
- [在 Power BI Desktop 中針對 DirectQuery 模型進行疑難排解](../connect-data/desktop-directquery-troubleshoot.md)
- [Power BI 資料來源](../connect-data/power-bi-data-sources.md)
- [Power BI Desktop 中的儲存模式](../transform-model/desktop-storage-mode.md)
- [Power BI Desktop 中的彙總](../transform-model/desktop-aggregations.md)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com)
