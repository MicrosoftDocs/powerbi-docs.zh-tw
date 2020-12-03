---
title: Power BI Desktop 中以運算式為基礎的標題
description: 使用條件式程式設計格式，在 Power BI Desktop 中建立根據程式設計運算式變更的動態標題
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 04/10/2019
LocalizationGroup: Connect to data
ms.openlocfilehash: b7bcf06e075fc123a05cd7c184fbd9f12e006d24
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96414338"
---
# <a name="expression-based-titles-in-power-bi-desktop"></a>Power BI Desktop 中以運算式為基礎的標題

您可以為 Power BI 視覺效果建立自訂的動態標題。 藉由建立以欄位、變數或其他程式設計項目為基礎的資料分析運算式 (DAX)，您的視覺效果標題可以視需要自動調整。 這些變更是以篩選條件、選取項目或其他使用者互動和設定為基礎。

![Power BI Desktop 條件式格式設定選項的螢幕擷取畫面](media/desktop-conditional-formatting-visual-titles/expression-based-title-01.png)

建立動態標題 (有時稱為「以運算式為基礎的標題」  ) 很直接。 

## <a name="create-a-field-for-your-title"></a>建立標題的欄位

若要建立以運算式為基礎的標題，第一個步驟是在模型中建立用於標題的欄位。 

有各種充滿創意的方式，可讓視覺效果標題反映出您想要其顯示的內容，或是您想要表達的內容。 讓我們來看看一些範例。

您可以建立一個運算式，該運算式會根據視覺效果針對產品品牌名稱所擷取的篩選內容而變更。 下圖顯示這類欄位的 DAX 公式。

![DAX 公式的螢幕擷取畫面](media/desktop-conditional-formatting-visual-titles/expression-based-title-02.png)

另一個範例是使用根據使用者語言或文化特性而變更的動態標題。 您可以使用 `USERCULTURE()` 函式，在 DAX 量值中建立特定語言的標題。 此函式會根據其作業系統或瀏覽器設定，傳回使用者的文化特性代碼。 您可以使用下列 DAX switch 陳述式來選取正確的翻譯值。 

```
SWITCH (
  USERCULTURE(),
  "de-DE", “Umsatz nach Produkt”,
  "fr-FR", “Ventes par produit”,
  “Sales by product”
)
```

或者，也可以從包含所有翻譯的查閱資料表中擷取字串。 您會將該資料表放在您的模型中。 

這些只是幾個範例，您可以使用這些範例為 Power BI Desktop 中的視覺效果建立以運算式為基礎的動態標題。 您可以對標題執行的動作僅受限於您的想像力和模型。


## <a name="select-your-field-for-your-title"></a>選取標題的欄位

當針對您在模型中建立的欄位建立了 DAX 運算式之後，您必須將它套用到您的視覺效果標題。

若要選取欄位並加以套用，請移至 [視覺效果]  窗格。 在 [格式]  區域中，選取 [標題]  以顯示視覺效果的標題選項。 

當您以滑鼠右鍵按一下 **標題文字** 時，即會出現可讓您選取 [**fx <em>條件式格式設定]</em>** 的操作功能表。 當您選取該功能表項目時，[標題文字]  對話方塊隨即出現。 

![[標題文字] 對話方塊的螢幕擷取畫面](media/desktop-conditional-formatting-visual-titles/expression-based-title-02b.png)

您可以從該視窗中選取您建立用於標題的欄位。

## <a name="limitations-and-considerations"></a>限制與考量

目前實作視覺效果中以運算式為基礎的標題有一些限制：

* Python 視覺效果、R 視覺效果或關鍵影響因素視覺效果目前不支援以運算式為基礎的格式。
* 您為標題建立的欄位必須是字串資料類型。 目前不支援傳回數字或日期/時間 (或任何其他資料類型) 的量值。
* 當您將視覺效果釘選到儀表板時，不會沿用以運算式為基礎的標題。

## <a name="next-steps"></a>後續步驟

本文描述如何建立 DAX 運算式，以將視覺效果的標題轉換成動態欄位，而這些欄位會在使用者與您的報表互動時變更。 您也可能發現下列文章很有用。

* [設定資料表格式化的條件](desktop-conditional-table-formatting.md)
* [在 Power BI Desktop 中使用跨報表鑽研](desktop-cross-report-drill-through.md)
* [在 Power BI Desktop 中使用鑽研](desktop-drillthrough.md)
