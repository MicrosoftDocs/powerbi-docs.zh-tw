---
title: 使用 Power BI Desktop 中的增強型資料集中繼資料
description: 本文描述如何使用 Power BI 中的增強型資料集中繼資料。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: conceptual
ms.date: 09/22/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 2c5e465026f1ba7564bda18ad3b005b024a663a7
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96404977"
---
# <a name="using-enhanced-dataset-metadata"></a>使用增強型資料集中繼資料

當 Power BI Desktop 建立報表時，也會在對應的 PBIX 和 PBIT 檔案中建立資料集中繼資料。 之前中繼資料是儲存在 Power BI Desktop 特定的格式中。 其先前使用了 Base 64 編碼 M 運算式及資料來源，並假設了儲存中繼資料的方式。

隨著 **增強型資料集中繼資料** 功能的發行，我們克服了許多其中的限制。 開啟檔案時，PBIX 檔案會自動升級為增強型中繼資料。 使用 **增強型資料集中繼資料**，由 Power BI Desktop 建立的中繼資料，即會使用類似於 Analysis Services 表格式模型使用的格式，以 [表格式物件模型](/analysis-services/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo)做為基礎。


**增強型資料集中繼資料** 功能是一種策略性及基礎功能，因為未來的 Power BI 功能都會以這項中繼資料為基礎建置。 其中一部分可獲益於增強型資料集中繼資料的額外功能，包括 Power BI 資料集管理的 [XMLA 讀取/寫入](/power-platform-release-plan/2019wave2/business-intelligence/xmla-readwrite)，以及將 Analysis Services 工作負載移轉至 Power BI，使其獲益於下一代的功能。


## <a name="next-steps"></a>後續步驟

您可以使用 Power BI Desktop 執行各種作業。 如需有關其功能的詳細資訊，請參閱下列資源：

* [Power BI Desktop 是什麼？](../fundamentals/desktop-what-is-desktop.md)
* [Power BI Desktop 的新功能](../fundamentals/desktop-latest-update.md)
* [Power BI Desktop 的查詢概觀](../transform-model/desktop-query-overview.md)
* [Power BI Desktop 中的資料類型](desktop-data-types.md)
* [使用 Power BI Desktop 合併資料並使其成形](desktop-shape-and-combine-data.md)
* [Power BI Desktop 中的常見查詢工作](../transform-model/desktop-common-query-tasks.md)