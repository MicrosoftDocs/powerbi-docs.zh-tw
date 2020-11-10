---
title: 建立內容以移轉到 Power BI
description: 在移轉至 Power BI 時建立與驗證內容的指導方針。
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/20/2020
ms.author: v-pemyer
ms.openlocfilehash: a12a320b061967e9201e3513e504277a9df586b4
ms.sourcegitcommit: 84e75a2cd92f4ba4e0c08ba296b981b79d6d0e82
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88803200"
---
# <a name="createcontenttomigratetopowerbi"></a>建立內容以移轉到 Power BI

本文描述 **第 4 階段** ，這與移轉到 Power BI 時建立與驗證內容相關。

:::image type="content" source="media/powerbi-migration-create-validate-content/migrate-to-powerbi-stage-4.png" alt-text="顯示 Power BI 移轉階段的影像。本文的重點在於第 4 階段。":::

> [!NOTE]
> 如需上圖的完整說明，請參閱 [Power BI 移轉概觀](powerbi-migration-overview.md)。

第 4 階段的重點是執行實際工作，以將概念證明 (POC) 轉換為可供生產環境使用的解決方案。

此階段會產出一個已在開發工作區中經過驗證、並已準備好部署到生產的 Power BI 解決方案。

> [!TIP]
> 本文中討論的大部分主題也適用於標準 Power BI 實作專案。

## <a name="create-the-production-solution"></a>建立生產解決方案

此時，要供生產環境使用的 Power BI 解決方案，可由執行 POC 的同一人員繼續製作， 也可改由不同的人員接手。 只要不會延誤時程，則更建議讓未來負責 Power BI 開發的人員參與。 如此一來，其即可主動學習。

> [!IMPORTANT]
> 盡可能重複使用 POC 中的大部分工作。

### <a name="develop-new-import-dataset"></a>開發新的匯入資料集

如果現有的 Power BI 資料集都不符合您的需求，或者無法加以增強來符合需求時，您可以選擇建立新的匯入資料集。

理想的情況是，從一開始就考慮將資料及報表的開發工作分離。 [將資料及報表分離](report-separate-from-model.md)將在不同人員負責資料模型化及報表時，有助於分離工作與權限。 這種方式可提供更具擴充性的方法，並鼓勵重複使用資料。

與開發匯入資料集相關的必要活動包括：

- 從一或多個資料來源 (可能是 Power BI 的資料流程) [取得資料](../connect-data/desktop-quickstart-connect-to-data.md)。
- [塑造、結合與準備](../connect-data/desktop-shape-and-combine-data.md)資料。
- 建立[資料集模型](../transform-model/desktop-modeling-view.md)，包括[日期資料表](../transform-model/desktop-date-tables.md)。
- 建立並確認 [模型關聯性](../transform-model/desktop-create-and-manage-relationships.md)。
- 定義[量值](../transform-model/desktop-measures.md)。
- 視需要設定[資料列層級安全性](../admin/service-admin-rls.md)。
- 設定同義字並[最佳化化 Q&A](../natural-language/q-and-a-best-practices.md)。
- 規劃擴充性、效能與並行，這可能會影響資料儲存模式決策，例如使用[複合模型](../transform-model/desktop-composite-models.md)或[彙總](../transform-model/desktop-aggregations.md)。

> [!TIP]
> 如果您有不同的開發/測試/生產環境，請考慮將資料來源[參數化](/power-query/power-query-query-parameters)。 這會讓部署 (如[第 5階段](powerbi-migration-deploy-support-monitor.md)中所述) 變得更容易。

### <a name="develop-new-reports-and-dashboards"></a>部署全新報表與儀表板

與 Power BI 報表或儀表板開發相關的必要活動包括：

- 決定對現有資料模型使用即時連線，或建立新的資料模型
- 建立新的資料模型時，決定模型資料表的 [資料儲存模式](../transform-model/desktop-storage-mode.md) (匯入、DirectQuery 或複合)。
- 決定最佳的資料視覺效果工具以符合需求：Power BI Desktop、Paginated Report Builder 或Excel。
- 決定[最佳的視覺效果，](../consumer/end-user-visual-type.md)以告訴報表其需要敘述的故事，以及處理報表需要回答的問題。
- 確保所有視覺效果都呈現清楚、簡潔及符合商務的術語。
- 解決互動性需求。
- 使用即時連線時，請新增[報表層級量值](../transform-model/desktop-tutorial-create-measures.md)。
- 在 Power BI 服務中建立[儀表板](../create-reports/service-dashboards.md)，特別是當取用者想要更輕鬆的監視重要計量時。

> [!NOTE]
> 在規劃或技術 POC 的早期階段中，會制定許多這類決策。

## <a name="validate-the-solution"></a>驗證解決方案

驗證 Power BI 解決方案，有四個的主要層面：

1. 資料精確度
2. 安全性
3. 功能
4. 效能

### <a name="validate-data-accuracy"></a>驗證資料精確度

在進行移轉時，您必須一次性確保新報表中資料符合舊版報表中所顯示的內容。 或在存有差異時，能夠解釋原因。 其比發現新解決方案解決了舊版解決方案中的錯誤更為常見。

於正在進行的資料驗證工作過程中，新的報表通常需要透過原始來源系統進行交叉檢查。 在理想的情況下，每次發佈報表變更時，都會以可重複的方式執行這項驗證。

### <a name="validate-security"></a>驗證安全性

在驗證安全性時，有兩個主要層面需要考量：

- 資料權限
- 存取資料集、報表及儀表板

在匯入資料集中，可藉由定義 [資料列層級列安全性](../admin/service-admin-rls.md) (RLS) 來套用資料權限。 當使用 DirectQuery 儲存模式 (可能會使用[單一登入](../connect-data/service-gateway-sso-overview.md)) 時，來源系統也可能會強制執行資料權限。

下列為授與 Power BI 內容存取權的主要方式：

- [工作區角色](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces) (適用於內容編輯器及檢視器)。
- 套用至已封裝工作區內容集的[應用程式權限](../collaborate-share/service-create-distribute-apps.md#publish-your-app) (適用於檢視器)。
- [共用](../collaborate-share/service-share-dashboards.md)個別報表或儀表板 (適用於檢視器)。

> [!TIP]
> 我們建議訓練內容作者，以了解如何有效管理安全性。 同時也請務必具備健全的測試、稽核與監視功能。

### <a name="validate-functionality"></a>驗證功能

現在到了再次檢查資料集詳細資料的時間，例如欄位名稱、格式設定、排序及預設摘要行為。 [交叉分析篩選器](../visuals/power-bi-visualization-slicers.md)、[向下切入](../consumer/end-user-drill.md)、[鑽研](../create-reports/desktop-drillthrough.md)、[運算式](../create-reports/desktop-conditional-format-visual-titles.md)、[按鈕](../create-reports/desktop-buttons.md)或[書籤](../create-reports/desktop-bookmarks.md)等互動式報表功能，都應經驗證。

在開發過程中，Power BI 解決方案應定期發佈至 Power BI 服務中的開發工作區。 並確認服務中的所有功能都如預期般運作，例如自訂視覺效果的呈現。 這也是執行進一步測試的好時機。 請測試[排程重新整理](../connect-data/refresh-scheduled-refresh.md)、[問與答](../consumer/end-user-q-and-a.md)，以及報表與儀表板在[行動裝置](../consumer/mobile/mobile-apps-for-mobile-devices.md)上的外觀。

### <a name="validate-performance"></a>驗證效能

Power BI 解決方案的效能對於取用者體驗至關重要。 大部分的報表皆應在 10 秒內呈現出視覺效果。 如果報表需要較長的時間載入，請暫停並重新考量可能造成延遲的原因。 除了 Power BI Desktop 之外，您也應該在 Power BI 服務中定期評估報表效能。

不合格的[DAX (資料分析運算式)](../transform-model/desktop-quickstart-learn-dax-basics.md)、不佳的資料集設計，或不理想的報表設計 (例如嘗試在單一頁面上呈現太多視覺效果)，會引發許多效能問題。 技術環境問題 (例如網路、多載的資料閘道，或 Premium 容量的設定方式) 也會導致效能問題。 如需詳細資訊，請參閱 [Power BI 最佳化指南](power-bi-optimization.md)及[針對 Power BI 報表效能進行疑難排解](report-performance-troubleshoot.md)。

## <a name="document-the-solution"></a>記錄解決方案

有兩種主要的文件類型適用於 Power BI 解決方案：

- 資料集文件
- 報表文件

文件可儲存在最容易由目標對象存取的地方。 常用選項包含：

- **在 SharePoint 網站上：** SharePoint 網站可能存在於卓越中心或內部 Power BI 的社群網站。
- **在應用程式內：** 將 URL 發佈至 Power BI 應用程式前，可能會先行設定，以將取用者導向至詳細資訊。
- **在個別 Power BI Desktop 檔案內：** 資料表及資料行等的模型項目可定義描述。 撰寫報表時，這些描述會在 [欄位] 窗格中顯示為工具提示。

> [!TIP]
> 如果要建立網站來作為 Power BI 相關文件的中樞，請考量[自訂 [取得說明] 功能表](../admin/service-admin-portal.md#publish-get-help-information)及其 URL 位置。

### <a name="create-dataset-documentation"></a>建立資料集文件

資料集文件特別適用於會在未來管理資料集的使用者。 若此文件包含下列項目，將十分有用：

- 所制定的設計決策及原因。
- 誰擁有、維護及認證資料集。
- 資料重新整理需求。
- 在資料集中定義的自訂商務規則。
- 特定的資料集安全性或資料隱私權需求。
- 未來的維護需求。
- 已知開啟問題或延遲的待辦項目。

您也可以選擇建立變更記錄檔，以摘要說明資料集在一段時間內所發生的最重要變更。

### <a name="create-report-documentation"></a>建立報表文件

報表文件 (通常是適用於報表取用者的逐步解說) 可協助取用者讓報表及儀表板發揮更大的價值。 簡短的影片教學課程通常也十分有效。

您也可以選擇在報表的隱藏頁面上包含其他報表文件。 其中可包含設計決策及變更記錄檔。

## <a name="next-steps"></a>後續步驟

在[此 Power BI 移轉系列的下一篇文章](powerbi-migration-deploy-support-monitor.md)中了解第 5 階段，其涉及在移轉到 Power BI 時，部署、支援並監視內容。

其他實用資源包括：

- [Microsoft BI 轉換](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [規劃 Power BI 企業部署白皮書](https://aka.ms/PBIEnterpriseDeploymentWP)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com/)

經驗豐富的 Power BI 合作夥伴可協助組織成功進行移轉程序。 若要與 Power BI 合作夥伴交流，請造訪 [Power BI 合作夥伴入口網站](https://powerbi.microsoft.com/partners/)。
