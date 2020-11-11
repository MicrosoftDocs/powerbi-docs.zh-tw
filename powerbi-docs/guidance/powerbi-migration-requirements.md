---
title: 收集需求以移轉到 Power BI
description: 在移轉到 Power BI 時收集需求並排列優先順序的相關指引。
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/20/2020
ms.author: v-pemyer
ms.openlocfilehash: 21d619c42648f90746af9961475bb531dc24d5ab
ms.sourcegitcommit: 37bd34053557089c4fbf0e05f78e959609966561
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94396635"
---
# <a name="gather-requirements-to-migrate-to-power-bi"></a>收集需求以移轉到 Power BI

本文描述 **階段 1** ，這與移轉到 Power BI 時收集需求並排列優先順序相關。

:::image type="content" source="media/powerbi-migration-requirements/migrate-to-powerbi-stage-1.png" alt-text="顯示 Power BI 移轉階段的影像。本文的重點在於階段 1。":::

> [!NOTE]
> 如需上圖的完整說明，請參閱 [Power BI 移轉概觀](powerbi-migration-overview.md)。

階段 1 的重點在於資訊收集，並規劃要移轉到 Power BI 的個別解決方案。

階段 1 中輸出包括已排列優先順序的詳細需求。 不過，必須完成階段 2 和 3 中的其他活動，才能完全預估工作量。

> [!IMPORTANT]
> 階段 1-5 代表與一個特定解決方案相關的活動。 部分組織/租用戶層級的決策和活動會影響解決方案層級中程序。 [Power BI 移轉概觀](powerbi-migration-overview.md)一文中會討論一些較高階的規劃活動。 適當時，請延後到組織層級決策以取得效率和一致性。

> [!TIP]
> 本文中討論的大部分主題也適用於標準 Power BI 實作專案。

## <a name="compile-requirements"></a>編譯需求

現有 BI 成品其清查 (在[移轉前步驟](powerbi-migration-pre-migration-steps.md)中編譯) 會成為在 Power BI 中所建立新解決方案的需求輸入。 收集需求旨在了解目前的狀態，以及在 Power BI 中重新設計報表時，使用者想要變更或重構哪些項目。 詳細需求對於[階段 2](powerbi-migration-planning.md) 中的解決方案部署規劃、在[階段 3](powerbi-migration-proof-of-concept.md) 中建立概念證明期間，以及在[階段 4](powerbi-migration-create-validate-content.md) 中建立生產環境就緒解決方案時都很有用。

### <a name="gather-report-requirements"></a>收集報表需求

編譯完整、容易參考的報表相關資訊，例如：

- **用途、對象和預期的動作：** 識別適用於每個報表的用途和商務程序，以及對象、分析工作流程和報表取用者應採取的預期動作。
- **取用者如何使用報表：** 請考慮與現有報表其報表取用者坐下來了解報表的實際用途。 您可了解要在新版 Power BI 中排除或改善的特定報表項目。 此程序需要投入額外的時間，但對於重要報表或經常使用的報表會很有幫助。
- **擁有者和主題專家：** 識別報表擁有者，以及與報表或資料領域相關的任何主題專家。 其可能會成為未來新 Power BI 報表的擁有者。 包括任何特定變更管理需求 (通常在 IT 管理的解決方案與公司管理的解決方案之間會有所不同)，以及未來進行變更時所需的核准與簽署。
- **內容傳遞方法：** 釐清報表取用者對內容傳遞的期望。 可能是依需求以互動方式執行、內嵌在自訂應用程式中，或使用電子郵件訂閱的排程傳遞。 此外，可能也會有觸發警示通知的需求。
- **互動功能需求：** 判斷「必須具備」和「可有可無」的互動功能需求，例如篩選、向下切入或鑽研。
- **資料來源：** 確保已探索報表所需的所有資料來源，並了解資料延遲需求 (資料有效期限)。 識別每個報表的歷程記錄資料、趨勢和資料快照需求，使其能夠與資料需求一致。 稍後對新報表及其來源資料執行資料驗證時，資料來源文件可能也很有用。
- **安全性需求：** 釐清安全性需求 (例如允許的檢視人員、允許的編輯人員及任何資料列層級安全性需求)，包括一般組織安全性的任何例外。 記錄任何資料敏感度等級、資料隱私權或法規/合規性需求。
- **計算、KPI 和商務規則：** 識別並記錄目前在現有報表內定義的所有計算、KPI 和商務規則，使其能夠與資料需求一致。
- **可用性、版面配置和外觀需求：** 識別與資料視覺效果、群組和排序需求，以及可見度條件相關的特定可用性、版面配置和外觀需求。 包括任何與行動裝置傳遞相關的特定考量。
- **列印和匯出需求：** 判斷是否對列印、匯出或細節完美的版面配置有任何特定需求。 這些需求會影響最適合的報表類型 (例如 Power BI、Excel 或編頁報表)。 請注意，報表取用者通常非常注重過去的工作方式，因此不要害怕挑戰其思考方式。 討論時，請務必著重於「改善」而不是「變革」。
- **風險或疑慮：** 判斷報表是否有其他技術或功能需求，以及有關其所呈現資訊的任何風險或疑慮。
- **開放式問題和待辦項目：** 識別目前要新增至待辦項目的任何未來維護、已知問題或延後要求。

> [!TIP]
> 請考慮將需求分類為「必須具備」或「可有可無」來予以排序。 取用者經常會事先要求可能需要的所有項目，因為其認為這可能是提出要求的唯一機會。 此外，在處理多個反覆項目中的優先順序時，請將待辦項目提供給利害關係人。 這有助於溝通、制定決策，以及追蹤待決的承諾。

### <a name="gather-data-requirements"></a>收集資料需求

編譯與資料有關的詳細資訊，例如：

- **現有的查詢：** 識別是否有現有的報表查詢或預存程序可供 [DirectQuery 模型](../connect-data/desktop-use-directquery.md)或 [複合模型](../transform-model/desktop-composite-models.md)使用，或可轉換成匯入模型。
- **資料來源的類型：** 編譯所需的資料來源類型，包括集中式資料來源 (例如企業資料倉儲)，以及非標準資料來源 (例如可擴充企業資料來源以進行報告的一般檔案或 Excel 檔案)。 找出資料來源所在的位置對於[資料閘道](../connect-data/service-gateway-onprem.md)連線也很重要。
- **資料結構和清理需求：** 判斷每個必要資料來源的資料結構，以及所需的 [資料清理](../transform-model/desktop-query-overview.md)活動範圍。
- **資料整合：** 當有多個資料來源時，評定如何處理資料整合，以及如何定義每個模型資料表之間的 [關聯性](../transform-model/desktop-create-and-manage-relationships.md)。 識別簡化模型所需的特定資料項目，並[縮小其大小](import-modeling-data-reduction.md)。
- **可接受的資料延遲：** 判斷每個資料來源的資料延遲需求。 這會影響要使用哪種[資料儲存模式](../transform-model/desktop-storage-mode.md)的決策。 了解匯入模型資料表的資料重新整理頻率也很重要。
- **資料量和可擴縮性：** 評估預期的資料量，這會列入 [大型模型支援](../admin/service-premium-large-models.md)以及設計 DirectQuery 或 [複合模型](../transform-model/desktop-composite-models.md)的相關決策考量。 了解歷程記錄資料需求的相關考量也很重要。 針對較大型的資料集，還需要判斷[累加式資料重新整理](../admin/service-premium-incremental-refresh.md)規則。
- **量值、KPI 和商務規則：** 評定量值、KPI 和商務規則的需求。 這會影響有關在何處套用邏輯的決策：在資料集或資料整合程序中。
- **主要資料和資料目錄：** 請考慮是否有需要注意的主要資料問題。 判斷與企業資料目錄的整合是否適合用於增強可搜尋性、存取定義，或產生組織接受的一致術語。
- **安全性和資料隱私權：** 判斷是否對資料集有任何特定安全性或資料隱私權考量，包括 [資料列層級安全性](../admin/service-admin-rls.md)需求。
- **開放式問題和待辦項目：** 將目前的任何已知問題、已知資料品質瑕疵、未來維護或延後要求新增至待辦項目。

> [!IMPORTANT]
> 透過[共用資料集](../connect-data/service-datasets-share.md)可達成資料的再使用性，其可選擇性地[認證](../collaborate-share/service-endorse-content.md)共用資料集，以指出可信度並改善可搜尋性。 透過[資料流程](../transform-model/dataflows/dataflows-introduction-self-service.md)可達成資料準備再使用性，以減少多個資料集中的重複邏輯。 資料流程也可大幅減少來源系統上的負載，因為資料的擷取頻率較低 (多個資料集可接著從資料流程匯入資料)。

## <a name="identify-improvement-opportunities"></a>識別改善機會

在大部分的情況下，都會進行一些修改和改善。 很少會出現沒有任何重構或增強的直接一對一移轉。 您可考慮的三種改善類型包括：

- **合併報表：** 類似的報表可使用篩選、書籤或個人化等技術進行合併。 擁有較少報表但每個報表更有彈性，可大幅改善報表取用者的體驗。 請考慮將[問與答 (自然語言查詢)](../natural-language/q-and-a-best-practices.md) 的資料集最佳化，以提供更大的彈性給報表取用者，使其可建立自己的視覺效果。
- **效率提升：** 在需求收集期間，通常可找到改善機會。 例如，當分析師手動編譯數字時，或當可簡化工作流程時。 [Power Query](../transform-model/desktop-query-overview.md) 在取代目前執行的手動活動方面可能扮演重要角色。 如果商務分析師發現自己執行相同的活動來定期清理和準備資料，則可重複的 Power Query 資料準備步驟將能夠大幅節省時間並減少錯誤。
- **集中管理資料模型：** 經授權和認證資料集是受控自助 BI 的骨幹。 在此情況下，只會管理資料一次，而分析師可彈性地使用並擴充該資料，以符合其報告和分析需求。

> [!NOTE]
> 如需集中管理資料模型的詳細資訊，請參閱[核心的紀律](center-of-excellence-microsoft-business-intelligence-transformation.md#discipline-at-the-core)和[邊緣的彈性](center-of-excellence-microsoft-business-intelligence-transformation.md#flexibility-at-the-edge)。

## <a name="prioritize-and-assess-complexity"></a>排列優先順序並評定複雜度

此時會提供初始清查，並可能包括特定需求。 為一組準備要移轉的初始 BI 成品排列優先順序時，應該合併考量報表和資料，也應該彼此獨立考量。

識別高優先順序的報表，這可能包括下列類型的報表：

- 為公司帶來重要價值。
- 經常執行。
- 資深領導階層或主管需要。
- 牽涉到合理程度的複雜度 (以改善初始移轉反覆執行期間的成功機率)。

識別高優先順序的資料，這可能包括下列類型的資料：

- 包含重要資料項目。
- 是可服務許多使用案例的常見組織資料。
- 可用來建立共用資料集，以供報表和許多報表作者重複使用。
- 牽涉到合理程度的複雜度 (以改善初始移轉反覆執行時的成功機率)。

## <a name="next-steps"></a>後續步驟

在 [Power BI 移轉系列的下一篇文章](powerbi-migration-planning.md)中了解階段 2，這與規劃單一 Power BI 解決方案移轉相關。

其他實用資源包括：

- [Microsoft BI 轉換](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [規劃 Power BI 企業部署白皮書](https://aka.ms/PBIEnterpriseDeploymentWP)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com/)

經驗豐富的 Power BI 合作夥伴可協助組織成功進行移轉程序。 若要與 Power BI 合作夥伴交流，請造訪 [Power BI 合作夥伴入口網站](https://powerbi.microsoft.com/partners/)。