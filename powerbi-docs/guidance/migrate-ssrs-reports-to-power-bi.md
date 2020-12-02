---
title: 將 SQL Server Reporting Services 報表移轉到 Power BI
description: 協助您將 SQL Server Reporting Services (SSRS) 報表遷移至 Power BI 的指導。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 01/03/2020
ms.openlocfilehash: f1b9b710c9f9e4ade80866026f728ddbe3ae6971
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96393178"
---
# <a name="migrate-sql-server-reporting-services-reports-to-power-bi"></a>將 SQL Server Reporting Services 報表移轉到 Power BI

本文適用於 SQL Server Reporting Services (SSRS) 報表作者和 Power BI 系統管理員。 其中提供指導，協助您將[報表定義語言 (RDL)](/sql/reporting-services/reports/report-definition-language-ssrs) 報表遷移至 Power BI。

> [!NOTE]
> 您只可以遷移 RDL 報表。 在 Power BI 中，RDL 報表稱為「編頁報表」  。

指導分為四個階段。 我們建議您先閱讀整篇文章，再遷移報表。

1. [開始之前](#before-you-start)
1. [移轉前階段](#pre-migration-stage)
1. [移轉階段](#migration-stage)
1. [移轉後階段](#post-migration-stage)

您可以在不需要停機的情況下，達成移轉至 SSRS 伺服器，或對報表使用者造成中斷。 請務必了解，不需要移除任何資料或報表。 因此，這表示您可以讓目前環境保持現狀，直到您準備好將其淘汰為止。

## <a name="before-you-start"></a>開始之前

開始移轉之前，您應該先確認您的環境符合特定必要條件。 我們將說明這些必要條件，也會向您介紹有用的移轉工具。

### <a name="preparing-for-migration"></a>準備進行移轉

當您準備將報表遷移至 Power BI 時，請先確認貴組織具有 [Power BI Premium](../admin/service-premium-what-is.md) 訂用帳戶。 需要有此訂用帳戶，才能裝載和執行 Power BI 編頁報表。

### <a name="supported-versions"></a>支援的版本

您可以遷移在內部部署執行，或在雲端提供者 (例如 Azure) 所裝載的虛擬機器上執行的 SSRS 執行個體。

下列清單說明支援遷移至 Power BI 的 SQL Server 版本：

> [!div class="checklist"]
> - SQL Server 2012
> - SQL Server 2014
> - SQL Server 2016
> - SQL Server 2017
> - SQL Server 2019

也可以從 Power BI 報表伺服器進行移轉。

### <a name="migration-tool"></a>移轉工具

建議您使用 [RDL 移轉工具](https://github.com/microsoft/RdlMigration)來協助準備和遷移報表。 此工具是由 Microsoft 所開發，可協助客戶將 RDL 報表從其 SSRS 伺服器遷移至 Power BI。 其可在 GitHub 上取得，其中記載移轉案例的端對端逐步解說。

此工具會將下列工作自動化：

* 檢查[不支援的資料來源](../paginated-reports/paginated-reports-data-sources.md)和[不支援的報表功能](../paginated-reports/paginated-reports-faq.md#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi)
* 將任何「共用」  資源轉換為「內嵌」  資源：
  * 共用 **資料來源** 成為內嵌資料來源
  * 共用 **資料集** 成為內嵌資料集
* 將報表 (通過檢查) 以編頁報表形式發佈至指定的 Power BI 工作區 (在 Premium 容量上)

其不會修改或移除現有的報表。 完成時，此工具會輸出所有已完成動作 (成功或失敗) 的摘要。

經過一段時間後，Microsoft 可能會改善此工具。 我們也鼓勵社群參與和協助增強該工具。

## <a name="pre-migration-stage"></a>移轉前階段

確認貴組織符合必要條件之後，您就可以開始 _移轉前_ 階段。 這個階段有三個階段：

1. 探索
1. 評定
1. 準備

### <a name="discover"></a>探索

「探索」  階段的目標是要識別您現有的 SSRS 執行個體。 此程序牽涉到掃描網路，以識別貴組織中的所有 SQL Server 執行個體。

您可以使用 [Microsoft Assessment and Planning Toolkit](https://www.microsoft.com/download/details.aspx?id=7826)。 也稱為「MAP Toolkit」，其會探索並報告您的 SQL Server 執行個體、版本及已安裝的功能。 這是功能強大的清查、評量和報告工具，可簡化您的移轉規劃程序。

### <a name="assess"></a>評定

探索到 SSRS 執行個體後，「評定」  階段的目標是要了解任何無法遷移的 SSRS 報表 (或伺服器項目)。

只有 RDL 報表可以從您的 SSRS 伺服器遷移到 Power BI。 每個遷移的 RDL 報表都會變成 Power BI 編頁報表。

不過，下列 SSRS 項目類型無法遷移至 Power BI：

- 共用資料來源 <sup>1</sup>
- 共用資料集 <sup>1</sup>
- 資源，例如影像檔案
- KPI (SSRS 2016 或更新版本 - 僅限 Enterprise Edition)
- 行動報表 (SSRS 2016 或更新版本 - 僅限 Enterprise Edition)
- 報表模型 (已淘汰)
- 報表組件 (已淘汰)

<sup>1</sup> [RDL 移轉工具](https://github.com/microsoft/RdlMigration)會自動轉換共用資料來源和共用資料集 (假設其使用支援的資料來源)。

如果 RDL 報表依賴 [Power BI 編頁報表尚未支援](../paginated-reports/paginated-reports-faq.md#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi)的功能，您可以計劃將其重新開發為 [Power BI 報表](../consumer/end-user-reports.md)。 即使您的 RDL 報表可以遷移，我們還是建議您考慮將其現代化為 Power BI 報表 (若有意義的話)。

如果您的 RDL 報表需要從內部部署資料來源  擷取資料，其無法使用單一登入 (SSO)。 目前，從這些來源進行的所有資料擷取都會使用閘道資料來源使用者帳戶  的安全性內容來完成。 SQL Server Analysis Services (SSAS) 無法以每個使用者為基礎來強制執行資料列層級安全性 (RLS)。

一般而言，Power BI 編頁報表已針對 **列印** 或 **PDF 產生** 進行最佳化。 Power BI 報表已針對 **探索和互動** 進行最佳化。 如需詳細資訊，請參閱[何時使用 Power BI 中的編頁報表](report-paginated-or-power-bi.md)。

### <a name="prepare"></a>準備

「準備」  階段的目標牽涉到備妥一切。 其中涵蓋設定 Power BI 環境、規劃如何保護和發佈報表，以及重新開發不會遷移之 SSRS 項目的想法。

1. 確定已為您的 Power BI Premium 容量啟用[編頁報表工作負載](../admin/service-admin-premium-workloads.md#paginated-reports)，而且有足夠的記憶體。
1. 確認您報表[資料來源](../paginated-reports/paginated-reports-data-sources.md)的支援，並設定 [Power BI Gateway](../connect-data/service-gateway-onprem.md)，以允許與任何內部部署資料來源進行連線。
1. 熟悉 Power BI 安全性，並使用 [Power BI 工作區和工作區角色](../collaborate-share/service-new-workspaces.md)規劃[如何重現您的 SSRS 資料夾和權限](/sql/reporting-services/security/secure-folders)。
1. 熟悉 Power BI 共用，並透過發佈 [Power BI 應用程式](../collaborate-share/service-create-distribute-apps.md)來規劃散發內容的方式。
1. 請考慮使用[共用 Power BI 資料集](../connect-data/service-datasets-build-permissions.md)取代 SSRS 共用資料來源。
1. 使用 [Power BI Desktop](../fundamentals/desktop-what-is-desktop.md) 來開發行動裝置最佳化的報表，有可能使用 [Power KPI 自訂視覺效果](https://appsource.microsoft.com/product/power-bi-visuals/WA104381083?tab=Overview)取代您的 SSRS 行動報表和 KPI。
1. 重新評估您的報表中 **UserID** 內建欄位的使用方式。 如果您依賴 **UserID** 來保護報表資料，請了解其會針對編頁報表 (裝載於 Power BI 服務時)，傳回使用者主體名稱 (UPN)。 因此，內建欄位會傳回類似 _m.blythe&commat;adventureworks.com_ 的內容，而不是傳回 NT 帳戶名稱，例如 _AW\mblythe_。 您將需要修改資料集定義，也可能需要修改來源資料。 修改並發佈之後，建議您徹底測試報表，以確定資料權限如預期般運作。
1. 重新評估您的報表中 **ExecutionTime** 內建欄位的使用方式。 針對編頁報表 (裝載於 Power BI 服務時)，內建欄位會以國際標準時間 (或 UTC)  傳回日期/時間。 它可能會影響報表參數的預設值，以及報表的執行時間標籤 (通常會加入至報表頁尾)。
1. 如果您的資料來源是 SQL Server (內部部署)，請確認報表並未使用地圖視覺效果。 地圖視覺效果取決於空間資料類型，而這些不受閘道支援。 如需詳細資訊，請參閱[編頁報表的資料擷取指引 (SQL Server 複雜資料類型)](report-paginated-data-retrieval.md#sql-server-complex-data-types)。
1. 請確定您的報表作者已安裝 [Power BI 報表產生器](../paginated-reports/report-builder-power-bi.md)，而且可在貴組織內輕鬆地散發之後的版本。

## <a name="migration-stage"></a>移轉階段

備妥 Power BI 環境和報表之後，您就可以開始進行「移轉」  階段。

移轉選項有兩個：「手動」  和「自動化」  。 手動移轉適用於少數報表，或需要在移轉前修改的報表。 自動化移轉適用於大量報表的移轉。

### <a name="manual-migration"></a>手動移轉

任何有權存取 SSRS 執行個體和 Power BI 工作區的人，都可以手動將報表遷移至 Power BI。 以下是要遵循的步驟：

1. 開啟 SSRS 入口網站，其中包含您想要遷移的報表。
1. 下載每個報表定義並將 .rdl 檔案儲存在本機。
1. 開啟「最新版」的  Power BI 報表產生器，然後使用您的 Azure AD 認證連線到 Power BI 服務。
1. 在 Power BI 報表產生器中開啟每分報表，然後：
   1. 確認所有資料來源和資料集都內嵌在報表定義中，而且是[支援的資料來源](../paginated-reports/paginated-reports-data-sources.md)。
   1. 預覽報表以確保其正確轉譯。
   1. 選擇 [另存新檔]  選項，然後選取 [Power BI 服務]  。
   1. 選取將包含報表的工作區。
   1. 確認報表是否順利儲存。 如果您的報表設計尚不支援某些功能，儲存動作將會失敗。 您將會收到原因的通知。 接著，您必須修改報表設計，然後再次嘗試儲存。

### <a name="automated-migration"></a>自動移轉

自動化移轉有兩個選項。 您可以使用：

- RDL 移轉工具
- 適用於 SSRS 和 Power BI 的公開可用 API

本文已說明 [RDL 移轉工具](#migration-tool)。

您也可以使用公開可用的 SSRS 和 Power BI API 來自動化內容的移轉。 雖然 RDL 移轉工具已經使用這些 API，但您可以開發符合您的確切需求的自訂工具。

如需 API 的詳細資訊，請參閱：

- [Power BI REST API 參考](../developer/automation/rest-api-reference.md)
- [SQL Server Reporting Services REST API](/sql/reporting-services/developer/rest-api)

## <a name="post-migration-stage"></a>移轉後階段

成功完成移轉之後，您就可以開始進行 _移轉後_ 階段。 這個階段牽涉到執行一系列的移轉後工作，以確保一切都正確且有效率地運作。

### <a name="configure-data-sources"></a>設定資料來源

將報表遷移至 Power BI 後，您必須確保其資料來源已正確設定。 其可能涉及指派給閘道資料來源，以及[安全地儲存資料來源認證](../paginated-reports/paginated-reports-data-sources.md#azure-sql-database-authentication)。 這些動作不是由 RDL 移轉工具完成。

### <a name="review-report-performance"></a>檢閱報表效能

我們強烈建議您完成下列動作，以確保可能達到最佳的報表使用者體驗：

1. 在 [Power BI 支援的每個瀏覽器](../fundamentals/power-bi-browsers.md)中測試報表，以確認報表正確轉譯。
1. 執行測試來比較 SSRS 和 Power BI 中的報表轉譯時間。 檢查 Power BI 報表會在可接受的時間內轉譯。
1. 如果 Power BI 報表因記憶體不足而無法轉譯，請將[額外的資源配置給 Power BI Premium 容量](../admin/service-admin-premium-workloads.md#paginated-reports)。
1. 對於長時間轉譯的報表，請考慮讓 Power BI 將其以[含報表附件的電子郵件訂閱](../consumer/paginated-reports-subscriptions.md)形式，傳遞給您的報表使用者。
1. 對於以 Power BI 資料集為依據的 Power BI 報表，請檢閱模型設計以確保其已完全最佳化。

### <a name="reconcile-issues"></a>協調問題

移轉後階段對於協調所有問題而言非常重要，而且可解決任何效能疑慮。 將編頁報表工作負載新增至容量，可能會致使下列項目的效能變慢：編頁報表和儲存在容量中的其他內容  。

如需這些問題的詳細資訊，包括了解和減輕這些問題的特定步驟，請參閱下列文章：

- [最佳化 Premium 容量](../admin/service-premium-capacity-optimize.md)
- [使用應用程式監視 Premium 容量](../admin/service-admin-premium-monitor-capacity.md)

## <a name="next-steps"></a>後續步驟

如需本文的詳細資訊，請參閱下列資源︰

- [什麼是 Power BI Premium 中的編頁報表？](../paginated-reports/paginated-reports-report-builder-power-bi.md)
- [編頁報表的資料擷取指引](report-paginated-data-retrieval.md)
- [何時使用 Power BI 中的編頁報表](report-paginated-or-power-bi.md)
- [Power BI 中的編頁報表：常見問題](../paginated-reports/paginated-reports-faq.md)
- [線上課程：一天內完成編頁報表](../learning-catalog/paginated-reports-online-course.md)
- [Power BI Premium 常見問題集](../admin/service-premium-faq.md)
- [RDL 移轉工具](https://github.com/microsoft/RdlMigration)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com)

Power BI 合作夥伴可協助貴組織成功進行遷移程序。 若要與 Power BI 合作夥伴交流，請造訪 [Power BI 合作夥伴入口網站](https://powerbi.microsoft.com/partners/)。
