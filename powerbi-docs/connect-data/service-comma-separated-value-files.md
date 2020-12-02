---
title: 從逗點分隔值 (.CSV) 檔案取得資料
description: 了解如何從 CSV 檔案取得資料並放入 Power BI
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 05/08/2019
LocalizationGroup: Data from files
ms.openlocfilehash: 01bef505d48f28df869bf2be705dcda963b3d0f9
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96403321"
---
# <a name="get-data-from-comma-separated-value-csv-files"></a>從逗點分隔值 (.CSV) 檔案取得資料
![CSV 圖示](media/service-comma-separated-value-files/csv_icon.png)

逗點分隔值檔案通常稱為 .CSV，這是具有多列資料並以逗號分隔每個值的簡單文字檔。 這些類型的檔案可以在相對很小的檔案內包含大量資料，因此是 Power BI 的理想資料來源。 您可以在[這裡](https://go.microsoft.com/fwlink/?LinkID=619356)下載範例 .CSV 檔案。

如果您有 .CSV，就能夠放到 Power BI 網站中作為資料集，以開始瀏覽資料、建立一些儀表板，並與其他人分享您的深入解析。

>[!TIP]
>許多組織會每天輸出內含更新資料的 .CSV。 若要確保您在 Power BI 中的資料集與更新的檔案保持同步，請務必以相同名稱將檔案儲存到 OneDrive。

## <a name="where-your-file-is-saved-makes-a-difference"></a>檔案的儲存位置會形成差異
**本機** - 如果您將 .CSV 檔案儲存到電腦上的本機磁碟或組織中的其他位置，您可以從 Power BI 將檔案「匯入」Power BI。 您的檔案實際上會保留在本機磁碟，因此不是真的將整個檔案匯入 Power BI。 真正發生的情況是在 Power BI 中建立新的資料集，並將資料從 .CSV 檔案載入資料集。

**OneDrive - 商務** - 如果您有商務用 OneDrive，並使用與用來登入 Power BI 相同的帳戶進行登入，這樣做可以有效地讓 .CSV 檔案，與 Power BI 中的資料集、報表和儀表板保持同步。由於 Power BI 和 OneDrive 都在雲端，因此 Power BI 每隔約一小時就會「連接」到您在 OneDrive 上的檔案。 如果發現任何變更，便會自動更新 Power BI 中的資料集、報表和儀表板。

**OneDrive - 個人** - 如果您將檔案儲存到自己的 OneDrive 帳戶，則可以利用許多與使用商務用 OneDrive 相同的優點。 最大的差異是當您第一次連接到檔案時 (使用 [取得資料] > [檔案] > [OneDrive - 個人])，需要使用 Microsoft 帳戶登入 OneDrive，這通常與用來登入 Power BI 的帳戶不同。 當您使用 Microsoft 帳戶登入 OneDrive 時，請務必選取 [讓我保持登入] 選項。 如此一來，Power BI 每隔約一小時就會連接到您的檔案，以確保您在 Power BI 中的資料集保持同步。

**SharePoint 小組網站** - 將 Power BI Desktop 檔案儲存到 SharePoint - 小組網站與儲存到商務用 OneDrive 大致相同。 最大的差異是從 Power BI 連接到檔案的方式。 您可以指定 URL 或連接到根資料夾。

## <a name="import-or-connect-to-a-csv-file"></a>匯入或連接到 .CSV 檔案
>[!IMPORTANT]
>您可以匯入 Power BI 的檔案大小上限為 1 GB。

1. 在 Power BI 的導覽器窗格中，按一下 [取得資料]。
   
   ![Power B I Desktop 中 [取得資料] 的螢幕擷取畫面，其中顯示功能窗格中的按鈕。](media/service-comma-separated-value-files/csv_get_data_button.png)
2. 在 [檔案] 中，按一下 [取得]。
   
   ![[檔案] 對話方塊的螢幕擷取畫面，其中顯示 [取得] 按鈕。](media/service-comma-separated-value-files/csv_files_get.png)
3. 尋找您的檔案。
   
   ![四個磚的螢幕擷取畫面，該磚用來尋找檔案，其中顯示本機檔案、OneDrive 商務、OneDrive 個人及 SharePoint 的選取項目。](media/service-comma-separated-value-files/csv_find_your_file.png)

## <a name="next-steps"></a>後續步驟
**瀏覽您的資料** - 將檔案中的資料匯入 Power BI 後，您就可以開始瀏覽。 只要以滑鼠右鍵按一下新的資料集，然後按一下 [瀏覽]。

**排程重新整理** - 如果將您的檔案儲存到本機磁碟，就能夠設定排定的重新整理，讓 Power BI 中的資料集和報表保持最新狀態。 如需深入了解，請參閱 [Power BI 的資料重新整理](refresh-data.md)。 如果將您的檔案儲存到 OneDrive，Power BI 每隔約一小時就會自動與其同步處理。

