---
title: 建立卓越中心
description: 了解卓越中心如何協助 Microsoft 建立標準化的分析和資料平台，以使用正確的作業模型、專案關係人參與和共用與專用投資來顯露見解。
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/19/2020
ms.openlocfilehash: f3cdf40c0cdb17269232093f7407c61b13794a3e
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088641"
---
# <a name="establish-a-center-of-excellence"></a>建立卓越中心

本文的對象是 IT 專業人員和 IT 管理員。 您將了解如何在組織中設定 BI 和分析卓越中心 (COE)，以及 Microsoft 如何設定。

對某些人來說，COE 只是一種技術支援人員，而這種誤解與現實相差甚遠。

一般來說，BI 和分析 COE 是負責建立和維護 BI 平台的專業人員小組。 其也負責建立單一事實來源，和定義一組一致的全公司計量來顯露和加速見解。 不過，COE 是一種廣泛的字詞。 因此，它可以用不同的方式來實作和管理，且其結構和範圍可能會因組織而異。 這在核心上一律都是關於強大的平台在適當時間，將適當資料和見解功能提供給適當的人。 在理想的情況下，它也會提升推廣、定型和支援。 在 Microsoft，將它描述為 _[核心的紀律](center-of-excellence-microsoft-business-intelligence-transformation.md#discipline-at-the-core)_ ，並以 BI 平台和單一事實來源形式提供。

在較大型的組織中，您可找到多個 COE，其中包含核心 COE，由衛星 COE「擴充」—通常是在部門層級。 如此一來，衛星 COE 就是一群熟悉分類法和定義的專家，其知道如何將核心資料轉換成「對其部門」有意義的東西。 部門分析師會獲得核心資料的許可權，並信任其用於自己的報告。 他們會建立解決方案，依賴謹慎準備的核心維度、事實和商務邏輯。 有時候，他們也可以使用較小部門特定的資料集和商務邏輯來擴充。 重要的是，衛星 COE 不會中斷連線，也不會獨立採取行動。 在 Microsoft，衛星 COE 提升了 _[邊緣彈性](center-of-excellence-microsoft-business-intelligence-transformation.md#flexibility-at-the-edge)_ 。

為了讓此擴充案例成功，部門必須「即用即付」。 換句話說，部門必須在財務上投資核心 COE。 如此一來，就不會擔心他們「未得到公平對待」，或甚至是需求遭到取消優先權。

為了支援此案例，核心 COE 必須進行調整，以符合注資部門的需求。 數個資料集上線後，規模經濟便會展現。 在 Microsoft，很快就能看出，集中工作更經濟實惠，且帶來更快的結果。 每個新的主題領域上線時，我們會有更大的規模經濟，其可供在整個平台上運用和貢獻，並強化基礎資料文化。

來看一下一個範例：我們的 BI 平台提供核心維度、事實及商務邏輯以供財務、銷售和行銷之用。 其也定義數百個關鍵效能指標 (KPI)。 現在，Power Platform 企業中的分析師需要準備領導主管儀表板。 某些 KPI (例如營收和管線) 直接來自 BI 平台。 不過，其他則是以更細微的企業需求為基礎。 其中一項需求是針對使用者採用 Power BI 特定功能的 KPI：資料流程。 因此，分析師會產生 Power BI [複合模型](composite-model-guidance.md)整合核心 BI 平台資料與部門資料。 然後新增商務邏輯來定義其部門 KPI。 最後，其會根據新的模型來撰寫領導人員儀表板，利用全公司的 COE 資源，並用當地知識和資料加以擴大。

重要的是，核心與衛星 COE 之間的責任劃分可讓部門分析師專注於創新，而不是管理資料平台。 有時，衛星 COE 與核心 COE 之間甚至可有相互助益的關係。 例如，衛星 COE 可能會定義新的計量，並對其部門證明有益，最後是對整個公司有益的核心計量，且由核心 COE 提供和支援。

## <a name="bi-platform"></a>BI 平台

在組織中，可能會用不同的名稱來稱呼 COE，例如 BI 小組或群組。 名稱的重要性小於實際用途。 如果沒有正式小組，則建議培育一個小組，將核心 BI 專家整合在一起，以建立 BI 平台。

在 Microsoft，COE 稱為 BI 平台。 它有許多專案關係人群組，其代表公司內不同部門，例如財務、銷售和行銷。 它會組織成執行[共用功能](#shared-capabilities)和[專用交付](#dedicated-deliveries)。

:::image type="content" source="media/center-of-excellence-establish/business-intelligence-platform-operating-model.png" alt-text="圖表顯示共用功能和專用交付，如下列各節中所述。":::

### <a name="shared-capabilities"></a>共用功能

共用功能是建立和操作 BI 平台的必要條件。 其支援所有為平台注資的專案關係人群組。 包含下列小組：

- **核心平台工程：** 我們設計了具有工程思維的 BI 平台。 它其實是一組架構，可支援資料擷取、處理以豐富資料，以及在 BI 語意模型中交付該資料供分析師使用。 工程師負責核心 BI 平台功能的技術設計和實作。 例如，其會設計和實作資料管線。
- **基礎結構和裝載：** IT 工程師負責佈建和管理所有 Azure 服務。
- **支援和作業：** 這個小組可讓平台保持執行。 支援會照顧使用者的需要，例如資料許可權等。 作業可讓平台保持執行，確保符合服務等級協定 (SLA)，並溝通延遲或失敗。
- **發行管理：** 技術計畫經理 (PM) 會發行變更。 變更範圍從平台架構更新到對 BI 語意模型進行的變更要求。 這是確保變更不會中斷任何事情的最後防線。

### <a name="dedicated-deliveries"></a>專用交付

每個專案關係人群組都有一個專用的交付小組。 通常是由資料工程師、分析工程師和技術 PM 所組成，並由由其專案關係人群組所資助。

## <a name="bi-team-roles"></a>BI 小組角色

在 Microsoft，BI 平台是由可擴充的專業人員小組運作。 小組會對應到專用和共用的資源。 現在，我們有下列角色：

- **計畫經理：** PM 是專用資源。 其擔任 BI 小組與專案關係人之間的主要連絡人。 其工作是將專案關係人商務需求轉譯為技術規格。 並且，會管理專案關係人交付物的優先順序。
- **資料庫負責人：** 其為負責將新資料集上線至集中式資料倉儲的專用資源。 將資料集上線可能需要設定符合標準的維度、新增商務邏輯和自訂屬性，以及標準名稱和格式設定。
- **分析負責人：** 其為負責設計和開發 BI 語意模型的專用資源。 其致力於使用標準命名和格式設定來套用一致的架構。 效能最佳化是其角色中很重要的一部分。
- **作業和基礎結構：** 其為負責管理作業和資料管線的共用資源。 其也負責管理 Azure 訂用帳戶、Power BI 容量、虛擬機器和資料閘道。
- **支援：** 其為負責撰寫文件、組織定型、溝通 BI 語意模型變更及回答使用者問題的共用資源。

## <a name="governance-and-compliance"></a>治理和合規性

針對每個專案關係人群組，PM 負責人提供跨計畫的控管和監督。 其覆寫目標是確保 IT 投資能夠產生商業價值並降低風險。 定期舉辦籌畫委員會會議，以審查進度並核准主要倡議。

## <a name="grow-your-own-community"></a>擴大自有社群

透過下列方式，在組織中建立並擴大社群：

- 舉辦定期的「上班時間」活動，預留時間給 BI 小組，讓使用者可詢問問題、提出建議、分享想法，甚至提出抱怨。
- 建立 Teams 頻道以提供支援，並鼓勵任何人詢問和回應張貼的問題。
- 經營及推廣非正式使用者群組，並鼓勵員工出席或參加。
- 針對特定產品和 BI 平台本身，舉辦更正式的訓練活動。 考慮提供 [Power BI 一日儀表板](https://powerbi.microsoft.com/diad/) (英文)，這是免費的課程套件，且是向員工首次介紹 Power BI 的絕佳方式。

## <a name="next-steps"></a>後續步驟

如需本文的詳細資訊，請參閱下列資源︰

- [COE 中的 BI 解決方案架構](center-of-excellence-business-intelligence-solution-architecture.md)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com/)

在[此系列的下一篇文章](center-of-excellence-business-intelligence-solution-architecture.md)中，了解 COE 中 BI 方案架構和所採用的不同技術。

### <a name="professional-services"></a>專業服務

認證 Power BI 合作夥伴可協助組織成功設定 COE。 其可提供符合成本效益的訓練或資料稽核。 若要與 Power BI 合作夥伴交流，請造訪 [Power BI 合作夥伴入口網站](https://powerbi.microsoft.com/partners/)。

您也可以與經驗豐富的諮詢合作夥伴進行互動。 其可協助[評定](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=assessment&country=ALL&region=ALL)、[評估](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=proof-of-concept&country=ALL&region=ALL)或[實作](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=implementation&country=ALL&region=ALL&page=1) Power BI。
