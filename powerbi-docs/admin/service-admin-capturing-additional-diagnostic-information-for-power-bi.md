---
title: 取得支援的診斷資訊
description: 從 Power BI 服務手動收集診斷資訊的指示。 將此資訊傳送給支援人員，以協助進行疑難排解。
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 01/21/2021
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 59e434d571c5b8d10c944bc385fb4e18ed89963c
ms.sourcegitcommit: 84f0e7f31e62cae3bea2dcf2d62c2f023cc2d404
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2021
ms.locfileid: "98781195"
---
# <a name="capture-diagnostic-information-from-the-power-bi-service"></a>從 Power BI 服務捕捉診斷資訊

在您聯繫 Microsoft 支援服務以取得有關 Power BI 服務的問題，您可以收集可協助我們解決問題的檔案。 建議您從瀏覽器會話取得瀏覽器追蹤。 瀏覽器追蹤是一個診斷檔案，可在發生問題時提供 Power BI 服務中所發生內容的重要詳細資料。

Power BI 系統管理員可以使用 [Power Platform 系統管理中心](https://admin.powerplatform.microsoft.com/)中的 [說明 **+ 支援**] 體驗來取得自助解決方案，以及聯繫支援人員。 您使用下列步驟收集的診斷檔案可以附加至您的支援要求，以協助進行疑難排解。 如需更多支援選項，請參閱 [Power BI 支援選項](service-support-options.md)。

若要收集瀏覽器追蹤和其他會話資訊，請依照下列步驟進行您所使用的瀏覽器。

## <a name="collect-a-browser-trace"></a>收集瀏覽器追蹤

> [!IMPORTANT]
>無論您使用何種瀏覽器，都必須先登入 [Power BI 服務](https://app.powerbi.com)*再* 開始收集瀏覽器追蹤資訊。 此步驟很重要，可確保追蹤資訊不會包含與您的登入相關的敏感性資訊。

#### <a name="google-chrome-or-microsoft-edge"></a>[Google Chrome 或 Microsoft Edge](#tab/google-chrome-or-microsoft-edge)

Google Chrome 和 Microsoft Edge (Chromium) 都是以 [Chromium 開放原始碼專案](https://www.chromium.org/Home)為基礎。 下列步驟示範如何使用在兩個瀏覽器中類似的開發人員工具。 如需詳細資訊，請參閱 [Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools) 和 [Microsoft Edge (Chromium) 開發人員工具](/microsoft-edge/devtools-guide-chromium)。

1. 登入之後，請在鍵盤上按 F12 鍵。 或者，在 Microsoft Edge 選取 **設定及更多 ( ... )**  >  **其他工具**  >  **開發人員工具**。 在 Google Chrome 中，選取 [ **自訂和控制 Google chrome** :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/chromium-icon-settings.png" alt-text="google chrome 設定] 功能表。" border="false"::: > **其他工具**  > **開發人員工具**。
1. 藉由設定追蹤選項，準備收集瀏覽器追蹤。 您也將停止並清除在開始重現問題之前所收集到的任何資訊。 根據預設，瀏覽器只會保留目前載入頁面的追蹤資訊。 請遵循下列步驟來設定瀏覽器，以保留所有的追蹤資訊，即使您的重現移至多個頁面也一樣：
    1. 在 [ **開發人員工具** ] 視窗中，選取 [ **網路** ] 索引標籤。然後選取 [ **保留記錄**]。
    
       :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-preserve-log.png" alt-text="開發人員工具 [網路] 索引標籤，並保留已選取的記錄檔。" :::

     2. 選取 [**主控台**] 索引標籤，然後選取 [**設定**  >  **保留記錄** 檔]。 
   
           :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-console-settings.png" alt-text="使用主控台索引標籤開發人員工具，並保留已選取的記錄檔。" :::

        再次選取 **設定** 以關閉 **主控台設定**。

3. 接下來，請停止並清除進行中的任何錄製。 選取 [ **網路** ] 索引標籤，選取 [ **停止記錄網路記錄** 檔]，然後 **清除**。
   
   :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-stop-recording.png" alt-text="開發人員工具 [網路] 索引標籤，並已選取 [停止並清除錄製選項]。" :::
     
2. 現在，您將重現您在 Power BI 服務中遇到的問題。 若要開始，請在 **開發人員工具** 選取 [ **網路** ] 索引標籤。選取 [ **記錄網路** 記錄檔]。

    > [!IMPORTANT]
    >重新整理 Power BI 服務中的瀏覽器頁面，再開始重現問題，以便正確地捕捉追蹤。

   重現導致您需要協助的問題的步驟。

     :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-record-network-log.png" alt-text="已選取 [網路] 索引標籤和 [記錄網路] 記錄的開發人員工具。" :::

    當您重現問題時，您會在 **開發人員工具** 視窗中看到類似下圖的輸出。

    :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-output.png" alt-text="具有顯示會話輸出的 [網路] 索引標籤的開發人員工具。" :::
    
3. 重現問題行為之後，您必須儲存記錄檔，並將其附加至您的支援要求。
    1. 若要匯出網路記錄檔，請在 **開發人員工具** 選取 [ **網路** ] 索引標籤。選取 [ **停止錄製網路記錄** 檔]。 然後，選取 [ **匯出 HAR** ]，然後儲存檔案。

         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-export-har.png" alt-text="已選取 [網路] 索引標籤、[停止錄製] 和 [匯出 HAR 選項] 開發人員工具。" :::

    2. 若要匯出主控台輸出，請在 **開發人員工具** 選取 [ **主控台** ] 索引標籤。以滑鼠右鍵按一下顯示的訊息，然後選取 [ **另存** 新檔]，並將主控台輸出儲存至文字檔。
    
         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-save-as.png" alt-text="開發人員工具已選取主控台索引標籤，並顯示 [另存新檔] 選項。" :::

   以壓縮格式（如 .zip）封裝儲存的 HAR 檔案、主控台輸出和螢幕錄製，並將檔案附加至您的支援要求。

#### <a name="apple-safari"></a>[Apple Safari](#tab/apple-safari)

下列步驟示範如何使用 Apple Safari 中的開發人員工具。 如需詳細資訊，請參閱 [Safari 開發人員工具概觀](https://support.apple.com/guide/safari-developer/safari-developer-tools-overview-dev073038698/11.0/mac)。

1. 登入之後，啟用 Apple Safari 中的開發人員工具：
    1. 從頁面標頭中選取 [ **Safari**  >  **喜好** 設定]。
    
       :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-preferences.png" alt-text="已選取喜好設定的 Apple Safari 功能表。" :::

    2. 選取 [ **Advanced**]，然後選取 **功能表列中的 [顯示開發功能表** ]，以啟用開發人員工具。
    
       :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-show-develop-menu.png" alt-text="選取功能表列中的 [顯示開發] 功能表的 Safari [advanced] 功能表。" :::

2. 接下來，您將在 **Web** 偵測器中設定選項，讓您的瀏覽器保留所有的追蹤資訊。 根據預設，瀏覽器只會保留目前載入頁面的追蹤資訊。 這些設定可確保即使您的重現需要前往一個以上的頁面，也會收集追蹤資訊。

    1. 選取 [**開發**  >  **顯示 Web 檢查**]。
    
        :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-web-inspector.png" alt-text="已選取 [顯示 Web 偵測器] 的 [開發] 功能表。" :::

    2. 選取 **網路**  >  **保留記錄**
       
         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-network-preserve-log.png" alt-text="具有網路的 Web 偵測器功能表，並保留選取的記錄。" :::

    1. 選取 **主控台**  >  **保留記錄**
   
       :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-console-preserve-log.png" alt-text="具有主控台的 Web 偵測器功能表，並保留已選取的記錄檔。" :::

3. 設定選項之後，請選取 [**網路**  >  **清除網路專案**]，以確保您的記錄只包含有關問題重現的詳細資料。

    :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-clear-network-items.png" alt-text="已選取 [網路] 和 [清除網路專案] 的 [Web 偵測器] 功能表。" :::


4. 現在您已經準備好重現問題。 
    > [!IMPORTANT]
    >重新整理 Power BI 服務中的瀏覽器頁面，再開始重現問題，以便正確地捕捉追蹤。

    請完成這些步驟來重現您遇到的問題。 當您重現問題時，您會在 [ **網路** ] 視窗中看到類似下圖的輸出。

    :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-session-output.png" alt-text="顯示範例輸出的網路視窗。" :::

5. 重現問題行為之後，您必須儲存記錄檔，並將其附加至您的支援要求。

    1. 若要匯出網路記錄檔，請從 [ **網路** ] 索引標籤選取 [ **匯出** ]，然後將檔案儲存為 HAR 格式。

         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/safari-export.png" alt-text="已選取 [匯出] 選項的 [網路] 索引標籤。" :::

    2. 若要匯出主控台輸出，請在 [ **開發** 工具] 窗格中選取 [ **主控台** ] 索引標籤，然後展開視窗。 將游標放在主控台輸出的開頭，然後拖曳並選取輸出的完整內容。 使用 -C 命令來複製輸出，並將儲存至文字檔。

   以壓縮格式（如 .zip）封裝儲存的 HAR 檔案、主控台輸出和螢幕錄製，並將檔案附加至您的支援要求。

#### <a name="firefox"></a>[Firefox](#tab/firefox)

下列步驟示範如何使用 Firefox 中的開發人員工具。 如需詳細資訊，請參閱 [Firefox 開發人員工具](https://developer.mozilla.org/docs/Tools)。

1. 登入之後，請在鍵盤上按 F12 鍵。 或者，在 Firefox 中選取 [ **開啟功能表** :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/firefox-menu.png" alt-text="Firefox 功能表] 圖示。" border="false"::: > **Web 開發人員**  > **切換工具**。 工具會顯示在螢幕底部。

1. 接下來，您將設定偵測 **器** 中的選項，讓您的瀏覽器保留所有的追蹤資訊。 根據預設，瀏覽器只會保留目前載入頁面的追蹤資訊。 這些設定可確保即使您的重現需要前往一個以上的頁面，也會收集追蹤資訊。

    1. 在 [偵測 **器** ] 視窗中，選取 [ **網路** ] 索引標籤。然後，選取 [ **保存記錄**]。
    
       :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/firefox-network-persist-logs.png" alt-text="已選取 [網路] 索引標籤和保存記錄的偵測器工具。" :::

     2. 選取 [**主控台**] 索引標籤，然後選取 [**主控台設定**  >  **保存記錄** 檔]。 
   
           :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/firefox-console-persist-logs.png" alt-text="已選取 [主控台] 索引標籤和保存記錄的偵測器工具。" :::

3. 設定選項之後，清除任何進行中的記錄。 選取 [ **網路** ] 索引標籤，然後 **清除**。
   
   :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/browser-trace-stop-recording.png" alt-text="開發人員工具 [網路] 索引標籤，並已選取 [停止並清除錄製選項]。" :::
     
2. 現在您已經準備好重現問題。 
    > [!IMPORTANT]
    >重新整理 Power BI 服務中的瀏覽器頁面，再開始重現問題，以便正確地捕捉追蹤。
 
    請完成這些步驟來重現您遇到的問題。
    
3. 重現問題行為之後，您必須儲存記錄檔，並將其附加至您的支援要求。
    1. 若要匯出網路記錄檔，請選取 [**網路**  >  **HAR 匯出/匯入**]，然後 **將其全部儲存為 HAR**。

         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/firefox-save-har.png" alt-text="具有 HAR 匯出/匯入功能表的 [網路] 索引標籤，並儲存所有選取的選項。" :::

    2. 若要匯出主控台輸出，請選取 [ **主控台** ] 索引標籤。以滑鼠右鍵按一下顯示的訊息，然後選取 [ **匯出可見的訊息**]，並將主控台輸出儲存至文字檔。
    
         :::image type="content" source="media/service-admin-capturing-additional-diagnostic-information-for-power-bi/firefox-export-visible-messages.png" alt-text="已選取主控台索引標籤，並顯示 [匯出可見訊息] 選項。" :::

   以壓縮格式（如 .zip）封裝儲存的 HAR 檔案、主控台輸出和螢幕錄製，並將檔案附加至您的支援要求。

---

收集診斷檔案之後，請將其附加至您的支援要求，以協助支援工程師解決您的問題。 HAR 檔案會包含瀏覽器視窗與 Power BI 服務之間網路要求的所有相關資訊，包括：

* 每個要求的活動識別碼。

* 每個要求的精確時間戳記。

* 傳回用戶端的所有錯誤資訊。

這項追蹤也會包含用來填入畫面上所示視覺效果的資料。

## <a name="next-steps"></a>後續步驟

* [在 Microsoft 365 中追蹤 Power BI 服務健全狀況](service-admin-health.md)
* [啟用服務中斷通知](service-interruption-notifications.md)
* [加入 Power BI 社群](https://community.powerbi.com/)
