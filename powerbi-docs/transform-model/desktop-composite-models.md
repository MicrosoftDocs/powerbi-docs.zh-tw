---
title: 在 Power BI Desktop 中使用複合模型
description: 在 Power BI Desktop 中透過多個資料連線與多對多關聯性來建立資料模型
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: conceptual
ms.date: 01/15/2020
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 078596c91f86f635cb69f543ee0ea828e5cef62d
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415856"
---
# <a name="use-composite-models-in-power-bi-desktop"></a>在 Power BI Desktop 中使用複合模型

先前在 Power BI Desktop 中，當您在報表中使用 DirectQuery 時，該報表都不允許其他 DirectQuery 或「匯入」資料連線。 複合模型可以移除該限制。 報表能以各種組合，完美地包含來自多個 DirectQuery 或「匯入」資料連線的資料連線。

Power BI Desktop 中的複合模型功能包含三種相關功能：

* **複合模型**：讓報表能夠具有任意組合的多個資料連線，包括 DirectQuery 連線或「匯入」。 本文會詳細描述複合模型。

* **多對多關聯性**：您可以使用複合模型在資料表之間建立「多對多關聯性」  。 此方法會移除資料表中唯一值的需求。 此方法也會移除先前的因應措施，像是只為建立關聯性而導入新的資料表。 如需詳細資訊，請參閱[在 Power BI Desktop 中套用多對多關聯性](desktop-many-to-many-relationships.md)。

* **儲存模式**：您現在可以指定哪些視覺效果查詢後端資料來源。 不需要查詢的視覺效果，即便是使用 DirectQuery，也同樣會匯入。 此功能可提升效能，並減輕後端的負載。 先前即使是像交叉分析篩選器這類簡單的視覺效果，都會起始查詢，以查詢後端來源。 如需詳細資訊，請參閱[管理 Power BI Desktop 中的儲存模式](desktop-storage-mode.md)。

## <a name="use-composite-models"></a>使用複合模型

您可以運用複合模型，在使用 Power BI Desktop 或 Power BI 服務時，連線到不同類型的資料來源。 您可以用幾種方式進行這些資料連線：

* 將資料匯入至 Power BI，這是取得資料的最常見方式。
* 透過使用 DirectQuery 直接連線到資料原始來源存放庫中的資料。 如需 DirectQuery 的詳細資訊，請參閱[使用 Power BI 的 DirectQuery](../connect-data/desktop-directquery-about.md)。

當您使用 DirectQuery 時，可透過「複合模型」建立可執行下列作業其中之一或兩者的 Power BI 模型 (例如，單一 *.pbix* Power BI Desktop 檔案)：

* 結合來自一或多個 DirectQuery 來源的資料。
* 結合來自 DirectQuery 來源的資料與「匯入」資料。

例如，您可以藉由使用複合模型來建置結合下列資料類型的模型：

* 來自企業資料倉儲的銷售資料。
* 來自部門 SQL Server 資料庫的銷售目標資料。
* 從試算表匯入的資料。

結合多個 DirectQuery 來源的資料或結合 DirectQuery 與「匯入」資料的模型，即稱為「複合模型」。

您能如往常一般，建立資料表之間的關聯性 (即使這些資料表來自不同的來源)。 不論實際基數為何，任何跨來源的關聯性都會使用「多對多」基數來建立。 您可以將其變更為一對多、多對一或一對一。 無論您設定哪一種基數，跨來源的關聯性都有不同的行為。 您無法使用資料分析運算式 (DAX) 函式，從 `many` 端抓取 `one` 端的值。 您也可能會看到相同來源中多對多關聯性對效能的影響。

> [!NOTE]
> 在複合模型內容中，所有匯入的資料表便有如單一來源，不論實際的基礎資料來源為何。

## <a name="example-of-a-composite-model"></a>複合模型範例

如需「複合模型」的範例，請考慮使用 DirectQuery 連線到 SQL Server 中公司資料倉儲的報表。 在此情況下，資料倉儲會包含「依國家/地區的銷售額」  、「季」  和「腳踏車 (產品)」  資料，如下圖所示：

![複合模型的關聯性檢視](media/desktop-composite-models/composite-models_04.png)

此時，您可以使用此來源中的欄位，以建置簡單的視覺效果。 下圖是依 *ProductName* 顯示所選季度的總銷售額。

![根據資料的視覺效果](media/desktop-composite-models/composite-models_05.png)

但是，如果您有資料在 Office Excel 試算表中，且是關於指派給每個產品的產品經理以及行銷優先順序，該怎麼辦？ 如果您想要依「產品經理」  檢視「銷售額」  ，可能無法將此本機資料新增至公司的資料倉儲。 或者，在最佳的情況下可能需要幾個月的時間。

可能可以從資料倉儲匯入銷售資料，而不是使用 DirectQuery。 銷售資料便可以與您從試算表匯入的資料結合。 不過，該方法並不合理，因為會導致在一開始時使用 DirectQuery。 原因可能包括：

* 在基礎來源實施的某個安全性規則組合。
* 要能夠檢視最新資料的需求。
* 純粹因為資料規模。

這就是複合模型派上用場的地方。 複合模型可讓您使用 DirectQuery 連線到資料倉儲，然後針對其他來源使用 [取得資料]  。 在此範例中，我們會先建立對公司資料倉儲的 DirectQuery 連線。 我們使用 [取得資料]  、選擇 [Excel]  ，然後瀏覽至包含我們本機資料的試算表。 最後，我們匯入試算表，其中包含「產品名稱」  、指派的「銷售經理」  和「優先順序」  。  

![[導覽器] 視窗](media/desktop-composite-models/composite-models_06.png)

在 [欄位]  清單中，您可以看到兩個資料表：來自 SQL Server 的原始 **Bike** 資料表，和新的 **ProductManagers** 資料表。 新資料表會包含從 Excel 匯入的資料。

![資料表的欄位檢視](media/desktop-composite-models/composite-models_07.png)

同樣地，在 Power BI Desktop 的 [關聯性]  檢視中，現在可看到稱為 **ProductManagers** 的其他資料表。

![資料表的關聯性檢視](media/desktop-composite-models/composite-models_08.png)

我們現在需要將這些資料表與模型中的其他資料表相關聯。 如往常，我們在來自 SQL Server 的 **Bike** 資料表，與匯入的 **ProductManagers** 資料表之間建立關聯性。 亦即，關聯性是在 **Bike[ProductName]** 與 **ProductManagers[ProductName]** 之間。 如先前所述，跨來源的所有關聯性預設為「多對多」基數。

![[建立關聯性] 視窗](media/desktop-composite-models/composite-models_09.png)

現在我們已經建立此關聯性，它就會如我們所預期，顯示在 Power BI Desktop 的 [關聯性]  檢視中。

![新的 [關聯性] 檢視](media/desktop-composite-models/composite-models_10.png)

我們現在可以使用 [欄位]  清單中的任何欄位來建立視覺效果。 這種方法可順暢地混合使用多個來源的資料。 例如，每個「產品經理」  的 *SalesAmount* 總計會顯示在下圖中：

![[欄位] 窗格](media/desktop-composite-models/composite-models_11.png)

下列範例顯示使用從他處所匯入一些額外資料來擴充「維度」  資料表 (例如「產品」  或「客戶」  ) 的常見情況。 也可以讓資料表使用 DirectQuery 連線到各種來源。 為了繼續我們的範例，假設每個 **Country** 與 **Period** 的 **SalesTargets** 都儲存在個別部門資料庫中。 您可以照常使用 [取得資料]  來連線到該資料，如下圖所示：

![[導覽器] 視窗](media/desktop-composite-models/composite-models_12.png)

如我們先前所執行，可在新的資料表與模型中其他資料表之間建立關聯性，然後建立可結合資料表資料的視覺效果。 讓我們再次查看 [關聯性]  檢視，我們已在此建立了新的關聯性：

![具有許多資料表的 [關聯性] 檢視](media/desktop-composite-models/composite-models_13.png)

下圖是以新資料和我們所建立的關聯性為基礎。 左下角的視覺效果顯示「銷售額」  總計與「目標」  ，而變異數計算則顯示差異。 「銷售額」  和「目標」  資料來自兩個不同的 SQL Server 資料庫。

![顯示更多資料的影像](media/desktop-composite-models/composite-models_14.png)

## <a name="set-the-storage-mode"></a>設定儲存模式

複合模型中的每個資料表都有儲存模式，指出該資料表是以 DirectQuery 或「匯入」為基礎。 儲存模式可在 [屬性]  窗格中檢視和修改。 若要顯示儲存模式，請以滑鼠右鍵按一下 [欄位]  清單中的資料表，然後選取 [屬性]  。 下圖顯示 **SalesTargets** 資料表的儲存模式。

每個資料表的工具提示上也可檢視儲存模式。

![顯示儲存模式的工具提示](media/desktop-composite-models/composite-models_16.png)

針對包含來自 DirectQuery 的一些資料表與一些「匯入」資料表的任何 *Power BI Desktop* 檔案 (.pbix 檔案)，狀態列會顯示稱為 [混合]  的儲存模式。 您可以按一下狀態列中的該字詞，然後將所有資料表輕鬆地切換為「匯入」。

如需儲存模式的詳細資訊，請參閱[管理 Power BI Desktop 中的儲存模式](desktop-storage-mode.md)。  

> [!NOTE]
> 您可以在 Power BI Desktop 和 Power BI 服務中使用「混合」  儲存模式。

## <a name="calculated-tables"></a>計算資料表

您可以將導出資料表新增至使用 DirectQuery 的模型。 定義導出資料表的資料分析運算式 (DAX) 可以參考匯入或 DirectQuery 資料表，或兩者的組合。

導出資料表一律為匯入，而且會在您重新整理資料表時，重新整理其資料。 如果導出資料表參考 DirectQuery 資料表，則參考 DirectQuery 資料表的視覺效果一律會顯示基礎來源中的最新值。 或者，參考導出資料表的視覺效果，會顯示導出資料表最近一次重新整理時的值。

## <a name="security-implications"></a>安全性影響

複合模型對安全性會有一些影響。 傳送至某個資料來源的查詢，可能包含從其他來源擷取的資料值。 在先前範例中，依「產品經理」  顯示「銷售額」  的視覺效果，會傳送 SQL 查詢給 Sales 關聯式資料庫。 該 SQL 查詢可能包含「產品經理」的名稱及其相關聯「產品」。

![顯示安全性影響的指令碼](media/desktop-composite-models/composite-models_17.png)

因此，傳送至關聯式資料庫的查詢現在會包含儲存在試算表中的資訊。 如果這是機密資訊，您應該考慮安全性影響。 特別是，請考慮下列幾點：

* 可以檢視追蹤或稽核記錄檔的任何資料庫系統管理員，都可以檢視這項資訊，即使沒有資料原始來源的資料權限亦然。 在此範例中，系統管理員需要 Excel 檔案的權限。

* 應該考慮每個來源的加密設定。 您想要避免透過加密連線從其中一個來源擷取資訊，然後意外地將它包含在透過未加密連線傳送至另一個來源的查詢中。

為了允許確認您已經考慮過所有安全性意涵，當您建立複合模型時，Power BI Desktop 會顯示警告訊息。  

基於類似原因，當您開啟從不受信任來源傳送的 Power BI Desktop 檔案時，請小心。 如果檔案包含複合模型，則某人使用檔案開啟者的使用者認證來從某一個來源擷取的資訊會作為部分查詢傳送到另一個資料來源。 Power BI Desktop 檔案的惡意作者可能會檢視這項資訊。 當您初次開啟包含多個來源的 Power BI Desktop 檔案時，Power BI Desktop 會顯示警告。 此警告和開啟包含原生 SQL 查詢的檔案時所顯示的警告類似。  

## <a name="performance-implications"></a>效能影響  

使用 DirectQuery 時，您應該一律考量效能，主要是為了確保後端來源有充足的資源，以便為使用者提供良好的體驗。 良好的體驗表示視覺效果在五秒內重新整理。 如需更多效能建議，請參閱[如何在 Power BI 中使用 DirectQuery](../connect-data/desktop-directquery-about.md)。

使用複合模型會增加額外的效能考量。 單一視覺效果可能會導致傳送查詢到多個來源，這通常會將某一個查詢的結果傳遞到第二個來源。 這種情況可能會導致下列執行形式：

* **包含大量常值的 SQL 查詢**：例如，要求一組選定「產品經理」  之總「銷售量」  的視覺效果，必須先找出那些產品經理所管理的「產品」  。 此順序必須在視覺效果傳送以 `WHERE` 子句包含所有產品識別碼的 SQL 查詢之前進行。

* **在低層級資料粒度層級查詢的 SQL 查詢，其資料之後會在本機彙總**：隨著「產品經理」  上符合篩選準則的「產品」  數目增加，在 `WHERE` 子句中包含所有產品可能變得效率不佳或不可行。 相反地，您可以較低「產品」  層級來查詢關聯式來源，然後在本機彙總結果。 如果「產品」  基數超過 1 百萬的上限，查詢就會失敗。

* **依值分組，每個群組一個的多個 SQL 查詢**：當彙總使用 **DistinctCount** 且是依據另一來源的某資料行來分組時，如果外部來源不支援有效率地傳遞定義群組的許多常值，就有必要依值分組，每個群組傳送一個 SQL 查詢。

   依「產品經理」  (從試算表匯入) 要求 **CustomerAccountNumber** (來自 SQL Server 資料表) 相異計數的視覺效果，就需要在傳送至 SQL Server 的查詢中傳遞來自「產品經理」  資料表的詳細資料。 針對其他來源 (例如 Redshift)，此動作不可行。 相反地，針對每個「銷售經理」  會傳送一個 SQL 查詢；最多以實際限制為限，超過就會查詢失敗。

上述每一種情況對於效能各有其影響，確切的細節也會隨每個資料來源而異。 雖然在聯結兩個來源的關聯性中，會維持使用低資料行基數 (數千個)，但效能應不會受到影響。 當這個基數增加時，您應該更加注意對於結果效能的影響。

此外，使用「多對多」關聯性時，表示必須針對每個總計或小計層級，將個別查詢傳送至基礎來源，而不是在本機彙總詳細值。 一個包含總計的簡單資料表視覺效果會傳送兩個 SQL 查詢，而不是一個。

## <a name="limitations-and-considerations"></a>限制與考量

這一版的複合模型有一些限制：

目前，只有連接到 SQL、Oracle 和 Teradata 資料來源的複合模型才支援[累加式重新整理](../admin/service-premium-incremental-refresh.md)。

下列 Live Connect (多維度) 來源不能與複合模型搭配使用：

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Power BI 資料集
* Azure Analysis Services

當您使用 DirectQuery 連線到這些多維度來源時，將無法連線到其他 DirectQuery 來源，也無法與「匯入」資料結合。

使用複合模型時，仍然受限於 DirectQuery 的現有限制。 這其中有許多限制現在會依個別資料表的儲存模式而異。 例如，「匯入」資料表上的導出資料行可以參考其他資料表，但 DirectQuery 資料表上的導出資料行仍僅能參考相同資料表上的資料行。 如果模型內有任何資料表為 DirectQuery，則其他限制會套用至整個模型。 例如，當 QuickInsights 及問與答功能中有任何資料表為 DirectQuery 的儲存模式時，該模型便無法使用這兩項功能。

## <a name="next-steps"></a>後續步驟

如需複合模型及 DirectQuery 的詳細資訊，請參閱下列文章：

* [Power BI Desktop 中的多對多關聯性](desktop-many-to-many-relationships.md)
* [Power BI Desktop 中的儲存模式](desktop-storage-mode.md)
* [使用 Power BI 的 DirectQuery](../connect-data/desktop-directquery-about.md)
* [Power BI 中 DirectQuery 支援的資料來源](../connect-data/power-bi-data-sources.md)
