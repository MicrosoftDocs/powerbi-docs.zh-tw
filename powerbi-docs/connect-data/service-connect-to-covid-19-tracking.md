---
title: 連線至 COVID-19 美國追蹤報表
description: 如何取得並安裝 COVID-19 美國案例範本應用程式，以及如何連線至資料。
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 04/05/2020
LocalizationGroup: Connect to services
ms.openlocfilehash: fc421f7635a3d6e3b2336d5bce081d7914c0fad5
ms.sourcegitcommit: 8250187368d3de48663eb516a816ff701119b579
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "96998846"
---
# <a name="connect-to-the-covid-19-us-tracking-report"></a>連線至 COVID-19 美國追蹤報表
本文示範如何安裝 COVID-19 追蹤報表的範本應用程式，以及如何連線至資料來源。

![COVID-19 美國追蹤報表](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-title-screen.png)

如需報表本身的詳細資訊，包括免責聲明和資料相關資訊，請參閱[美國州政府和地方政府的 COVID-19 追蹤範例](../create-reports/sample-covid-19-us.md)。

在安裝範本應用程式並連線至資料來源後，即可依照需求來自訂報表。 然後即可將報表當作應用程式散發給組織中的同事。

## <a name="install-the-app"></a>安裝應用程式

1. 按一下下列連結以取得應用程式：[COVID-19 美國追蹤報表範本應用程式](https://app.powerbi.com/groups/me/getapps/services/pbi-contentpacks.covid19ms)

1. 在應用程式的 [AppSource] 頁面上，按一下 [[立即取得]](https://app.powerbi.com/groups/me/getapps/services/pbi-contentpacks.covid19ms)。

    [![AppSource 中的新型冠狀病毒 (COVID-19) 美國追蹤報表](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-appsource-icon.png)](https://app.powerbi.com/groups/me/getapps/services/pbi-contentpacks.covid19ms)

1. 出現提示時，請按一下 [安裝]  。 應用程式安裝完成後，會顯示在 [應用程式] 頁面上。

   ![[應用程式] 頁面上的 COVID-19 美國追蹤報表](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-apps-page-icon.png)

## <a name="connect-to-data-sources"></a>連接至資料來源

1. 按一下 [應用程式] 頁面上的圖示以開啟應用程式。 應用程式隨即開啟，其中顯示範例資料。

1. 在頁面頂端的橫幅中，選取 [連線至資料] 連結。

   ![GitHub 應用程式 [連線至資料] 連結](media/service-connect-to-covid-19-tracking/power-bi-covid-19-connect-data.png)

1. [參數] 對話方塊隨即出現。 沒有必要的參數。 按 [下一步]  。

   ![[COVID-19 美國追蹤報表] 的 [參數] 對話方塊螢幕擷取畫面。](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-parameters-dialog.png)

1. [驗證方法] 對話方塊隨即出現。 已預先填入建議值。 除非您具備不同值的特定知識，否則請勿變更這些值。

    按 [下一步]  。

   ![[COVID-19 美國追蹤報表] 驗證對話方塊的螢幕擷取畫面。](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-authentication-dialog.png)

1. 按一下 [ **登入**]。

   ![[COVID-19 美國追蹤報表] 登入對話方塊的螢幕擷取畫面。](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-signin-dialog.png)
 
   報表會連線至資料來源，並使用最新的資料填入。 在這段期間，您會看到範例資料，且重新整理正在進行中。

   ![Covid-19 美國追蹤報表正在重新整理](media/service-connect-to-covid-19-tracking/service-covid-19-us-tracking-report-refresh-monitor.png)

## <a name="schedule-report-refresh"></a>排程報表重新整理

當資料重新整理完成時，您會位於與應用程式建立關聯的工作區中。 [設定重新整理排程](../connect-data/refresh-scheduled-refresh.md)以將報表資料保持在最新狀態。

## <a name="customize-and-share"></a>自訂和共用

如需詳細資訊，請參閱[自訂和共用應用程式](../connect-data/service-template-apps-install-distribute.md#customize-and-share-the-app)。 在發佈或散發應用程式前，請務必先檢閱[報告免責聲明](../create-reports/sample-covid-19-us.md#disclaimers)。

## <a name="next-steps"></a>後續步驟
* [適用於美國州和地方政府的 COVID-19 追蹤範例](../create-reports/sample-covid-19-us.md)
* 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
* [什麼是 Power BI 範本應用程式？](../connect-data/service-template-apps-overview.md)
* [在組織中安裝並散發範本應用程式](../connect-data/service-template-apps-install-distribute.md)
