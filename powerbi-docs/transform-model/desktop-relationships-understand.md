---
title: Power BI Desktop 中的模型關聯性
description: 關於 Power BI Desktop 中模型關聯性理論的介紹
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: conceptual
ms.date: 10/15/2019
ms.openlocfilehash: 101207fe60f4e66344b936bdef2c4b18d9ab947f
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088158"
---
# <a name="model-relationships-in-power-bi-desktop"></a>Power BI Desktop 中的模型關聯性

本文的目標為使用 Power BI Desktop 匯入資料的模型製作人員。 這是要提供直覺式、準確和最佳模型的重要模型設計主題。

如需有關最佳模型設計的更深入討論，包括資料表角色和關聯性，請參閱[了解星型結構描述及其對 Power BI 的重要性](../guidance/star-schema.md)一文。

## <a name="relationship-purpose"></a>關聯性目的

簡單地說，Power BI 關聯性會將對模型資料表的資料行套用的篩選條件傳播到其他模型資料表。 只要有可遵循的關聯性路徑，篩選就會傳播，這可能會牽涉傳播到多個資料表。

關聯性路徑具有決定性，這表示篩選一律會以相同方式傳播，而不會隨機變化。 不過，您可以停用關聯性，或讓篩選內容由使用特定 DAX 函數的模型計算修改。 如需詳細資訊，請參閱此文章稍後的[相關的 DAX 函式](#relevant-dax-functions)主題。

> [!IMPORTANT]
> 請務必了解模型關聯性不會強制執行資料完整性。 如需詳細資訊，請參閱此文章稍後的[關聯性評估](#relationship-evaluation)主題。 本主題說明當您的資料有資料完整性問題時，模型關聯性的行為方式。

讓我們透過動畫範例來看看關聯性如何傳播篩選。

:::image type="content" source="media/desktop-relationships-understand/animation-filter-propagation.gif" alt-text="關聯性篩選傳播的動畫範例。":::

在此範例中，模型包含四個資料表：**Category**、**Product**、**Year** 和 **Sales**。 **Category** 資料表與 **Product** 資料表相關，而 **Product** 資料表與 **Sales** 資料表相關。 **Year** 資料表也與 **Sales** 資料表相關。 所有關聯性都是一對多 (本文稍後會描述其詳細資料)。

查詢 (可能是由 Power BI 卡片視覺效果所產生) 要求針對單一類別 **Cat-A** 於一年 **CY2018** 所提出銷售訂單的總銷售數量。 這就是為何您看到在 **Category** 與 **Year** 資料表上已套用篩選條件。 對 **Category** 資料表的篩選傳播至 **Product** 資料表，以隔離指派給類別 **Cat-A** 的兩個產品。 然後，**Product** 資料表篩選會傳播至 **Sales** 資料表，以便只將這些產品的兩個銷售資料列隔離。 這兩個銷售資料列代表指派給類別 **Cat-A** 的產品銷售。 其合併數量為 14 個單位。 同時，**Year** 資料表篩選會傳播以進一步篩選 **Sales** 資料表，產生一個銷售資料列，針對僅指派給類別 **Cat-A** 並以年 **CY2018** 排序的產品。 此查詢所傳回的數量值為 11 個單位。 請注意，將多個篩選套用至資料表時 (例如此範例中的 **Sales** 資料表)，它一律是 AND 作業，要求所有條件必須為 true。

### <a name="disconnected-tables"></a>已中斷連線的資料表

模型資料表未與另一個模型資料表相關聯是不正常的。 在有效的模型設計中，這類資料表可以描述為「已中斷連線的資料表」  。 已中斷連線的資料表不是用來將篩選傳播到其他模型資料表。 相反地，它是用來接受「使用者輸入」(或許是使用交叉分析篩選器視覺效果)，讓模型計算能夠以有意義的方式使用輸入值。 例如，假設有一個已中斷連線的資料表，載入了某個範圍的貨幣匯率值。 只要已套用一個篩選條件以依據單一匯率值進行篩選，量值運算式就可使用該值來轉換銷售值。

Power BI Desktop 模擬參數是可建立中斷連線資料表的功能。 如需詳細資訊，請參閱[在 Power BI Desktop 中建立及使用模擬參數來視覺化變數](desktop-what-if.md)一文。

## <a name="relationship-properties"></a>關聯性屬性

一個模型關聯性會將資料表中的一個資料行與另一個資料表中的一個資料行產生關聯。 (有一個特殊案例，其中此需求未滿足，而其僅適用 DirectQuery 模型中的多重資料行關聯性。 如需詳細資訊，請參閱 [COMBINEVALUES](/dax/combinevalues-function-dax) DAX 函式一文)。

> [!NOTE]
> 您無法將某個資料行與 _相同資料表_ 中的不同資料行相關聯。 這有時會與定義資料表自我參考的關聯式資料庫外部索引鍵條件約束的功能混淆。 此關聯式資料庫概念可以用來儲存父子式關聯性 (例如，每個員工記錄會與某個「主管」員工相關聯)。 根據此類型的關聯性產生的模型階層，無法透過建立模型關聯性解析。 若要達成此目的，請參閱 [Parent 和 Child 函數](/dax/parent-and-child-functions-dax)一文。

### <a name="cardinality"></a>基數

每個模型關聯性都必須定義基數類型。 有四個基數類型選項，代表「從」和「到」相關資料行的資料特性。 「一」端表示資料行包含唯一值;「多」端表示資料行可以包含重複的值。

> [!NOTE]
> 如果資料重新整理作業嘗試將重複的值載入至「一」端資料行，則整個資料重新整理將會失敗。

以下項目符號清單中說明這四個選項 (與其速記法)：

- 一對多 (1:\*)
- 多對一 (\*:1)
- 一對一 (1:1)
- 多對多 (\*:\*)

在 Power BI Desktop 中建立關聯性時，設計工具會自動偵測並設定基數類型。 設計工具會查詢模型以得知哪些資料行包含唯一值。 「匯入」模型會使用內部儲存體統計資料，而 DirectQuery 模型會將分析查詢傳送至資料來源。 不過，有時候可能會出錯。 發生這種情況是因為資料表尚未載入資料，或是因為您預期包含重複值的資料行目前包含唯一的值。 不論是哪一種情況，只要任「一端」資料行包含唯一值 (或是資料表還未載入資料列)，您就可以更新基數類型。

「一對多」  和「多對一」  基數選項基本上是相同的，而且它們也是最常見的基數類型。

設定一對多或多對一關聯性時，您會選擇符合您與資料行相關聯之順序的關聯性。 考慮如何使用在每個資料表中找到的 **ProductID** 資料行，設定從 **Product** 資料表到 **Sales** 資料表的關聯性。 此基數類型會是「一對多」  ，因為 **Product** 資料表中的 **ProductID** 資料行包含唯一的值。 如果您以相反方向來關聯資料表，將 **Sales** 關聯至 **Product**，則基數會是「多對一」  。

「一對一」  關聯性表示兩個資料行都包含唯一的值。 此基數類型並不常見，且可能代表非最佳的模型設計，因為它會儲存多餘的資料。 如需使用此基數類型的詳細資訊，請參閱[一對一關聯性指導方針](../guidance/relationships-one-to-one.md)。

「多對多」  關聯性表示兩個資料行都可以包含重複的值。 此基數類型不常使用。 在設計複雜的模型需求時，這通常很有用。 如需使用此基數類型的指引，請參閱[多對多關聯性指引](../guidance/relationships-many-to-many.md)。

> [!NOTE]
> 針對 Power BI 報表伺服器所開發的模型，目前不支援多對多基數類型。

> [!TIP]
> 在 Power BI Desktop 模型檢視中，您可以藉由查看關聯線任一端的指標 (1 或 \*) 來解讀關聯性的基數類型。 若要判斷哪些資料行是相關的，您必須選取關聯線 (或將游標暫留在上方)，以反白顯示資料行。

### <a name="cross-filter-direction"></a>交叉篩選方向

每個模型關聯性都必須定義交叉篩選方向。 您的選擇會決定篩選將傳播的方向。 可能的交叉篩選選項視基數類型而定。

| 基數類型 | 交叉篩選選項 |
| --- | --- |
| 一對多 (或多對一) | 單一<br>兩者 |
| 一對一 | 兩者 |
| 多對多 | 單一 (Table1 至 Table2)<br>單一 (Table2 至 Table1)<br>兩者 |

「單一」  交叉篩選方向表示「單向」，而「兩者」  表示「雙向」。 在兩個方向篩選的關聯性通常會稱為「雙向」  。

針對一對多關聯性，交叉篩選方向一律來自「一」端，並可選擇性地來自「多」端 (雙向)。 針對一對一關聯性，交叉篩選方向一律來自兩個資料表。 最後，針對多對多關聯性，交叉篩選方向可以來自其中一個資料表，或來自兩個資料表。 請注意，當基數類型包含「一」端時，該篩選一律會從該端傳播。

當交叉篩選方向設定為 [兩者]  時，可以使用額外屬性。 當強制執行資料列層級安全性 (RLS) 規則時，其可套用雙向篩選。 如需 RLS 的詳細資訊，請參閱[使用 Power BI Desktop 的資料列層級安全性 (RLS)](../create-reports/desktop-rls.md) 一文。

修改關聯性交叉篩選方向 (包括停用篩選傳播) 也可以透過模型計算來完成。 您可以使用 [CROSSFILTER](/dax/crossfilter-function) DAX 函式來達成此目的。

雙向關聯性對效能可能會有負面影響。 此外，嘗試設定雙向關聯性可能會導致不明確的篩選傳播路徑。 在此情況下，Power BI Desktop 可能無法認可關聯性變更，並會發出錯誤訊息來警示您。 不過，有時候 Power BI Desktop 可能會允許您在資料表之間定義不明確的關聯性路徑。 本文稍後的[優先順序規則](#precedence-rules)主題中會描述影響不明確偵測和路徑解析的優先順序規則。

建議您只在必要時才使用雙向篩選。 如需詳細資訊，請參閱[雙向關聯性指導方針](../guidance/relationships-bidirectional-filtering.md)。

> [!TIP]
> 在 Power BI Desktop 模型檢視中，您可以藉由留意關聯線的箭頭來解讀關聯性的交叉篩選方向。 單箭頭代表箭頭方向的單向篩選；雙箭頭代表雙向關聯性。

### <a name="make-this-relationship-active"></a>將此關聯性設為作用中

兩個模型資料表之間只能有一個作用中的篩選傳播路徑。 但您可以引進其他關聯性路徑，不過這些關聯性必須全設定為「非作用中」  。 非作用中的關聯性只能在模型計算評估期間變成作用中。 您可以使用 [USERELATIONSHIP](/dax/userelationship-function-dax) DAX 函數來達成此目的。

如需詳細資訊，請參閱[作用中與非作用中關聯性指導方針](../guidance/relationships-active-inactive.md)。

> [!TIP]
> 在 Power BI Desktop 模型檢視中，您可以解讀關聯性的作用中與非作用中狀態。 作用中關聯性會以實線表示；非作用中關聯性則以虛線表示。

### <a name="assume-referential-integrity"></a>採用參考完整性

「採用參考完整性」  屬性僅適用於以相同資料來源為基礎之兩個 DirectQuery 儲存模式資料表之間的一對多和一對一關聯性。 啟用時，傳送至資料來源的原生查詢會使用 INNER JOIN 而不是 OUTER JOIN，將兩個資料表聯結在一起。 啟用此屬性一般可改善查詢效能，不過會取決於資料來源的詳細資料。

當這兩個資料表之間存在資料庫外部索引鍵條件約束時，請一律啟用此屬性。 當外部索引鍵條件約束不存在時，只要您的特定資料完整性存在，就仍可以啟用該屬性。

> [!IMPORTANT]
> 如果資料完整性遭到危害，則內部聯結可消除資料表之間不符的資料列。 例如，假設有一個模型 **Sales** 資料表，而該資料行的 **ProductID** 資料行值於相關的 **Product** 資料表中不存在。 從 **Product** 資料表傳播到 **Sales** 資料表的篩選，將會排除銷售資料列中的未知產品。 這會導致銷售結果被輕描淡寫。
>
> 如需詳細資訊，請參閱 [Power BI Desktop 中的採用參考完整性設定](../connect-data/desktop-assume-referential-integrity.md)一文。

## <a name="relevant-dax-functions"></a>相關的 DAX 函數

有數個與模型關聯性相關的 DAX 函數。 下列項目符號清單中會簡短說明每個函數：

- [RELATED](/dax/related-function-dax)：擷取來自「一」端的值。
- [RELATEDTABLE](/dax/relatedtable-function-dax)：從「多」端擷取資料列的資料表。
- [USERELATIONSHIP](/dax/userelationship-function-dax)：強制使用特定非作用中模型關聯性。
- [CROSSFILTER](/dax/crossfilter-function)：修改關聯性交叉篩選方向 (為一或兩者)，否則會停用篩選傳播 (無)。
- [COMBINEVALUES](/dax/combinevalues-function-dax)：將兩個或多個文字字串聯結成一個文字字串。 此函數的目的是要支援 DirectQuery 模型中的多重資料行關聯性。
- [TREATAS](/dax/treatas-function)：將資料表運算式結果以篩選形式套用至來自不相關資料表的資料行。
- [Parent 和 Child 函數](/dax/parent-and-child-functions-dax)：一系列的相關函數，可用來產生計算結果欄，以移植父子式階層。 然後，這些資料行就可以用來建立固定層級的階層。

## <a name="relationship-evaluation"></a>關聯性評估

從評估觀點來看，模型關聯性可分類為「一般」或「有限」。 這不是可設定的關聯性屬性。 事實上，它是從兩個相關資料表的基數類型和資料來源推斷而來。 請務必了解評估類型，因為若資料完整性受到危害，可能會有效能相關的隱含問題或後果。 本主題將說明這些隱含問題和完整性後果。

首先，需要一些模型化理論，才能完全了解關聯性評估。

「匯入」或 DirectQuery 模型會從 Vertipaq 快取或來源資料庫提供其所有資料。 在這兩個執行個體中，Power BI 都能夠判斷關聯性的「一」端存在。

不過，「複合」模型包含的資料表可以使用不同儲存模式 (匯入、DirectQuery 或雙重) 或多個 DirectQuery 來源。 每個來源，包括匯入資料的 Vertipaq 快取，都會被視為「來源群組」。 然後，可將模型關聯性分類為「來源群組內」或「來源群組間」。 「來源群組內」關聯性是指來源群組中兩個資料表的關聯性，而「來源群組間」關聯性則是不同來源群組間資料表的關聯性。 請注意，匯入模型或 DirectQuery 模型中的關聯性一律屬於「來源群組間」關聯性。

讓我們看看「複合」模型範例。

:::image type="content" source="media/desktop-relationships-understand/source-group-example.png" alt-text="由兩個來源群組組合而成的複合模型範例。":::

在此範例中，複合模型包含兩個來源群組：Vertipaq 來源群組與 DirectQuery 來源群組。 Vertipaq 來源群組包含三個資料表，而 DirectQuery 來源群組則包含兩個資料表。 「來源群組間」關聯性會為 Vertipaq 來源群組中的資料表與 DirectQuery 來源群組中的資料表建立關聯。

### <a name="regular-relationships"></a>一般關聯性

當查詢引擎可以判斷關聯性的「一」端時，模型關聯性為「一般」。 它已確認「一」端資料行包含唯一值。 所有一對多「來源群組內」關聯性都是一般關聯性。

在下列範例中，有兩個一般關聯性，兩者都標示為 。關聯性包括 Vertipaq 來源群組內包含的一對多關聯性，以及 DirectQuery 來源內包含的一對多關聯性。

:::image type="content" source="media/desktop-relationships-understand/source-group-example-regular.png" alt-text="由兩個來源群組組合而成，並標示為一般關聯性的「複合」模型範例。":::

針對所有資料都儲存在 Vertipaq 快取中的匯入模型，則會在資料重新整理時，為每個一般關聯性建立資料結構。 資料結構是由所有資料行對資料行值的索引對應所組成，而其目的是在查詢時加速聯結資料表。

查詢時，一般關聯性允許進行「資料表展開」。 資料表展開會藉由包含基底資料表的原生資料行，然後展開到相關資料表來建立虛擬資料表。 針對「匯入」資料表，這會在查詢引擎中完成；針對 DirectQuery 資料表，則會在傳送至來源資料庫的原生查詢中完成 (只要未啟用 **採用參考完整性** 屬性)。 然後，查詢引擎會在展開的資料表上採取動作，套用篩選，並依展開的資料表資料行中的值進行分組。

> [!NOTE]
> 也會展開非作用中的關聯性，即使關聯性未由計算使用也一樣。 雙向關聯性對資料表展開沒有任何影響。

若是一對多關聯性，資料表展開會使用 LEFT OUTER JOIN 語義，從「多」對「一」端執行。 從「多」對「一」端的相符值不存在時，就會將空白的虛擬資料列新增至「一」端資料表。

展開資料表也會發生一對一「來源群組內」關聯性，但須使用 FULL OUTER JOIN 語義。 它可確保在必要時，會在任一端新增空白的虛擬資料列。

空白的虛擬資料列實際上是「未知的成員」  。 未知的成員代表參考完整性違規，其中的「多」端值沒有對應的「一」端值。 在理想情況下，這些空白不應該存在，而且可以藉由清理或修復來源資料來消除。

讓我們透過動畫範例來看看資料表展開如何運作。

:::image type="content" source="media/desktop-relationships-understand/animation-expanded-table.gif" alt-text="資料表延伸模組的動畫範例。":::

在此範例中，模型包含三個資料表：**Category**、**Product** 和 **Sales**。 **Category** 資料表與 **Product** 資料表具有一對多關聯性，而 **Product** 資料表與 **Sales** 資料表具有一對多關聯性。 **Category** 資料表包含兩個資料列，**Product** 資料表包含三個資料列，而 **Sales** 資料表包含五個資料列。 所有關聯性的兩端都有相符的值，這表示沒有參考完整性違規。 查詢時間展開資料表顯示。 資料表包含來自這三個資料表的資料行。 它實際上是三個資料表中所含資料的反正規化檢視。 新的資料列會新增至 **Sales** 資料表，而且它具有的生產識別碼值 (9)在 **Product** 中沒有相符值。 這是參考的完整性違規。 在展開的資料表中，新的資料列具有 **Category** 和 **Product** 資料表資料行的 (空白) 值。

### <a name="limited-relationships"></a>有限關聯性

若未保證「一」端，模型關聯性即為「有限」。 此情況可能有兩個原因：

- 關聯性使用多對多基數類型 (即使其中一個或兩個資料行包含唯一值)
- 關聯性為「來源群組間」(只存在於「複合」模型的案例)

在下列範例中，有兩個有限關聯性，兩者都標示為 **L**。這兩個關聯性包括 Vertipaq 來源群組內包含的多對多關聯性，以及一對多「來源群組間」關聯性。

:::image type="content" source="media/desktop-relationships-understand/source-group-example-limited.png" alt-text="由兩個來源群組組合而成，並標示為有限關聯性的「複合」模型範例。":::

針對匯入模型，永遠都不會為有限關聯性建立資料結構。 這表示必須在查詢時解析資料表聯結。

永遠都不會針對有限關聯性進行資料表展開。 資料表聯結是藉由使用 INNER JOIN 語意來達成，基於此原因，系統不會為了補償參考完整性違規而加入空白虛擬資料列。

與有限關聯性相關的其他限制如下：

- RELATED DAX 函數無法用來擷取「一」端資料行值
- 強制 RLS 具有拓撲限制

> [!NOTE]
> 在 Power BI Desktop 模型檢視中，不一定能夠判斷模型關聯性是否為一般或有限。 多對多關聯性一律為有限，當其為「來源群組間」關聯性時，則為一對多關聯性。 若要判斷關聯性是否為「來源群組間」關聯性，您必須檢查資料表儲存體模式和資料來源，以獲得正確的判斷。

### <a name="precedence-rules"></a>優先順序規則

雙向關聯性可以在模型資料表之間引進多個 (因此不明確) 的篩選傳播路徑。 下列清單提供 Power BI 用於不明確偵測和路徑解析的優先順序規則：

1. 多對一和一對一關聯性，包括有限關聯性
2. 多對多關聯性
3. 雙向關聯性，相反方向 (也就是從「多」方)

### <a name="performance-preference"></a>效能喜好設定

下列清單會篩選傳播效能，從最快到最慢的效能：

1. 一對多「來源群組內」關聯性
2. 多對多基數關聯性
3. 透過中繼資料表達成的多對多模型關聯性，且牽涉到至少一個雙向關聯性
4. 「來源群組間」關聯性

## <a name="next-steps"></a>後續步驟

如需本文的詳細資訊，請參閱下列資源︰

- [了解星型結構描述及其對 Power BI 的重要性](../guidance/star-schema.md)
- [一對一關聯性指導方針](../guidance/relationships-one-to-one.md)
- [多對多關聯性指引](../guidance/relationships-many-to-many.md)
- [作用中與非作用中關聯性指導方針](../guidance/relationships-active-inactive.md)
- [雙向關聯性指導方針](../guidance/relationships-bidirectional-filtering.md)
- [關聯性疑難排解指導方針](../guidance/relationships-troubleshoot.md)
- 影片：[The Do's and Don'ts of Power BI Relationships](https://www.youtube.com/watch?v=78d6mwR8GtA) (Power BI 關聯性的建議事項和避免事項)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com/)
