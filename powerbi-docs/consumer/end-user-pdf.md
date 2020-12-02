---
title: 將報表匯出至 PDF
description: 了解如何將 Power BI 報表匯出至 PDF。
author: mihart
ms.author: mihart
ms.custom: ''
ms.reviewer: cmfinlan
ms.service: powerbi
ms.subservice: pbi-explore
ms.topic: how-to
ms.date: 09/17/2020
LocalizationGroup: Share your work
ms.openlocfilehash: de9265112d587418345c2eadb8d33acdddf900d4
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96399687"
---
# <a name="export-reports-from-power-bi-to-pdf"></a>從 Power BI 將報表匯出至 PDF

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

[!INCLUDE [power-bi-service-new-look-include](../includes/power-bi-service-new-look-include.md)]

有了 Power BI，您就可以將報表發佈為 PDF 格式，並根據 Power BI 報表輕鬆地建立文件。 當您匯出至 PDF 時，Power BI 報表中每個頁面都會變成 PDF 文件中的個別頁面。

## <a name="export-your-power-bi-report-to-pdf"></a>將 Power BI 報表匯出至 PDF
在 Power BI 服務中，選取要顯示在畫布上的報表。 您也可以從導覽窗格的 [首頁]  、[應用程式]  或其他任何容器中選取報表。

1. 從功能表列中選取 [匯出]   > [PDF]  。

    ![從功能表列選取 [匯出]](media/end-user-pdf/power-bi-export-pdfs.png)

    隨即出現快顯視窗，其中有選項可供您選取 [目前的值]  或 [預設值]  。 [目前的值]  會以目前狀態匯出報表，其中包括您對交叉分析篩選器和篩選值進行的有效變更。 大多數使用者會選取此選項。 或者，選取 [預設值] 則會以原始狀態 (如同「設計師」共用當下的狀態) 匯出報表，而不會反映您對該原始狀態進行的任何變更。
    
    另外，還會出現核取方塊供您選取是否要匯出報表的隱藏索引標籤。 如果您只要在瀏覽器中匯出可看見的報表索引標籤，請選取此核取方塊。 如果您希望在匯出過程中取得所有隱藏索引標籤，則可以不要選取此核取方塊。 如果核取方塊呈現灰色，即代表報表中沒有任何隱藏索引標籤。 在您選取完成後，請選取 [匯出]  繼續。
    
    您也可以按一下 [僅匯出目前頁面] 選項，只匯出報表中您目前正在檢視的頁面。  根據預設，系統會取消選取此選項，而且會從您的報表匯出所有頁面。
    
    進度列會顯示在右上角。 匯出可能需要幾分鐘的時間。 您可以在正在匯出報表時繼續使用 Power BI 工作。

    ![匯出進度訊息](media/end-user-pdf/power-bi-export-progress.png)

    在 Power BI 服務完成匯出程序後，通知橫幅會隨即變更以讓您知道。

2. 您可以在瀏覽器顯示下載檔案的位置取得檔案。 在下圖中，是以瀏覽器視窗底部的下載橫幅方式顯示。

    ![下載的檔案位置](media/end-user-pdf/power-bi-export-done.png)

就是這麼簡單。 您可以下載檔案，並以任何 PDF 檢視器開啟它，例如 Microsoft Edge 中提供的 PDF 檢視器。


## <a name="limitations-and-considerations"></a>限制與考量
當您使用 [匯出至 PDF]  功能時，需牢記幾項考量與限制。

* PDF 將包含 Power BI 畫布上顯示的資料與視覺效果。 如果視覺效果包含捲軸，PDF 將會包含其無法捲動之預設狀態的視覺效果。  
* 目前不支援 R 視覺效果與 Python 視覺效果。 在 PDF 中，這些視覺效果會是空白，並顯示錯誤訊息。 
* 目前支援經認證的 Power BI 視覺效果。 如需認證 Power BI 視覺效果 (包括如何使 Power BI 視覺效果獲得認證) 的詳細資訊，請參閱[讓 Power BI 視覺效果獲得認證](../developer/visuals/power-bi-custom-visuals-certified.md)。 不支援未經認證的 Power BI 視覺效果。 在 PDF 中，將會顯示它們並出現錯誤訊息。
* 不支援 ESRI 視覺效果。
* 目前無法匯出超過 50 頁的報表。
* 將報表匯出至 PDF 的程序可能需時數分鐘，請耐心等候。 影響所需時間的因素，包括報表結構及 Power BI 服務目前的負載。
* 若 Power BI 服務中沒有 [匯出至 PDF] 功能表項目，可能是因為 Power BI 管理員停用了此功能。 請連絡管理員以取得詳細資料。
* 背景影像會按圖表的周框區域剪裁。 我們建議您先移除背景影像，再匯出至 PDF。
* Power BI 租用戶網域外部使用者擁有的報表 (例如，組織外部某人所擁有並與您共用的報表) 無法發佈至 PDF。
* 如果您與組織外部的某人 (也就是不在您 Power BI 租用戶中的使用者) 共用儀表板，則該使用者無法將共用儀表板的相關聯報表匯出至 PDF。 例如，如果您是 aaron@contoso.com，您可以與 cassie@northwinds.com 共用。 但是 cassie@northwinds.com 無法將相關聯報表匯出至 PDF。
* 將包含背景影像的報表匯出成 PDF 時，如果使用 [頁面背景] 中的 [標準] 或 [填滿] 選項，您可能會在匯出中看到扭曲的影像。 為得到最佳結果，請使用 [最適大小]  選項，以免匯出的文件發生問題。
* Power BI 服務會使用您的 Power BI 語言設定作為 PDF 的輸出語言。 若要查看或設定語言喜好設定，請選取齒輪圖示 ![齒輪圖示](media/end-user-powerpoint/power-bi-settings-icon.png) > [設定]   > [一般]   > [語言]  。
* 針對匯出選擇 [目前的值]  時，目前不適用 URL 篩選。
* 具有異常自訂頁面大小的報表可能會在匯出案例中遇到問題。 為獲得最佳結果，請考慮切換到報表的標準頁面大小。
* 匯出至 PDF 時，使用主題與自訂字型的報表會以預設字型取代自訂字型。
* 雖然我們希望提供一致的體驗，但無法保證從 Power BI 服務匯出的 PDF 將一律符合從本機 Power BI Desktop 檔案匯出的 PDF。
* 匯出至 PDF 時，無法保證 PBIX 報表的像素完全精確。

## <a name="next-steps"></a>後續步驟
[列印報表](end-user-print.md)
