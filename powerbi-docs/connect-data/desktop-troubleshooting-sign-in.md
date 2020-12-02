---
title: 在 Power BI Desktop 中對登入問題進行疑難排解
description: 登入 Power BI Desktop 常見問題的解決方案
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: troubleshooting
ms.date: 03/05/2020
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 4a825c2e3bcfdbe637c59fde9c33dc23ad326b0e
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96404403"
---
# <a name="troubleshooting-sign-in-for-power-bi-desktop"></a>對 Power BI Desktop 的登入進行疑難排解
當您嘗試登入 **Power BI Desktop** 時，有時可能會遇到錯誤。 登入問題有兩個主要原因：**Proxy 驗證錯誤** 和 **非 HTTPS URL 重新導向錯誤**。 

若要判斷造成您登入問題的原因，首先請連絡您的系統管理員並提供診斷資訊，以便他們判斷問題的原因。 藉由追蹤與您登入問題相關聯的問題，系統管理員可以判斷適用於您的錯誤是以下哪一個。 

讓我們依序看看每個問題。 在本文結尾會討論如何在 Power BI Desktop 中擷取「追蹤」，這有助於追蹤疑難排解的問題。


## <a name="proxy-authentication-required-error"></a>需要 Proxy 驗證錯誤

以下畫面顯示「需要 Proxy 驗證」錯誤的範例。

![Proxy 驗證錯誤的登入錯誤](media/desktop-troubleshooting-sign-in/desktop-tshoot-sign-in_01.png)

*Power BI Desktop* 追蹤檔案中的以下例外狀況與此錯誤相關聯：

* *Microsoft.PowerBI.Client.Windows.Services.PowerBIWebException*
* *HttpStatusCode:ProxyAuthenticationRequired*

當此錯誤發生時，最可能的原因是您網路上的 Proxy 驗證伺服器封鎖 **Power BI Desktop** 發出的 Web 要求。 

如果您的網路使用 Proxy 驗證伺服器，您的管理員就可以藉由在 Proxy 驗證伺服器上將以下網域新增至允許清單，來修正此問題：

* app.powerbi.com
* api.powerbi.com
* *.analysis.windows.net 命名空間中的網域

對於屬於政府雲端的客戶，可藉由在 Proxy 驗證伺服器上將以下網域新增至允許清單，來修正此問題：

* app.powerbigov.us
* api.powerbigov.us
* *.analysis.usgovcloudapi.net 命名空間中的網域

## <a name="non-https-url-redirect-not-supported-error"></a>不支援非 HTTPS URL 重新導向錯誤

目前版本的 **Power BI Desktop** 使用目前版本的 Active Directory Authentication Library (ADAL)，而它不允許重新導向至不安全的 (非 HTTPS) URL。 

*Power BI Desktop* 追蹤檔案中的以下例外狀況與此錯誤相關聯：

* *Microsoft.IdentityModel.Clients.ActiveDirectory.AdalServiceException:WebView 中不支援非 HTTPS URL 重新導向*
* *ErrorCode: non_https_redirect_failed*

如果發生 *ErrorCode: non_https_redirect_failed*，表示重新導向鏈結中的一或多個重新導向頁面或提供者不是 HTTPS 保護的端點，或者一或多個重新導向的憑證簽發者不屬於裝置的信任根憑證。 登入重新導向鏈結中的所有提供者都必須使用 HTTPS URL。 若要解決此問題，請連絡您的系統管理員，並要求其驗證網站使用安全的 URL。 

## <a name="how-to-collect-a-trace-in-power-bi-desktop"></a>如何在 Power BI Desktop 中收集追蹤

若要在 **Power BI Desktop** 中收集追蹤，請遵循這些步驟：

1. 在 [Power BI Desktop] 中的以下位置啟用追蹤，移至 [檔案] > [選項及設定] > [選項]，然後在左窗格中的選項中選取 [診斷]。 在顯示的窗格中，選取 [啟用追蹤] 旁邊的方塊，如以下影像所示。 您可能需要重新啟動 [Power BI Desktop]。
   
   ![在 Power BI Desktop 中啟用追蹤](media/desktop-troubleshooting-sign-in/desktop-tshoot-sign-in_02.png)

2. 然後按照重現錯誤的步驟操作。 當錯誤發生時，**Power BI Desktop** 會將事件新增到追蹤記錄 (保留在本機電腦上)。

3. 瀏覽到本機電腦上的 [Traces] 資料夾。 您可以藉由在您啟用追蹤的 [診斷] 中，選取顯示為 [開啟損毀傾印/追蹤資料夾] 的連結來尋找該資料夾，如上一個影像所示。 通常可以在本機電腦的以下位置找到：

    `C:\Users/<user name>/AppData/Local/Microsoft/Power BI Desktop/Traces`

該資料夾中可能有許多追蹤檔案。 請確定只傳送最近的檔案給您的系統管理員，這樣有助於他們快速識別錯誤。 


## <a name="using-default-system-credentials-for-web-proxy"></a>使用 Web Proxy 的預設系統認證

Power BI Desktop 發出的 Web 要求不會使用 Web Proxy 認證。 在使用 Proxy 伺服器的網路中，Power BI Desktop 可能無法成功提出 Web 要求。 

從 2020 年 3 月的 Power BI Desktop 版本開始，系統或網路系統管理員可以允許使用預設系統認證來進行 Web Proxy 驗證。 系統管理員可以建立名為 **UseDefaultCredentialsForProxy** 的登錄項目，並將值設定為一 (1) 以允許使用預設系統認證進行 Web Proxy 驗證。

登錄項目可以放在下列其中一個位置：

`[HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Microsoft Power BI Desktop]`
`[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Power BI Desktop]`

登錄項目不一定要同時放在這兩個位置中。

![使用預設系統認證的登錄機碼](media/desktop-troubleshooting-sign-in/desktop-tshoot-sign-in-03.png)

建立登錄項目後 (可能需要重新開機)，當 Power BI Desktop 提出 Web 要求時，就會使用在 Internet Explorer 中定義的 Proxy 設定。 

如同對 Proxy 或認證設定所做的任何變更一樣，建立此登錄項目時可能會影響安全性，因此系統管理員必須先確定其已正確設定 Internet Explorer Proxy，再啟用此功能。         

### <a name="limitations-and-considerations-for-using-default-system-credentials"></a>使用預設系統認證的限制與考量

在啟用這項功能之前，系統管理員應該考量的一系列安全性影響。 

為用戶端啟用這項功能時，應遵循下列建議：

* 僅使用 **協商** 作為 Proxy 伺服器上的驗證配置，以確保用戶端僅使用加入至 Active Directory 網路的 Proxy 伺服器。 
* 請勿在使用這項功能的用戶端上使用 **NTLM 後援**。
* 當此功能依照本節的建議啟用及設定時，如果使用者不在具有 Proxy 的網路上，則不會使用嘗試連至 Proxy 伺服器和使用預設系統認證的程序。


[使用 Web Proxy 的預設系統認證](#using-default-system-credentials-for-web-proxy)

