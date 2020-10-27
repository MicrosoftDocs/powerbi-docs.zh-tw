---
title: Power BI 中適用於商務使用者的視覺效果類型
description: Power BI 服務中的視覺效果類型
author: mihart
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 10/07/2020
ms.author: mihart
ms.custom: contperfq4
LocalizationGroup: Consumer
ms.openlocfilehash: 6d2ded8060ebe663989fd4f91fc22e4163f60c93
ms.sourcegitcommit: d2f633b4bfa271051ba1d2ef0e6e8da7dcf42818
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2020
ms.locfileid: "91830664"
---
# <a name="visual-types-in-power-bi"></a>Power BI 中的視覺效果類型

[!INCLUDE[consumer-appliesto-yynn](../includes/consumer-appliesto-yynn.md)]

視覺效果 (也稱為「圖表」 ) 是資料的圖片表示法。 一些常見範例包括直條圖、地圖、散佈圖和星形量測計。 您會在報表、儀表板及問與答中看見視覺效果。

此頁面所述的視覺效果都是以 Power BI 封裝的視覺效果。 這些是您最常遇到的視覺效果類型。 此頁面可讓您快速瀏覽這些預先封裝的視覺效果。 如需這些視覺效果的深入資訊，請參閱[關於視覺效果類型的 Power BI 報表「設計師」文件](../visuals/power-bi-visualization-types-for-reports-and-q-and-a.md)。

Power BI 未自動包含的視覺效果稱為「自訂視覺效果」。 自訂視覺效果可以從外部網站 (例如 Microsoft AppSource) 或內部來源 (例如您的組織存放區) 匯入到 Power BI。 匯入自訂視覺效果，需要具備報表的編輯權限。 若要了解這些增益集視覺效果，請參閱 [Power BI 中的自訂視覺效果](../developer/visuals/power-bi-custom-visuals.md)。



## <a name="list-of-visuals-available-in-power-bi"></a>Power BI 提供的視覺效果清單
所有這些視覺效果都能在 Power BI 儀表板及報表中找到，並[於問與答中詳述](end-user-q-and-a.md)。 若要了解如何與視覺效果互動，請參閱[在報表、儀表板和應用程式中與視覺效果互動](end-user-visualizations.md)

## <a name="a"></a>A
### <a name="area-charts-basic-layered-and-stacked"></a>區域圖：基本 (分層) 與堆疊
![區域圖](media/end-user-visual-type/basic-area-map-small.png)

基本區域圖以折線圖為基礎，會將軸與折線之間的區域填滿。 區域圖強調隨著時間的變化大小，而且可用來強調跨趨勢的總計值。 例如，代表收益隨時間變化的資料，可以在區域圖中繪製，藉此強調總收益。

## <a name="b"></a>B
### <a name="bar-and-column-charts"></a>橫條圖和直條圖
![直條圖](media/end-user-visual-type/pbi-nancy-viz-bar.png)

 ![橫條圖](media/end-user-visual-type/pbi-nancy-viz-col.png)

橫條圖是查看不同類別間特定值的標準作法。

## <a name="c"></a>C
### <a name="cards-single-number"></a>卡片：單一數字
![單一數字卡片](media/end-user-visual-type/pbi-nancy-viz-card.png)

單一數字卡片會顯示單一事實 (即單一資料點)。 有時您在 Power BI 儀表板或報告中追蹤的最重要項目是一個單一數字，例如總銷售額、歷年的市佔率，或總商機。  

### <a name="cards-multi-row"></a>卡片：多列
![多列卡片](media/end-user-visual-type/multi-row-card.png)

多列卡片會顯示一或多個資料點，每個資料列各一個。


### <a name="combo-charts"></a>組合圖
![組合圖](media/end-user-visual-type/combo-small.png)

組合圖結合了直條圖和折線圖。 將兩種圖結合成一張圖，讓您可以更快速地比較資料。 組合圖可以有一或兩個 Y 軸，因此請務必仔細查看。 

組合圖極適合：
- 當您的折線圖和直條圖具有相同的 X 軸。
- 當您要比較具有不同值範圍的多個量值
- 當您要在一個視覺效果中說明兩個量值間的相互關聯
- 當您要檢查量值是否符合另一個量值所定義的目標
- 當您要節省畫布的空間

## <a name="d"></a>D    
### <a name="decomposition-tree"></a>分解樹狀結構
![分解樹狀結構](media/end-user-visual-type/power-bi-decomposition.png)

分解樹狀結構視覺效果可讓您將多個維度上的資料視覺化。 它會自動彙總資料，並且能夠以任何順序向下切入到您的維度。 這也是一種人工智慧 (AI) 視覺效果，因此，您可以要求它根據特定準則來尋找下一個要向下切入到其中的維度。 這讓它成為特定探索和進行根本原因分析的重要工具。

### <a name="doughnut-charts"></a>環圈圖
![環圈圖](media/end-user-visual-type/donut-small.png)

環圈圖類似於圓形圖。  它們會顯示部分與整體的關聯性。 唯一的差別在於，中央為空白，且保留空間給標籤或圖示。

## <a name="f"></a>F
### <a name="funnel-charts"></a>漏斗圖
![漏斗圖](media/end-user-visual-type/pbi-nancy-viz-funnel.png)

漏斗圖利於以視覺化方式展現具有階段的程序，而項目會依序從某個階段流向下一個階段。  其中一個範例是銷售程序，其開頭為潛在客戶而結尾為採購履約。

例如，會分階段追蹤客戶的銷售漏斗圖：潛在客戶 (Lead) > 合格的潛在客戶 (Lead) > 潛在客戶 (Prospect) > 合約 > 關閉。 漏斗圖的圖形一看就能表達出您追蹤中程序的健全狀況。
漏斗圖的每個階段代表總數中所佔的百分比。 因此，在大部分情況下，漏斗圖形狀像漏斗 -- 第一階段最大，然後每個後續階段比前一階段小。 梨狀的漏斗圖也很實用，能識別出程序中的問題。 但通常第一階段，也就是「引入」階段佔最大部分。

## <a name="g"></a>G
### <a name="gauge-charts"></a>量表圖
![量表圖](media/end-user-visual-type/gauge-m.png)

星形量測計圖表具有圓弧線段，並且會顯示針對某一目標/KPI 測量進度的單一值。 目標或目標值是由線條 (指針) 表示。 達到該目標的進度是由陰影表示。 代表該進度的值會以粗體顯示在弧線內。所有可能的值會從最小 (最左邊的值) 到最大 (最右邊的值) 平均分散在弧線上。

在上述範例中，我們是汽車零售商，正在追蹤銷售小組每個月的平均銷售量。 我們的目標是 140，以黑色指針代表。 最小的可能平均銷售量是 0，而我們將最大值設為 200。 藍色陰影顯示我們這個月的銷售量目前平均約為 120。 幸好我們還有一週的時間來達成目標。

星形量測計極適合用來：
- 顯示目標的達成進度
- 代表 KPI 等百分位數量值
- 顯示單一量值的健全狀況
- 顯示可快速掃描和了解的資訊

## <a name="k"></a>K
 ### <a name="key-influencers-chart"></a>關鍵影響因素圖表
![關鍵影響因素](media/end-user-visual-type/power-bi-influencer.png)

關鍵影響因素圖表顯示出所選結果或值的主要成因。

關鍵影響因素是協助您了解影響關鍵計量之因素的最佳選擇。 例如，什麼原因讓客戶簽下第二張訂單 **，或者為什麼去年六月的銷售額如此亮眼** 。 

### <a name="kpis"></a>KPI
![KPI](media/end-user-visual-type/power-bi-kpi.png)

關鍵效能指標 (KPI) 是一種視覺提示，指出對於可測量目標已達成的進度。 

KPI 極適合：
- 測量進度 (超前或落後了那些項目？)
- 測量離目標的距離 (超前或落後了多少？)

## <a name="l"></a>L
### <a name="line-charts"></a>折線圖
![折線圖](media/end-user-visual-type/pbi-nancy-viz-line.png)

折線圖強調完整連續值的整體圖形，通常是一段期間。

## <a name="m"></a>M
### <a name="maps-basic-maps"></a>地圖：基本地圖
![基本地圖](media/end-user-visual-type/pbi-nancy-viz-map.png)

使用基本地圖建立類別和數量資訊與空間位置的關聯。

### <a name="maps-arcgis-maps"></a>地圖：ArcGIS 地圖
![ArcGis 地圖](media/end-user-visual-type/power-bi-esri-map-theme2.png)

ArcGIS 地圖與 Power BI 的結合，把在點之外加上地圖的做法帶到了全新境界。 您可以使用基礎地圖、位置類型、佈景主題、符號樣式及參考圖層等選項，建立具有豐富資訊的絶佳地圖視覺效果。 地圖上的官方資料圖層 (例如人口普查資料) 與空間分析結合之後，能讓人更深入了解視覺效果中的資料。

### <a name="maps-filled-maps-choropleth"></a>地圖：區域分布圖 (分級著色圖)
![區域分布圖](media/end-user-visual-type/pbi-nancy-viz-filledmap.png)

區域分布圖使用陰影、濃淡或圖樣，顯示值的比例如何隨著地理位置或地區而有所不同。 可使用範圍介於淺色 (較不常見/較低) 到深色 (較常見/較多) 的陰影，快速顯示這些相對差異。

### <a name="maps-shape-maps"></a>地圖：圖形地圖
![圖形地圖](media/end-user-visual-type/power-bi-shape-map2.png)

圖形地圖會使用色彩來比較地圖上的區域。 圖形地圖無法在地圖上顯示資料點的確切地理位置。 相反地，其主要目的是要藉由不同的著色，在地圖上顯示區域的相對比較。

### <a name="matrix"></a>Matrix
![螢幕擷取畫面顯示 [收益] 和 [YTD 收益] 的年度和季度資料矩陣圖。](media/end-user-visual-type/matrix.png)

矩陣圖視覺效果是一種資料表視覺效果 (請參閱下方的＜資料表＞)，可支援分層式配置。 通常，報表設計師會在報表和儀表板中包含矩陣，讓使用者能夠選取矩陣中一或多個項目 (資料列、資料行、資料格)，以交叉醒目提示報表頁面的其他視覺效果。  

## <a name="p"></a>P
### <a name="pie-charts"></a>圓形圖
![圓形圖](media/end-user-visual-type/pbi-nancy-viz-pie.png)

圓形圖會顯示部分與整體的關聯性。 

### <a name="power-apps-visual"></a>Power Apps 視覺效果
![Power Apps 視覺效果](media/end-user-visual-type/power-bi-powerapps-visual.png)

報表設計師可以建立 Power App，並將其內嵌到 Power BI 報表中。 「商務使用者」可以在 Power BI 報表內與該視覺效果互動。 

## <a name="q"></a>Q
### <a name="qa-visual"></a>問與答視覺效果
![問與答視覺效果](media/end-user-visual-type/power-bi-q-and-a.png)

>[!TIP]
>問與答視覺效果類似於[儀表板上的問與答體驗](../create-reports/power-bi-tutorial-q-and-a.md)，可讓您使用自然語言來詢問資料的相關問題。 

如需詳細資訊，請參閱 [Power BI 中的問與答視覺效果](../visuals/power-bi-visualization-types-for-reports-and-q-and-a.md)。

## <a name="r"></a>R
### <a name="ribbon-chart"></a>功能區圖表
![功能區圖表](media/end-user-visual-type/power-bi-ribbon.png)

功能區圖表會顯示哪些資料類別具有最高的等級 (最大值)。 功能區圖表適合顯示等級變更，最高等級 (值) 一律顯示於每個時段的最上方。

## <a name="s"></a>S
### <a name="scatter-bubble-and-dot-plot-charts"></a>散佈圖、泡泡圖與點圖

散佈圖一律會有兩個值座標軸，沿著水平軸顯示一組數字資料，沿著垂直軸顯示另一組數值。 此圖表顯示 x 與 y 數交集處的點，結合這些值可形成單一的資料點。 視資料之不同，這些資料點可能平均散布或不平均地散佈在水平軸。

![泡泡圖](media/end-user-visual-type/pbi-nancy-viz-bubble.png)

泡泡圖會將資料點以泡泡取代，而泡泡的大小代表其他維度的資料。



點圖類似於泡泡圖和散佈圖，不同之處在於其可沿 X 軸繪製數值或類別資料。 此範例使用的是正方形而非圓形，並沿著 X 軸繪製銷售額。

![點圖](media/end-user-visual-type/power-bi-dot-plot-squares.png)

### <a name="scatter-high-density"></a>散佈圖高密度
![高密度散佈圖](media/end-user-visual-type/density-scatter.png)

根據定義，高密度資料是取樣來在合理範圍內快速建立視覺效果以回應互動。 高密度取樣會使用消除重疊點的演算法，並確保視覺效果會呈現資料集中的所有點。 它不只會繪製代表性的資料樣本。  

還可確保提供回應、轉譯和清楚保留整體資料集中重要點的最佳組合。

### <a name="slicers"></a>交叉分析篩選器
![slicer](media/end-user-visual-type/pbi-slicer.png)

交叉分析篩選器是一種獨立圖表，可用來篩選頁面上的其他視覺效果。 交叉分析篩選器有許多不同的格式 (類別、範圍、日期等)，可將其格式化以允許只選取一個、選取多個或所有可用的值。 

交叉分析篩選器極適合：
- 在報表畫布上顯示常用或重要篩選，以方便存取
- 不需要開啟下拉式清單，即可輕鬆查看目前篩選的狀態
- 依資料行篩選不必要的資料，並隱藏在資料表中
- 將交叉分析篩選器放在重要的視覺效果旁邊，以建立更多重點報表


### <a name="smart-narrative"></a>智慧型敘事
![智慧型敘事](media/end-user-visual-type/power-bi-smart-narrative.png)

智慧型敘事會將文字新增至報表，以指出趨勢、關鍵的重點，以及新增說明與內容。 此文字可協助使用者了解資料，並快速識別重要的發現。

### <a name="standalone-images"></a>獨立映像
![獨立影像](media/end-user-visual-type/pbi-nancy-viz-image.png)

獨立影像是已新增至報表或儀表板的圖形。 

## <a name="t"></a>T
### <a name="tables"></a>資料表
![資料表](media/end-user-visual-type/table-type.png)

資料表是一個方格，其中以資料列和資料行的邏輯數列包含相關的資料。 它也可能包含標頭和總計資料列。 資料表適合處理您要在許多值裡尋找單一類別的量化比較。 例如，這個資料表會顯示類別的五個不同量值。

資料表極適合：
- 查看並比較詳細資料和實際值 (而非視覺表示法)
- 以表格格式顯示資料
- 依類別顯示數值資料

### <a name="tree-maps"></a>樹狀圖
![樹狀圖](media/end-user-visual-type/pbi-nancy-viz-tree.png)

樹狀圖是彩色矩形圖，值會以矩形大小表示。  它們可以是階層式，各矩形可以巢嵌在主要矩形內。 每個矩形內的空間配置是根據測量中的值。 矩形會依大小從左上角 (最大) 排列到右下角 (最小)。

樹狀圖極適合：
- 顯示大量的階層式資料
- 橫條圖無法有效處理大量值的時候
- 顯示各部分與整體之間的比例
- 顯示量值在階層中每個類別層級的分佈模式
- 使用大小和色彩編碼顯示屬性
- 找出模式、極端值、最重要的參與者和例外狀況

## <a name="w"></a>W
### <a name="waterfall-charts"></a>瀑布圖
![瀑布圖](media/end-user-visual-type/waterfall-small.png)

瀑布圖會顯示總額的增減變動。 它適用於了解起始值 (例如淨收益) 如何受到一系列正面和負面變更的影響。

資料行會標示色彩，讓您快速地分辨增加和減少。 起始值和最終值資料行通常在水平軸上開始，而中間值則是浮動的資料行。 由於其「外觀」，瀑布圖也稱為橋樑圖 (bridge chart)。

瀑布圖極適合：
- 您擁有跨越時間或不同類別目錄的量值變更時
- 稽核對總值造成的重大變更
- 藉由顯示營收的各種來源來標示貴公司的年度收益，並達到總收益 (或虧損)
- 呈現貴公司一年的開始和結束人數
- 以視覺化方式顯示您的每月收入與支出，以及帳戶的日常餘額

## <a name="tell-qa-which-visual-to-use"></a><a name="qna"></a>告訴問與答要使用的視覺效果
使用 Power BI 問與答輸入自然語言查詢時，您可以在查詢中指定視覺效果類型。  例如：


「以樹狀圖依州顯示銷售量」

![問與答工作階段](media/end-user-visual-type/qa-treemap.png)

## <a name="next-steps"></a>後續步驟
[在報表、儀表板和應用程式中與視覺效果互動](end-user-visualizations.md)    
[來自 sqlbi.com 的正確視覺效果參考](https://www.sqlbi.com/wp-content/uploads/videotrainings/dashboarddesign/visuals-reference-may2017-A3.pdf)

