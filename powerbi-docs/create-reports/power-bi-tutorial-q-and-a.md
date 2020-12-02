---
title: 使用 Power BI 問與答來探索及建立視覺效果
description: 如何使用 Power BI 問與答在儀表板和報表中建立新視覺效果。
author: maggiesMSFT
ms.author: maggies
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 05/13/2019
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 01ab8e63785680ea4fcd30cee170297f1cf1d674
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96396122"
---
# <a name="use-power-bi-qa-to-explore-your-data-and-create-visuals"></a>使用 Power BI 問與答來探索您的資料及建立視覺效果

有時若要從您的資料獲得解答，最快的方法是使用自然語言詢問問題。 Power BI 中的問與答功能可讓您使用您自己的用語來探索資料。  本文的第一個部分說明如何在 Power BI 服務的儀表板中使用「問與答」。 第二個部分說明在 Power BI 服務或 Power BI Desktop 中建立報表時，您可以使用「問與答」進行的動作。 如需更多背景，請參閱[取用者問與答](../consumer/end-user-q-and-a.md)文章。 

[Power BI 行動應用程式的問與答](../consumer/mobile/mobile-apps-ios-qna.md)和 [Power BI Embedded 的問與答](../developer/embedded/qanda.md)會在不同的文章中說明。 

問與答易於互動，甚至充滿樂趣。 通常，一個問題會帶來更多其他問題，原因在於視覺效果會顯示可探索的有趣路徑。 觀看 Amanda 示範使用問與答來建立視覺效果、深入探討這些視覺效果，以及將其釘選至儀表板。

<iframe width="560" height="315" src="https://www.youtube.com/embed/qMf7OLJfCz8?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="part-1-use-qa-on-a-dashboard-in-the-power-bi-service"></a>第 1 部分：在 Power BI 服務的儀表板上使用問與答

在 Power BI 服務 (app.powerbi.com) 中，儀表板包含從一或多個資料集釘選的磚，因此您可以詢問這些資料集包含的所有資料。 若要查看哪些報表和資料集已用來建立儀表板，請從功能表列選取 [檢視相關項目]  。

![檢視相關的報表和資料集](media/power-bi-tutorial-q-and-a/power-bi-view-related.png)

問與答問題方塊位於儀表板的左上角，這也是您用自然語言輸入問題的地方。 看不到問與答方塊嗎？ 請參閱 **取用者問與答** 文章中的 [考量與疑難排解](../consumer/end-user-q-and-a.md#considerations-and-troubleshooting)。  問與答會辨識您輸入的文字，然後找出哪裡 (哪個資料集) 可尋找解答。 問與答也可以用自動完成、重新描述，和其他文字及視覺輔助工具，協助您建立問題。

![顯示 Power BI 儀表板的螢幕擷取畫面，其中包含詢問與資料相關問題的選項。](media/power-bi-tutorial-q-and-a/powerbi-qna.png)

您問題的答案會顯示為互動式的視覺效果，而且每當您修改問題時便會更新。

1. 請開啟儀表板並將游標放在問題方塊中。 在右上角，選取 [新的問與答體驗]  。

    ![Power BI 新的問與答體驗](media/power-bi-tutorial-q-and-a/power-bi-qna-new-experience.png)

1. 即使您還沒開始輸入，問與答也會顯示包含建議的新畫面，以協助您提出問題。 您會在基礎資料集裡看到包含資料表名稱的片語和完整問題，甚至可能會看到列出完整問題，若資料集擁有者已建立[精選問題](service-q-and-a-create-featured-questions.md)。

   ![問與答建議的問題](media/power-bi-tutorial-q-and-a/power-bi-qna-suggested-questions.png)

   您可以選擇這些問題的其中一個做為起點，並繼續精簡問題，藉此尋找特定解答。 或者，使用資料表名稱來幫助您撰寫新的問題。

2. 從問題清單中選取，或開始輸入您自己的問題並從下拉式清單建議中選取。

   ![從清單中選取問題](media/power-bi-tutorial-q-and-a/power-bi-qna-select-a-question-how-many-stores.png)

3. 當您輸入問題時，問與答會挑選最佳的視覺效果來顯示您的答案。

   ![問與答依縣/市的商店數目](media/power-bi-tutorial-q-and-a/power-bi-qna-how-many-stores-by-state.png)

4. 當您修改問題時，視覺效果會動態變更。

   ![問與答以橫條圖顯示依縣/市的商店數目](media/power-bi-tutorial-q-and-a/power-bi-qna-stores-by-state-bar-chart.png)

1. 當您輸入問題時，Power BI 會使用在儀表板上有磚的任何資料集尋找最佳解答。  如果所有的圖格都來自 *datasetA* ，則您的答案將來自 *datasetA* 。  如果有磚來自 *datasetA* 和 *datasetB*，則問與答就會搜尋這 2 個資料集的最佳回應。

   > [!TIP]
   > 所以要小心，如果只有一個磚來自 *datasetA* ，而您從儀表板中移除了，問與答將不再有權存取 *datasetA* 。
   >

5. 如果您很滿意結果，請將視覺效果釘選到儀表板，方法是選取在右上角的釘選圖示。 如果儀表板已與您共用或為應用程式的一部分，您就無法釘選。

   ![問與答將視覺效果釘選](media/power-bi-tutorial-q-and-a/power-bi-qna-pin-visual.png)

## <a name="part-2-use-qa-in-a-report-in-power-bi-service-or-power-bi-desktop"></a>第 2 部分：在 Power BI 服務或 Power BI Desktop 中的報表使用問與答

使用問與答瀏覽您的資料集，以及將視覺效果新增至報表和儀表板。 報表是以單一資料集為基礎，且可能是完全空白或包含充滿視覺效果的頁面。 但是，只因為報表是空的並不表示沒有任何資料讓您探索 -- 資料集連結到報表，且正在等候您瀏覽並建立視覺效果。  若要查看使用哪個資料集來建立報表，請在 Power BI 服務的閱讀檢視中開啟報表，然後從功能表列選取 [檢視相關項目]  。

![檢視相關資料集](media/power-bi-tutorial-q-and-a/power-bi-view-related.png)

若要在報表中使用問與答，您必須具有報表與基礎資料集的編輯權限。 在[取用者問與答](../consumer/end-user-q-and-a.md)文章中，我們將此稱為「建立者」  案例。 如果相反地您是在「取用」  與您共用的報表，則將無法使用問與答。

1. 在編輯檢視中開啟報表 (Power BI 服務) 或在報表檢視中開啟報表 (Power BI Desktop)，然後從功能表列選取 [詢問問題]  。

    **Power BI Desktop**    
    ![在 Power BI Desktop 中選取詢問問題](media/power-bi-tutorial-q-and-a/power-bi-desktop-question.png)

    **服務**    
    ![在 Power BI 服務中選取詢問問題](media/power-bi-tutorial-q-and-a/power-bi-service.png)

2. 問與答問題方塊會顯示在報表畫布上。 下列範例中，問題方塊顯示在另一個視覺效果之上。 這是正常的，但將空白頁面新增至報表然後才提問，可能會是比較好的做法。

    ![顯示畫布的螢幕擷取畫面，其中視覺效果上包含了問與答的問題方塊。](media/power-bi-tutorial-q-and-a/power-bi-ask-question.png)

3. 請將游標放在 [問題] 方塊中。 當您輸入時，問與答會顯示可協助您形成問題的建議。

   ![在問與答的問題方塊中輸入](media/power-bi-tutorial-q-and-a/power-bi-q-and-a-suggestions.png)

4. 當您輸入問題時，問與答會挑選最佳的[視覺效果](../visuals/power-bi-visualization-types-for-reports-and-q-and-a.md)來顯示您的答案；而當您修改這個問題時，視覺效果就會動態改變。

   ![問與答建立視覺效果](media/power-bi-tutorial-q-and-a/power-bi-q-and-a-visual.png)

5. 當您有喜歡的視覺效果時，請選取 ENTER。 若要儲存報表的視覺效果，請選取 [檔案] > [儲存]  。

6. 與新的視覺效果互動。 您建立視覺效果的方式並不重要 -- 可以使用相同的所有互動性、格式和功能。

   ![與視覺效果互動](media/power-bi-tutorial-q-and-a/power-bi-q-and-a-ellipses.png)

   如果您在 Power BI 服務中建立視覺效果，您甚至可以[將它釘選至儀表板](service-dashboard-pin-tile-from-q-and-a.md)。

## <a name="tell-qa-which-visualization-to-use"></a>告訴問與答要使用的視覺效果
在使用問與答的時候，您不只可以要求要說明資料，也可以告訴 Power BI 要如何顯示答案。 只需在問題結尾加上「為<visualization type>」。  例如「依工廠顯示庫存量為地圖」和「顯示總庫存為卡片」。  請自己試試看吧。

## <a name="considerations-and-troubleshooting"></a>考量與疑難排解
- 如果您已使用即時連線或閘道連線到資料集，必須[針對該資料集啟用](service-q-and-a-direct-query.md)問與答。

- 您已開啟報表且沒有看到問與答的選項。 如果您使用 Power BI 服務，請務必在編輯檢視中開啟報表。 如果您無法開啟編輯檢視，則表示您沒有該報表的編輯權限，而您可以的該特定報表的問與答。

## <a name="next-steps"></a>後續步驟

- [取用者問與答](../consumer/end-user-q-and-a.md)   
- [在問與答中詢問問題的秘訣](../consumer/end-user-q-and-a-tips.md)   
- [準備適用於問與答的活頁簿](service-prepare-data-for-q-and-a.md)  
- [準備問與答的內部部署資料集](service-q-and-a-direct-query.md)   
- [從問與答將磚釘選至儀表板](service-dashboard-pin-tile-from-q-and-a.md)
