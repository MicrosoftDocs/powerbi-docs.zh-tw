---
title: 從 Power BI 視覺效果匯出資料
description: 從報表視覺效果和儀表板視覺效果匯出資料，並在 Excel 中檢視。
author: mihart
ms.author: mihart
ms.reviewer: cmfinlan
featuredvideoid: removed
ms.service: powerbi
ms.subservice: pbi-explore
ms.topic: how-to
ms.date: 12/21/2020
LocalizationGroup: Consumers
ms.openlocfilehash: cd07004149afd2525c5830e04e5c2490eeebcb3c
ms.sourcegitcommit: 0711972326521944fdd8572403c0b15f31b916da
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97721378"
---
# <a name="export-data-from-a-visual"></a>匯出視覺效果的資料

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]


若要查看用來建立視覺效果的資料，[您可在 Power BI 中顯示該資料](end-user-show-data.md)或將其匯出至 Excel。 匯出資料的選項需要特定類型或授權，以及內容的編輯權限。 如果無法匯出，請連絡 Power BI 系統管理員或 IT 技術支援中心。 

匯出資料需要 Power BI Pro 授權，使用 Premium 容量與您共用的儀表板或報表也需要。 若要深入了解，請參閱[我擁有哪些授權？](end-user-license.md)。 報表作者可能已關閉報表的資料匯出功能。 如果無法匯出資料，請連絡報表作者。


## <a name="from-a-visual-on-a-power-bi-dashboard"></a>從 Power BI 儀表板上的視覺效果

1. 從 Power BI 儀表板上開始。 在這裡，我們使用來自 ***行銷與銷售範例** _應用程式的儀表板。 您可以[從 AppSource.com 下載此應用程式](https://appsource.microsoft.com/en-us/product/power-bi/microsoft-retail-analysis-sample.salesandmarketingsample
)。

    ![應用程式儀表板](media/end-user-export/power-bi-dashboard.png)

2. 將滑鼠暫留在視覺效果上方以顯示_ [更多選項]* (...)，然後按一下以顯示動作功能表。

    ![選取省略符號時出現的功能表](media/end-user-export/power-bi-option-menu.png)

3. 選取 [匯出至 .csv]。

4. 後續步驟取決於所正在使用的瀏覽器。 系統可能會提示儲存檔案，或您可能會在瀏覽器底部看到所匯出檔案的連結。 根據預設，您的匯出會儲存到本機的 [下載] 資料夾中。 

    ![顯示匯出檔案連結的 Chrome 瀏覽器](media/end-user-export/power-bi-dashboards-export.png)

5. 在 Excel 中開啟檔案。 

    > [!NOTE]
    > 如果您沒有資料的權限，就無法以 Excel 匯出或開啟。  

    ![Excel 中的年初迄今單位總量](media/end-user-export/power-bi-excel.png)


## <a name="from-a-visual-in-a-report"></a>從報表中的視覺效果
您可以從報表中的視覺效果將資料匯出為 .csv 或 .xlsx (Excel) 格式。 

1. 在儀表板上，選取圖格來開啟基礎報表。  在此範例中，我們選取與上方相同的視覺效果的「年初迄今單位總量差異 %」。 

    ![已醒目提示的儀表板圖格](media/end-user-export/power-bi-export-tile.png)

    因為此圖格是從「銷售與行銷範例」報表建立的，所以會開啟該報表。 而且，報表會開啟到包含所選圖格視覺效果的頁面。 

2. 在報表中選取視覺效果。 請注意右邊的 [篩選] 窗格。 此視覺效果已套用篩選。 若要深入了解篩選，請參閱[在報表中使用篩選](end-user-report-filter.md)。

    ![已選取的篩選窗格](media/end-user-export/power-bi-export-filter-pane.png)


3. 選取視覺效果右上角的 [更多選項 (...)]。 選擇 [匯出資料]。

    ![下拉式清單中已選取的 [匯出資料]](media/end-user-export/power-bi-export-reports.png)

4. 您會看到要匯出 [摘要的資料] 或 [基礎資料] 的選項。 如果您使用的是「銷售與行銷範例」應用程式，將會停用 [基礎資料]。 但是，您可能會發現已啟用兩個選項的報表。 以下是差異的說明。

    **摘要的資料**：如果您想要匯出在該視覺效果中目前所看到內容的資料，請選取此選項。  此類型匯出只會顯示用來建立視覺效果目前狀態的資料。 如果視覺效果已套用篩選，則您匯出的資料也會經過篩選。 例如，針對此視覺效果，您的匯出只會包含 2014 年和中部區域的資料，且只有四個製造商的資料：VanArsdel、Natura、Aliqui 和 Pirum。 如果視覺效果具有彙總 (加總、平均值等)，則匯出也會彙總。 
  

    **基礎資料**：如果您想要匯出視覺效果中所見的資料 **和** 來自基礎資料集的其他資料，請選取此選項。  這可能包括資料集所包含但未在視覺效果中使用的資料。 如果視覺效果已套用篩選，則您匯出的資料也會經過篩選。  如果您的視覺效果有彙總 (加總、平均值等)，則匯出將會移除彙總；基本上會將資料扁平化。 

    ![選擇基礎或摘要的功能表](media/end-user-export/power-bi-export-underlying.png)

5. 後續步驟取決於所正在使用的瀏覽器。 系統可能會提示您儲存檔案，或者您可能會在瀏覽器底部看到所匯出檔案的連結。 如果您在 Microsoft Teams 中使用 Power BI 應用程式，則匯出的檔案會儲存在本機的 [下載] 資料夾中。 

    ![在 Microsoft Edge 瀏覽器中顯示的匯出檔案](media/end-user-export/power-bi-export-edge-screen.png)

    > [!NOTE]
    > 如果您沒有資料的權限，就無法以 Excel 匯出或開啟。  


6. 在 Excel 中開啟檔案。 將資料數量與在儀表板上從相同視覺效果匯出的資料比較。 差別在於此匯出包含 **基礎資料**。 

    ![範例 Excel](media/end-user-export/power-bi-underlying.png)

## <a name="next-steps"></a>後續步驟

[顯示用來建立視覺效果的資料](end-user-show-data.md)