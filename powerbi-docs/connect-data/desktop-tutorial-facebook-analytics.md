---
title: 教學課程：使用 Power BI Desktop 來分析 Facebook 資料
description: 您將了解如何從 Facebook 匯入資料，並用於 Power BI Desktop。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: tutorial
ms.date: 05/06/2020
LocalizationGroup: Learn more
ms.openlocfilehash: c138b5d3b03b360ee1f83c57a98906b5fec25d6e
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410957"
---
# <a name="tutorial-analyze-facebook-data-by-using-power-bi-desktop"></a>教學課程：使用 Power BI Desktop 來分析 Facebook 資料

在本教學課程中，您將了解如何從 Facebook 匯入資料，並用於 Power BI Desktop。 您將連線 Power BI Facebook 頁面並從中匯入資料、將轉換套用至匯入的資料，然後在報表視覺效果中使用資料。

> [!WARNING]
> 由於 Facebook 應用程式權限限制，此文章中所述的連接器功能目前無法正常運作。 我們正與 Facebook 合作，以盡快恢復此功能。


## <a name="connect-to-a-facebook-page"></a>連線至 Facebook 頁面

本教學課程使用來自 [Microsoft Power BI Facebook 頁面](https://www.facebook.com/microsoftbi)的資料。 除了個人的 Facebook 帳戶之外，您不需要任何特殊認證就能連線此頁面並匯入資料。

1. 開啟 Power BI Desktop，接著在 [開始使用]  對話方塊中選取 [取得資料]  ，或在 [首頁]  功能區索引標籤中選取 [取得資料]  ，然後選取 [更多]  。
   
2. 在 [取得資料]  對話方塊中，從 [線上服務]  群組選取 [Facebook]  ，然後選取 [連線]  。
   
   ![取得資料](media/desktop-tutorial-facebook-analytics/t_fb_getdataother.png)
   
   對話方塊隨即出現，提醒您使用第三方服務的風險。
   
   ![第三方服務警告](media/desktop-tutorial-facebook-analytics/t_fb_connectingtotps.png)
   
3. 選取 [繼續]  。 
   
4. 在 [Facebook]  文字方塊中輸入名稱 **microsoftbi** 作為 **使用者名稱**，從 [連線]  下拉式清單中選取 [貼文]  ，然後選取 [確定]  。
   
   ![連線](media/desktop-tutorial-facebook-analytics/2.png)
   
5. 當提示輸入認證時，請登入 Facebook 帳戶，並允許 Power BI 存取您的帳戶。
   
   ![認證](media/desktop-tutorial-facebook-analytics/facebookcredentials.png)

   連線到 Power BI Facebook 頁面之後，您就會看見頁面貼文資料的預覽。 
   
   ![資料預覽](media/desktop-tutorial-facebook-analytics/t_fb_1-loadpreview.png)
   
## <a name="shape-and-transform-the-imported-data"></a>使匯入的資料成形和轉換

假設您想要查看並顯示一段時間內具有最多留言的貼文，但您注意到在貼文資料預覽中，**created_time** 資料難以閱讀和理解，且完全沒有任何留言資料。 若要充分利用資料，您需要執行某種資料成形和清理作業。 若要執行此操作，請使用 Power BI Desktop 的 Power Query 編輯器，在將資料匯入 Power BI Desktop 之前或之後加以編輯。 

### <a name="split-the-datetime-column"></a>分割日期/時間資料行

首先，分隔 **created_time** 資料行中的日期和時間值，使其更容易閱讀。 

1. 在 Facebook 資料預覽中，選取 [編輯]  。 
   
   ![資料預覽編輯](media/desktop-tutorial-facebook-analytics/t_fb_1-editpreview.png)
   
   Power BI Desktop 的 Power Query 編輯器會在新視窗中開啟，並顯示來自 Power BI Facebook 頁面的資料預覽。 
   
   ![Power Query 編輯器](media/desktop-tutorial-facebook-analytics/t_fb_1-intoqueryeditor.png)
   
2. 選取 **created_time** 資料行。 請注意，該資料行是 **文字** 資料類型，在資料行標頭中會以 **ABC** 圖示來表示。 以右鍵按一下標頭，並在下拉式清單中選取 [分割資料行]   > [依分隔符號]  。 或者，您也可以在功能區 [首頁]  索引標籤的 [轉換]  群組下方，選取 [分割資料行]   > [依分隔符號]  。  
   
   ![依分隔符號分割資料行](media/desktop-tutorial-facebook-analytics/delimiter1.png)
   
3. 在 [依分隔符號分割資料行]  對話方塊中，從下拉式清單中選取 [自訂]  、在輸入欄位中輸入 **T** (作為 **created_time** 值時間部分開頭的字元)，然後選取 [確定]  。 
   
   ![[依分隔符號分割資料行] 對話方塊](media/desktop-tutorial-facebook-analytics/delimiter2.png)
   
   該資料行會分割成兩個資料行，各自包含 *T* 分隔符號前後的字串。 新資料行分別命名為 **created_time.1** 和 **created_time.2**。 Power BI 已自動偵測到並將第一個資料行的資料類型變更為 **Date**，以及將第二個資料行變更為 **Time**，且已將日期和時間值格式化，使其更容易閱讀。
   
4. 重新命名這兩個資料行。 選取 **created_time.1** 資料行，然後從功能區 [轉換]  索引標籤的 [任何資料行]  群組中選取 [重新命名]  。 或者，您也可以按兩下資料行標頭並輸入新的資料行名稱 **created_date**。 為 **created_time.2** 重複執行此操作，並將其命名為 **created_time**。
   
   ![新的日期和時間資料行](media/desktop-tutorial-facebook-analytics/delimiter3.png)
   
### <a name="expand-the-nested-column"></a>展開巢狀資料行

日期和時間資料現在會以您想要的方式呈現，只要展開巢狀資料行即可公開留言資料。 

1. 選取 **object_link** 資料行頂端的 ![展開圖示](media/desktop-tutorial-facebook-analytics/14.png) 圖示，以開啟 [展開/彙總]  對話方塊。 選取 [connections]  \(連接\)，然後選取 [確定]  。 
   
   ![展開 object_link](media/desktop-tutorial-facebook-analytics/expand1.png)
   
   資料行標題會變更為 **object_link.connections**。
2. 選取 **object_link.connections** 資料行上方的 ![展開圖示](media/desktop-tutorial-facebook-analytics/14.png)圖示、然後依序選取 [留言]  和 [確定]  。 資料行標題會變更為 **object_link.connections.comments**。
   
3. 選取 **object_link.connections.comments** 資料行上方的 ![展開圖示](media/desktop-tutorial-facebook-analytics/14.png) 圖示，但這次在對話方塊中選取 [彙總]  而不是 [展開]  。 選取 [# id 的計數]  ，然後選取 [確定]  。 
   
   ![彙總留言](media/desktop-tutorial-facebook-analytics/expand2.png)
   
   資料行現在會顯示每個訊息的留言數目。 
   
4. 將 **object_link.connections.comments.id 的計數** 資料行重新命名為 **Number of comments** \(留言數目\)。
   
5. 選取 [Number of comments] \(留言數目\)  資料行標頭旁的向下箭號，然後選取 [遞減排序]  以查看已排序的貼文 (從最多留言數目到最少留言數目)。 
   
   ![每個訊息的留言](media/desktop-tutorial-facebook-analytics/data-fixed.png)
   
### <a name="review-query-steps"></a>檢閱查詢步驟

當您在 Power Query 編輯器中使資料成形並轉換時，每個步驟都會記錄於 [Power Query 編輯器]  視窗右側 [查詢設定]  窗格的 [套用的步驟]  區域中。 您可以反向逐步執行 [套用的步驟]  來查看所做變更，並視需要編輯、刪除或重新排列這些步驟。 修改這些步驟時請小心，因為變更先前的步驟可能會中斷後續步驟。 

套用到目前為止的資料轉換之後，[套用的步驟]  看起來應該如下：
   
   ![套用的步驟](media/desktop-tutorial-facebook-analytics/applied-steps.png)
   
   >[!TIP]
   >[套用的步驟]  本質上是以 [Power Query M 公式語言](/powerquery-m/quick-tour-of-the-power-query-m-formula-language)所撰寫的公式。 若要查看和編輯公式，請在功能區 [常用]  索引標籤的 [查詢]  群組中選取 [進階編輯器]  。 

### <a name="import-the-transformed-data"></a>匯入轉換的資料

當您處理完資料之後，請在功能區的 [首頁]  索引標籤中選取 [關閉並套用]   > [關閉並套用]  ，以將資料匯入至 Power BI Desktop。 
   
   ![關閉並套用](media/desktop-tutorial-facebook-analytics/t_fb_1-loadandclose.png)
   
   對話方塊會顯示將資料載入至 Power BI Desktop 資料模型的進度。 
   
   ![正在載入資料](media/desktop-tutorial-facebook-analytics/t_fb_1-loading.png)
   
   載入資料之後，資料會在 [報表]  檢視中顯示為 [欄位]  窗格中的新查詢。
   
   ![螢幕擷取畫面，其中顯示稱為 Query1 的查詢其可用欄位。](media/desktop-tutorial-facebook-analytics/fb-newquery.png)
   
## <a name="use-the-data-in-report-visualizations"></a>在報表視覺效果中使用資料 

現在您已從 Facebook 頁面匯入資料，便可以使用視覺效果，快速且輕鬆地深入解析您的資料。 建立視覺效果很簡單，只要選取一個欄位，或將欄位從 [欄位]  清單拖曳至報表畫布即可。

### <a name="create-a-bar-chart"></a>建立橫條圖

1. 在 Power BI Desktop [報表]  檢視中，從 [欄位]  窗格選取 [訊息]  ，或將其拖曳至報表畫布。 畫布上會出現一個顯示所有貼文訊息的資料表。 
   
   ![顯示 [報表] 檢視的螢幕擷取畫面，其中包含訊息清單。](media/desktop-tutorial-facebook-analytics/table-viz.png)
   
2. 選取該資料表之後，也請選取 [欄位]  窗格中的 [Number of comments] \(留言數目\)  ，或將其拖曳到資料表。 
   
3. 在 [視覺效果]  窗格中，選取 **堆疊橫條圖** 圖示。 資料表會變更為橫條圖，並顯示每個貼文的留言數目。 
   
   ![橫條圖](media/desktop-tutorial-facebook-analytics/barchart1.png)
   
4. 選取視覺效果旁邊的 [更多選項]  (...)，然後選取 [排序依據]   > [Number of comments] \(留言數目\)  ，以便依遞減的留言數來排序資料表。 

   請注意，大部分留言都會與 **(空白)** 訊息建立關聯 (這些貼文可能是故事、連結、影片或其他非文字內容)。 
   
5. 若要篩選出空白列，請從 [篩選]  窗格選取 [訊息是 (全部)]  、選取 [全選]  ，然後選取 [(空白)]  以將其取消選取。 

   [篩選]  項目會變更為 [訊息不是 (空白)]  ，而 **(空白)** 列會從圖表視覺效果中消失。
   
   ![篩選出空白列](media/desktop-tutorial-facebook-analytics/barchart3.png)
   
### <a name="format-the-chart"></a>將資料表格式化

視覺效果變得越來越有趣了，但您在圖表中看不到大部分貼文內容。 顯示更多貼文內容：

1. 使用圖表視覺效果的控點，盡可能將圖表大小調整到最大。 
   
2. 選取圖表後，選取 [視覺效果]  窗格中的 **格式** 圖示 (滾筒刷)。
   
3. 選取 **Y 軸** 旁的向下箭號，然後將 [最大容量]  滑桿拖曳到最右邊 (**50%** )。 
4. 將 [文字大小]  降至 **10 pt** 以容納更多文字。
   
   ![格式變更](media/desktop-tutorial-facebook-analytics/barchart4.png)
   
   圖表現在會顯示更多貼文內容。 
   
   ![顯示更多貼文](media/desktop-tutorial-facebook-analytics/barchart5.png)
   
圖表的 X 軸 (留言數目) 不會顯示實際值，且看不到圖表底部。 讓我們改用資料標籤： 

1. 選取 **格式** 圖示，然後將 **X 軸** 旁的滑桿設為 [關閉]  。 
   
2. 將 [資料標籤]  滑桿設為 [開啟]  。 

   現在圖表會顯示每個貼文的確切留言數目。
   
   ![套用資料標籤](media/desktop-tutorial-facebook-analytics/barchart6.png)
   
### <a name="edit-the-data-type"></a>編輯資料類型

看起來好多了，但資料標籤全都有 **.0** 小數位數，這可能會造成失焦與誤解，因為 [貼文數目]  必須是整數。 若要修正這個問題，您需要將 [貼文數目]  資料行的資料類型變更為 **整數**：

1. 以滑鼠右鍵按一下 [欄位]  窗格中的 [Query1]  (或將滑鼠暫留在其上方)，然後選取 [更多選項]  (...)。 

2. 從操作功能表中，選取 [編輯查詢]  。 或者，從功能區 [首頁]  索引標籤的 [外部資料]  群組中，選取 [編輯查詢]   > [編輯查詢]  。 
   
3. 從 [Power Query 編輯器]  視窗中選取 [Number of comments] \(留言數目\)  資料行，並遵循下列其中一個步驟來變更資料類型： 
   - 選取 [Number of comments] \(留言數目\)  資料行標頭旁的 **1.2** 圖示，然後從下拉式清單中選取 [整數] 
   - 以滑鼠右鍵按一下資料行標頭，然後選取 [變更類型]   > [整數]  。
   - 選取 [資料類型：  十進位數字] (在 [首頁]  索引標籤的 [轉換]  群組中，或 [轉換]  索引標籤的 [任何資料行]  群組中)，然後選取 [整數]  。
   
   資料行標頭中的圖示會變更為 **123**，其表示 **整數** 資料類型。
   
   ![變更資料類型](media/desktop-tutorial-facebook-analytics/change-datatype.png)
   
3. 若要套用變更，請選取 [檔案]   > [關閉並套用]  (或 [檔案]   > [套用]  ) 以讓 [Power Query 編輯器]  視窗保持開啟。 

   載入變更之後，圖表上的資料標籤就會變成整數。
   
   ![具有整數的圖表](media/desktop-tutorial-facebook-analytics/vis-3.png)
   
### <a name="create-a-date-slicer"></a>建立日期交叉分析篩選器

假設您想要以視覺化方式顯示貼文一段時間內的留言數目。 您可以建立交叉分析篩選器視覺效果，以篩選不同時間範圍的圖表資料。 

1. 選取畫布的空白區域，然後選取 [視覺效果]  窗格中的 **交叉分析篩選器** 圖示。 

   空白的交叉分析篩選器視覺效果隨即出現。
   
   ![選取交叉分析篩選器圖示](media/desktop-tutorial-facebook-analytics/slicer1.png)
   
2. 從 [欄位]  窗格選取 **created_date** 欄位，或將其拖曳到新的交叉分析篩選器。 

   交叉分析篩選器會根據欄位的 **日期** 資料類型而變更為日期範圍滑桿。
   
   ![日期範圍滑桿交叉分析篩選器](media/desktop-tutorial-facebook-analytics/slicer2.png)
   
3. 移動滑桿控點來選取不同的日期範圍，並注意圖表資料如何據以篩選。 您也可以選取交叉分析篩選器中的日期欄位並輸入特定日期，或從快顯行事曆中來選擇。
    
   ![進行資料配量](media/desktop-tutorial-facebook-analytics/slicer3.png)
   
### <a name="format-the-visualizations"></a>將視覺效果格式化

為圖表提供更清楚且更吸引人的標題： 

1. 選取圖表後，請選取 [視覺效果]  窗格中的 **格式** 圖示，然後選取 **標題** 旁的下拉式箭號以將其展開。

2. 將 [標題文字]  變更為 **Comments per post** \(每篇貼文的留言\)。 

3. 選取 [字型色彩]  旁的下拉式箭號，然後選取綠色以搭配視覺效果的綠色列。

4. 將 [文字大小]  增加到 **10 pt**，並將 [字型家族]  變更為 **Segoe (Bold)** 。

5. 嘗試使用其他格式化選項和設定，以變更視覺效果的外觀。 

   ![視覺效果](media/desktop-tutorial-facebook-analytics/vis-1.png)

## <a name="create-more-visualizations"></a>建立更多視覺效果

如您所見，很容易就能自訂報表中的視覺效果，以便依您想要的方式來呈現資料。 例如，嘗試使用匯入的 Facebook 資料來建立此折線圖，以顯示一段時間內留言數目。

![折線圖](media/desktop-tutorial-facebook-analytics/moreviz.png)

Power BI Desktop 提供從頭到尾流暢的體驗，包括從各種資料來源取得資料、讓資料成形以符合您的分析需求，乃至於以豐富且互動的方式將此資料視覺化。 準備好報表之後，您可以[將其上傳至 Power BI 服務](../create-reports/desktop-upload-desktop-files.md)並依此建立儀表板，並與其他 Power BI 使用者共用。

## <a name="next-steps"></a>後續步驟
* [Microsoft Learn for Power BI](/learn/powerplatform/power-bi?WT.mc_id=powerbi_landingpage-docs-link)
* [瀏覽 Power BI 論壇](https://go.microsoft.com/fwlink/?LinkID=519326)
* [閱讀 Power BI 部落格](https://go.microsoft.com/fwlink/?LinkID=519327)