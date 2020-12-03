---
title: 使用 Power BI Desktop 中的導出資料表
description: Power BI Desktop 中的導出資料表
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: how-to
ms.date: 05/06/2020
LocalizationGroup: Model your data
ms.openlocfilehash: de919d5dc72ec4c9f1939d844a1cd287728f1ac8
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415902"
---
# <a name="create-calculated-tables-in-power-bi-desktop"></a>在 Power BI Desktop 中建立計算資料表
大多時候，您會從外部資料來源將資料匯入模型中，以建立資料表。 但是「計算資料表」可讓您根據已載入模型中的資料來新增資料表。 您會建立[資料分析運算式 (DAX)](/dax/index) 公式來定義資料表的值，而不是從資料來源查詢值並將其載入新的資料表資料行。

如同在 Power BI Desktop 中，DAX 是用來處理關聯式資料的公式語言。 DAX 所包含的程式庫是由 200 個以上的函數、運算子和建構函式所組成，為建立公式提供極大的彈性，可計算幾乎所有資料分析需求的結果。 計算資料表最適合用於中繼計算及要當做模型一部分儲存的資料，而不是即時計算的資料表或作為查詢結果一部分的資料表。 例如，您可選擇「聯集」或「交叉聯結」兩個現有資料表。

計算資料表就如同其他 Power BI Desktop 資料表，可以與其他資料表建立關聯。 計算資料表中的資料行具有資料類型、格式，並可能屬於某種資料類別。 您可以為資料行指定任何名稱，並將其加入報表視覺效果，就像是其他欄位一樣。 如果其提取資料的任何來源資料表已重新整理或已更新，則會重新計算導出資料表，除非該資料表所使用的資料來自使用 DirectQuery 的資料表；在使用 DirectQuery 的案例中，該資料表將會在資料集重新整理之後反映變更。 如果資料表需要使用 DirectQuery，最好也在 DirectQuery 中具有導出資料表。

## <a name="create-a-calculated-table"></a>建立計算資料表

您可以使用 Power BI Desktop 的 [報表檢視] 或 [資料檢視] 中的 [新增資料表] 功能來建立計算資料表。

例如，假設您是人事經理，具有 [西北部員工] 資料表和另一個 [西南部員工] 資料表。 您想要將這兩個資料表合併成一個名為 [西區員工] 的單一資料表。

**西北部員工**

 ![Power BI Desktop 的螢幕擷取畫面，其中顯示西南部員工的表格式資料。](media/desktop-calculated-tables/calctables_nwempl.png)

**西南部員工**

 ![Power BI Desktop 的螢幕擷取畫面，其中顯示西南部員工的表格式資料。](media/desktop-calculated-tables/calctables_swempl.png)

在 Power BI Desktop 的 [報表檢視] 或 [資料檢視] 中，於 [模型化] 索引標籤的 [計算] 群組中，選取 [新增資料表]。 在 [資料檢視] 中執行起來比較簡單，因為您可立即查看您的新計算資料表。

 ![資料檢視中的新資料表](media/desktop-calculated-tables/calctables_formulabarempty.png)

在公式列中輸入下列公式：

```dax
Western Region Employees = UNION('Northwest Employees', 'Southwest Employees')
```

名為 [西區員工] 的新資料表隨即建立，且就像任何其他資料表一樣出現在 [欄位] 窗格中。 就如同其他任何資料表，您可以建立與其他資料表的關聯性、新增量值和計算結果欄，以及將欄位新增至報表。

 ![新增計算資料表](media/desktop-calculated-tables/calctables_westregionempl.png)

 ![[欄位] 窗格中的新資料表](media/desktop-calculated-tables/calctables_fieldlist.png)

## <a name="functions-for-calculated-tables"></a>導出資料表的函數

您可以透過任何傳回資料表的 DAX 運算式來定義計算資料表，包括另一個資料表的簡單參照。 例如：

```dax
New Western Region Employees = 'Western Region Employees'
```

本文只提供計算資料表的快速簡介。 您可以搭配 DAX 使用導出資料表，來解決許多分析問題。 以下是您可能使用的一些較常見的 DAX 資料表函式：

* DISTINCT
* VALUES
* CROSSJOIN
* UNION
* NATURALINNERJOIN
* NATURALLEFTOUTERJOIN
* INTERSECT
* CALENDAR
* CALENDARAUTO

如需這些和其他傳回資料表的 DAX 函式，請參閱 [DAX 函式參考](/dax/dax-function-reference)。

