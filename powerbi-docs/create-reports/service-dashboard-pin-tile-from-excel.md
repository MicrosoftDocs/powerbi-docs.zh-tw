---
title: 如何從 Excel 將磚釘選到 Power BI 儀表板
description: 從商務用 OneDrive 上的 Excel 將磚釘選到 Power BI 儀表板 釘選範圍、圖表、資料表
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: l8JoB7w0zJA
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 05/02/2018
LocalizationGroup: Dashboards
ms.openlocfilehash: b62a780bc504c0b2fc90aa368d8dc30ac745867e
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96417397"
---
# <a name="pin-a-tile-to-a-power-bi-dashboard-from-excel"></a>從 Excel 將磚釘選到 Power BI 儀表板
您要先連接活頁簿和 Power BI 服務 (app.powerbi.com)，才可以從 Excel 活頁簿釘選磚。 連接活頁簿其實就是將該活頁簿的連結唯讀版本帶入 Power BI 服務，且讓您將範圍釘選到儀表板。 您甚至可以將整份工作表釘選到儀表板。  
如果活頁簿已與您共用，您就能夠檢視擁有者釘選的磚，但不能自行建立任何儀表板磚。 

如需 Excel 和 Power BI 如何合作的詳細資訊，請參閱[從 Excel 活頁簿檔案取得資料](https://go.microsoft.com/fwlink/?LinkID=521962)。

觀看 Will 示範數種連接至 Excel 活頁簿及從中匯入資料的方式。

<iframe width="560" height="315" src="https://www.youtube.com/embed/l8JoB7w0zJA" frameborder="0" allowfullscreen></iframe>

## <a name="connect-your-excel-workbook-from-onedrive-for-business-to-power-bi"></a>從商務用 OneDrive 將 Excel 活頁簿連接至 Power BI
當您選擇 [連接]  時，您的活頁簿會顯示在 Power BI 中，就像是在 Excel Online 中一樣。 但不同於 Excel Online，您有一些很棒的功能，可協助您將工作表中的項目釘選到儀表板。

您無法在 Power BI 中編輯活頁簿。 但如果您需要進行一些變更，則可以從工作區的 [活頁簿]  索引標籤中選取鉛筆圖示，然後選擇在 Excel Online 中編輯活頁簿，或在電腦上以 Excel 開啟活頁簿。 您所做的任何變更都會儲存到 OneDrive 上的活頁簿。

1. 將活頁簿上傳至您的商務用 OneDrive。

2. 從 Power BI 選取 [取得資料] > [檔案] > [OneDrive - 商務]，然後瀏覽至您儲存 Excel 檔案的位置，以[連接到該活頁簿](../connect-data/service-excel-workbook-files.md)。 選取檔案並選擇 [連接] > [連接]  。

    ![[商務用 OneDrive] 對話方塊](media/service-dashboard-pin-tile-from-excel/power-bi-connect.png)

3. 在 Power BI 中，活頁簿會新增至工作區的 [活頁簿]  索引標籤。  ![活頁簿圖示](media/service-dashboard-pin-tile-from-excel/pbi_workbookicon.png) 圖示表示此為 Excel 活頁簿，而黃色星號代表其剛新增。
    
    ![活頁簿索引標籤](media/service-dashboard-pin-tile-from-excel/power-bi-workbooks.png)
4. 選取活頁簿名稱，在 Power BI 中開啟活頁簿。

    將不會儲存您對 Power BI 中活頁簿所進行的變更，且不會影響商務用 OneDrive 上的原始活頁簿。 如果您排序、篩選或變更 Power BI 中的值，將無法儲存或釘選這些變更。 如果您需要儲存所進行的變更，請選取右上角的 [編輯]  ，以便在 Excel Online 或 Excel 中開啟以進行編輯。 以此方式進行的變更，需要幾分鐘的時間才會更新儀表板上的磚。
   
    ![Power BI 中的 Excel Online](media/service-dashboard-pin-tile-from-excel/power-bi-opened.png)

## <a name="pin-a-range-of-cells-to-a-dashboard"></a>將資料格範圍釘選到儀表板
新增[儀表板磚](../consumer/end-user-tiles.md)的一種方法是在 Power BI 中從 Excel 活頁簿新增。 範圍可以從儲存在商務用 OneDrive 的 Excel 活頁簿釘選，或是從其他群組共用的文件庫釘選。 該範圍可以包含資料、圖表、資料表、樞紐分析表、樞紐分析圖，以及其他 Excel 組件。

1. 反白顯示您要釘選到儀表板的資料格。
   
    ![在 Excel 活頁簿中選取資料格](media/service-dashboard-pin-tile-from-excel/pbi_selectrange.png)
2. 選取釘選 ![釘選圖示](media/service-dashboard-pin-tile-from-excel/pbi_pintile_small.png) 圖示。 
3. 將磚釘選至現有的儀表板或新的儀表板上。 
   
   * 現有儀表板：從下拉式清單中選取儀表板的名稱。
   * 新儀表板：輸入新儀表板的名稱。
   
     ![[釘選到儀表板] 對話方塊](media/service-dashboard-pin-tile-from-excel/pbi_dashdialog1.png)
4. 選取 [釘選]  。 您可利用靠近右上角所出現的成功訊息，知道該範圍已加入儀表板成為磚。 
   
    ![[已釘選到儀表板] 對話方塊](media/service-dashboard-pin-tile-from-excel/power-bi-go-to-dashboard.png)
5. 選取 [移至儀表板]  。 您可以在這裡[重新命名、調整大小、連結和移動](service-dashboard-edit-tile.md)釘選的視覺效果。 選取釘選的磚預設會在 Power BI 中開啟活頁簿。

## <a name="pin-an-entire-table-or-pivottable-to-a-dashboard"></a>釘選整個資料表或樞紐分析表至儀表板
遵循上述步驟，但不選取資料格範圍，而是選取整份資料表或樞紐分析表。

若要釘選資料表，請選取整份資料表並確認包含標頭。  若要釘選樞紐分析表，請務必包含樞紐分析表每個可見的部分，包括篩選 (如有使用)。

 ![選取資料格](media/service-dashboard-pin-tile-from-excel/pbi_selecttable.png)

從資料表或樞紐分析表建立的磚，會顯示整個資料表。  如果您加入/移除/篩選原始活頁簿中的資料列或資料行，則於磚中也會新增/移除/篩選它們。

## <a name="view-the-workbook-linked-to-the-tile"></a>檢視連結至該磚的活頁簿
選取活頁簿磚時會在 Power BI 中開啟連結的活頁簿。 因為活頁簿檔案位於擁有者的商務用 OneDrive 上，所以檢視該活頁簿需要擁有該活頁簿的「讀取」權限。 如果沒有權限，就會收到錯誤訊息。  

 ![影片](media/service-dashboard-pin-tile-from-excel/pin-from-excel.gif)

## <a name="considerations-and-troubleshooting"></a>考量與疑難排解
不支援的功能：Power BI 使用 Excel Services 來擷取活頁簿圖格。 因此，因為 Excel Services REST API 不支援 Excel 的某些功能，所以在 Power BI 中的磚上不會看到它們。 例如：走勢圖、設定條件式格式的圖示和時間交叉分析篩選器。 如需不支援功能的完整清單，請參閱 [Unsupported Features in Excel Services REST API](/sharepoint/dev/general-development/unsupported-features-in-excel-services-rest-api) (Excel Services REST API 中不支援的功能)

## <a name="next-steps"></a>後續步驟
[共用可連結至 Excel 活頁簿的儀表板](../collaborate-share/service-share-dashboard-that-links-to-excel-onedrive.md)

[從 Excel 活頁簿取得資料](../connect-data/service-excel-workbook-files.md)

有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)
