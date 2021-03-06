---
title: 資料流程最佳做法
description: 資料流程最佳做法連結與指導方針的集合
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-dataflows
ms.topic: how-to
ms.date: 12/10/2020
LocalizationGroup: Data from files
ms.openlocfilehash: fb688b20fd8b5ee1288f670fba9f7f45fc058680
ms.sourcegitcommit: 1cad78595cca1175b82c04458803764ac36e5e37
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2021
ms.locfileid: "98565356"
---
# <a name="dataflows-best-practices"></a>資料流程最佳做法

Power BI **資料流程** 是企業導向的資料準備解決方案，可讓資料生態系統準備好用於取用、重複使用及整合。 此文章提供最佳做法清單，其中包含文章與其他資訊的連結，可協助您了解並發揮資料流程的全部功能。

## <a name="dataflows-across-the-power-platform"></a>Power Platform 中的資料流程

資料流程可用於各種 Power Platform 技術，例如 Power Query、Microsoft Dynamics 365 與其他 Microsoft 供應項目。 如需有關資料流程如何在 Power Platform 中運作的更多資訊，請參閱[在 Microsoft 產品之間使用資料流程](/power-query/dataflows/overview-dataflows-across-power-platform-dynamics-365) (機器翻譯)。


## <a name="dataflows-best-practices-table-and-links"></a>資料流程最佳做法表格與連結

下表提供一系列文章連結，這些文章描述建立或使用資料流程時的最佳做法。 這些連結包括開發商務邏輯、開發複雜資料流程、重複使用資料流程，以及如何利用您的資料流程達成企業規模的相關資訊。


|**主題**  |**指導方針區域**  |**文章或內容的連結**  |
|---------|---------|---------|
|Power Query     | 充分利用您資料整頓體驗的祕訣與訣竅        |[Power Query 最佳做法](/power-query/best-practices) \(部分機器翻譯\)        |
|利用計算實體     |在資料流程中使用計算實體有效能方面的好處         |[計算實體案例](/power-query/dataflows/computed-entities-scenarios) (機器翻譯)         |
|開發複雜的資料流程     |用於開發大規模、高效能資料流程的模式         |[複雜資料流程](/power-query/dataflows/best-practices-developing-complex-dataflows) \(部分機器翻譯\)         |
|重複使用資料流程     |模式、指導方針與使用案例         |[重複使用資料流程](/power-query/dataflows/best-practices-reusing-dataflows)         |
|大規模實作     |適用於企業架構的大規模使用級別指導方針         |[使用資料流程的資料倉儲](/power-query/dataflows/best-practices-for-data-warehouse-using-dataflows) \(部分機器翻譯\)         |
|利用增強型計算     |可能可提升資料流程效能高達 25 倍         |[增強型計算引擎](dataflows-premium-workload-configuration.md#using-the-compute-engine-to-improve-performance)         |
|最佳化您的工作負載設定     |了解您可以扳動以將效能最大化的拉桿，以充分運用您的資料流程基礎結構         |[資料流程工作負載設定](dataflows-premium-workload-configuration.md)         |
|聯結及展開資料表     |建立高效能聯結         |[最佳化展開資料表作業](/power-query/optimize-expanding-table-columns) \(部分機器翻譯\)         |
|查詢摺疊基本概念     |使用來源系統來加快轉換速度         |[查詢摺疊](/power-query/power-query-folding) \(部分機器翻譯\)         |
|使用資料分析     |了解資料行品質、分配及分析設定檔         |[資料分析工具](/power-query/data-profiling-tools)         |
|實作錯誤處理     |開發健全的資料流程復原性來重新整理錯誤並提供建議         |[常見錯誤的模式](/power-query/dealing-with-errors) \(部分機器翻譯\)  </br> [複雜錯誤處理](/power-query/error-handling) \(部分機器翻譯\)      |
|使用結構描述檢視      |改善使用寬型資料表及執行結構描述層級作業時的撰寫體驗         |[結構描述檢視](/power-query/schema-view) \(部分機器翻譯\)         |
|連結實體      |重複使用與參考轉換         |[連結實體](/power-query/dataflows/linked-entities)         |
|累加式重新整理      |載入最新或已變更的資料與完整重新載入         |[累加式重新整理](/power-query/dataflows/incremental-refresh)         |
|||


        
## <a name="next-steps"></a>後續步驟

下列文章提供資料流程和 Power BI 的詳細資訊：

* [資料流程和自助資料準備簡介](dataflows-introduction-self-service.md)
* [建立資料流程](dataflows-create.md)
* [設定及取用資料流程](dataflows-configure-consume.md)
* [資料流程的進階功能](dataflows-premium-features.md)
* [將資料流程儲存體設定為使用 Azure Data Lake Gen 2](dataflows-azure-data-lake-storage-integration.md)
* [使用資料流程的 AI](dataflows-machine-learning-integration.md)
* [資料流程限制與考量](dataflows-features-limitations.md)