---
title: 從 Power BI Desktop 檔案取得資料
description: 了解如何從 Power BI Desktop 取得資料和報表並放入 Power BI
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 05/26/2020
LocalizationGroup: Data from files
ms.openlocfilehash: e89f45d302216af8193029cb613b4e7a54365b8d
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410382"
---
# <a name="get-data-from-power-bi-desktop-files"></a>從 Power BI Desktop 檔案取得資料
![Power BI Desktop 檔案圖示](media/service-desktop-files/pbid_file_icon.png)

**Power BI Desktop** 讓商業智慧和報表變得容易。 不論您是要連接到許多不同的資料來源、查詢和轉換資料、建立資料模型，還是建立強大的動態報表，**Power BI Desktop** 都讓商業智慧工作變得直接易懂又快速。 如果您不熟悉 **Power BI Desktop**，請參閱 [開始使用 Power BI Desktop](../fundamentals/desktop-getting-started.md)。

當您將資料放入 **Power BI Desktop**，並建立一些報表後，您就能夠將儲存的檔案放入 **Power BI 服務**。

## <a name="where-your-file-is-saved-makes-a-difference"></a>檔案的儲存位置會形成差異
**本機** - 如果您將檔案儲存到電腦上的本機磁碟或組織中的其他位置，您可以「匯入」檔案或從 Power BI Desktop「發佈」，以將其資料和報表放入 Power BI。 您的檔案實際上會保留在本機磁碟，因此不是真的將整個檔案移至 Power BI。 真正發生的情況是在 Power BI 中建立新的資料集，並將資料和資料模型從 Power BI Desktop 檔案載入資料集。 如果您的檔案有任何報表，這些報表會顯示在 Power BI 網站的 [報表] 下。

**OneDrive - 商務** - 如果您有商務用 OneDrive，並使用與用來登入 Power BI 相同的帳戶進行登入，這樣做可以有效地讓 Power BI Desktop 中的工作，與 Power BI 中的資料集、報表和儀表板保持同步。由於 Power BI 和 OneDrive 都在雲端，因此 Power BI 每隔約一小時就會「連接」到您在 OneDrive 上的檔案。 如果發現任何變更，便會自動更新 Power BI 中的資料集、報表和儀表板。

**OneDrive - 個人** - 如果您將檔案儲存到自己的 OneDrive 帳戶，則可以利用許多與使用商務用 OneDrive 相同的優點。 最大的差異是當您第一次連接到檔案時 (使用 [取得資料] > [檔案] > [OneDrive - 個人])，需要使用 Microsoft 帳戶登入 OneDrive，這通常與用來登入 Power BI 的帳戶不同。 當您使用 Microsoft 帳戶登入 OneDrive 時，請務必選取 [讓我保持登入] 選項。 如此一來，Power BI 每隔約一小時就會連接到您的檔案，以確保您在 Power BI 中的資料集保持同步。

**SharePoint 小組網站** - 將 Power BI Desktop 檔案儲存到 SharePoint - 小組網站與儲存到商務用 OneDrive 大致相同。 最大的差異是從 Power BI 連接到檔案的方式。 您可以指定 URL 或連接到根資料夾。 您也可以<a href="https://support.microsoft.com/office/sync-sharepoint-and-teams-files-with-the-onedrive-sync-app-6de9ede8-5b6e-4503-80b2-6190f3354a88">設定同步資料夾</a>，以指向 SharePoint 資料夾；該處的檔案會與 SharePoint 上主要複本同步。

## <a name="import-or-connect-to-a-power-bi-desktop-file-from-power-bi"></a>從 Power BI 匯入或連接到 Power BI Desktop 檔案
>[!IMPORTANT]
>您可以匯入 Power BI 的檔案大小上限為 1 GB。

1. 在 Power BI 的導覽器窗格中，按一下 [取得資料]。
   
   ![[取得資料] 的螢幕擷取畫面，其中顯示該按鈕在功能窗格中。](media/service-desktop-files/pbid_get_data_button.png)
2. 在 [檔案] 中，按一下 [取得]。
   
   ![[檔案] 對話方塊的螢幕擷取畫面，其中顯示 [取得] 按鈕。](media/service-desktop-files/pbid_files_get.png)
3. 尋找您的檔案。 Power BI Desktop 檔案的副檔名為 .PBIX。
   
   ![四個磚的螢幕擷取畫面，該磚用來尋找檔案，其中顯示本機檔案、OneDrive 商務、OneDrive 個人及 SharePoint 磚。](media/service-desktop-files/pbid_find_your_file.png)

## <a name="publish-a-file-from-power-bi-desktop-to-your-power-bi-site"></a>將檔案從 Power BI Desktop 發佈至您的 Power BI 網站
使用 Power BI Desktop 的 [發佈]，在一開始從本機磁碟機匯入檔案資料或連線到 OneDrive 上的檔案方面，類似於使用 Power BI 的 [取得資料]。 不過，有一些差異：如果從本機磁碟機上傳，則會想要經常重新整理該資料，以確保資料的線上和本機複本彼此都是最新的。 

以下是快速操作說明，但您可以參閱[從 Power BI Desktop 發佈](../create-reports/desktop-upload-desktop-files.md)以深入了解。

1. 在 Power BI Desktop 中，按一下 [檔案] > [發佈] > [發佈至 Power BI]，或在功能區上按一下 [發佈]。
   
   ![功能區上 [發佈] 的螢幕擷取畫面，其中顯示如何從 Power BI Desktop 發佈。](media/service-desktop-files/pbid_publish.png)
2. 登入 Power BI。 只有第一次才需要執行這項作業。
   
   完成時，就會得到連結，用於在 Power BI 網站中開啟報表。
   
   ![登入確認對話方塊的螢幕擷取畫面，其中顯示已成功登入並呈現用來開啟報表的連結。](media/service-desktop-files/pbid_publishing.png)

## <a name="next-steps"></a>後續步驟
**瀏覽您的資料** - 將檔案中的資料和報表匯入 Power BI 後，您就可以開始瀏覽。 如果您的檔案已經有報表，即會顯示在導覽器窗格的 [報表] 中。 如果檔案只有資料，您可以建立新報表；請直接以滑鼠右鍵按一下新資料集，然後按一下 [瀏覽]。

**重新整理外部資料來源** - 如果您的 Power BI Desktop 檔案連接到外部資料來源，您可以設定排定的重新整理，確保資料集一律為最新狀態。 在大多數情況下，設定排定的重新整理相當容易，但細節部分則不在本文的討論範圍內。 如需深入了解，請參閱 [Power BI 的資料重新整理](refresh-data.md)。
