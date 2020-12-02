---
title: 連線至危機通訊狀態報表
description: 如何取得及安裝 COVID-19 危機通訊狀態報表範本應用程式，以及如何連線至資料
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 04/06/2020
LocalizationGroup: Connect to services
ms.openlocfilehash: 7cce4f9e78fce27fedf795a4a0016593580f061a
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96403160"
---
# <a name="connect-to-the-crisis-communication-presence-report"></a>連線至危機通訊狀態報表

此 Power BI 應用程式是 Microsoft Power Platform 中危機通訊解決方案的報表/儀表板成品。 此應用程式會追蹤危機通訊應用程式使用者的背景工作位置。 此解決方案結合 Power Apps、Power Automate、Teams、SharePoint 和 Power BI 的功能。 可在 Web、行動裝置或 Teams 中使用。

![危機通訊狀態報表應用程式報表](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report.png)

儀表板會向緊急狀況管理員顯示其醫療系統的彙總資料，以協助其做出及時且正確的決策。

本文示範如何安裝應用程式及如何連線至資料來源。 如需危機通訊應用程式的詳細資訊，請參閱[設定及了解 Power Apps 中的危機通訊範例範本](/powerapps/maker/canvas-apps/sample-crisis-communication-app) (機器翻譯)

在安裝範本應用程式並連線至資料來源後，即可依照需求來自訂報表。 然後您即可將報表當作應用程式散發給組織中的同事。

## <a name="prerequisites"></a>必要條件

在安裝此範本應用程式前，必須先安裝並設定[危機通訊範例](/powerapps/maker/canvas-apps/sample-crisis-communication-app)。 安裝此解決方案會建立將資料填入應用程式所需的資料來源參考。

安裝危機通訊範例時，請記下 ["CI_Employee Status" 和清單識別碼的 SharePoint 清單資料夾路徑](/powerapps/maker/canvas-apps/sample-crisis-communication-app#monitor-office-absences-with-power-bi)。

## <a name="install-the-app"></a>安裝應用程式

1. 按一下下列連結以取得應用程式：[危機通訊狀態報表範本應用程式](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.crisiscomms)

1. 在應用程式的 [AppSource][ **頁面上選取 [立即取得]**](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.crisiscomms)。

    [![AppSource 中的危機通訊狀態報表應用程式](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-appsource-get-it-now.png)](https://appsource.microsoft.com/en-us/product/power-bi/pbi-contentpacks.crisiscomms)

1. 閱讀 [還有一件事]  中的資訊，然後選取 [繼續]  。

    ![危機通訊狀態報表應用程式，[還有一件事]](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-1-more-thing.png)

1. 選取 [安裝]  。 

    ![安裝危機通訊狀態報表應用程式](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-select-install.png)

    應用程式安裝完成後，會顯示在 [應用程式] 頁面上。

   ![[應用程式] 頁面上的危機通訊狀態報表應用程式](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>連接至資料來源

1. 選取 [應用程式] 頁面上的圖示以開啟應用程式。

1. 在啟動顯示畫面上，選取 [探索]  。

   ![範本應用程式啟動顯示畫面](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-splash-screen.png)

   應用程式隨即開啟，其中顯示範例資料。

1. 在頁面頂端的橫幅中，選取 [連線至資料]  連結。

   ![危機通訊狀態報表應用程式的連線至資料連結](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-connect-data.png)

1. 在對話方塊中：
   1. 在 [SharePoint_Folder] 欄位中，輸入 ["CI_Employee Status" SharePoint 清單路徑](/powerapps/maker/canvas-apps/sample-crisis-communication-app#monitor-office-absences-with-power-bi)。
   1. 在 [List_ID] 欄位中，輸入從清單設定中取得的清單識別碼。 完成時，按一下 [下一步]  。

   ![危機通訊狀態報表應用程式 URL 對話方塊](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-url-dialog.png)

1. 在顯示的下一個對話方塊中，將驗證方法設定為 **OAuth2**。 您不需要對隱私權等級設定執行任何操作。

   選取 [登入]  。

   ![危機通訊狀態報表應用程式驗證對話方塊](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-authentication-dialog.png)

1. 在 Microsoft 登入畫面上登入 Power BI。

   ![Microsoft 登入畫面](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-microsoft-login.png)

   登入後，報表會連線至資料來源，並使用最新的資料填入。 在這段期間，活動監視器會開啟。

   ![危機通訊狀態報表應用程式正在重新整理](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-refresh-monitor.png)

## <a name="schedule-report-refresh"></a>排程報表重新整理

當資料重新整理完成時，請[設定重新整理排程](../connect-data/refresh-scheduled-refresh.md)以將報表資料保持在最新狀態。

1. 在頂端標題列中，選取 [Power BI]  。

   ![Power BI 階層連結](media/service-connect-to-crisis-communication-presence-report/service-crisis-communication-presence-report-app-powerbi-breadcrumb.png)

1. 在左側瀏覽窗格中，在 [工作區]  下尋找醫院緊急回應決策支援儀表板工作區，並遵循[設定排程的重新整理](../connect-data/refresh-scheduled-refresh.md)一文中所述指示。

## <a name="customize-and-share"></a>自訂和共用

如需詳細資訊，請參閱[自訂和共用應用程式](../connect-data/service-template-apps-install-distribute.md#customize-and-share-the-app)。 在發佈或散發應用程式前，請務必先檢閱[報告免責聲明](../create-reports/sample-covid-19-us.md#disclaimers)。

## <a name="next-steps"></a>後續步驟
* [設定及了解 Power Apps 中的危機通訊範例範本](/powerapps/maker/canvas-apps/sample-crisis-communication-app) (機器翻譯)
* 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
* [什麼是 Power BI 範本應用程式？](../connect-data/service-template-apps-overview.md)
* [在組織中安裝並散發範本應用程式](../connect-data/service-template-apps-install-distribute.md)