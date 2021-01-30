---
title: 展開報表頁面之視覺效果的工具提示
description: 使用報表頁面工具提示的指引。
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 11/24/2019
ms.openlocfilehash: 1adb33dbff1de368d8d9b98ff0e7ad5f5f88387c
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99087836"
---
# <a name="extend-visuals-with-report-page-tooltips"></a>展開報表頁面之視覺效果的工具提示

本文適用於設計 Power BI 報表的報表作者。 其提供建立[報表頁面工具提示](../create-reports/desktop-tooltips.md)時的相關建議。

## <a name="suggestions"></a>建議

報表頁面工具提示可以改善報表使用者的體驗。 頁面工具提示可讓報表使用者快速且有效率地從視覺效果取得更深入的見解。 其可與不同的報表物件建立關聯：

- **視覺效果：** 您可以根據視覺效果，設定哪些視覺效果會顯示您的頁面工具提示。 您可以根據視覺效果，將視覺效果設定為不顯示任何工具提示、預設顯示視覺效果工具提示 (在視覺效果欄位窗格中設定)，或使用特定頁面工具提示。
- **視覺效果標題：** 您可以設定要顯示頁面工具提示的特定視覺效果。 報表使用者可以將游標停留在視覺效果標題圖示上來顯示頁面工具提示—請務必告知您的使用者有此圖示。

> [!NOTE]
> 報表視覺效果只會在工具提示頁面篩選與視覺效果的設計相容時，才顯示頁面工具提示。 例如，依「產品」  分組的視覺效果，與依「產品」  篩選的工具提示頁面相容。
>
> 頁面工具提示不支援互動功能。 如果您想要讓報表使用者進行互動，請改為建立[鑽研頁面](../create-reports/desktop-drillthrough.md)。
>
> Power BI 視覺效果不支援頁面工具提示。

以下是一些建議的設計案例：

- [不同的觀點](#different-perspective)
- [新增詳細資料](#add-detail)
- [新增說明](#add-help)

### <a name="different-perspective"></a>不同的觀點

頁面工具提示可以將與來源視覺效果相同的資料視覺化。 其做法是使用相同的視覺效果和樞紐分析群組，或使用不同的視覺效果類型。 頁面工具提示也可以套用與來源視覺效果所套用篩選的不同篩選。

下列範例顯示當報表使用者將游標停留在 [EnabledUsers]  值上時所發生的情況。 值的篩選內容是 2018 年 11 月的 Yammer。

![矩陣視覺效果顯示依資料列中年份和月份分組的值方格。 報表使用者已將游標停留在單一值上。 頁面工具提示已顯示。](media/report-page-tooltips/suggestion-different-perspective.png)

頁面工具提示隨即顯示。 其呈現不同的資料視覺效果 (折線圖和群組直條圖)，並套用對比時間篩選。 請注意，資料點的篩選內容是 2018 年 11 月。 但頁面工具提示會顯示「一整年所有月份」  的趨勢。

### <a name="add-detail"></a>新增詳細資料

頁面工具提示可以顯示其他詳細資料及新增內容。

下列範例顯示當報表使用者將游標停留在郵遞區號 98022 的 [Average of Violation Points] \(違規平均分數\)  值上時所發生的情況。

![資料表視覺效果顯示值方格，而資料表包含三個資料行。 頁面工具提示已顯示。](media/report-page-tooltips/suggestion-add-details.png)

頁面工具提示隨即顯示。 其呈現郵遞區號 98022 的特定屬性和統計資料。

### <a name="add-help"></a>新增說明

您可以將視覺效果標題設定為顯示視覺效果標題的頁面工具提示。 您可以使用 RTF 文字方塊，將說明文件新增至頁面工具提示。 也可以新增影像和圖形。

有趣的是，按鈕、影像、文字方塊和圖形也可以顯示視覺效果標題頁面工具提示。

下列範例顯示當報表使用者將游標暫留在[視覺效果標頭圖示](../create-reports/desktop-visual-elements-for-reports.md)上時所發生的情況。

![報表使用者已將游標停留在視覺效果標題圖示 (問號圖示) 上。 豐富的格式化工具提示已顯示。](media/report-page-tooltips/suggestion-add-help.png)

頁面工具提示隨即顯示。 在四個文字方塊中顯示 RTF 文字，以及一個圖形 (線條)。 頁面工具提示藉由描述視覺效果中顯示的每個縮寫來提供協助。

## <a name="recommendations"></a>建議

在報表設計階段，建議採用下列做法：

- **頁面大小：** 將您的頁面工具提示設定為小型。 您可以使用內建 **工具提示** 選項 (320 像素寬、240 像素高)。 或者，您可以設定自訂維度。 請小心不要使用太大的頁面大小，這可能會使來源頁面上的視覺效果模糊不清。
- **頁面檢視：** 在報表設計師中，將頁面檢視設定為 [實際大小]  (頁面檢視預設為 [符合一頁大小]  )。 如此一來，您就可以在設計時看到頁面工具提示的實際大小。
- **樣式：** 請考慮將頁面工具提示設計成使用與報表相同的主題和樣式。 如此一來，使用者就會覺得位於相同的報表中。 或者，為您的工具提示設計精美樣式，並請務必將此樣式套用至所有頁面工具提示。
- **工具提示篩選：** 將篩選指派給頁面工具提示，讓您可以在設計時預覽實際的結果。 發行報表之前，請務必移除這些篩選。
- **頁面可見度：** 請一律隱藏工具提示頁面 - 使用者不應直接巡覽至這些頁面。

## <a name="next-steps"></a>後續步驟

如需本文的詳細資訊，請參閱下列資源：

- [在 Power BI Desktop 中根據報表頁面建立工具提示](../create-reports/desktop-tooltips.md)
- [在 Power BI Desktop 中自訂工具提示](../create-reports/desktop-custom-tooltips.md)
- [使用視覺效果元素強化 Power BI 報表](../create-reports/desktop-visual-elements-for-reports.md)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com/)
