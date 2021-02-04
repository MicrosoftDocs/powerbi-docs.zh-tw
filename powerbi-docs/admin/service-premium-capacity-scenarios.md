---
title: Microsoft Power BI 容量案例
description: 描述常見的 Power BI 容量案例。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: conceptual
ms.date: 11/11/2020
ms.custom: ''
LocalizationGroup: Premium
ms.openlocfilehash: 0038cce77a62f32a5fb5ca32a49fd8f6337352a6
ms.sourcegitcommit: c33e53e1fab1f29872297524a7b4f5af6c806798
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/04/2021
ms.locfileid: "99532743"
---
# <a name="premium-capacity-scenarios"></a>Premium 容量案例

本文描述已實作 Power BI Premium 容量的真實案例。 文中也會說明常見問題和挑戰，以及如何找出問題並協助解決這些問題：

- [將資料集保持在最新狀態](#keeping-datasets-up-to-date)
- [識別回應緩慢的資料集](#identifying-slow-responding-datasets)
- [識別偶發性資料集回應緩慢的原因](#identifying-causes-for-sporadically-slow-responding-datasets)
- [判斷是否有足夠的記憶體](#determining-whether-there-is-enough-memory)
- [判斷是否有足夠的 CPU](#determining-whether-there-is-enough-cpu)

步驟和圖表、資料表範例來自 **Power BI Premium 容量計量應用程式**，Power BI 管理員有權可存取。

> [!NOTE]
> Power BI Premium 最近已發行名叫 **Premium Gen2** 的新版本 Premium，其目前處於預覽狀態。 Premium Gen2 將能簡化 Premium 容量的管理，並減少管理負擔。 如需詳細資訊，請參閱 [Power BI Premium 第 2 代 (預覽)](service-premium-what-is.md#power-bi-premium-generation-2-preview)。
>
>若要查看 Power BI Embedded Gen2 增強功能，請參閱 [Power BI Embedded 層代 2](../developer/embedded/power-bi-embedded-generation-2.md)。

## <a name="keeping-datasets-up-to-date"></a>將資料集保持在最新狀態

在此案例中，當使用者抱怨報表資料有時似乎是舊的或「過時」時，就會觸發調查。

在應用程式中，管理員會與 [重新整理]  視覺效果進行互動，並依據 [最長等候時間]  以遞減的順序排序資料集。 此視覺效果可協助他們揭露等候時間最長的資料集 (依工作區名稱分組)。

![資料集重新整理，依遞減的最長等候時間排序，且依工作區分組](media/service-premium-capacity-scenarios/dataset-refreshes.png)

在 [每小時平均重新整理等候時間]  視覺效果中，他們注意到重新整理等候時間的尖峰持續發生在每天 4PM。

![重新整理等候的尖峰固定在 4PM](media/service-premium-capacity-scenarios/peak-refresh-waits.png)

這些結果有幾個可能的解釋：

- 可能同時發生太多重新整理嘗試，超過容量節點所定義的限制。 在此案例中，在具備預設記憶體配置的 P1 上同時有六個重新整理。

- 要重新整理的資料集可能太大，而無法放入可用的記憶體中 (至少需要兩倍的記憶體才能進行完整重新整理)。
- 效率不佳的 Power Query 邏輯可能會在資料集重新整理期間導致記憶體使用尖峰。 當容量忙碌時，此尖峰可能偶爾會達到實體限制，使重新整理失敗，而且可能會影響容量的其他報表檢視作業。
- 經常被查詢的資料集必須留在記憶體中，可能會影響其他資料集重新整理的能力，因為可用的記憶體有限。

為了協助調查，Power BI 管理員可以尋找：

- 資料重新整理時的不足可用記憶體，當時的可用記憶體小於要重新整理的資料集大小的 2 倍。
- 尚未重新整理的資料集，它們在重新整理之前不在記憶體中，且會在重新整理時間拉長時開始顯示互動式流量。 若要查看在任何指定時間載入記憶體的資料集，Power BI 系統管理員可查看應用程式中 [資料集] 索引標籤的資料集區域。 然後，系統管理員可按一下 [每小時載入的資料集計數] 的其中一個橫列，藉此交叉篩選至特定時間。 下圖中的一個局部尖峰，表示將多個資料集載入記憶體中的一個小時，可能會使排程的重新整理延遲開始。
- 當排程的資料重新整理開始時，所發生的資料集收回增加。 收回可能表示在重新整理之前提供太多不同互動式報表而導致記憶體壓力。 [每小時資料集收回和記憶體耗用量]  視覺效果可以清楚指出收回中的尖峰。

下圖顯示已載入資料集中的本機尖峰，可看出互動式查詢導致重新整理開始的延遲。 在 [每小時載入的資料集計數] 視覺效果中選取一段時間，將會交叉篩選 [資料集大小] 視覺效果。

![已載入資料集中的局部尖峰，顯示互動式查詢使重新整理的開始延遲](media/service-premium-capacity-scenarios/hourly-loaded-dataset-counts.png)

Power BI 管理員可以採取下列步驟來嘗試解決此問題，以確保有足夠的記憶體可供資料重新整理開始：

- 聯絡資料集擁有者，要求他們將資料重新整理排程錯開和拉長間隔。
- 移除不必要的儀表板或儀表板磚，特別是強制執行資料列層級安全性的內容，以減少資料集查詢的載入。
- 藉由最佳化 Power Query 邏輯來加速資料重新整理。 改善計算結果欄或資料表的模型建立。 減少資料集大小或設定較大的資料集，以執行累加式資料重新整理。

## <a name="identifying-slow-responding-datasets"></a>識別回應緩慢的資料集

在此案例中，已開始針對使用者抱怨特定報表花太多時間開啟進行調查。 有時候報表會停止回應。

Power BI 系統管理員可使用應用程式中的 [查詢持續時間] 視覺效果，依遞減的 [平均持續期間] 來排序資料集，藉此判斷效能最差的資料集。 此視覺效果也會顯示資料集查詢計數，讓您可以查看資料集的查詢頻率。

![效能最差的資料集](media/service-premium-capacity-scenarios/worst-performing-datasets.png)

管理員可以參考 [查詢持續時間分佈]  視覺效果，其中顯示在篩選的時間週期內，貯體裡查詢效能的整體分佈 (< = 30 毫秒，0-100 毫秒)。 一般而言，大多數使用者會將花費時間小於一秒的查詢視為回應性良好。 花費較長時間的查詢通常會造成效能不佳此認知。

[每小時查詢持續時間分佈]  視覺效果讓 Power BI 管理員識別出容量效能可能被認為不佳的一小時期間。 代表著查詢持續時間超過一秒的長條區段越大，使用者會感覺效能不佳的風險就越大。

視覺效果是互動式的，若選取某個長條區段，就會交叉篩選報表頁面上與之對應的 [查詢持續時間]  資料表視覺效果，以顯示其所代表的資料集。 這種交叉篩選可讓 Power BI 管理員輕鬆地識別哪些資料集的回應速度很慢。

下圖為以 [每小時查詢持續時間分佈] 篩選的視覺效果，其著重在一小時單位中效能最差的資料集。

![篩選後的 [每小時查詢持續時間分佈] 視覺效果顯示效能較差的資料集](media/service-premium-capacity-scenarios/hourly-query-duration-distributions.png)

在找出於特定一小時的時間範圍內效能不佳資料集後，Power BI 系統管理員即可調查效能不佳是因容量過載所造成，還是因為資料集或報表設計不佳所導致。 他們可以參考 [查詢等候時間]  視覺效果，並以遞減的平均查詢等候時間來排序資料集。 如果有大量查詢正在等候，則對資料集的高需求便可能是造成太多查詢延遲其原因。 如果平均查詢等候時間相當大 (> 100 毫秒)，最好檢查資料集和報表，看看是否可加以改進。 例如，減少指定報表頁面上的視覺效果，或是 DAX 運算式最佳化。

![[查詢等候時間] 視覺效果有助於揭露效能不佳的資料集](media/service-premium-capacity-scenarios/query-wait-times.png)

資料集中查詢等候時間堆積的可能原因有好幾個：

- 不夠好的模型設計、量值運算式、或甚至是報表的設計 - 可能會導致長時間執行的查詢高度耗用 CPU 的所有情況。 這會強制新的查詢等候，直到 CPU 執行緒變成可用狀態，並可建立在尖峰上班時間內經常看到的結隊效果 (想想塞車)。 [查詢等待]  頁面將會是主要資源，用以判斷資料集是否有較高的平均查詢等候時間。
- 大量同時的容量使用者 (數百到數千個) 取用相同的報表或資料集。 即使是設計良好的資料集，也可能在並行臨界值之下執行不良。 此效能問題是由單一資料集其查詢計數遠高於其他資料集的查詢計數所導致。 例如：您可能會看到一個資料集有 30 萬筆查詢，但其他所有資料集的查詢數都低於 30 萬。 在某個時間點，對此資料集的查詢會開始錯開，這可以在 [查詢持續時間]  視覺效果中看到。
- 同時查詢許多不同的資料集，導致資料集進出記憶體的頻繁循環，因而過度置換。 此狀況會造成使用者將資料集載入記憶體時效能不佳的問題。 若要確認，Power BI 管理員可以參考 [每小時資料集收回和記憶體耗用量]  視覺效果，它可能顯示正在重複收回已大量載入記憶體的資料集。

## <a name="identifying-causes-for-sporadically-slow-responding-datasets"></a>識別偶發性資料集回應緩慢的原因

在此案例中，已針對使用者表示報表視覺效果有時回應速度很慢或變得沒有回應開始進行調查。 在其他時間，報表視覺效果的回應性有時候又能令人接受。

使用應用程式內的 [查詢持續時間]  區段，以下列方式尋找肇事的資料集：

- 在 [查詢持續時間] 視覺效果中，系統管理員依資料集篩選資料集 (從查詢過的最上方資料集開始)，並檢查 [每小時查詢散發] 視覺效果中的交叉篩選列。
- 當單一一小時長條顯示出「所有查詢持續時間群組 vs. 該資料集的其他一小時長條」之間的比率明顯改變，(例如，色彩之間的比率大幅變化)，這表示此資料集的效能發生了偶發性的變更。
- 顯示出效能不良查詢異常部分的一小時長條，恰好指出該資料集受到嘈雜鄰居效應影響的時間範圍 (鄰居效應由其他資料集的活動造成)。

下圖為 1 月30 日中的一小時，這期間發生資料集效能顯著變慢的情形，以 "(3,10s]" 的執行持續時間貯體大小表示。 按一下這一小時長條可顯示在這段時間內載入記憶體的所有資料集，並顯露出可能造成嘈雜鄰居效應的資料集。

![顯示最差效能 (很大一部分) 的長條](media/service-premium-capacity-scenarios/worst-performing-queries.png)

一旦識別出有問題的時間範圍 (例如，上圖中的 1 月 30 日)，Power BI 管理員可以移除所有資料集篩選，然後只篩選該時間範圍，以判斷在這段時間內主動查詢的資料集。 造成嘈雜鄰居效應的肇事資料集，通常是最常查詢或是最長平均查詢持續時間的資料集。

此問題的解決方法之一，是將肇事資料集散佈在不同的工作區上、不同 Premium 容量上，或是在支援資料集大小、耗用量需求和資料重新整理模式的共用容量上。

反過來做也可以。 Power BI 管理員可以識別資料集查詢效能大幅改善的時間，然後尋找不在其中的資料集。 如果該時間點缺少特定資訊，可能有助於指向造成問題的原因。

## <a name="determining-whether-there-is-enough-memory"></a>判斷是否有足夠的記憶體

若要判斷是否有足夠的記憶體容量可完成其工作負載，Power BI 管理員可以參考應用程式的 [資料集] 索引標籤中 [耗用的記憶體百分比] 視覺效果。 [全部]  (總計) 記憶體代表載入記憶體中的資料集所耗用的記憶體，不論它們是否為主動查詢或處理。 [使用中]  記憶體代表目前正在主動處理之資料集所耗用的記憶體。

狀況良好的容量，視覺效果看起來會像這樣，顯示 [全部] (總計) 和 [使用中] 記憶體之間的差距：

![狀況良好的容量會顯示 [全部] (總計) 和 [使用中] 記憶體之間的差距](media/service-premium-capacity-scenarios/memory-healthy-capacity.png)

在遭遇記憶體壓力的容量中，同一視覺效果會清楚顯示使用中記憶體和總記憶體貼近，這表示無法再將其他資料集載入記憶體中。 在此情況下，Power BI 管理員可以按一下 [容量重新啟動]  (在管理入口網站的容量設定區域的 [進階選項]  中)。 重新啟動容量會將所有資料集從記憶體中清除，並允許它們視需要重新載入記憶體中 (藉由查詢或資料重新整理)。

> [!NOTE]
> 針對 Premium Gen2 和 [Embedded Gen2](../developer/embedded/power-bi-embedded-generation-2.md)，不需要追蹤記憶體耗用量。 Premium Gen2 和 Embedded Gen2 的唯一限制是單一成品的記憶體使用量。 磁碟使用量不能超過容量上可用的記憶體。 如需 Premium Gen2 的詳細資訊，請參閱 [Power BI Premium 第 2 代 (預覽)](service-premium-what-is.md#power-bi-premium-generation-2-preview)。

![**使用中** 記憶體與 **所有** 記憶體貼近](media/service-premium-capacity-scenarios/memory-unhealthy-capacity.png)

## <a name="determining-whether-there-is-enough-cpu"></a>判斷是否有足夠的 CPU

一般來說，容量的平均 CPU 使用率應維持低於80%。 超過此值表示容量已接近 CPU 飽和。

CPU 飽和會表現在作業花費的時間比所需的更長，因為 CPU 嘗試處理所有作業時，會執行許多 CPU 環境切換。 這在具有大量同時查詢的 Premium 容量中，表現出來就是查詢等候時間拉長。 查詢等候時間拉長的結果，就是回應速度比平常慢。 Power BI 管理員可以藉由檢視 [每小時查詢等候時間分佈]  視覺效果，輕鬆地識別 CPU 何時飽和。 查詢等候時間的週期性尖峰計數表示 CPU 可能飽和。

![查詢等候時間的定期尖峰計數表示 CPU 可能飽和](media/service-premium-capacity-scenarios/peak-query-wait-times.png)

在背景作業中，有時會偵測到類似的模式 (如果背景作業會影響 CPU 飽和)。 Power BI 管理員可以針對特定資料集尋找重新整理時間的週期性尖峰，這可能表示當時的 CPU 飽和 (可能是因為其他正在進行的資料集重新整理和/或互動式查詢)。 在此情況下，應用程式中的 [系統]  檢視不一定能顯示 CPU 處於100%。 [系統]  檢視會顯示每小時的平均值，但 CPU 可能會在繁重作業時飽和數分鐘，且在等候時間中顯示尖峰。

有更多細微之處可看出 CPU 飽和。 雖然等候的查詢數目很重要，但查詢等候時間某些程度一定會發生，而不會造成明顯效能降低。 某些資料集 (平均查詢時間較長，表示複雜度或大小) 比其他資料集更容易受 CPU 飽和的影響。 若要輕鬆識別出這些資料集，Power BI 管理員可以在 [每小時等候時間分佈]  視覺效果中，尋找色彩組合變更的長條。 在找到極端值長條之後，他們可以尋找在該時間內有查詢等候的資料集，並查看其平均查詢等候時間，與平均查詢持續時間相比較。 當這兩個計量的大小相同，而且資料集的查詢工作負載並非微不足道時，很可能是因為 CPU 不足而影響資料集。

當多個使用者短時間高頻率耗用資料集時 (例如，在訓練課程中)，這種效果可能特別明顯，每次的高載都會導致 CPU 飽和。 在此情況下，此資料集可能面臨嚴重的查詢等候時間，而且會影響容量中的其他資料集 (嘈雜鄰居效應)。

在某些情況下，Power BI 管理員可以藉由建立儀表板 (會以任何資料集重新整理定期查詢快取的圖格) 而不是報表，來要求資料集擁有者建立較穩定的查詢工作負載。 這有助於避免儀表板載入時的尖峰。 對於指定的商務需求，此解決方案可能不一定可行，不過，它可以是不需要變更資料集就避免 CPU 飽和的有效方式。

> [!NOTE]
> 針對 Premium Gen2 和 [Embedded Gen2](../developer/embedded/power-bi-embedded-generation-2.md)，CPU 時間使用率會在每個成品層級上追蹤，而且會顯示在容量使用率應用程式中。 每個成品都會顯示其在指定時間範圍內的總 CPU 時間使用率。 如需 Premium Gen2 的詳細資訊，請參閱 [Power BI Premium 第 2 代 (預覽)](service-premium-what-is.md#power-bi-premium-generation-2-preview)。

## <a name="acknowledgments"></a>通知

本文是由資料平台 MVP 暨 [Bitwise Solutions](https://www.bitwisesolutions.com.au/) 的獨立 BI 專家 Peter Myers 所撰寫。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [使用應用程式監視 Premium 容量](service-admin-premium-monitor-capacity.md)    
> [!div class="nextstepaction"]
> [在管理入口網站中監視容量](service-admin-premium-monitor-portal.md)   

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)

Power BI 已推出 Power BI Premium Gen2 作為預覽供應項目，其能透過對下列領域的改進來改善 Power BI Premium 體驗：
* 效能
* 個別使用者授權
* 範圍更大的擴縮
* 改善的計量
* 自動調整
* 降低管理負擔

如需 Power BI Premium Gen2 的詳細資訊，請參閱 [Power BI Premium 第 2 代 (預覽)](service-premium-what-is.md#power-bi-premium-generation-2-preview)。

