---
title: 解決啟動 Power BI Desktop 的問題
description: 解決啟動 Power BI Desktop 的問題
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/28/2018
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 78cfcd51a951095353ce5d0f25c4511cc720c632
ms.sourcegitcommit: 05303d3e0454f5627eccaa25721b2e0bad2cc781
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2018
ms.locfileid: "52578213"
---
# <a name="resolve-issues-when-power-bi-desktop-will-not-launch"></a>解決 Power BI Desktop 無法啟動的問題
在 **Power BI Desktop** 中，因為 Power BI 內部部署閘道在本機電腦的具名管道上設置了系統管理原則限制，所以會封鎖安裝並執行舊版 **Power BI 內部部署資料閘道**的使用者，讓他們無法啟動 Power BI Desktop。 

## <a name="resolve-issues-with-the-on-premises-data-gateway-and-power-bi-desktop"></a>解決內部部署資料閘道和 Power BI Desktop 的問題
您可以透過下列三個選項，來解決與內部部署資料閘道相關聯的問題，並允許啟動 Power BI Desktop：

### <a name="resolution-1-install-the-latest-version-of-power-bi-on-premises-data-gateway"></a>解決方法 1：安裝最新版的 Power BI 內部部署資料閘道
最新版的 Power BI 內部部署資料閘道不會在本機電腦上設置具名管道限制，且允許正確啟動 Power BI Desktop。 如果您需要繼續使用 Power BI 內部部署資料閘道，建議使用這個解決方法。 您可以從[這個位置](https://go.microsoft.com/fwlink/?LinkId=698863)下載最新版的 Power BI 內部部署資料閘道。 請注意，這是直接下載安裝執行檔的連結。

### <a name="resolution-2-uninstall-or-stop-the-power-bi-on-premises-data-gateway-windows-service"></a>解決方法 2：解除安裝或停止 Power BI 內部部署資料閘道 Windows 服務
如果不再需要 Power BI 內部部署資料閘道，您可以解除安裝或停止 Power BI 內部部署資料閘道 Windows 服務，這樣會移除原則限制並允許啟動 Power BI Desktop。

### <a name="resolution-3-run-power-bi-desktop-with-administrator-privilege"></a>解決方法 3：以系統管理員權限執行 Power BI Desktop
或者，您可以系統管理員的身分成功啟動 Power BI Desktop，這樣也可以成功啟動 Power BI Desktop。 但仍建議您如前文所述，安裝最新版的 Power BI 內部部署資料閘道。

請務必注意，Power BI Desktop 經過程式設計成多處理序架構，且這些處理序中有數個使用 Windows 具名管道來通訊。 可能會有其他處理序影響那些具名管道。 這種影響最常見的原因是安全性，包括的情況如防毒軟體或防火牆可能會封鎖管道或將流量重新導向至特定連接埠。 以系統管理員權限啟動 Power BI Desktop 可以解決該問題。 如果無法以系統管理員權限啟動，請連絡您的系統管理員以判斷是哪些已套用的安全性規則讓具名管道無法正常通訊，並且將 Power BI Desktop 和其個別的子處理序加入白名單。

## <a name="resolve-issues-when-connecting-to-sql-server"></a>解決連線至 SQL Server 時的問題
如果連線至 SQL Server 資料庫時，您會遇到類似下列的錯誤訊息，您通常可以系統管理員身分啟動 **Power BI Desktop**，然後建立 SQL Server 連線來解決問題：

    "An error happened while reading data from the provider: 'Could not load file or assembly 'System.EnterpriseServices, Version=4.0.0.0, Culture=neutral, PublicKeyToken=xxxxxxxxxxxxx' or one of its dependencies. Either a required impersonation level was not provided, or the provided impersonation level is invalid. (Exception from HRESULT: 0x80070542)'"

以系統管理員身分啟動並建立連線之後，所需的 DLL 便已正確註冊。 在這之後，就不需要以系統管理員身分啟動 Power BI Desktop。

## <a name="help-with-other-issues-when-launching-power-bi-desktop"></a>協助解決啟動 Power BI Desktop 時發生的其他問題
我們致力於將 **Power BI Desktop** 所發生的問題涵蓋在本文中。 我們經常檢視可能會影響眾多客戶的問題，並將它們包含在我們的文章內。

如果啟動 **Power BI Desktop** 時發生的問題與內部部署資料閘道無關，或上述解決方法無法解決問題，您可以將支援事件提交給 [Power BI 支援](https://support.powerbi.com) (https://support.powerbi.com), 以協助找出並解決問題。

如果未來遇到 **Power BI Desktop** 的其他問題 (我們希望沒有或非常少)，開啟追蹤並收集記錄檔將有助於更佳隔離並找出問題。 若要開啟追蹤，請選取 [檔案] > [選項及設定] > [選項]，選取 [診斷]，然後核取 [診斷選項] 下的 [啟用追蹤]。 我們了解 **Power BI Desktop** 必須在執行中才能設定此選項，因此更有助於解決未來與啟動 **Power BI Desktop** 相關聯的問題。

