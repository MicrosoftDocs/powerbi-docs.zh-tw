---
title: 作用中與非作用中關聯性指導方針
description: 使用作用中或非作用中模型關聯性的指導方針。
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 03/02/2020
ms.openlocfilehash: 1d872aadf8258bd43114075477f2c37638f1f295
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99087261"
---
# <a name="active-vs-inactive-relationship-guidance"></a>作用中與非作用中關聯性指導方針

此文章以使用 Power BI Desktop 的資料模型製作人員為目標。 其提供您有關何時建立作用中或非作用中模型關聯性的指導方針。 根據預設，作用中關聯性會將篩選條件傳播到其他資料表。 不過，非作用中關聯性只會在 DAX 運算式啟動 (使用) 關聯性時傳播篩選條件。

[!INCLUDE [relationships-prerequisite-reading](includes/relationships-prerequisite-reading.md)]

## <a name="active-relationships"></a>作用中關聯性

一般來說，我們建議您盡可能定義作用中關聯性。 其擴大報表作者和問與答使用者使用您模型的範圍和潛力。

請考慮設計用來分析航班準時效能 (OTP) 的匯入模型範例。 該模型有一個 **Flight** 資料表，其為事實類型資料表，每個航班都儲存在一個資料列。 每個資料列都記錄航班日期、航班編號、起飛和抵達的機場，以及任何延遲時間 (以分鐘為單位)。 另外還有 **Airport** 資料表，其為維度類型資料表，每個機場都儲存在一個資料列。 每個資料列都會描述機場代碼、機場名稱與國家/地區。

以下是這兩個資料表的部分模型圖表。

![此圖顯示包含兩個資料表的模型：Flight 與 Airport。 下列段落描述關聯性設計。](media/relationships-active-inactive/flight-model-1.png)

**Flight** 與 **Airport** 資料表之間有兩個模型關聯性。 在 **Flight** 資料表中，**DepartureAirport** 和 **ArrivalAirport** 資料行與 **Airport** 資料表的 **Airport** 資料行相關。 在星狀結構描述設計中，**Airport** 資料表是描述為 [角色扮演維度](star-schema.md#role-playing-dimensions)。 在此模型中，這兩個角色是「起飛機場」與「抵達機場」。

雖然這種設計適用於關聯式星狀結構描述設計，但不適用於 Power BI 模型。 這是因為模型關聯性是篩選條件傳播的路徑，且這些路徑必須具確定性。 基於這個理由，模型在兩個資料表之間不能有多個作用中關聯性。 因此，一個關聯性為作用中，而另一個為非作用中 (以虛線表示)，如此範例中所述。 具體而言，作用中的是 **ArrivalAirport** 資料行的關聯性。 這表示套用至 **Airport** 資料表的篩選條件會自動傳播至 **Flight** 資料表的 **ArrivalAirport** 資料行。

此模型設計會對資料報告方式施加嚴格的限制。 具體而言，您無法篩選 **Airport** 資料表來自動分離起飛機場的航班詳細資料。 因為報告需求「同時」涉及起飛與抵達機場的篩選條件 (或分組)，所以需要兩個作用中關聯性。 將此需求轉譯為 Power BI 模型設計，表示模型必須有兩個機場資料表。

以下是已改善的模型設計。

![此圖顯示包含四個資料表的模型：Date、Flight、Departure Airport 與 Arrival Airport。](media/relationships-active-inactive/flight-model-2.png)

該模型現在有兩個機場資料表：**Departure Airport** 與 **Arrival Airport**。 這些資料表與 **Flight** 資料表之間的模型關聯性為作用中。 另請注意，**Departure Airport** 與 **Arrival Airport** 資料表中的資料行名稱前面會加上 _Departure_ 或 _Arrival_ 一字。

已改善的模型設計支援產生下列報表設計。

![此圖顯示包含兩個交叉分析篩選器與一個資料表視覺效果的報表頁面。 交叉分析篩選器為 [月份] 與 [起飛機場]。](media/relationships-active-inactive/flight-report-design.png)

報表頁面是依墨爾本為起飛機場進行篩選，並依抵達機場將表格視覺效果分組。

> [!NOTE]
> 針對匯入模型，額外的資料表已導致模型大小增加，且重新整理時間更長。 因此，其與[匯入模型化的資料縮減技術](import-modeling-data-reduction.md)一文中所述的建議相衝突。 不過，在範例中，只具有作用中關聯性的需求會覆寫這些建議。
>
> 此外，維度類型資料表包含的資料列數，相對於事實類型資料表通常較少。 因此，增加的模型大小與重新整理時間不太可能太大。

### <a name="refactoring-methodology"></a>重構方法

以下方法可將模型從單一角色扮演維度類型資料表，重構為「每個角色一個資料表」的設計。

1. 移除任何非作用中關聯性。
2. 請考慮將角色扮演維度類型資料表重新命名，以更清楚地描述其角色。 在此範例中，**Airport** 資料表與 **Flight** 資料表的 **ArrivalAirport** 資料行相關聯，因此將其重新命名為 **Arrival Airport**。
3. 建立角色扮演資料表的複本，並為其提供反映其角色的名稱。 如果其為匯入資料表，我們建議您定義導出資料表。 如果其為 DirectQuery 資料表，您可以複製 Power Query 查詢。

    在此範例中，**Departure Airport** 資料表是使用下列導出資料表定義來建立的。

    ```dax
    Departure Airport = 'Arrival Airport'
    ```

4. 建立作用中關聯性，以建立新資料表的關聯性。
5. 請考慮將資料表中的資料行重新命名，使其正確地反映其角色。 在此範例中，所有資料行前面都會加上 _Departure_ 或 _Arrival_ 一字。 這些名稱可確保報表視覺效果預設會有自我描述且明確的標籤。 這也會改善問與答體驗，讓使用者可以輕鬆地撰寫其問題。
6. 請考慮將描述新增至角色扮演資料表。 (在 [欄位] 窗格中，當報表作者將游標停留在資料表上時，描述會出現在工具提示中)。如此一來，您可以將任何額外篩選條件傳播詳細資料傳達給您的報表作者。

## <a name="inactive-relationships"></a>非作用中的關聯性

在特定情況下，非作用中關聯性可以解決特殊報告需求。

現在讓我們來考慮不同模型與報告需求：

- 銷售模型包含 **Sales** 資料表，其中有兩個日期資料行：**OrderDate** 與 **ShipDate**
- **Sales** 資料表中的每個資料列都記錄單一訂單
- 日期篩選條件幾乎一律會套用至 **OrderDate** 資料行，其一律儲存有效的日期
- 只有一個量值需要將日期篩選條件傳播到 **ShipDate** 資料行，其中可以包含空白 (直到訂單出貨)
- 不需要同時篩選 (或分組) 訂單「與」出貨日期期間

以下是這兩個資料表的部分模型圖表。

![此圖顯示包含兩個資料表的模型：Sales 與 Date。 Sales 資料表包含六個量值。](media/relationships-active-inactive/sales-model.png)

**Sales** 與 **Date** 資料表之間有兩個模型關聯性。 在 **Sales** 資料表中，**OrderDate** 和 **ShipDate** 資料行與 **Date** 資料表的 **Date** 資料行相關聯。 在此模型中，**Date** 資料表的兩個角色是「訂單日期」與「出貨日期」。 作用中的是 **OrderDate** 資料行的關聯性。

所有六個量值 (一個除外) 都必須依 **OrderDate** 資料行進行篩選。 不過，**Orders Shipped** 量值必須依 **ShipDate** 資料行進行篩選。

以下是 **Orders** 量值定義。 其僅計算篩選內容中 **Sales** 資料表的資料列。 套用至 **Date** 資料表的任何篩選條件都會傳播到 **OrderDate** 資料行。

```dax
Orders = COUNTROWS(Sales)
```

以下是 **Orders Shipped** 量值定義。 其使用 [USERELATIONSHIP](/dax/userelationship-function-dax) DAX 函式，只有在運算式評估期間，才會啟用特定關聯性的篩選條件傳播。 在此範例中，是使用 **ShipDate** 資料行的關聯性。

```dax
Orders Shipped =
CALCULATE(
    COUNTROWS(Sales)
    ,USERELATIONSHIP('Date'[Date], Sales[ShipDate])
)
```

此模型設計支援產生下列報表設計。

![此圖顯示包含一個交叉分析篩選器與一個資料表視覺效果的報表頁面。 交叉分析篩選器為 [季]，而表格視覺效果列出每月銷售統計資料。](media/relationships-active-inactive/sales-report-design.png)

報表頁面依季 2019 Q4 進行篩選。 依月份分組的表格視覺效果，並顯示各種銷售統計資料。 **Orders** 與 **Orders Shipped** 量值產生不同結果。 其各自使用相同的摘要邏輯 (計算 **Sales** 資料表的資料列)，但 **Date** 資料表篩選條件傳播不同。

請注意，[季] 交叉分析篩選器包含空白項目。 此交叉分析篩選器項目會顯示為[資料表展開](../transform-model/desktop-relationships-understand.md#regular-relationships)的結果。 不過，每個 **Sales** 資料表資料列都有訂單日期，但是有些資料列有空白出貨日期，這些訂單都尚未出貨。 資料表展開也會考慮非作用中關聯性，因此可能因為多方關聯性上的空白或資料完整性問題，而出現空白。

## <a name="recommendations"></a>建議

總而言之，我們建議您盡可能定義作用中關聯性。 其擴大報表作者和問與答使用者使用您模型的範圍和潛力。 這表示角色扮演維度類型資料表應該在您的模型中重複。

不過，在特定情況下，您可以為角色扮演維度類型資料表定義一或多個非作用中關聯性。 在下列情況下，您可以考慮此設計：

- 報表視覺效果不需要同時依不同角色進行篩選
- 您可以使用 USERELATIONSHIP DAX 函式來啟用相關模型計算的特定關聯性

## <a name="next-steps"></a>後續步驟

如需本文的詳細資訊，請參閱下列資源：

- [Power BI Desktop 中的模型關聯性](../transform-model/desktop-relationships-understand.md)
- [了解星型結構描述及其對 Power BI 的重要性](star-schema.md)
- [關聯性疑難排解指導方針](relationships-troubleshoot.md)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com/)
