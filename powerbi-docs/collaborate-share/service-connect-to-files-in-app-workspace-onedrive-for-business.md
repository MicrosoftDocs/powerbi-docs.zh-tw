---
title: 連接到傳統工作區 OneDrive 中的檔案
description: 瞭解如何在您的傳統 Power BI 工作區的 OneDrive 上儲存及連接到您的 Excel、CSV 和 Power BI Desktop 檔案。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukasz
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 01/28/2021
LocalizationGroup: Share your work
ms.openlocfilehash: f6544a137b8f656e938db4516de5e8c0685394b4
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99085791"
---
# <a name="connect-to-files-stored-in-onedrive-for-a-classic-workspace"></a>連接到儲存在 OneDrive 中的傳統工作區檔案
當您 [在 Power BI 中建立 *傳統* 工作區](service-create-workspaces.md)時，您也會建立具有相關商務用 OneDrive 的 Microsoft 365 群組。 此文章說明如何在商務用 OneDrive 上儲存及更新 Excel、CSV 與 Power BI Desktop 檔案。 這些更新會自動反映到以這些檔案為基礎的 Power BI 報表和儀表板中。

> [!NOTE]
> *新* 的工作區體驗會變更 Power BI 工作區與 Microsoft 365 群組之間的關聯性。 每次建立一個新的工作區時，不會自動建立 Microsoft 365 群組。 您也可以 [為新的工作區設定工作區 OneDrive](service-create-the-new-workspaces.md#set-a-workspace-onedrive)。

將檔案新增到傳統工作區是兩個步驟的程式： 

1. 首先，請[將檔案上傳至工作區的商務用 OneDrive](#1-upload-files-to-the-onedrive-for-business-for-your-workspace)。
2. 然後您[從 Power BI 連接至這些檔案](#2-import-excel-files-as-datasets-or-as-excel-online-workbooks)。

> [!NOTE]
> 具有 [Power BI Pro 授權](../fundamentals/service-features-license-type.md)才能使用工作區。
> 

## <a name="1-upload-files-to-the-onedrive-for-business-for-your-workspace"></a>1 將檔案上傳至工作區的商務用 OneDrive
1. 在 Power BI 服務中，選取工作區旁的箭號 > 選取工作區名稱旁邊的省略符號 ( **...** )。 
   
   ![Power BI 工作區的螢幕擷取畫面，其中顯示所選取的工作區名稱。](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-ellipsis.png)
2. 選取 [檔案] 以開啟 Microsoft 365 上工作區的商務用 OneDrive。
   
   > [!NOTE]
   > 如果在工作區功能表上看不到 [檔案]，請選取 [成員] 以開啟工作區的商務用 OneDrive。 在該處選取 [檔案] 。 Microsoft 365 會設定應用程式群組工作區檔案的 OneDrive 儲存位置。 此程序可能需要一些時間。
   > 
   > 
3. 您可以在這裡將檔案上傳至工作區的商務用 OneDrive。 選取 [上傳] ，並瀏覽至您的檔案。
   
   ![商務用 OneDrive 的螢幕擷取畫面，其中顯示如何巡覽以上傳檔案。](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_grpfilesonedrive.png)

## <a name="2-import-excel-files-as-datasets-or-as-excel-online-workbooks"></a>2 將 Excel 檔案匯入為資料集或 Excel Online 活頁簿
既然檔案已在工作區的商務用 OneDrive 中，即可進行選擇。 您可以： 

* [將 Excel 活頁簿中的資料以資料集匯入](../connect-data/service-get-data-from-files.md)。 然後使用此資料建置可在網頁瀏覽器和行動裝置上檢視的報表和儀表板。
* 或者[連接到 Power BI 的完整 Excel 活頁簿](../connect-data/service-excel-workbook-files.md)，讓其顯示畫面完全與在 Excel Online 一樣。

### <a name="import-or-connect-to-the-files-in-your-workspace"></a>匯入或連線至工作區中的檔案
1. 在 Power BI 中，切換至工作區，讓工作區名稱顯示於左上角。 
2. 在導覽窗格的底部，選取 [取得資料]。 
   
   ![[取得資料] 按鈕的螢幕擷取畫面，其中顯示該按鈕位於功能窗格中。](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-get-data-button.png)
3. 在 [檔案]  方塊中選取 [取得] 。
   
   ![[檔案] 對話方塊的螢幕擷取畫面，其中顯示 [取得] 按鈕。](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_getfiles.png)
4. 選取 [OneDrive - <工作區名稱>]。
   
    ![三個磚的螢幕擷取畫面，該磚用來選取工作區，其中顯示本機檔案、OneDrive 與 SharePoint。](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_grp_one_drive_shrpt.png)
5. 選取您想要的檔案 > [連接]。
   
    此時您需決定是要[從 Excel 活頁簿匯入資料](../connect-data/service-get-data-from-files.md)，或[連線至整個 Excel 活頁簿](../connect-data/service-excel-workbook-files.md)。
6. 選取 [匯入]  或 [連接] 。
   
    ![[商務用 OneDrive] 對話方塊的螢幕擷取畫面，其中顯示 [從 Excel 匯入] 或 [連接到 Excel]。](media/service-connect-to-files-in-app-workspace-onedrive-for-business/pbi_importexceldataorwholecrop.png)
7. 如果您選取 [匯入]，則活頁簿會出現在 [資料集] 索引標籤中。 
   
    ![Power BI 中工作區的螢幕擷取畫面，其中顯示 [資料集] 標籤索引。](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-excel-file-import.png)
   
    如果您選取 [連線]，則活頁簿會出現在 [活頁簿] 索引標籤中。
   
    ![Power BI 中工作區的螢幕擷取畫面，其中顯示 [活頁簿] 索引標籤。](media/service-connect-to-files-in-app-workspace-onedrive-for-business/power-bi-app-excel-file-connect.png)

## <a name="next-steps"></a>後續步驟
* [在 Power BI 中建立應用程式和工作區](../collaborate-share/service-create-distribute-apps.md)
* [從 Excel 活頁簿匯入資料](../connect-data/service-get-data-from-files.md)
* [連線到整個 Excel 活頁簿](../connect-data/service-excel-workbook-files.md
* 有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)
* 想提出意見反應嗎？ 請前往 [Power BI Ideas](https://ideas.powerbi.com/forums/265200-power-bi)
