---
title: 準備移轉到 Power BI
description: 移轉至 Power BI 時的移轉前步驟指導方針。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: 33bee844aced23973bd033cf0d9ae9d8caa4d267
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418570"
---
# <a name="prepare-to-migrate-to-power-bi"></a>準備移轉到 Power BI

本文描述在移轉至 Power BI 之前可考慮的動作。

:::image type="content" source="media/powerbi-migration-pre-migration-steps/migrate-to-powerbi-pre-migration-steps.png" alt-text="顯示 Power BI 移轉階段的影像。本文強調移轉前的步驟。":::

> [!NOTE]
> 如需上圖的完整說明，請參閱 [Power BI 移轉概觀](powerbi-migration-overview.md)。

移轉前步驟強調前端規劃，這在進行五個移轉階段之前，都是很重要的準備工作。 大部分的移轉前步驟只會發生一次，但對較大型組織而言，可能會針對每個業務單位或部門區域反覆執行某些步驟。

移轉前步驟的輸出包含初始治理模型、初始高階部署規劃，以及所要移轉報表及資料的詳細目錄。 第 1、2 及第 3 階段的活動需要其他資訊，才能完整估計遷移個別解決方案的工作量需求。

> [!TIP]
> 本文中討論的大部分主題也適用於標準 Power BI 實作專案。

## <a name="create-costbenefit-analysis-and-evaluation"></a>建立成本/權益分析與評估

初始評估期間有幾個最重要的考量，包括：

- 清楚了解商業案例及 BI 策略，以達到特定的理想未來狀態。
- 清楚了解成功的意義，以及如何衡量移轉方案的進度與成功。
- 成本預估及投資報酬率 (ROI) 計算結果。
- 數個具生產力 Power BI 方案的成功結果，其針對範圍及複雜性層級較小。

## <a name="identify-stakeholders-and-executive-support"></a>識別專案關係人及主管支援

識別專案關係人有幾個考量，包括：

- 確保與專案關係人在商業案例及 BI 策略上保持一致。
- 納入整個業務單位的代表，即使其內容預定於未來的時程進行移轉，也能瞭解其動機與疑慮。
- 即早納入 Power BI 專家。
- 建立並遵循與專案關係人的溝通計畫。

> [!TIP]
> 如果擔心會變成過度溝通，那麼您大概是對的。

## <a name="generate-initial-governance-model"></a>產生初始治理模型

有幾個幾個重要項目需在 Power BI 的實作初期解決，包括：

- 採用 Power BI 的特定目標，以及 Power BI 該如何融入組織整體的 BI 策略。
- 如何處理 Power BI 系統管理員角色，特別是在分散的組織中。
- 達成受信任資料的相關原則：使用授權資料來源、解決資料品質問題，以及使用一致的術語與一般定義。
- 將資料來源、資料模型、報表及內容傳遞給內部與外部使用者的安全性及資料隱私權策略。
- 如何符合內部及外部合規性、法規與稽核需求。

> [!IMPORTANT]
> 最有效的治理模型致力於平衡使用者權限與所需控制層級。 如需詳細資訊，請參閱[核心的紀律](center-of-excellence-microsoft-business-intelligence-transformation.md#discipline-at-the-core)及[邊緣的彈性](center-of-excellence-microsoft-business-intelligence-transformation.md#flexibility-at-the-edge)。

## <a name="conduct-initial-deployment-planning"></a>進行初始部署規劃

初始部署規劃牽涉到為組織實作 Power BI 的定義標準、原則及喜好設定。

請注意，[第 2 階段](powerbi-migration-planning.md)會參考解決方案層級的部署規劃。 第 2 階段活動應該盡可能遵守組織層級的決策。

有些重要項目需在 Power BI 的實作初期解決，包括：

- [Power BI 租用戶設定](admin-tenant-settings.md)決策，應納入記錄。
- [工作區管理](../collaborate-share/service-new-workspaces.md)決策，其應納入記錄。
- 與資料及[內容散發方法](../collaborate-share/service-how-to-collaborate-distribute-dashboards-reports.md)相關的考量及偏好設定，例如應用程式、工作區、共用、訂閱及內容內嵌。
- 與[資料集模式](../connect-data/service-dataset-modes-understand.md)相關的偏好設定，例如使用匯入模式、DirectQuery 模式，或在[複合模型](composite-model-guidance.md)中結合使用這兩種模式。
- [保護資料及存取](../admin/service-admin-power-bi-security.md)。
- 使用[共用資料集](../connect-data/service-datasets-share.md)以供重複使用。
- 套用[資料認證](../collaborate-share/service-endorsement-overview.md)，以推廣使用授權與受信任資料。
- 使用不同的[報表類型](../create-reports/index.yml)，包含不同使用案例或業務單位的 Power BI 報表、Excel 報表或編頁報表。
- 變更管理集中式 BI 成品及公司管理 BI 成品的管理方法。
- 取用者、資料建模者、報表作者及系統管理員的訓練計畫。
- 支援內容作者，方法是使用 [Power BI Desktop 範本](../create-reports/desktop-templates.md)、[自訂視覺效果](https://powerbi.microsoft.com/blog/how-to-govern-power-bi-visuals-inside-your-organization/)，以及已納入記載的報表設計標準。
- 管理使用者需求的流程及程序，例如要求新的授權、新增閘道資料來源、取得閘道資料來源權限、要求新的工作區、工作區權限變更，以及其他可能定期出現的常見需求。

> [!IMPORTANT]
> 部署規劃是一項反覆的程序。 部署決策會隨著組織運用 Power BI 的經驗不斷增長，以及 Power BI 的發展，而進行多次調整及擴充。 在此期間所做決定會用於移轉程序[第 2 階段](powerbi-migration-planning.md)中所討論的解決方案層級部署規劃期間。

## <a name="establish-initial-architecture"></a>建立初始架構

[BI 解決方案架構](center-of-excellence-business-intelligence-solution-architecture.md)會隨著時間不斷演進與成熟。 應立即處理的 Power BI 設定工作包括：

- Power BI 租用戶設定及 Azure Active Directory 整合。
- 定義 [Power BI 系統管理員](../admin/service-admin-role.md)。
- 採購並指派初始[使用者授權](../admin/service-admin-licensing-organization.md)。
- 設定及檢閱 [Power BI 租用戶設定](admin-tenant-settings.md)。
- 設定 [工作區角色](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces)，並將存取權指派給 Azure Active Directory 安全性群組及使用者。
- 設定初始[資料閘道](../connect-data/service-gateway-deployment-guidance.md)叢集，並規劃定期更新。
- 採購初始 [Premium 容量授權](../admin/service-admin-premium-purchase.md) (如果適用)。
- 設定 [Premium 容量工作負載](../admin/service-admin-premium-workloads.md)，並規劃持續性的管理。

## <a name="define-success-criteria-for-migration"></a>定義移轉的成功準則

第一項工作就是了解移轉個別解決方案的成功標準。 您可能會問的問題包括：

- **這種移轉的特定動機及目標是什麼？** 如需詳細資訊，請參閱 [Power BI 移轉概觀 (考慮移轉原因)](powerbi-migration-overview.md#consider-migration-reasons)。 此文描述移轉至 Power BI 最常見的原因。 當然，目標應指定於組織層級。 除此之外，移轉舊版 BI 解決方案可能會獲益於節省的成本，而移轉不同的舊版 BI 解決方案，可能需要專注於取得工作流程最佳化的優勢。
- **這項移轉的預期成本/權益或 ROI 為何？** 清楚了解與成本、所增加功能、降低的複雜度，或所增加彈性相關的預期，對於衡量成功很有幫助。 其可提供指導原則，進而協助在移轉過程中制定決策。
- **哪些關鍵效能指標(KPI) 會用來衡量成功？** 下列清單中列出部分範例 KPI：
    - 從舊版 BI 平台轉譯的報表數目，每月遞減。
    - 從 Power BI 轉譯的報表數目，每月遞增。
    - Power BI 報表取用者數目，每季遞增。
    - 依目標日期移至生產的報表百分比。
    - 每年遞減的授權成本。

> [!TIP]
> [Power BI 活動記錄](../admin/service-admin-auditing.md)可用作衡量 KPI 進度的來源。

## <a name="prepare-inventory-of-existing-reports"></a>準備現有報表的詳細目錄

準備舊版 BI 平台中現有報表的詳細目錄，是了解已經具備哪些內容的重要步驟。 此步驟會得出用以評估移轉工作量需求的資料。 準備詳細目錄的相關活動可能包括：

1. **報表詳細目錄：** 編譯屬於移轉候選方案的報表及儀表板清單。
2. **資料來源的詳細目錄：** 編譯現有報表所存取所有資料來源的清單。 其應包含企業資料來源，以及部門與個人資料來源。 此程序可能會發現 IT 部門先前所未知的資料來源，這些來源通常稱為「影子 IT」。
3. **稽核記錄：** 取得舊版 BI 平台稽核記錄中的資料，以了解使用模式並協助排定優先順序。 要從稽核記錄取得的重要資訊包括：
    - 每週/每月/每季執行各個報表的平均次數。
    - 每週/每月/每季各個報表的平均取用者數目。
    - 每個報表的取用者，特別是主管所使用的報表。
    - 各個報表的最近一次執行日期。

> [!NOTE]
> 在許多情況下，內容並不會完全依照原樣移轉至 Power BI。 移轉代表有機會重新設計資料架構及/或改善報表傳遞。 編譯報表詳細目錄對於了解目前存在的內容非常重要，因此您可著手評估所需進行的重構。 本系列中其餘文章會更詳細地描述可能的改善。

## <a name="explore-automation-options"></a>探索自動化選項

您無法從端對端完全自動化 Power BI 轉換程序。

當有現有工具可使用時，編譯現有的資料及報表詳細目錄也可以是自動化的一項候選方案。 自動化可用於移轉程序的部分 (例如編譯現有的詳細目錄)，高度取決於您擁有的工具。

## <a name="next-steps"></a>後續步驟

在 [Power BI 移轉系列的下一篇文章中](powerbi-migration-requirements.md)深入了解第 1 階段，這與移轉到 Power BI 時收集需求並排列優先順序相關。

其他實用資源包括：

- [Microsoft BI 轉換](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [規劃 Power BI 企業部署白皮書](https://aka.ms/PBIEnterpriseDeploymentWP)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com/)

經驗豐富的 Power BI 合作夥伴可協助組織成功進行移轉程序。 若要與 Power BI 合作夥伴交流，請造訪 [Power BI 合作夥伴入口網站](https://powerbi.microsoft.com/partners/)。
