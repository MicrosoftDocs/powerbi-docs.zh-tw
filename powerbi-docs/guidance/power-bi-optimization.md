---
title: Power BI 最佳化指南
description: Power BI 最佳化指南。
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: 3a541c46f78c5e5cd25b47a94394a011fd61954f
ms.sourcegitcommit: 4ac9447d1607dfca2e60948589f36a3d64d31cb4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2020
ms.locfileid: "92916536"
---
# <a name="optimization-guide-for-power-bi"></a>Power BI 最佳化指南

此文章提供的指導方針可讓開發人員與系統管理員建立並維護最佳化的 Power BI 解決方案。 您可以在不同的架構層級最佳化您的解決方案。 這些層級包括：

- 資料來源
- 資料模型
- 視覺效果，包括儀表板、Power BI 報表，以及 Power BI 編頁報表
- 環境，包括容量、資料閘道與網路

## <a name="optimizing-the-data-model"></a>最佳化資料模型

資料模型支援整個視覺效果體驗。 資料模型可能是外部裝載或內部裝載，而在 Power BI 中其稱為「資料集」  。 請務必了解您的選項，並為您的解決方案選擇適當的資料集類型。 資料集模式有三種：匯入、DirectQuery 及複合。 如需詳細資訊，請參閱 [Power BI 服務中的資料集](../connect-data/service-datasets-understand.md)以及 [Power BI 服務中的資料集模式](../connect-data/service-dataset-modes-understand.md)。

如需特定的資料集模式指導方針，請參閱：

- [匯入模型的資料減少技術](import-modeling-data-reduction.md)
- [Power BI Desktop 中的 DirectQuery 模型指南](directquery-model-guidance.md)
- [Power BI Desktop 中的複合模型指導方針](composite-model-guidance.md)

## <a name="optimizing-visualizations"></a>最佳化視覺效果

Power BI 視覺效果可以是儀表板、Power BI 報表，或 Power BI 編頁報表。 每個都有不同的架構，因此每個都有自己的指導方針。 

### <a name="dashboards"></a>儀表板

請務必了解，Power BI 會維護儀表板圖格的快取，但動態報表圖格與串流圖格除外。 如需詳細資訊，請參閱 [Power BI 中的資料重新整理 (圖格重新整理)](../connect-data/refresh-data.md#tile-refresh)。 如果您的資料集強制執行動態[資料列層級安全性 (RLS)](../admin/service-admin-rls.md)，請務必了解效能方面的影響，因為圖格會以每個使用者為基礎進行快取。

當您將動態報表圖格釘選到儀表板時，其內容不是由查詢快取提供。 相反地，其行為就像報表一樣，而且會即時對後端核心進行查詢。

正如其名，從快取中擷取資料所提供的效能，會比依賴資料來源更佳且更一致。 利用這項功能的其中一種方式是讓儀表板成為您使用者的第一個登陸頁面。 將常用和經常要求的視覺效果釘選到儀表板。 如此一來，儀表板會成為重要的「第一線防護」，這可以提供容量負載較低的一致效能。 使用者仍然可以按一下報表，以分析詳細資料。

針對 DirectQuery 與即時連線資料集，系統會透過定期查詢資料來源來更新快取。 根據預設，每小時會更新一次快取，不過您可以在資料集設定中設定不同的頻率。 每個快取更新都會將查詢傳送至底層資料來源，以更新快取。 產生的查詢數目取決於釘選到依賴該資料來源儀表板的視覺效果數。 請注意，如果啟用資料列層級安全性，則會為每個不同的安全性內容產生查詢。 例如，假設對使用者進行分類的角色有兩種，而其對資料有兩種不同檢視。 在查詢快取重新整理期間，Power BI 會產生兩組查詢。

### <a name="power-bi-reports"></a>Power BI 報表

針對最佳化 Power BI 報表設計，有一些建議。

> [!NOTE]
> 當報表是以 DirectQuery 資料集為基礎時，如需額外的報表設計最佳化，請參閱 [Power BI Desktop 中的 DirectQuery 模型指導方針 (最佳化報表設計)](directquery-model-guidance.md#optimize-report-designs)。

#### <a name="apply-the-most-restrictive-filters"></a>套用限制最嚴格的篩選條件

視覺效果所需顯示的資料越多，要載入的視覺效果就越慢。 雖然此原則看起來很明顯，但卻很容易忘記。 例如：假設您有大型資料集。 除了該資料集外，您還使用了資料表來建置報表。 終端使用者會在頁面上使用交叉分析篩選器來取得想要的資料列，且通常只會對數十個資料列感興趣。

一個常見錯誤是在不篩選的情況下保留資料表預設檢視，亦即全部超過 1 億個資料列。 在每次重新整理時，都會將這些資料列的資料載入記憶體，並進行解壓縮。 這種處理會造成龐大的記憶體需求。 解決方式：使用「前 N 筆」篩選條件來減少資料表顯示的最大項目數。 您可以將最大項目設為超過使用者需要的數量，例如 10,000 筆。 結果是不但終端使用者的體驗不會變更，記憶體的用量還會大幅下降。 而最重要的是，效能也會改善。

建議您將如上設計方法用於報表中的每一個視覺效果。 問問自己，需要這個視覺效果中的所有資料嗎？ 是否有任何方式可以進一步篩選視覺效果中顯示的資料量，並將對終端使用者體驗的影響降至最低？ 請記住，資料表特別耗費資源。

#### <a name="limit-visuals-on-report-pages"></a>限制報表頁面上的視覺效果

上述原則同樣適用於新增至報表頁面的視覺效果數目。 強烈建議您限制特定報表頁面上只顯示必要的視覺效果數目。 [鑽研頁面](report-drillthrough.md)與[報表頁面工具提示](report-page-tooltips.md)十分適合提供其他詳細資料，而不會將更多視覺效果塞滿報表。

#### <a name="evaluate-custom-visual-performance"></a>評估自訂視覺效果效能

請務必以其步調放入每個自訂視覺效果，以確保高效能。 最佳化不佳的 Power BI 視覺效果可能會對整個報表效能造成負面影響。

### <a name="power-bi-paginated-reports"></a>Power BI 編頁報表

Power BI 編頁報表設計可以透過將最佳做法設計套用至報表的資料擷取來進行最佳化。 如需詳細資訊，請參閱[編頁報表的資料擷取指導方針](report-paginated-data-retrieval.md)。

此外，請確定您的容量有足夠的記憶體配置給[編頁報表工作負載](../admin/service-admin-premium-workloads.md#paginated-reports)。

## <a name="optimizing-the-environment"></a>將環境最佳化

您可以透過設定容量設定、調整資料閘道大小，以及降低網路延遲，將 Power BI 環境最佳化。

### <a name="capacity-settings"></a>容量設定

使用 Power BI Premium (P SKU) 或 Power BI Embedded (A SKU，A4-A6) 提供的容量時，您可管理容量設定。 如需詳細資訊，請參閱[管理 Premium 容量](../admin/service-premium-capacity-manage.md)。 如需如何最佳化容量的指導方針，請參閱[最佳化 Premium 容量](../admin/service-premium-capacity-optimize.md)。

### <a name="gateway-sizing"></a>閘道大小調整

每當 Power BI 必須存取無法直接透過網際網路存取的資料時，就需要閘道。 您可以在內部部署伺服器或 VM 裝載的基礎結構即服務 (IaaS) 上安裝[內部部署資料閘道](../connect-data/service-gateway-onprem.md)。

若要了解閘道工作負載與大小調整建議，請參閱[內部部署的資料閘道大小調整](gateway-onprem-sizing.md)。

### <a name="network-latency"></a>網路延遲

網路延遲可能會因要求到達 Power BI 服務所需時間增加以及傳遞回應所需時間增加而影響報表效能。 Power BI 中的租用戶會指派給特定區域。

> [!TIP]
> 若要判斷租用戶的所在位置，請參閱[我的 Power BI 租用戶位於何處？](../admin/service-admin-where-is-my-tenant-located.md)

租用戶中的使用者存取 Power BI 服務時，他們的要求一律會路由至此區域。 例如，當要求到達 Power BI 服務之後，服務可能會將其他要求傳送至底層資料來源或資料閘道，而這些要求也受限於網路延遲。

[Azure Speed Test](https://azurespeedtest.azurewebsites.net/) 這類工具可以指出用戶端與 Azure 區域之間的網路延遲。 一般而言，若要將網路延遲的影響降到最低，請盡量將資料來源、閘道和 Power BI 叢集保留在最接近的位置。 要求最好位於相同區域內。 如果網路延遲是問題，則您可以透過將其放置在雲端裝載的虛擬機器中，嘗試將閘道與資料來源放置在更接近 Power BI 叢集的位置。

## <a name="monitoring-performance"></a>監視效能

您可以監視效能以找出瓶頸。 為了達到持續最佳化，建議您將焦點放在緩慢的查詢或報表視覺效果上。 監視可以在 Power BI Desktop 中的設計階段，或 Power BI Premium 容量中的生產工作負載上完成。 如需詳細資訊，請參閱[在 Power BI 中監視報表效能](monitor-report-performance.md)。

## <a name="next-steps"></a>後續步驟

如需本文的詳細資訊，請參閱下列資源︰

- [Power BI 指導方針](index.yml)
- [監視報表效能](monitor-report-performance.md)
- 白皮書：[規劃 Power BI 企業部署](https://go.microsoft.com/fwlink/?linkid=2057861)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com/)




