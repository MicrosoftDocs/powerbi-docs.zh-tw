---
title: 使用 Power BI 連接到帶狀線
description: Stripe for Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 6a194a4d56f4a940ad892ccd2f9097dd782f49d3
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "61167679"
---
# <a name="connect-to-stripe-with-power-bi"></a>使用 Power BI 連接到帶狀線
您可以在 Power BI 中，使用 Power BI 內容套件來視覺化及瀏覽 Stripe 資料。 Power BI 的 Stripe 內容套件會提取有關您的客戶、費用、事件和發票的資料。 這些資料包括過去 30 天的最近一萬個事件和五千筆費用。 此內容會依您控制的排程每天自動重新整理一次。 

連接到 [Power BI 的 Stripe 內容套件](https://app.powerbi.com/getdata/services/stripe)。

## <a name="how-to-connect"></a>如何連接
1. 選取左瀏覽窗格底部的 [取得資料]。  
   
    ![](media/service-connect-to-stripe/getdata.png)
2. 在 [服務]  方塊中，選取 [取得]  。  
   
    ![](media/service-connect-to-stripe/services.png)  
3. 選取 [Stripe]  &gt; [取得]  。  
   
    ![](media/service-connect-to-stripe/stripe.png)  
4. 提供要連接的 Stripe [API 金鑰](https://dashboard.stripe.com/account/apikeys)。  
   
    ![](media/service-connect-to-stripe/creds.png)
5. 匯入程序會自動開始。 完成時，新的儀表板、報表和模型會出現在瀏覽窗格中，並以星號標示。 選取儀表板以檢視匯入的資料。
   
    ![](media/service-connect-to-stripe/dashboard.png)

**接下來呢？**

* 請嘗試在儀表板頂端的[問與答方塊中提問](consumer/end-user-q-and-a.md)
* [變更儀表板中的圖格](service-dashboard-edit-tile.md)。
* [選取圖格](consumer/end-user-tiles.md)，開啟基礎報表。
* 雖然資料集排程為每天重新整理，但是您可以變更重新整理排程，或使用 [立即重新整理]  視需要嘗試重新整理

## <a name="next-steps"></a>後續步驟
[Power BI 是什麼？](power-bi-overview.md)

[取得 Power BI 的資料](service-get-data.md)

