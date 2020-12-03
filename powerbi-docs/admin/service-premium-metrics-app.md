---
title: Power BI Premium 計量應用程式
description: 了解如何使用 Power BI Premium 計量應用程式管理您的 Premium 容量並進行疑難排解。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: how-to
ms.date: 11/11/2020
LocalizationGroup: Premium
ms.openlocfilehash: 6b214aacaeff0cc939af60b97d0c4781e1e4d36b
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96413625"
---
# <a name="power-bi-premium-metrics-app"></a>Power BI Premium 計量應用程式

您可以使用 **Power BI Premium 計量應用程式** 來管理 Power BI Premium 訂用帳戶的健康情況與容量。 使用應用程式時，系統管理員可以使用程式的 [容量健康情況中心]  查看監視其 Premium 容量健康情況的指標，並與其互動。 計量應用程式包含稱為 [容量健康情況中心]  的登陸頁面，以及與三個重要計量有關的詳細資料：

* 作用中記憶體
* 查詢等候
* 重新整理等候

![Power BI Premium 計量應用程式](media/service-premium-metrics-app/premium-metrics-app-00.png)

下列各節將詳細說明登陸頁面與三個計量報表頁面。 

> [!IMPORTANT]
> 如果 Power BI Premium 容量遇到高資源使用量，因而發生效能或可靠性問題，您可收到通知電子郵件以找出問題並加以解決。 這是對超載容量進行疑難排解的簡單方式。 如需詳細資訊，請參閱[容量和可靠性通知](service-interruption-notifications.md#capacity-and-reliability-notifications)。

> [!NOTE]
> Power BI Premium 最近已發行名叫 **Premium Gen2** 的新版本 Premium，其目前處於預覽狀態。 Premium Gen2 將能簡化 Premium 容量的管理，並減少管理負擔。 特別是，其能大幅減少系統管理員必須監視以確保效能及使用者體驗的計量 (僅限 CPU)。 如需詳細資訊，請參閱 [Power BI Premium 第 2 代 (預覽)](service-premium-what-is.md#power-bi-premium-generation-2-preview)。


## <a name="premium-capacity-health-center"></a>Premium 容量健康情況中心

當您開啟 **Power BI Premium 計量應用程式** 時，您會看到 [容量健康情況中心]  ，其中提供 Power BI Premium 容量的健康情況概觀。

![Premium 計量應用程式中的容量健康情況中心](media/service-premium-metrics-app/premium-metrics-app-01.png)

如果您的組織有多個 Premium 訂用帳戶，您就可以從登陸頁面中選取想要查看的 Power BI Premium 容量。 若要查看 Premium 容量，請選取名為 [選取容量以查看其計量]  之頁面頂端附近的下拉式清單。

這三個 KPI 會根據對它們套用的設定，顯示所選 Premium 容量的目前健康情況。 

若要查看每個 KPI 的特定資料，請選取位於每個 KPI 視覺效果底部的 [瀏覽]  按鈕，並顯示其詳細資料頁面。 下列各節說明每個 KPI 與其頁面提供的詳細資料。

## <a name="the-active-memory-metric"></a>作用中記憶體計量

**使用中記憶體** 計量是「容量規劃」  類別的一部分，這是一個良好的健全狀況指示器，可評估使用量的容量資源耗用量，因此可視需要調整容量以規劃容量規模。 

![作用中記憶體 KPI](media/service-premium-metrics-app/premium-metrics-app-02.png)

**作用中記憶體** 是用來處理目前作用中資料集的記憶體，因此在需要記憶體時不會將其收回。 作用中記憶體計量會指出您的容量是否足以處理額外的負載，或目前是否已接近或已超過容量的負載能力。 目前正耗用的作用中記憶體代表可支援額外重新整理與查詢作業的記憶體容量會較小。 

**作用中記憶體** KPI 可測量容量其作用中記憶體超過 70% 閾值 50 次的次數 (標記設定為過去七天的 30%)，這可以指出容量是否正接近可能會讓使用者開始感受到查詢效能出現問題的時間點。

此節中顯示的量測計視覺效果會顯示自上次重新整理報表時算起的過去七天內，容量已超過 70% 閾值 4 次，並依每小時的貯體區隔。 量測計的最大值 168，代表過去七天小時數 (以小時為單位)。

若要了解使用中記憶體 KPI 的詳細資料，請按一下 [瀏覽]  按鈕，以查看提供其詳細計量之特定視覺效果的報表頁面，以及顯示在頁面右欄的疑難排解指南。 

這裡提供兩個案例說明，只要在報表頁面上選取 [案例 1]  或 [案例 2]  ，即可顯示說明。 

![顯示使用中記憶體詳細資料頁面的螢幕擷取畫面。](media/service-premium-metrics-app/premium-metrics-app-03.png)

與每個案例相關聯的疑難排解指南會提供計量所代表意義的詳細說明，因此您可以進一步了解容量的狀態，以及可以執行哪些動作來緩解任何問題。 

下列各節會說明上述兩個案例。

### <a name="scenario-one---current-load-is-too-high"></a>案例 1 - 目前的負載太高 

若要判斷容量是否有足夠的記憶體可完成工作負載，請參閱頁面上的第一個視覺效果：**A：耗用記憶體百分比**，會顯示目前處理中的資料集正在耗用，因此無法收回的記憶體。

警示閾值是一條紅色虛線，會標示耗用 90% 記憶體容量的事件。

警告閾值是一條黃色虛線，會標示耗用 70% 記憶體容量的事件。 

黑色虛線為記憶體使用量趨勢線，可指示依整個圖形時間軸期間目前容量的記憶體使用量所估計的記憶體使用量趨勢。

高於警示閾值 (紅色虛線) 與記憶體趨勢線 (黑色虛線) 若出現次數多，表示系統有記憶體容量壓力，可能會導致在這段時間內無法將額外的資料集載入至記憶體。 

當您看到這類情況時，應仔細查看頁面上的其他圖表，以更正確地判斷為何會耗用這麼多記憶體，以及如何進行負載平衡或最佳化，或視需要相應增加容量。 

頁面上的第二個視覺效果，**B：每小時載入的作用中資料集**，會顯示記憶體中載入的最高資料集數目 (以每小時的貯體數計算)。 

第三個視覺效果，**C：資料集在記憶體中的原因**，是一個資料表，其中會依工作區名稱、資料集名稱、記憶體中資料集未壓縮大小來列出資料集，並說明將其載入至記憶體的原因 (例如，因為重新整理或查詢，或兩者)。

#### <a name="diagnosing-scenario-one"></a>診斷案例 1

一致的高作用中記憶體使用量可能會導致強制回收目前使用中的資料集，或無法載入新的資料集。 下列步驟可協助您診斷問題

1. 查看圖表 *A：耗用記憶體百分比*

    **a.** 如果圖表 A 顯示超過警示閾值 (90%) 多次且/或連續數個小時，表示您的容量發生記憶體不足情況的頻率太高。 我們可以在下面的圖表中看到警告閾值 (70%) 已超過四次。

    ![圖表 a，耗用記憶體百分比](media/service-premium-metrics-app/premium-metrics-app-04.png)

    **b.** 標題為 *B：每小時載入的作用中資料集*，會依每小時貯體數顯示記憶體中載入的最高唯一資料集數目。 選取視覺效果中的橫條，可交叉篩選資料集出現在記憶體視覺效果中的原因。  

    ![圖表 b，每小時耗用的記憶體](media/service-premium-metrics-app/premium-metrics-app-05.png)     

    **c.** 請參閱 **為何資料集在記憶體中** 資料表，以查看記憶體中已載入資料集的清單。 依據「資料集大小 (MB)」  排序，以反白顯示佔用最多記憶體的資料集。 容量作業可分類為「互動式」  或「背景」  。 互動式作業包括轉譯要求及回應使用者互動 (篩選、問與答查詢等)。 查詢數總計和重新整理數總計可讓您了解資料集上是否有執行完成的重度互動 (查詢) 或背景 (重新整理) 作業。 請務必了解互動式作業一律會優先於背景作業，以盡可能確保最佳使用者體驗。 如果資源不足，會將背景作業排入佇列，等到有資源可用時再處理。 Power BI 服務可以在程序中停止背景作業 (例如資料集重新整理與 AI 函式)，並將其排入佇列。
    
    ![資料表 c，資料集清單](media/service-premium-metrics-app/premium-metrics-app-06.png)  

#### <a name="remedies-for-scenario-one"></a>案例 1 的因應措施

您可以採取下列步驟來補救與案例 1 相關的問題：

1. **相應增加容量** - 將容量相應增加至下一個 SKU，將可提供高達目前 SKU 兩倍的記憶體，因而降低容量目前遇到的任何記憶體壓力。

2. **將資料集移至其他容量** - 如果您有另一個記憶體更大的容量可用，可以將包含較大型資料集的工作區移至該容量。


### <a name="scenario-two---future-load-will-exceed-limits"></a>案例 2 - 未來的負載將會超過限制

若要判斷是否有足夠的記憶體可供容量完成工作負載，可以參考位於頁面頂端的 **A：耗用記憶體百分比** 視覺效果，它代表目前處理中的資料集所耗用而無法收回的記憶體。 黑色虛線會反白顯示趨勢。 在有記憶體壓力的容量中，相同的視覺效果會清楚地顯示記憶體趨勢線 (黑色虛線)，這表示可能會導致其他資料集無法在該時間點載入到記憶體中。 趨勢線 (黑色虛線) 會根據七天的資料顯示成長趨勢。 

![顯示案例二使用中記憶體詳細資料頁面的螢幕擷取畫面。](media/service-premium-metrics-app/premium-metrics-app-07.png)

#### <a name="diagnosing-scenario-two"></a>診斷案例 2

若要診斷案例 2，請判斷趨勢線是否會針對警告或警示閾值顯示向上趨勢。 

1. 請考量 **圖表 A：**

    ![已耗用記憶體圖表](media/service-premium-metrics-app/premium-metrics-app-08.png)

    **a.** 如果圖表顯示向上傾斜，表示記憶體耗用量在過去七天內已增加。

    **b.** 目前成長狀況假設，並預測趨勢線何時會跨越警告臨界值 (黃色虛線)。

    **c.** 請至少每隔兩天檢查一次趨勢線，以了解趨勢是否持續不變。

#### <a name="remedies-for-scenario-two"></a>案例 2 的因應措施

您可以採取下列步驟來因應與案例 2 相關的問題：

1. **相應增加容量** - 將容量相應增加至下一個 SKU，將可提供高達目前 SKU 兩倍的記憶體，因而降低容量目前遇到的任何記憶體壓力。

2. **將資料集移至其他容量** - 如果您有另一個記憶體更大的容量可用，可以將包含較大型資料集的工作區移至該容量。


## <a name="the-query-waits-metric"></a>查詢等候計量

[查詢]  類別會指出使用者是否可能看到回應速度緩慢，或可能會變成沒有回應的報表視覺效果。 **查詢等候** 是查詢作業從觸發到開始執行之間所需的時間。 此 KPI 會測量佔所選容量 25% 或更多的查詢是否等候 100 毫秒或更長時間才會執行。 當沒有足夠的可用 CPU 來執行所有擱置中的查詢時，就會發生查詢等候情況。 

![查詢等候量測計](media/service-premium-metrics-app/premium-metrics-app-09.png)

此視覺效果中的量測計顯示了自上次重新整理報表算起的過去七天內，17.32% 的查詢會等候 100 毫秒以上的時間。 

若要了解查詢等候 KPI 的詳細資料，請按一下 [瀏覽]  按鈕，以顯示相關計量視覺效果的報表頁面，並在頁面右欄中提供疑難排解指南。 疑難排解指南有兩個案例，每個都會提供計量的詳細說明、容量的狀態，以及您可以採取哪些措施來減輕問題。

我們將在下列各節中依序討論每個查詢等候案例。

### <a name="scenario-one---long-running-queries-consume-cpu"></a>案例 1 - 長時間執行查詢耗用 CPU

在案例 1 中，長時間執行的查詢佔用了太多 CPU。 

您可以調查是否有報表效能不佳是因為多載的容量或設計不良的資料集或報表所造成。 有數個原因會導致長時間執行查詢，而長時間執行的定義為花費超過 10 秒來完成執行。 資料集大小和複雜度及查詢複雜度，只是幾個可能造成長時間執行查詢的範例。 

在報表頁面上，會出現下列視覺效果： 

* 最上方標題為 **A：較長等候時間** 的資料表會列出含有等候查詢的資料集。 
* **B：每小時較長等候時間分佈** 會顯示等候時間較長的分佈。 
* 標題為 **C：每小時長時間執行查詢計數** 的圖表，會顯示依每小時的貯體分割執行的長時間執行查詢計數。
* 最後一個視覺效果，資料表 **D：長時間執行的查詢**，會列出長時間執行的查詢和其統計資料。

![查詢等候詳細資料頁面](media/service-premium-metrics-app/premium-metrics-app-10.png)

您可以採取一些步驟來診斷及因應查詢等候時間的問題，如下所述。

#### <a name="diagnosing-scenario-one"></a>診斷案例 1

首先，您可以判斷當您的查詢正在等候時，是否發生長時間執行查詢的情況。 

![較長等候時間資料表](media/service-premium-metrics-app/premium-metrics-app-11.png)

查看 **圖 B** 的圖表中會顯示等候超過 100 毫秒的查詢計數。 選取其中一個顯示大量等候項目的資料行。

![較長等候時間分佈](media/service-premium-metrics-app/premium-metrics-app-12.png)

當您按一下較長等候時間的資料行時，**圖表 C** 會進行篩選，以顯示在這段時間內長時間執行查詢的計數，如下圖所示：

![每小時長時間查詢計數](media/service-premium-metrics-app/premium-metrics-app-13.png)

此外，也會篩選 **圖表 D**，以顯示在選取的時段內長時間執行的查詢。

![長時間執行的查詢](media/service-premium-metrics-app/premium-metrics-app-14.png)

#### <a name="remedies-for-scenario-one"></a>案例 1 的因應措施

以下是您可以採取的步驟，以解決案例 1 中的問題：

1. **執行 PerfAnalyzer 以最佳化報表和資料集** - 報表的效能分析器會在頁面上顯示每次互動的效果，包括每個視覺效果重新整理時使用的時間，以及時間用在處理哪些作業。

2. **相應增加容量** - 將容量相應增加至下一個 SKU，將可提供高達目前 SKU 兩倍的 CPU，因而降低可能造成查詢執行時間變長的任何 CPU 壓力。

3. **將資料集移至其他容量** - 如果您有另一個有更多 CPU 可用的容量，可以將包含資料集 (內含等候的查詢) 的工作區移至其他容量。

### <a name="scenario-two---too-many-queries"></a>案例 2 - 太多查詢

在案例 2 中，有太多查詢正在執行。

當要執行的查詢數目超過容量限制時，查詢會排入佇列，直到有資源可以執行為止。 如果佇列大小變得太大，該佇列中的查詢最後會等待超過 100 毫秒。

![案例 2](media/service-premium-metrics-app/premium-metrics-app-15.png)


#### <a name="diagnosing-scenario-two"></a>診斷案例 2

從 **資料表 A** 選取一個具有高百分比等待時間的資料集。

![較長等候時間資料表](media/service-premium-metrics-app/premium-metrics-app-16.png)

一旦您選取了較長等待時間的資料集，**圖表 B** 會經過篩選，以顯示在過去七天內，該資料集的查詢等候時間分佈。 接下來，選取 **圖表 B** 的其中一個資料行。

![每小時較長等候時間分布圖](media/service-premium-metrics-app/premium-metrics-app-17.png)

然後會篩選 **圖表 C**，以顯示從圖表 B 選取的佇列時間長度。

![每小時查詢佇列長度](media/service-premium-metrics-app/premium-metrics-app-18.png)

如果佇列長度超過閾值 20，表示選取的資料集內的查詢可能會延遲，因為有太多查詢嘗試同時執行。

![執行查詢資料表](media/service-premium-metrics-app/premium-metrics-app-19.png)

#### <a name="remedies-for-scenario-two"></a>案例 2 的因應措施

您可以採取下列步驟來因應與案例 2 相關的問題：

1. **相應增加容量** - 將容量相應增加至下一個 SKU，將可提供高達目前 SKU 兩倍的記憶體，因而降低容量目前遇到的任何記憶體壓力。

2. **將資料集移至其他容量** - 如果您有另一個記憶體更大的容量可用，可以將包含較大型資料集的工作區移至該容量。


## <a name="the-refresh-waits-metric"></a>重新整理等候計量

**重新整理等候** 計量可在使用者能使用舊的或過時的報表資料時提供見解。 **重新整理等候** 是指指定的資料重新整理從依需求觸發或排定執行的時間開始算起，等到開始執行之間的等候時間。 此 KPI 會測量 10% 或更多的擱置中重新整理要求是否已等候 10 分鐘或更久。 當可用的記憶體或 CPU 不足時，通常就會產生等待情況。

![重新整理等候量測計](media/service-premium-metrics-app/premium-metrics-app-20.png)

此量測計會顯示自上次重新整理報表重新整理的過去七天內，3.18% 的重新整理等候超過 10 分鐘。 

若要了解 **重新整理等候** KPI 的詳細資料，請按一下 [瀏覽]  按鈕，這會在報表頁面的右欄中提供含有計量的頁面和疑難排解指南。 此指南提供和頁面上的計量有關的詳細說明，並協助您了解容量的狀態，以及可以採取哪些措施來緩解任何問題。

![探索重新整理等候計量](media/service-premium-metrics-app/premium-metrics-app-21.png)

這裡提供兩個案例說明，只要在報表頁面上選取 [案例 1] 或 [案例 2]，即可顯示說明。 我們將在下列各節中依序討論每個案例。

### <a name="scenario-one---not-enough-memory"></a>案例 1 - 記憶體不足

在案例 1 中，沒有足夠的可用記憶體來載入資料集。 在記憶體不足的情況下，有兩種情況會導致重新整理受到節流影響：

1. 記憶體不足，無法載入資料集。
2. 因為有優先順序較高的作業，所以重新整理遭到取消。 

載入資料集的優先順序如下：

1. 互動式查詢
2. 隨選重新整理
3. 排程重新整理

如果沒有足夠的記憶體可載入用於互動式查詢的資料集，系統會停止排程的重新整理，並卸載其資料集，直到有足夠的記憶體可使用為止。 如果無法釋出足夠的記憶體，系統會停止隨選重新整理，並卸載它們的資料集。

#### <a name="diagnosing-scenario-one"></a>診斷案例 1

若要診斷案例 1，請先判斷節流是否是因為記憶體不足所致。 判斷步驟如下所示。

1. 從 **資料表 A** 按一下您想進一步了解的資料集來將它選取： 

    ![資料表 A](media/service-premium-metrics-app/premium-metrics-app-22.png)

    a. 在 **資料表 A** 中選取資料集時，會篩選 **圖表 B** 以顯示發生等候情況的時間。

    ![圖表 B](media/service-premium-metrics-app/premium-metrics-app-23.png)

    b. 接著會篩選 **圖表 C** 以顯示任何節流，下一個步驟中會說明。 

2. 查看現在篩選後 **圖表 C** 的結果。如果圖表在資料集等待時發生記憶體不足節流，表示資料集是因記憶體不足而產生等候情況。

    ![圖表 C](media/service-premium-metrics-app/premium-metrics-app-24.png)

3. 最後，請檢查 **圖表 D**，其中會顯示所發生的重新整理為排定的或隨選的類型。 任何同時執行的隨選重新整理都可能是導致發生節流的原因。

    ![圖表 D](media/service-premium-metrics-app/premium-metrics-app-25.png)


#### <a name="remedies-for-scenario-one"></a>案例 1 的因應措施

您可以採取下列步驟來補救與案例 1 相關的問題：

1. **相應增加容量** - 將容量相應增加至下一個 SKU，將可提供高達目前 SKU 兩倍的記憶體，因而降低容量目前遇到的任何記憶體和 CPU 壓力。

2. **將資料集移至其他容量** - 如果您的等候時間是因記憶體壓力所造成，而且您有另一個記憶體更大的容量可用，可以將包含等候中資料集的工作區移至其他容量。

3. **將排程的重新整理分散** - 分散重新整理有助於避免太多重新整理嘗試同時執行。



### <a name="scenario-two---not-enough-cpu-for-refresh"></a>案例 2 - 沒有足夠的 CPU 可執行重新整理

在第 2 個案例中，沒有足夠的可用 CPU 來執行重新整理。 

針對容量，Power BI 會限制可同時發生的重新整理次數。 此數目相當於後端核心數 x 1.5 倍。 例如，具備 4 個後端核心的 P1 容量可同時執行 6 次重新整理。 一旦達到同時執行重新整理數上限，其他重新整理將會等候執行中的重新整理完成為止。

![重新整理的案例 2](media/service-premium-metrics-app/premium-metrics-app-26.png)

#### <a name="diagnosing-scenario-two"></a>診斷案例 2

若要診斷第 2 個案例，請先判斷是否是因為同時執行的重新整理數達到上限而發生節流。 判斷步驟如下所示。

1. 從 **資料表 A** 按一下您想進一步了解的資料集來將它選取： 

    ![資料表 A](media/service-premium-metrics-app/premium-metrics-app-22.png)

    a. 在 **資料表 A** 中選取資料集時，會篩選 **圖表 B** 以顯示發生等候情況的時間。

    ![圖表 B](media/service-premium-metrics-app/premium-metrics-app-23.png)

    b. 接著會篩選 **圖表 C** 以顯示任何節流，下一個步驟中會說明。 

2. 查看現在篩選後 **圖表 C** 的結果。如果圖表顯示在資料集等候時發生的「最高並行作業數目」  發生，代表資料集是因為沒有足夠的可用 CPU 而產生等候情況。

    ![圖表 C](media/service-premium-metrics-app/premium-metrics-app-24.png)

3. 最後，請檢查 **圖表 D**，其中會顯示所發生的重新整理為排定的或隨選的類型。 任何同時執行的隨選重新整理都可能是導致發生節流的原因。

    ![圖表 D](media/service-premium-metrics-app/premium-metrics-app-25.png)


#### <a name="remedies-for-scenario-two"></a>案例 2 的因應措施

1. **相應增加容量** - 將容量相應增加至下一個 SKU，將可提供高達目前 SKU 兩倍的記憶體，以及目前 SKU 兩倍的同時執行重新整理數處理能力，因而降低容量目前遇到的任何記憶體和 CPU 壓力。

2. **將資料集移至其他容量** - 如果您的等候時間是因達到並行作業數上限所造成，而且您有另一個具備並行作業能力的容量可用，可以將包含等候中資料集的工作區移至其他容量。

3. **將排程的重新整理分散** - 分散重新整理有助於避免太多重新整理嘗試同時執行。



## <a name="next-steps"></a>後續步驟

* [什麼是 Power BI Premium？](service-premium-what-is.md)
* [Microsoft Power BI Premium 白皮書](https://aka.ms/pbipremiumwhitepaper)
* [Planning a Power BI Enterprise Deployment (規劃 Power BI 企業部署) 技術白皮書](https://aka.ms/pbienterprisedeploy)
* [Pro 延長試用版啟用](../fundamentals/service-self-service-signup-for-power-bi.md)
* [Power BI Embedded 常見問題集](../developer/embedded/embedded-faq.md)

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)

Power BI 已推出 Power BI Premium Gen2 作為預覽供應項目，其能透過對下列領域的改進來改善 Power BI Premium 體驗：
* 效能
* 個別使用者授權
* 範圍更大的擴縮
* 改善的計量
* 自動調整
* 降低管理負擔

如需 Power BI Premium Gen2 的詳細資訊，請參閱 [Power BI Premium 第 2 代 (預覽)](service-premium-what-is.md#power-bi-premium-generation-2-preview)。