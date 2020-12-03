---
title: Power BI 的客戶獲利率範例：觀看導覽
description: Power BI 的客戶獲利率範例：觀看導覽
author: maggiesMSFT
ms.author: maggies
ms.reviewer: amac
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 07/05/2019
LocalizationGroup: Samples
ms.openlocfilehash: adc642d5366949e547e0115badd5e800ffa04bb0
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415097"
---
# <a name="customer-profitability-sample-for-power-bi-take-a-tour"></a>Power BI 的客戶獲利率範例：觀看導覽

客戶獲利率範例內容套件包含製作行銷資料的公司儀表板、報表和資料集。 財務長建立這個儀表板是為了查看其五個業務單位經理 (主管)、產品、客戶和毛利 (GM) 的關鍵計量。 他們一眼即可看出影響獲利率的因素。

![客戶獲利率範例的儀表板](media/sample-customer-profitability/power-bi-dash.png)

此範例是系列中的一部分，說明您可如何使用 Power BI 的商業導向資料、報表與儀表板。 它是由 [obviEnce](http://www.obvience.com/) 使用真實資料 (已匿名化) 所建立。 資料會以數種格式提供：內容套件、.pbix Power BI Desktop 檔案，或 Excel 活頁簿。 請參閱 [Power BI 範例](sample-datasets.md)。 

此教學課程探索 Power BI 服務中的客戶獲利率範例內容套件。 因為 Power BI Desktop 和服務中報表的使用體驗皆非常類似，因此您也可以在 Power BI Desktop 中使用範例 .pbix 檔案來進行教學課程。 

您不需要 Power BI 授權，即可在 Power BI Desktop 中瀏覽範例。 如果您沒有 Power BI Pro 授權，則可以將範例儲存到 Power BI 服務中的 [我的工作區]。 

## <a name="get-the-sample"></a>取得範例

您必須先將範例下載為[內容套件](#get-the-content-pack-for-this-sample)、[.pbix 檔案](#get-the-pbix-file-for-this-sample)或 [Excel 活頁簿](#get-the-excel-workbook-for-this-sample)，才能使用範例。

### <a name="get-the-content-pack-for-this-sample"></a>取得此範例的內容套件

1. 開啟 Power BI 服務 (app.powerbi.com) 並登入，然後開啟您要儲存範例的工作區。

   如果您沒有 Power BI Pro 授權，則可以將範例儲存到 [我的工作區]。

2. 在左下角選取 [取得資料]  。

   ![選取 [取得資料]](media/sample-datasets/power-bi-get-data.png)
3. 在顯示的 [取得資料]  頁面上，選取 [範例]  。

4. 選取 [客戶獲利率範例]  ，然後選擇 [連接]  。  

    ![連線至範例](media/sample-customer-profitability/get-supplier-sample.png)
5. Power BI 會匯入內容套件，然後將新儀表板、報表和資料集新增至您目前的工作區。

    ![進入客戶獲利率範例](media/sample-customer-profitability/customer-profitability-sample-entry.png)

### <a name="get-the-pbix-file-for-this-sample"></a>取得此範例的 .pbix 檔案

或者，您可以將[客戶獲利率範例](https://download.microsoft.com/download/6/A/9/6A93FD6E-CBA5-40BD-B42E-4DCAE8CDD059/Customer%20Profitability%20Sample%20PBIX.pbix)下載為 .pbix 檔案，其設計目的是要用於 Power BI Desktop。

### <a name="get-the-excel-workbook-for-this-sample"></a>取得此範例的 Excel 活頁簿

如果您想要檢視此範例的資料來源，其也有可用的 [Excel 活頁簿](https://go.microsoft.com/fwlink/?LinkId=529781) 格式。 活頁簿包含的 Power View 工作表可供您檢視及修改。 若要查看未經處理資料，請啟用「資料分析」增益集，然後選取 [Power Pivot] > [管理]  。 若要啟用 Power View 和 Power Pivot 增益集，請參閱[在 Excel 中探索 Excel 範例](sample-datasets.md#explore-excel-samples-inside-excel)以了解詳情。

## <a name="what-is-our-dashboard-telling-us"></a>儀表板告訴我們什麼？

在您儲存範例的工作區中，尋找並選取客戶獲利率儀表板：

![客戶獲利率範例的儀表板](media/sample-customer-profitability/power-bi-dash.png)

### <a name="company-wide-dashboard-tiles"></a>全公司的儀表板圖格
1. 開啟 Power BI 服務中的儀表板。 該儀表板磚可讓 CFO 看到對他們而言很重要的高階公司計量。 當他們看到值得關注的項目時，可以選取磚來深入探究資料。

2. 檢閱儀表板左側的磚。

    ![經理的磚](media/sample-customer-profitability/power-bi-manager.png)

   注意下列詳細資料：
   - 公司的毛利為 42.5%。
   - 有 80 位客戶。
   - 銷售五種不同的產品。
   - 對預算的營收 % 差異在二月為最低，但在三月來到最高。
   - 我們的營收大部分來自東部和北部區域。 毛利從未超過預算，ER-0 和 MA-0 業務單位則需要進一步調查。
   - 年度總收益接近預算。

### <a name="manager-specific-dashboard-tiles"></a>經理特定儀表板圖格
儀表板右側的磚能提供小組計分卡。 財務長需要追蹤其轄下經理，而這些磚能讓他們使用 GM% 來全面掌握收益狀況。 如果任一經理的 GM% 趨勢不盡人意，他們就可以進一步調查。

![管理員的 GM %](media/sample-customer-profitability/power-bi-manager2.png)

藉由分析經理特定儀表板磚，我們可能會發現：

- 除了 Carlos 以外的所有主管皆已超越其銷售目標。 不過，Carlos 的實際銷售額是最高的。
- Annelie 的 GM% 最低，但我們可以看到其在三月之後穩定增加。
- 相反地，Valery 的 GM% 卻巨幅下滑。
- Andrew 這一年的變動劇烈。

## <a name="explore-the-dashboards-underlying-data"></a>探索儀表板的基礎資料
儀表板具有連結到報表和 Excel 活頁簿的磚。

### <a name="open-the-excel-online-data-source"></a>開啟 Excel 線上資料來源
此儀表板上的兩個磚 [目標與實際]  和 [每年營收成長]  ，都是從 Excel 活頁簿釘選而來。 當您選取其中任何一個磚時，Power BI 隨即開啟資料來源 (在此案例中為 Excel Online)。

![Excel Online](media/sample-customer-profitability/power-bi-excel-online.png)

1. 選取從 Excel 釘選的其中一個磚。 Excel Online 會在 Power BI 服務內開啟。
2. 請注意該活頁簿的資料分散於三個索引標籤中。 開啟 [營收]  。
3. 我們來看看 Carlos 還未達到其目標的原因：  

    a. 從 [主管]  滑桿，選取 [Carlos Grilo]  。   

    b. 從第一個樞紐分析表可看出 Carlos 銷售最多的產品 Primus，其營收成長與去年相比下降了 152%。 [每年營收差異]  圖表顯示 Carlos 在大多數月份中的預算都低於標準。  

    ![樞紐分析表](media/sample-customer-profitability/power-bi-pivotchart.png)

    ![Carlos 的結果](media/sample-customer-profitability/power-bi-carlos.png)

4. 繼續探索。 如果發現感興趣的項目，請選取右上角的 [釘選]  ![釘選圖示](media/sample-customer-profitability/power-bi-excel-pin.png) [將其釘選到儀表板](service-dashboard-pin-tile-from-excel.md)。

5. 使用瀏覽器的上一頁箭頭來返回儀表板。

### <a name="open-the-underlying-power-bi-report"></a>開啟基礎 Power BI 報表
客戶獲利率範例儀表板上大部分的磚，都是從基礎客戶獲利率範例報表釘選而來。

1. 選取其中一個磚，以在 [閱讀檢視] 中開啟該報表。

   如果此磚是在問與答中建立，選取此磚會開啟問與答視窗。 選取 [結束問與答]  以返回儀表板並嘗試其他磚。

2. 報表有三頁。 報表底部的每個索引標籤都代表一個不同頁面。

    ![底部的三個索引標籤](media/sample-customer-profitability/power-bi-report-tabs.png)

    * [小組計分卡]  著重於五位經理的績效及其客戶個資清冊。
    * [產業毛利分析]  提供一種方法，用以分析相較於整個產業現況的獲利率。
    * [主管計分卡]  以自訂頁面大小格式提供每位經理的檢視。

### <a name="team-scorecard-page"></a>[小組計分卡] 頁面
![[小組計分卡] 報表分頁](media/sample-customer-profitability/customer2.png)

讓我們仔細觀察兩個小組成員，看看有什麼發現： 

1. 在左側的 [主管]  交叉分析篩選器中，選取 Andrew 的名字來篩選報表頁面，只顯示與他有關的資料：

   * 如需快速查看 KPI，請查看 Andrew 的 [營收狀態 (整年)]  ；呈現綠色，表示他的業績很好。
   * [按月和主管對預算的營收百分比差異]  圖表顯示，除了二月份下跌，Andrew 的表現都很不錯。 Andrew 最主要的區域是東部區域，包括 49 個客戶和 5 個產品 (共 7 個)。 Andrew 的 GM% 不是最高或最低。
   * [今年營收和按月對預算的營收 % 差異]  圖表顯示平穩甚至有獲利。 不過，如果您在區域矩形式樹狀結構圖中選取 [中部]  方塊進行篩選時，您會發現 Andrew 只有三月份在印第安納州有營收。 此意圖是故意為之，還是有什麼需要一探究竟嗎？

2. 現在來看看 Valery。 在 [主管]  交叉分析篩選器中，選取 Valery 的名字來篩選報表頁面，只顯示與 Valery 有關的資料。 

   ![Valery 的資料](media/sample-customer-profitability/customer3.png)

   * 請注意 [營收狀態 (整年)]  的紅色 KPI。 此項目肯定需要進一步調查。
   * Valery 的營收差異也十分令人擔憂，Valery 連設定的邊際收益都達不到。
   * Valery 手上只有九位客戶、負責兩項產品，且幾乎只和北部區域的客戶打交道。 這個特點能夠說明計量的巨幅波動。
   * 如果您在矩形式樹狀結構圖中選取 [北部]  方塊，其顯示 Valery 在北部區域的毛利與整體毛利一致。
   * 選取每個其他 [依區域的總營收]  方塊會發現一個有趣現象：他們的 GM% 從 23% 到 79%。 Valery 營收數字在北部區域以外所有區域都是絕對季節性的。

3. 繼續探索為什麼 Valery 的區域業績不佳。 看看區域、其他業務單位和報表的下一頁：**產業毛利分析**。

### <a name="industry-margin-analysis"></a>產業毛利分析
這個報表頁面提供不同的資料面。 它著眼於整個產業的毛利，按區段切分。 CFO 用這個頁面比較公司暨業務單位度量與產業度量，幫助他們解釋趨勢和獲利率。 您可能會納悶為什麼 [依月份和主管區分的毛利率]  圖表放在這個頁面，因為它是小組特定的。 它在這裡有助於我們依業務單位主管篩選頁面。  

![[產業利潤分析] 報表頁面](media/sample-customer-profitability/customer6.png)

1. 獲利率如何依產業變化？ 如何依產業切分產品和客戶？ 若要回答這些問題，請從左上方選取一或多個產業 (從 CPG 產業開始)。 若要清除篩選，請選取橡皮擦圖示。

2. 在 **依產業區分的營收對預算差異 %、GM% 和今年營收** 泡泡圖中，財務長會尋找最大的泡泡，因為它們對營收的影響最大。 若要輕鬆地依產業區段查看每位經理的影響力，請依序選取區域圖中的每位經理姓名來篩選頁面。

3. 當您選取圖表中的每位經理時，請注意下列詳細資料：
   * Andrew 影響的區域遍及許多不同的產業區段，其 GM% (多為好的一面) 和差異 % 的變化也極大。
   * Annelie 的圖表很類似，除了 Annelie 只專注於聚焦於聯邦區段及短劍產品的少數幾個產業區段。
   * Carlos 目標明確，在服務區段取得豐厚的利潤。 Carlos 在高科技區段及嶄新工業區段的差異 % 也成長驚人，與預算相較，表現十分突出。
   * Tina 負責少數幾個區段且擁有最高的 GM%，但泡泡都不大，這表示 Tina 對公司營收的影響最小。
   * Valery 只負責一種產品，只處理五個產業區段。 Valery 的產業影響力有季節性，但一直都是大型的泡泡，這表示對公司營收的影響巨大。 產業區段可否說明他們不盡人意的表現？

### <a name="executive-scorecard"></a>主管計分卡
此頁面具有自訂頁面大小格式。

## <a name="dig-into-the-data-by-asking-questions-with-qa"></a>利用問與答問來提問以深入探索資料
我們的分析可能有助於判斷哪些產業讓 Valery 產生最多收益。 讓我們使用問與答。

1. 選取 [編輯報表]  以在 [編輯檢視] 中開啟報表。 只有在您擁有該報表的情況下才能使用 [編輯檢視]。 此檢視有時稱為 *建立者* 模式。 反之，此報表只與您共用，您無法在 [編輯檢視] 中開啟它。

2.  從儀表板頂端，選取 [詢問問題]  來開啟問與答問題方塊。

    ![詢問一個與資料相關的問題](media/sample-customer-profitability/power-bi-ask-question.png)

3. 在問題方塊中輸入 *Valery 依產業分類的總營收*。 請注意當您輸入問題時，視覺效果更新的方式。

    ![在問題方塊中輸入問題](media/sample-customer-profitability/power-bi-qna.png)

   如您所見，配銷產業是 Valery 最大的收益區域。

### <a name="dig-deeper-by-adding-filters"></a>加入篩選器更深入探究
讓我們看看配銷產業。  

1. 開啟 [產業毛利分析]  報表頁面。
2. 在不選取報表頁面上任何視覺效果的情況下，展開右側的篩選窗格 (如果未展開)。 [篩選]  窗格應該只會顯示 [頁面層級篩選]  。  

   ![頁面層級篩選](media/sample-customer-profitability/power-bi-filters.png)
3. 找到 [產業]  的篩選，然後選取箭號來展開清單。 讓我們新增 [配銷] 產業的頁面篩選。 首先，清除 [全選]  核取方塊，以清除所有選取項目。 然後只選取 [配銷]  。  

   ![[配銷] 的篩選條件](media/sample-customer-profitability/customer7.png)
4. [依月份和主管區分的毛利率]  圖表告訴我們，只有 Valery 和 Tina 在此產業有客戶，且 Valery 只有在 6 月到 11 月這段時間才需要處理這項產業的業務。   
5. 在 [依月份和主管區分的毛利率]  圖表圖例中，依序選取 [Tina]  和 [Valery]  。 請注意，和 Valery 相比，[依產品區分的總營收]  圖表的 Tina 部分真的很小。
6. 若要查看實際營收，請選取儀表板中的 [問與答] 方塊並輸入 *依主管及案例顯示配銷的總營收*。  

     ![在 [問與答] 方塊中輸入問題](media/sample-customer-profitability/power-bi-qna2.png)

    我們可以類似的方法瀏覽其他產業，甚至加入客戶，以在視覺效果中了解 Valery 績效的成因。

## <a name="next-steps-connect-to-your-data"></a>後續步驟：連線到您的資料
您可以在此環境盡情嘗試，因為您可以選擇不儲存您的變更。 但如果儲存了變更，您也可以隨時選取 [取得資料]  以取得此範例的新複本。

希望此教學已讓您了解 Power BI 儀表板、問與答和報表能夠如何提供範例資料的見解。 現在輪到您了，請連接到您自己的資料。 您可以透過 Power BI 連接到各式各樣的資料來源。 若要深入了解，請參閱[開始使用 Power BI 服務](../fundamentals/service-get-started.md)。
