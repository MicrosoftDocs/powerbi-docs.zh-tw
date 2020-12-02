---
title: 使用 Power BI 連接到 Salesforce
description: Salesforce for Power BI
author: paulinbar
ms.author: painbar
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 05/30/2019
LocalizationGroup: Connect to services
ms.openlocfilehash: f43d60a22d436cc0be5aa57bc9b383d535dbfc0d
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96392879"
---
# <a name="connect-to-salesforce-with-power-bi"></a>使用 Power BI 連接到 Salesforce
您可以使用 Power BI 輕鬆地連接到您的 Salesforce.com 帳戶。 有了此連線，您就可以擷取 Salesforce 資料，並自動提供儀表板和報表。

深入了解 Power BI 的 [Salesforce 整合](https://powerbi.microsoft.com/integrations/salesforce)。

## <a name="how-to-connect"></a>如何連接
1. 在 Power BI 中，選取導覽窗格底端的 [取得資料]。
   
   ![[取得資料] 按鈕的螢幕擷取畫面，其中顯示該按鈕位於功能窗格中。](media/service-connect-to-salesforce/pbi_getdata.png) 
2. 在 [服務]  方塊中，選取 [取得] 。
   
   ![[服務] 對話方塊的螢幕擷取畫面，其中顯示 [取得] 按鈕。](media/service-connect-to-salesforce/pbi_getservices.png) 
3. 選取 [適用於 Salesforce 的分析]，然後選取 [取得]。  
   
   ![[適用於 Salesforce 的分析] 對話方塊的螢幕擷取畫面，其中顯示 [立即取得] 連結。](media/service-connect-to-salesforce/salesforce.png)
4. 選取 [登入] 啟動登入流程。
   
    ![[連線到 Salesforce] 對話方塊的螢幕擷取畫面，其中顯示 [登入] 按鈕。](media/service-connect-to-salesforce/dialog.png)
5. 出現提示時，請輸入您的 Salesforce 認證。 選取 [允許] 並讓 Power BI 存取您的基本 Salesforce 資訊和資料。
   
   ![Salesforce 認證的螢幕擷取畫面，其中顯示 Power B I 正在要求存取資訊。](media/service-connect-to-salesforce/sf_authorize.png)
6. 使用下拉式選項，設定您要匯入 Power BI 的內容：
   
   * **儀表板**
     
     以角色來選取預先定義的儀表板 (例如 **銷售經理**)。 這些儀表板會擷取一組特定的 Salesforce 標準資料，其中不包含自訂欄位。
     
     ![Salesforce 儀表板的螢幕擷取畫面，其中顯示以角色來選取預先定義儀表板的選項。](media/service-connect-to-salesforce/pbi_salesforcechooserole.png)
   * **報表**
     
     從您的 Salesforce 帳戶選取一個或多個自訂報表。 這些報表會比對您在 Salesforce 中的檢視，且可包含自訂欄位或物件中的資料。
     
     ![Salesforce 報表的螢幕擷取畫面，其中顯示自訂報表清單。](media/service-connect-to-salesforce/pbi_salesforcereports.png)
     
     如果您沒有看到任何報表，請在您的 Salesforce 帳戶中加入或建立報表，然後再試著連接一次。

7. 選取 [連接] 開始匯入程序。 您會在匯入期間看到顯示匯入正在進行中的通知。 匯入完成後，您會看到導覽窗格中列出您 Salesforce 資料的儀表板、報表和資料集。
   
   ![銷售經理儀表板的螢幕擷取畫面，其中顯示儀表板、報表和資料集。](media/service-connect-to-salesforce/pbi_getdatasalesforcedash.png)

您可以變更此儀表板，以您想要的任何方式來顯示資料。 您可以透過問與答提問，或[選取磚](../consumer/end-user-tiles.md)開啟基礎報表，然後[編輯或移除儀表板磚](../create-reports/service-dashboard-edit-tile.md)。

**接下來呢？**

* 請嘗試在儀表板頂端的[問與答方塊中提問](../consumer/end-user-q-and-a.md)
* 在儀表板中[編輯或移除磚](../create-reports/service-dashboard-edit-tile.md)
* [選取圖格](../create-reports/service-dashboard-tiles.md)，開啟基礎報表
* 雖然資料集排程為每天重新整理，但您可以變更重新整理排程，或使用 [立即重新整理] 視需要嘗試重新整理

## <a name="system-requirements-and-considerations"></a>系統需求和考量

- 與已啟用 API 存取的 Salesforce 生產帳戶連接

- 登入期間獲授 Power BI 應用程式的權限

- 帳戶有足夠可用的 API 呼叫，以便提取和重新整理資料

- 進行重新整理所需的有效驗證權杖。 Salesforce 有每個應用程式最多五個驗證權杖的上限，因此請確認您匯入的資料集為五個以下。

- Salesforce Reports API 有支援最多 2000 個資料列的限制。


## <a name="troubleshooting"></a>疑難排解

如發生任何錯誤，請檢閱上述需求。 

目前不支援登入自訂或沙箱網域。

### <a name="unable-to-connect-to-the-remote-server-message"></a>「無法連線到遠端伺服器」訊息

若您在嘗試連線到 Salesforce 帳戶時收到「無法連線到遠端伺服器」的訊息，請參閱下列論壇上的這個解決方法：[Salesforce Connector sign in Error Message:Unable to connect to the remote server](https://www.outsystems.com/forums/Forum_TopicView.aspx?TopicId=17674&TopicName=log-in-error-message-unable-to-connect-to-the-remote-server&) (Salesforce 連接器登入錯誤訊息：無法連線到遠端伺服器)


## <a name="next-steps"></a>後續步驟
[Power BI 是什麼？](../fundamentals/power-bi-overview.md)

[Power BI 服務的資料來源](service-get-data.md)
