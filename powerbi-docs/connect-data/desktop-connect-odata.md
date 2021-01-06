---
title: 在 Power BI Desktop 中連接至 OData 摘要
description: 輕鬆地在 Power BI Desktop 中連接至 OData 摘要並加以使用
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 01/04/2021
LocalizationGroup: Connect to data
ms.openlocfilehash: d1a4e8f7d5a057b51de7284d0db0b2440ccb93df
ms.sourcegitcommit: 932f6856849c39e34229dc9a49fb9379c56a888a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97926449"
---
# <a name="connect-to-odata-feeds-in-power-bi-desktop"></a>在 Power BI Desktop 中連接至 OData 摘要
在 Power BI Desktop 中，您可以連接至 **OData 摘要** 並使用基礎資料，就像 Power BI Desktop 中的任何其他資料來源。

若要連接至 OData 摘要，請在 Power BI Desktop 內選取 [主資料夾] 功能區的 [取得資料] > [OData 摘要]。

![Power BI Desktop 中 [取得資料] 功能區的螢幕擷取畫面，其中顯示 [OData 摘要] 選取項目。](media/desktop-connect-odata/connect-to-odata_1.png)

在出現的 [OData 摘要] 視窗中，將您的 OData 摘要 URL 輸入或貼到方塊內，然後選取 [確定]。

![[OData 摘要] 對話方塊的螢幕擷取畫面，其中顯示 [URL] 欄位。](media/desktop-connect-odata/connect-to-odata_2.png)

Power BI Desktop 連接至 OData 摘要，並在 [導覽] 視窗中顯示可用的資料表和其他資料元素。 當您選取一項元素時，[導覽] 視窗右方窗格會顯示資料的預覽。 您可以選取任何數量的資料表進行匯入。 [導覽] 視窗會顯示目前所選取資料表的預覽。

![[導覽] 對話方塊的螢幕擷取畫面，其中顯示所選資料表資料的預覽。](media/desktop-connect-odata/connect-to-odata_3.png)

您可以選擇 [編輯] 按鈕，其會啟動 [查詢編輯器]，供您在匯入 Power BI Desktop 之前從 OData 摘要修改或轉換資料。 或著您可以選取 [載入] 按鈕，然後匯入您在左窗格中選取的所有資料元素。

當我們選取 [載入] 時，Power BI Desktop 會匯入選取的元素，並顯示匯入進度的 [載入] 視窗。

![[載入] 對話方塊的螢幕擷取畫面，其中顯示匯入進度。](media/desktop-connect-odata/connect-to-odata_4.png)

完成後，Power BI Desktop 會讓選取的資料表和其他資料元素可以在 [欄位] 窗格中使用，其會出現在 Power BI Desktop 中 [報表] 檢視的右側。

![[欄位] 窗格的螢幕擷取畫面，其中顯示已選取資料表的清單。](media/desktop-connect-odata/connect-to-odata_5.png)

這樣就大功告成了！

您現在可以在 Power BI Desktop 中使用從 OData 摘要匯入的資料來建立視覺效果、報表，或與其他任何您可能想要連接或匯入的資料進行互動，例如其他 Excel 活頁簿、資料庫其他資料來源。

## <a name="next-steps"></a>後續步驟
您可以使用 Power BI Desktop 連接至各式各樣的資料。 如需有關資料來源的詳細資訊，請參閱下列資源︰

* [Power BI Desktop 是什麼？](../fundamentals/desktop-what-is-desktop.md)
* [Power BI Desktop 中的資料來源](desktop-data-sources.md)
* [使用 Power BI Desktop 合併資料並使其成形](desktop-shape-and-combine-data.md)
* [在 Power BI Desktop 中連接至 Excel 活頁簿](desktop-connect-excel.md)   
* [直接將資料輸入 Power BI Desktop 中](desktop-enter-data-directly-into-desktop.md)   
