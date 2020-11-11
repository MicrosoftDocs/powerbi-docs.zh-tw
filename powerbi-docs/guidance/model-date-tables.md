---
title: 在 Power BI Desktop 中建立日期資料表
description: 在 Power BI Desktop 中建立日期資料表的技術和指導方針。
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/24/2020
ms.author: v-pemyer
ms.openlocfilehash: 350d4889643556d4e1c6389580415ccba46b55d4
ms.sourcegitcommit: 37bd34053557089c4fbf0e05f78e959609966561
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94396625"
---
# <a name="create-date-tables-in-power-bi-desktop"></a>在 Power BI Desktop 中建立日期資料表

此文章以使用 Power BI Desktop 的資料模型製作人員為目標。 其中描述在您的資料模型中建立日期資料表的良好設計做法。

若要使用資料分析運算式 (DAX) [時間智慧函式](/dax/time-intelligence-functions-dax)，則有必要的模型需求：您的模型中至少必須有一個「日期資料表」。 日期資料表是符合下列需求的資料表：

> [!div class="checklist"]
> - 其必須具有資料類型 [日期] (或 [日期/時間]) 的資料行，也稱為「日期資料行」。
> - 日期資料行必須包含唯一值。
> - 日期資料行不能包含「空白」。
> - 日期資料行不能有任何遺漏的日期。
> - 日期資料行必須涵蓋整年。 一年不一定是日曆年度 (一月至十二月)。
> - 日期資料表必須[標示為日期資料表](../transform-model/desktop-date-tables.md#setting-your-own-date-table)。

您可以使用下列任何一種方法，將日期資料表加入至您的模型：

- 自動日期/時間選項
- 連線到日期維度資料表的 Power Query
- 產生日期資料表的 Power Query
- 產生日期資料表的 DAX
- 複製現有的資料庫的 DAX

> [!TIP]
> 日期資料表可能是您要新增至任何模型中的最一致的功能。 此外，在組織內應一致地定義日期資料表。 因此，無論您決定使用哪一種技術，我們都建議您建立 [Power BI Desktop 範本](../create-reports/desktop-templates.md)，其中包含完整設定的日期資料表。 將範本與您組織中的所有模組工具共用。 因此，每當有人開發新的模型時，就可以從一致定義的日期資料表開始。

## <a name="use-auto-datetime"></a>使用自動日期/時間

[[自動日期/時間]](../transform-model/desktop-auto-date-time.md) 選項能提供便利、快速且容易使用的時間智慧。 報表作者可以在對行事曆時間週期進行篩選、分組及向下鑽研時使用時間智慧。

我們建議您只在處理行事曆日期週期，以及具有與時間相關的簡單模型需求時，才將 [自動日期/時間] 選項保持開啟。 在您建立臨機操作模型或執行資料探索或分析時，使用此選項可能也會很方便。 不過，這種方法並不支援可將篩選條件傳播到多個資料表的單一日期資料表設計。 如需詳細資訊，請參閱 [Power BI Desktop 中的自動日期/時間指導方針](auto-date-time.md)。

## <a name="connect-with-power-query"></a>使用 Power Query 進行連線

當您的資料來源已經有日期資料表時，建議您將其作為模型日期資料表的來源使用。 當您連線到資料倉儲時通常是這種情況，因為其會有日期維度資料表。 如此一來，您的模型就會在您的組織中針對時間運用單一事實來源。

如果您正在開發 DirectQuery 模型，而您的資料來源未包含日期資料表，我們強烈建議您將日期資料表新增至資料來源。 其應該符合日期資料表的所有模型需求。 然後，您可以使用 Power Query 連線到日期資料表。 如此一來，您的模型計算就可以運用 DAX 時間智慧功能。

## <a name="generate-with-power-query"></a>使用 Power Query 產生

您可以使用 Power Query 產生日期資料表。 以下兩個部落格項目會為您示範：

- [使用 Power Query 指令碼建立日期維度](https://www.mattmasson.com/2014/02/creating-a-date-dimension-with-a-power-query-script/) \(英文\)，作者：Matt Masson
- [在 Power Query 中產生日期維度資料表](https://blog.crossjoin.co.uk/2013/11/19/generating-a-date-dimension-table-in-power-query/) \(英文\)，作者：Chris Webb

> [!TIP]
> 如果您的組織中沒有資料倉儲或其他一致的時間定義，請考慮使用 Power Query 來發佈[資料流程](../transform-model/dataflows/dataflows-introduction-self-service.md)。 然後，讓所有資料模組工具都連線到資料流程，以將日期資料表新增至其模型。 資料流程會成為組織中時間的單一事實來源。

如果您需要產生日期資料表，請考慮使用 DAX 來進行。 您可能會發現這樣比較容易。 此外，可能更方便，因為 DAX 包含一些內建的智慧功能，可簡化建立及管理日期資料表的工作。

## <a name="generate-with-dax"></a>使用 DAX 產生

您可以在模型中產生日期資料表，方法是使用 [CALENDAR](/dax/calendar-function-dax) 或 [CALENDARAUTO](/dax/calendarauto-function-dax) DAX 函式來建立導出資料表。 每個函式都會傳回日期的單欄資料表。 接著，您可以使用導出資料行來擴充導出資料表，以支援您的日期間隔篩選和群組需求。

- 當您想要定義日期範圍時，請使用 **CALENDAR** 函式。 您會傳入兩個值：開始日期和結束日期。 這些值可以由其他 DAX 函式 (例如 `MIN(Sales[OrderDate])` 或 `MAX(Sales[OrderDate])`) 來定義。
- 當您想要讓日期範圍自動包含儲存在模型中的所有日期時，請使用 **CALENDARAUTO** 函式。 您可以傳入單一選擇性參數，也就是年份的結束月份 (如果您的年份是日曆年度，其結束時間為十二月，您就不需要傳入值)。 這是很有用的函式，因為其可確保會傳回整年的日期，這是標示日期資料表的要求。 此外，您無需設法將資料表延伸到未來幾年：當資料重新整理完成時，其會觸發資料表的重新計算。 當新年份的日期載入至模型時，重新計算會自動擴充資料表的日期範圍。

## <a name="clone-with-dax"></a>使用 DAX 複製

當您的模型已經有日期資料表，而且您需要額外的日期資料表時，您可以輕鬆地複製現有的日期資料表。 當日期為[角色扮演維度](star-schema.md#role-playing-dimensions)時，情況就是這樣。 您可以藉由建立導出資料表來複製資料表。 導出資料表運算式就是現有日期資料表的名稱。

## <a name="next-steps"></a>後續步驟

如需本文的詳細資訊，請參閱下列資源：

- [Power BI Desktop 中的自動日期/時間](../transform-model/desktop-auto-date-time.md)
- [Power BI Desktop 中的自動日期/時間指導方針](auto-date-time.md)
- [在 Power BI Desktop 中設定和使用日期資料表](../transform-model/desktop-date-tables.md)
- [Power BI 中的自助資料準備](../transform-model/dataflows/dataflows-introduction-self-service.md)
- [CALENDAR 函式 (DAX)](/dax/calendar-function-dax)
- [CALENDARAUTO 函式 (DAX)](/dax/calendarauto-function-dax)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com/)