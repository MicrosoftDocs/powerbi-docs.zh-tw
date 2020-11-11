---
title: 大型資料集、資料點限制及資料策略
description: 適用於視覺效果和資料縮減策略的資料限制
author: msftrien
ms.reviewer: justyna
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 01/10/2020
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: 89bfba0dc679ddb7a9142c83e863cddaf1400063
ms.sourcegitcommit: 5ccab484cf3532ae3a16acd5fc954b7947bd543a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2020
ms.locfileid: "93412042"
---
# <a name="apply-data-point-limits-and-strategies-by-visual-type"></a>依視覺效果類型套用資料點限制與策略

[!INCLUDE[consumer-appliesto-yyyn](../includes/consumer-appliesto-yyyn.md)]    

在 Power BI 中呈現視覺效果時，視覺化作業必須既快速又精確。 這需要針對每個視覺效果類型設定底層的演算法。 Power BI 中的視覺效果必須有足夠的彈性來處理不同大小的資料集。 有些資料集只有少數幾個資料點，而其他資料集則會有數 PB 的資料點。 本文說明 Power BI 用來呈現視覺效果的策略。

## <a name="data-reduction-strategies"></a>資料縮減策略
每個視覺效果皆採用一或多個「資料縮減策略」  ，以處理所要分析且體積可能相當龐大的資料。 就算是簡單的資料表也會採用策略，以避免將整個資料集載入至用戶端。  所要使用的縮減策略會因視覺效果類型而異。 每個視覺效果都會在產生要傳送給伺服器之資料要求的過程中，從支援的「資料縮減策略」  中選取策略。 

每個視覺效果皆會控制那些策略上的參數，以影響整體的資料數量。   

## <a name="strategies"></a>策略
每個策略都有以所要視覺化之資料的形狀和類型為依據的預設值。 但您可以在 Power BI 的 [格式化] 窗格中覆寫這些預設值，以提供正確的使用者體驗。 

* **資料視窗化** (分割)：能以漸進方式載入整體資料集的片段，讓使用者以捲動方式瀏覽視覺效果中的資料。
* **前 N 項** ：只顯示前 N 個項目
* **簡單範例** ：顯示第一個、最後一個，以及它們之間 N 個平均分佈的項目。
* **後 N 項** ：只顯示最後 N 個項目。  適用於監視經常更新的資料。
* **高密度取樣** ：一種更顧及極端值和/或曲線形狀的改良式取樣演算法。
    * **量化線路取樣** ：根據某個軸上各個量化中的極端值進行資料點取樣
    * **重疊點取樣** ：根據重疊值進行資料點取樣以保留極端值

## <a name="statistics"></a>統計
某些模型可以提供有關某些資料行之值數目的統計資料。 當有這類資訊存在時，如果視覺效果並未明確覆寫策略的值計數，我們就會運用該資訊在多個階層之間提供更好的平衡。

如需詳細資訊，請參閱 [Analysis Services 的新功能](/sql/analysis-services/what-s-new-in-analysis-services) \(機器翻譯\)

## <a name="dynamic-limits"></a>動態限制
除了上述策略之外，具有兩個群組資料行階層 (軸和圖例，或類別和數列) 的視覺效果還會使用一個額外的策略，稱為「動態限制」  。  動態限制的設計目的是要提供更好的資料點平衡。 

與靜態限制相比，動態限制能為稀疏資料提供更好的點選擇。 例如，您可以將視覺效果設定成選取 100 個類別和 10 個數列，總計 1000 個點。 但實際資料具有 50 個類別和 20 個數列。  在查詢執行階段，動態限制會選取所有 20 個數列，以填滿所要求的 1000 個點。

伺服器會在符合下面所述的情況下自動套用動態限制：

* 在具有內部部署 SSAS 2016 版或更新版本，並[運用伺服器的 SuperDax 功能](/archive/blogs/analysisservices/whats-new-in-microsoft-sql-server-analysis-services-tabular-models-in-sql-server-2016-ctp-2-3) \(英文\) 的 Power BI Desktop 中

* 在使用匯入的模型、Direct Query、即時連線至服務，或即時連線至 AS PaaS 的 Desktop 或 Power BI 服務中。 

* 在透過內部部署閘道連線至內部部署 SSAS 的 Power BI 服務中，我們無法使用動態限制。 內部部署閘道並不完全支援會從內部部署 SSAS 傳回不同結果集結構的動態限制策略。  

## <a name="strategies-and-data-point-limits-by-visual-type"></a>依視覺效果類型區分的策略和資料點限制

### <a name="area-chart"></a>區域圖
請參閱[線路取樣的運作方式](../create-reports/desktop-high-density-sampling.md#how-the-new-line-sampling-algorithm-works)

### <a name="barcolumn-chart"></a>橫條圖/直條圖
- 在類別目錄模式下時
    - 類別：使用一次顯示 500 個資料列的視窗進行虛擬化
    - 數列：前 60 個
    - 在純量模式下 (可以使用動態限制)
        - 點數上限：10,000
        - 類別：500 個值的樣本
        - 數列：前 20 個值

### <a name="card-multirow"></a>卡片 (多列) 
- 值：使用一次顯示 200 個資料列的視窗進行虛擬化

### <a name="combo-chart"></a>組合圖
 使用與直條圖相同的策略。 請注意， **組合圖** 中的線路並不會使用 **折線圖** 所使用的高密度演算法。

### <a name="power-bi-visuals"></a>Power BI 視覺效果
最多 30,000 個，但需由視覺效果作者指示要使用的策略。 預設限制為 1000，但視覺效果建立者可加以變更，其上限為 30000。

### <a name="doughnut"></a>環圈圖
- 點數上限：3,500
- 群組：前 500 個
- 詳細資料:前 20 個

### <a name="filled-map-choropleth"></a>區域分布圖 (分級著色圖) 
區域分布圖可以使用統計資料或動態限制。 Power BI 會嘗試依下列順序使用縮減：動態限制、統計資料、設定。 
- 點數上限：10000
- 類別：前 500 個
- 數列 (當 X 與 Y 都存在時)：前 20 個

### <a name="funnel"></a>漏斗圖
- 點數上限：3,500
- 類別：前 3,500 個

### <a name="kpi"></a>KPI
- 趨勢軸
- 最後 3,500 個

### <a name="line-chart"></a>折線圖
請參閱[線路取樣的運作方式](../create-reports/desktop-high-density-sampling.md#how-the-new-line-sampling-algorithm-works)

### <a name="line-chart-high-density"></a>折線圖 (高密度)
請參閱[高密度取樣](../create-reports/desktop-high-density-sampling.md)

### <a name="map"></a>地圖 
- 點數上限：3,500

視設定而定，地圖可以有：
- 位置：前 3,500 個
- 位置、大小：前 3,500 個
- 位置、緯度、經度的彙總 (+/-大小)：前 3,500 個
- 緯度、經度：請參閱[高密度散佈圖](../create-reports/desktop-high-density-scatter-charts.md)
- 緯度、經度、大小：前 3,500 個
- 圖例、緯度、經度：請參閱[高密度散佈圖](../create-reports/desktop-high-density-scatter-charts.md)
- 圖例、緯度、經度、大小：前 233 個圖例、前 15 個緯度和經度 (可使用統計資料或動態限制)
- 位置、圖例、緯度、經度的彙總 (+/-大小)：前 233 個位置、前 15 個圖例 (可使用統計資料或動態限制)

### <a name="matrix"></a>Matrix
- 資料列：使用一次顯示 500 個資料列的視窗進行虛擬化
- 資料行：前 100 個群組資料行 
- 值：有多個值不會計入資料縮減

### <a name="powerapps-visual"></a>PowerApps 視覺效果
最多 30,000 個，但需由視覺效果作者指示要使用的策略。 預設限制為 1000，但視覺效果建立者可加以變更，其上限為 30000。

### <a name="radial-gauge"></a>星形量測計
無縮減策略

### <a name="slicer"></a>交叉分析篩選器
- 值：使用一次顯示 200 個資料列的視窗進行虛擬化

### <a name="scatter-chart-high-density"></a>散佈圖 (高密度)
請參閱[高密度散佈圖](./desktop-high-density-scatter-charts.md)

### <a name="pie"></a>圓形圖
- 點數上限：3,500
- 群組：前 500 個
- 詳細資料:前 20 個

### <a name="r--python-visuals"></a>R 和 Python 視覺效果
限制為 150,000 個資料列。 如果選取超過 150,000 個資料列，則只會使用前 150,000 個資料列

### <a name="ribbon-chart"></a>功能區圖表
- 在類別目錄模式下時
    - 類別：使用一次顯示 500 個資料列的視窗進行虛擬化 (資料視窗化)
    - 數列：前 60 個
    - 在純量模式下 (可以使用動態限制)
        - 點數上限：10,000
        - 類別：500 個值的樣本
        - 數列：前 20 個值

### <a name="shape-map-preview"></a>圖形圖 (預覽)
圖形圖可以使用統計資料或動態限制。 
- 點數上限：1,500
- 類別：前 500 個

### <a name="table"></a>資料表
- 值：使用一次顯示 500 個資料列的視窗進行虛擬化 (資料視窗化)

### <a name="tree-map-could-use-statistics-or-dynamic-limits"></a>樹狀圖 (可使用統計資料或動態限制)
- 點數上限：3,500
- 群組：前 500 個
- 詳細資料:前 20 個

### <a name="waterfall-chart"></a>瀑布圖
- 當只有類別值區時
    - 點數上限：3,500
    - 僅限類別 - 前 3,500 個
- 當類別和明細都存在時
    - 類別：使用一次顯示 30 個資料列的視窗進行虛擬化 (資料視窗化)
    - 明細 - 前 200 個值


## <a name="next-steps"></a>後續步驟
[視覺效果類型](power-bi-report-visualizations.md)
