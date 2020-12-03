---
title: Power BI 報表伺服器中的分頁報表資料來源
description: 深入了解在 Power BI 報表伺服器中分頁報表 (.rdl) 可連接的資料來源。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 06/26/2020
ms.openlocfilehash: 4559995baa7d3e0b5796ca6076687c26c4a0854d
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415373"
---
# <a name="paginated-report-data-sources--in-power-bi-report-server"></a>Power BI 報表伺服器中的分頁報表資料來源
Power BI 報表伺服器中的 Reporting Services 分頁報表所支援的資料來源，和 SQL Server Reporting Services 中支援的資料來源相同。 請參閱 [Reporting Services 支援的資料來源](/sql/reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs)清單。

## <a name="connect-to-oracle-data-sources-with-useinstalleduiculture"></a>使用 UseInstalledUICulture 連線到 Oracle 資料來源

為了連線到 Oracle 資料來源，Power BI 報表伺服器會使用與 NLS 無關的「.Net 的 Oracle 資料提供者」(ODP.NET)。

根據預設，報表伺服器會使用第一個用戶端的 UI 文化特性來載入 ODP.NET。  因此，在服務重新啟動之前，所有從報表伺服器連線到 Oracle 的後續連線都會使用該初始 UI 文化特性。  此方法可能造成轉譯報表的問題，因為 UI 文化特性格式不相符。

為了在 Power BI 報表伺服器中提供更好的體驗，我們已引進名為 UseInstalledUICulture 的組態設定。 當 UseInstalledUICulture 設定為 true 時，報表伺服器一律使用伺服器的 UI 文化特性載入 ODP.NET，而不是第一個用戶端的文化特性。
Power BI 報表伺服器從「2020 年 3 月服務版本」開始提供此設定。

若要啟用此功能，請修改 rsreportserver.config 檔案中的 ORACLE 延伸模組項目，如下所示。
```xml
<Extension Name="ORACLE" Type="Microsoft.ReportingServices.DataExtensions.OracleClientConnectionWrapper,Microsoft.ReportingServices.DataExtensions">
    <Configuration>
        <UseInstalledUICulture>true</UseInstalledUICulture>
    </Configuration>
</Extension>
```

## <a name="next-steps"></a>後續步驟
您現在已經連接到資料來源，接著可以[建立分頁報表](quickstart-create-paginated-report.md)。  


有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)