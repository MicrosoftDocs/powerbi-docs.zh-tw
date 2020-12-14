---
title: 使用 Power BI Desktop 中的增強型資料集中繼資料
description: 本文描述如何使用 Power BI 中的增強型資料集中繼資料。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: conceptual
ms.date: 12/08/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 661e50617094d396e8beb887ac0e4a27c28c2ca7
ms.sourcegitcommit: 30d0668434283c633bda9ae03bc2aca75401ab94
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2020
ms.locfileid: "96906952"
---
# <a name="using-enhanced-dataset-metadata"></a>使用增強型資料集中繼資料

當 Power BI Desktop 建立報表時，也會在對應的 PBIX 和 PBIT 檔案中建立資料集中繼資料。 之前中繼資料是儲存在 Power BI Desktop 特定的格式中。 中繼資料使用了 Base-64 編碼 M 運算式及資料來源。 Power BI 假設了儲存該中繼資料的方式。

隨著 **增強型資料集中繼資料** 功能的發行，我們克服了許多其中的限制。 開啟檔案時，PBIX 檔案會自動升級為增強型中繼資料。 使用 **增強型資料集中繼資料**，由 Power BI Desktop 建立的中繼資料，即會使用類似於 Analysis Services 表格式模型使用的格式，以 [表格式物件模型](/analysis-services/tom/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo)做為基礎。


**增強型資料集中繼資料** 功能是一種策略性及基礎功能。 未來的 Power BI 功能都會以其中繼資料為基礎建置。 其他可能獲益於增強型資料集中繼資料的功能還包括：

- 用於管理 Power BI 資料集的 [XMLA 讀取/寫入](/power-platform-release-plan/2019wave2/business-intelligence/xmla-readwrite)
- 將 Analysis Services 工作負載移轉到 Power BI，以獲益於新一代的功能。

## <a name="limitations"></a>限制
在增強型中繼資料支援之前，針對 SQL Server、Oracle、Teradata 和舊版 HANA 連線，Power BI Desktop 會將原生查詢新增至資料模型。 Power BI 服務資料模型會使用此查詢。 有了增強型中繼資料支援，Power BI 服務資料模型會在執行階段重新產生原生查詢。 而不會使用 Power BI Desktop 所建立的查詢。 在大部分的情況下，此擷取會正確自行解決，但某些轉換必須讀取基礎資料才能運作。 您可能會在報表中看到先前已處理過的一些錯誤。 例如，錯誤會指出： 

「無法將資料表 'Dimension City' 中的 M 查詢轉換成原生來源查詢。 請稍後再試一次，或連絡客戶支援。 如果需要連絡支援人員，請提供這些詳細資料。」 

您可在 Power BI Desktop 中的三個不同位置修正查詢：

- 當套用變更或進行重新整理時。
- 在通知您運算式無法摺疊至資料來源的 Power Query 編輯器警告列中。
    :::image type="content" source="media/desktop-enhanced-dataset-metadata/enhanced-metadata-apply-query-changes.png" alt-text="[套用查詢變更] 訊息的螢幕擷取畫面：無法將運算式摺疊至資料來源。":::
- 當在開啟報表後執行評估，以檢查是否有不支援的查詢時。 執行這些評估可能會影響效能。


## <a name="next-steps"></a>後續步驟

您可以使用 Power BI Desktop 執行各種作業。 如需有關其功能的詳細資訊，請參閱下列資源：

* [Power BI Desktop 是什麼？](../fundamentals/desktop-what-is-desktop.md)
* [Power BI Desktop 的新功能](../fundamentals/desktop-latest-update.md)
* [Power BI Desktop 的查詢概觀](../transform-model/desktop-query-overview.md)
* [Power BI Desktop 中的資料類型](desktop-data-types.md)
* [使用 Power BI Desktop 合併資料並使其成形](desktop-shape-and-combine-data.md)
* [Power BI Desktop 中的常見查詢工作](../transform-model/desktop-common-query-tasks.md)
