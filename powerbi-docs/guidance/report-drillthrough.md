---
title: 使用報表頁面鑽研
description: 使用報表頁面鑽研的指引。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 11/28/2019
ms.openlocfilehash: 4aa7c3992183dad6fad30e31e31e935fbaa29c32
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418478"
---
# <a name="use-report-page-drillthrough"></a>使用報表頁面鑽研

本文適用於設計 Power BI 報表的報表作者。 其提供建立[報表頁面鑽研](../create-reports/desktop-drillthrough.md)時的相關建議。

建議您設計報表，以允許報表使用者完成下列流程：

1. 檢視報表頁面。
2. 識別要更深入分析的視覺元素。
3. 以滑鼠右鍵按一下視覺元素進行鑽研。
4. 執行免費的分析。
5. 返回來源報表頁面。

## <a name="suggestions"></a>建議

建議您考慮兩種類型的鑽研案例：

- [更深入](#additional-depth)
- [更廣泛的觀點](#broader-perspective)

### <a name="additional-depth"></a>更深入

當您的報表頁面顯示摘要結果時，鑽研頁面可將報表使用者引導至交易層級詳細資料。 此設計方法可讓使用者只在必要時才檢視支援的交易。

下列範例顯示當報表使用者從每月銷售摘要進行鑽研時所發生的情況。 鑽研頁面包含特定月份的詳細訂單清單。

![標題為「銷售摘要」的矩陣視覺效果會依資料列中的年份和月份，以及資料行中的國家/地區來分組銷售。 也會顯示鑽研頁面。](media/report-drillthrough/suggestion-drillthrough-add-depth.png)

### <a name="broader-perspective"></a>更廣泛的觀點

鑽研頁面可以達成與更深入相反的目標。 此案例非常適合用來鑽研至全面檢視。

下列範例顯示當報表使用者從郵遞區號進行鑽研時所發生的情況。 鑽研頁面會顯示該郵遞區號的一般資訊。

![資料表視覺效果包含三個資料行：[Zip Code]、[Average of Violation Points] 和 [Average of Grade Rating]。 也會顯示鑽研頁面。](media/report-drillthrough/suggestion-drillthrough-broader-perspective.png)

## <a name="recommendations"></a>建議

在報表設計階段，建議採用下列做法：

- **樣式：** 請考慮將鑽研頁面設計成使用與報表相同的主題和樣式。 如此一來，使用者就會覺得位於相同的報表中。
- **鑽研篩選：** 設定鑽研篩選，讓您可以在設計鑽研頁面時預覽實際的結果。 發行報表之前，請務必移除這些篩選。
- **其他功能：** 鑽研頁面就像任何報表頁面。 您甚至可以使用其他互動功能予以增強，包括交叉分析篩選器或篩選。
- **空白：** 避免新增在套用鑽研篩選之後可能顯示空白或產生錯誤的視覺效果。
- **頁面可見度：** 請考慮隱藏鑽研頁面。 如果您決定將鑽研頁面保持可見，請務必新增一個按鈕，讓使用者清除任何先前設定的鑽研篩選。 針對按鈕指派一個[書籤](../create-reports/desktop-bookmarks.md)。 該書籤應設定為移除所有篩選。
- **[上一頁] 按鈕：** 當您指派鑽研篩選時，會自動新增 [上一頁] [按鈕](../create-reports/desktop-buttons.md)。 建議予以保留。 如此一來，報表使用者就可以輕鬆地返回來源頁面。
- **探索：** 您可以設定視覺效果標題圖示文字，或將指示新增至文字方塊，以協助提升鑽研頁面的感知能力。 您也可以設計重疊，如[此部落格文章](https://alluringbi.com/2019/10/23/overlays-for-true-self-serve-reporting/)中所述。

> [!TIP]
> 您也可以將鑽研設定為 Power BI 編頁報表。 您可以透過將連結新增至 Power BI 報表來執行這項作業。 連結可以定義 [URL 參數](https://powerbi.microsoft.com/blog/url-parameters-for-paginated-reports-are-now-available/)。

## <a name="next-steps"></a>後續步驟

如需本文的詳細資訊，請參閱下列資源：

- [在 Power BI Desktop 中使用鑽研](../create-reports/desktop-drillthrough.md)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com/)
