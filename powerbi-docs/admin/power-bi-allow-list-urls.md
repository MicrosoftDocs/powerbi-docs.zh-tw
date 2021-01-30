---
title: 將 Power BI URL 新增至允許清單
description: 此文章列出要新增至允許清單以連線到 Power BI 的 URL 端點和連接埠。
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 06/25/2020
ms.custom: seodec18
ms.openlocfilehash: 1495400a59d8250f407a5f7415a550871501e4e3
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99098900"
---
# <a name="add-power-bi-urls-to-your-allow-list"></a>將 Power BI URL 新增至允許清單
[//]: # "suparnap、miwehnia 和 natham 是維護這份清單的連絡人"

Power BI 服務需要連線到網際網路。 此文章中表格所列的端點應該可供使用 Power BI 服務的客戶存取。

若要使用 Power BI 服務，您必須能夠連線到下列表格中標記為 **必要** 的端點，以及在連結的網站上標記為 **必要** 的所有端點。 若外部網站的連結是某個特定區域，您就只需要檢閱該區段中的端點。

標記為 **選擇性** 的端點，也可以新增至允許清單，讓特定功能得以運作。

Power BI 服務只需為列出的端點開啟 TCP 連接埠 443。

萬用字元 (*) 代表根網域下的所有層級，而當資訊無法使用時，會以 N/A 表示。 [目的地] 欄會列出網域名稱及外部網站的連結，其中包含更詳細的端點資訊。

>[!Important]
>下列表格中的資訊不適用於 Power BI Germany、由 21Vianet 運作的 Power BI China 或 Power BI for US Government。 若要深入了解雲端服務之間的通訊，請參閱[連線政府和全球 Azure 雲端服務](service-govus-overview.md#connect-government-and-global-azure-cloud-services)。

## <a name="authentication"></a>驗證

Power BI 需要仰賴 Microsoft 365 驗證與身分識別區段中的必要端點。 若要使用 Power BI，必須要可以連線到以下所連結的網站中之端點。

| 資料列 | 目的 | 目的地 | 連接埠 |
| --- | --- | --- | --- |
| 1 | **必要：** 驗證及身分識別 | 請參閱 [Microsoft 365 Common 與 Office Online URL](/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) 文件  | N/A |

## <a name="general-site-usage"></a>一般網站使用方式

如需使用 Power BI 的一般用途，必須要可連線到以下所列資料表與連結網站中的端點。

| 資料列 | 目的 | 目的地 | 連接埠 |
| --- | --- | --- | --- |
| 1 | **必要：** 後端 API | api.powerbi.com | TCP 443 |
| 2 | **必要：** 後端 API | *.analysis.windows.net | TCP 443 |
| 3 | **必要：** 後端 API | *.pbidedicated.windows.net | TCP 443 |
| 4 | **必要：** 內容傳遞網路 (CDN) | content.powerapps.com | TCP 443 |
| 5 | **必要：** Microsoft 365 整合 | 請參閱 [Microsoft 365 Common 與 Office Online URL](/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) 文件 | N/A |
| 6 | **必要：** 入口網站 | *.powerbi.com | TCP 443 |
| 7 | **必要：** 服務遙測 | dc.services.visualstudio.com | TCP 443 |
| 8 | **選擇性：** 資訊訊息 | dynmsg.modpim.com | TCP 443 |
| 9 | **選擇性：** NPS 問卷 | nps.onyx.azure.net | TCP 443 |
| | | |

## <a name="administration"></a>系統管理

若要在 Power BI 中執行系統管理功能，必須要可連線到以下連結網站中的端點。

| 資料列 | 目的 | 目的地 | 連接埠 |
| --- | --- | --- | --- |
| 1 | **必要：** 供管理使用者及檢視稽核記錄檔 | 請參閱 [Microsoft 365 Common 與 Office Online URL](/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) 文件 | N/A |
| | | |

## <a name="getting-data"></a>取得資料

若要從例如 OneDrive 等特定資料來源取得資料，必須要能連線到下表中的端點。 組織中使用的特定資料來源可能需要存取其他網際網路網域和 URL。

| 資料列 | 目的 | 目的地 | 連接埠 |
| --- | --- | --- | --- |
| 1 | **必要：** AppSource (Power BI 中的內部或外部應用程式) | appsource.microsoft.com <br> *.s-microsoft.com  | TCP 443 |
| 2 | **選擇性：** 登入並取得內容套件的資料 | 取決於使用的內容套件 | 取決於使用的內容套件 |
| 3 | **選擇性：** 從「OneDrive 個人」匯入檔案 | 請參閱 [OneDrive 網站的必要 URL 與連接埠](/onedrive/required-urls-and-ports) | N/A |
| 4 | **選擇性：** 60 秒 Power BI 教學課程影片 | *.doubleclick.net <br> *.ggpht.com <br> *.google.com <br> *.googlevideo.com <br> *.youtube.com <br> *.ytimg.com <br> fonts.gstatic.com | TCP 443 |
| 5 | **選擇性：** PubNub 串流資料來源 | 請參閱 [PubNub 文件](https://support.pubnub.com/hc/en-us/categories/360004336832-PubNub-101) | N/A |
| | | |

## <a name="dashboard-and-report-integration"></a>儀表板與報表整合

Power BI 需要特定端點以支援您的儀表板與報表。 您必須可連線到以下所列資料表與連結網站中的端點。

| 資料列 | 目的 | 目的地 | 連接埠 |
| --- | --- | --- | --- |
| 1 | **必要：** Excel 整合 | 請參閱 [Microsoft 365 Common 與 Office Online URL](/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) 文件 | N/A |
| | | |

## <a name="power-bi-visuals"></a>Power BI 視覺效果

Power BI 仰賴特定端點以檢視及存取 Power BI 視覺效果。 您必須可連線到以下所列資料表與連結網站中的端點。

| 資料列 | 目的 | 目的地 | 連接埠 |
| --- | --- | --- | --- |
| 1 | **必要：** 從 Marketplace 介面或檔案匯入自訂視覺效果 | *.azureedge.net <br> *.blob.core.windows.net <br> *.osi.office.net <br> *.msecnd.net <br> store.office.com <br> web.vortex.data.microsoft.com <br> store-images.s-microsoft.com | TCP 443 |
| 2 | **選擇性：** Bing 地圖服務 | bing.com <br> platform.bing.com <br> *.virtualearth.net | TCP 443 |
| 3 | **選擇性：** PowerApps | 請參閱 PowerApps 系統需求網站的[必要服務區段](/powerapps/maker/canvas-apps/limits-and-config#required-services) | N/A |
| 4 | **選擇性：** Visio | 請參閱 [Microsoft 365 Common 與 Office Online URL](/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online) 的文件，以及 [SharePoint Online 和商務用 OneDrive](/office365/enterprise/urls-and-ip-address-ranges#sharepoint-online-and-onedrive-for-business) 文件 | N/A |
| | | |

## <a name="related-external-sites"></a>相關的外部網站

Power BI 連結至其他相關網站。 這些網站會裝載文件、支援、新功能要求等。 存取這些網站將不會影響 Power BI 的功能，因此可自由選擇是否要新增至允許清單。

| 資料列 | 目的 | 目的地 | 連接埠 |
| --- | --- | --- | --- |
| 1 | **選擇性：** 社群網站 | community.powerbi.com <br> oxcrx34285.i.lithium.com | TCP 443 |
| 2 | **選擇性：** 文件網站 | docs.microsoft.com <br> img-prod-cms-rt-microsoft-com.akamaized.net <br> statics-uhf-eas.akamaized.net <br> cdnssl.clicktale.net <br> ing-district.clicktale.net | TCP 443 |
| 3 | **選擇性：** 下載網站 (適用於 Power BI Desktop 等) | download.microsoft.com | TCP 443 |
| 4 | **選擇性：** 外部重新導向 | aka.ms <br> go.microsoft.com | TCP 443 |
| 5 | **選擇性：** Ideas 意見反應網站| ideas.powerbi.com <br> powerbi.uservoice.com | TCP 443 |
| 6 | **選擇性：** Power BI 網站，包含登陸頁面、深入了解連結、支援網站、下載連結、合作夥伴展示工具等。 | powerbi.microsoft.com | TCP 443 |
| 7 | **選擇性：** Power BI 開發人員中心 | dev.powerbi.com | TCP 443 |
| 8 | **選擇性：** 支援網站 | support.powerbi.com <br> s3.amazonaws.com <br> *.olark.com <br> logx.optimizely.com <br> mscom.demdex.net <br> tags.tiqcdn.com | TCP 443 |
| | | |
