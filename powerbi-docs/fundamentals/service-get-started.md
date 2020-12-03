---
title: 教學課程：開始在 Power BI 服務中建立
description: 開始使用 Power BI 線上服務 (app.powerbi.com)
author: mihart
ms.author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-fundamentals
ms.topic: tutorial
ms.date: 07/08/2020
LocalizationGroup: Get started
ms.openlocfilehash: 4e74bec243faad281c457caaa15a6edacf2b10cb
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96417121"
---
# <a name="tutorial-get-started-creating-in-the-power-bi-service"></a>教學課程：開始在 Power BI 服務中建立
本教學課程是 *Power BI 服務* 的部分功能簡介。 您會在本課程中連接資料、建立報表和儀表板，並詢問資料的相關問題。 您可以在 Power BI 服務中執行更多動作；本教學課程僅為了提高您的興趣。 若要了解 Power BI 服務如何與其他 Power BI 供應項目相配合，建議您參閱[什麼是 Power BI](power-bi-overview.md)。

您是報表的「讀者」，而非建立者嗎？ [開始使用 Power BI 服務](../consumer/end-user-experience.md)是一個非常好的起點。

:::image type="content" source="media/service-get-started/power-bi-service-rearranged-dashboard.png" alt-text="財務範例儀表板的螢幕擷取畫面。":::

在本教學課程中，您完成下列步驟：

> [!div class="checklist"]
> * 登入 Power BI 線上帳戶或註冊 (若您還沒有帳戶的話)。
> * 開啟 Power BI 服務。
> * 取得一些資料，並在報表檢視中予以開啟。
> * 使用該資料建立視覺效果，並將它另存為報表。
> * 釘選來自報表的磚來建立儀表板。
> * 使用問與答自然語言工具將其他視覺效果新增至儀表板。
> * 調整大小、重新排列，並在儀表板上編輯磚的詳細資料。
> * 刪除資料集、報表和儀表板來清除資源。

## <a name="sign-up-for-the-power-bi-service"></a>註冊 Power BI 服務
您需要 Power BI Pro 授權才能在 Power BI 中建立內容。 如果您沒有 Power BI 帳戶，請先[註冊免費 Power BI Pro 試用](https://app.powerbi.com/signupredirect?pbi_source=web)，再開始進行。

## <a name="step-1-get-data"></a>步驟 1：取得資料

一般來說，當您想要建立 Power BI 報表時，您會從 Power BI Desktop 開始。 Power BI Desktop 提供更多功能。 您可先轉換、塑造及為資料建立模型，再開始設計報表。 但這一次，我們會從頭開始在 Power BI 服務中建立報表。

在本教學課程中，我們會從簡易的 Microsoft Excel 檔案取得資料。 想要跟著做嗎？ [下載財務範例檔案](https://go.microsoft.com/fwlink/?LinkID=521962)。

1. 若要開始，請在瀏覽器中開啟 Power BI 服務 (app.powerbi.com)。 

    沒有帳戶嗎？ 別擔心，您可[註冊以取得免費的 Power BI Pro 試用](https://app.powerbi.com/signupredirect?pbi_source=web)

1. 在瀏覽窗格中選取 [我的工作區]。

1. 在 [我的工作區] 中，選取 [新增] > [上傳檔案]。

    [取得資料] 頁面隨即開啟。   

3. 在 [新增內容] 區段下方，確認已選取 [檔案]，然後選取儲存 Excel 檔案的位置。
   
    :::image type="content" source="media/service-get-started/power-bi-service-get-data-local-file.png" alt-text="[建立新內容] > [檔案] 的螢幕擷取畫面。":::

5. 瀏覽至電腦上的檔案，然後選擇 [開啟]。

5. 在本教學課程中，我們會選取 [匯入] 以將 Excel 檔案新增為資料集，然後使用該資料集建立報表和儀表板。 如果選取 [上傳]，則整個 Excel 活頁簿會上傳至 Power BI，且在其中，您可在 Excel Online 中進行開啟和編輯。
   
   :::image type="content" source="media/service-get-started/power-bi-import.png" alt-text="選擇 [匯入] 的螢幕擷取畫面。":::
6. 當準備好資料集時，請選取財務範例資料集旁邊的 [更多選項 (…)]，然後選取 [建立報表]。
1. 開啟報表編輯器。 

    :::image type="content" source="media/service-get-started/power-bi-service-datasets.png" alt-text="[所有內容] > [建立報表] 的螢幕擷取畫面。":::

    報表畫布是空白的。 我們會在右側看到 [篩選]、[視覺效果] 與 [欄位] 窗格。

    :::image type="content" source="media/service-get-started/power-bi-service-blank-report.png" alt-text="空白報表畫布的螢幕擷取畫面。":::

    > [!TIP]
    > 選取位於左上角的全域導覽按鈕來摺疊瀏覽窗格。 透過這種方式，畫布即會具備更多空間。
    >
    >:::image type="content" source="media/service-get-started/power-bi-global-nav-button.png" alt-text="[全域導覽] 按鈕。":::
    >

7. 您目前正在 [編輯] 檢視中。 請注意位於功能表列的 [閱讀檢視] 選項。 

    :::image type="content" source="media/service-get-started/power-bi-service-reading-view.png" alt-text="[閱讀檢視] 選項的螢幕擷取畫面。":::

    在 [編輯檢視] 時，可修改報表，因為您是報表的「擁有者」和「建立者」。 當與同事共用報表時，通常同事只能夠在 [閱讀檢視] 中與報表互動。 同事是您 **工作區** 中報表的「取用者」。 

## <a name="step-2-create-a-chart-in-a-report"></a>步驟 2：在報表中建立圖表
現在您已連線到資料，請開始進行探索。 當發現有趣的項目時，您可在報表畫布上儲存該項目。 接著您可將其釘選到儀表板以進行監視，並查看該項目隨時間的變化。 要緊的事要先做。
    
1. 請在報表編輯器中，使用頁面右側的 [欄位] 窗格來建立視覺效果。 選取 [Gross Sales] \(總銷售額\) 欄位，然後選取 [Date] \(日期\) 欄位。
   
   :::image type="content" source="media/service-get-started/power-bi-service-fields-pane-selected.png" alt-text="[欄位] 清單的螢幕擷取畫面。":::

    Power BI 會分析資料，並建立直條圖視覺效果。 

    > [!NOTE]
    > 若先選取 [Date] \(日期\) 欄位，而非 [Gross Sales] \(總銷售額\) 欄位，則會看見表格。 但別擔心！ 我們即將在下一個步驟中變更視覺效果。

    有些欄位的旁邊會有 Sigma 符號，因為 Power BI 偵測到其包含數值。

    :::image type="content" source="media/service-get-started/power-bi-sigma-fields.png" alt-text="具備 Sigma 符號的欄位。":::

2. 讓我們切換到顯示此資料的不同方式。 折線圖是顯示一段時間內數值的良好視覺效果。 從 [視覺效果] 窗格選取 **折線圖** 圖示。
   
   :::image type="content" source="media/service-get-started/power-bi-service-select-line-chart.png" alt-text="已選取折線圖的報表編輯器螢幕擷取畫面。":::

3. 這張圖表看起來很有趣，讓我們將它「釘選」到儀表板。 將滑鼠停留在視覺效果上，並選取釘選圖示。
   
   :::image type="content" source="media/service-get-started/power-bi-service-pin-visual.png" alt-text="[釘選] 圖示的螢幕擷取畫面。":::

4. 因為這是一份新報表，系統會提示您先儲存該報表，才可將視覺效果釘選到儀表板。 為報表命名 (例如「財務範例報表」)，然後選取 [儲存]。 

    您現在正在 [閱讀檢視] 中查看報表。 

6. 請再次選取 **釘選** 圖示。
 
5. 選取 [新增儀表板]，然後將其命名 (例如「財務範例儀表板」)。 
   
   :::image type="content" source="media/service-get-started/power-bi-pin.png" alt-text="命名儀表板的螢幕擷取畫面。":::
  
    靠近右上角的成功訊息可讓您知道，視覺效果已新增至儀表板，成為儀表板上的磚。
   
    :::image type="content" source="media/service-get-started/power-bi-pin-success.png" alt-text="[釘選到儀表板] 對話方塊的螢幕擷取畫面。":::

    現在您已釘選此視覺效果，該視覺效果會儲存在儀表板上。 資料會保持在最新狀態，如此即可透過一目了然的方式追蹤最新值。 但是，如果在報表中變更視覺效果類型，儀表板上的視覺效果將不會變更。

7. 選取 [移至儀表板]，即可查看新儀表板，以及您釘選為儀表板磚的折線圖。 
   
   :::image type="content" source="media/service-get-started/power-bi-service-dashboard-tile.png" alt-text="已釘選視覺效果的儀表板螢幕擷取畫面。":::
   
8. 請選取儀表板上新的磚。 Power BI 會讓您回到 [閱讀檢視] 中的報表。

1. 若要切換回 [編輯檢視]，請選取功能表列 > [編輯] 中的 [更多選項] (…)。

    :::image type="content" source="media/service-get-started/power-bi-service-edit-report.png" alt-text="選取 [編輯] 以編輯報表的螢幕擷取畫面。":::

    回到 [編輯檢視] 時，您即可繼續探索及釘選磚。

## <a name="step-3-explore-with-qa"></a>步驟 3：使用問與答進行探索

如要快速探索資料，請試著在問與答的問題方塊中提問。 問與答可供詢問與資料相關的自然語言查詢。 在儀表板中，[問與答] 方塊位於功能表列下方的頂端 (**詢問與資料相關的問題**)。 在報表中，其位於頂端的功能表列 (**詢問問題**)。

1. 若要返回儀表板，請選取黑色 **Power BI** 標題列中的 [我的工作區]。

    :::image type="content" source="media/service-get-started/power-bi-service-go-my-workspace.png" alt-text="回到 [我的工作區]。":::

1. 在 [我的工作區] 中，選取儀表板。

    :::image type="content" source="media/service-get-started/power-bi-service-dashboard-tab.png" alt-text="選取儀表板的螢幕擷取畫面。":::

1. 選取 [詢問資料相關問題]。 問與答會自動提供一些建議。 

    :::image type="content" source="media/service-get-started/power-bi-service-new-qanda.png" alt-text="[問與答] 畫布的螢幕擷取畫面。":::

    > [!NOTE]
    > 如果您沒有看到建議，請開啟 [新的問與答體驗]。

    :::image type="content" source="media/service-get-started/power-bi-new-qna-experience.png" alt-text="開啟全新 [問與答] 體驗的螢幕擷取畫面。":::

1. 某些建議會傳回單一值。 例如：選取 **什麼是平均齒輪**。

    問與答會搜尋答案，並以「卡片」視覺效果的形式呈現。

3. 選取 [釘選視覺效果] 並將此視覺效果釘選到財務範例儀表板。

    :::image type="content" source="media/service-get-started/power-bi-qna-pin-tile.png" alt-text="釘選視覺效果的螢幕擷取畫面。":::

1. 返回 [問與答]，然後選取 [顯示所有建議]。
1. 選取 [total profit by country] \(總收益 (依國家/地區)\)。 

    :::image type="content" source="media/service-get-started/power-bi-qna-total-profit-country.png" alt-text="總收益 (依國家/地區) 的螢幕擷取畫面。":::

1. 將對應也釘選到財務範例儀表板。

1. 在儀表板上，選取剛才釘選的對應。 看到其再次開啟 [問與答] 了嗎？ 
1. 將游標放在 [問與答] 方塊中的 [by country] \(依國家/地區\) 之後，然後鍵入 *as bar*。 Power BI 會使用結果來建立橫條圖。

    :::image type="content" source="media/service-get-started/power-bi-qna-profit-country-bar.png" alt-text="橫條圖視覺效果的螢幕擷取畫面。":::

1. 也請將橫條圖釘選到財務範例儀表板。

4. 選取 [結束問與答] 返回儀表板時，您即會看到剛建立的新磚。 

   :::image type="content" source="media/service-get-started/power-bi-service-dashboard-qna.png" alt-text="已釘選問與答視覺效果儀表板的螢幕擷取畫面。":::

   您會發現即使在 [問與答] 中將對應變更為橫條圖，磚仍會維持對應，因為在您釘選時其還是對應。 

## <a name="step-4-reposition-tiles"></a>步驟 4：重新置放磚

我們可以重新排列磚，以更充分利用儀表板的空間。

1. 將「總銷售額」折線圖磚的右下角往上拖曳，直到它與 [銷售量] 磚位於相同的高度，然後放開。

    :::image type="content" source="media/service-get-started/power-bi-service-resize-tile.png" alt-text="重新調整磚大小的螢幕擷取畫面。":::

    現在，這兩個磚具有相同的高度。

1. 針對 [COGS 平均] 磚選取 [更多選項 (…)] > [編輯詳細資料]。 

    :::image type="content" source="media/service-get-started/power-bi-tile-edit-details.png" alt-text="磚 [更多選項] 功能表的螢幕擷取畫面。":::

1. 在 [標題] 方塊中，鍵入「銷售貨物平均成本」 > [套用]。

    :::image type="content" source="media/service-get-started/power-bi-tile-details-dialog.png" alt-text="[編輯詳細資料] 對話方塊的螢幕擷取畫面。":::

1. 重新排列其他視覺效果以使其配合。

    這樣看起來更美觀。

    :::image type="content" source="media/service-get-started/power-bi-service-rearranged-dashboard.png" alt-text="重新排列後儀表板的螢幕擷取畫面。":::


## <a name="clean-up-resources"></a>清除資源
既然您已經完成本教學課程，就可以刪除資料集、報表和儀表板。 

1. 選取黑色 **Power BI** 標題列中的 [我的工作區]。
2. 選取財務範例資料集旁邊的 [更多選項 (…)] > [刪除]。

    :::image type="content" source="media/service-get-started/power-bi-service-delete-dataset.png" alt-text="刪除資料集的螢幕擷取畫面。":::

    您會看到一個警告，其通知 **所有包含此資料集資料的報表和儀表板磚都會遭到刪除**。

4. 選取 [刪除]。

## <a name="next-steps"></a>後續步驟

探索 Power BI 的 Microsoft Learn 內容系列：

- [學習 Power BI](/learn/powerplatform/power-bi?WT.mc_id=powerbi_landingpage-docs-link) (英文)
- [成為 Power BI 資料分析師](/users/microsoftpowerplatform-5978/collections/djwu3eywpk4nm) (英文)