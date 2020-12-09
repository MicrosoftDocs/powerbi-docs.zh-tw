---
title: 在視覺效果中向下切入及向上切入
description: 本文說明如何向下切入 Microsoft Power BI 服務的視覺效果。
author: mihart
ms.author: mihart
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: pbi-explore
ms.topic: how-to
ms.date: 12/03/2020
LocalizationGroup: Visualizations
ms.openlocfilehash: c379e60e346912c6ecccc6df9671b7d527edc114
ms.sourcegitcommit: cb6e0202de27f29dd622e47b305c15f952c5769b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2020
ms.locfileid: "96578214"
---
# <a name="drill-mode-in-a-visual-in-power-bi"></a>Power BI 視覺效果中的切入模式

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]


本文說明如何向下切入 Microsoft Power BI 服務的視覺效果。 在您的資料點上使用向下切入和向上切入，您可以深入探索資料。 

## <a name="drill-requires-a-hierarchy"></a>鑽研需要階層

當視覺效果有階層時，您可以向下鑽研以顯示其他詳細資料。 例如，您可能有一個視覺效果，它會以運動、專業領域和活動所構成的階層來查看奧運獎牌計數。 根據預設，視覺效果會依運動 (體操、滑雪、水上運動等) 顯示獎牌計數。 但因為它有階層，因此當您選取其中一個視覺項目 (例如橫條圖、折線圖或泡泡圖) 時，會顯示越來越詳細的圖片。 當您選取 [水上運動]  項目時，會顯示游泳、跳水和水球的資料。  選取 [跳水]  項目素時，會顯示跳板、跳台和雙人跳水活動的詳細資料。

日期是獨特的階層類型。  報表設計師通常會在視覺效果中新增日期階層。 常見的日期階層包含年份、季度、月份和日。 

## <a name="figure-out-which-visuals-can-be-drilled"></a>找出可以切入的視覺效果
不確定哪些 Power BI 視覺效果包含階層？ 請將游標停留在視覺效果上。 如果您在頂端看到這些切入控制項的組合，則表示此視覺效果有階層。

![切入圖示的螢幕擷取畫面。](./media/end-user-drill/power-bi-drill-icons.png)  


## <a name="learn-how-to-drill-down-and-up"></a>了解如何向下切入和向上切入

在此範例中，我們會使用樹狀圖，其階層由國家/地區、城市、郵遞區號和商店名稱組成。 在切入樹狀圖之前，系統會依國家/地區查看今年售出的單位總量。 「地區」是階層的最上層。

![樹狀圖和其篩選條件的螢幕擷取畫面。](./media/end-user-drill/power-bi-treemap.png)  


### <a name="two-ways-to-access-the-drill-features"></a>存取切入功能的兩種方式

針對具有階層的視覺效果，您可以透過兩種方式來存取向下切入、向上切入及展開功能。 請兩種都試試看，並使用您最喜歡的方式。

- 第一種方法：將游標暫留在視覺效果上，以查看並使用圖示。 透過選取向下箭號，先開啟向下切入。 灰色背景可讓您知道向下切入是作用中狀態。   

    ![停留範例的螢幕擷取畫面。](./media/end-user-drill/power-bi-drill-hover.png)

- 第二種方法：以滑鼠右鍵按一下視覺效果以顯示及使用功能表。

    ![按一下滑鼠右鍵範例的螢幕擷取畫面。](./media/end-user-drill/power-bi-drill-action-menu.png)



## <a name="drill-pathways"></a>鑽研路徑

### <a name="drill-down-all-fields-at-once"></a>一次向下切入所有欄位
![向下切入圖示](./media/end-user-drill/power-bi-drill-icon3.png)

您可以透過數種方式來切入視覺效果。 選取雙箭號 ![一次切入所有層級的圖示](./media/end-user-drill/power-bi-drill-icon3.png) 向下切入圖示會帶您前往階層中的下一層。 如果您查看肯塔基州和田納西州的 [國家/地區] 層級，即可向下切入至這兩州的城市層級，然後是這兩州的郵遞區號層級，最後再到這兩州的商店名稱層級。 路徑中的每個步驟都會顯示新的資訊。

![此圖顯示切入路徑](./media/end-user-drill/power-bi-drill-path.png)

選取向上切入圖示 ![向上切入圖示](./media/end-user-drill/power-bi-drill-icon5.png) 直到您回到 [依國家/地區的今年總單位數]。

### <a name="expand-all-fields-at-once"></a>一次展開所有欄位
![展開圖示](./media/end-user-drill/power-bi-drill-icon6.png)

「展開」會將其他階層層級新增至目前的檢視。 因此，如果您要查看 **區域** 層級，您可以同時展開樹狀結構中的所有目前分葉。  您的第一個切入會同時為 **KY** 與 **TN** 新增城市資料。 下一個切入會同時為 **KY** 與 **TN** 新增郵遞區號資料，而且也會保留城市資料。 路徑中的每個步驟都會顯示相同的資訊，並在每一個層級新增新的資訊。

![此圖顯示展開路徑](./media/end-user-drill/power-bi-expand-path.png)


### <a name="drill-down-one-field-at-a-time"></a>一次向下切入一個欄位


1. 選取向下切入圖示將它開啟 ![已開啟向下切入開啟/關閉圖示的螢幕擷取畫面。](./media/end-user-drill/power-bi-drill-icon2.png).

    現在，當您選取視覺效果項目時，即可選擇 [逐一向下切入欄位]。 視覺效果項目範例為：橫條圖、泡泡圖和分葉圖。

    ![箭號指向向下切入開啟/關閉圖示已開啟的視覺效果螢幕擷取畫面。](media/end-user-drill/power-bi-select-drill-icon.png)

    如果您未開啟向下切入，則選取視覺效果項目 (例如橫條圖、泡泡圖或分葉圖) 時，就不會向下切入。 相反地，它會交叉篩選報表頁面上的其他圖表。

1. 針對 **TN** 選取「分葉」。 現在，您的樹狀圖會顯示田納西州中擁有商店的全部城市和國家/地區。

    ![僅顯示 TN 資料的樹狀圖螢幕擷取畫面。](media/end-user-drill/power-bi-drill-down-first.png)

1. 目前，您可以：

    1. 繼續針對田納西州向下切入。

    1. 針對田納西州中的特定城市向下切入。

    1. 這次，改為展開。

    繼續一次向下切入一個欄位。  選取 [Knoxville, TN]。 現在樹狀圖會顯示您在 Knoxville 之商店的郵遞區號。

    ![顯示郵遞區號 37919 的樹狀圖螢幕擷取畫面。](media/end-user-drill/power-bi-drill-twice.png)

    請注意當您向下鑽研並重新往回時，標題會變更。

    此外，再向下切入一個欄位。 選取郵遞區號 **37919** 並向下切入至商店名稱。 

    ![顯示所有 Knoxville Lindseys 之樹狀圖的螢幕擷取畫面。](media/end-user-drill/power-bi-drill-last.png)    

    針對此特定資料，一次向下切入所有層級可能並不有趣。 讓我們改為嘗試展開。

### <a name="expand-all-and-expand-one-field-at-a-time"></a>一次全部展開欄位和一次展開一個欄位

只顯示郵遞區號或商店名稱的樹狀圖無法提供足夠的資訊。  那麼，讓我們向下「展開」階層的一個層級。  

1. 首先，向上切回郵遞區號層級。     
1. 在樹狀圖使用中的情況下，選取向下展開圖示 ![向下展開圖示的螢幕擷取畫面](./media/end-user-drill/power-bi-drill-icon6.png)。 您的樹狀圖現在顯示兩個層級的階層：郵遞區號與商店名稱。

    ![顯示郵遞區號和商店名稱的樹狀圖螢幕擷取畫面](./media/end-user-drill/power-bi-expand.png)

1. 若要查看田納西州所有四個階層層級的資料，請選取向上切入箭號，直到您到達第二個層級，亦即 [依地區與城市的今年總單位數]。

    ![顯示所有 TN 資料的樹狀圖螢幕擷取畫面。](media/end-user-drill/power-bi-expand-second.png)

1. 請確定向下切入仍然開啟 ![已開啟向下切入開啟/關閉圖示的螢幕擷取畫面。](./media/end-user-drill/power-bi-drill-icon2.png) 並選取向下展開圖示 ![向下展開圖示的螢幕擷取畫面](./media/end-user-drill/power-bi-drill-icon6.png)。 樹狀圖現在會顯示相同數目的分葉 (方塊)，但每個分葉有額外的詳細資料。 除了城市與州之外現在也會顯示郵遞區號。

    ![顯示城市、州和郵遞區號的視覺效果螢幕擷取畫面。](./media/end-user-drill/power-bi-expand-third.png)

1. 再次選取 [向下展開] 以在樹狀圖上顯示田納西州詳細資料的所有四個階層層級。 將滑鼠停留在分葉以查看更多詳細資料。

    ![顯示工具提示與分葉特定資料的樹狀圖螢幕擷取畫面。](./media/end-user-drill/power-bi-expand-final.png)

## <a name="show-the-data-as-you-drill"></a>在您切入時顯示資料
使用 [顯示為資料表] 以了解背後所代表的意義。 每次您切入或展開時，[顯示為資料表] 都會顯示要用來建置視覺效果的資料。 這可能有助您了解階層、切入和展開如何搭配運作以建置視覺效果。 

在右上角選取 [更多動作] \(...\)，然後選取 [顯示為資料表]。 

![省略符號功能表的螢幕擷取畫面。](./media/end-user-drill/power-bi-more-actions.png)

Power BI 會開啟樹狀圖，以便其可填滿畫布。 構成樹狀圖的資料會顯示在視覺效果下方。 

![具有如下所示之資料表的樹狀圖螢幕擷取畫面。](./media/end-user-drill/power-bi-show-table.png)

在畫布中只有視覺效果的情況下，繼續進行切入。 監看資料表中的資料變更，以反映用來建立樹狀圖的資料。 下表顯示從國家/地區到商店名稱，一次向下切入所有欄位的結果。 第一個資料表代表階層的最上層，顯示兩個分葉的樹狀圖，一個用於 **KY**，另一個用於 **TN**。 當您一次向下切入所有層級時，接下來的三個資料表代表樹狀圖的資料，從地區到城市到郵遞區號到商店名稱。


![顯示向下切入全部四個層級資料的螢幕擷取畫面。](./media/end-user-drill/power-bi-show-data.png)

請注意，[城市]、[郵遞區號] 和 [名稱] 的總計相同。 符合項總計並不一定都是如此。  但是針對這項資料，每個郵遞區號和每個城市都只有一間商店。  



## <a name="considerations-and-limitations"></a>考量與限制
- 根據預設，切入不會篩選報表中的其他視覺效果。 不過，報表設計師可以變更此預設行為。 當您切入時，請查看頁面上的其他視覺效果是否為交叉篩選或交叉醒目提示。

- 檢視與您共用的報表需要 Power BI Pro 或 Premium 授權，或者要將報表儲存在 Power BI Premium 容量中時也一樣。 [我有哪些授權？](end-user-license.md)


## <a name="next-steps"></a>後續步驟

[Power BI 報表中的視覺效果](../visuals/power-bi-report-visualizations.md)

[Power BI 報表](end-user-reports.md)

[Power BI - 基本概念](end-user-basic-concepts.md)

有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)
