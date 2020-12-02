---
title: Power BI Desktop 中的自動日期/時間指引
description: 使用 Power BI Desktop 中自動日期/時間功能的指導方針。
author: peter-myers
ms.author: v-pemyer
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 10/23/2019
ms.openlocfilehash: ed99c48aaef116f58ebff0d8026b37938a39de3b
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96394581"
---
# <a name="auto-datetime-guidance-in-power-bi-desktop"></a>Power BI Desktop 中的自動日期/時間指引

本文的目標為開發 Power BI Desktop 中的「匯入」模型或「複合」模型的資料模型製作人員。 它提供在特定情況下使用 Power BI Desktop「自動日期/時間」上的指導方針、建議及考量。 如需「自動日期/時間」的概觀和一般簡介，請參閱 [Power BI Desktop 中的自動日期/時間](../transform-model/desktop-auto-date-time.md)。

[自動日期/時間] 選項能提供便利、快速且容易使用的時間智慧。 報表作者可以在對行事曆時間週期進行篩選、分組及向下鑽研時使用時間智慧。

## <a name="considerations"></a>考量

下列項目符號清單會描述與 [自動日期/時間] 選項相關的考量，以及可能的限制。

- **適用於全部或全部不適用：** 啟用 [自動日期/時間] 選項時，它會套用至不是關聯性 &quot;眾多&quot; 端之匯入資料表中的所有日期資料行上。 您無法以個別資料行為基礎來予以啟用或停用。
- **僅限行事曆週期：** [年] 和 [季] 資料行會與行事曆週期相關聯。 這代表年份會從 1 月 1 日開始，並於 12 月 31 日結束。 您無法自訂年份的開始 (或結束) 日期。
- **自訂：** 您無法自訂用來描述時間週期的值。 此外，您也無法新增其他資料行來描述其他時間週期 (例如週)。
- **年份篩選：** [季]、[月] 與 [日] 資料行值不會包含年份值。 例如，[月] 資料行只會包含月份名稱 (也就是一月、二月等)。 這些值並無法完全自我描述，且在某些報表設計中可能無法傳達年份篩選內容。

    這就是為何篩選或分組必須在 [年] 資料行上進行。 使用階層來向下鑽研時將會篩選年份，除非刻意移除 [年] 層級。 如果沒有依年份的篩選或分組，則以依月份的分組為例，將會彙總該月份於所有年間的值。
- **單一資料表日期篩選：** 由於每個日期資料行都會產生自己的 (隱藏) 自動日期/時間資料表，所以無法將時間篩選套用到某個資料表，然後再將它傳播到多個模型資料表上。 在對如銷售和銷售預算之類的多個主體 (事實類型資料表) 進行報告時，這種方式的篩選是常見的模型需求。 使用自動日期/時間時，報表作者必須將篩選套用到每個不同的日期資料行上。
- **模型大小：** 會產生隱藏自動日期/時間資料表的每個日期資料行都會導致模型大小增加，也會延長資料重新整理時間。
- **其他報告工具：** 在下列情況下無法使用自動日期/時間資料表：
  - 使用[在 Excel 中進行分析](../collaborate-share/service-analyze-in-excel.md)。
  - 使用 Power BI 編頁報表 Analysis Services 查詢設計工具。
  - 使用非 Power BI 的報表設計工具連線到模型。

## <a name="recommendations"></a>建議

我們建議您只在處理行事曆日期週期，以及具有與時間相關的簡單模型需求時，才將 [自動日期/時間] 選項保持開啟。 在您建立臨機操作模型或執行資料探索或分析時，使用此選項可能也會很方便。

當您的資料來源已經定義日期維度資料表時，便應該使用此資料表來一致地定義組織內的時間。 特別是在您的資料來源為資料倉儲的情況。 否則，您可以使用 DAX [CALENDAR](/dax/calendar-function-dax) 或 [CALENDARAUTO](/dax/calendarauto-function-dax) 函式來在模型中產生日期資料表。 您可以接著新增計算結果欄來支援已知時間篩選和分組需求。 此設計方法可能可以讓您建立能傳播至所有事實類型資料表的單一日期資料表，並可能可以產生套用時間篩選的單一資料表。 如需建立日期資料表的詳細資訊，請參閱[在 Power BI Desktop 中設定和使用日期資料表](../transform-model/desktop-date-tables.md)一文。

如果 [自動日期/時間] 選項與您的專案無關，我們建議您停用全域 [自動日期/時間] 選項。 這將能確保您建立的所有新 Power BI Desktop 檔案都不會啟用 [自動日期/時間] 選項。

## <a name="next-steps"></a>後續步驟

如需本文的詳細資訊，請參閱下列資源：

- [在 Power BI Desktop 中建立日期資料表](model-date-tables.md)
- [Power BI Desktop 中的自動日期/時間](../transform-model/desktop-auto-date-time.md)
- [在 Power BI Desktop 中設定和使用日期資料表](../transform-model/desktop-date-tables.md)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com/)
