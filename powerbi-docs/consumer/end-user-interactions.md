---
title: 了解報表中的視覺效果互動方式
description: 適用於 Power BI 終端使用者的文件，說明視覺效果在報表頁面上的互動方式。
author: mihart
ms.author: mihart
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: pbi-explore
ms.topic: how-to
ms.date: 09/11/2020
LocalizationGroup: Reports
ms.openlocfilehash: bfb96a6c4d078744bdd285f07ea5cf88a55aab25
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96399871"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>如何在 Power BI 報表中相互進行視覺效果交叉篩選

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

Power BI 的其中一項絕佳功能，是報表頁面上所有視覺效果互連的方式。 如果您選取其中一個視覺效果的資料點，頁面上包含該資料的其他視覺效果就會全部根據該選取項目而變更。 

![視覺效果互動的影片](media/end-user-interactions/interactions.gif)

## <a name="how-visuals-interact-with-each-other"></a>視覺效果彼此互動的方式

根據預設，當您選取報表頁面上某個視覺效果中的資料點時，即會交叉篩選或交叉醒目提示頁面上的其他視覺效果。 頁面上視覺效果的確切互動方式由報表「設計者」  建立。 「設計者」  可以選擇開啟和關閉視覺效果互動，也可以選擇變更預設交叉篩選、交叉醒目提示和[切入](end-user-drill.md)行為。 

如果您尚未使用階層或切入，可以閱讀 [Power BI 中的向下切入](end-user-drill.md)，以了解相關資訊。 

### <a name="cross-filtering-and-cross-highlighting"></a>交叉篩選和交叉醒目提示

交叉篩選和交叉醒目提示有助於識別資料中某個值對另一個值的貢獻度。 「交叉篩選」  與「交叉醒目提示」  這兩個字詞用來區分本文所述的兩項行為：當您使用 [篩選]  窗格來篩選視覺效果及將其醒目提示時所發生的情況。  

讓我們在查看下列報表頁面時，定義這些詞彙。 「依區段的總類別量」環圈圖有兩個值：「審核」和「便利性」。 

![報表頁面](media/end-user-interactions/power-bi-interactions-before.png)

1. 看看當我們選取 [審核]  時會發生什麼事。

    ![選取環圈圖 [審核] 區段後的報表頁面](media/end-user-interactions/power-bi-interactions-after.png)

2. **交叉篩選** 會移除不適用的資料。 選取環圈圖的 [審核]  會交叉篩選折線圖。 折線圖現在只顯示 [審核] 區段的資料點。 

3. **交叉醒目提示** 會保留所有原始資料點，但會讓不適用所選範圍的部分變暗。 選取環圈圖的 [審核]  會交叉醒目提示直條圖。 直條圖會讓所有適用 [便利性] 區段的資料變暗，並醒目提示適用 [審核] 區段的所有資料。 


## <a name="considerations-and-troubleshooting"></a>考量與疑難排解
- 如果報表所含的視覺效果支援[切入](end-user-drill.md)，則根據預設，當您切入某個視覺效果時，不會影響報表頁面上的其他視覺效果。 不過，報表設計師  可以變更此行為，因此請檢查可鑽研的視覺效果，以查看報表設計師  是否已啟用 [鑽研篩選其他視覺效果]  。
    
- 交叉篩選和交叉醒目提示報表頁面上的其他視覺效果時，會保留視覺效果層級篩選。 因此，如果 VisualA 具有報表設計師或您所套用的視覺效果層級篩選，且您使用 visualA 與 visualB 互動，則來自 visualA 的視覺效果層級篩選即會套用至 visualB。

    ![顯示已設定篩選條件的報表頁面](media/end-user-interactions/power-bi-visual-filters.png)

## <a name="next-steps"></a>後續步驟
[如何使用報表篩選](../consumer/end-user-report-filter.md)


[關於篩選及醒目提示](end-user-report-filter.md)。
