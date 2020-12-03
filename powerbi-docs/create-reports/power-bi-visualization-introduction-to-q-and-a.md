---
title: 使用 Power BI 問與答建立視覺效果
description: 了解如何在 Power BI 服務中使用使用零售分析範例來建立問與答的視覺效果
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 05/13/2019
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 7eae93eb2b4594a180836f43a758c6bef7b3e90e
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415028"
---
# <a name="create-a-visual-with-power-bi-qa"></a>使用 Power BI 問與答建立視覺效果

有時若要從您的資料獲得解答，最快的方法是使用自然語言詢問問題。  在本文章中，我們將探討由兩種不同的方式來建立相同的視覺效果：第一種是在問與答中提問，第二種則是在報表中建立問。 我們將使用 Power BI 服務在報表中建立視覺效果，但使用 Power BI Desktop 的程序幾乎相同。

![Power BI 填滿了圖表](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-create-visual.png)

若要跟著做，您必須使用您可以編輯的報表，因此我們將使用 Power BI 提供的其中一個範例。

## <a name="create-a-visual-with-qa"></a>使用問與答建立視覺效果

我們要如何使用問與答建立此折線圖？

1. 從 Power BI 工作區選取 [取得資料]  \> [範例]  \> [零售分析範例]   > [連線]  。

1. 開啟 [零售分析範例] 儀表板，並將游標放在問與答方塊中：[詢問一個與資料相關的問題]  。

    ![將游標放在問與答方塊中](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-cursor-in-qna-box.png)

2. 在問與答方塊中，輸入類似以下問題的內容：
   
    **今年度銷售額和去年度銷售額，依月份，以區域圖形式**
   
    當您輸入您的問題後，問與答會挑選最佳的視覺效果來顯示您的答案；而當您修改這個問題時，視覺效果就會動態改變。 問與答也可以用建議、自動完成及拼字校正，協助您建立問題。 問與答會建議少量的用語變更：「今年度銷售額和去年度銷售額，依 *時間月份*，以區域圖形式」。  

    ![問與答更正了用語](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-corrected-create-filled-chart.png)

4. 選取該句子來接受建議。 
   
   當您完成問題輸入後，結果會是您在儀表板中所見的相同圖表。
   
   ![問與答填滿的區域圖](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-create-filled-chart.png)

4. 若要將圖表釘選至儀表板，請選取釘選圖示 ![釘選圖示](media/power-bi-visualization-introduction-to-q-and-a/pinnooutline.png) 報表圖示。

## <a name="create-a-visual-in-the-report-editor"></a>在報表編輯器中建立視覺效果

1. 巡覽回 [零售分析範例] 儀表板。
   
2. 儀表板包含「去年度銷售額和本年度銷售額」的相同區域圖的磚。  選取此圖格。 請勿選取您使用問與答建立的磚。 選取它會開啟問與答。 原始區域圖磚是在報表中建立，所以報表會開啟含有這個視覺效果的頁面。

    ![[零售分析範例] 儀表板](media/power-bi-visualization-introduction-to-q-and-a/power-bi-dashboard.png)

1. 選取 [編輯報表]  ，在 [編輯檢視] 中開啟報表。  如果您不是報表的擁有者，就不會有在 [編輯] 檢視中開啟報表的選項。
   
    ![[編輯報表] 按鈕](media/power-bi-visualization-introduction-to-q-and-a/power-bi-edit-report.png)
4. 選取區域圖，然後在 [欄位]  窗格中檢閱設定。  報表建立者建立了此圖表，方法是選取這三個值 (來自 [銷售額] 資料表的 [去年銷售量] 和 [本年度銷售額 > 值]，以及來自 [時間] 資料表的 [FiscalMonth])，然後在 [軸] 與 [值] 庫中組織這些值。
   
    ![[視覺效果] 窗格](media/power-bi-visualization-introduction-to-q-and-a/gnatutorial_3-new.png)

    您會看到它們最後有相同的視覺效果。 以這種方式來建立並不太複雜。 但使用問與答來建立較為簡單！

## <a name="next-steps"></a>後續步驟

- [在儀表板和報表中使用問與答](power-bi-tutorial-q-and-a.md)  
- [取用者問與答](../consumer/end-user-q-and-a.md)
- [讓資料適用於 Power BI 的問與答](service-prepare-data-for-q-and-a.md)

有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)
