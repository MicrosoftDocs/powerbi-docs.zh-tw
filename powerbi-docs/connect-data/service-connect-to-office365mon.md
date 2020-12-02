---
title: 使用 Power BI 連接到 Office365Mon
description: Office365Mon for Power BI
author: paulinbar
ms.author: painbar
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 11/26/2019
LocalizationGroup: Connect to services
ms.openlocfilehash: c7433bcc75da316e2e705a63dbcc2f17745ad573
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96403045"
---
# <a name="connect-to-office365mon-with-power-bi"></a>使用 Power BI 連接到 Office365Mon
使用 Power BI 與 Office365Mon 範本應用程式，輕鬆分析您 Office 365 的中斷問題與健康狀態效能資料。 Power BI 會擷取您的資料 (包括中斷與健康狀況探查)，然後根據該資料建置現成的儀表板與報表。

連線到 Power BI 適用的 [Office365Mon 範本應用程式](https://msit.powerbi.com/groups/me/getapps/services/office365mon.office365mon_powerbi_v3)。

>[!NOTE]
>Office365Mon 系統管理帳戶是連接及載入 Power BI 範本應用程式的必備項目。

## <a name="how-to-connect"></a>如何連接
1. 在導覽窗格的底部，選取 [取得資料]。
   
   ![[取得資料] 按鈕的螢幕擷取畫面，其中顯示該按鈕位於功能窗格中。](media/service-connect-to-office365mon/pbi_getdata.png)
2. 在 [服務]  方塊中，選取 [取得] 。
   
   ![[服務] 對話方塊的螢幕擷取畫面，其中顯示 [取得] 按鈕。](media/service-connect-to-office365mon/pbi_getservices.png) 
3. 選取 [Office365Mon] \> [取得]。
   
   ![[Office365Mon] 對話方塊的螢幕擷取畫面，其中顯示 [取得] 連結。](media/service-connect-to-office365mon/o365mon.png)
4. 針對 [驗證方法]，選取 [oAuth2] \> [登入]。
   
   出現提示時，輸入 Office365Mon 管理認證，並遵循驗證程序。
   
   ![[連接至 Office365Mon] 對話方塊的螢幕擷取畫面，其中顯示 [驗證方法] 欄位中的 OAuth2。](media/service-connect-to-office365mon/creds.png)
   
   ![Office365Mon 登入的螢幕擷取畫面，其中為認證的提示。](media/service-connect-to-office365mon/creds2.png)
5. Power BI 匯入資料之後，您會在導覽窗格中看到新的儀表板、報表和資料集。 新的項目會以黃色星號 \* 標示，選取 Office365Mon 項目。
   
   ![Power BI 中功能窗格的螢幕擷取畫面，其中顯示儀表板、報表與資料集。](media/service-connect-to-office365mon/dashboard4.png)

**接下來呢？**

* 請嘗試在儀表板頂端的[問與答方塊中提問](../consumer/end-user-q-and-a.md)
* [變更儀表板中的圖格](../create-reports/service-dashboard-edit-tile.md)。
* [選取圖格](../consumer/end-user-tiles.md)，開啟基礎報表。
* 雖然資料集排程為每天重新整理，但是您可以變更重新整理排程，或使用 [立即重新整理] 視需要嘗試重新整理

## <a name="troubleshooting"></a>疑難排解
如果您使用 Office365Mon 訂用帳戶認證登入之後收到 **「登入失敗」** 的錯誤，則您使用的帳戶沒有權限可從您的帳戶擷取 Office365Mon 訂用帳戶資料。 請確認它是系統管理員帳戶，然後重試一次。

## <a name="next-steps"></a>後續步驟
[Power BI 是什麼？](../fundamentals/power-bi-overview.md)

[取得 Power BI 的資料](service-get-data.md)
