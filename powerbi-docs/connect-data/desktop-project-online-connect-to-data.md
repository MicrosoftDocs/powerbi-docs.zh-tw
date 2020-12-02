---
title: Project Online：透過 Power BI Desktop 連接到資料
description: Project Online：透過 Power BI Desktop 連接到資料
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 04/01/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: b6078a2122a77682af328f9935b23da0d0d0d945
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96404931"
---
# <a name="connect-to-project-online-data-through-power-bi-desktop"></a>透過 Power BI Desktop 連線到 Project Online 資料
您可以透過 Power BI Desktop 連接到 Project Online 中的資料。

## <a name="step-1-download-power-bi-desktop"></a>步驟 1：下載 Power BI Desktop
1. [下載 Power BI Desktop](https://go.microsoft.com/fwlink/?LinkID=521662)，然後執行安裝程式，在電腦上安裝 **Power BI Desktop**。

## <a name="step-2-connect-to-project-online-with-odata"></a>步驟 2：透過 OData 連接到 Project Online
1. 開啟 **Power BI Desktop**。
2. 在 [歡迎使用] 畫面上，選取 [取得資料]。
3. 選擇 [OData 摘要]，然後選取 [連接]。
4. 在 [URL] 方塊中，輸入您的 OData 摘要位址，然後按一下 [確定]。
   
   如果您的 Project Web App 網站位址類似 *https://\<tenantname\>.sharepoint.com/sites/pwa*，則您將針對 OData 摘要輸入的位址會是 *https://\<tenantname\>.sharepoint.com/sites/pwa/\_api/Projectdata*。
   
   在本例中，我們使用：

    `https://contoso.sharepoint.com/sites/pwa/default.aspx`

5. Power BI Desktop 會提示驗證公司或學校帳戶。 請選取組織帳戶，然後輸入您的認證。
   
   ![Power BI Desktop 的螢幕擷取畫面，其中顯示要連線的認證提示。](media/desktop-project-online-connect-to-data/image.png)

您用來連線到 OData 摘要的帳戶，至少必須有 Project Web App 網站的公事包檢視者存取權。 

從這裡，您可以選擇要連接的資料表並建立查詢。  要了解如何開始進行嗎？  以下部落格文章示範如何從 Project Online 資料建立燃盡圖。  該部落格文章使用 Power Query 連接到 Project Online，不過也適用於 Power BI Desktop。

[使用 Power Pivot 和 Power Query 為專案建立燃盡圖](https://blogs.office.com/2014/03/24/creating-burndown-charts-for-project-using-power-pivot-and-power-query/)

