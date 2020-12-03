---
title: 從 Power BI Desktop 將報表匯出為 PDF 格式
description: 從 Power BI Desktop 輕鬆地匯出為 PDF，同時輕鬆地列印這些 PDF 報表
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 02/28/2019
LocalizationGroup: Create reports
ms.openlocfilehash: 815b8557b640de70690dcb90570f7764ff8c47a0
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96412981"
---
# <a name="export-reports-to-pdf-from-power-bi-desktop"></a>從 Power BI Desktop 將報表匯出為 PDF
在 **Power BI Desktop** 或 Power BI 服務中，可將報表匯出為 PDF 檔案，因此可輕鬆地利用該 PDF 分享或列印報表。

![匯出至 PDF](media/desktop-export-to-pdf/export-to-pdf_01.png)

將您的報表從 **Power BI Desktop** 匯出為 PDF 的程序，您如此即可列印 PDF 或與其他人分享該 PDF 文件，用法相當直接。 只要從 Power BI Deskop 選取 [檔案]> [匯出至 PDF]  即可。

**匯出至 PDF** 程序會匯出報表中所有 *可見* 的頁面，且每個報表頁面在 PDF 中會匯出為單一頁面。 目前看不到的報表頁面 (例如任何工具提示或隱藏的頁面)，並不會匯出至 PDF 檔案。 

![匯出至 PDF 正在處理中](media/desktop-export-to-pdf/export-to-pdf_02.png)

當您選取 檔案 > 匯出至 PDF  時，會起始匯出作業，同時會隨即出現對話方塊，顯示匯出程序正在進行中。 匯出程序完成之前，該對話方塊會一直停留在螢幕上。 匯出過程中，會停用所有與該匯出報表的互動。 要與該報表進行互動的唯一方法，就是等到匯出程序完成，或是取消該匯出。 

匯出完成時，會將 PDF 載入電腦上預設的 PDF 檢視器。 

## <a name="considerations-and-limitations"></a>考量與限制
使用 **匯出至 PDF** 功能時，請注意幾項考量：

* 此功能會匯出 Power BI 視覺效果，但並「不會」  匯出任何對報表套用的背景圖案。

因為背景圖案不會匯出至 PDF，所以請特別注意使用深色背景圖案的報表。 若您報表中的文字為淡色或是白色，以凸顯於深色的背景圖案上，即會因為背景圖案並不會與報表的其他部分一起匯出，而在匯出至 PDF 的程序中，發生不易閱讀或無法閱讀的情況。 



## <a name="next-steps"></a>後續步驟
在 **Power BI Desktop** 中有各式各樣有趣的視覺效果元素與功能。 如需有關資訊的詳細資訊，請參閱下列資源︰

* [使用視覺效果元素強化 Power BI 報表](desktop-visual-elements-for-reports.md)
* [Power BI Desktop 是什麼？](../fundamentals/desktop-what-is-desktop.md)
