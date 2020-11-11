---
title: 規劃部署以移轉至 Power BI
description: 在移轉至 Power BI 時規劃部署的指導方針。
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/20/2020
ms.author: v-pemyer
ms.openlocfilehash: fd57d893a0c381c345364306e04d4897597b36f1
ms.sourcegitcommit: 37bd34053557089c4fbf0e05f78e959609966561
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94396970"
---
# <a name="plan-deployment-to-migrate-to-power-bi"></a>規劃部署以移轉至 Power BI

本文描述 **第 2 階段** ，這與規劃單一 Power BI 解決方案的移轉相關。

:::image type="content" source="media/powerbi-migration-planning/migrate-to-powerbi-stage-2.png" alt-text="顯示 Power BI 移轉階段的影像。本文的重點在於第 2 階段。":::

> [!NOTE]
> 如需上圖的完整說明，請參閱 [Power BI 移轉概觀](powerbi-migration-overview.md)。

第 2 階段的重點在於定義如何使用第 1 階段中所定義的需求來將解決方案移轉至 Power BI。

第 2 階段其輸出包含盡可能多的特定決策，以引導部署程序。

這種決策是一種反覆且非線性的程序。 而部分規劃已於[遷移前步驟](powerbi-migration-pre-migration-steps.md)中制定。 學習概念證明 (如[第 3 階段](powerbi-migration-proof-of-concept.md)中所述) 可能會與部署規劃同時進行。 即使在建立解決方案時 (如[第 4 階段](powerbi-migration-create-validate-content.md)中所述)，也可能會出現影響部署規劃決策的其他資訊。

> [!IMPORTANT]
> 第 1-5 階段代表與特定解決方案相關的活動。 部分組織/租用戶層級的決策和活動會影響解決方案層級中程序。 [Power BI 移轉概觀](powerbi-migration-overview.md)一文中會討論一些較高階的規劃活動。 在情況適當時，請延後組織層級決策，以取得效率及一致性。

> [!TIP]
> 本文中討論的主題也適用於標準 Power BI 實作專案。

## <a name="choose-power-bi-product"></a>選擇 Power BI 產品

首要決策是選擇 Power BI 產品。 您需決定使用 [Power BI 服務](../fundamentals/power-bi-service-overview.md) 或 [Power BI 報表伺服器](../report-server/get-started.md)。 在發佈內容之後，即可使用許多其他選項，例如內嵌、行動傳遞及電子郵件訂閱。

如需架構考量的詳細資訊，請參閱 [規劃 Power BI 企業部署白皮書](https://aka.ms/PBIEnterpriseDeploymentWP)的 **第 3 節** 。

> [!CAUTION]
> 請注意，若想要依賴使用儲存在檔案系統中的 Power BI Desktop 檔案，則此非最佳方法。 使用 Power BI 服務 (或 Power BI 報表伺服器) 對安全性、內容發佈及共同作業有極大的好處。 Power BI 服務也會啟用稽核與監視活動的功能。

## <a name="decide-on-workspace-management-approach"></a>決定工作區管理方法

[工作區](../collaborate-share/service-new-workspaces.md)是 Power BI 服務的核心概念，這讓工作區管理成為規劃的重要層面。 問題包括：

- 此全新解決方案需要新的工作區嗎？
- 需要個別的工作區來容納開發、測試及生產嗎？
- 資料及報表會使用個別的工作區，或單一工作區是否足夠？ 個別工作區有許多優點，尤其是關於保護資料集方面。 必要時，可由發佈報表的使用者分開管理。
- 工作區的安全性需求為何？ 這將影響[工作區角色](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces)的規劃。 如果內容取用者會使用應用程式，則[應用程式權限](../collaborate-share/service-create-distribute-apps.md#publish-your-app)會與工作區分開管理。 不同應用程式檢視器權限可在符合報表或儀表板其唯讀取用者的安全性需求時提供彈性。
- 現有群組是否可用來保護新的內容？ Azure Active Directory 及 Microsoft 365 群組都受到支援。 當與現有程序一致時，使用群組可讓權限管理比指派給個別使用者更容易。
- 是否有任何與外部來賓使用者相關的安全性考量？ 您可能需要與 Azure Active Directory 系統管理員及 Power BI 系統管理員合作，以設定[來賓使用者存取權](../admin/service-admin-azure-ad-b2b.md)。

> [!TIP]
> 請考量為特定商務活動或專案建立工作區。 您可能會想根據組織架構 (例如每個部門的工作區) 來為工作區建立架構，但這種方法經常會變得過於廣泛。

## <a name="determine-how-content-will-be-consumed"></a>判斷使用內容的方式

了解解決方案取用者對查看報表及儀表板的偏好會很有幫助。 問題包括：

- [Power BI 應用程式](../consumer/end-user-apps.md) (其中包含單一工作區中的報表和儀表板) 是將內容傳遞給取用者的最佳方式嗎？直接存取工作區對內容檢視器而言是否足夠？
- 某些報表及儀表板是否會內嵌在其他位置，例如 [Teams](../collaborate-share/service-embed-report-microsoft-teams.md)、[SharePoint Online](../collaborate-share/service-embed-report-spo.md)，或[安全的入口網站或網站](../collaborate-share/service-embed-secure.md)？
- 取用者會使用[行動裝置](../consumer/mobile/mobile-apps-for-mobile-devices.md)存取內容嗎？ 將報表傳遞至小型外型規格裝置的需求，將會影響部分[報表設計決策](../create-reports/desktop-create-phone-report.md)。

## <a name="decide-if-other-content-may-be-created"></a>決定是否可建立其他內容

有幾個關鍵決策可讓取用者建立新的內容，例如：

- 是否允許取用者從已發佈資料集建立新的報表？ 將資料集[權限](../connect-data/service-datasets-build-permissions.md)指派給使用者，即可啟用這項功能。
- 如果取用者想要自訂報表，其是否可[儲存報表的複本](../connect-data/service-datasets-copy-reports.md)並個人化，以符合其需求？

> [!CAUTION]
> 雖然 [儲存複本] 功能是一項不錯的功能，但當報表包含特定圖形或頁首/頁尾訊息時，應該謹慎使用。 由於標誌、圖示及文字訊息通常與品牌需求或法規合規性有關，因此請務必謹慎控制其傳遞與散佈的方式。 如果使用 [儲存複本]，但新作者仍然無法變更原始圖形或頁首/頁尾訊息，則可能會對實際產生報表的人員造成混淆。 這也可能減少品牌帶來的意義。

## <a name="evaluate-needs-for-premium-capacity"></a>評估 Premium 容量的需求

當工作區儲存在 [Premium 容量](../admin/service-premium-what-is.md)時，即可使用其他功能。 下列是將工作區儲存在 Premium 容量上可能有利的幾個原因：

- 內容可由不具 Power BI Pro 授權的取用者存取。
- 支援大型資料集。
- 支援更頻繁的資料重新整理。
- 支援使用資料流程的完整功能集。
- Enterprise 功能，包括部署管線與 XMLA 端點。
- 支援編頁報表 (啟用工作負載時)。

## <a name="determine-data-acquisition-method"></a>判斷資料取得方法

報表所需的資料可能會影響數個決策。 問題包括：

- 是否可使用現有的 Power BI [共用資料集](../connect-data/service-datasets-share.md)？或建立新 Power BI 資料集是否適用於此解決方案？
- 是否需要使用新資料或量值來增強現有的共用資料集，以符合其他需求？
- 哪一種[資料儲存模式](../transform-model/desktop-storage-mode.md)最適合？ 選項包括匯入、DirectQuery、複合或即時連線。
- 可使用[彙總](../transform-model/desktop-aggregations.md)來提升查詢效能嗎？
- 建立[資料流程](../transform-model/dataflows/dataflows-introduction-self-service.md)會很有用嗎？可用其作為多個資料集的來源嗎？
- 是否需要註冊新的[閘道資料來源](../connect-data/service-gateway-data-sources.md)？

## <a name="decide-where-original-content-will-be-stored"></a>決定儲存原始內容的位置

除了規劃目標部署目的地之外，也請務必規劃原始 (或來源) 內容的儲存位置，例如：

- 指定用來儲存原始 Power BI Desktop (.pbix) 檔案的核准位置。 在理想的情況下，此位置僅供編輯內容的人員使用。 其安全性應該與 Power BI 服務中設定的方式一致。
- 使用原始 Power BI Desktop 檔案位置，檔案包含版本設定歷程記錄或原始檔控制。 版本設定允許內容作者將其還原成先前的檔案版本(如有必要)。 商務用 OneDrive 或 SharePoint 正適用於此用途。
- 指定用來儲存非集中式來源資料 (例如一般檔案或 Excel 檔案) 的核准位置。 其路徑可供任一資料集作者存取，且不會發生錯誤，並會定期備份。
- 針對從 Power BI 服務匯出的內容指定核准位置。 其目的在於確保 Power BI 服務中定義的安全性不會意外遭到規避。

> [!IMPORTANT]
> 當原始 Power BI Desktop 檔案包含匯入的資料時，指定受保護的位置尤其重要。

## <a name="assess-the-level-of-effort"></a>評估工作量

在取得足夠需求 (如 [第 1 階段](powerbi-migration-requirements.md)中所述) 及解決方案部署規劃程序的資訊後，即可立即評估工作量。 接著，您可運用工作、時間表及相關責任來制訂專案計劃。

> [!TIP]
> 人力成本 (薪資) 通常是大部分組織中最高昂的費用。 增強生產力雖然有著絕佳的投資報酬率 (ROI)，但卻很難加以精確預估。

## <a name="next-steps"></a>後續步驟

在[此 Power BI 移轉系列的下一篇文章](powerbi-migration-proof-of-concept.md)中了解第 3 階段，其涉及在移轉到 Power BI 時，進行概念證明以儘早降低風險及解決未知問題。

其他實用資源包括：

- [Microsoft BI 轉換](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [規劃 Power BI 企業部署白皮書](https://aka.ms/PBIEnterpriseDeploymentWP)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com/)

經驗豐富的 Power BI 合作夥伴可協助組織成功進行移轉程序。 若要與 Power BI 合作夥伴交流，請造訪 [Power BI 合作夥伴入口網站](https://powerbi.microsoft.com/partners/)。