---
title: 在 Power BI Desktop 中設定精選表格 (預覽)
description: 在 Power BI Desktop 中建立精選表格，以顯示在 Excel 的資料類型庫中。
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 09/17/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 20a81ed4675f6392f28a20f7b741d0c0ad1076eb
ms.sourcegitcommit: 4e347efd132b48aaef6c21236c3a21e5fce285cc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92680759"
---
# <a name="set-featured-tables-in-power-bi-desktop-preview"></a>在 Power BI Desktop 中設定精選表格 (預覽)

在 Excel 的資料類型庫中，使用者可在 Power BI 資料集的「精選表格」中尋找資料。 在本文中，您會了解如何在資料集中將表格設為「精選」。 這些標記可讓使用者更輕鬆地將企業資料新增至 Excel 工作表。 以下是設定與共用精選表格的基本步驟。

1. 您可在 Power BI Desktop 中找到自己資料集中的精選表格 (本文)
1. 將包含精選表格的這些資料集儲存到其中一個新工作區。 報表建立者可使用這些精選表格來建立報表。 
1. 組織的其他部門可連線到這些精選表格 (在 Excel 中稱為「資料類型」)，以取得相關和可重新整理的資料。 [在 Excel 中存取 Power BI 的精選表格 (預覽)](service-excel-featured-tables.md) 一文描述如何在 Excel 中使用這些精選表格。

> [!NOTE]
> 您可[在 Power BI 中升級或認證資料集](../collaborate-share/service-endorse-content.md)。 這稱為「背書」。 Excel 會優先處理資料類型資源庫中背書資料集內的表格。 Excel 會先列出認證資料集中的精選表格，然後列出升級資料集中的表格。 之後，Excel 會列出未背書資料集中的精選表格。 

## <a name="turn-on-the-featured-table-preview"></a>開啟精選表格預覽

1. 在 Power BI Desktop 中，選取 [檔案] > [選項及設定] > [選項] > [預覽功能]。
2. 選取 [Featured tables] \(精選表格\) 核取方塊。

    :::image type="content" source="media/service-excel-featured-tables/power-bi-preview-featured-tables.png" alt-text="預覽 [Featured tables] \(精選表格\) 選項":::

3. 重新啟動 Power BI Desktop。

## <a name="select-a-table"></a>選取資料表

1. 在 Power BI Desktop 中，移至 [模型] 檢視。

    :::image type="content" source="media/service-excel-featured-tables/power-bi-model-view.png" alt-text="預覽 [Featured tables] \(精選表格\) 選項":::
 
2. 選取資料表，然後將 [Is featured table] \(是否為精選表格\) 設為 [是]。

    :::image type="content" source="media/service-excel-featured-tables/power-bi-featured-table-yes.png" alt-text="預覽 [Featured tables] \(精選表格\) 選項":::

4. 在 [Set up this featured table] \(設定此精選表格\) 中提供必要欄位：

    - [描述]。 
        > [!TIP]
        > 描述開頭請使用「精選表格」，以利 Power BI 報表建立者加以識別。
    - Excel 會使用 [資料列標籤] 欄位值，所以使用者可輕鬆識別資料列。 其會顯示為已連結儲存格的資料格值，位於 [資料選取器] 窗格和 [資訊] 卡片中。 
    - [索引鍵資料行] 欄位值會提供資料列的唯一識別碼。 這個值可讓 Excel 將儲存格連結到資料表中的特定資料列。

    :::image type="content" source="media/service-excel-featured-tables/power-bi-set-up-featured-table.png" alt-text="預覽 [Featured tables] \(精選表格\) 選項":::

1. 當發佈或匯入資料集至 Power BI 服務後，Excel 的資料類型庫即會顯示精選表格。 您和其他報表建立者也可以此資料集為基礎來建立報表。

1. 在 Excel 中： 
    - Excel 會快取資料類型的清單，所以必須重新啟動 Excel，才能看到新發佈的精選表格。
    - 有些資料集不支援預覽功能，所以 Excel 不會顯示在這些資料集所定義的精選表格中。 如需詳細資料，請參閱下一節＜考量與限制＞。

## <a name="considerations-and-limitations"></a>考量與限制

以下是初始預覽的限制。

- Excel 不會顯示使用下列功能的 Power BI 資料集精選表格：

    - DirectQuery 資料集。
    - 具有即時連線的資料集。

- Excel 只會顯示精選表格資料行和計算結果欄中的資料。 初始預覽中不會提供相關資料表上定義的量值，以及從關聯性計算得出的隱含量值。
- Excel 只會顯示儲存在新 Power BI 工作區中的精選表格。 儲存在傳統工作區中的精選表格不會顯示為 Excel 資料類型。 您可在 Power BI 中[將傳統工作區升級為新工作區](service-upgrade-workspaces.md)。
- 如需其他 Excel 考量，請參閱＜在 Excel 中存取 Power BI 的精選表格＞一文中的[＜考量與限制＞](service-excel-featured-tables.md#considerations-and-limitations)。

## <a name="next-steps"></a>後續步驟

- [在 Excel 中存取 Power BI 的精選表格](service-excel-featured-tables.md)
- 請參閱 Excel 文件，了解如何[從 Power BI 使用 Excel 的資料類型](https://support.office.com/article/use-excel-data-types-from-power-bi-preview-cd8938ce-f963-444d-b82a-7140848241e9)。
- 有問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)

