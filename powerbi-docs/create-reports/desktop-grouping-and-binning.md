---
title: 在 Power BI Desktop 中使用群組和量化
description: 了解如何在 Power BI Desktop 中群組和量化項目
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 12/18/2019
LocalizationGroup: Create reports
ms.openlocfilehash: 5f1b3d226fb7b27ebb31879d2f4a5c3489660b94
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96412912"
---
# <a name="use-grouping-and-binning-in-power-bi-desktop"></a>在 Power BI Desktop 中使用群組和量化
當 Power BI Desktop 建立視覺效果時，會根據在基礎資料中找到的值，將資料彙總成區塊 (或群組)。 通常沒有問題，但您偶爾會想要調整這些區塊的呈現方式。 例如，您可能想要將三種產品類別放在一個較大的類別 (一個「群組」  ) 中。 或者，您可能想要以量化大小 1,000,000 美元來查看銷售數字，而不是 923,983 美元大小的	區塊。

在 Power BI Desktop 中，您可以 *群組* 資料點，以協助您更清楚地檢視、分析及探索視覺效果中的資料和趨勢。 您也可以定義「量化大小」  ，將值放入大小相同的群組，好讓您以有意義的方式將資料視覺化。 此動作通常稱為「量化」  。

## <a name="using-grouping"></a>使用群組
若要使用群組，請按住 Ctrl 鍵，再按一下滑鼠來選取多個元素，以選取視覺效果上的兩個或多個元素。 然後以滑鼠右鍵按一下多重選取元素之一，並從操作功能表選擇 [群組]  。

![群組命令、圖形、群組、Power BI Desktop](media/desktop-grouping-and-binning/grouping-binning_1.png)

建立後，群組會新增至視覺效果的 [圖例]  貯體。 此群組也會出現在 [欄位]  清單中。

![圖例和欄位清單、群組、Power BI Desktop](media/desktop-grouping-and-binning/grouping-binning_2.png)

一旦擁有群組，您就可以輕鬆地編輯該群組的成員。 以滑鼠右鍵按一下 [圖例]  貯體或 [欄位]  清單中的欄位，然後選擇 [編輯群組]  。

![編輯群組命令、圖例和欄位清單、Power BI Desktop](media/desktop-grouping-and-binning/grouping-binning_3.png)

在 [群組]  對話方塊中，您可以建立新的群組或修改現有的群組。 您也可以將任何群組「重新命名」  。 只要按兩下 [群組和成員]  方塊中的群組標題，然後輸入新名稱。

您可以對群組進行各種動作。 您可以將 [未分組的值]  清單的項目新增到新的群組，或新增到其中一個現有群組。 若要建立新的群組，請從 [未分組的值]  方塊選取兩個或更多個項目 (使用 CTRL + 按一下)，然後選取該方塊下方的 [群組]  按鈕。

您可以將未分組的值新增至現有群組︰只要選取其中一個 [未分組的值]  ，然後選取要新增值的現有群組，然後選取 [群組]  按鈕。 若要從群組移除項目，請從 [群組及成員]  方塊加以選取，然後選取 [取消群組]  。 您也可以將未分組的類別移至 [其他]  群組，或讓其保留未分組狀態。

![[群組] 對話方塊、Power BI Desktop](media/desktop-grouping-and-binning/grouping-binning_4.png)

> [!NOTE]
> 您可以在 [欄位]  區中建立任何欄位的群組，而不需要從現有的視覺效果中選取多個項目。 只要以滑鼠右鍵按一下欄位，然後從出現的功能表中選取 [新增群組]  即可。

## <a name="using-binning"></a>使用量化
您可以在 **Power BI Desktop** 中，設定數值和時間欄位的量化大小。 您可以使用量化，將 Power BI Desktop 顯示的資料設為正確大小。

若要套用量化大小，請以滑鼠右鍵按一下 [欄位]  ，然後選擇 [新增群組]  。

![[新增群組] 命令、[欄位] 清單、Power BI Desktop](media/desktop-grouping-and-binning/grouping-binning_5.png)

從 [群組]  對話方塊，將 [量化大小]  設定為您要的大小。

![量化大小、[群組] 對話方塊、Power BI Desktop](media/desktop-grouping-and-binning/grouping-binning_6.png)

當您選取 [確定]  時，您會注意到 [欄位]  窗格中會顯示新欄位，並在名稱後面加上 **(二進位)** 。 然後，您可以將該欄位拖曳到畫布上，以在視覺效果中使用量化大小。

![將 bins 欄位拖曳到畫布上，Power BI Desktop](media/desktop-grouping-and-binning/grouping-binning_7.png)

若要查看 *量化* 的執行方式，請觀賞這段 [影片](https://www.youtube.com/watch?v=BRvdZSfO0DY)。

使用 *群組* 和 *量化* 可確保報表中的視覺效果只以您要的方式來顯示資料。
