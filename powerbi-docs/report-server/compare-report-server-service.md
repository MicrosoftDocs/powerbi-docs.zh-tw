---
title: 比較 Power BI 報表伺服器和 Power BI 服務
description: 本文會比較 Power BI 報表伺服器和 Power BI 服務的功能。
author: maggiesMSFT
ms.author: maggies
keywords: ''
ms.topic: overview
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.custom: mvc
ms.date: 07/28/2020
ms.openlocfilehash: 6d63e8825965a18d2ea5b6d56112c3a063c3456e
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418064"
---
# <a name="comparing-power-bi-report-server-and-the-power-bi-service"></a>比較 Power BI 報表伺服器和 Power BI 服務

Power BI 報表伺服器和 Power BI 服務有許多相似之處和一些主要差異。 下表將會逐一說明。

## <a name="features-of-power-bi-report-server-and-the-power-bi-service"></a>Power BI 報表伺服器和 Power BI 服務的功能

| 功能 | Power BI 報表伺服器 | Power BI 服務 | 備忘稿 |
|---------|---------|---------|---------|
| 部署 | 內部部署或雲端託管 | 雲端 | 如果透過 Power BI Premium 或具有軟體保證的 SQL Server Enterprise 進行授權，Power BI 報表伺服器可以部署在 Azure VM (雲端託管) 中|
| 來源資料 | 雲端及/或內部部署 | 雲端及/或內部部署 |  |
| 授權 | Power BI Premium 或包含軟體保證 (SA) 的 SQL Server | Power BI Pro 及/或 Power BI Premium | |  
| 生命週期 | 新式生命週期原則 | 完全受控的服務 |  |
| 發行週期 | 一年三次 (一月、五月、九月) | 每月一次 | 最新功能和修正首先會提供給 Power BI 服務。 在每個 Power BI 報表伺服器版本中，來自 Power BI Desktop 版本之服務的功能彙總套件；大部分其他功能只適用於 Power BI 服務。 |
| 在 Power BI Desktop 中建立 Power BI 報表 | 是 | 是 |  |
| 在瀏覽器中建立 Power BI 報表 | 否 | 是 |  |
| 裝載並連線至 Power BI 共用資料集 | 否 | 是 | [跨工作區的資料集簡介](../connect-data/service-datasets-across-workspaces.md) |
| 需要閘道 | 否 | 是 (針對內部部署資料來源) |  |
| 即時串流 | 否 | 是 | [Power BI 中的即時串流](../connect-data/service-real-time-streaming.md) |
| 儀表板 | 否 | 是 | [Power BI 服務中的儀表板](../consumer/end-user-dashboards.md) |
| 使用應用程式發佈群組的報表 | 否 | 是 | [使用儀表板和報表建立並發佈應用程式](../collaborate-share/service-create-distribute-apps.md) |
| 內容套件 | 否 | 是 | [組織內容套件：簡介](../collaborate-share/service-organizational-content-pack-introduction.md) |
| 連線到服務 (例如 Salesforce) | 是 | 是 | 在 Power BI 服務中，使用內容套件[連線至您所使用的服務](../connect-data/service-connect-to-services.md)。 在 Power BI 報表伺服器中，請使用經認證的連接器來連線至服務。 如需詳細資料，請參閱 [Power BI 報表伺服器中的 Power BI 報表資料來源](data-sources.md)。 |
| 問與答 | 否 | 是 | [Power BI 服務和 Power BI Desktop 中的問與答](../create-reports/power-bi-tutorial-q-and-a.md) 
| 深入資訊摘要 | 否 | 是 | [使用 Power BI 自動產生資料的見解](../consumer/end-user-insights.md) |
| 在 Excel 中進行分析 | 否 | 是 | [使用 Excel 分析](../collaborate-share/service-analyze-in-excel.md) 
| 編頁報表 | 是 | 是 | Premium 容量的預覽版中，[可於 Power BI 服務內使用編頁的報表](../paginated-reports/paginated-reports-report-builder-power-bi.md) |
| Power BI 行動應用程式 | 是 | 是 | [Power BI 行動裝置應用程式概觀](../consumer/mobile/mobile-apps-for-mobile-devices.md) |
| ARC GIS 地圖 | 否 | 是 | [Power BI 服務及 Power BI Desktop 中由 Esri 提供的 ArcGIS 地圖](../visuals/power-bi-visualizations-arcgis.md) |
| Power BI 報表的電子郵件訂用帳戶 | 否 | 是 | [為您自己或其他人訂閱](../collaborate-share/service-report-subscribe.md) Power BI 服務中的報表或儀表板 |
| 編頁報表的電子郵件訂用帳戶 | 是 | 是 | [為您自己和其他人訂閱 Power BI 服務中的編頁報表](../consumer/paginated-reports-subscriptions.md)<br><br>[Reporting Services 中的電子郵件傳遞](/sql/reporting-services/working-with-subscriptions-web-portal)  |
| 資料警示 | 否 | 是 | Power BI 服務中的[資料警示](../create-reports/service-set-data-alerts.md)
| 資料列層級安全性 (RLS) | 是 | 是 | DirectQuery (資料來源) 與匯入模式中皆可使用 <br><br>[Power BI 服務](../admin/service-admin-rls.md)中的資料列層級安全性 <br><br>[Power BI 報表伺服器](row-level-security-report-server.md)中的資料列層級安全性 |
| 多對多關聯性 | 否 | 是 | 在 Power BI Desktop 中[套用多對多關聯性](../transform-model/desktop-many-to-many-relationships.md) |
| 跨報表鑽研 | 否 | 是 | [使用跨報表鑽研](../create-reports/desktop-cross-report-drill-through.md) |
| 全螢幕模式 | 否 | 是 | [Power BI 服務](../consumer/end-user-focus.md)中的全螢幕模式 |
| 進階 Microsoft 365 共同作業 | 否 | 是 | 使用 Microsoft 365 [在工作區中共同作業](../collaborate-share/service-collaborate-power-bi-workspace.md) |
| R 指令碼和視覺效果 | 否 | 是 | 在 Power BI Desktop 中[建立 R 視覺效果](../create-reports/desktop-r-visuals.md)和執行 R 指令碼，並將其發佈至 Power BI 服務。 您無法將具有 R 指令碼或視覺效果的 Power BI 報表儲存至 Power BI 報表伺服器。  |
| Python 指令碼和視覺效果 | 否 | 是 | 在 Power BI Desktop 中[建立 Python 指令碼](../connect-data/desktop-python-scripts.md)和視覺效果，並將其發佈至 Power BI 服務。 您無法將具有 Python 指令碼或視覺效果的 Power BI 報表，儲存至 Power BI 報表伺服器。 |
| 預覽功能 | 否 | 是 | [選擇加入 Power BI 服務預覽](../consumer/end-user-preview-features.md)功能 |
| Power BI 視覺效果 | 是 | 是 | [Power BI 視覺效果](../developer/visuals/power-bi-custom-visuals.md) |
| 複合模型 | 否 | 是 |
| Power BI Desktop | 針對報表服務器進行了版本最佳化，可透過報表伺服器下載使用 | 針對 Power BI 服務進行了版本最佳化，可從 Windows 市集取得 | [適用於報表伺服器的 Power BI Desktop](https://powerbi.microsoft.com/report-server/) <br><br> [適用於 Power BI 服務的 Power BI Desktop](https://aka.ms/pbidesktopstore) |

## <a name="next-steps"></a>後續步驟

[安裝 Power BI 報表伺服器](install-report-server.md)