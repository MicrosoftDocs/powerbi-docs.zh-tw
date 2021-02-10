---
title: 使用 Power BI 分析熱門股票
description: 使用 Power BI 分析熱門股票
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 02/09/2021
LocalizationGroup: Connect to services
ms.openlocfilehash: 934451c06927237fd252d60102e2e5db73e31bc1
ms.sourcegitcommit: de3b45cad5ae21c77692ce4490e21de01d21e6f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/10/2021
ms.locfileid: "100082684"
---
# <a name="analyze-popular-stocks-with-power-bi"></a>使用 Power BI 分析熱門股票

股票市場應用程式會顯示多個 Kpi，以在 Power BI 中開始分析旅程。 您可以使用它來追蹤熱門股票和 ETFs 的每週、每月或每年趨勢的結束日期。 此應用程式會顯示 Power BI 的運作方式，包括追蹤股票高和最低股價、移動平均、磁區分配、Bollinger 等量，甚至是一段時間內熱門股票的效能比較。

應用程式具備四個儀表板：
* **ETF 儀表板**：顯示四個主要索引的結束趨勢。 
* **股票和 ETFs 比較**：提供正規化的圖表，讓您輕鬆地比較股票和 EFTs。
* **庫存效能分析**：利用視覺效果來分析所選股票的趨勢、音量、OHLC 和 Bollinger 帶。
* **磁區取向分佈**：可讓您依磁區細分庫存效能。

您可以使用流覽側邊窗格或頁面右上方的向前和向後箭號，在儀表板之間流覽。

![股票應用程式的螢幕擷取畫面。](media/service-connect-to-analyze-stocks/stocks-app.png)

## <a name="etf-dashboard"></a>ETF 儀表板

ETF 儀表板具有視覺效果，可顯示四個主要索引的結束趨勢。 
* **Nasdaq**： Nasdaq 複合索引會測量 Nasdaq exchange 上超過3000個股票的變更。
* **&P 500**： s&p 500 被視為最佳的單一大型投資量測計。
* **Dow** 產品： Dow，為您展示 IT 產業領導人的市場成長，例如 Microsoft。 Dow 的收盤趨勢表示在此索引下的股票已于一天結束後關閉的趨勢。
* **Russell 2000**： Russel 2000 是適用于相互金的最常見基準測試。 您可以使用 Russell 2000 關閉趨勢視覺效果，提供超過2000個低範圍股票的投資指引。

儀表板頂端的 [執行中] 橫幅會顯示目前當天的收盤價，以及顯示在頁面上的四個索引的先前日子的價格變更。

預設 view-graph view-可協助您瞭解趨勢在一段時間內的變化幅度。 您可以使用儀表板左上角的時間調整按鈕，選擇查看一周、一個月或一年的趨勢。 將指標停留在圖表上，以取得特定日期的實際資料點。

![ETF 儀表板圖形視圖的螢幕擷取畫面。](media/service-connect-to-analyze-stocks/etf-dashboard-graph.png)  

在 X 軸上，您會看到時間週期，而在 y 軸上，您會看到結尾值。

您也可以按一下儀表板右上角的切換開關來切換至 k 線圖。 在 [k 線] 中，您可以看到每個資料點的開啟、高、低和收盤價。 將指標停留在圖表上，以取得特定日期的實際資料點。

![ETF 儀表板 k 線視圖的螢幕擷取畫面。](media/service-connect-to-analyze-stocks/etf-dashboard-candlestick.png)

## <a name="stocks-and-etfs-comparison"></a>股票和 ETFs 比較

股票和 ETFs 比較儀表板會顯示兩個正規化的圖表，讓您輕鬆地比較所選股票和 ETFs。

![股票比較儀表板選取按鈕的螢幕擷取畫面。](media/service-connect-to-analyze-stocks/stocks-comparison-dashboard.png)

若要使用此頁面，請先選取您想要比較的股票。 
1. 按一下 ![ 股票比較儀表板清除選取專案的 [選取] 按鈕螢幕擷取畫面。](media/service-connect-to-analyze-stocks/stocks-comparison-dashboard-select.png)
1. 在出現的 [ **選取股票** ] 頁面上，按一下 [ **清除** ] 以移除任何先前的選取專案，然後選取您想要比較的股票與  ![ 股票比較儀表板的螢幕擷取畫面。](media/service-connect-to-analyze-stocks/stocks-comparison-dashboard-select-clear.png)
1. 按一下 [套用]  。

選取您感興趣的股票之後，請使用下拉式箭號來選取您想要比較的特定股票。

![股票比較儀表板的螢幕擷取畫面：選取下拉式清單。](media/service-connect-to-analyze-stocks/stocks-comparison-dashboard-select-dropdown.png)

## <a name="stock-performance-analysis"></a>庫存效能分析

 股票效能分析儀表板會顯示有關所選存貨的重要 KPI，例如前一天的收盤、收盤、open、high 和 low。 選取下拉式清單，從您選取要分析的股票內選擇您想要查看的存貨。 您會看到值在您選擇的存貨之後變更。

![庫存效能分析的螢幕擷取畫面：選取。](media/service-connect-to-analyze-stocks/stocks-performance-select.png)
 
### <a name="closing-trend"></a>收盤趨勢

您可以查看所選存貨的結束趨勢，也可以選擇將其切換為 month view 或 year view，方法是按一下頁面左上角的按鈕。 擁有年份的觀點將可協助您查看股票在哪一年的哪個部分取得或遺失價值。

![已選取股票的結束趨勢螢幕擷取畫面](media/service-connect-to-analyze-stocks/stocks-performance-closing-trend.png)  

### <a name="volume"></a>磁碟區

您可以藉由向下滾動至下一個視覺效果，查看選取的存貨量。 您可以將滑鼠停留在時間間隔，以查看該年度該部分的存貨量。

![選定股票數量的螢幕擷取畫面](media/service-connect-to-analyze-stocks/stocks-performance-volume.png)
 
### <a name="ohlc-chart"></a>OHLC 圖

OHLC 圖具有極大的效用，因為它們會同時顯示指定股票的四個主要資料點。 因此，在頁面的下一個視覺效果中，您會看到 OHLC 視覺效果，其中顯示所選存貨的開啟、關閉、高和低。 您也可以藉由變更移動平均，更深入探討資料。 

![OHLC 的螢幕擷取畫面](media/service-connect-to-analyze-stocks/stocks-performance-ohlc.png)

### <a name="bollinger-band"></a>Bollinger 寬線

Bollinger 波段會使用複雜的數學來顯示趨勢。 您可以看到許多在 OHLC 中的 KPI，以及您可以看到另外三行的 KPI。 中間行顯示移動平均。 頂端線會依特定數目的標準差來向上移動，而底部的行則會依標準差向下移動。

![Bollinger 頻外的螢幕擷取畫面。](media/service-connect-to-analyze-stocks/stocks-performance-bollinger.png) 

## <a name="sectorwise-distribution"></a>Sectorwise 分佈

在 [磁區發佈] 頁面上，您會看到各種股票和其所屬市場。 如果您按一下任何磁區，則會篩選出股票，並開始顯示屬於所選磁區的股票。 

![磁區發佈的螢幕擷取畫面。](media/service-connect-to-analyze-stocks/sector-wise-distribution.png)
 
然後，您可以將滑鼠停留在股票上方以查看重要的 KPI，例如先前的關閉、關閉和差異。 差別將可協助您瞭解從昨天起的存貨已獲得或遺失的程度。

![磁區分配詳細資料的螢幕擷取畫面。](media/service-connect-to-analyze-stocks/sector-wise-distribution-detail.png)

您可以向下滾動以查看該類別中的所有股票。
 
若要查看不同部門的市場分佈，我們有「磁區型分佈」視覺效果，其顯示的磁區從上到下的最高差異在於最後一天的收盤價。

![不同磁區市場分佈的螢幕擷取畫面](media/service-connect-to-analyze-stocks/stocks-comparison-based-on-sector.png)


## <a name="next-steps"></a>下一步

* [什麼是 Power BI 範本應用程式](service-template-apps-overview.md)
* [在 Power BI 中建立範本應用程式](service-template-apps-create.md)
* [在組織中安裝並散發範本應用程式](service-template-apps-install-distribute.md)
* 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
