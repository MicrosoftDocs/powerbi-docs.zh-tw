---
title: 人力資源範例：觀看導覽
description: 適用於 Power BI 的人力資源範例：觀看導覽
author: maggiesMSFT
ms.author: maggies
ms.reviewer: amac
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 07/05/2019
LocalizationGroup: Samples
ms.openlocfilehash: 94cb0d7f5ac83220f3b37f878add4f5bfa2caaf6
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96395869"
---
# <a name="human-resources-sample-for-power-bi-take-a-tour"></a>適用於 Power BI 的人力資源範例：觀看導覽

人力資源範例內容套件包含儀表板、報表，以及人力資源部門的資料集。 在此範例中，即使產業或規模不同，每家公司的人力資源部門皆具有相同的報表模型。 此範例著眼於新進員工、在職員工和離職員工。 它會致力於找出雇用策略中的任何趨勢。 我們的主要的目標是希望了解：

* 雇用的人員
* 徵才策略中的偏差
* 自願離職中的趨勢

![人力資源範例概觀的儀表板](media/sample-human-resources/hr1.png)

此範例是系列中的一部分，說明您可如何使用 Power BI 的商業導向資料、報表與儀表板。 它是由 [obviEnce](http://www.obvience.com/) 使用真實資料 (已匿名化) 所建立。 資料會以數種格式提供：內容套件、.pbix Power BI Desktop 檔案，或 Excel 活頁簿。 請參閱 [Power BI 範例](sample-datasets.md)。 

此教學課程探索 Power BI 服務中的人力資源範例內容套件。 因為 Power BI Desktop 和服務中報表的使用體驗皆非常類似，因此您也可以在 Power BI Desktop 中使用範例 .pbix 檔案來進行教學課程。 

您不需要 Power BI 授權，即可在 Power BI Desktop 中瀏覽範例。 如果您沒有 Power BI Pro 授權，則可以將範例儲存到 Power BI 服務中的 [我的工作區]。 

## <a name="get-the-sample"></a>取得範例

您必須先將範例下載為[內容套件](#get-the-content-pack-for-this-sample)、[.pbix 檔案](#get-the-pbix-file-for-this-sample)或 [Excel 活頁簿](#get-the-excel-workbook-for-this-sample)，才能使用範例。

### <a name="get-the-content-pack-for-this-sample"></a>取得此範例的內容套件

1. 開啟 Power BI 服務 (app.powerbi.com) 並登入，然後開啟您要儲存範例的工作區。

   如果您沒有 Power BI Pro 授權，則可以將範例儲存到 [我的工作區]。

2. 在左下角選取 [取得資料]  。
   
   ![選取 [取得資料]](media/sample-datasets/power-bi-get-data.png)
3. 在顯示的 [取得資料]  頁面上，選取 [範例]  。
   
4. 選取 [人力資源範例]  ，然後選擇 [連線]  。  
   
   ![連線至範例](media/sample-human-resources/pbi_hr_sample_connect.png)

5. Power BI 會匯入內容套件，然後將新儀表板、報表和資料集新增至您目前的工作區。
   
   ![人力資源範例項目](media/sample-human-resources/hr-sample-entry.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>取得此範例的 .pbix 檔案

或者，您可以將人力資源範例下載為 [.pbix](https://download.microsoft.com/download/6/9/5/69503155-05A5-483E-829A-F7B5F3DD5D27/Human%20Resources%20Sample%20PBIX.pbix) 檔案，其設計目的是要與 Power BI Desktop 搭配使用。

### <a name="get-the-excel-workbook-for-this-sample"></a>取得此範例的 Excel 活頁簿

如果您想要檢視此範例的資料來源，其也有可用的 [Excel 活頁簿](https://go.microsoft.com/fwlink/?LinkId=529780) 格式。 活頁簿包含的 Power View 工作表可供您檢視及修改。 若要查看未經處理資料，請啟用「資料分析」增益集，然後選取 [Power Pivot] > [管理]  。 若要啟用 Power View 和 Power Pivot 增益集，請參閱[在 Excel 中探索 Excel 範例](sample-datasets.md#explore-excel-samples-inside-excel)以了解詳情。

## <a name="new-hires"></a>新進員工
首先，我們來探索新進員工。

1. 在您的工作區中，選取 [儀表板]  索引標籤，然後開啟 [人力資源範例]  儀表板。
2. 在儀表板上，選取 [依月份的新進員工、去年相同期間的新進員工、在職員工 YoY % 變更]  圖格。  

   ![新進員工計數圖格](media/sample-human-resources/hr2.png)  

   人力資源範例報表會開啟 [ **新進員工** ] 頁面。  

   ![新進員工頁面](media/sample-human-resources/hr3.png)

3. 查看以下感興趣的項目：

    * [新進員工、新進員工 SPLY 和依月份在職員工 YoY % 變更]  組合圖表顯示，比起去年，我們今年每個月份都雇用更多員工。 有幾個月更是大幅成長。
    * 在 [ 依地區和民族的新進員工和在職員工]  組合圖中，可以注意到我們在 **東部** 地區雇用的員工變少了。
    * [依年齡群組的新進員工 YoY Var]  瀑布圖顯示我們雇用的主要是年輕員工。 此趨勢可能是因為這些工作大部分是兼職性質。
    * [依性別的新進員工]  圓形圖顯示性別分配大略平均。

    您可以找到其他見解嗎？ 例如，哪個區域性別分配不均。 

4. 選取圖表中不同的年齡群組和性別，以探索年齡、性別、地區和民族群組之間的關聯性。

5. 從頂端導覽窗格選取 [人力資源範例]  ，以返回儀表板。

   ![返回儀表板](media/sample-human-resources/power-bi-breadcrumbs.png)

## <a name="compare-currently-active-and-former-employees"></a>比較目前在職員工和離職員工
讓我們來探索目前在職員工的資料和不再於公司任職的員工資料。

1. 在儀表板中，選取 [ **依年齡群組的在職員工** ] 圖格。

   ![依年齡群組的在職員工圖格](media/sample-human-resources/pbi_hr_sample_activepie.png)

   人力資源範例報表會開啟 [**在職員工和離職員工比較**] 頁面。  

   ![在職員工和離職員工比較頁面](media/sample-human-resources/hr5.png)

 2. 查看以下感興趣的項目：

    * 左側的兩個組合圖顯示在職員工和離職員工的每年變更。 由於快速雇用，我們今年有更多在職員工，但離職員工也比去年多。
    * 相較於其他月份，8 月的離職員工更多。 選取不同的年齡群組、性別或地區，以查看是否可以找到任何極端值。
    * 透過圓形圖可發現，我們的在職員工和離職員工的性別和年齡群組分配平均。 選取不同年齡群組，以查看不同年齡的性別如何分配。 在每個年齡群組中，我們的性別分配是否平均？

## <a name="reasons-for-separation"></a>離職原因
讓我們使用編輯檢視來查看報表。 您可以變更圓形圖，以顯示離職員工資料，而不是在職員工資料。

1. 選取左上角的 [ **編輯報表** ]。

2. 選取 [ **依年齡群組的在職員工** ] 圓形圖。

3. 在 [欄位]  中選取 [員工]  ，以展開 [員工]  資料表。 清除 [在職員工計數]  ，以移除該欄位。

4. 選取 [員工]  資料表中的 [離職員工計數]  ，將它新增至 [欄位]  區中的 [值]  方塊。

5. 在報表畫布上，選取 [依離職原因的離職人員]  橫條圖中的 [自願]  列。 

   此列會在報表中以其他視覺效果反白顯示自願離職的員工。

6. 選取 [依年齡群組的離職員工]  圓形圖的 50 + 配量。

7. 查看右下角的折線圖。 此圖會篩選顯示自願離職的部分。  

   ![超過 50 歲的離職員工](media/sample-human-resources/pbi_hr_sample_sepsover50.png)

   請注意，50 歲以上群組中的趨勢。 在下半年期間，更多 50 歲以上的員工自願離職。 此趨勢是需要更多資料以進一步調查的領域。

8. 您也可以針對 [依性別的在職員工]  圓形圖遵循相同步驟，將它變更為離職員工，而不是在職員工。 查看依性別顯示的自願離職資料，看看是否能發現任何其他深入資訊。

9. 從頂端導覽窗格選取 [人力資源範例]  ，以返回儀表板。 您可以將所做的變更儲存至報表。

## <a name="bad-hires"></a>不當員工
最後要探索的部分是不當員工。 不當員工定義為沒有在職超過 60 天以上的員工。 我們雇用速度很快，但是否有雇用良好的人才？

1. 選取 [ **依年齡群組的不當員工 %** ] 儀表板圖格。 報表會開啟索引標籤三，即 [不適任員工]  。

   ![依年齡群組不適任員工佔在職員工的 %](media/sample-human-resources/hr7.png)  
2. 選取左側 [區域]  交叉分析篩選器中的 [西北部]  ，並在 [依性別的不適任員工計數]  環圈圖中選擇 [男性]  。 查看 [不適任員工]  頁面上的其他圖表。 請注意，不適任員工中的男性比女性多，且群組 A 中有許多不適任員工。

   ![西北部不適任員工](media/sample-human-resources/pbi_hr_sample_badhirespage.png)  

3. 如果您查看 [依性別的不適任員工計數]  環圈圖，並在 [區域]  交叉分析篩選器中選取不同的區域，您會注意到東部區域是不適任員工女性多於男性的唯一區域。  

4. 從頂端導覽窗格選取儀表板名稱，以返回儀表板。

## <a name="ask-a-question-in-the-dashboard-qa-box"></a>在儀表板問與答方塊中提問
在 [[問與答問題方塊]](power-bi-tutorial-q-and-a.md) 儀表板中，您可以使用自然語言提出您的資料問題。 問與答辨識您輸入的文字，然後找出在哪個資料集裡可以找到解答。

1. 選取問與答的問題方塊。 請注意，即使您還沒開始輸入，問與答也會顯示建議，以協助您提出問題。

   ![問與答方塊建議](media/sample-human-resources/pbi_hr_sample_qabox.png)

2. 您可挑選其中一個建議，或輸入：*顯示東部區域的年齡群組、性別和不適任員工*。  

   ![問與答方塊解答](media/sample-human-resources/pbi_hr_sample_qa_answer.png)

   請注意，大部分的女性不當員工都在 30 歲以下。

## <a name="next-steps-connect-to-your-data"></a>後續步驟：連線到您的資料
您可以在此環境盡情嘗試，因為您可以選擇不儲存您的變更。 但如果儲存了變更，您也可以隨時選取 [取得資料]  以取得此範例的新複本。

希望此教學已讓您了解 Power BI 儀表板、問與答和報表能夠如何提供範例資料的見解。 現在輪到您了，請連接到您自己的資料。 您可以透過 Power BI 連接到各式各樣的資料來源。 若要深入了解，請參閱[開始使用 Power BI 服務](../fundamentals/service-get-started.md)。
