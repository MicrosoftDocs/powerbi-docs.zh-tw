---
title: Microsoft BI 轉換
description: 了解 Microsoft 如何成功推動商務決策的資料文化特性。 其描述其 BI 策略和願景。
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/19/2020
ms.openlocfilehash: f64fa087665aec7515737d6c4d70328c0c74b13a
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088618"
---
# <a name="microsofts-bi-transformation"></a>Microsoft BI 轉換

本文的對象是 IT 專業人員和 IT 管理員。 您將了解 BI 策略和願景，其讓我們持續利用自有資料作為資產。 您也將了解如何使用 Power BI 來成功推動商務決策的資料文化特性。

首先是一些背景資訊：今天，資料激增以危險的高速影響者消費者和企業。 要在這個資料密集的環境中成功，需要分析師和主管人員可將大量資料提取成簡潔的見解。 Microsoft BI 工具其演化改變了 Microsoft 本身探索資料的方式，並得到在公司中推動影響所需的正確見解。

如此，組織也可如何改變其使用資料的方式呢？ 讓我們透過分享 BI 轉換旅程的案例來協助了解。

## <a name="microsoft-journey"></a>Microsoft 旅程

在幾年前的 Microsoft，我們的組織文化特性鼓勵個人尋求資料和見解其完整擁有權。 也經歷過對於以標準化方式行事的強烈文化抵抗。 因此，組織文化特性導致報告和分析挑戰。 具體而言，其導致：

- 不一致的資料定義、階層、計量和關鍵效能指標 (KPI)。 例如，每個國家/地區都有自己的新營收報告方式。 沒有一致性，但有很多混淆。
- 分析師花費 75% 的時間收集和編譯資料。
- 78% 的報表在「離線環境」中建立。
- 超過 350 種集中式財務工具和系統。
- 每年大約會支出美金 $300 萬元在「影子應用程式」。

這些挑戰提醒我們思考，如何把事情做得更好。 財務和其他內部小組收到主管支援，進行企業評論程序的轉型，這會導致建立整合 BI 平台作為單一事實來源。 (我們將在本文稍後詳細討論 BI 平台。)最後，這些創新讓企業評論從密集的表格式觀點，轉換成著重於重要商務主題的更簡單且深入視覺效果。

我們如何達成這個成功的結果？ 提供由 IT 管理的集中式 BI，並以自助式 BI (SSBI) 加以擴充來獲致成功。 我們以兩種創意的方式來描述：「核心的紀律」，和「邊緣的彈性」。

### <a name="discipline-at-the-core"></a>核心的紀律

核心的紀律表示 IT 藉由策劃單一主要資料來源來保留控制權。 提供標準化的公司 BI，以及定義一致的分類與 KPI 階層，是該紀律的一部分。 重要的是，資料許可權會集中地強制執行，以確保人員只能讀取所需資料。

首先，我們了解 BI 轉換並不是一項技術問題。 為了達到成功，我們學會先定義成功，然後將其轉譯成重要計量。 無法了解對我們來說，在資料之間達成定義一致性有多重要。

我們的轉換並非一夕之間發生。 我們排定子公司計分卡交付的優先順序，包含大約 30 個 KPI。 經過幾年後，我們逐漸擴充了主題領域的數目和深度，並建立更複雜的 KPI 階層。 今天，其可供在客戶層級將較低層級的 KPI 彙總至公司層級的較高層級。 我們的總 KPI 計數現在超過 2000，每個都是成功的重要量值，且與公司目標一致。 現在在整個公司中，公司報表和 SSBI 解決方案會呈現已妥善定義、一致且安全的 KPI。

### <a name="flexibility-at-the-edge"></a>邊緣的彈性

在核心的邊緣，財務、銷售和行銷小組的分析師變得更有彈性且更靈活。 其目前受益於能夠更快速地分析資料。 更正式的說，這種情況被描述為「受控自助式 BI (SSBI)」。 我們現在了解受控 SSBI 對於 IT 和分析師而言是與「互惠互利」有關。 重要的是，我們藉由推動標準化、知識，以及重複使用資料和 BI 解決方案而體驗到了最佳化。 對公司而言，我們增效衍生出更多價值，因為我們在集中式 BI 與受控 SSBI 之間取得適當的平衡。

### <a name="our-solution"></a>解決方案

**Starlight** 是提供給內部資料統一和分析平台的名稱，這個平台可支援財務、銷售、行銷和工程。 其任務是提供健全、共用且可擴充的資料平台。 此平台完全是由財務部門所建立，並使用最新的 Microsoft 產品繼續運作至今。

**KPI Lake** 不是 Azure Data Lake。 而是使用 Microsoft SQL Server Analysis Services 且裝載於 Azure IaaS 中的 Starlight 驅動表格式 BI 語意模型。 BI 語意模型提供來自超過 100 個內部來源的資料，並定義許多階層和 KPI。 其任務是在財務、行銷和銷售之間啟用企業績效報告和分析小組。 它會透過相關來源中統一 BI 語意模型來取得及時、準確且執行良好的見解。

一開始部署時是令人興奮的時刻，因為表格式 BI 語意模型會產生立即且可測量的優點。 第一個版本集中在 C+E 財務和行銷 BI 平台。 過去六年來，它經過擴充，合併其他的商務見解解決方案。 今天，它仍持續演進，並協助全球和商業企業評論，以及標準報告和 SSBI。 其採用在發行之後飆升到 5 倍，遠遠超出我們最初的期望。

以下是主要優點的摘要：

- 協助子公司計分卡、全球企業評論，以及財務、行銷、銷售報表和分析。
- 支援自助式分析，讓分析師能夠探索隱藏在資料中的見解。
- 推動獎勵補償、行銷和作業分析、銷售績效計量、資深領導審查，以及年度規劃程序等的報告和分析。
- 它可從「單一事實來源」提供自動化且動態的報告和分析。

**KPI Lake** 是絕佳的成功案例。 我們經常會向客戶呈現，以展示如何有效使用最新技術的範例。 不意外的是，它與其中許多項都高度共鳴。

#### <a name="how-it-works"></a>運作方式

Starlight 平台會管理從取得到處理，然後一直到發佈的資料程序：

1. 穩固且敏捷的資料整合會以排定方式進行，並從超過 100 個不同的原始來源合併資料。 來源資料系統包含關聯式資料庫、Azure Data Lake Storage 和 Azure Synapse 資料庫。 主題領域包括財務、行銷、銷售和工程。
2. 暫存之後，資料會使用主要資料和商務邏輯來進行遵從與強化。 然後會載入至資料倉儲資料表。 接著會重新整理表格式 BI 語意模型。
3. 整個公司的分析師會使用 Excel 和 Power BI，從表格式 BI 語意模型提供見解和分析。 而且，它可讓企業主捍衛自己企業的計量定義。 必要時，可使用 Azure IaaS 搭配負載平衡來達到調整。

## <a name="deliver-success"></a>實現成功

幽默地來說，每個人都想要一個版本的事實... 前提是他們自己的版本。 但對於某些組織來說，這是他們的現實。 由於個人追求資料與見解的完整所有權，因此有多個版本的事實。 對這些組織而言，這種不受控方法不可能是企業成功的路徑。

這就是為什麼我們相信您需要「卓越中心 (COE)」。 COE 是一個中央小組，其負責定義全公司的計量和定義，還有更多。 它也是一種企業功能，將人員、程序和技術元件組織成一組完整的企業競爭力與能力。

我們會看到許多證據支持，全面且強大的 COE 是提供價值和使企業成功最大化的關鍵。 可包含變更計畫、標準程序、角色、指導方針、最佳做法、支援、訓練和更多項目。

我們邀請您閱讀此 COE 系列中的文章，以深入了解。 讓我們協助探索組織可如何擁抱變更來實現成功。

## <a name="next-steps"></a>後續步驟

如需本文的詳細資訊，請參閱下列資源︰

- [建立卓越中心](center-of-excellence-establish.md)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com/)

在[此系列的下一篇文章](center-of-excellence-establish.md)中，了解 COE 如何在 Microsoft 協助立標準化的分析和資料平台，以從資料顯露見解。

### <a name="professional-services"></a>專業服務

認證 Power BI 合作夥伴可協助組織成功設定 COE。 其可提供符合成本效益的訓練或資料稽核。 若要與 Power BI 合作夥伴交流，請造訪 [Power BI 合作夥伴入口網站](https://powerbi.microsoft.com/partners/)。

您也可以與經驗豐富的諮詢合作夥伴進行互動。 其可協助[評定](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=assessment&country=ALL&region=ALL)、[評估](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=proof-of-concept&country=ALL&region=ALL)或[實作](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=implementation&country=ALL&region=ALL&page=1) Power BI。
