---
title: 取得更佳的內嵌式 BI 見解：Power BI 內嵌式分析效能最佳做法
description: 本文提供 Power BI 內嵌式分析最佳做法的指引。 使用 Power BI 內嵌式分析，取得更佳的內嵌式 BI 見解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 12/12/2018
ms.openlocfilehash: f8bf41ae9a4b6f2e16aae2c05df8fa4448a0457c
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888780"
---
# <a name="power-bi-embedded-analytics-performance-best-practices"></a>Power BI 內嵌式分析效能最佳做法

本文提供能更快速轉譯應用程式中的報表、儀表板及磚的建議。

> [!Note]
> 請記住，載入時間主要取決於與報表相關聯的元素和資料本身，包括視覺效果、資料大小，以及查詢及量值的複雜度。 如需詳細資訊，請參閱 [Power BI 最佳化指南](../../guidance/power-bi-optimization.md)。

## <a name="update-tools-and-sdk-packages"></a>更新工具和 SDK 套件

保持工具和 SDK 套件的最新狀態。

* 請一律使用最新版本的 [Power BI Desktop](https://powerbi.microsoft.com/desktop/)。

* 安裝最新版本的 [Power BI 用戶端 SDK](https://github.com/Microsoft/PowerBI-JavaScript)。 我們會持續發行其他增強功能，因此請務必隨時掌握最新狀態。

## <a name="embed-parameters"></a>內嵌參數

`powerbi.embed(element, config)` 方法會接受一個元素及一個設定。config 參數包括可能影響效能的欄位。

### <a name="embed-url"></a>內嵌 URL

請避免自行產生內嵌 URL。 反之，請務必透過呼叫[取得報表](/rest/api/power-bi/reports/getreportsingroup)、[取得儀表板](/rest/api/power-bi/dashboards/getdashboardsingroup)，或[取得磚](/rest/api/power-bi/dashboards/gettilesingroup) API 來取得內嵌 URL。 我們已將名為 **_config_** 的新參數新增至 URL，用來提升效能。

### <a name="permissions"></a>權限

如果您不想在編輯模式中內嵌報表，請提供 [檢視] 權限。 如此一來，內嵌程式碼就不會初始化用於編輯模式的元件。

### <a name="filters-bookmarks-and-slicers"></a>篩選條件、書籤和交叉分析篩選器

通常，報表視覺效果會與快取資料一起儲存。 快取資料可用來提供有感效能。 報表會在執行查詢時轉譯快取的資料。 若提供篩選條件、書籤或交叉分析篩選器，則快取資料便不相關，且視覺效果只會在視覺效果查詢結束後轉譯。

若您使用相同的篩選條件、書籤和交叉分析篩選器內嵌報表，來改善您的效能，請儲存已套用篩選條件、書籤和交叉分析篩選器的報表。 這會轉譯包含快取資料的報表，其中包含篩選條件、書籤和交叉分析篩選器。

## <a name="switching-between-reports"></a>在報表之間切換

將多個報表內嵌至相同的 iframe 時，請不要為每個報表產生新的 iframe。 請改為搭配不同的設定使用 `powerbi.embed(element, config)` 來內嵌新報表。

> [!NOTE]
> 為客戶進行內嵌 (也稱為「應用程式擁有資料」案例) 時，於報表之間切換需要使用具備所有報表和資料集權限的內嵌權仗。 如需詳細資訊，請參閱[產生權杖 API](/rest/api/power-bi/embedtoken/generatetoken) \(英文\)。

## <a name="query-caching"></a>查詢快取

具備 Power BI Premium 容量或 Power BI Embedded 容量的組織，可以利用查詢快取，加速與資料集建立關聯的報表。

[深入了解 Power BI 中的查詢快取](../../connect-data/power-bi-query-caching.md)。

## <a name="preload"></a>預先載入

使用 `powerbi.preload()` 來改善終端使用者效能。 `powerbi.preload()` 方法會下載 JavaScript、css 檔案和其他成品，其稍後會用來內嵌報表。

如果不想立即內嵌報表，請呼叫 `powerbi.preload()`。 例如，如果內嵌的 Power BI 內容未顯示在首頁，請使用 `powerbi.preload()` 下載並快取用於內嵌內容的成品。

## <a name="bootstrapping-the-iframe"></a>啟動載入 iframe

> [!NOTE]
> [Power BI 用戶端 SDK](https://github.com/Microsoft/PowerBI-JavaScript) 2.9 版是啟動 iframe 的必要項目。

`powerbi.bootstrap(element, config)` 可讓您在所有必要參數可用前開始內嵌。 啟動程序 API 會準備及初始化 iframe。
使用啟動程序 API 時，仍需在相同的 HTML 元素上呼叫 `powerbi.embed(element, config)`。

舉例來說，此功能的其中一個使用案例，就是同時執行 iframe 啟動程序和後端呼叫來進行內嵌。
> [!TIP]
> 請於可用時使用開機程序 API，以先產生 iframe 再向終端使用者顯示。

[深入了解 iframe 啟動程序](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Bootstrap-For-Better-Performance)。

## <a name="measure-performance"></a>測量效能

### <a name="performance-events"></a>效能事件

若要測量內嵌效能，您可以使用兩個事件：

1. 載入事件：直到報表初始化完成前的時間 (Power BI 標誌會在載入完成時消失)。
2. 轉譯事件：直到報表使用實際資料完全轉譯前的時間。 轉譯事件會在每次報表重新轉譯時發出 (例如在套用篩選條件後)。 若要測量報表，請務必在第一個引發的事件中執行計算。

快取資料會在可用且並未產生其他事件時轉譯。

[深入了解事件處理](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Handling-Events)。

### <a name="performance-analyzer"></a>效能分析器

若要檢查報表元素的效能，您可以使用 Power BI Desktop 中的效能分析器。
效能分析器可讓您查看和記錄記錄檔，測量您每個報表元素的執行效能。

[深入了解效能分析器](../../create-reports/desktop-performance-analyzer.md)。

> [!NOTE]
> 請務必記得將內嵌報表效能與 powerbi.com 上的效能進行比較。 這有助您了解效能問題的來源

## <a name="next-steps"></a>後續步驟

* [Power BI 最佳化指南](../../guidance/power-bi-optimization.md)
* [如何針對 Power BI 內嵌式分析的問題進行疑難排解](embedded-troubleshoot.md)
* [Power BI 內嵌式分析常見問題集](embedded-faq.md)