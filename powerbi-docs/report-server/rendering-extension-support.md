---
title: PDF 轉譯延伸模組符合 ISO 14289-1 - Power BI 報表伺服器與 SSRS
description: 本文件描述 Power BI 報表伺服器和 SQL Server Reporting Services PDF 轉譯延伸模組是否符合 ISO 14289-1 (PDF/UA) 規格。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 11/04/2019
ms.openlocfilehash: eb2e3e599afad20401bfba0563041f8a7e442041
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418294"
---
# <a name="pdf-rendering-extension-conformance-to-iso-14289-1---power-bi-report-server--ssrs"></a>PDF 轉譯延伸模組符合 ISO 14289-1 - Power BI 報表伺服器與 SSRS

適用於︰Power BI 報表伺服器和 SQL Server Reporting Services (SSRS)

本文件描述 Power BI 報表伺服器和 SQL Server Reporting Services PDF 轉譯延伸模組是否符合 [ISO 14289-1 (PDF/UA)](https://www.pdfa.org/publication/pdfua-in-a-nutshell/) \(英文\) 規格。

> [!NOTE]
> 您可選取瀏覽器的 [列印]  ，然後選取 [儲存為 PDF]  來儲存或列印本白皮書。

## <a name="1--scope"></a>1.範圍

不適用

## <a name="2--normative-references"></a>2.基準參考

不適用

## <a name="3--terms-and-definitions"></a>3.詞彙和定義

不適用

## <a name="4--notation"></a>4.標記法

不適用

## <a name="5-version-identification"></a>5.版本識別

PDF 轉譯延伸模組提供 PDF/UA 的支援，如本文件中所述。 在某些情況下 (如下所述)，使用者有義務執行步驟，以確保 PDF 完全符合 PDF/UA 標準。  我們預期使用者會在此程序的最後一個步驟中新增適當的 PDF/UA 版本和符合性識別碼，指出已完成必要的工作，使得 PDF 完全符合 PDF/UA 標準。

本文件中列出的所有內容都是基於將裝置資訊設定 AccessiblePdf 設為 `true` 來轉譯 PDF 文件。 在某些情況下，合規性限制是因為報表定義語言 (RDL) 中的限制所導致。

## <a name="6--conformance-requirements"></a>6.符合性需求

|     準則     |     支援的功能     |     備註      |
|----|--------|--------|
|    6.1 一般    |                 支援    |    PDF 轉譯延伸模組會建立 PDF 版本 1.7。    |
|    6.2 符合的檔案    |                 支援但有例外狀況    |    請參閱第 7 節 - 檔案格式需求中的備註。    |
|    6.3 符合的讀取器    |     不適用     |         |
|    6.4 符合的輔助技術    |     不適用     |         |

## <a name="7--file-format-requirements"></a>7.檔案格式需求

|     準則     |     支援的功能     |     備註      |
|-----|-------|------------------------|
|    7.1 一般    |                 支援但有例外狀況    |    所有真實內容都應如 ISO 32000-1:2008, 14.8 中的定義加以標記。 不應在結構樹狀目錄中標記成品 (ISO 32000-1:2008, 14.8.2.2.2)。 <li> PDF 轉譯延伸模組不提供將個別項目明確標示為成品的彈性，因此它會改為將對應至 ISO 32000-1:2008, 14.8.2.2.2 中準則的各個項目成品化。<br>內容應該以邏輯讀取順序，使用語義上最適當的標記在結構樹狀目錄中標示。 <br> **注意事項** 4 WCAG 2.0，指導方針 1.4 針對協助工具的對比、色彩和其他格式的相關問題進行說明。 <br><li> 使用者必須確保其文件不會受限於這些問題。 <br>ISO 32000-1:2008, 14.8.4 中定義的標準標記不得重新對應。 <li> PDF 轉譯延伸模組不會重新對應標準標記。 Documents 會從 Document 根元素開始。 <br>聲稱符合此國際標準的檔案，其 Suspects 值應為 false (ISO 32000-1:2008, Table 321)。 <li> PDF 轉譯延伸模組沒有此 Suspects 項目。 此屬性是選擇性的。    |
|    7.2 文字    |                 支援但有例外狀況    |    內容應以邏輯讀取順序標記。 文件內容中的每個邏輯元素都必須使用語義上最適當的標記。 <br><li> PDF 轉譯延伸模組會盡可能在可行時，將內容以邏輯讀取順序標記。<br>字元碼應對應至 Unicode，如 ISO 32000-1:2008, 14.8.2.4.2 中所述。 Unicode 規格中未包含的字元可能會使用 Unicode 專用區，或宣告另一個字元編碼。 <br>自然語言應如 ISO 32000-1:2008, 14.9.2 中所討論及/或如 32000-1:2008, 7.9.2 中所述宣告。 應該宣告自然語言中的變更。 文字字串內自然語言中的變更 (例如，在替代的描述內) 應使用語言識別碼來宣告，如 ISO 32000-1:2008, 14.9.2.2 中所述。 <br><li> PDF 轉譯延伸模組只會在文件層級宣告自然語言    |
|    7.3 圖形    |                 支援但有例外狀況    |    除了文字物件以外的圖形物件，都必須使用如 ISO 32000-1:2008, 14.8.4.5, Table 340 中所述的 Figure 標記來標記。 如果下列任一例外狀況成立，則應該將圖形標記為成品： <br><li> 圖形未代表有意義的內容，或是 <li>  圖形會顯示為連結註解的背景，在此情況下，連結上的替代文字應該同時描述圖形和連結。 <li> PDF 轉譯延伸模組會使用 Figure 標記來標記圖形物件。 <br>伴隨著圖形的標題應該使用 Caption 標記來標記。 <li> PDF 轉譯延伸模組目前不會在含有 Caption 標記的圖形上標記標題。 <br>Figure 標記應包含可代表使用 Figure 標記來標記的替代表示法或取代文字，如 ISO 32000-1:2008, 14.7.2, Table 323 中所述。 <br>**注意事項** 1 另請參閱 WCAG 2.0，指導方針 1.1。 <br>如果圖形中呈現的文字未使用意欲要由人類讀者閱讀的自然語言文字，則應提供描述圖形本質或用途的替代文字。 <br>**注意事項** 2 文字範例的文字，或語言所使用的書寫系統範例，就是未使用自然語言的文字範例。   PDF 轉譯延伸模組支援在圖形上使用替代文字，但新增替代文字與否則由使用者自行決定。 <br>關於 BBox 屬性的其他注意事項： <br><li> PDF 轉譯延伸模組目前無法寫入 BBox 屬性。 <li> 因應措施是以新的 Figures 或 Artifacts 的方式手動重新標記圖例。    |
|    7.4 標題    |                 不適用    |    RDL 不支援以任何方式對標題標記。 使用者可以視需要將它們標記。    |
|    7.5 資料表    |                 支援但有例外狀況    |    資料表應該包含標頭。 資料表標頭應根據 ISO 32000-1:2008, Table 337 和 Table 349 來標記。 <br>**注意事項** 1 個資料表可以包含資料行標頭、資料列標頭或兩者。 <br>**注意事項** 2 當輔助技術依賴時，必須盡可能提供有關資料表結構資訊。 標頭在提供結構化資訊方面扮演重要的角色。 <br><li> 使用者可以視需要在其資料表中包含標頭。 RDL 和 PDF 轉譯延伸模組提供資料列標頭的支援。 <br>  TH 類型的結構元素應該有 Scope 屬性。   <li> PDF 轉譯延伸模組會對 Column 和 Row 成員的 TH 元素上包含 Scope 屬性，而不會對 Corner 資料格包含。<br>資料表標記結構僅應用來標記邏輯資料列和/或資料行關聯性中顯示的內容。   <li> 這取決於使用者選擇在其 RDL 中使用資料表的方式。    |
|    7.6 清單    |                 不適用    |    RDL 不支援清單的標記。 在 RDL 中，其結構上是具有單一資料表資料格的資料表。 <br>使用者可以視需要將它們重新標記。    |
|    7.7 數學運算式    |                 支援但有例外狀況    |    所有數學運算式都應該含括在 Formula 標記內，如 ISO 32000-1:2008, 14.8.4.5 中的詳細說明，而且應該具有 Alt 屬性。 <br><li> PDF 轉譯延伸模組目前未在 Formula 標記內含括數學運算式。 <br>將字元對應到 Unicode 的需求，應如 ISO 32000-1:2008, 9.10.2 和 14.8.2.4 中所闡述，套用至數學運算式。 <br><li> PDF 轉譯延伸模組支援此功能。    |
|    7.8 頁首及頁尾    |                 支援    |    執行頁首及頁尾應該識別為分頁成品，而且應該根據 ISO 32000-1:2008, 14.8.2.2.2, Table 330分類為 Header 或 Footer 子類型。 <br><li> 頁首或頁尾會被視為成品，並標記為成品。    |
|    7.9 注意事項和參考    |                 不適用    |    PDF 轉譯延伸模組不支援標記注意事項和參考。 <br>使用者可以視需要將它們標記。    |
|    7.10 選擇性內容    |                 不適用    |         |
|    7.11 內嵌的檔案    |                 不適用    |         |
|    7.12 文章執行緒    |                 不適用    |         |
|    7.13 數位簽章    |                 不適用    |         |
|    7.14 非互動式表單    |                 不適用    |         |
|    7.15 XFA    |                 不適用    |         |
|    7.16 安全性    |                 不適用    |         |
|    7.17 導覽    |                 支援    |    文件應包含符合讀取順序和導覽目標層級的文件大綱 (ISO 32000-1:2008, 12.3.3)。 <br><li> RDL 支援報表項目的書籤，但使用者必須選取此選項。 接著會由 PDF 轉譯延伸模組將這些書籤轉譯為文件大綱。 <br>如果存在，PageLabels 號碼樹狀目錄中的項目 (ISO 32000-1:2008, 7.7.2, Table 28) 應具有適當語義。 <br><li> PDF 轉譯延伸模組不包含 PageLabels 號碼樹狀目錄。    |
|    7.18 註解    |                 不適用    |    RDL 不支援註解    |
|    7.21 字型    |                 支援    |         |
|    7.21.1 一般    |                 支援    |         |
|    7.21.2 字型類型    |                 支援    |         |
|    7.21.3 複合字型    |                 支援    |         |
|    7.21.3.1 一般    |                 支援    |         |
|    7.21 3.2 CIDFonts    |                 支援    |         |
|    7.21.3.3 CMaps    |                 支援    |         |
|    7.21.4 內嵌    |                 支援    |         |
|    7.21.4.1 一般    |                 支援    |         |
|    7.21.4.2 子集內嵌    |                 支援    |         |
|    7.21.5 字型計量    |                 支援    |         |
|    7.21.6 字元編碼    |                 支援    |         |
|    7.21.7 Unicode 字元對應    |                 支援    |         |
|    7.21.8 使用 .notdef 字符    |                 支援    |         |

## <a name="8--conforming-reader-requirements"></a>8.符合讀者需求

不適用

## <a name="9--at-requirements"></a>9.AT 需求

不適用

## <a name="disclaimer"></a>Disclaimer

© 2017 Microsoft Corporation. All rights reserved. The names of actual companies and products mentioned herein may be the trademarks of their respective owners. The information contained in this document represents the current view of Microsoft Corporation on the issues discussed as of the date of publication. Microsoft cannot guarantee the accuracy of any information presented after the date of publication. Microsoft regularly updates its websites with new information about the accessibility of products as that information becomes available.

Customization of the product voids this conformance statement from Microsoft. Please consult with Assistive Technology (AT) vendors for compatibility specifications of specific AT products.

This document is for informational purposes only. MICROSOFT MAKES NO WARRANTIES, EXPRESS OR IMPLIED, IN THIS DOCUMENT.


## <a name="next-steps"></a>後續步驟
[系統管理員概觀](admin-handbook-overview.md)  

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)

