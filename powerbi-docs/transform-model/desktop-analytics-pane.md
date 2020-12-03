---
title: 使用 Power BI Desktop 中的 [分析] 窗格
description: 為 Power BI Desktop 中的視覺效果建立動態參考線
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: how-to
ms.date: 01/10/2020
LocalizationGroup: Create reports
ms.openlocfilehash: 1437e680ac7dc4114d68bd534ba8ec93dd8ae508
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96416040"
---
# <a name="use-the-analytics-pane-in-power-bi-desktop"></a>使用 Power BI Desktop 中的 [分析] 窗格

您可以使用 Power BI Desktop 的 [分析]  窗格，將動態「參考線」  新增至視覺效果，藉此彰顯重要的趨勢或見解。 [分析]  圖示與窗格位於 Power BI Desktop 的 [視覺效果]  區域中。

![[分析] 窗格，[視覺效果]，Power BI Desktop](media/desktop-analytics-pane/analytics-pane_1.png)

> [!NOTE]
> [分析]  窗格只會在您選取了 Power BI Desktop 畫布上的視覺效果時顯示。

## <a name="search-within-the-analytics-pane"></a>在分析窗格內進行搜尋

從 2018 年 2 月發行的 Power BI Desktop (2.55.5010.201 版或更新版本) 開始，您可以在 [視覺效果]  窗格的 [分析]  子窗格內進行搜尋。 當您選取 [分析]  圖示時，就會出現 [搜尋] 方塊。

![[搜尋] 方塊，[分析] 窗格，[視覺效果]，Power BI Desktop](media/desktop-analytics-pane/analytics-pane_1b.png)

## <a name="use-the-analytics-pane"></a>使用 [分析] 窗格

您可以使用 [分析]  窗格，建立下列類型的動態參考線：

* X 軸常數線
* Y 軸常數線
* 最小值線
* 最大值線
* 平均值線
* 最小值線
* 中間值線
* 對稱網底

> [!NOTE]
> 並非所有參考線都適用於所有類型的視覺效果。

下列章節示範可以如何在視覺效果中使用 [分析]  窗格及動態參考線。

若要檢視視覺效果可用的動態參考線，請遵循下列步驟：

1. 選取或建立視覺效果，然後從 [視覺效果]  區段選取 **分析** 圖示。

    ![檢視視覺效果分析，[視覺效果] 窗格，Power BI Desktop](media/desktop-analytics-pane/analytics-pane_2.png)

2. 選取您要建立的參考線類型以展開其選項。 在此案例中，我們將選取 [平均值線]  。

    ![[平均值線] 方塊，[分析] 窗格，[視覺效果]，Power BI Desktop](media/desktop-analytics-pane/analytics-pane_3.png)

3. 若要建立新的線，請選取 [ **+新增]&nbsp;** 。 然後您可以為參考線命名。 按兩下文字方塊並輸入您要的名稱。

    現在您可以設定參考線的各種選項了。 您可以指定其 [色彩]  、[透明度]  百分比、[線條樣式]  與 [位置]  \(相較於視覺效果的資料元素\)。 您也可以選擇是否要包含 [資料標籤]  。 若要依據您的參考線指定視覺效果量值，請選取 [量值]  下拉式清單，其中已自動填入視覺效果中的資料元素。 這裡我們選取 [文化特性]  作為量值，加上「文化特性平均值」  標籤，然後自訂其他幾個選項。

    ![文化特性平均值參考線，[分析] 窗格，視覺效果，Power BI Desktop](media/desktop-analytics-pane/analytics-pane_4.png)

4. 如果您希望顯示資料標籤，請將 [資料標籤]  從 [關閉]  變更為 [開啟]  。 當您這樣做時，即取得資料標籤的其他所有選項。

    ![[資料標籤] 設定，[分析] 窗格，視覺效果，Power BI Desktop](media/desktop-analytics-pane/analytics-pane_5.png)

5. 請注意顯示在 [分析]  窗格中，[平均值線]  項目旁的數字。 這告訴您視覺效果上目前有多少動態線及其類型。 如果我們針對 [負擔能力]  新增 [最大值線]  ，[分析]  窗格中就會顯示我們也對這個視覺效果套用了 [最大值線]  動態參考線。

    ![最大值線與平均值線總計，[分析] 窗格，視覺效果，Power BI Desktop](media/desktop-analytics-pane/analytics-pane_6.png)

如果您選取的視覺效果無法套用動態參考線 (在這個案例中為 [地圖]  視覺效果)，您就會在選取 [分析]  窗格時看到下列訊息。

![地圖視覺效果不提供的分析，[分析] 窗格，[視覺效果]，Power BI Desktop](media/desktop-analytics-pane/analytics-pane_7.png)

您可以透過 [分析]  窗格建立動態參考線，以醒目提示方式強調您感興趣的各種見解。

我們正在規劃更多功能，包括讓視覺效果有更多動態參考線可以套用。 因此請時常回來查看新功能。

## <a name="apply-forecasting"></a>套用預測

如果資料來源中有時間資料，您可以使用 [預測]  功能。 先選取視覺效果，然後展開 [分析]  窗格的 [預測]  區段。 您可以指定多個輸入以修改預測結果，例如「預測長度」  或「信賴區間」  等。 下圖顯示已套用預測的基本參考線視覺效果。 使用您的想像 (並嘗試運用預測) 來了解如何將其套用到您的模型。

![預測功能，[分析] 窗格，[視覺效果]，Power BI Desktop](media/desktop-analytics-pane/analytics-pane_8.png)

> [!NOTE]
> 預測功能僅適用於折線圖視覺效果。

## <a name="limitations"></a>限制

使用動態參考線的能力取決於使用的視覺效果類型。 下列清單更明確地描述了這些限制。

您可以在以下的視覺效果中，使用「X 軸常數線」  、「Y 軸常數線」  與「對稱網底」  ：

* 散佈圖

您可以在下列視覺效果上使用「常數線」  、「最小值線」  、「最大值線」  、「平均值線」  、「中間值線」  與「百分位數線」  ：

* 區域圖
* 群組橫條圖
* 群組直條圖
* 折線圖
* 散佈圖

下列視覺效果只可從 [分析]  窗格使用「常數線」  ：

* 堆疊區域圖
* 堆疊橫條圖
* 堆疊直條圖
* 瀑布圖
* 100% 堆疊橫條圖
* 100% 堆疊直條圖

如果有時間資料，下列視覺效果就可以使用「趨勢線」  ：

* 區域圖
* 群組直條圖
* 折線圖
* 折線圖和群組直條圖

最後，您目前無法將任何動態參考線套用到許多視覺效果，包括 (但不限於)：

* 漏斗圖
* 折線圖和群組直條圖
* 折線圖和堆疊直條圖
* 功能區圖表
* 非笛卡兒視覺效果，例如環圈圖、量測計、矩陣、圓形圖和資料表

唯有在 *Power BI Desktop* 中使用匯入的資料時，或是即時連線到執行 **Analysis Service 2016** 或更新版本、**Azure Analysis Services** 之伺服器上的模型或 Power BI 服務上的資料集時，才能使用百分位數線。

## <a name="next-steps"></a>後續步驟

您可以使用 Power BI Desktop 執行各種作業。 如需有關其功能的詳細資訊，請參閱下列資源：

* [Power BI Desktop 的新功能](../fundamentals/desktop-latest-update.md)
* [取得 Power BI Desktop](../fundamentals/desktop-get-the-desktop.md)
* [Power BI Desktop 是什麼？](../fundamentals/desktop-what-is-desktop.md)
* [Power BI Desktop 的查詢概觀](desktop-query-overview.md)
* [Power BI Desktop 中的資料類型](../connect-data/desktop-data-types.md)
* [使用 Power BI Desktop 合併資料並使其成形](../connect-data/desktop-shape-and-combine-data.md)
* [在 Power BI Desktop 中執行常見工作](desktop-common-query-tasks.md)
