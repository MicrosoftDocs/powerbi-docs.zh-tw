---
title: 搭配匯入、即時連接和直接查詢使用自然語言
description: 在本文中，我們將探討問與答功能如何與 Power BI 中可用的不同資料來源類型搭配運作。 我們也將探討索引和快取的概念。
author: mohaali
ms.author: mohaali
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 08/19/2020
ms.openlocfilehash: 23ecc8edd82f6c1694c850f73fef2a892230ff14
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418961"
---
# <a name="use-natural-language-with-import-live-connect-and-direct-query"></a>搭配匯入、即時連接和直接查詢使用自然語言

Power BI 中的問與答功能，可讓您使用自然語言詢問資料的相關問題，快速從資料取得解答。 本文說明如何使用索引和快取，改善每個支援設定的效能。

## <a name="what-data-sources-are-supported-in-qa"></a>問與答支援哪些資料來源？

下列設定支援問與答：

- 匯入模式
- 即時連接模式 - 使用內部部署 SQL Server Analysis Services、Azure Analysis Services 或 Power BI 資料集
- 直接查詢 - Azure Synapse、Azure SQL 和 SQL Server 2019。 雖然其他來源可以在直接查詢模式中運作，但我們並未正式支援這些來源。

根據預設，如果您使用問與答視覺效果，則會在報表內啟用問與答。 如果您使用直接查詢或即時連接，則會出現提示。 您可以前往選項，明確地開啟/關閉報表的自然語言功能。

![問與答桌面選項](media/qna-desktop-options.png)

如需詳細資訊，請參閱 [Power BI 問與答的限制](q-and-a-limitations.md)。

## <a name="how-does-indexing-work-with-qa"></a>索引如何與問與答搭配運作？

當您啟用問與答時，會建立索引，快速提供即時意見反應給使用者，並協助解譯使用者的問題。 索引可能需要一些時間才能建立，而且會有下列要素和限制。

- 除非已明確從問與答工具關閉，否則所有資料行名稱和資料表都會插入索引。
- 少於 100 個字元的所有文字值都會編製索引。 大於 100 個字元的文字值將不會編製索引。 
- 問與答最多會在其索引中儲存 5 百萬個唯一值。 如果您超過此閾值，索引將不會保留所有可能的值，因此可能會降低您從問與答所收到結果的正確性。
- 如果在編製索引期間發生錯誤，索引會維持在部分狀態，並將在下次重新整理時重建，如下一節所述。

## <a name="how-often-is-the-index-refreshed-and-cached"></a>索引重新整理和快取的頻率為何？

在 Power BI Desktop 中，當您使用問與答時，就會建立索引。 隨即會出現一個小圖示，讓您知道正在建立索引。 在這段期間，問與答視覺效果 (包括建議) 可能需要一些時間才能載入。

在 Power BI 服務中，會在發佈/重新發佈和重新整理時重建索引。 問與答索引不一定會自動建立，有時會視需要建立，以利將資料集重新整理最佳化。 若是直接查詢，我們最多會每天為資料編製索引一次，以降低對直接查詢來源的影響。

## <a name="next-steps"></a>後續步驟

您可以透過各種方式將自然語言整合至報表中。 如需詳細資訊，請參閱下列文章：

* [問與答視覺效果](../visuals/power-bi-visualization-q-and-a.md)
* [問與答最佳做法](q-and-a-best-practices.md)
