---
title: 從 Excel 活頁簿檔案取得資料
description: 了解如何從 Excel 活頁簿檔案取得資料並放入 Power BI
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 09/06/2019
LocalizationGroup: Data from files
ms.openlocfilehash: 0411cceb056d3471b3084a38916b83c815a0ae3b
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410359"
---
# <a name="get-data-from-excel-workbook-files"></a>從 Excel 活頁簿檔案取得資料
![Excel 圖示](media/service-excel-workbook-files/excel_icon.png)

Microsoft Excel 是極為普遍使用的商務應用程式， 也是將資料帶入 Power BI 極為常見的方式。

## <a name="what-types-of-workbooks-does-power-bi-support"></a>Power BI 支援哪些活頁簿類型？
Power BI 支援匯入或連接到以 Excel 2007 及更新版本建立的活頁簿。 活頁簿必須儲存為 .xlsx 或 .xlsm 檔案類型，並小於 1 GB。 本文所述的部分功能僅適用於較新版的 Excel。

### <a name="workbooks-with-ranges-or-tables-of-data"></a>使用資料範圍或資料表的活頁簿
如果您的活頁簿包含具有資料範圍的簡單工作表，為了在 Power BI 中充分利用您的資料，請務必將這些範圍格式化為資料表。 如此一來，當您在 Power BI 中建立報表時，就會在 [欄位] 窗格中看到具名資料表和資料行，因此可以更容易將資料視覺化。

### <a name="workbooks-with-data-models"></a>使用資料模型的活頁簿
活頁簿可以包含具有一個或多個資料表的資料模型，這些資料表是透過連結資料表、Power Query (Excel 2016 的 [取得和轉換]) 或 Power Pivot 載入資料模型。 Power BI 支援所有資料模型屬性，例如關聯性、量值、階層和 KPI。

> [!NOTE]
> Power BI 租用戶之間無法共用使用資料模型的活頁簿。 例如，使用 *contoso.com* 帳戶登入 Power BI 的使用者，無法與從 *woodgrovebank.com* 使用 Power BI 登入帳戶登入的使用者共用 Excel 活頁簿。
> 
> 

### <a name="workbooks-with-connections-to-external-data-sources"></a>連接到外部資料來源的活頁簿
如果您使用 Excel 連接到外部資料來源，在 Power BI 中開啟活頁簿後，您就可以根據已連接資料來源中的資料建立報表和儀表板。 您也可以設定「排定的重新整理」，以自動連接到資料來源並取得更新。 您將不再需要從 Excel 的 [資料] 功能區手動重新整理。 報表或儀表板磚中以該資料來源的資料為基礎的所有視覺效果都會自動更新。 如需深入了解，請參閱 [Power BI 的資料重新整理](refresh-data.md)。

### <a name="workbooks-with-power-view-sheets-pivottables-and-charts"></a>使用 Power View 工作表、樞紐分析表和圖表的活頁簿
您的 PowerView 工作表、樞紐分析表和圖表在 Power BI 中是否顯示及顯示方式，取決於活頁簿檔案的儲存位置，以及您選擇將其放入 Power BI 的方式。 底下將深入探討。

## <a name="data-types"></a>資料類型
Power BI 支援下列資料類型：整數、十進位數字、貨幣、日期、True/False、文字。 在 Excel 中將資料標示為特定資料類型會改善 Power BI 的體驗。

## <a name="prepare-your-workbook-for-power-bi"></a>準備活頁簿以供 Power BI 使用
請觀賞這段實用的影片，以深入了解如何確保 Excel 活頁簿已準備好供 Power BI 使用。

<iframe width="500" height="281" src="https://www.youtube.com/embed/l2wy4XgQIu0" frameborder="0" allowfullscreen></iframe>

## <a name="where-your-workbook-file-is-saved-makes-a-difference"></a>活頁簿檔案的儲存位置會形成差異
**本機** - 如果您將活頁簿檔案儲存到電腦上的本機磁碟或組織中的其他位置，您可以從 Power BI 將檔案載入 Power BI。 您的檔案實際上會保留在本機磁碟，因此不是真的將整個檔案匯入 Power BI。 真正發生的情況是在 Power BI 中建立新的資料集，並將資料和資料模型 (如果有) 從活頁簿載入資料集。 如果您的活頁簿有任何 Power View 工作表，這些工作表會顯示在 Power BI 網站的 [報表] 下。 Excel 2016 還提供 [發佈] 功能 (在 [檔案] 功能表下)。 使用 [發佈] 實際上就是使用 Power BI 的 [取得資料] > [檔案] > [本機檔案]，但如果您定期變更活頁簿，這樣做通常會更容易在 Power BI 更新您的資料集。

**OneDrive - 商務** - 如果您有商務用 OneDrive，並使用與用來登入 Power BI 相同的帳戶進行登入，這樣做可以有效地讓 Excel 中的工作，與 Power BI 中的資料集、報表和儀表板保持同步。由於 Power BI 和 OneDrive 都在雲端，因此 Power BI 每隔約一小時就會「連接」到您在 OneDrive 上的活頁簿檔案。 如果發現任何變更，便會自動更新 Power BI 中的資料集、報表和儀表板。 就像是將活頁簿儲存到本機磁碟，您也可以使用 [發佈] 立即更新 Power BI 中的資料集和報表；如果未這麼做，Power BI 通常會在一小時內自動同步處理。

**OneDrive - 個人** - 如果您將活頁簿檔案儲存到自己的 OneDrive 帳戶，則可以利用許多與使用商務用 OneDrive 相同的優點。 最大的差異是當您第一次連接到檔案時 (使用 [取得資料] > [檔案] > [OneDrive - 個人])，需要使用 Microsoft 帳戶登入 OneDrive，這通常與用來登入 Power BI 的帳戶不同。 當您使用 Microsoft 帳戶登入 OneDrive 時，請務必選取 [讓我保持登入] 選項。 如此一來，Power BI 每隔約一小時就會連接到您的活頁簿檔案，以確保您在 Power BI 中的資料集和報表保持同步。

**SharePoint 小組網站** - 將 Power BI Desktop 檔案儲存到 SharePoint - 小組網站與儲存到商務用 OneDrive 大致相同。 最大的差異是從 Power BI 連接到檔案的方式。 您可以指定 URL 或連接到根資料夾。

## <a name="one-excel-workbook--two-ways-to-use-it"></a>一個 Excel 活頁簿 - 兩種使用方式
如果您將活頁簿檔案儲存到 **OneDrive**，有幾個方式可以瀏覽您在 Power BI 中的資料。

![商務用 OneDrive 的螢幕擷取畫面，其中顯示匯入或連線到 Excel 資料的選項。](media/service-excel-workbook-files/excel_import_connect.png)

### <a name="import-excel-data-into-power-bi"></a>將 Excel 資料匯入至 Power BI
當您選擇 [匯入] 時，資料表及/或資料模型中任何支援的資料都會匯入 Power BI 中的新資料集。 如果您有任何 Power View 工作表，則會在 Power BI 中重新建立為報表。

您可以繼續編輯活頁簿。 當您儲存變更後，這些變更通常會在一小時內與 Power BI 中的資料集同步處理。 如果您需要立即同步處理，您可以直接再按一次 [發佈] 立即匯出變更。 您在報表和儀表板中的任何視覺效果也會更新。

如果您使用 [取得和轉換資料] 或 Power Pivot 將資料載入資料模型，或是您的活頁簿具有想要在 Power BI 中查看的 Power View 工作表及視覺效果，請選擇此選項。

在 Excel 2016 中，您也可以使用 [發佈] > [匯出]。 其功能幾乎相同。 如需深入了解，請參閱[從 Excel 2016 發佈至 Power BI](service-publish-from-excel.md)。

### <a name="connect-manage-and-view-excel-in-power-bi"></a>在 Power BI 中連接、管理及檢視 Excel
當您選擇 [連接] 時，您的活頁簿會顯示在 Power BI 中，就像是在 Excel Online 中一樣。 但不同於 Excel Online，您有一些很棒的功能，可協助您將工作表中的項目釘選到儀表板。

您無法在 Power BI 中編輯活頁簿。 但如果您需要進行一些變更，您可以按一下 [編輯]，然後選擇在 Excel Online 中編輯活頁簿，或在電腦上以 Excel 開啟活頁簿。 您所做的任何變更都會儲存到 OneDrive 上的活頁簿。

如果您只有工作表中的資料，或是有需要釘選到儀表板的範圍、樞紐分析表和圖表，請選擇此選項。

在 Excel 2016 中，您也可以使用 [發佈] > [上傳]。 其功能幾乎相同。 如需深入了解，請參閱[從 Excel 2016 發佈至 Power BI](service-publish-from-excel.md)。

## <a name="import-or-connect-to-an-excel-workbook-from-power-bi"></a>從 Power BI 匯入或連接到 Excel 活頁簿
1. 在 Power BI 的導覽窗格中，按一下 [取得資料]。
   
   ![[取得資料] 的螢幕擷取畫面，其中顯示該按鈕在功能窗格中。](media/service-excel-workbook-files/excel_get_data_button.png)
2. 在 [檔案] 中，按一下 [取得]。
   
   ![[檔案] 對話方塊的螢幕擷取畫面，其中顯示 [取得] 按鈕。](media/service-excel-workbook-files/excel_files_get.png)
3. 尋找您的檔案。
   
   ![四個磚的螢幕擷取畫面，該磚用來尋找檔案，其中顯示本機檔案、OneDrive 商務、OneDrive 個人及 SharePoint 磚。](media/service-excel-workbook-files/excel_find_your_file.png)
4. 如果您的活頁簿檔案位於 OneDrive 或 SharePoint - 小組網站上，請選擇 [匯入] 或 [連接]。

## <a name="local-excel-workbooks"></a>本機 Excel 活頁簿
您也可以使用本機 Excel 檔案並將其上傳到 Power BI。 只要從上一個功能表選取 [本機檔案]，然後導覽至您儲存 Excel 活頁簿的位置即可。

![[本機檔案] 磚的螢幕擷取畫面，其中顯示如何巡覽以選取 Excel 活頁簿。](media/service-excel-workbook-files/excel_import_6.png)

選取之後，您可以選擇將檔案上傳到 Power BI。

![[本機檔案] 對話方塊的螢幕擷取畫面，其中顯示 [將 Excel 檔案上傳到 Power BI] 選取項目。](media/service-excel-workbook-files/excel_import_7.png)

上傳活頁簿之後，您會收到活頁簿準備就緒的通知。

![通知的螢幕擷取畫面，其中顯示活頁簿已就緒。](media/service-excel-workbook-files/excel_import_8.png)

活頁簿準備就緒之後，即可在 Power BI 的 [報表] 區段中找到此活頁簿。

![[報表] 區段的螢幕擷取畫面，其中顯示含有 Excel 資料的所選報表。](media/service-excel-workbook-files/excel_import_9.png)

## <a name="publish-from-excel-2016-to-your-power-bi-site"></a>從 Excel 2016 發佈至您的 Power BI 網站
使用 Excel 2016 的 [發佈至 Power BI] 功能，實際上就是使用 Power BI 的 [取得資料] 匯入或連接到您的檔案。 此處不會詳細說明，不過您可以參閱[從 Excel 2016 發佈至 Power BI](service-publish-from-excel.md) 以深入了解。

## <a name="troubleshooting"></a>疑難排解
活頁簿檔案太大？ 請參閱[減少 Excel 活頁簿的大小以在 Power BI 中檢視](reduce-the-size-of-an-excel-workbook.md)。

目前，當您選擇 [匯入] 時，Power BI 只會匯入具名資料表或資料模型中的資料。 因此，如果活頁簿中沒有具名資料表、Power View 工作表或 Excel 資料模型，您就會看到錯誤：[在此 Excel 活頁簿中找不到任何資料]。 [這篇文章](service-admin-troubleshoot-excel-workbook-data.md)說明如何修正您的活頁簿並重新匯入。

## <a name="next-steps"></a>後續步驟
**瀏覽您的資料** - 將檔案中的資料和報表匯入 Power BI 後，您就可以開始瀏覽。 只要以滑鼠右鍵按一下新的資料集，然後按一下 [瀏覽]。 如果您在步驟 4 中，選擇連接到 OneDrive 上的活頁簿檔案，您的活頁簿會顯示在 [報表] 中。 當您按一下活頁簿時，活頁簿會在 Power BI 中開啟，就像是在 Excel Online 中一樣。

**排程重新整理** - 如果您的 Excel 活頁簿檔案連接到外部資料來源，或是從本機磁碟匯入，您可以設定排定的重新整理，確保資料集或報表一律為最新狀態。 在大多數情況下，設定排定的重新整理相當容易，但細節部分則不在本文的討論範圍內。 如需深入了解，請參閱 [Power BI 的資料重新整理](refresh-data.md)。

[從 Excel 2016 發佈至 Power BI](service-publish-from-excel.md)

[Power BI 的資料重新整理](refresh-data.md)
