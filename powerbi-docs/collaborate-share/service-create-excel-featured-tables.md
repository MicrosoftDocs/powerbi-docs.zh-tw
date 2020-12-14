---
title: 在 Power BI Desktop 中設定精選表格
description: 在 Power BI Desktop 中建立精選表格，如此其即會顯示在 Excel 組織資料類型庫中。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 12/07/2020
LocalizationGroup: Share your work
ms.openlocfilehash: 8c03263e7cc3a8833c06523601fcc12ef14484e1
ms.sourcegitcommit: 30d0668434283c633bda9ae03bc2aca75401ab94
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2020
ms.locfileid: "96906880"
---
# <a name="set-featured-tables-in-power-bi-desktop-to-show-in-excel-organization-data-types-gallery"></a>在 Power BI Desktop 中設定精選表格，以顯示在 Excel 組織資料類型庫中

在 Excel 的資料類型庫中，使用者可在 Power BI 資料集的「精選表格」中尋找資料。 在本文中，您會了解如何在資料集中將表格設為「精選」。 這些標記可讓使用者更輕鬆地將企業資料新增至 Excel 工作表。 以下是設定與共用精選表格的基本步驟。

1. 您可在 Power BI Desktop 中找到自己資料集中的精選表格 (本文)
1. 將包含精選表格的這些資料集儲存到其中一個新工作區。 報表建立者可使用這些精選表格來建立報表。 
1. 組織的其他部門可連線到這些精選表格 (在 Excel 中稱為「資料類型」)，以取得相關和可重新整理的資料。 [在 Excel 中存取 Power BI 的精選表格](service-excel-featured-tables.md)一文描述如何在 Excel 中使用這些精選表格。

> [!NOTE]
> 您可[在 Power BI 中升級或認證資料集](../collaborate-share/service-endorse-content.md)。 這稱為「背書」。 Excel 會優先處理資料類型資源庫中背書資料集內的表格。 Excel 會先列出認證資料集中的精選表格，然後列出升級資料集中的表格。 之後，Excel 會列出未背書資料集中的精選表格。 

> [!NOTE]
> 從 2020 年 12 月版的 Power BI Desktop 開始，預設可建立精選表格。 如果正在使用舊版，請升級 Power BI Desktop，或透過 [檔案] > [選項與設定] > [選項] > [預覽功能] 啟用 [精選表格] 功能。

## <a name="select-a-table"></a>選取資料表

1. 在 Power BI Desktop 中，移至 [模型] 檢視。

    :::image type="content" source="media/service-excel-featured-tables/power-bi-model-view.png" alt-text="[模型] 檢視":::
 
2. 選取資料表，然後將 [Is featured table] \(是否為精選表格\) 設為 [是]。

    :::image type="content" source="media/service-excel-featured-tables/power-bi-featured-table-yes.png" alt-text="將 [Is featured table] \(是否為精選表格\) 設為 [是]":::

4. 在 [Set up this featured table] \(設定此精選表格\) 中提供必要欄位：

    - [描述]。 
        > [!TIP]
        > 描述開頭請使用「精選表格」，以利 Power BI 報表建立者加以識別。
    - Excel 會使用 [資料列標籤] 欄位值，所以使用者可輕鬆識別資料列。 其會顯示為已連結儲存格的資料格值，位於 [資料選取器] 窗格和 [資訊] 卡片中。 
    - [索引鍵資料行] 欄位值會提供資料列的唯一識別碼。 這個值可讓 Excel 將儲存格連結到資料表中的特定資料列。

    :::image type="content" source="media/service-excel-featured-tables/power-bi-set-up-featured-table.png" alt-text="設定精選表格":::

1. 當發佈或匯入資料集至 Power BI 服務後，Excel 的資料類型庫即會顯示精選表格。 您和其他報表建立者也可以此資料集為基礎來建立報表。

1. 在 Excel 中： 
    - Excel 會快取資料類型的清單，所以必須重新啟動 Excel，才能看到新發佈的精選表格。
    - 不支援某些資料集。 這些資料集中定義的精選表格不會出現在 Excel 中。 如需詳細資料，請參閱下一節＜考量與限制＞。

## <a name="considerations-and-limitations"></a>考量與限制

目前的限制如下：

- 這項整合適用於目前通道的 Excel。
- Excel 不會顯示使用下列功能的 Power BI 資料集精選表格： 

    - DirectQuery 資料集。
    - 具有即時連線的資料集。

- Excel 只會顯示精選表格中所定義資料行、計算結果欄和量值中的資料。 不會提供下列內容：
   
    - 相關表格上定義的量值。
    - 從關聯性計算而來的隱含量值。

- Excel 只會顯示儲存在新 Power BI 工作區中的精選表格 (「資料類型」)。 儲存在傳統工作區中的精選表格不會顯示為 Excel 資料類型。 您可在 Power BI 中[將傳統工作區升級為新工作區](service-upgrade-workspaces.md)。

Excel 中的資料類型體驗類似 lookup 函式。 其會接受 Excel 工作表提供的儲存格值，並會在 Power BI 精選表格中搜尋相符的資料列。 搜尋體驗具有下列行為：

- 資料列比對是以精選表格中的文字資料行為基礎。 使用與 Power BI Q&A 功能相同的索引，其已最佳化英文搜尋。 以其他語言搜尋可能不會產生正確的相符項目。 
- 比對時不考慮大部分數值資料行。 如果資料列標籤或索引鍵資料行是數值，則會納入比對。
- 個別搜尋字詞的比對是以完全相符和前置詞相符為基礎。 儲存格值的分割依據為空格或其他空白字元，例如定位點。 然後，每個單字都視為搜尋字詞。 資料列的文字欄位值會和每個搜尋字詞進行完全相符和前置詞相符比較。 如果資料列的文字欄位以搜尋字詞開頭，則會傳回前置詞相符。 例如，如果儲存格包含 “Orange County”，則 “Orange” 和 “County” 會視為不同的搜尋字詞。 

    - 傳回文字資料行值完全符合 “Orange” 或 “County” 的資料列。 
    - 傳回文字資料行值以 “Orange” 或 “County” 開頭的資料列。 
    - 重要的是，不會傳回包含 “Orange” 或 “County” 但其不為開頭的資料列。

- Power BI 為每個儲存格最多傳回 100 項資料列建議。
- 不支援某些符號。
- XMLA 端點不支援設定或更新精選表格
- 具有資料模型的 Excel 檔案可用來發佈精選表格。 將資料載入至 Power BI Desktop，然後發佈精選表格。
- 變更精選表格中的 [資料表名稱]、[資料列標籤] 或 [索引鍵資料行]，可能會影響儲存格連結到資料表資料列的 Excel 使用者。 
- Excel 會顯示從 Power BI 資料集擷取資料的時間。 這個時間不一定是資料在 Power BI 中重新整理的時間，或資料集的最新資料點時間。 例如，假設 Power BI 的資料集在一週前重新整理過，而基礎來源資料在重新整理發生時已存在一週。 所以實際的資料時間是兩週，但 Excel 所顯示資料擷取日期/時間會是在 Excel 中提取資料的日期/時間。
- 如需其他 Excel 考量，請參閱＜在 Excel 中存取 Power BI 的精選表格＞一文中的[＜考量與限制＞](service-excel-featured-tables.md#considerations-and-limitations)。

## <a name="next-steps"></a>後續步驟

- [在 Excel 中存取 Power BI 的精選表格](service-excel-featured-tables.md)
- 請參閱 Excel 文件，了解如何[從 Power BI 使用 Excel 的資料類型](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9)。
- 有問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)

