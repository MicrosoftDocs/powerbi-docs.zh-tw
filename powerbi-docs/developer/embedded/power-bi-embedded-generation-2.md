---
title: Power BI Embedded 層代2說明為 Power BI Embedded 分析的一部分
description: 瞭解 Power BI Embedded analytics 中的 Power BI Embedded 層代2供應專案。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: overview
ms.date: 02/03/2021
ms.openlocfilehash: fa72ab380cac1a1ac6d12cb431bdacfb5964ee83
ms.sourcegitcommit: c33e53e1fab1f29872297524a7b4f5af6c806798
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/04/2021
ms.locfileid: "99534485"
---
# <a name="power-bi-embedded-generation-2-preview"></a>Power BI Embedded 層代 2 (預覽) 

Power BI Embedded 最近發行了新版本的 Power BI Embedded， **Power BI Embedded 層代 2**，為方便起見，稱為 **內嵌 Gen2** 。 Embedded Gen2 目前為預覽狀態，可供內嵌訂閱者在預覽期間使用。 您仍然可以建立原始版本的 Power BI Embedded 資源（稱為 *Embedded gen 1*），或建立新的 *embedded gen 2* 資源。 在預覽期間，您可以平行執行這兩種類型的 Power BI Embedded 容量，並將任何工作區指派給 Gen1 或 Gen2 容量」。

所有 Power BI Embedded Gen 1 的功能（例如暫停和繼續容量）都會保留在 Gen 2 中。 此外，Gen 2 容量資源提供下列更新和改善體驗：

* **增強效能** -隨時都能提高任何容量大小的效能。 作業將一律以最快速度執行，且不會在容量上的負載接近容量限制時變慢。

* **更大的擴充** 功能，包括下列增強功能：

    * 重新整理 *平行存取沒有任何限制*-您不再需要追蹤在容量上重新整理資料集的排程

    * *較少的記憶體限制*

    * *將報表互動和排程的重新整理完全分隔開來*

* **適用于編頁報表和 AI 工作負載的較低進入層級** –以 *A1* SKU 為開頭，並依您的需要成長。

* **立即調整資源** 規模，立即調整您的 Power BI Embedded 資源。 在幾分鐘內調整 Gen1 資源的規模，以秒為單位調整 Gen2 資源。

* 在 **不停機的情況下進行調整**-使用內嵌 Gen2 可以調整 Power BI Embedded 資源，而不會發生任何停機狀況。

* **改善的計量** ，包括明確和標準化的容量使用率資料，取決於容量所執行之分析作業的複雜度。 計量不會受到其他因素的影響，例如容量大小，以及執行分析時系統上的負載層級。 使用改良的計量時，內建的報告工具可讓您清楚地看到：
    * 使用率分析
    * 預算規劃
    * 退款
    * 需要升級您的容量

    >[!NOTE]
    >改進的計量之後將在預覽期間開放使用。 在過去七天內尋求使用量計量存取權的客戶，可以藉由聯絡客戶支援來達到此目的。

## <a name="using-embedded-gen2"></a>使用內嵌 Gen2

建立內嵌的 Gen2 容量資源，以充分利用其更新。 若要建立內嵌的 Gen2 容量資源，請遵循 [Azure 入口網站中建立 Power BI Embedded 容量](azure-pbie-create-capacity.md)的指示。

## <a name="known-limitations"></a>已知的限制

* 無法在 [計量應用程式](../../admin/service-admin-premium-monitor-capacity.md)中追蹤內嵌式 Gen2 容量使用率。 如需詳細資訊，請參閱 [Premium Gen2 監視器更新](../../admin/service-premium-what-is.md#updates-for-premium-gen2-preview-2)。

* 特定工作負載的記憶體配置設定不適用於內嵌的 Gen2 容量。 如需詳細資訊，請參閱 [Embedded Gen 2 記憶體增強功能](embedded-capacity.md#embedded-gen-2-memory-enhancements-preview)

* 如果您使用 XMLA 搭配 Embedded Gen2，請確定您使用的是最新版本的資料模型和管理工具。

* 只有最新的用戶端程式庫才支援內嵌 Gen2 中的 Analysis services 功能。 適用于支援這項需求之相依工具的預估發行日期，列在 [Premium Gen2 的已知限制](../../admin/service-premium-what-is.md#known-limitations-in-premium-gen2)中。

* 所有目前適用于 Power BI Embedded 的 Azure 計量和記錄診斷，只支援 Gen1 的容量。

## <a name="next-steps"></a>下一步

> [!div class="nextstepaction"]
> [在 Azure 入口網站中建立 Power BI Embedded 容量](azure-pbie-create-capacity.md)

> [!div class="nextstepaction"]
> [Power BI 內嵌式分析中的容量和 SKU](embedded-capacity.md)

> [!div class="nextstepaction"]
> [什麼是 Power BI Premium？](../../admin/service-premium-what-is.md)

> [!div class="nextstepaction"]
>[對客戶進行內嵌](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[為組織內嵌](embed-sample-for-your-organization.md)