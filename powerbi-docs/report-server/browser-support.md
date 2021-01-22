---
title: Power BI 報表伺服器的瀏覽器支援
description: 了解管理及檢視 Power BI 報表伺服器和報表檢視器控制項所支援的瀏覽器版本。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 01/21/2021
ms.openlocfilehash: 71ee66c6cd531a35a53a3263feaf94115b528114
ms.sourcegitcommit: 77912d4f6ef2a2b1ef8ffccc50691fe5b38ee97a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/22/2021
ms.locfileid: "98687480"
---
# <a name="browser-support-for-power-bi-report-server"></a>Power BI 報表伺服器的瀏覽器支援
了解管理及檢視 Power BI 報表伺服器和報表檢視器控制項所支援的瀏覽器版本。

> [!NOTE]
> 舊版 Microsoft Edge 瀏覽器的支援將于2021年3月9日停止，Microsoft Internet Explorer 11 的支援將于2021年8月17日起停止。

## <a name="browser-requirements-for-the-web-portal"></a>入口網站的瀏覽器需求
以下是入口網站目前支援的瀏覽器清單。

**Microsoft Windows**  
*Windows 7、8.1、10；Windows Server 2008 R2、2012、2012 R2*

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)

**Apple OS X**  
*OS X 10.9-10.11*

* Apple Safari (+)
* Google Chrome (+)
* Mozilla Firefox (+)

**Apple iOS**  
*使用 iOS 10 的 iPhone 與 iPad*

* Apple Safari (+)

**Google Android**  
*電話和平板電腦 (含 Android 4.4 (KitKat) 或更新版本)*

* Google Chrome (+)
  
  **(+)** 最新的公開發行版本

## <a name="browser-requirements-for-the-report-viewer-web-control-2015"></a>報表檢視器 Web 控制項 (2015) 的瀏覽器需求
以下是報表檢視器 Web 控制項目前支援的瀏覽器清單。 報表檢視器支援從入口網站檢視報表。

**Microsoft Windows**  
*Windows 7、8.1、10；Windows Server 2008 R2、2012、2012 R2*

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)

**Apple OS X**  
*OS X 10.9-10.11*

* Apple Safari (+)
  
  **(+)** 最新的公開發行版本

### <a name="authentication-requirements"></a>驗證需求
瀏覽器可支援必須由報表伺服器處理的特定驗證配置，用戶端要求才會成功。 下表將識別 Windows 作業系統上執行之每個瀏覽器所支援的預設驗證類型。

| **瀏覽器類型** | **支援** | **瀏覽器預設值** | **伺服器預設值** |
| --- | --- | --- | --- |
| **Microsoft Edge** (+) |交涉, Kerberos, NTLM, 基本 |交涉 |是。 預設驗證設定適用於 Edge。 |
| **Microsoft Internet Explorer** |交涉, Kerberos, NTLM, 基本 |交涉 |是。 搭配 Internet Explorer 使用預設驗證設定。 |
| **Google Chrome**(+) |交涉, NTLM, 基本 |交涉 |是。 預設驗證設定適用於 Chrome。 |
| **Mozilla Firefox**(+) |NTLM，基本 |NTLM |是。 搭配 Firefox 使用預設驗證設定。 |
| **Apple Safari**(+) |NTLM，基本 |基本 |是。 搭配 Safari 使用預設驗證設定。 |

 **(+)** 最新的公開發行版本

### <a name="script-requirements-for-viewing-reports"></a>檢視報表的指令碼需求
若要使用報表檢視器，請設定瀏覽器來執行指令碼。

如果指令碼功能未啟用，當您開啟報表時，會看到類似下列的錯誤訊息：

```
Your browser does not support scripts or has been configured to not allow scripts to run. Click here to view this report without scripts
```

 如果您選擇檢視不含指令碼支援的報表，報表會以 HTML 轉譯，且不含報表檢視器功能 (例如，報表工具列和文件引導模式)。

> [!NOTE]
> 報表工具列屬於 HTML 檢視器元件的一部分。 根據預設，此工具列會出現在瀏覽器視窗中轉譯的每個報表上方。 報表檢視器會提供一些功能，包括搜尋報表中的資訊、捲動至特定頁面以及調整頁面大小以供檢視等功能。 如需有關報表工具列或 HTML 檢視器的詳細資訊，請參閱＜ [HTML Viewer and the Report Toolbar](/sql/reporting-services/html-viewer-and-the-report-toolbar)＞。
> 
> 

## <a name="browser-support-for-report-viewer-web-server-controls-in-visual-studio"></a>Visual Studio 中報表檢視器 Web 伺服器控制項的瀏覽器支援
報表檢視器 Web 伺服器控制項是用來在 ASP.NET Web 應用程式中內嵌報表功能。 如需有關如何取得報表檢視器控制項的詳細資訊，請參閱[使用報表檢視器控制項整合 Reporting Services - 開始進行](/sql/reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls-get-started)。

請使用已啟用指令碼支援的瀏覽器。 如果瀏覽器無法執行指令碼，您便無法檢視報表。

**Microsoft Windows**  
*Windows 7、8.1、10；Windows Server 2008 R2、2012、2012 R2*

* Microsoft Edge (+)
* Microsoft Internet Explorer 11
* Google Chrome (+)
* Mozilla Firefox (+)
  
  **(+)** 最新的公開發行版本

## <a name="next-steps"></a>後續步驟
[系統管理員概觀](admin-handbook-overview.md)  
[安裝 Power BI 報表伺服器](install-report-server.md)  
[下載報表產生器](https://www.microsoft.com/download/details.aspx?id=53613)  
[下載 SQL Server Data Tools (SSDT)](/sql/ssdt/download-sql-server-data-tools-ssdt)

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
