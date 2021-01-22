---
title: 解決啟動 Power BI Desktop 時發生的問題
description: 解決啟動 Power BI Desktop 時發生的問題
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: troubleshooting
ms.date: 11/14/2020
LocalizationGroup: Troubleshooting
ms.openlocfilehash: c41f8f9b23ef57d5dd6fd4b851918b7ffa5904a0
ms.sourcegitcommit: ab28cf07b483cb4b01a42fa879b788932bba919d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2021
ms.locfileid: "98226931"
---
# <a name="troubleshoot-opening-power-bi-desktop"></a>針對 Power BI Desktop 的開啟問題進行疑難排解

此文章說明並提供多種 Power BI 無法開啟之情況的補救方式。 

## <a name="resolve-issues-with-opening-encrypted-pbix-files"></a>解決開啟已加密 PBIX 檔案的問題

您無法使用不支援資訊保護的 Power BI Desktop 版本開啟已加密的 PBIX 檔案。

如果您需要繼續使用 Power BI Desktop，建議的解決方法是將其更新至支援資訊保護的版本。 您可以下載[最新版本的 Power BI Desktop](https://www.microsoft.com/download/confirmation.aspx?id=58494) (這是直接下載安裝可執行檔的連結)。 最新版的 Power BI Desktop 支援資訊保護，而且可以解密並開啟任何已加密的 PBIX 檔案。

###

## <a name="resolve-issues-with-the-on-premises-data-gateway-and-power-bi-desktop"></a>解決內部部署資料閘道和 Power BI Desktop 的問題

在 Power BI Desktop 中，因為 Power BI 內部部署閘道在本機電腦的具名管道上設置了系統管理原則限制，所以會封鎖安裝並執行舊版 *Power BI 內部部署資料閘道* 的使用者，讓他們無法開啟 Power BI Desktop。

您可以透過下列三個選項，來解決與內部部署資料閘道相關聯的問題，並允許開啟 Power BI Desktop：

### <a name="resolution-1-install-the-latest-version-of-power-bi-on-premises-data-gateway"></a>解決方法 1：安裝最新版的 Power BI 內部部署資料閘道

最新版的 Power BI 內部部署資料閘道不會在本機電腦上設置具名管道限制，且允許正確開啟 Power BI Desktop。 如果您需要繼續使用 Power BI 內部部署資料閘道，建議的解決方法是將其更新。 您可以[下載最新版的 Power BI 內部部署資料閘道](https://go.microsoft.com/fwlink/?LinkId=698863)。 這是直接下載安裝可執行檔的連結。

### <a name="resolution-2-uninstall-or-stop-the-power-bi-on-premises-data-gateway-microsoft-service"></a>解決方法 2：解除安裝或停止 Power BI 內部部署資料閘道 Microsoft 服務

如果不再需要 Power BI 內部部署資料閘道，您可以將其解除安裝。 或者，您可以停止 Power BI 內部部署資料閘道 Microsoft 服務，這樣會移除原則限制並允許開啟 Power BI Desktop。

### <a name="resolution-3-run-power-bi-desktop-with-administrator-privilege"></a>解決方法 3：以系統管理員權限執行 Power BI Desktop

您可以改為以系統管理員身分成功啟動 Power BI Desktop，這樣也可以成功開啟 Power BI Desktop。 但仍建議您如先前所述，安裝最新版的 Power BI 內部部署資料閘道。

Power BI Desktop 經過程式設計成多處理序架構，且這些處理序中有數個使用 Windows 具名管道來通訊。 可能會有其他處理序影響那些具名管道。 這種影響最常見的原因是安全性，包括的情況如防毒軟體或防火牆可能會封鎖管道或將流量重新導向至特定連接埠。 以系統管理員權限開啟 Power BI Desktop 可以解決該問題。 如果您無法以系統管理員權限開啟，請洽詢您的系統管理員，以判斷哪些安全性規則導致具名管道無法正確通訊。 然後將 Power BI Desktop 及其各自的子處理序新增至允許清單。

## <a name="resolve-issues-when-connecting-to-sql-server"></a>解決連線至 SQL Server 時的問題

當您嘗試連線到 SQL Server 資料庫時，可能會看到類似下列文字的錯誤訊息：

`"An error happened while reading data from the provider:`\
`'Could not load file or assembly 'System.EnterpriseServices, Version=4.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxx' or one of its dependencies.`\
`Either a required impersonation level was not provided, or the provided impersonation level is invalid. (Exception from HRESULT: 0x80070542)'"`

如果您先以系統管理員身分開啟 Power BI Desktop，然後再建立 SQL Server 連線，通常可以解決此問題。

以系統管理員身分開啟 Power BI Desktop 並建立連線之後，便會正確地註冊所需的 DLL。 之後就不需要再以系統管理員身分開啟 Power BI Desktop。 如果使用替代的 Windows 認證連線到 SQL server，則每次連線時，都必須以系統管理員身分開啟 Power BI Desktop。

## <a name="get-help-with-other-launch-issues"></a>取得其他啟動問題的協助

我們盡可能在本文中涵蓋 Power BI Desktop 會發生的問題。 我們經常檢視可能會影響眾多客戶的問題，並將它們包含在我們的文章內。

如果開啟 Power BI Desktop 時發生的問題與內部部署資料閘道無關，或上述解決方法無法解決問題，您可以將支援事件提交給 *Power BI 支援* (<https://support.powerbi.com>) 以協助找出並解決問題。

如果您未來使用 Power BI Desktop 時發生其他問題，開啟追蹤並收集記錄檔會有所幫助， 記錄檔可能有助於隔離並識別問題。 若要開啟追蹤功能，請選擇 [檔案] > [選項及設定] > [選項]、選取 [診斷]，然後選取 [啟用追蹤]。 Power BI Desktop 必須在執行中才能設定此選項，但這有助於解決未來與開啟 Power BI Desktop 有關的問題。
