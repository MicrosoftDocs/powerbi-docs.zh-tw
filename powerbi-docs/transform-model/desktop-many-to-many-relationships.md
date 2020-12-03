---
title: Power BI Desktop 中的多對多關聯性
description: 在 Power BI Desktop 中搭配多對多基數使用關聯性
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: conceptual
ms.date: 12/19/2019
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 5f64a9a896fbb5ea3e080e1d07f6cc7d980430b8
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415695"
---
# <a name="apply-many-many-relationships-in-power-bi-desktop"></a>在 Power BI Desktop 中套用多對多關聯性

使用 Power BI Desktop 中的「多對多基數關聯性」  ，您可以聯結使用「多對多」  基數的資料表。 您可以更輕鬆並更直覺的建立包含兩個或多個資料來源的資料模型。 「複合模型」  功能是 Power BI Desktop 中的大型功能，而「多對多基數關聯性」  則是其中的一部分。

![Power BI Desktop、[編輯關聯性] 窗格中的多對多關聯性](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

Power BI Desktop 的「多對多基數關聯性」  是由三個相關功能的其中一項所組成：

* **複合模型**：「複合模型」  允許報表可有兩個以上任意組合的資料連線，包括 DirectQuery 連線或匯入。 如需詳細資訊，請參閱[在 Power BI Desktop 中使用複合模型](desktop-composite-models.md)。

* **多對多基數關聯性**：您可以使用複合模型在資料表之間建立「多對多基數關聯性」  。 此方法會移除資料表中唯一值的需求。 此方法也會移除先前的因應措施，像是只為建立關聯性而導入新的資料表。 本文中進一步說明此功能。

* **儲存模式**：您現在可以指定哪些視覺效果必須查詢後端資料來源。 不需要查詢的視覺效果，即便是使用 DirectQuery，也同樣會匯入。 此功能可提升效能，並減輕後端的負載。 以往，即使像是交叉分析篩選器這類的簡單視覺效果，也會起始傳送到後端來源的查詢。 如需詳細資訊，請參閱 [Power BI Desktop 中的儲存模式](desktop-storage-mode.md)。

## <a name="what-a-relationship-with-a-many-many-cardinality-solves"></a>多對多基數關聯性解決的問題

在可使用「多對多基數關聯性」  之前，兩個資料表之間的關聯性是在 Power BI 中定義的。 關聯性中必須至少有一個資料表資料行包含唯一的值。 但是通常不會有任何資料行包含唯一的值。

例如，兩個資料表可能有標示為 Country 的資料行。 不過，任一資料表中的 Country 值都不是唯一的。 若要聯結這類資料表，您必須建立因應措施。 其中一個因應措施可能是引進具有所需唯一值的額外資料表。 使用「多對多基數關聯性」  時，如果您使用具有「多對多」  基數的關聯性，便可直接聯結這類資料表。

## <a name="use-relationships-with-a-many-many-cardinality"></a>使用多對多基數關聯性

當您定義 Power BI 中兩個資料表之間的關聯性時，您必須定義關聯性的基數。 例如，ProductSales 和 Product 之間的關聯性 (使用資料行 ProductSales[ProductCode] 和 Product[ProductCode]) 便會定義為「多對一」  。 我們會以此方式定義關聯性是因為每一項產品都有多項銷售額，且 Product 資料表中資料行 (ProductCode) 是唯一的。 當您將關聯性基數定義為「多對一」  、「一對多」  或「一對一」  時，Power BI 便會進行驗證，因此您選取的基數會符合實際資料。

例如，請查看下圖的簡單模型：

![Power BI Desktop、關聯性檢視、ProductSales 和 Product 資料表](media/desktop-many-to-many-relationships/many-to-many-relationships_02.png)

現在，想像 **Product** 資料表只會顯示兩個資料列，如下所示：

![Power BI Desktop、具有兩個資料列的 Product 資料表視覺效果](media/desktop-many-to-many-relationships/many-to-many-relationships_03.png)

另外，想像 Sales 資料表只有四個資料列，其中包含產品 C 的資料列。由於發生參考完整性錯誤之故，產品 C 資料列在 **Product** 資料表上並不存在。

![Power BI Desktop、具有四個資料列的 Sales 資料表視覺效果](media/desktop-many-to-many-relationships/many-to-many-relationships_04.png)

**ProductName** 與 **Price** (來自 **Product** 資料表) 以及每種產品 **Qty** 總計 (來自 ProductSales 資料表) 會顯示如下：

![Power BI Desktop、顯示產品名稱、價格和數量的視覺效果](media/desktop-many-to-many-relationships/many-to-many-relationships_05.png)

如同先前影像中所示，有一個空白的 **ProductName** 資料列與產品 C 銷售建立關聯。此空白資料列會導致下列情況：

* **ProductSales** 資料表中的任何資料列沒有存在於 **Product** 資料表中的對應資料列。 發生參考完整性問題，如同我們在此範例中所看到的產品 C。

* **ProductSales** 資料表中任何資料列的外部索引鍵資料行為 Null。

基於上述原因，兩個案例中的空白資料行都會導致 **ProductName** 和 **Price** 未知的銷售。

有時候，資料表是透過兩個資料行聯結，但沒有任何一個是唯一的資料行。 例如，以這兩個資料表為例：

* **Sales** 資料表會依 **State** 顯示銷售資料，每個資料列都包含該州某個銷售類型的銷售量。 州包括加州 (CA)、華盛頓州 (WA)、德州 (TX)。

    ![Power BI Desktop、依州顯示銷售額的 Sales 資料表](media/desktop-many-to-many-relationships/many-to-many-relationships_06.png)

* **CityData** 資料表會顯示城市的資料，包括人口與州 (例如加州 (CA)、華盛頓州 (WA) 及紐約州 (New York))。

    ![Power BI Desktop、顯示城市、州和人口的 Sales 資料表](media/desktop-many-to-many-relationships/many-to-many-relationships_07.png)

**State** 的資料行現在已在這兩個資料表中。 您可以依照州和每州的總人口，合理地報告兩個總銷售額。 不過，有一個問題：**State** 資料行在任一資料表中都不是唯一的。

## <a name="the-previous-workaround"></a>先前的因應措施

在 2018 年 7 月之前發行的 Power BI Desktop 版本中，您無法建立這些資料表之間的直接關聯性。 常見的因應措施如下：

* 建立第三個資料表，其中只包含唯一的 State 識別碼。 資料表可以是下列項目的任何一項或全部：
  * 計算資料表 (使用資料分析運算式 [DAX] 定義)。
  * 以查詢編輯器中定義查詢為基礎的資料表，可顯示從其中一個資料表取得的唯一識別碼。
  * 合併的完整集。

* 然後透過使用常見的「多對一」  關聯性，將兩個原始資料表與新的資料表建立關聯。

您可以讓因應措施資料表保持可見。 您也可以隱藏因應措施資料表，使其不會出現在 [欄位]  清單中。 若您隱藏資料表，「多對一」  關聯性常會設為雙向篩選，且您可使用來自任一資料表的 State 欄位。 後續的交叉篩選會散佈至另一個資料表。 以下影像會顯示該方法：

![Power BI Desktop、關聯性檢視、隱藏的 State 資料表](media/desktop-many-to-many-relationships/many-to-many-relationships_08.png)

接著，顯示 **State** (來自 **CityData** 資料表) 以及 **Population** 總計與 **Sales** 總計的視覺效果會出現如下：

![顯示具有狀態、人口和銷售資料的資料表螢幕擷取畫面。](media/desktop-many-to-many-relationships/many-to-many-relationships_09.png)

> [!NOTE]
> 因為此因應措施中使用來自 **CityData** 資料表的州，所以只會列出該資料表中的州，因此會排除德州 (TX)。 此外，和「多對一」  關聯性不同，雖然總計資料列包含所有 **Sales** (包括德州 (TX) 的銷售額)，但詳細資料不包括涵蓋這類不相符資料列的空白資料列。 同樣地，也沒有空白資料列涵蓋 **State** 值為 Null 的任何 **Sales**。

假設您也將 City 新增至該視覺效果。 雖然已知每個 City 的人口，但針對 City 顯示的 **Sales** 卻只會重複對應 **State** 的 **Sales**。 當資料行群組與某個彙總量值無關時，通常會發生這種情況，如下所示：

![Power BI Desktop、州、城市人口和銷售額](media/desktop-many-to-many-relationships/many-to-many-relationships_10.png)

假設您在這裡將新 Sales 資料表定義為所有 State 的組合，並使其顯示在 [欄位]  清單中。 相同的視覺效果會顯示 **State** (在新的資料表上)、總 **Population**，以及總 **Sales**：

![Power BI Desktop、州、人口和銷售額視覺效果](media/desktop-many-to-many-relationships/many-to-many-relationships_11.png)

如您所見，TX (其附帶 **Sales** 資料但 *Population* 資料未知) 及 New York (其 **Population** 已知但沒有任何 **Sales**) 會包含在其中。 此因應措施並非最佳方法，且有許多問題。 若為多對多基數關聯性，可以解決所產生的問題，如下一節中所述。

## <a name="use-a-relationship-with-a-many-many-cardinality-instead-of-the-workaround"></a>使用多對多基數關聯性取代因應措施

從 Power BI Desktop 的 2018 年 7 月版本開始，您可以直接關聯資料表 (例如我們先前所述的資料表) 而無須訴諸類似的因應措施。 現在可以將關聯性基數設為「多對多」  。 此設定指出沒有任何資料表包含唯一值。 針對這類關聯性，您仍然可以控制哪個資料表會篩選另一個資料表。 或者，您也可以套用雙向篩選，其中每個資料表都會篩選另一個資料表。

在 Power BI Desktop 中，當確定資料表都未在關聯性資料行中包含唯一值時，基數會預設為「多對多」  。 在這種情況下，會出現警告訊息，確認您想要設定關聯性，且變更不是資料問題的非預期效果。

例如，當您直接建立 CityData 與 Sales 之間的關聯性 (其中的篩選條件應從 CityData 流至 Sales) 時，Power BI Desktop 會顯示 [編輯關聯性]  視窗：

![Power BI Desktop、編輯關聯性對話方塊](media/desktop-many-to-many-relationships/many-to-many-relationships_01.png)

產生的 [關聯性]  檢視會顯示兩個資料表之間的直接多對多關聯性。 [欄位]  清單中資料表外觀及其在建立視覺效果之後的後續行為，都會與我們套用因應措施時相似。 在因應措施中，顯示相異 State 資料的額外資料表並未設為可見。 如先前所述，會顯示出現 **State**、**Population** 和 **Sales** 資料的視覺效果：

![Power BI Desktop、State、Population 和 Sales 資料表](media/desktop-many-to-many-relationships/many-to-many-relationships_12.png)

「多對多基數關聯性」  和更典型的「多對一」  關聯性，兩者的主要差異如下：

* 顯示的值不包含導致另一個資料表中不相符資料列的空白資料列。 此外，當在另一個資料表關聯性中使用的資料行為 Null 時，也不會代表資料列的值。
* 您無法使用 `RELATED()` 函式，因為可和一個以上的資料列建立關聯。
* 在其中一個資料表上使用 `ALL()` 函式不會移除套用到另一個以多對多關聯性相關資料表的篩選條件。 在先前範例中，如下所示所定義量值不會移除對相關 CityData 資料表中資料行的篩選條件：

    ![指令碼範例](media/desktop-many-to-many-relationships/many-to-many-relationships_13.png)

    顯示 **State**、**Sales** 及 **Sales total** 資料的視覺效果會產生此圖表：

    ![資料表視覺效果](media/desktop-many-to-many-relationships/many-to-many-relationships_14.png)

考慮上述差異，請務必確認使用 `ALL(<Table>)` 的計算 (例如 *% of grand total*) 傳回的是所想結果。

## <a name="limitations-and-considerations"></a>限制與考量

這一版的「多對多基數關聯性」  和複合模型有一些限制。

下列 Live Connect (多維度) 來源不能與複合模型搭配使用：

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Power BI 資料集
* Azure Analysis Services

當您使用 DirectQuery 連線到這些多維度來源時，即無法連線到其他 DirectQuery 來源，也無法與匯入的資料合併。

使用「多對多基數關聯性」  時，使用 DirectQuery 的現有限制仍然適用。 許多限制現在會依每個資料表而不同，視資料表的儲存模式而定。 例如，已匯入資料表上的計算結果欄可以參考其它資料表，但 DirectQuery 資料表上的計算結果欄仍僅能參考相同資料表上的資料行。 如果模型內有任何資料表為 DirectQuery，則其他限制會套用至整個模型。 例如，若某個模型內的任何資料表具有 DirectQuery 儲存模式，則該模型不提供 QuickInsights 和問與答功能。

## <a name="next-steps"></a>後續步驟

如需複合模型及 DirectQuery 的詳細資訊，請參閱下列文章：
* [在 Power BI Desktop 中使用複合模型](desktop-composite-models.md)
* [Power BI Desktop 中的儲存模式](desktop-storage-mode.md)
* [使用 Power BI 的 DirectQuery](../connect-data/desktop-directquery-about.md)
* [Power BI 資料來源](../connect-data/power-bi-data-sources.md)
