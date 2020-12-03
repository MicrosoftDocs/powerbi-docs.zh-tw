---
title: 一對一關聯性指導方針
description: 開發一對一模型關聯性的指導方針。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 03/02/2020
ms.openlocfilehash: 19fe2aa003c3d39169bc449dab83c09702f49b1d
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96419145"
---
# <a name="one-to-one-relationship-guidance"></a>一對一關聯性指導方針

此文章以使用 Power BI Desktop 的資料模型製作人員為目標。 其能為您提供處理一對一模型關聯性的指導方針。 當兩個資料表個別包含具有通用與唯一值的資料行時，便可以建立一對一關聯性。

[!INCLUDE [relationships-prerequisite-reading](includes/relationships-prerequisite-reading.md)]

有兩個涉及一對一關聯性的案例：

- [變質維度](#degenerate-dimensions)：您可以從事實類型資料表衍生[變質維度](star-schema.md#degenerate-dimensions)。
- [跨資料表的資料列資料](#row-data-spans-across-tables)：以兩個 (或多個) 模型資料表的形式載入單一業務實體或主體，原因可能是其資料源自不同的資料存放區。 此案例對於維度類型資料表來說可能很常見。 例如，主要產品詳細資料會儲存在營運銷售系統中，而補充產品詳細資料則儲存在不同的來源中。

    不過，您通常不會將兩個事實類型資料表與一對一關聯性產生關聯。 這是因為這兩個事實類型資料表都需要具有相同的維度性與資料粒度。 此外，每個事實類型資料表都需要唯一的資料行，以允許建立模型關聯性。

## <a name="degenerate-dimensions"></a>變質維度

將來自事實類型資料表的資料行用於篩選或分組時，您可以考慮在個別的資料表中加以提供。 如此一來，您便可以將用來篩選或分組的資料行，與用來對事實資料列進行摘要的資料行分隔開來。 此分隔可以：

- 減少儲存空間
- 簡化模型計算
- 為改善查詢效能做出貢獻
- 為您的報表作者提供更加直覺的 [欄位]  窗格體驗

假設有一個將銷售訂單詳細資料儲存在兩個資料行中的來源銷售資料表。

![銷售資料表的資料表資料列。](media/relationships-one-to-one/sales-order-rows.png)

**OrderNumber** 資料行會儲存訂單號碼，而 **OrderLineNumber** 資料行則儲存訂單內的行序列。

在下列模型圖表中，請注意訂單號碼和訂單行號資料行並沒有載入 **Sales** (銷售) 資料表。 相反地，系統使用其值來建立名為 **SalesOrderLineID** 的 [Surrogate 索引鍵](star-schema.md#surrogate-keys)。 (索引鍵值的計算方式是將訂單號碼乘以 1000，然後再加上訂單行號。)

![此模型圖表包含兩個資料表：Sales (銷售) 與 Sales Order (銷售訂單)。 一對一關聯性將兩個 SalesOrderLineID 資料行相關聯。](media/relationships-one-to-one/sales-order-degenerate.png)

**Sales Order** (銷售訂單) 資料表能透過下列三個資料行，為報表作者提供豐富的體驗：**Sales Order** (銷售訂單)、**Sales Order Line** (銷售訂單行) 與 **Line Number** (行號)。 其也包含階層。 這些資料表資源能支援需要針對訂單與訂單行進行篩選、分組或向下切入的報表設計。

由於 **Sales Order** (銷售訂單) 資料表是衍生自銷售資料，每個資料表中的資料列數目應該都會完全相同。 此外，每個 **SalesOrderLineID** 資料行的值應該都是相符的。

## <a name="row-data-spans-across-tables"></a>跨資料表的資料列資料

考慮一個涉及兩個具一對一關聯性的維度類型資料表範例：**Product** (產品) 與 **Product Category** (產品類別)。 每個資料表都代表匯入的資料，並具有包含唯一值的 **SKU** (庫存單位) 資料行。

以下是這兩個資料表的部分模型圖表。

![此模型圖表包含兩個資料表。 下列段落會描述其設計。](media/relationships-one-to-one/product-to-product-category.png)

第一個資料表的名稱為 **Product** (產品)，其中包含三個資料行：**Color** (色彩)、**Product** (產品) 與 **SKU**。 第二個資料表的名稱為 **Product Category** (產品類別)，其中包含兩個資料行：**Category** (類別) 與 **SKU**。 一對一關聯性將兩個 **SKU** 資料行相關聯。 關聯性會朝兩個方向進行篩選，此情況在一對一關聯性中一律會發生。

為了協助描述關聯性篩選傳播的運作方式，此模型圖表已修改為顯示資料表資料列。 此文章中的所有範例都是以此資料為基礎。

> [!NOTE]
> 您無法在 Power BI Desktop 模型圖表中顯示資料表資料列。 在本文中，為了以清楚的範例來支援討論，已事先完成。

![此模型圖表現在顯示資料表資料列。 下列段落會描述資料列詳細資料。](media/relationships-one-to-one/product-to-product-category-2.png)

下列項目符號清單描述這兩個資料表的資料列詳細資料：

- **Product** (產品) 資料表有三個資料列：
  - **SKU** CL-01、**Product** T 恤、**Color** 綠色
  - **SKU** CL-02、**Product** 牛仔褲、**Color** 藍色
  - **SKU** AC-01、**Product** (產品) Hat (帽子)、**Color** (色彩) Blue (藍色)
- **Product Category** (產品類別) 有兩個資料列：
  - **SKU** CL-01、**Category** (類別) Clothing (服飾)
  - **SKU** AC-01、**Category** (類別) Accessories (配件)

請注意，**Product Category** (產品類別) 資料表沒有包含產品 SKU CL-02 的資料列。 我們將會在此文章稍後討論遺漏此資料列的後果。

在 [欄位]  窗格中，報表作者將能找到兩個資料表中的產品相關欄位：[Product]  \(產品\) 與 [Product Category]  \(產品類別\)。

![[欄位] 窗格以展開的方式顯示這兩個資料表，並將資料行列為欄位且標註 [產品] 和 [產品類別]。](media/relationships-one-to-one/product-to-product-category-fields-pane.png)

讓我們看看將來自兩個資料表的欄位新增到資料表視覺效果時，會發生什麼事。 在此範例中，[SKU]  資料行是源自 [Product]  \(產品\) 資料表。

![資料表視覺效果包含四個資料行：[SKU]、[Product] \(產品\)、[Color] \(色彩\) 與 [Category] \(類別\)。 產品 SKU CL-02 的 [Category] \(類別\) 值為空白。](media/relationships-one-to-one/product-to-product-category-table-visual.png)

請注意，產品 SKU CL-02 的 [Category]  \(類別\) 值為空白。 這是因為此產品在 [Product Category]  \(產品類別\) 資料表中並沒有資料列。

### <a name="recommendations"></a>建議

在資料列資料會跨越模型資料表時，我們建議您盡可能避免建立一對一模型關聯性。 這是因為此設計可能會：

- 列出比所需還要多的資料表，使得 [欄位]  窗格變得更加雜亂
- 使報表作者難以找到相關聯的欄位，因為這些欄位散佈於多個資料表上
- 限制建立階層的能力，因為其層級必須是以來自「相同資料表」  的資料行為基礎
- 在資料表之間的資料列沒有完全相符的情況下產生未預期的結果

視一對一關聯性為「島內」  或「島間」  而定，特定建議會有所不同。 如需關聯性評估的詳細資訊，請參閱 [Power BI Desktop 中的模型關聯性 (關聯性評估)](../transform-model/desktop-relationships-understand.md#relationship-evaluation)。

### <a name="intra-island-one-to-one-relationship"></a>島內一對一關聯性

在資料表之間存在一對一的「島內」  關聯性時，建議將資料合併成單一模型資料表。 這是透過合併 Power Query 查詢來完成的。

下列步驟會展示將一對一相關的資料合併及模型化的方法：

1. **合併查詢**：在 [結合兩個查詢](../connect-data/desktop-shape-and-combine-data.md#combine-queries)時，請考慮每個查詢中資料的完整性。 如果某個查詢包含一組完整的資料列 (例如主要清單)，請將另一個查詢與其合併。 設定合併轉換以使用「左方外部聯結」  ，其為預設的聯結類型。 此聯結類型能確保您會保留第一個查詢的所有資料列，並以第二個查詢中任何相符的資料列來加以補充。 將第二個查詢的所有必要資料行展開至第一個查詢。
2. **停用查詢載入**：請務必 [停用第二個查詢的載入](import-modeling-data-reduction.md#disable-power-query-query-load)。 如此一來，其便不會將結果載入為模型資料表。 此設定能減少資料模型儲存體大小，並協助整理 [欄位]  窗格。

    在我們的範例中，報表作者現在會在 [欄位]  窗格中找到名為 [Product]  \(產品\) 的單一資料表。 其包含所有產品相關欄位。

    ![[欄位] 窗格以展開的方式顯示這兩個資料表，並將資料行列為欄位且標註 [產品]。](media/relationships-one-to-one/product-to-product-category-fields-pane-consolidated.png)
3. **取代遺漏值**：如果第二個查詢具有不相符的資料列，透過其所引進的資料行中便會出現 NULL。 適當時，請考慮以語彙基元值取代 NULL。 當報表作者會依資料行值進行篩選或分組時，取代遺漏值便特別重要，因為報表視覺效果中可能會出現空白。

    在下列資料表視覺效果中，請注意產品 SKU CL-02 的類別現在已顯示為 _[Undefined]_ \(未定義\)。 在查詢中，將會以此語彙基元文字值來取代 Null 類別。

    ![資料表視覺效果包含四個資料行：[SKU]、[Product] \(產品\)、[Color] \(色彩\) 與 [Category] \(類別\)。 產品 SKU CL-02 的 [Category] \(類別\) 值現已標記為 "Undefined" (未定義)。](media/relationships-one-to-one/product-to-product-category-table-visual-null-replaced.png)

4. **建立階層**：如果關聯性存在於現已合併之資料表的「資料行之間」  ，請考慮建立階層。 如此一來，報表作者將能快速識別報表視覺效果切入的機會。

    在我們的範例中，報表作者現在可以使用具有下列兩個層級的階層：[Category]  \(類別\) 與 [Product]  \(產品\)。

    ![[欄位] 窗格以展開的方式顯示這兩個資料表，並將資料行列為欄位且標註 [產品]。](media/relationships-one-to-one/product-to-product-category-fields-pane-consolidated-with-hierarchy.png)

如果您喜歡個別資料表協助組織欄位的方式，我們仍然建議合併成單一資料表。 您仍然可以組織欄位，只是須改為使用「顯示資料夾」  。

在我們的範例中，報表作者可以在 [Marketing]  \(行銷\) 顯示資料夾內找到 [Category]  \(類別\) 欄位。

![[欄位] 窗格在名為 [Marketing] \(行銷\) 的顯示資料夾中顯示 [Category] \(類別\) 欄位。](media/relationships-one-to-one/product-to-product-category-fields-pane-consolidated-display-folder.png)

如果您仍決定在模型中定義一對一的島內關聯性，在可能的情況下，請確保相關聯的資料表中具有相符的資料列。 由於一對一的島內關聯性會評估為[一般關聯性](../transform-model/desktop-relationships-understand.md#regular-relationships)，因此資料完整性問題可能會以空白的形式出現在報表視覺效果中。 (您可以在此文章所呈現的第一個資料表視覺效果中看到空白分組的範例。)

### <a name="inter-island-one-to-one-relationship"></a>島間一對一關聯性

當資料表之間存在一對一的「島間」  關聯性時，將不會有替代模型設計，除非您在資料來源預先合併資料。 Power BI 會將一對一模型關聯性評估為[受限關聯性](../transform-model/desktop-relationships-understand.md#limited-relationships)。 因此，請務必確保相關聯的資料表中具有相符的資料列，因為系統會將不相符的資料列從查詢結果中排除。

讓我們看看將來自兩個資料表的欄位新增到資料表視覺效果，且資料表之間存在受限關聯性時，會發生什麼事。

![資料表視覺效果包含四個資料行：[SKU]、[Product] \(產品\)、[Color] \(色彩\) 與 [Category] \(類別\)。 資料表只有兩個資料列。](media/relationships-one-to-one/product-to-product-category-table-visual-weak-relationship.png)

資料表只會顯示兩個資料列。 產品 SKU CL-02 遺失，因為 [Product Category]  \(產品類別\) 資料表中沒有相符的資料列。

## <a name="next-steps"></a>後續步驟

如需本文的詳細資訊，請參閱下列資源：

- [Power BI Desktop 中的模型關聯性](../transform-model/desktop-relationships-understand.md)
- [了解星型結構描述及其對 Power BI 的重要性](star-schema.md)
- [關聯性疑難排解指導方針](relationships-troubleshoot.md)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com/)
