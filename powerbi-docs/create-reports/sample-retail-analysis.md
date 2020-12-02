---
title: 適用於 Power BI 的零售分析範例：觀看導覽
description: 適用於 Power BI 的零售分析範例：觀看導覽
author: maggiesMSFT
ms.author: maggies
ms.reviewer: amac
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 07/02/2019
LocalizationGroup: Samples
ms.openlocfilehash: 1a3a4bc467299f7baeb12ca68af1d2730d5839f0
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96395984"
---
# <a name="retail-analysis-sample-for-power-bi-take-a-tour"></a>適用於 Power BI 的零售分析範例：觀看導覽

零售分析範例內容套件包含儀表板、報表和資料集，用於分析跨多個門市和區域銷售之商品的零售銷售資料。 計量會比較今年與去年的各種表現：銷售量、單位、毛利率和變異數，以及新門市分析。 

![零售分析範例的儀表板](media/sample-retail-analysis/retail1.png)

此範例是系列中的一部分，說明您可如何使用 Power BI 的商業導向資料、報表與儀表板。 它是由 [obviEnce](http://www.obvience.com/) 使用真實資料 (已匿名化) 所建立。 資料會以數種格式提供：內容套件、.pbix Power BI Desktop 檔案，或 Excel 活頁簿。 請參閱 [Power BI 範例](sample-datasets.md)。 

此教學課程探索 Power BI 服務中的零售分析範例內容套件。 因為 Power BI Desktop 和服務中報表的使用體驗皆非常類似，因此您也可以在 Power BI Desktop 中使用範例 .pbix 檔案來進行教學課程。 

您不需要 Power BI 授權，即可在 Power BI Desktop 中瀏覽範例。 如果您沒有 Power BI Pro 授權，則可以將範例儲存到 Power BI 服務中的 [我的工作區]。 

## <a name="get-the-sample"></a>取得範例

 您必須先將範例下載為[內容套件](#get-the-content-pack-for-this-sample)、[.pbix 檔案](#get-the-pbix-file-for-this-sample)或 [Excel 活頁簿](#get-the-excel-workbook-for-this-sample)，才能使用範例。

### <a name="get-the-content-pack-for-this-sample"></a>取得此範例的內容套件

1. 開啟 Power BI 服務 (app.powerbi.com) 並登入，然後開啟您要儲存範例的工作區。 

    如果您沒有 Power BI Pro 授權，則可以將範例儲存到 [我的工作區]。

2. 在左下角選取 [取得資料]  。

    ![選取 [取得資料]](media/sample-datasets/power-bi-get-data.png)
3. 在顯示的 [取得資料]  頁面上，選取 [範例]  。
   
4. 選取 [零售分析範例]  ，然後選擇 [連線]  。  
  
   ![連線至範例](media/sample-retail-analysis/retail16.png)
   
5. Power BI 會匯入內容套件，然後將新儀表板、報表和資料集新增至您目前的工作區。
   
   ![零售分析範例項目](media/sample-retail-analysis/retail-entry.png)
  
### <a name="get-the-pbix-file-for-this-sample"></a>取得此範例的 .pbix 檔案

或者，您可以將零售分析範例下載為 [.pbix 檔案](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)，其設計目的是要用於 Power BI Desktop。 

### <a name="get-the-excel-workbook-for-this-sample"></a>取得此範例的 Excel 活頁簿

如果您想要檢視此範例的資料來源，其也有可用的 [Excel 活頁簿](https://go.microsoft.com/fwlink/?LinkId=529778) 格式。 活頁簿包含的 Power View 工作表可供您檢視及修改。 若要查看未經處理資料，請啟用「資料分析」增益集，然後選取 [Power Pivot] > [管理]  。 若要啟用 Power View 和 Power Pivot 增益集，請參閱[在 Excel 中探索 Excel 範例](sample-datasets.md#explore-excel-samples-inside-excel)以了解詳情。

## <a name="start-on-the-dashboard-and-open-the-report"></a>進入儀表板，然後開啟報表

1. 在儲存範例的工作區中，開啟 [儀表板]  索引標籤，然後尋找 [零售分析範例]  儀表板並加以選取。 
2. 在儀表板上，選取 [新門市和現有門市的門市總計]  圖格，該圖格將開啟至零售分析範例報表中的 [銷售門市概觀]  頁面。 

   ![[商店數總計] 磚](media/sample-retail-analysis/retail-analysis-7.png)  

   在此報表頁面上，您會看到我們共有 104 家門市，其中 10 家是新門市。 我們有兩種連鎖店：Fashions Direct 和 Lindseys。 Fashions Direct 的門市通常比較大。
3. 在 [依連鎖店劃分的本年度銷售量]  圓形圖中，選取 [Fashion Direct]  。

   ![[依連鎖店劃分的本年度銷售量] 圖表](media/sample-retail-analysis/retail3.png)  

   請注意 [總銷售額差異百分比]  泡泡圖中的結果：

   ![[總銷售差異百分比] 圖表](media/sample-retail-analysis/pbi_sample_retanlbubbles.png)  

   **FD-01** 區有 **每平方英呎最高的平均銷售額**，FD-02 區與去年相比的 **總銷售額差異** 最低。 FD-03 區和 FD-04 區的整體表現最差。
4. 選取個別泡泡或其他圖表，即可查看交叉醒目提示，呈現您選取範圍的影響。
5. 若要返回儀表板，請從頂端導覽窗格選取 [零售分析範例]  。

   ![導覽列](media/sample-retail-analysis/power-bi-breadcrumbs.png)
6. 在儀表板中，選取 [新門市和現有門市的本年度銷售量]  圖格，這相當於在問與答問題方塊中輸入 [本年度銷售量]  。

   ![[本年度銷售量] 圖格](media/sample-retail-analysis/pbi_sample_retanlthisyrsales.png)

   問與答的結果會出現：

   ![問與答中的本年度銷售量](media/sample-retail-analysis/retail7.png)

## <a name="review-a-tile-created-with-power-bi-qa"></a>檢閱為 Power BI 問與答所建立的磚
讓我們詳加說明。

1. 將問題變更為「**依區域** 劃分的本年度銷售量」  。 觀察結果：問與答會將答案自動呈現在橫條圖中，並建議其他片語：

   ![問與答中的依區域劃分的本年度銷售量](media/sample-retail-analysis/retail8.png)
2. 現在將問題變更為「**依郵遞區號和連鎖店** 劃分的本年度銷售量」  。

   請注意當您輸入並顯示適當的圖表時，Power BI 會如何回答問題。
3. 實驗更多問題，看看會得到何種結果。
4. 當您準備好時，請返回儀表板。

## <a name="dive-deeper-into-the-data"></a>深入探索資料
現在探討更詳細的層面，我們來查看區域的表現。

1. 在儀表板上，選取 [本年度銷售量、去年度銷售量]  圖格，該圖格將開啟報告的 [區域每月銷售額]  頁面。

   ![[本年度銷售量、去年度銷售量] 圖格](media/sample-retail-analysis/pbi_sample_retanlareacht.png)

   在 [依會計月份劃分的總銷售額差異百分比]  圖表中，您會發現與去年相比，差異百分比的變化很大，1月、4 月和 7 月是特別糟糕的月份。

   ![[依會計月份劃分的總銷售差異百分比] 圖表](media/sample-retail-analysis/pbi_sample_retanlsalesvarcol.png)

   現在來看看是否可以縮小範圍，找出問題所在。
2. 在泡泡圖中，選取 [020-Mens]  泡泡。

   ![選取 [020-Mens]](media/sample-retail-analysis/retail11.png)  

   您會觀察到，雖然男性類別在 4 月並沒有像整體生意那樣受到嚴重影響，但 1 月和 7 月仍是有問題的月份。
1. 現在選取 [010-Womens]  泡泡。

   ![選取 [010-Womens]](media/sample-retail-analysis/retail12.png)

   請注意，女性類別在所有月份的表現都比整體生意更差，而且每個月的表現幾乎也都不如去年。
1. 再次選取泡泡即可清除篩選條件。

## <a name="try-out-the-slicer"></a>試用交叉分析篩選器
我們來看一看特定區域的表現。

1. 在左上方的 [區域經理]  交叉分析篩選器中選取 [Allan Guinot]  。

   ![選取 [Allan Guinot]](media/sample-retail-analysis/retail13.png)

   請注意，與去年相比 Allan 的區域在 3 月和 6 月的表現優異。
2. 在 [Allan Guinot]  仍處於選取狀態時，請在泡泡圖中選取 [Womens-10]  泡泡。

   ![已選取 [Allan Guinot] 和 [Womens-10]](media/sample-retail-analysis/power-bi-allan.png)

   請注意，針對 [Womens-10] 類別，Allan 的區域沒有達到去年營業額。
3. 探索其他區域的經理和類別狀況；您可找出其他的見解嗎？
4. 當您準備好時，請返回儀表板。

## <a name="what-the-data-says-about-sales-growth-this-year"></a>有關本年度銷售成長的資料
我們要探討的最後一個領域，是透過檢查本年度新開的門市來探索我們的成長。

1. 選取 [依開幕月份、連鎖店劃分的本年度開幕門市]  圖格，開啟報表的 [新門市分析]  頁面。

   ![[新門市分析] 頁面](media/sample-retail-analysis/retail15.png)

   如圖格顯示，本年度開張的 Fashions Direct 門市比 Lindseys 門市更多。
2. 觀察 [依名稱劃分的每平方英呎銷售量]  圖表：

   ![[依名稱劃分的每平方英呎銷售量] 圖表](media/sample-retail-analysis/retail14.png)

    請注意新門市的平均銷售額/平方英呎差異。
3. 選取右上方圖表 [依開幕月份和連鎖店劃分的開幕門市計數]  中的 [Fashions Direct]  圖例項目。 請注意即使是同一系列的連鎖店，最佳門市 (Fashions Direct 溫徹斯特店) 的表現顯著優於最差門市 (Fashions Direct 辛辛那提 2 號店)，分別是 $21.22 美元及 $12.86 美元。

   ![已選取 Fashions Direct](media/sample-retail-analysis/power-bi-lindseys.png)
4. 選取 [名稱]  交叉分析篩選器中的 [Fashions Direct 溫徹斯特店]  ，然後觀察折線圖。 第一個銷售數字在二月報告。
5. 選取交叉分析篩選器中的 [Fashions Direct 辛辛那提 2 號店]  ，折線圖中顯示該門市於 6 月開幕，似乎是表現最差的門市。
6. 透過在整個圖表中選擇其他長條、折線和泡泡進行探索，並看看您可以找到哪些見解。

## <a name="next-steps-connect-to-your-data"></a>後續步驟：連線到您的資料
您可以在此環境盡情嘗試，因為您可以選擇不儲存您的變更。 但如果儲存了變更，您也可以隨時選取 [取得資料]  以取得此範例的新複本。

希望此教學已讓您了解 Power BI 儀表板、問與答和報表能夠如何提供範例資料的見解。 現在輪到您了，請連接到您自己的資料。 您可以透過 Power BI 連接到各式各樣的資料來源。 若要深入了解，請參閱[開始使用 Power BI 服務](../fundamentals/service-get-started.md)。
