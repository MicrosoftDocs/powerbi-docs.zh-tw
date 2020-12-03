---
title: 從客戶 Power BI 移轉中學習
description: 在移轉至 Power BI 時向客戶學習。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: fd5490eae689a4119566474da2ef4d19017a8134
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96419168"
---
# <a name="learn-from-customer-power-bi-migrations"></a>從客戶 Power BI 移轉中學習

本文是移轉至 Power BI 的系列總結，從兩個成功移轉至 Power BI 的客戶案例，分享所學到的重要經驗。

## <a name="international-consumer-goods-company"></a>國際消費性商品公司

一家銷售數百項產品的國際消費性商品公司，在 2017 年決定採用雲端優先策略。 公司選取 Power BI 作為商業智慧 (BI) 平台的主要因素之一，是因為其與 Azure 和 Microsoft 365 的深入整合。

### <a name="conduct-a-phased-migration"></a>進行階段式移轉

在 2017 年，公司開始使用 Power BI。 組織最初的目標是引進 Power BI 作為額外的 BI 工具。 此決策讓內容作者、取用者和 IT 人員有時間適應提供 BI 的新方式。 也讓他們可以培養 Power BI 的專業知識。

在 2018 年下半年間，公司發出正式公告，宣告 Power BI 成為組織核准的 BI 工具。 因此，所有新的 BI 開發工作都應該在 Power BI 中進行。 Power BI Premium 的推出，是制定此決策的關鍵驅動因素。 此時，組織不建議使用舊版 BI 平台，並規劃開始進行轉換。

到 2019 年底，開始將現有內容從舊版 BI 平台移轉至 Power BI。 一些早期採用者已快速移轉其內容。 這有助於更進一步提高組織內部使用 Power BI 的動力。 接著，要求內容擁有者和作者開始準備，以便在 2020 年底前完全移轉至 Power BI。 組織仍然面臨技能、時間和資金的相關挑戰，但這些挑戰皆與技術平台本身無關。

> [!IMPORTANT]
> 當 Power BI 在組織內已成功並根深蒂固之後，便要求業務單位從舊版 BI 平台進行正式移轉。

### <a name="prepare-to-handle-varying-responses"></a>準備處理各種不同的回應

在這個大型的非集中式組織中，對於移至 Power BI 的接受度和意願各有不同。 除了時間與預算的相關考量之外，還有員工為了培養舊版 BI 平台技能而投入了大量的心血。 因此，對於宣佈要將 Power BI 制式化的這項消息，並非所有人都歡迎。 由於每個業務單位都有自己的預算，因此個別的業務單位可能會挑戰類似的決策。 在中央制定 IT 工具決策時，會導致執行發起人和 BI 領導者必須面對一些挑戰。

> [!IMPORTANT]
> 與業務單位中的領導團隊溝通非常重要，這可確保其了解將 Power BI 制式化的高階組織優勢。 當移轉進行到接近淘汰舊版 BI 平台的時日，有效的溝通益發重要。

### <a name="focus-on-the-bigger-picture"></a>著重全局

公司發現，雖然某些移轉的報表可以複寫類似的原始設計，但不是每個報表都能在 Power BI 中如實複寫。 不過，這是可預期的，因為所有的 BI 平台都不同。 這表示需要不同的設計思維。

指引內容作者專注於在 Power BI 中建立適合目的的報表，而不是嘗試使用與舊版報表相同的複本。 因此，在移轉過程中特別需要主題專家，提供諮詢和確認。 把心思放在考量報表設計目的，並在適當時加以改良。

> [!IMPORTANT]
> 有時候在接受移轉期間，是改良的好時機。 在其他時候，更好的選擇是提供與之前完全相同的價值，而不進行大幅改良，以免干擾到移轉時間表。

### <a name="cautiously-assess-priorities"></a>謹慎評定優先順序

針對舊版 BI 平台進行分析，以便充分了解其使用量。 舊版 BI 平台含有數千個已發佈的報表，去年存取了其中大約一半的報表。 當評定哪些報表會提供重要的價值給組織時，該數字可能會再減半。 這些報表會優先進行移轉。

> [!IMPORTANT]
> 您很容易會高估報表的實際重要性。 若是不常使用的報表，請評估其是否可以完全淘汰。 有時候，最簡單便宜的做法就是什麼都不留。

### <a name="cautiously-assess-complexity"></a>謹慎評定複雜度

在排列優先處理的報表中，會根據預估投入心力的程度 (簡單、中等或複雜) 累積預估時間。 雖然這聽起來像是相當直接的程序，但別期望每個報表所預估的時間都準確。 您可能會發現某個預估非常不準確。 例如，公司有一份公認為非常複雜的報表。 顧問預估需要 50 天才能轉換。 不過，在 Power BI 中重新設計的報表，則能在大約 50 小時內完成。

> [!IMPORTANT]
> 雖然取得資金和人員指派通常都需要預估時間，但彙總起來的價值可能最高。

### <a name="decide-how-change-management-is-handled"></a>決定變更管理的處理方式

由於 BI 資產數量很高，因此對公司擁有的報表進行變更管理會是一項挑戰。 IT 管理的報表是根據標準變更管理實務來處理。 不過，由於數量龐大，因此不可能集中變更公司擁有的內容。

> [!IMPORTANT]
> 當無法從中央小組管理變更時，其餘的責任就會落在各業務單位。

### <a name="create-an-internal-community"></a>建立內部社群

公司建立了卓越中心 (COE)，提供內部訓練課程和資源。 此 COE 也是內部諮詢小組，可隨時協助內容作者解決技術問題、排除障礙，並提供最佳做法指引。

此外，還有內部 Power BI 社群，共計超過 1,600 名成員，可謂相當成功。 此社群是在 Yammer 中管理。 成員可以詢問內部相關的問題，並獲得遵守最佳做法及符合組織條件約束的解答。 這種使用者對使用者的互動類型，可大幅減輕 COE 的支援負擔。 不過，COE 會監視問題與解答，並在適當時參與交談。

更新的 Power BI 專家網路，是內部社群的延伸。 其中包含組織內幾位精挑細選的 Power BI 達人。 這些人是業務單位中具備高度技能的 Power BI 實踐者、熱心的擁護者，也是積極想要解決公司內部挑戰的人員。 Power BI 專家網路成員必須遵守 COE 所建立的最佳做法和指導方針，並協助更廣泛的內部 Power BI 社群了解及加以實作。 雖然 Power BI 專家網路與 COE 協同合作並可獲得專門訓練，但 Power BI 專家是與 COE 分開運作。 每個 Power BI 專家都可以定義其運作方式的規範，別忘了他們在原先的職位上還有其他責任和優先事項。

> [!IMPORTANT]
> 請為 COE 的功能妥善定義一個範圍，例如：採用、控管、指引、最佳做法、訓練、支援，甚至是實作開發。 雖然 COE 非常重要，但計算投資報酬可能會很棘手。

### <a name="monitor-migration-progress-and-success"></a>監視移轉進度及是否成功

關鍵效能指標 (KPI) 會在移轉至 Power BI 期間持續受到監視。 其可協助公司了解計量的趨勢，例如報表瀏覽次數、使用中報表數目及每月相異使用者人數。 隨著舊版 BI 平台使用量降低，會測量到 Power BI 使用量增加，目標是要達到逆轉的關係。 每月會更新目標以因應變更。 如果使用量低於預期，將會識別瓶頸之所在，以利採取適當動作。

> [!IMPORTANT]
> 建立移轉計分卡，包含可採取動作的商業智慧，可監視移轉工作是否成功。

## <a name="large-transportation-and-logistics-company"></a>大型運輸和物流公司

大型北美運輸和物流公司正積極投資資料基礎結構和分析系統的現代化。

### <a name="allow-a-period-of-gradual-growth"></a>允許一段時日的漸進成長

公司在 2018 年開始使用 Power BI。 到 2019 年中，Power BI 成為所有新 BI 使用案例偏好使用的平台。 然後，在 2020 年，公司將重點放在逐步淘汰現有的 BI 平台，以及各種自訂開發的 ASP.NET BI 解決方案。

> [!IMPORTANT]
> 等到組織中有許多 Power BI 現用使用者後，再開始逐步淘汰其舊版 BI 平台和解決方案。

### <a name="balance-centralized-and-distributed-groups"></a>平衡集中式和分散式群組

在公司中，有兩種類型的 BI 小組：中央 BI 小組和分散在整個組織的分析群組。 中央 BI 小組具有 Power BI 即平台的擁有權責任，但不擁有任何內容。 因此，中央 BI 小組是支援分散式分析群組的技術提供中樞。

每個分析群組會專門負責特定業務單位或共用服務功能。 小型群組可能包含一位分析師，而較大的群組則可以有 10-15 位分析師。

> [!IMPORTANT]
> 分散式分析群組是由熟悉日常商務需求的主題專家所組成。 此區分可讓中央 BI 小組主要專注於 BI 服務和工具的技術提供和支援。

### <a name="focus-on-dataset-reusability"></a>專注於資料集再使用性

依賴自訂 ASP.NET BI 解決方案，會妨礙開發新的 BI 解決方案。 其所需的技能，使得自助內容作者的人數不多。 因為 Power BI 是更平易近人的工具 (專為自助 BI 所設計)，所以發行後會快速散佈到整個組織。

提升公司內資料分析師的能力，會產生立即的正面結果。 不過，Power BI 開發一開始的焦點是放在視覺效果上。 雖然會產生寶貴的 BI 解決方案，但此焦點會導致大量的 Power BI Desktop 檔案，而且每個檔案在報表及其資料集之間都有一對一關聯性。 這會產生許多資料集，以及重複的資料和商務邏輯。 為了減少重複的資料、邏輯和工作，公司為內容作者提供了訓練和支援。

> [!IMPORTANT]
> 包含在您內部訓練工作中重複使用資料的重要性相關資訊。 儘早處理重要的概念。

### <a name="test-data-access-multiple-ways"></a>以多種方式測試資料存取

公司的資料倉儲平台是 DB2。 根據目前的資料倉儲設計，公司發現 DirectQuery 模型 (而不是匯入模型) 最適合其需求。

> [!IMPORTANT]
> 進行技術概念證明，評估最適合的模型儲存模式。 此外，指導資料模型製作人員有關模型儲存模式的資訊，以及如何為其專案選擇適當的模式。

### <a name="educate-authors-about-premium-licensing"></a>指導作者有關 Premium 授權的資訊

由於相較於其舊版 BI 平台更容易開始使用 Power BI，因此許多早期採用者都是沒有舊版 BI 工具授權的人員。 如預期般，內容作者的人數已大幅增加。 這些內容作者理所當然想要與其他人共用其內容，因此持續需要額外的 Power BI Pro 授權。

公司大量投資 Premium 工作區，最值得注意的是將 Power BI 內容散發給具有 Power BI 免費授權的許多使用者。 支援小組與內容作者合作，以確保其在適當時使用 Premium 工作區。 這可在使用者只需要取用內容時，避免不必要地配置 Power BI Pro 授權。

> [!IMPORTANT]
> 授權問題經常發生。 請準備好指導並協助內容作者解決授權問題。 驗證 Power BI Pro 授權的使用者要求是否具有正當性。

### <a name="understand-the-data-gateways"></a>了解資料閘道

公司在初期有許多個人閘道。 使用內部部署資料閘道叢集，可將管理工作轉移到中央 BI 小組，讓內容作者社群能夠專注於產生內容。 中央 BI 小組與內部 Power BI 的使用者社群合作，以減少個人閘道數目。

> [!IMPORTANT]
> 請規劃建立和管理內部部署資料閘道。 決定誰可以安裝和使用個人閘道，並使用閘道原則來強制執行。

### <a name="formalize-your-support-plan"></a>形成支援方案

隨著組織內有越來越多人採用 Power BI，公司發現多層式支援方法相當有用：

- **第 1 層：內部小組：** 人們每天彼此教學相長。
- **第 2 層：Power BI 社群：** 人們詢問內部小組社群問題，彼此學習並傳達重要資訊。
- **第 3 層：中央 BI 小組和 COE：** 人們提交電子郵件要求以取得協助。 每週舉辦兩次「上班時間」研討會，共同討論問題並分享想法。

> [!IMPORTANT]
> 雖然前兩層較不正式，但與第三層支援同等重要。 經驗豐富的使用者通常主要會依賴認識的人，而較新的使用者 (或是業務單位或共用服務的唯一資料分析師) 則傾向依賴正式支援。

### <a name="invest-in-training-and-governance"></a>投資訓練和控管

過去一年來，公司改善了其內部訓練供應項目，並增強其資料控管計畫。 控管委員會包含來自每個分散式分析群組的主要成員，加上 COE。

在其內部目錄中，現在有六個內部 Power BI 課程。 [Dashboard in a Day](https://powerbi.microsoft.com/diad/) 課程仍是新手的熱門課程。 為了協助使用者加深技能，他們提供一系列包含三個 Power BI 課程和兩個 DAX 課程。

其中一個最重要的資料控管決策與管理 Premium 容量相關。 公司選擇在業務單位和共用服務的重要分析區域使用容量。 因此，如果發生效率不佳的情況，則只有該區域會受到影響，而且非集中式容量管理員能夠視情況來管理容量。

> [!IMPORTANT]
> 注意如何使用 Premium 容量，以及如何為其指派工作區。

## <a name="next-steps"></a>後續步驟

其他實用資源包括：

- [Microsoft BI 轉換](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [規劃 Power BI 企業部署技術白皮書](https://aka.ms/PBIEnterpriseDeploymentWP) (英文)
- [Dashboard in a Day](https://powerbi.microsoft.com/diad/)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com/)

經驗豐富的 Power BI 合作夥伴可協助貴組織成功進行移轉程序。 若要與 Power BI 合作夥伴交流，請造訪 [Power BI 合作夥伴入口網站](https://powerbi.microsoft.com/partners/)。
