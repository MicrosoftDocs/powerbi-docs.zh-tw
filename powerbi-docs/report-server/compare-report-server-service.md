---
title: 比較 Power BI 報表伺服器和 Power BI 服務
description: 本文會比較 Power BI 報表伺服器和 Power BI 服務的功能。
keywords: ''
author: maggiesMSFT
ms.author: maggies
ms.topic: overview
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.custom: mvc
ms.date: 12/03/2019
ms.openlocfilehash: 88df45a95e485695a9a2f36358c1fcca9670f258
ms.sourcegitcommit: e492895259aa39960063f9b337a144a60c20125a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74831125"
---
# <a name="comparing-power-bi-report-server-and-the-power-bi-service"></a>比較 Power BI 報表伺服器和 Power BI 服務

Power BI 報表伺服器和 Power BI 服務有許多相似之處和一些主要差異。 下表將會逐一說明。

## <a name="features-of-power-bi-report-server-and-the-power-bi-service"></a>Power BI 報表伺服器和 Power BI 服務的功能

| 功能 | Power BI 報表伺服器 | Power BI 服務 | 備忘稿 |
|---------|---------|---------|---------|
| 部署 | 內部部署或雲端託管 | 雲端 | 如果透過 Power BI Premium 授權，Power BI 報表伺服器可以部署在 Azure VM (雲端託管) 中 |
| 來源資料 | 雲端及/或內部部署 | 雲端及/或內部部署 |  |
| 授權 | Power BI Premium 或包含軟體保證 (SA) 的 SQL Server | Power BI Pro 及/或 Power BI Premium | |  
| 生命週期 | 新式生命週期原則 | 完全受控的服務 |  |
| 發行週期 | 一年三次 (一月、五月、九月) | 每月一次 | 最新功能和修正首先會提供給 Power BI 服務。 在接下來的幾個版本中，大部分的核心功能都會提供給 Power BI 報表伺服器，而某些功能僅適用於 Power BI 服務。 |
| 在 Power BI Desktop 中建立 Power BI 報表 | 是 | 是 |  |
| 在瀏覽器中建立 Power BI 報表 | 否 | 是 |  |
| 需要閘道 | 否 | 是 (針對內部部署資料來源) |  |
| 即時串流 | 否 | 是 | [Power BI 中的即時串流](../service-real-time-streaming.md) |
| 儀表板 | 否 | 是 | [Power BI 服務中的儀表板](../consumer/end-user-dashboards.md) |
| 使用應用程式發佈群組的報表 | 否 | 是 | [使用儀表板和報表建立並發佈應用程式](../service-create-distribute-apps.md) |
| 內容套件 | 否 | 是 | [組織內容套件：簡介](../service-organizational-content-pack-introduction.md) |
| 連線到服務 (例如 Salesforce) | 是 | 是 | 在 Power BI 服務中，使用內容套件[連線至您所使用的服務](../service-connect-to-services.md)。 在 Power BI 報表伺服器中，請使用經認證的連接器來連線至服務。 如需詳細資料，請參閱 [Power BI 報表伺服器中的 Power BI 報表資料來源](data-sources.md)。 |
| 問與答 | 否 | 是 | [Power BI 服務和 Power BI Desktop 中的問與答](../power-bi-tutorial-q-and-a.md) 
| 深入資訊摘要 | 否 | 是 | [使用 Power BI 自動產生資料的見解](../consumer/end-user-insights.md) |
| 在 Excel 中進行分析 | 否 | 是 | [使用 Excel 分析](../service-analyze-in-excel.md) 
| 編頁報表 | 是 | 是 | Premium 容量的預覽版中，[可於 Power BI 服務內使用編頁的報表](../paginated-reports-report-builder-power-bi.md) |
| Power BI 行動應用程式 | 是 | 是 | [Power BI 行動裝置應用程式概觀](../consumer/mobile/mobile-apps-for-mobile-devices.md) |
| ARC GIS 地圖 | 否 | 是 | [Power BI 服務及 Power BI Desktop 中由 Esri 提供的 ArcGIS 地圖](../visuals/power-bi-visualization-arcgis.md) |
| Power BI 報表的電子郵件訂用帳戶 | 否 | 是 | [為您自己或其他人訂閱](../service-report-subscribe.md) Power BI 服務中的報表或儀表板 |
| 編頁報表的電子郵件訂用帳戶 | 是 | 是 | [為您自己和其他人訂閱 Power BI 服務中的編頁報表](../consumer/paginated-reports-subscriptions.md)<br><br>[Reporting Services 中的電子郵件傳遞](https://docs.microsoft.com/sql/reporting-services/subscriptions/e-mail-delivery-in-reporting-services)  |
| 資料警示 | 否 | 是 | Power BI 服務中的[資料警示](../service-set-data-alerts.md)
| 資料列層級安全性 (RLS) | 是 | 是 | DirectQuery (資料來源) 與匯入模式中皆可使用 <br><br>[Power BI 服務](../service-admin-rls.md)中的資料列層級安全性 <br><br>[Power BI 報表伺服器](row-level-security-report-server.md)中的資料列層級安全性 |
| 全螢幕模式 | 否 | 是 | [Power BI 服務](../consumer/end-user-focus.md)中的全螢幕模式 |
| 進階的 Office 365 共同作業 | 否 | 是 | 搭配 Office 365 [在工作區中共同作業](../service-collaborate-power-bi-workspace.md) |
| R 視覺效果 | 否 | 是 | 在 Power BI Desktop 中[建立 R 視覺效果](../desktop-r-visuals.md)，並將其發佈至 Power BI 服務。 您無法將具有 R 視覺效果的 Power BI 報表，儲存至 Power BI 報表伺服器。  |
| 預覽功能 | 否 | 是 | [選擇加入 Power BI 服務預覽](../consumer/end-user-preview-features.md)功能 |
| 自訂視覺效果 | 是 | 是 | [Power BI 的自訂視覺效果](../developer/power-bi-custom-visuals.md) |
| 複合模型 | 否 | 是 |
| Power BI Desktop | 針對報表服務器進行了版本最佳化，可透過報表伺服器下載使用 | 針對 Power BI 服務進行了版本最佳化，可從 Windows 市集取得 | [適用於報表伺服器的 Power BI Desktop](https://powerbi.microsoft.com/report-server/) <br><br> [適用於 Power BI 服務的 Power BI Desktop](https://aka.ms/pbidesktopstore) |

## <a name="next-steps"></a>後續步驟

[安裝 Power BI 報表伺服器](install-report-server.md)
