---
title: Power BI Desktop 中的查詢概觀
description: Power BI Desktop 中的查詢概觀
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: conceptual
ms.date: 01/11/2020
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 9202b94808624ca9e3332ba7acdca29a3ce759ca
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96413980"
---
# <a name="query-overview-in-power-bi-desktop"></a>Power BI Desktop 中的查詢概觀
透過 Power BI Desktop，您可以連接到資料世界、建立具吸引力的基礎報表，並與他人分享您的成果；其他使用者可接著以您的成果做為建置基礎，並擴展其商務智慧成果。

Power BI Desktop 包含三種檢視：

* **報表** 檢視 - 您可以在此利用所建立的查詢，建立多頁具吸引力的視覺效果，並依您想要顯示的方式進行排列，以與他人共用
* **資料** 檢視 - 以資料模型格式檢視報表中的資料，您可以在此加入量值、建立新的資料行及管理關聯性
* **關聯性** 檢視 - 以圖形表示資料模型中已建立的關聯性，並視需要進行管理或修改。

選取 Power BI Desktop 左側三個圖示的其中一個以存取這些檢視。 在下圖中，會選取 [報表] 檢視，並以圖示旁的黃色寬線表示。  

![Power BI Desktop 的螢幕擷取畫面，其中顯示已選取的 [報表] 檢視。](media/desktop-query-overview/queryoverview_viewicons.png)
 
Power BI Desktop 也隨附 Power Query 編輯器。 使用 Power Query 編輯器來連接到一或多個資料來源、依您的需求成形和轉換資料，然後將該模型載入 Power BI Desktop。

本文概述 Power Query 編輯器中的資料工作，但您可以深入了解。 在本文結尾，您將找到有關支援資料類型的詳細指導。 您也將找到有關連接到資料、資料成形、建立關聯性及如何開始使用的指導。

但首先，讓我們來認識 Power Query 編輯器。

## <a name="power-query-editor"></a>Power Query 編輯器
若要移至 Power Query 編輯器，請從 Power BI Desktop 的 [首頁] 索引標籤選取 [編輯查詢]。  

![Power B I Desktop 的螢幕擷取畫面，其中顯示 Power Query 編輯器 [首頁] 索引標籤。](media/desktop-query-overview/queryoverview_queryview.png)

在沒有資料連線的情況下，Power Query 編輯器看起來就像是準備填入資料的空白窗格。  

![Power B I Desktop 的螢幕擷取畫面，其中顯示沒有任何資料連線的 Power Query 編輯器。](media/desktop-query-overview/queryoverview_blankpane.png)

載入查詢之後，Power Query 編輯器檢視會變得更有趣。 如果我們連接到下列 Web 資料來源，Power Query 編輯器會載入該資料的相關資訊，然後您可以開始將此資料成形：

[*https://www.bankrate.com/retirement/best-and-worst-states-for-retirement/*](https://www.bankrate.com/retirement/best-and-worst-states-for-retirement/)

以下是建立資料連線之後所顯示的 Power Query 編輯器：

1. 在功能區中，現在有許多按鈕可以與查詢中的資料互動。
2. 在左窗格中，會列出查詢以供選取、檢視及成形。
3. 在中央窗格中，會顯示所選查詢的資料以供成形。
4. [查詢設定] 窗格隨即顯示，其列出查詢的屬性和所套用驟。  
   
   ![Power B I Desktop 的螢幕擷取畫面，其中顯示 Power Query 編輯器中的 [查詢設定] 窗格。](media/desktop-query-overview/queryoverview_withdataconnection.png)

我們將分別討論這四個區域：功能區、[查詢] 窗格、[資料] 檢視和 [查詢設定] 窗格。

## <a name="the-query-ribbon"></a>查詢功能區
Power Query 編輯器中的功能區是由四個索引標籤組成：[首頁]、[轉換]、[新增資料行] 和 [檢視]。

[首頁] 索引標籤包含常見的查詢工作。

![Power B I Desktop 的螢幕擷取畫面，其中顯示 Power Query 編輯器的 [查詢] 功能區。](media/desktop-query-overview/queryoverview_ribbon.png)

若要連接到資料並開始查詢建立程序，請選取 [新增來源]。 此時會出現一個功能表，提供最常見的資料來源。  

![Power B I Desktop 的螢幕擷取畫面，其中顯示 [新增來源] 按鈕。](media/desktop-query-overview/query-overview-new-source-menu.png)

如需可用資料來源的詳細資訊，請參閱＜資料來源＞ 。 如需連接到資料的相關資訊，包括範例和步驟，請參閱＜連接到資料＞ 。

[轉換]  索引標籤可存取常見的資料轉換工作，例如：

* 新增或移除資料行
* 變更資料類型 
* 分割資料行 
* 其他資料驅動工作

![Power B I Desktop 的螢幕擷取畫面，其中顯示 [首頁] 索引標籤。](media/desktop-query-overview/queryoverview_transformribbon.png)

如需轉換資料的詳細資訊，包括範例，請參閱[教學課程：在 Power BI Desktop 中將資料成形及合併](../connect-data/desktop-shape-and-combine-data.md)。

[加入資料行]  索引標籤提供與加入資料行、格式化資料行資料及加入自訂資料行相關聯的其他工作。 下圖顯示 [加入資料行]  索引標籤。  

![Power B I Desktop 的螢幕擷取畫面，其中顯示 [新增資料行] 索引標籤。](media/desktop-query-overview/queryoverview_addcolumnribbon.png)

功能區上的 [檢視]  索引標籤可用來切換是否顯示特定窗格或視窗。 此索引標籤可用來顯示 [進階編輯器]。 下圖顯示 [檢視]  索引標籤。  

![Power B I Desktop 的螢幕擷取畫面，其中顯示 [檢視] 索引標籤。](media/desktop-query-overview/queryoverview_viewribbon.png)

請注意，您也可以在中央窗格中，以滑鼠右鍵按一下資料行或其他資料來執行功能區所提供的許多工作。

## <a name="the-left-queries-pane"></a>左窗格 (查詢)
左窗格 (或 [查詢] 窗格) 顯示作用中的查詢數目及查詢名稱。 當您從左窗格選取查詢時，其資料會顯示在中央窗格中，您可以在此將資料成形及轉換，以符合您的需求。 下圖顯示內含查詢的左窗格。  

![Power B I Desktop 的螢幕擷取畫面，其中顯示左側窗格中的 [查詢]。](media/desktop-query-overview/queryoverview_theleftpane.png)

## <a name="the-center-data-pane"></a>中央窗格 (資料)
在中央窗格 (或 [資料] 窗格) 中，會顯示所選查詢的資料。 此窗格是完成 [查詢] 檢視中大部分工作的位置。

下圖顯示先前建立的 Web 資料連線。 已選取 [產品] 資料行，當以滑鼠右鍵按一下其標頭時，會顯示可用的功能表項目。 請注意，許多快顯功能表項目與功能區索引標籤中的按鈕相同。  

![Power B I Desktop 的螢幕擷取畫面，其中顯示中間窗格中的 [資料]。](media/desktop-query-overview/queryoverview_thecenterpane.png)

當您選取右鍵功能表項目 (或功能區按鈕) 時，查詢會將步驟套用至資料。 也會將步驟儲存為查詢本身的一部分。 如下一節所述，這些步驟會循序記錄到 [查詢設定]  窗格中。  

## <a name="the-right-query-settings-pane"></a>右窗格 (查詢設定)
右窗格 (或 [查詢設定] 窗格) 是顯示與查詢建立關聯所有步驟的位置。 例如，在下圖中，[查詢設定]  窗格的 [套用的步驟]  區段會反映剛才已變更 [整體分數]  資料行類型的真實情況。

![Power B I Desktop 的螢幕擷取畫面，其中顯示右測窗格中的 [查詢設定]。](media/desktop-query-overview/queryoverview_querysettingspane.png)

當額外的成形步驟套用至查詢時，即會從 [套用的步驟] 區段中擷取這些步驟。

請務必了解基礎資料「不會」改變。 相反地，Power Query 編輯器會對其資料檢視進行調整和成形。 其也會對根據 Power Query 編輯器中已成形和已修改基礎資料檢視所發生的任何資料互動檢視來進行成形和調整。

在 [查詢設定]  窗格中，您可以視需要重新命名步驟、刪除步驟或重新排序步驟。 若要執行這項操作，請以滑鼠右鍵按一下 [套用的步驟]  區段中的步驟，然後從出現的功能表中進行選擇。 所有查詢步驟會依其在 [套用的步驟] 窗格中出現的順序來執行。

![Power B I Desktop 的螢幕擷取畫面，其中顯示 [查詢設定] 屬性和 [套用的步驟] 篩選。](media/desktop-query-overview/queryoverview_querysettings_rename.png)

## <a name="advanced-editor"></a>進階編輯器
[進階編輯器] 可讓您查看 Power Query 編輯器透過每個步驟所建立的程式碼。 也可讓您建立自己的成形程式碼。 若要啟動 [進階編輯器]，請從功能區選取 [檢視]  ，然後選取 [進階編輯器] 。 此時會出現一個視窗，並顯示現有的查詢程式碼。  
![Power B I Desktop 的螢幕擷取畫面，其中顯示 [進階編輯器] 對話方塊。](media/desktop-query-overview/queryoverview_advancededitor.png)

您可以在 [進階編輯器]  視窗中直接編輯程式碼。 若要關閉視窗，請選取 [完成]  或 [取消]  按鈕。  

## <a name="saving-your-work"></a>儲存您的工作
當查詢符合需求時，請從 Power Query 編輯器的 [檔案] 功能表選取 [關閉並套用]。 此動作會套用變更並關閉編輯器。  
![Power B I Desktop 的螢幕擷取畫面，其中顯示 [檔案] 索引標籤下的 [關閉並套用] 選項。](media/desktop-query-overview/queryoverview_closenload.png)

進行時，Power BI Desktop 會提供一個顯示其狀態的對話方塊。  
![Power B I Desktop 的螢幕擷取畫面，其中顯示 [套用的查詢變更] 確認對話方塊。](media/desktop-query-overview/queryoverview_loading.png)

當準備好時，Power BI Desktop 可以將您的工作儲存為 *.pbix* 檔案格式。

若要儲存您的工作，請選取 [檔案] \> [儲存] (或 [檔案] \> [另存新檔])，如下圖所示。  
![Power B I Desktop 的螢幕擷取畫面，其中顯示 Power Query 編輯器 [檔案] 索引標籤。](media/desktop-query-overview/queryoverview_savework.png)

## <a name="next-steps"></a>後續步驟
您可以使用 Power BI Desktop 執行各種作業。 如需有關其功能的詳細資訊，請參閱下列資源：

* [Power BI Desktop 是什麼？](../fundamentals/desktop-what-is-desktop.md)
* [Power BI Desktop 中的資料來源](../connect-data/desktop-data-sources.md)
* [在 Power BI Desktop 中連線至資料](../connect-data/desktop-connect-to-data.md)
* [教學課程：在 Power BI Desktop 中將資料成形及合併](../connect-data/desktop-shape-and-combine-data.md)
* [在 Power BI Desktop 中執行常見查詢工作](desktop-common-query-tasks.md)