---
title: 將影像、影片和其他項目新增至儀表板
description: 有關如何使用 [新增磚] 小工具將影像、影片、文字方塊、Web 程式碼和資料流資料磚新增至儀表板的文件。
author: maggiesMSFT
ms.reviewer: ''
featuredvideoid: e2PD8m1Q0vU
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 10/28/2020
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: 72306a6269df91a75b750628e3534bf5891fe6b0
ms.sourcegitcommit: 4ac9447d1607dfca2e60948589f36a3d64d31cb4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2020
ms.locfileid: "92916904"
---
# <a name="add-images-videos-and-more-to-your-dashboard"></a>將影像、影片和其他項目新增至儀表板

藉由將磚新增至儀表板，您可以將影像、文字方塊、影片、串流資料或 Web 程式碼放在儀表板上。 

請觀看 Amanda 如何將磚新增至儀表板。

   
<iframe width="560" height="315" src="https://www.youtube.com/embed/e2PD8m1Q0vU" frameborder="0" allowfullscreen></iframe>


## <a name="add-an-image-video-or-other-tile"></a>新增影像、影片或其他磚
您可以直接將影像、文字方塊、影片、串流資料或 Web 程式碼新增至儀表板。

1. 從儀表板的頂端功能表列選取 [新增磚]  。 視空間限制，您可能只會看到加號 ![加號](media/service-dashboard-add-widget/power-bi-add-tile-icon-small.png)。
   
    ![新增磚圖示](media/service-dashboard-add-widget/power-bi-add-tile-icon.png)
2. 選取要加入的磚類型： 

    **[Web 內容](#add-web-content)**

    **[影像](#add-an-image)**

    **[文字方塊](#add-a-text-box-or-dashboard-heading)**

    **[影片](#add-a-video)**

    **[自訂串流資料](#add-streaming-data)**
   
    ![新增磚視窗](media/service-dashboard-add-widget/power-bi-add-tile.png)

## <a name="add-an-image"></a>加入影像
如果您想要將公司標誌或其他影像新增至儀表板，請在線上儲存影像檔並連結至該檔案。 請確定不需要安全性認證以便存取影像檔。 例如，由於 OneDrive 和 SharePoint 需要驗證，因此儲存於該處的影像無法如此這般地新增至儀表板。  

1. 從 [新增磚]  視窗中，選取 [影像]   > [下一步]  。

2. 從 [新增影像磚]  視窗中，新增影像資訊：   
   
   a. 若要在影像上方顯示標題，請選取 [顯示標題與子標題]  並輸入 [標題]  和選擇性的 [子標題]  。

   b. 輸入影像 [URL]  。

   c. 若要將標題設定為超連結，請選取 [設定自訂連結]  並輸入 [URL]  。 

      同事按一下此影像或標題時，即會前往此 URL。

   d. 選取 [套用]  。 

      ![[新增影像磚] 視窗](media/service-dashboard-add-widget/pbi-widget-add-image-new.png)

3. 在儀表板上，視需要調整影像大小和移動影像。
     
     ![儀表板上的影像](media/service-dashboard-add-widget/power-bi-add-image-dash.png)

## <a name="add-a-text-box-or-dashboard-heading"></a>新增文字方塊或儀表板標題

若要加入儀表板標題，請在文字方塊中輸入您的標題並增加字型。

1. 從 [新增磚]  視窗中，選取 [文字方塊]   > [下一步]  。

2. 設定文字方塊的格式︰
   
   a. 若要在文字方塊上方顯示標題，請選取 [顯示標題與子標題]  並輸入 [標題]  和選擇性的 [子標題]  。

   b. 輸入並格式化文字方塊的 [內容]  。  

   c. 或者設定標題的自訂連結。 自訂連結可以是外部網站或您的工作區中的儀表板或報告。 不過在此範例中，我們已在文字方塊內新增超連結，因此會將 [設定自訂連結]  保持為未選取狀態。

   d. 選取 [套用]  。 

     ![[新增文字方塊磚] 視窗](media/service-dashboard-add-widget/power-bi-add-textbox.png)
   
3. 在儀表板上，視需要調整文字方塊大小和移動文字方塊。
   
   ![具有影像與文字的儀表板](media/service-dashboard-add-widget/pbi-widget-text-added-new.png)

## <a name="add-a-video"></a>加入影片
將 YouTube 或 Vimeo 影片加入儀表板後，該影片就會直接在儀表板上播放。

1. 從 [新增磚]  視窗中，選取 [影片]   > [下一步]  。
2. 將影片資訊新增至 [新增影片磚]  視窗：   
   
   a. 若要在影片磚上方顯示標題和子標題，請選取 [顯示標題與子標題]  並輸入 [標題]  和選擇性的 [子標題]  。 在此範例中，我們會新增 [子標題]  ，然後將其轉換成整個 YouTube 播放清單的超連結。

   b. 輸入影片的 [影片 URL]  。

   c. 新增 [標題]  和 [子標題] **的超連結，讓您的同事在觀賞內嵌影片之後，可以在 YouTube 上檢視整個播放清單。** 若要這麼做，請在 [ 功能]  下，選取 [設定自訂連結]  ，然後輸入播放清單的 [URL]  。

   d. 選取 [套用]  。  

   ![[新增影片磚] 視窗](media/service-dashboard-add-widget/power-bi-add-video-new.png)

3. 在儀表板上，視需要調整影片大小和移動影片。
     
   ![新增影片磚的儀表板](media/service-dashboard-add-widget/pbi-widget-video-added-new.png)
4. 選取要播放影片的影片磚。
5. 選取移至 YouTube 播放清單的子標題。

## <a name="add-streaming-data"></a>新增串流資料
您可以使用 PubNub 將串流資料 (例如 Twitter 摘要或感應器資料) 新增至儀表板中的磚。 Power BI 已建立整合，以便從 PubNub 取得資料。 在這裡，將說明其運作方式。
   

<iframe width="560" height="315" src="https://www.youtube.com/embed/kOuINwgkEkQ" frameborder="0" allowfullscreen></iframe>

1. 從 [新增磚]  視窗中，選取 [自訂串流資料]   > [下一步]  。
2. 選取 [新增串流資料集]  。
3. 使用 Power BI API 或 PubNub 建立 [新增串流資料集]  。
4. 填入 [資料集名稱]  、[訂用帳戶金鑰]  和 [頻道名稱]  的欄位。 如果它是安全連線，則還會有授權金鑰。 您可以使用 PubNub 中的範例值來進行試用。
5. 選取 [下一步]  。
    您會在資料集中看到可用的欄位，以及其資料類型和 JSON 格式。
6. 選取 [連接]  。
    您已建立串流資料集。
7. 返回儀表板，然後再次選取 [新增磚]   > [自訂串流資料]   > [下一步]  。
8. 選取您建立的感應器資料資料集 > [下一步]  。
9. 選取您想要的視覺效果類型。 折線圖通常適用於此資料。
10. 選取 [軸]  、[圖例]  和 [值]  。
11. 決定您想要顯示的時間量，以秒、分鐘或小時為單位。
12. 選取 [下一步]  。
13. 如有需要，請為其提供 [標題]  和 [子標題]  。
14. 將其釘選到您的儀表板。


1. 從 [新增磚]  視窗中，選取 [自訂串流資料]   > [下一步]  。

2. 選取 [新增串流資料集]  。

3. 使用 Power BI API 或 PubNub 建立 [新增串流資料集]  。

4. 填入 [資料集名稱]  、[訂用帳戶金鑰]  和 [頻道名稱]  的欄位。 如果它是安全連線，則還會有授權金鑰。 您可以使用 PubNub 中的範例值來進行試用。

5. 選取 [下一步]  。

   您會在資料集中看到可用的欄位，以及其資料類型和 JSON 格式。

6. 選取 [連接]  。

   您已建立串流資料集。

7. 返回儀表板，然後再次選取 [新增磚]   > [自訂串流資料]   > [下一步]  。

8. 選取您建立的感應器資料資料集 > [下一步]  。

9. 選取您想要的視覺效果類型。 折線圖通常適用於此資料。

10. 選取 [軸]  、[圖例]  和 [值]  。

11. 決定您想要顯示的時間量，以秒、分鐘或小時為單位。

12. 選取 [下一步]  。

13. 選擇性地為其提供 [標題]  和 [子標題]  。

14. 將其釘選到您的儀表板。

## <a name="add-web-content"></a>加入 Web 內容
您可以在報表或儀表板中，貼上或鍵入作為磚的任何 HTML 內容。 請以手動方式輸入內嵌程式碼，或從 Twitter、YouTube、embed.ly 等網站複製/貼上。

1. 從 [新增磚]  視窗中，選取 [Web 內容]   > [下一步]  。

2. 將資訊新增至 [新增 Web 內容磚]  視窗：
   
   a. 若要在磚上方顯示標題，請選取 [顯示標題與子標題]  並輸入 [標題]  和選擇性的 [子標題]  。

   b. 輸入內嵌程式碼。 我們在這個範例會複製並貼上 Twitter 摘要。

   c. 選取 [套用]  。

   ![[新增 Web 內容磚] 視窗](media/service-dashboard-add-widget/power-bi-add-web-content.png)
   

3. 在儀表板上，視需要調整 Web 內容大小和移動 Web 內容。
     
   ![含有四個磚的儀表板](media/service-dashboard-add-widget/pbi-widget-code-added-new.png)

### <a name="tips-for-embedding-web-content"></a>內嵌 Web 內容的提示
* 若為 Iframe，請使用安全的來源。 如果您輸入 Iframe 內嵌程式碼並取得空白磚，則請確認 Iframe 來源未使用 *http* 。 如果使用的話，請將其變更為 *https* 。
  
  ```html
  <iframe src="https://xyz.com">
  ```
* 編輯寬度和高度資訊。 這個內嵌程式碼會內嵌影片，並將影片播放程式設定為 560 x 315 個像素。 當您調整磚大小時，這個大小不會變更。
  
  ```html
  <iframe width="560" height="315"
  src="https://www.youtube.com/embed/Cle_rKBpZ28" frameborder="0"
   allowfullscreen></iframe>
  ```
  
  如果您希望播放程式調整大小以符合磚大小、請將寬度和高度設為 100%。
  
  ```html
  <iframe width="100%" height="100%"
  src="https://www.youtube.com/embed/Cle_rKBpZ28" frameborder="0"
   allowfullscreen></iframe>
  ```
* 這個程式碼會內嵌推文，並以個別連結的方式在儀表板上保留 AFK 播客、\@GuyInACube 的 Twitter 網頁、關注、#analytics、回覆、轉推和讚的連結。  選取圖格本身會帶您前往 Twitter 的播客。
  
  ```html
  <blockquote class="twitter-tweet" data-partner="tweetdeck">
  <p lang="en" dir="ltr">Listen to
  <a href="https://twitter.com/GuyInACube">@GuyInACube</a> talk to
  us about making videos about Microsoft Business Intelligence
  platform
  <a href="https://t.co/TmRgalz7tv">https://t.co/TmRgalz7tv </a>
  <a href="https://twitter.com/hashtag/analytics?src=hash">
  #analytics</a></p>&mdash; AFTK Podcast (@aftkpodcast) <a
  href="https://twitter.com/aftkpodcast/status/693465456531771392">
  January 30, 2016</a></blockquote> <script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>
  ```

## <a name="edit-a-tile"></a>編輯磚
若要對現有的磚進行變更：

1. 將滑鼠暫留在磚右上角並選取 [更多選項]  (...)。
   
    ![選取磚省略符號](media/service-dashboard-add-widget/pbi_ellipses.png)
2. 選取 [編輯詳細資料]  ，以顯示 [磚詳細資料]  視窗並進行變更。
   
    ![編輯詳細資料](media/service-dashboard-add-widget/pbi-edit.png)

## <a name="considerations-and-troubleshooting"></a>考量與疑難排解
* 若想要更輕鬆地在儀表板上移動磚，請新增標題和選擇性的子標題。
* 如果想要內嵌網站的內容，但網站未提供可供複製及貼上的內嵌程式碼，請參閱 embed.ly 以取得產生內嵌程式碼的協助。
* 請確定不需要安全性認證以便存取影像檔。 例如，由於 OneDrive 和 SharePoint 需要驗證，因此儲存於該處的影像無法如此這般地新增至儀表板。  

## <a name="next-steps"></a>後續步驟
[Power BI 設計工具的儀表板磚簡介](service-dashboard-tiles.md)

有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)。

