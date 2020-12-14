---
title: 安裝 Power BI 報表伺服器的硬體和軟體需求
description: 此文章將列出安裝並執行 Power BI 報表伺服器的最低硬體和軟體需求。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 12/07/2020
ms.openlocfilehash: 10fb104d1c03ae5d08836b8e865178c347d848ce
ms.sourcegitcommit: 0bf42b6393cab7a37d21a52b934539cf300a08e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2020
ms.locfileid: "96781765"
---
# <a name="hardware-and-software-requirements-for-installing-power-bi-report-server"></a>安裝 Power BI 報表伺服器的硬體和軟體需求

此文章將列出安裝並執行 Power BI 報表伺服器的最低硬體和軟體需求。

## <a name="processor-memory-and-operating-system-requirements"></a>處理器、記憶體和作業系統需求

| 元件 | 需求 |
| --- | --- |
| .NET Framework |4.8<br><br>如果伺服器無法存取網際網路，則可從 [Windows 的 Microsoft .NET Framework 4.8 (離線安裝程式)](https://support.microsoft.com/en-us/help/4503548/) 手動安裝 .NET Framework。<br/><br/> 如需 .NET Framework 4.8 的詳細資訊、建議和指導，請參閱[開發人員的 .NET Framework 部署手冊](/dotnet/framework/deployment/deployment-guide-for-developers)。<br/><br/>Windows 8.1 和 Windows Server 2012 R2 需要有 [KB2919355](https://support.microsoft.com/kb/2919355) 才能安裝 .NET Framework 4.8。 |
| 硬碟 |Power BI 報表伺服器至少需要 1 GB 的可用硬碟空間。<br><br>裝載報表伺服器資料庫的資料庫伺服器則需要額外的空間。 |
| 記憶體 |**最小值：** 1 GB<br/><br/> **建議值︰** 至少 4 GB |
| 處理器速度 |**最小值：** x64 處理器：1.4 GHz<br/><br/> **建議配備：** 2.0 GHz 或更快 |
| 處理器類型 |x64 處理器：AMD Opteron、AMD Athlon 64、具有 Intel EM64T 支援的 Intel Xeon、具有 EM64T 支援的 Intel Pentium IV |
| 作業系統 |Windows Server 2019 Datacenter<br><br>Windows Server 2019 Standard<br><br>Windows Server 2016 Datacenter<br><br>Windows Server 2016 Standard<br><br>Windows 10 Home<br><br>Windows 10 Professional<br><br>Windows 10 Enterprise<br> |

> [!NOTE]
> 只有 x64 處理器會支援 Power BI 報表伺服器的安裝。


## <a name="database-server-version-requirements"></a>資料庫伺服器版本需求

SQL Server 可用來裝載報表伺服器資料庫。 SQL Server 資料庫引擎執行個體可以是本機或遠端執行個體。 以下是可用來裝載報表伺服器資料庫的 SQL Server 資料庫引擎支援版本：

* Azure SQL 受控執行個體 (Power BI 報表伺服器 2020 年 1 月版與更新版本)
* SQL Server 2019
* SQL Server 2017
* SQL Server 2016
* SQL Server 2014
* SQL Server 2012

當您在遠端電腦上建立報表伺服器資料庫時，必須設定連線，才能使用網域使用者帳戶或具有網路存取權的服務帳戶。 如果您決定使用遠端 SQL Server 執行個體，請仔細考慮報表伺服器應該用來連線到 SQL Server 執行個體的認證。 如需詳細資訊，請參閱 [Configure a Report Server Database Connection](/sql/reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager) (設定報表伺服器資料庫連線)。

## <a name="considerations"></a>考量

Power BI 報表伺服器會安裝預設值，以設定讓報表伺服器運作所需的核心設定。 它的需求如下：

* Power BI 報表伺服器支援的語言包括：英文、德文、西班牙文、日文、義大利文、法文、俄文、簡體中文、繁體中文、葡萄牙文 (巴西)、韓文
* 在您設定報表伺服器資料庫前，SQL Server 資料庫引擎必須已安裝且可用。 資料庫引擎執行個體裝載 Reporting Services 設定管理員會建立的報表伺服器資料庫。 實際的安裝體驗不需要資料庫引擎。
* [SQL Server 版本支援的 Reporting Services 功能](/sql/reporting-services/reporting-services-features-supported-by-the-editions-of-sql-server-2016)會概述 SQL server 版本之間的差異。
* 執行安裝程式的使用者帳戶必須是本機系統管理員群組的成員。
* 執行 Reporting Services 組態管理員的使用者帳戶，在裝載報表伺服器資料庫的資料庫引擎執行個體上必須有權存取與建立資料庫。
* 安裝程式必須能夠使用預設值，以保留提供存取報表伺服器和入口網站的 URL。 這些值為連接埠 80、強式萬用字元及格式為 **ReportServer** 和 **Reports** 的虛擬目錄名稱。

## <a name="read-only-domain-controller-rodc"></a>唯讀網域控制站 (RODC)

 您可以在具有唯讀網域控制站 (RODC) 的環境中安裝報表伺服器。 不過，Reporting Services 需要存取讀寫網域控制站的權限，才能正常運作。 如果 Reporting Services 只能存取 RODC，嘗試管理服務時可能會發生錯誤。

## <a name="power-bi-reports-and-analysis-services-live-connections"></a>Power BI 報表和 Analysis Services 即時連線

您可以使用即時連線針對表格式或多維度執行個體。 您的 Analysis Services 伺服器必須是適當的版本才能正常運作。

| **伺服器版本** | **必要的 SKU** |
| --- | --- |
| 2012 SP1 CU4 或更新版本 |商業智慧和企業版 SKU |
| 2014 |商業智慧和企業版 SKU |
| 2016 和更新版本 |標準 SKU 或更高版本 |

## <a name="next-steps"></a>後續步驟

[什麼是 Power BI 報表伺服器？](get-started.md)  
[系統管理員概觀](admin-handbook-overview.md)  
[安裝 Power BI 報表伺服器](install-report-server.md)  
[下載報表產生器](https://www.microsoft.com/download/details.aspx?id=53613)  
[下載 SQL Server Data Tools (SSDT)](/sql/ssdt/download-sql-server-data-tools-ssdt)

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
