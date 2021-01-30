---
title: Power BI 移轉概觀
description: 了解如何規劃和進行從其他第三方 BI 工具到 Power BI 的移轉。
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: 2089e9f7538fa5a1f4d0e14711dcd877decaa718
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99086824"
---
# <a name="power-bi-migration-overview"></a>Power BI 移轉概觀

有越來越多客戶在 Power BI 上標準化以推動資料文化，這牽涉到實現受控自助商業智慧 (SSBI)、將企業 BI 的傳遞合理化，以及解決經濟壓力。 此系列 Power BI 移轉文章其目的在於指導如何規劃和進行從其他第三方 BI 工具到 Power BI 的移轉。

Power BI 移轉系列中的文章包括：

1. Power BI 移轉概觀 (本文)
1. [準備移轉到 Power BI](powerbi-migration-pre-migration-steps.md)
1. [收集需求以移轉到 Power BI (階段 1)](powerbi-migration-requirements.md)
1. [規劃部署以移轉到 Power BI (階段 2)](powerbi-migration-planning.md)
1. [進行概念證明以移轉到 Power BI (階段 3)](powerbi-migration-proof-of-concept.md)
1. [建立內容以移轉到 Power BI (階段 4)](powerbi-migration-create-validate-content.md)
1. [部署到 Power BI (階段 5)](powerbi-migration-deploy-support-monitor.md)
1. [從客戶 Power BI 移轉中學習](powerbi-migration-learn-from-customers.md)

有兩個假設：組織目前已有舊版 BI 平台，且已決定正式將內容和使用者移轉到 Power BI。 移轉到 Power BI 服務是此系列的主要重點。 國家雲端客戶可能還有其他考量，但不在此系列文章的討論範圍內。

下圖顯示在組織中部署 Power BI 的四個高層級階段。

:::image type="content" source="media/powerbi-migration-overview/migrate-to-powerbi-high-level-overview.png" alt-text="顯示四個高層級階段的影像，下表將進行描述。":::

|階段|描述|
|--------|-----------|
|![第 1 階段：](media/common/icon-01-red-30x30.png)|**設定和評估 Power BI。** 第一個階段牽涉到建立初始 Power BI 架構。 此時會處理初步部署和控管規劃，並進行 Power BI 評估，包括投資報酬率及/或成本效益分析。|
|![階段 2：](media/common/icon-02-red-30x30.png)|**在 Power BI 中快速建立新的解決方案。** 在第二個階段中，自助 BI 作者可開始使用 Power BI，並評估是否符合其需求，以及是否可快速從 Power BI 取得價值。 階段 2 中的活動注重彈性和快速取得商業價值，這對於獲得認可選擇新的 BI 工具 (例如 Power BI) 而言至關重要。 因此，如上圖所示，階段 2 中的活動會與階段 3 中的移轉活動同時進行。|
|![階段 3。](media/common/icon-03-red-30x30.png)|**將 BI 資產從舊版平台移轉到 Power BI。** 第三個階段處理 Power BI 的移轉。 這是此系列 Power BI 移轉文章的重點。 下一節將討論五個特定的移轉階段。|
|![階段 4。](media/common/icon-04-red-30x30.png)|**採用、控管和監視 Power BI。** 最後一個階段是由持續進行的活動所組成，例如培養資料文化、溝通和訓練。 這些活動會大幅影響有效的 Power BI 實作。 您必須擁有適合組織的控管和安全性原則和程序，以及稽核與監視功能，才能進行調整、擴充和持續改善。|

> [!IMPORTANT]
> Power BI 的正式移轉幾乎一律會與開發新 Power BI 解決方案同時進行。 _Power BI 解決方案_ 是包含資料和報表使用的廣義字詞。 一個 Power BI Desktop (pbix) 檔案可能會包含資料模型或報表，或兩者都包含。 建議 (但不一定要) [將資料模型與報表分隔](../guidance/report-separate-from-model.md)，以便重複使用資料。
>
> 當規劃和進行正式移轉時，使用 Power BI 來撰寫新的需求將有助於獲得認可。 同步階段可為內容作者提供實用且真實世界的 Power BI 體驗。

## <a name="five-stages-of-a-power-bi-migration"></a>Power BI 移轉的五個階段

圖表的階段 3 處理 Power BI 移轉。 在這個階段中，有五個一般階段。

:::image type="content" source="media/powerbi-migration-overview/migrate-to-powerbi-five-stages.png" alt-text="顯示 Power BI 移轉階段的影像，其將於以下描述。":::

上圖所示的階段如下：

- [遷移前步驟](#pre-migration-steps)
- [階段 1：收集需求並排列優先順序](#stage-1-gather-requirements-and-prioritize)
- [階段 2：規劃部署](#stage-2-plan-for-deployment)
- [階段 3：進行概念證明](#stage-3-conduct-proof-of-concept)
- [階段 4：建立和驗證內容](#stage-4-create-and-validate-content)
- [階段 5：部署、支援和監視](#stage-5-deploy-support-and-monitor)

### <a name="pre-migration-steps"></a>遷移前步驟

移轉前步驟包括在開始專案以將內容從舊版 BI 平台移轉到 Power BI 之前可考慮的動作。 通常包括初始租用戶層級部署規劃。 如需這些活動的詳細資訊，請參閱[準備移轉到 Power BI](powerbi-migration-pre-migration-steps.md)。

### <a name="stage-1-gather-requirements-and-prioritize"></a>第 1 階段：收集需求並排列優先順序

階段 1 的重點在於收集資訊，並規劃單一解決方案的移轉。 此程序應該會反覆進行，並將範圍設定為合理大小的工作。 階段 1 其輸出包括所要移轉已排列優先順序的報表和資料清查。 需要階段 2 和 3 中的其他活動才能完全預估工作量。 如需階段 1 中活動的詳細資訊，請參閱[收集需求以移轉到 Power BI](powerbi-migration-requirements.md)。

### <a name="stage-2-plan-for-deployment"></a>第 2 階段：規劃部署

階段 2 的重點在於如何為每個特定解決方案，完成在階段 1 中所定義的需求。 階段 2 的輸出包括盡可能多的細節以引導程序，不過這是一個反覆進行的非線性程序。 建立概念證明 (在階段 3 中) 可能會與這個階段同時進行。 即使在建立解決方案時 (在階段 4 中)，也可能會出現影響部署規劃決策的其他資訊。 階段 2 中的這種部署規劃類型專注於解決方案層級，同時採用已在組織層級制定的決策。 如需階段 2 中活動的詳細資訊，請參閱[規劃部署以移轉到 Power BI](powerbi-migration-planning.md)。

### <a name="stage-3-conduct-proof-of-concept"></a>第 3 階段：進行概念證明

階段 3 的重點在於解決未知問題，並儘早降低風險。 技術概念證明 (POC) 有助於驗證假設，且可與部署規劃 (階段 2) 一起反覆進行。 這個階段其輸出是範圍縮小的 Power BI 解決方案。 請注意，我們不打算將 POC 視為一次性的工作。 不過，在階段 4 中可能需要其他工作才能準備好用於生產環境。 就這點來看，在組織中，您可能會將此活動視為原型、試驗、實體模型、快速入門或最簡可行產品 (MVP)。 您不一定要執行 POC，且可以非正式方式完成。 如需階段 3 中活動的詳細資訊，請參閱[進行概念證明以移轉到 Power BI](powerbi-migration-proof-of-concept.md)。

### <a name="stage-4-create-and-validate-content"></a>階段 4：建立和驗證內容

階段 4 是指將 POC 轉換成生產環境就緒解決方案的實際工作完成時。 這個階段其輸出是在開發環境中經過驗證的已完成 Power BI 解決方案。 應該準備好在階段 5 中進行部署。 如需階段 4 中活動的詳細資訊，請參閱[建立內容以移轉到 Power BI](powerbi-migration-create-validate-content.md)。

### <a name="stage-5-deploy-support-and-monitor"></a>階段 5：部署、支援和監視

階段 5 的主要重點在於將新 Power BI 解決方案部署到生產。 這個階段其輸出是商務使用者目前所使用的生產解決方案。 使用敏捷方法時，可規劃一些要在未來反覆執行時提供的增強功能。 根據對 Power BI 的熟悉程度 (例如將風險和使用者中斷的情況降到最低)，您可選擇執行分段部署。 或者，您可一開始部署到較小的試驗使用者群組。 支援和監視在這個階段也很重要，且會持續進行。 如需階段 5 中活動的詳細資訊，請參閱[移轉到 Power BI](powerbi-migration-deploy-support-monitor.md)。

> [!TIP]
> 此系列 Power BI 移轉文章中討論的大部分概念也適用於標準 Power BI 實作專案。

## <a name="consider-migration-reasons"></a>考慮移轉原因

實現高生產力且良好的資料文化是許多組織其主要目標。 Power BI 是協助達成此目標的絕佳工具。 您可能考慮移轉到 Power BI 的三個常見原因如下：

- 引進可提高自助 BI 使用者社群能力的新功能，以 **實現受控自助 BI**。 Power BI 可供更廣泛地存取資訊並制定決策，同時減少依賴不容易找到的專家技能。
- **將企業 BI 的傳遞合理化**，以符合現有 BI 工具未解決的需求，同時降低複雜度、降低擁有權成本，以及/或從目前使用中的多項 BI 工具標準化。
- 減少資源、時間和人員，以 **解決經濟壓力** 來提高生產力。

## <a name="achieve-power-bi-migration-success"></a>成功移轉 Power BI

每個移轉都稍有不同。 這可能取決於組織結構、資料策略、資料管理成熟度和組織目標。 不過，我們持續看到一些客戶成功移轉 Power BI 的實例。

- **執行發起人：** 在程序中及早識別執行發起人。 這個人應該是在組織中積極支持 BI 的使用者，且個人有興趣投資以達成正面的移轉結果。 在理想情況下，執行發起人對於 Power BI 的相關結果具有最終權責。
- **訓練、支援和溝通：** 了解這不僅是一項技術計畫。 任何 BI 或分析專案也是人員計畫，因此請考慮提早投資使用者訓練和支援。 此外，請建立一個溝通計劃，以透明方式向所有利害關係人說明發生的狀況、原因，並設定務實的期望。 請務必在溝通計劃中包含意見回饋，以擷取利害關係人的意見。
- **快速致勝：** 一開始，優先處理具有有形商業價值且急迫的高價值項目。 當處理重新設計的報表時，請專注於報表嘗試解答的商務問題 (包括要採取的動作)，而不只是嘗試一律依舊版 BI 平台中的原狀來移轉報表。
- **現代化與改善：** 願意重新思考過去完成工作的方式。 移轉可提供實現改善的機會。 例如，其可排除手動資料準備工作，或將侷限於單一報表的商務規則重新定位。 如有正當理由，請考慮重構、現代化及合併現有解決方案。 這可能包括將多個報表合併成一個，或排除有一段時間未使用的舊版成品。
- **持續不斷的學習：** 準備使用階段式方法，同時持續不斷的學習和調整。 以簡短反覆的週期來工作，更快實現價值。 經常完成小型 POC 以將未知風險降到最低、驗證假設，以及了解新功能。 由於 Power BI 是每月更新的雲端服務，因此請務必持續掌握發展並適時調整方針。
- **變革阻力：** 了解可能會有各種不同的變革阻力；有些使用者會抗拒學習新工具。 此外，有些投入大量時間心力在取得不同 BI 工具專業知識的專業人員，可能感受到被取代的威脅。 請做好準備，因為這可能會導致內部政治鬥爭，特別是在高度分權的組織中。
- **條件約束：** 請務實地制定移轉計劃，包括資金、預估時間，以及所有相關人員的角色和責任。

## <a name="acknowledgments"></a>通知

此系列文章是由資料平台 MVP 暨 [Coates Data Strategies](https://www.coatesdatastrategies.com/) 擁有者 Melissa Coates 所撰寫。 參與者和審閱者包括 Marc Reguera、Venkatesh Titte、Patrick Baumgartner、Tamer Farag、Richard Tkachuk、Matthew Roche、Adam Saxton、Chris Webb、Mark Vaillancourt、Daniel Rubiolo、David Iseminger 和 Peter Myers。

## <a name="next-steps"></a>後續步驟

在[此 Power BI 移轉系列的下一篇文章](powerbi-migration-pre-migration-steps.md)中，了解移轉到 Power BI 時的移轉前步驟。

其他實用資源包括：

- [Microsoft BI 轉換](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [規劃 Power BI 企業部署白皮書](https://aka.ms/PBIEnterpriseDeploymentWP)
- [將 SSRS 報表移轉至 Power BI](migrate-ssrs-reports-to-power-bi.md)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com/)

經驗豐富的 Power BI 合作夥伴可協助組織成功進行移轉程序。 若要與 Power BI 合作夥伴交流，請造訪 [Power BI 合作夥伴入口網站](https://powerbi.microsoft.com/partners/)。
