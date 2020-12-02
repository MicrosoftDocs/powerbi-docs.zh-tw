---
title: 在 Excel 中存取 Power BI 的精選表格 (預覽)
description: 在 Excel 中，可在資料類型資源庫的 Power BI 資料集中，從精選表格中尋找資料。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 08/04/2020
LocalizationGroup: Share your work
ms.openlocfilehash: 95ccc80a37ad9703c60c82ce928d35b5e301947b
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96407300"
---
# <a name="access-power-bi-featured-tables-in-excel-preview"></a>在 Excel 中存取 Power BI 的精選表格 (預覽)

「精選表格」是將 Excel 中資料連結到 Power BI 中資料的方式。 這些表格可供更輕鬆地將企業資料新增至 Excel 工作表。 在 Excel 的資料類型資源庫中，您可從 Power BI 資料集的精選表格來尋找資料。 本文說明執行方法。

您在 Power BI 中建立資料集嗎？ 請參閱[在 Power BI Desktop 中設定精選表格](service-create-excel-featured-tables.md)。

> [!NOTE]
> 在 Exce 中，您也可以從任何可在 Power BI 中存取的 Power BI 資料集分析資料。 如需詳細資料，請參閱＜在 Excel 中對 Power BI 進行分析＞一文中[從 Excel 存取 Power BI 資料集的其他方式](service-analyze-in-excel.md#other-ways-to-access-power-bi-datasets-from-excel)。
> 

## <a name="the-excel-data-types-gallery"></a>Excel 資料類型資源庫
Power BI 資料集中精選表格會以「資料類型」型態出現在 [資料] 功能區的 Excel [資料類型] 資源庫中 。

:::image type="content" source="media/service-excel-featured-tables/excel-data-ribbon.png" alt-text="Excel 資料功能區中資料類型資源庫的螢幕擷取畫面。":::

資源庫展開時，其會顯示泛型資料類型 (例如 [股票] 與 [地理位置])，加上可供使用的前 10 大 [組織] 資料類型 -- 來自 Power BI 資料集的精選表格。

:::image type="content" source="media/service-excel-featured-tables/excel-data-types-gallery.png" alt-text="Excel 資料類型資源庫的螢幕擷取畫面。":::

## <a name="search-for-power-bi-data-in-the-data-types-gallery"></a>搜尋資料類型資源庫中的 Power BI 資料

若要搜尋 Power BI 精選表格中的資料，請在 Excel 工作表中選取儲存格或範圍，其中所包含值符合精選表格中的值。 選取 [資料類型] 資源庫旁邊的 **更多** 箭號。

:::image type="content" source="media/service-excel-featured-tables/excel-data-types-more.png" alt-text="Excel 資料類型資源庫中更多圖示的螢幕擷取畫面。":::

如果看到想要尋找的表格，請加以選取。 否則，請選取 [組織中的更多內容]。 Excel 會搜尋您有權存取的所有精選表格，並尋找相符項目。

:::image type="content" source="media/service-excel-featured-tables/excel-more-your-organization.png" alt-text="從您組織中進行選取 (預覽) 的螢幕擷取畫面。":::
 
Excel 會顯示所有可能的表格。 在 [資料選取器] 窗格的 [篩選] 方塊中鍵入，以縮小選項範圍。 選取相符的表格。

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-store.png" alt-text="Excel 組織資料、供應商資料類型資料表的螢幕擷取畫面。":::
 
如果 Excel 找到具有高信賴度的相符資料列，儲存格就會立即連結至這些資料列。 已連結項目圖示表示儲存格已連結至 Power BI 的資料列。

:::image type="content" source="media/service-excel-featured-tables/excel-linked-card-icon.png" alt-text="已連結項目圖示的螢幕擷取畫面。":::

若儲存格有多個可能符合的資料列，則儲存格會顯示問號圖示，並隨即開啟 [資料選取器] 窗格。 在下列範例中，我們選取了 B3:B9 的範圍，然後選取了 Power BI 精選表格 **Store**。 除了儲存格 B9 "508 - Pasadena Lindseys" 之外，所有資料列都相符。 [資料選取器] 會顯示兩個可能的相符項目，即兩個不同表格中的相同值。

:::image type="content" source="media/service-excel-featured-tables/excel-question-mark-featured-table.png" alt-text="Excel [資料選取器] 窗格的螢幕擷取畫面。":::
 
[組織資料] 選項可傳回多個精選表格的資料列。 Excel 會依照來源的資料類型，分組可能符合的資料列。 Excel 會根據最有可能的相符資料列來排序資料類型。 使用＞形箭號來折疊及展開相符資料列的資料類型。

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-multiple.png" alt-text="具有多種可能性的 Excel [資料選取器] 窗格其螢幕擷取畫面。":::
 
針對每個建議，選取 [資料選取器] 窗格中資料列名稱來查看資料列內的詳細資料，以協助挑選正確的資料列。 找到資料列之後，請按 [選取] 來連結 Excel 中資料格的資料列。 

:::image type="content" source="media/service-excel-featured-tables/excel-data-selector-details.png" alt-text="[資料選取器] 詳細資料的螢幕擷取畫面。":::

## <a name="explore-related-data"></a>探索相關資料

現在您已建立 Excel 工作表值與 Power BI 精選表格資料之間的連線，接著可探索該資料。 請使用此資料來增強 Excel 報表。

### <a name="view-related-data-in-a-card"></a>檢視卡片中的相關資料 
 
在儲存格中選取 **卡片** 圖示以顯示卡片，其包含精選表格中所有欄位與計算欄位的資料。 卡片標題會顯示精選表格中 [資料列標籤] 欄位的值。
 
:::image type="content" source="media/service-excel-featured-tables/excel-linked-item-details.png" alt-text="連結項目詳細資料的螢幕擷取畫面。":::

### <a name="insert-related-data-from-power-bi"></a>插入 Power BI 中的相關資料 

選取 **插入資料** 圖示，然後從欄位清單中選取欄位名稱，將其值新增至方格中。  

:::image type="content" source="media/service-excel-featured-tables/excel-select-field.png" alt-text="選取欄位名稱的螢幕擷取畫面。":::

一或多個欄位值會放在相鄰儲存格中。 儲存格公式會參考所連結的儲存格及欄位名稱，因此可使用 Excel 函式中的資料。

:::image type="content" source="media/service-excel-featured-tables/excel-cell-formula.png" alt-text="Excel 儲存格公式的螢幕擷取畫面。":::

### <a name="use-cell-formulas"></a>使用儲存格公式

在 Excel 表格中，您可參考所連結的表格資料行，然後使用 `.` (句號) 參考來新增資料欄位。

:::image type="content" source="media/service-excel-featured-tables/excel-dot-reference.png" alt-text="Excel 句號參考的螢幕擷取畫面。":::

同樣地，在儲存格中，您可參考儲存格，並使用 `.` (句號) 參考來擷取欄位。

:::image type="content" source="media/service-excel-featured-tables/excel-cell-dot-reference.png" alt-text="儲存格句號參考的螢幕擷取畫面。":::

### <a name="show-a-card-change-or-convert-to-text"></a>顯示卡片、變更或轉換為文字

連結的儲存格已新增快顯功能表選項。 以滑鼠右鍵按一下儲存格。 依照一般的選項，您也會看到：

- **顯示資料類型卡片**。
- [資料類型] > [轉換成文字]。
- [資料類型] > [變更]。
- **重新整理**。

:::image type="content" source="media/service-excel-featured-tables/excel-right-click-data-type.png" alt-text="以滑鼠右鍵按一下 [轉換為文字] 的螢幕擷取畫面。":::
 
[轉換為文字] 會移除 Power BI 精選表格的資料列連結。 重要的是，儲存格中文字會是已連結儲存格的資料列標籤值。 如果將儲存格連結到不想連結的資料列，請在 Excel 中選取 [復原] 以還原初始的儲存格值。
 
## <a name="data-caching-and-refresh"></a>資料快取和重新整理

當 Excel 將儲存格連結至 Power BI 精選表格中資料列時，即會擷取並儲存該 Excel 檔案中所有欄位的值。 與您共用檔案的所有人都可參考任一欄位，而不必向 Power BI 要求資料。  

使用 [資料] 功能區中的 [全部重新整理] 按鈕，以重新整理已連結儲存格中的資料。 

:::image type="content" source="media/service-excel-featured-tables/excel-refresh-all.png" alt-text="[全部重新整理] 的螢幕擷取畫面。":::
 
您也可以重新整理個別的儲存格。 以滑鼠右鍵按一下儲存格，然後選取 [資料類型] > [重新整理]。

## <a name="licensing"></a>授權

Excel 資料類型資源庫和 Power BI 精選表格的連線體驗僅供 Excel E5 和 G5 客戶使用。 

## <a name="security"></a>安全性

您在 Power BI 中只會看到有權存取資料集的精選表格。 重新整理資料時，您必須有權存取 Power BI 的資料集，才能擷取資料列。 您需要有 Power BI [資料集的建置或寫入權限](../connect-data/service-datasets-build-permissions.md)。
 
Excel 會快取傳回的整列資料。 與您共用 Excel 檔案的所有人，都可以看到所有已連結儲存格中所有欄位的資料。

如果 Power BI 資料集已套用資料列層級安全性或 Microsoft 資訊保護的敏感度標籤，則 Excel 資料類型資源庫不會包含該資料集的精選表格。 這是初始預覽的限制。

## <a name="administrative-control"></a>系統管理控制

Power BI 系統管理員可管控組織中哪些人可使用 Excel 資料類型資源庫中的精選表格。 如需詳細資訊，請參閱系統管理中心中的[允許連線至精選資料表](../admin/service-admin-portal.md#allow-connections-to-featured-tables)。 
 
### <a name="auditing"></a>稽核

管理稽核記錄檔會顯示精選表格的下列事件：

- **AnalyzedByExternalApplication**：讓系統管理員看到哪些使用者正在存取哪些精選表格。
- **UpdateFeaturedTables**：讓系統管理員看到哪些使用者正在發佈與更新精選表格。

如需稽核記錄事件的完整清單，請參閱[追蹤 Power BI 中的使用者活動](../admin/service-admin-auditing.md)。

## <a name="considerations-and-limitations"></a>考量與限制

以下是初始預覽的限制：

- 僅 Excel 測試人員版本提供此整合。
- Excel 資料類型資源庫包含可供具有 Power BI Desktop 和 Power BI 服務適當授權使用者使用的精選表格。 預覽版本可能不支援 Power BI 服務，但日後會新增。
- Excel 不會顯示使用下列功能的 Power BI 資料集精選表格： 

    - 資料列層級安全性資料集。
    - 啟用 Microsoft 資訊保護的資料集。
    - DirectQuery 資料集。
    - 具有即時連線的資料集。

- Excel 只會顯示精選表格資料行和計算結果欄中的資料。 初始預覽不提供下列內容：

    - 精選表格上定義的量值。
    - 相關資料表上定義的量值，以及從關聯性計算的隱含量值。

- Excel 只會顯示儲存在新 Power BI 工作區中的精選表格 (「資料類型」)。 儲存在傳統工作區或 [我的工作區] 中的精選表格不會顯示為 Excel 資料類型。 您可在 Power BI 中[將傳統工作區升級為新工作區](service-upgrade-workspaces.md)。

Excel 中的資料類型體驗類似 lookup 函式。 其會接受 Excel 工作表提供的儲存格值，並會在 Power BI 精選表格中搜尋相符的資料列。 搜尋體驗具有下列行為：

- 使用 [組織資料] 按鈕來搜尋時，Excel 只會搜尋 Power BI 資料集中的精選表格。
- 資料列比對是以精選表格中的文字資料行為基礎。 使用與 Power BI Q&A 功能相同的索引，其已最佳化英文搜尋。 以其他語言搜尋可能不會產生正確的相符項目。 比對時不考慮數值資料行。
- 個別搜尋字詞的比對是以完全相符和前置詞相符為基礎。 儲存格值的分割依據為空格或其他空白字元，例如定位點。 然後，每個單字都視為搜尋字詞。 資料列的文字欄位值會和每個搜尋字詞進行完全相符和前置詞相符比較。 如果資料列的文字欄位以搜尋字詞開頭，則會傳回前置詞相符。 例如，如果儲存格包含 “Orange County”，則 “Orange” 和 “County” 會視為不同的搜尋字詞。 

    - 傳回文字資料行值完全符合 “Orange” 或 “County” 的資料列。 
    - 傳回文字資料行值以 “Orange” 或 “County” 開頭的資料列。 
    - 重要的是，不會傳回包含 “Orange” 或 “County” 但其不為開頭的資料列。

- Power BI 為每個儲存格最多傳回 100 項資料列建議。
- XMLA 端點不支援設定或更新精選表格
- 具有資料模型的 Excel 檔案可用來發佈精選表格。 將資料載入至 Power BI 桌面，然後發佈精選表格。
- 變更精選表格的 [資料表名稱]、[資料列標籤] 或 [索引鍵資料行]，會影響儲存格連結到資料表資料列的 Excel 使用者。 
- Excel 會顯示從 Power BI 資料集擷取資料的時間。 這個時間不一定是資料在 Power BI 中重新整理的時間，或資料集的最新資料點時間。 例如，假設 Power BI 的資料集在一週前重新整理過，而基礎來源資料在重新整理發生時已存在一週。 所以實際的資料時間是兩週，但 Excel 所顯示資料擷取日期/時間會是在 Excel 中提取資料的日期/時間。

## <a name="next-steps"></a>後續步驟

- [在 Power BI Desktop 中設定精選表格](service-create-excel-featured-tables.md)
- 若要了解如何[從 Power BI 使用 Excel 資料類型](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9)，請參閱 Excel 文件。
- 有問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)

