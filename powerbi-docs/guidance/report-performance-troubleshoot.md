---
title: 疑難排解 Power BI 報表效能的問題
description: 診斷 Power BI 報表效能變慢的疑難排解指南。
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: troubleshooting
ms.date: 04/15/2020
ms.openlocfilehash: 9e9d3fa59defa1c33ba39ed7491ce099f350a0bf
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088204"
---
# <a name="troubleshoot-report-performance-in-power-bi"></a>疑難排解 Power BI 報表效能的問題

本文提供的指導方針，可協助開發人員與系統管理員疑難排解報表效能變慢的問題。 此指導方針適用於 Power BI 報表，也適用於 Power BI 編頁的報表。

報表使用者會將在與交叉分析篩選器或其他功能互動時，報表載入速度慢或更新速度慢等報表體驗，歸類成報表效能變慢。 當報表裝載在 Premium 容量中時，您也可以透過監視 [Power BI Premium 計量應用程式](../admin/service-admin-premium-monitor-capacity.md)，找出速度慢的報表。 此應用程式可協助您監視 Power BI Premium 訂閱的健康情況與容量。

## <a name="follow-flowchart-steps"></a>遵循流程圖的步驟

使用下列流程圖，有助於您了解效能變慢的原因，以及判斷所應採取的動作。

:::image type="content" source="media/report-performance-troubleshoot/flowchart.png" alt-text="顯示流程圖的影像。本文將詳細說明此流程圖。" border="true":::

此流程圖有六個結束點，每一個結束點皆會說明所應採取的動作：

|結束字元|動作|
|---------|---------|
|![流程圖結束點 1。](media/common/icon-01-red-30x30.png)|管理容量<br />縮放容量 |
|![流程圖結束點 2。](media/common/icon-02-red-30x30.png)|調查一般報表使用期間的容量活動|
|![流程圖結束點 3。](media/common/icon-03-red-30x30.png)|架構變更<br />考慮使用 Azure Analysis Services<br />檢查內部部署閘道|
|![流程圖結束點 4。](media/common/icon-04-red-30x30.png)|考慮使用 Azure Analysis Services<br />考慮 Power BI Premium|
|![流程圖結束點 5。](media/common/icon-05-red-30x30.png)|使用 Power BI Desktop 效能分析器<br />最佳化報表、模型或 DAX|
|![流程圖結束點 6。](media/common/icon-06-red-30x30.png)|開立支援票證|

## <a name="take-action"></a>採取動作

第一項考量是先了解速度慢的報表是否裝載於 Premium 容量中。

### <a name="premium-capacity"></a>進階容量

當確認報表裝載於 Premium 容量之後，請使用 **Power BI Premium 計量應用程式**，判斷裝載報表的容量，是否經常出現超過容量資源的狀況。 若經常超過 80%，便是 CPU 的問題。 對於記憶體，當[使用中的記憶體計量](../admin/service-premium-metrics-app.md#the-active-memory-metric)超過 50% ，就會發生此狀況。 當資源出現壓力時，可能表示需要[管理或調整容量](../admin/service-admin-premium-manage.md) (流程圖結束點 1)。 若資源足夠，請調查一般報表使用期間的容量活動 (流程圖結束點 2)。

### <a name="shared-capacity"></a>共用容量

當報表裝載於共用容量中時，您無法監視容量的健康情況。 您必須採取不同的調查方法。

首先，判斷效能變慢的時間點是在一天中的特定時間，或在一個月中的特定日。 若是如此，而且許多使用者會同時在這些時間點開啟報表，請考慮下列兩個選項：

- 將資料集移轉至 [Azure Analysis Services](/azure/analysis-services/analysis-services-overview) 或 Premium 容量，以增加查詢輸送量 (流程圖結束點 4)。
- 使用 Power BI Desktop 的[效能分析器](../create-reports/desktop-performance-analyzer.md)，了解每項報表元素 (例如視覺效果與 DAX 公式) 的狀況。 此結果特別適合用於判斷導致效能問題來自查詢或視覺呈現 (流程圖結束點 5)。

若判斷結果是沒有時間模式，請考慮效能變慢是否能歸因於特定地理位置或區域。 若是，可能是資料來源位於遠端，以及網路通訊的速度慢。 在此狀況下，請考慮：

- 使用 [Azure Analysis Services](/azure/analysis-services/analysis-services-overview) 變更架構 (流程圖結束點 3)。
- 最佳化[內部部署資料閘道效能](/data-integration/gateway/service-gateway-performance) (流程圖結束點 3)。

最後，若判斷結果是沒有時間模式，「也不是」  所有區域中都出現效能變慢的狀況，請調查效能變慢的問題，是否出現在特定裝置、用戶端或網頁瀏覽器。 若以上皆非，請使用 Power BI Desktop 的[效能分析器](../create-reports/desktop-performance-analyzer.md) (如前文所述)，最佳化報表或模型 (流程圖結束點 5)。

若您確定是特定裝置、用戶端或網頁瀏覽器導致效能變慢時，建議您前往 [Power BI 支援頁面](https://powerbi.microsoft.com/support/) (流程圖結束點 6) 開立支援票證。

## <a name="next-steps"></a>後續步驟

如需本文的詳細資訊，請參閱下列資源︰

- [Power BI 指導方針](index.yml)
- [監視報表效能](monitor-report-performance.md)
- [效能分析器](../create-reports/desktop-performance-analyzer.md)
- 白皮書：[規劃 Power BI 企業部署](https://go.microsoft.com/fwlink/?linkid=2057861)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com/)
