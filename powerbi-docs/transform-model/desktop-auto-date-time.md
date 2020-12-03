---
title: Power BI Desktop 中的自動日期/時間
description: 了解 Power BI Desktop 中的自動日期/時間功能。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: how-to
ms.date: 10/23/2019
ms.openlocfilehash: 24972026d7121809ac71c6c8352a147af38ad5be
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96416017"
---
# <a name="apply-auto-datetime-in-power-bi-desktop"></a>在 Power BI Desktop 中套用自動日期/時間

本文的目標為開發 Power BI Desktop 中的「匯入」模型或「複合」模型的資料模型製作人員。 其引進並描述 [自動日期/時間] 選項。

[自動日期/時間] 是 Power BI Desktop 中的資料載入選項。 此選項的目的是要根據載入至模型中的日期資料行，支援便利的時間智慧報表。 具體而言，其可讓報表作者使用資料模型透過行事曆時間期間 (年、季、月和日) 來篩選、分組及向下鑽研。 重要的是，您不需要明確地開發這些時間智慧功能。

啟用此選項時，假設下列所有條件皆為 true，則 Power BI Desktop 為每個日期資料行建立隱藏的自動日期/時間資料表：

- 資料表儲存模式為匯入
- 資料行資料類型是日期或日期/時間
- 資料行不是模型關聯性的「多」端

## <a name="how-it-works"></a>運作方式

每個自動日期/時間資料表實際上都是[計算資料表](desktop-calculated-tables.md)，會使用 DAX [CALENDAR](/dax/calendar-function-dax) 函數來產生資料列。 每個資料表也包含六個計算結果欄：**Day**、**MonthNo**、**Month**、**QuarterNo**、**Quarter** 和 **Year**。

> [!NOTE]
> Power BI 會根據[模型語言](../fundamentals/supported-languages-countries-regions.md#choose-the-language-for-the-model-in-power-bi-desktop)來翻譯及格式化資料行名稱和值。 例如，若模型是使用英文建立的，其就會以英文顯示月份名稱等，即使是在韓文用戶端中檢視也一樣。

Power BI Desktop 也會在自動日期/時間資料表的 [資料] 資料行與模型日期資料行之間建立關聯性。

自動日期/時間資料表包含完整的行事曆年度，內含儲存在模型日期資料行中的所有日期值。 例如，若日期資料行中最早的值是 2016 年 3 月 20 日，而最新的值是 2019 年10 月 23日，則此資料表會包含 1,461 個資料列。 每一個資料列會代表 2016 年到 2019 年的四個行事曆年份中的每個日期。 當 Power BI 重新整理模型時，每個自動日期/時間資料表也會重新整理。 如此一來，模型一律會包含日期資料行值所包含的日期。

如果可以看到自動日期/時間資料表的資料列，其外觀將如下所示：

![自動日期/時間資料表的資料列外觀的範例。 顯示七個資料行：Date、Day、MonthNo、Month、QuarterNo、Quarter 和 Year。 顯示 10 個資料列，描述從 2019 年 1 月 1 日到 2019 年 1 月 10 日的日期。](media/desktop-auto-date-time/auto-date-time-hidden-table-example-rows.png)

> [!NOTE]
> 自動日期/時間資料表會永久隱藏，即使是來自模型製作人員也一樣。 在 [欄位] 窗格或 [模型檢視] 圖表中看不到它們，也無法在資料檢視中看到其資料列。 此外，DAX 運算式不能直接參考該資料表和其資料行。
>
> 此外，如果您以[使用 Excel 分析](../collaborate-share/service-analyze-in-excel.md)或 Power BI 以外的報表設計工具來連線至模型時，您將無法使用這些項目。

資料表也會定義階層，提供視覺效果，並具有透過年、季、月和日層級的向下切入路徑。

如果可以在模型檢視圖表中看到自動日期/時間資料表，則其外觀將如下所示 (醒目提示相關資料行)：

![隱藏的自動日期/時間資料表外觀的範例。 顯示兩個資料表：Sales 和 LocalDateTime 資料表。 這些資料表是根據 Sales 資料表的 OrderDate 資料行和 LocalDateTime 資料表 Date 資料行來相關聯。 LocalDateTime 會定義七個資料行：Date、Day、Month、MonthNo、Quarter、QuarterNo、Year 和單一階層。 階層為指定的「日期階層」，且由四個層級所組成：Year、Quarter、Month 和 Day。](media/desktop-auto-date-time/auto-date-time-hidden-table-example-diagram.png)

## <a name="work-with-auto-datetime"></a>使用自動日期/時間

當日期資料行有自動日期/時間資料表 (而且該資料行可見)，報表作者將不會在 [欄位] 窗格中，找到欄位形式的該資料行。 相反地，他們會找到具有日期資料行名稱的可展開物件。 您可以輕鬆地識別它，因為它帶有行事曆圖示裝飾。 當報表作者展開行事曆物件時，他們會找到名為 **日期階層** 的階層。 展開階層之後，即可找到四個層級：**Year**、**Quarter**、**Month** 和 **Day**。

![[欄位] 窗格的範例，其中開啟了已展開的 Sales 資料表。 它包含 OrderDate 欄位，該欄位帶有行事曆圖示裝飾。 它已展開並開啟，並包含名為「日期階層」的階層。 它也會展開並包含四個層級：Year、Quarter、Month 和 Day。](media/desktop-auto-date-time/auto-date-time-fields-pane-example.png)

自動日期/時間產生的階層可用來以與一般階層可以使用的完全相同方式設定視覺效果。 您可以使用整個「日期階層」階層，或階層的特定層級來設定視覺效果。

不過，一般階層並不支援其中一項新增的功能。 將自動日期/時間階層 (或來自階層的層級) 新增至視覺效果庫時，報表作者可在使用階層或日期資料行之間切換。 此方法對某些視覺效果很有意義，前提是他們只需要日期資料行，而非是階層和其層級。 他們會從設定視覺效果欄位開始 (以滑鼠右鍵按一下視覺效果欄位，或按一下向下箭號)，然後使用操作功能表在日期資料行或日期階層之間切換。

![OrderDate 階層視覺效果欄位設定的範例。 開啟內容功能表會顯示兩個選項，允許切換使用 OrderDate 資料行或「日期階層」。](media/desktop-auto-date-time/auto-date-time-configure-visuals-fields.png)

最後，以 DAX 撰寫的模型計算可以「直接」參考日期資料行，或「間接」參考隱藏的自動日期/時間資料表資料行。

以 Power BI Desktop 撰寫的公式可以使用一般方式來參考日期資料行。 不過，您必須使用特殊的擴充語法來參考自動日期/時間資料表資料行。 您會從參考日期資料行開始，然後後面接著句點 (.)。 接著，公式列自動完成將允許您從自動日期/時間資料表中選取資料行。

![在公式列中輸入 DAX 量值運算式的範例。 公式目前為止會讀取 Date Count = COUNT(Sales[OrderDate])。 而自動完成清單會呈現來自隱藏的自動日期/時間資料表的所有七個資料行。 這些資料行為：Date、Day、Month、MonthNo、Quarter、QuarterNo 和 Year。](media/desktop-auto-date-time/auto-date-time-dax-auto-complete.png)

在 Power BI Desktop 中，有效的量值運算式可以讀取：

```dax
Date Count = COUNT(Sales[OrderDate].[Date])
```

> [!NOTE]
> 雖然此量值運算式在 Power BI Desktop 中有效，但它不是正確的 DAX 語法。 就內部而言，Power BI Desktop 會將您的運算式轉置，以參考 true (隱藏) 自動日期/時間資料表資料行。

## <a name="configure-auto-datetime-option"></a>設定自動日期/時間選項

您可以「全域」或針對「目前檔案」設定自動日期/時間。 全域選項適用於新的 Power BI Desktop 檔案，而且可以隨時開啟或關閉。 針對 Power BI Desktop 的新安裝，這兩個選項都會預設開啟。

目前的檔案選項也可以隨時開啟或關閉。 開啟時，會建立自動日期/時間資料表。 關閉時，會從模型中移除任何自動日期/時間資料表。

> [!CAUTION]
> 關閉目前檔案選項時請小心，因為這會移除自動日期/時間資料表。 請務必修正並中斷已設定為使用它們的任何報表篩選或視覺效果。

在 Power BI Desktop 中，選取 [檔案] > [選項及設定] > [選項]，然後選取 [全域] 或 [目前檔案] 頁面。 在任一頁面上，該選項會存在於 [時間智慧] 區段中。

![設定 Power BI Desktop 選項。 已選取來自 GLOBAL 群組的 [資料載入] 頁面。 在 [時間智慧] 區段中，會勾選 [自動為新檔案建立日期/時間] 選項。](media/desktop-auto-date-time/auto-date-time-configure-global-options.png)

## <a name="next-steps"></a>後續步驟

如需本文的詳細資訊，請參閱下列資源：

- [Power BI Desktop 中的自動日期/時間指導方針](../guidance/auto-date-time.md)
- [在 Power BI Desktop 中建立日期資料表](../guidance/model-date-tables.md)
- [在 Power BI Desktop 中設定和使用日期資料表](desktop-date-tables.md)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com/)
