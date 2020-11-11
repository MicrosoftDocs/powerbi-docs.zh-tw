---
title: 部署到 Power BI
description: 在移轉到 Power BI 時，關於部署、支援及監視內容的指導方針。
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/20/2020
ms.author: v-pemyer
ms.openlocfilehash: 3e0bb00042b869061b7cb7cebf624e324db7e916
ms.sourcegitcommit: 37bd34053557089c4fbf0e05f78e959609966561
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94396119"
---
# <a name="deploy-to-power-bi"></a>部署到 Power BI

本文說明 **階段 5** ，這與移轉到 Power BI 時部署、支援及監視內容相關。

:::image type="content" source="media/powerbi-migration-deploy-support-monitor/migrate-to-powerbi-stage-5.png" alt-text="顯示 Power BI 移轉階段的影像。本文的重點在於階段 5。":::

> [!NOTE]
> 如需上圖的完整說明，請參閱 [Power BI 移轉概觀](powerbi-migration-overview.md)。

階段 5 的主要焦點在於將新的 Power BI 解決方案部署到實際執行。

此階段的輸出是已準備好供企業使用的實際執行解決方案。 當使用敏捷方法運作時，可以規劃一些要在未來重複項目中提供的增強功能。 支援及監視在此階段也很重要，而且要持續進行。

> [!TIP]
> 以下將討論除了以平行方式執行及解除舊版報表以外，本文討論的主題也適合標準 Power BI 的實作專案。

## <a name="deploy-to-test-environment"></a>部署至測試環境

對於 IT 管理的解決方案，或是對商務生產力很重要的解決方案，通常會有測試環境。 測試環境介於開發與實際執行之間，而且並非所有 Power BI 解決方案都需要。 測試工作區可作為穩定的位置 (與開發分隔)，以便在發行至實際執行之前，進行使用者接受度測試 (UAT)。

若您的內容已發佈至 Premium 容量上的工作區，[部署管線](../create-reports/deployment-pipelines-overview.md)可以簡化開發、測試與實際執行工作區的部署程序。 或者，您也可以手動或使用 [PowerShell 指令碼](https://powerbi.microsoft.com/blog/duplicating-workspaces-by-using-power-bi-cmdlets/)進行發佈。

### <a name="deploy-to-test-workspace"></a>部署至測試工作區

部署至測試工作區期間的關鍵活動通常包括：

- **連接字串與參數：** 若開發與測試之間的資料來源不同，請調整資料集連接字串。 [參數化](../connect-data/service-parameters.md)可用於有效地管理連接字串。
- **工作區內容：** 將資料集與報表發佈至測試工作區，並建立儀表板。
- **應用程式。** 若測試工作區中的內容會形成 UAT 流程的一部分，則使用該內容發佈[應用程式](../consumer/end-user-apps.md)。 應用程式權限通常僅限於涉及 UAT 的少數人員。
- **資料重新整理：** 針對 UAT 主動發生期間的所有匯入資料集， [排程資料集重新整理](../connect-data/refresh-scheduled-refresh.md)。
- **安全性：** 更新或確認 [工作區角色](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces)。 測試工作區存取包括涉及 UAT 的少數人員。

> [!NOTE]
> 如需部署至開發、測試與生產環境的選項等詳細資訊，請參閱[規劃 Power BI 企業部署白皮書](https://aka.ms/PBIEnterpriseDeploymentWP) (英文) 的第 9 節。

### <a name="conduct-user-acceptance-testing"></a>進行使用者接受度測試

一般來說，UAT 包含身為主題專家的商務使用者。 經過驗證之後，他們就能提供新內容精確、符合需求，以及可更廣為他人使用而部署的核准。

此 UAT 程序正式運作的範圍 (包括寫入的簽核)，將取決於您的變更管理實作。

## <a name="deploy-to-production-environment"></a>部署至實際執行環境

部署至實際執行環境時，有幾個考量。

### <a name="conduct-a-staged-deployment"></a>進行分段部署

若您嘗試將風險與使用者中斷降至最低，或是有其他考量，您可以選擇執行分段部署。 實際執行的第一次部署可能涉及較小的試驗使用者群組。 有了試驗，就可以主動向試驗使用者要求意見反應。

逐漸擴張實際執行工作區或應用程式中的權限，直到所有目標使用者都擁有新 Power BI 解決方案的權限。

> [!TIP]
> 使用 [Power BI 活動記錄](../admin/service-admin-auditing.md)，了解取用者採用及使用新 Power BI 解決方案的方式。

### <a name="handle-additional-components"></a>處理其他元件

在部署處理序期間，您可能需要與 Power BI 系統管理員合作，以解決支援整個解決方案所需的其他需求，例如：

- **閘道維護：** 可能需要在資料閘道上註冊 [新的資料來源](../connect-data/service-gateway-data-sources.md)。
- **閘道驅動程式與連接器：** 新的專屬資料來源可能需要在閘道叢集中的每部伺服器上，安裝新的驅動程式或自訂連接器。
- **建立新的 Premium 容量：** 您可能可以使用現有的 [Premium 容量](../admin/service-premium-capacity-manage.md)。 或者，當新的 Premium 容量需要批准時，可能會有某些情況。 若您刻意想要分隔部門工作負載，可能就會發生這種情況。
- **設定 Power BI 資料流程：** 資料準備活動可以使用 Power Query Online，在 [Power BI 資料流程](../transform-model/dataflows/dataflows-introduction-self-service.md)中一次設定。 其有助於避免在許多不同的 Power BI Desktop 檔案中，複寫資料準備工作。
- **註冊新的組織視覺效果：** 您可以在自訂視覺效果 (非源自 AppSource ) 的管理入口網站中，完成 [組織視覺效果](../developer/visuals/power-bi-custom-visuals-organization.md)註冊。
- **設定功能內容：** 租用戶設定會控制哪些人可以在 Power BI 服務首頁中使用 [功能內容](https://powerbi.microsoft.com/blog/promote-your-reports-dashboards-and-apps-on-power-bi-home/)。
- **設定敏感度標籤：** Microsoft 資訊保護已整合所有的 [敏感度標籤](../admin/service-security-data-protection-overview.md)。

### <a name="deploy-to-production-workspace"></a>部署至實際執行工作區

部署至實際執行工作區期間的關鍵活動通常包括：

- **變更管理：** 如有必要，請取得部署的核准，並使用您的標準變更管理實作，與使用者擴展的部署進行通訊。 在允許實際執行部署的期間，可能會有已核准的變更管理視窗。 其通常適用於 IT 管理的內容，且較不常套用至自助內容。
- **復原計畫：** 有了移轉，預期其為新解決方案的第一次移轉。 若內容已經存在，若有必要，最好將計畫還原成先前的版本。 擁有舊版的 Power BI Desktop 檔案 (使用 SharePoint 或 OneDrive 版本設定) 適用於此用途。
- **連接字串與參數：** 當測試與實際執行之間的資料來源不同，請調整資料集連接字串。 [參數化](../connect-data/service-parameters.md)可以有效地用於此用途。
- **資料重新整理：** 針對所有匯入的資料集， [排程資料集重新整理](../connect-data/refresh-scheduled-refresh.md)。
- **工作區內容：** 將資料集與報表發佈至實際執行工作區，並建立儀表板。 若您的內容已發佈至 Premium 容量上的工作區，[部署管線](../create-reports/deployment-pipelines-overview.md)可以簡化開發、測試與實際執行工作區的部署程序。
- **應用程式：** 若應用程式是內容散發策略的一部分，請使用實際執行工作區中的內容，發佈 [應用程式](../consumer/end-user-apps.md)。
- **安全性：** 根據您的內容散發與共同作業策略，更新及確認 [工作區角色](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces)。
- **資料集設定：** 更新及確認每個資料集的設定，包括：
  - [背書](../collaborate-share/service-endorse-content.md) (例如已認證或已升級)
  - 閘道連線或資料來源認證
  - 排程重新整理
  - [精選問與答問題](../create-reports/service-q-and-a-create-featured-questions.md)
- **報表與儀表板設定：** 更新及確認每份報表與資料集的設定。 最重要的設定包括：
  - 描述
  - 連絡人或連絡群組
  - [敏感度標籤](../admin/service-security-apply-data-sensitivity-labels.md)
  - [精選內容](https://powerbi.microsoft.com/blog/promote-your-reports-dashboards-and-apps-on-power-bi-home/)
- **訂用帳戶：** 視需要設定報表訂閱。

> [!IMPORTANT]
> 此時，您已獲致巨大進展。 在完成移轉的同時，慶祝您的成就。

### <a name="communicate-with-users"></a>與使用者進行通訊

向取用者宣告新的解決方案。 讓他們知道他們可以在何處找到內容，以及相關聯的文件、常見問題與教學課程。 若要引進新的內容，請考慮規劃邊午餐邊學習之類的課程，或準備一些隨選影片。

請務必包含如何要求協助，以及如何提供意見反應的指示。

### <a name="conduct-a-retrospective"></a>進行追溯

請考慮進行追溯，檢查移轉運作良好的內容，以及下一次移轉時可以做得更好的內容。

## <a name="run-in-parallel"></a>平行執行

在許多情況下，新的解決方案會在預先決定的時間，與舊版解決方案平行執行。 平行執行的優點包括：

- 降低風險，特別是當報表有其關鍵性的時候。
- 讓使用者有時間熟悉新 Power BI 解決方案。
- 讓 Power BI 中顯示的資訊能與舊版報表交互參照。

## <a name="decommission-the-legacy-report"></a>解除舊版報表

待時機恰當，移轉到 Power BI 的報表應於舊版 BI 平台停用。 當下列情況發生時，可能會解除舊版報表：

- 預先決定的平行執行時間 (其應已傳送到使用者擴展) 已到期。 一般是 30-90 天。
- 舊版系統的所有使用者都可以存取新的 Power BI 解決方案。
- 舊版報表不會再發生重要活動。
- 新 Power BI 解決方案未發生任何可能影響使用者生產力的問題。

## <a name="monitor-the-solution"></a>監視解決方案

來自 [Power BI 活動記錄](../admin/service-admin-auditing.md)的事件可用於了解新解決方案的使用模式 (或[執行記錄](/sql/reporting-services/report-server/report-server-executionlog-and-the-executionlog3-view)，含有部署至 Power BI 報表伺服器的內容)。 分析活動記錄有助於判斷實際使用是否不同於預期。 也可以驗證能否適當地支援解決方案。

以下是一些可透過評論活動記錄來解決的問題：

- 檢視該內容的頻率？
- 誰正在檢視該內容？
- 通常是透過應用程式或工作區來檢視該內容嗎？
- 大部分的使用者都使用瀏覽器或行動應用程式嗎？
- 是否使用訂閱？
- 是否有根據此解決方案而建立的新報表？
- 更新該內容的頻率？
- 如何定義安全性？
- 是否定期發生問題 (例如資料重新整理失敗)？
- 是否有特定活動發生 (例如，重要的匯出活動或許多個別的報表共用) 顯示出額外訓練的需要？

> [!IMPORTANT]
> 請務必讓有關人員定期檢視活動記錄。 僅是擷取出來並儲存歷程記錄，對稽核或合規性目的都有價值。 然而，能夠採取積極主動的作為時，才會有實際價值。

## <a name="support-the-solution"></a>支援解決方案

雖然移轉已完成，但移轉後期對於解決問題及處理任何效能考量而言非常重要。 經過一段時間，移轉的解決方案可能會隨著商務需求的發展而變更。

依組織之間管理自助 BI 的方式而定，支援往往會有些微差異。 整個商務單位的 Power BI 達人，通常會非正式地成為第一線支援。 雖然這是非正式的角色，但應該是要受到鼓勵的重要人員。

有了正式支援程序 (由具有支援票證的 IT 人員擔任)，對於處理系統導向的例行性要求與擴大目的也是不可或缺的。

您也可能擁有 [Center of Excellence (卓越中心) (COE)](center-of-excellence-establish.md)，其如同在組織中支援、教育及管理 Power BI 的內部顧問。 COE 可以負責在內部入口網站中，策劃實用的 Power BI 內容。

最後，內容取用者應該清楚知道在與內容相關的問題時，可以連絡誰，並提供問題或改進意見的機制。

## <a name="next-steps"></a>後續步驟

在[此系列的最後一篇文章](powerbi-migration-learn-from-customers.md)中，說明在移轉到 Power BI 時向客戶學習。

其他實用資源包括：

- [Microsoft BI 轉換](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [規劃 Power BI 企業部署白皮書](https://aka.ms/PBIEnterpriseDeploymentWP) (英文)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com/)

經驗豐富的 Power BI 合作夥伴可協助您的組織成功進行移轉程序。 若要與 Power BI 合作夥伴交流，請造訪 [Power BI 合作夥伴入口網站](https://powerbi.microsoft.com/partners/)。