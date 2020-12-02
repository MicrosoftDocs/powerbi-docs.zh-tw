---
title: 在 Power BI 中監視報表效能
description: 如何在 Power BI 中監視報表效能的指導方針。
author: peter-myers
ms.author: v-pemyer
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 02/16/2020
ms.openlocfilehash: bd700ae7c6c175f4e9cf7841ce308a275ba9babb
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96393020"
---
# <a name="monitor-report-performance-in-power-bi"></a>在 Power BI 中監視報表效能

使用 [Power BI Premium 計量應用程式](../admin/service-premium-metrics-app.md)在 Power BI Desktop 中監視報表效能、了解瓶頸所在，以及了解如何改善報表效能。

監視效能與下列情況有關：

- 您的匯入資料模型重新整理變慢。
- 您的 DirectQuery 或「即時連線」報表速度很慢。
- 您的模型計算速度很慢。

為了達到持續最佳化，建議您將焦點放在緩慢的查詢或報表視覺效果上。

## <a name="use-query-diagnostics"></a>使用查詢診斷

在 Power BI Desktop 中使用[查詢診斷](/power-query/QueryDiagnostics)，以判斷在預覽或套用查詢時 Power Query 所執行的作業。 此外，請使用「診斷步驟」功能，記錄每個查詢步驟的詳細評估資訊。 結果會在 Power Query 中提供，您可以套用轉換以進一步了解查詢執行。

> [!NOTE]
> 查詢診斷目前是預覽功能，因此您必須在 [選項及設定] 中加以啟用。 啟用之後，您可以在 [Power Query 編輯器] 視窗的 [工具] 功能區索引標籤上找到其命令。

![Power Query 編輯器 [工具] 功能區索引標籤的螢幕擷取畫面，其中顯示 [診斷步驟] 命令、[開始診斷] 命令和 [停止診斷] 命令。](media/monitor-report-performance/power-query-diagnotics.png)

## <a name="use-performance-analyzer"></a>使用效能分析器

在 Power BI Desktop 中，使用[效能分析器](../create-reports/desktop-performance-analyzer.md)了解每個報表元素 (例如視覺效果和 DAX 公式) 執行的情況。 其特別適合用來判斷導致效能問題的原因是查詢還是視覺呈現。

## <a name="use-sql-server-profiler"></a>使用 SQL Server Profiler

您也可以使用 [SQL Server Profiler](/sql/tools/sql-server-profiler/sql-server-profiler) 來識別速度較慢的查詢。

> [!NOTE]
> SQL Server Profiler 是 [SQL Server Management Studio](/sql/ssms/download-sql-server-management-studio-ssms) 的一部分。

當您的資料來源為下列任一項目時，請使用 SQL Server Profiler：

- SQL Server
- SQL Server Analysis Services
- Azure Analysis Services

> [!CAUTION]
> Power BI Desktop 支援連線到診斷連接埠。 診斷連接埠允許其他工具的連線，並為診斷目的而執行追蹤。 不支援對 Power Desktop 資料模型進行任何變更。 對資料模型進行變更可能會導致損毀以及資料遺失。

若要建立 SQL Server Profiler 追蹤，請遵循這些指示：

1. 開啟您的 Power BI Desktop 報表 (如此一來，在下一個步驟中找出連接埠，關閉任何其他開啟的報表就很容易)。
1. 若要判斷 Power BI Desktop 所使用的連接埠，請在 PowerShell 中 (具有管理員權限)，或在命令提示字元中輸入下列命令：
    ```powershell
    netstat -b -n
    ```
    輸出應該是應用程式和其已開啟連接埠的清單。 尋找 **msmdsrv.exe** 所使用的連接埠，並加以記錄以供稍後使用。 這是您 Power BI Desktop 的執行個體。
1. 將 SQL Server Profiler 連線至您的 Power BI Desktop 報表：
    1. 開啟 SQL Server Profiler。
    1. 在 SQL Server Profiler 的 [檔案] 功能表上，選取 [新追蹤]。
    1. 針對 [伺服器類型]，選取 [Analysis Services]。
    1. 針對 [伺服器名稱]，輸入 _localhost:[先前記錄的連接埠]_ 。
    1. 按一下 [執行] - 現在，SQL Server Profiler 的追蹤已上線，而且正在主動分析 Power BI Desktop 查詢。
1. 當 Power BI Desktop 查詢執行時，您會看到其各自的持續期間和 CPU 時間。 視資料來源類型而定，您可能會看到指出查詢執行方式的其他事件。 您可以使用此資訊來判斷哪些查詢是瓶頸。

使用 SQL Server Profiler 的優點是可以儲存 SQL Server (關聯式) 資料庫追蹤。 追蹤可以變成 [Database Engine Tuning Advisor](/sql/relational-databases/performance/start-and-use-the-database-engine-tuning-advisor) 的輸入。 如此一來，您就可以收到如何微調資料來源的建議。

## <a name="monitor-premium-metrics"></a>監視 Premium 計量

針對 Power BI Premium 容量，可以使用 **Power BI Premium 計量應用程式** 來監視 Power BI Premium 訂用帳戶的健康情況與容量。 如需詳細資訊，請參閱 [Power BI Premium 計量應用程式](../admin/service-premium-metrics-app.md)。

## <a name="next-steps"></a>後續步驟

如需本文的詳細資訊，請參閱下列資源︰

- [查詢診斷](/power-query/QueryDiagnostics)
- [效能分析器](../create-reports/desktop-performance-analyzer.md)
- [針對 Power BI 中的報表效能問題進行疑難排解](report-performance-troubleshoot.md)
- [Power BI Premium 計量應用程式](../admin/service-premium-metrics-app.md)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com/)
