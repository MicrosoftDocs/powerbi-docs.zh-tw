---
title: 教學課程：使用 Power BI 連線到 GitHub 存放庫
description: 在本教學課程中，您使用 Power BI 連線至 GitHub 服務中的實際資料，而且 Power BI 會自動建立儀表板和報表。
author: maggiesMSFT
ms.reviewer: SarinaJoan
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 10/30/2020
ms.author: maggies
LocalizationGroup: Connect to services
ms.openlocfilehash: 805b7805d932468e973805d9496a5b25d4391fdd
ms.sourcegitcommit: 8861dac6724202a5b3be456a6aff8f3584e0cccf
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2020
ms.locfileid: "93132612"
---
# <a name="tutorial-connect-to-a-github-repo-with-power-bi"></a>教學課程：使用 Power BI 連線到 GitHub 存放庫
在本教學課程中，您會連線到實際的資料：GitHub 服務中的 Power BI 內容公用存放庫 (也稱為「存放庫」)。 Power BI 會自動建立具有資料的儀表板和報表。 您會看到如下問題的答案：Power BI 公用存放庫的參與人數有多少？ 誰參與最多？ 哪個星期幾的參與最多？ 以及其他問題。 

您也可以連線到自己的私人或公用 GitHub 存放庫。 [使用 Power BI 連線到 GitHub](service-connect-to-github.md) 一文說明如何使用 Power BI 的「範本應用程式」連線到存放庫。

![Power BI 中的 GitHub 報表](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-punch-card.png)

在本教學課程中，您會完成下列步驟：

> [!div class="checklist"]
> * 在尚未有 GitHub 帳戶時，註冊一個帳戶 
> * 登入 Power BI 帳戶，或在尚未有 Power BI 帳戶時，註冊一個帳戶
> * 開啟 Power BI 服務
> * 尋找 GitHub 應用程式
> * 輸入 Power BI 公用 GitHub 存放庫的資訊
> * 使用 GitHub 資料檢視儀表板和報表
> * 刪除應用程式以清除資源

如果您尚未註冊 Power BI，請先進行[免費註冊](https://app.powerbi.com/signupredirect?pbi_source=web)再開始。

## <a name="prerequisites"></a>必要條件

若要完成本教學課程，您需要 GitHub 帳戶 (如果還沒有的話)。 

- 註冊 [GitHub 帳戶](/contribute/get-started-setup-github)。


## <a name="how-to-connect"></a>如何連接
1. 登入 Power BI 服務 (`https://app.powerbi.com`)。 
2. 在導覽窗格中，選取 [應用程式]，然後選取 [取得應用程式]。
   
   ![Power BI Get 應用程式](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial.png) 

3. 選取 [應用程式]，在搜尋方塊中鍵入 **GitHub** > [立即取得]。
   
   ![Power BI Get GitHub](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-app-source.png) 

4. 在 [要安裝此 Power BI 應用程式嗎?] 中，選取 [安裝]。
5. 在 [您的新應用程式已準備就緒] 中，選取 [前往應用程式]。
6. 在 [開始使用您的新應用程式] 中，選取 [連線]。

    ![開始使用您的新應用程式](media/service-tutorial-connect-to-github/power-bi-new-app-connect-get-started.png)

7. 輸入該儲存機制的儲存機制名稱和儲存機制擁有者。 此存放庫的 URL 是 https://github.com/MicrosoftDocs/powerbi-docs，因此 [存放庫擁有者] 是 **MicrosoftDocs** ，而 [存放庫] 是 **powerbi-docs** 。 
   
    ![Power BI GitHub 存放庫名稱](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect.png)

5. 輸入您所建立的 GitHub 認證。 如果您已在瀏覽器中登入 GitHub，則 Power BI 可能會略過此步驟。 

6. 針對 [驗證方法]，將 [oAuth2] 保留為選取  [登入]\> 。

7. 遵循 GitHub 驗證畫面進行。 將 Power BI 權限授與 GitHub 資料。
   
   Power BI 現在可以與 GitHub 連線，並連線至資料。  資料會每天重新整理一次。

8. Power BI 匯入資料之後，您即可看到新 GitHub 工作區的內容。 
9. 在導覽窗格中，選取工作區名稱旁的箭號。 您會看到工作區包含一個儀表板和一份報表。 

    ![導覽窗格中的應用程式](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-left-nav-expanded.png)

10. 選取儀表板名稱旁邊的 [更多選項] (...) > [重新命名] > 鍵入 **GitHub 儀表板** 。
 
    ![Power BI GitHub 磚](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-left-nav.png) 

8. 選取全域導覽圖示來最小化導覽窗格，讓您有更多空間。

    ![全域導覽圖示](media/service-tutorial-connect-to-github/power-bi-global-navigation-icon.png)

10. 選取您的 GitHub 儀表板。
    
    GitHub 儀表板包含即時資料，因此您看到的值可能會有所不同。

    ![Power BI 中的 GitHub 儀表板](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-new-dashboard.png)

    

## <a name="ask-a-question"></a>詢問問題

1. 將您的游標放在 [詢問一個與資料相關的問題] 中。 Power BI 提供 **使用者入門問題** 。 

1. 選取 [有多少位使用者]。
 
    ![有多少位使用者](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-qna-how-many-users.png)

13. 在 **how many** (有多少位) 和 **users are there** (使用者) 之間，鍵入 **pull requests per** (提取要求 (每位))。 

     Power BI 會建立橫條圖，顯示每一位使用者的提取要求數。

    ![每一位使用者各有多少提取要求](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-qna-how-many-prs.png)


13. 選取圖釘來將它釘選到您的儀表板，然後 **離開問與答** 。

## <a name="view-the-github-report"></a>檢視 GitHub 報表 

1. 在 GitHub 儀表板中，選取直條圖 [提取要求數 (依月分)] 來開啟相關報表。

    ![提取要求數 (依月份) 直條圖](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-column-chart.png)

2. 在 [使用者的的總提取要求數] 圖表中，選取使用者名稱。 在此範例中，我們可以看到他們大多數的時數都集中在二月。

    ![Power BI GitHub 報表反白顯示](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-cross-filter-total-prs.png)

3. 選取 [穿孔卡片] 索引標籤來檢視報表中的下一個頁面。 
 
    ![Power BI GitHub 報表穿孔卡片](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-tues-3pm.png)

    顯然每週星期二下午 3 點是最常進行「認可」的時間，許多人會在這個時間簽入他們的工作。

## <a name="clean-up-resources"></a>清除資源

既然您已經完成本教學課程，就可以刪除 GitHub 應用程式。 

1. 在導覽窗格中，選取 [應用程式]。
2. 將滑鼠游標停留在 GitHub 磚，然後選取 [刪除] 垃圾桶。

    ![刪除 GitHub 應用程式](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-delete.png)

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已連線至 GitHub 公用存放庫並取得 Power BI 已在儀表板和報表中格式化的資料。 您已經探索儀表板和報表來回答有關資料的一些問題。 您現在可以深入了解連線至其他服務，例如 Salesforce、Microsoft Dynamics 和 Google Analytics。 
 
> [!div class="nextstepaction"]
> [使用 Power BI 範本應用程式連線到 GitHub](service-connect-to-github.md)
