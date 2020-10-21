---
title: 將超連結 (URL) 新增至資料表或矩陣
description: 本主題會指導如何將超連結 (URL) 新增至資料表。 您會使用 Power BI Desktop 來將超連結 (URL) 新增至資料集。 然後，在 Power BI Desktop 或 Power BI 服務中，您可以將那些超連結新增至您的報表資料表和矩陣。
author: maggiesMSFT
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 10/15/2020
ms.author: maggies
LocalizationGroup: Visualizations
ms.openlocfilehash: 824dc74d2461f9bbf6350694a48b00a327f3f13d
ms.sourcegitcommit: 59d07be9c3e4a2067f6d42c3002a194371bc4341
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2020
ms.locfileid: "92116584"
---
# <a name="add-hyperlinks-urls-to-a-table-or-matrix"></a>將超連結 (URL) 新增至資料表或矩陣
本主題會指導如何將超連結 (URL) 新增至資料表。 您會使用 Power BI Desktop 來將超連結 (URL) 新增至資料集。 然後，在 Power BI Desktop 或 Power BI 服務中，您可以將那些超連結新增至您的報表資料表和矩陣。 接著，您可以顯示 URL 或連結圖示，或將另一個資料行格式化為連結文字。

![包含超連結的資料表](media/power-bi-hyperlinks-in-tables/power-bi-url-link-text.png)

您也可以在 Power BI 服務和 Power BI Desktop 中，於[報表中的文字方塊](service-add-hyperlink-to-text-box.md)中建立超連結。 在 Power BI 服務中，您可以將超連結新增至[儀表板上的磚](service-dashboard-edit-tile.md)以及[儀表板上的文字方塊](service-dashboard-add-widget.md)。 


## <a name="format-a-url-as-a-hyperlink-in-power-bi-desktop"></a>將 URL 格式化為 Power BI Desktop 中的超連結

在 Power BI Desktop 中，您可以使用 URL 將欄位格式化為超連結，但是不能在 Power BI 服務中設定。 您也可以[在 Excel Power Pivot 中格式化超連結](#create-a-table-or-matrix-hyperlink-in-excel-power-pivot)，再將活頁簿匯入 Power BI。

1. 在 Power BI Desktop 中，如果含有超連結的欄位尚未存在於您的資料集內，請將其新增為[自訂資料行](../transform-model/desktop-common-query-tasks.md)。

    > [!NOTE]
    > 您無法在 DirectQuery 模式中建立資料行。  但若資料已經包含 URL，您可以將它們轉換成超連結。

2. 在 [資料] 或 [報表] 檢視中，選取資料行。 

3. 在 [模型]  索引標籤上，選取 [資料類別]   >  [Web URL]  。
   
    ![資料類別下拉式清單](media/power-bi-hyperlinks-in-tables/power-bi-format-web-url.png)

    > [!NOTE]
    > URL 的開頭必須是特定的前置詞。 如需完整清單，請參閱本文中的[考量與疑難排解](#considerations-and-troubleshooting)。

## <a name="create-a-table-or-matrix-with-a-hyperlink"></a>建立具有超連結的資料表或矩陣

1. 當您[將超連結格式化為 URL](#format-a-url-as-a-hyperlink-in-power-bi-desktop)之後，請切換至 [報表] 檢視。
2. 使用您分類為 Web URL 的欄位，建立資料表或矩陣。 超連結為藍色加底線。

    ![藍色且加上底線的連結](media/power-bi-hyperlinks-in-tables/power-bi-url-blue-underline.png)


## <a name="display-a-hyperlink-icon-instead-of-a-url"></a>顯示超連結圖示，而不是 URL

如果您不想在表格中顯示完整的 URL，可以改為顯示超連結圖示 ![超連結圖示](media/power-bi-hyperlinks-in-tables/power-bi-hyperlink-icon.png) 。 

> [!NOTE]
> 您無法在矩陣中顯示圖示。
   
1. 首先，[建立含有超連結的資料表](#create-a-table-or-matrix-with-a-hyperlink)。

2. 選取要使用的資料表。

    選取 [格式]  圖示![油漆滾筒圖示](media/power-bi-hyperlinks-in-tables/power-bi-paintroller.png)以開啟 [格式化] 索引標籤。

    展開 [值]  ，找到 **URL 圖示**並將其設定為 [開啟]  。

    ![開啟 URL 圖示](media/power-bi-hyperlinks-in-tables/power-bi-url-icon-on.png)

1. (選擇性) 從 Power BI Desktop [發佈報表](desktop-upload-desktop-files.md)至 Power BI 服務。 當您在 Power BI 服務中開啟報表時，超連結也會在該處運作。

## <a name="format-link-text-as-a-hyperlink"></a>將連結文字格式化為超連結

您也可以將資料表中的另一個欄位格式化為超連結，完全不具有該 URL 的資料行。 在此情況下，您不會將資料行格式化為 Web URL。

> [!NOTE]
> 您無法將另一個欄位格式化為矩陣中的超連結。

1. 如果具有超連結的欄位已存在於資料集中，請使用 Power BI Desktop 將其新增為[自訂資料行](../transform-model/desktop-common-query-tasks.md)。 同樣地，您無法在 DirectQuery 模式中建立資料行。  但若資料已經包含 URL，您可以將它們轉換成超連結。

2. 在 [資料] 或 [報表] 檢視中，選取包含此 URL 的資料行。 

3. 在 [模型]  索引標籤上，選取 [資料類別]  。 確定資料行已格式化為 [未分類]  。

2. 在 [報表] 檢視中，使用 URL 資料行和您要格式化為連結文字的資料行來建立資料表或矩陣。

3. 選取資料表之後，選取 [格式]  圖示![油漆滾筒圖示](media/power-bi-hyperlinks-in-tables/power-bi-paintroller.png)以開啟 [格式化] 索引標籤。

4. 展開 [條件式格式設定]  ，確定方塊中的名稱是您想要作為連結文字的資料行。 找到 [Web URL]  ，並將其設定為 [開啟]  。

    ![條件式格式設定 Web URL](media/power-bi-hyperlinks-in-tables/power-bi-format-conditional-web-url.png)

    > [!NOTE]
    > 如果找不到 [Web URL] 選項，請確定在 [資料類別] 下拉式方塊中，包含超連結的資料行「未」格式化為 [Web URL]。

5. 在 [Web URL]  對話方塊中，選取在 [根據欄位]  方塊中包含 URL 的欄位 > [確定]  。

    ![Web URL 對話方塊](media/power-bi-hyperlinks-in-tables/power-bi-format-web-url-dialog.png)

    此時，該資料行中的文字會格式化為連結。

    ![格式化為超連結的文字](media/power-bi-hyperlinks-in-tables/power-bi-url-link-text.png)

1. (選擇性) 從 Power BI Desktop [發佈報表](desktop-upload-desktop-files.md)至 Power BI 服務。 當您在 Power BI 服務中開啟報表時，超連結也會在該處運作。

## <a name="create-a-table-or-matrix-hyperlink-in-excel-power-pivot"></a>在 Excel Power Pivot 中建立資料表或矩陣超連結

將超連結新增至 Power BI 資料表和矩陣的另一種方式，是先在資料集內建立超連結，然後才從 Power BI 匯入/連線至該資料集。 這個範例會使用 Excel 活頁簿。

1. 請在 Excel 中開啟活頁簿。
2. 選取 [PowerPivot]  索引標籤，然後選擇 [管理]  。
   
   ![在 Excel 中開啟 PowerPivot](media/power-bi-hyperlinks-in-tables/createhyperlinkinpowerpivot2.png)
1. 當 PowerPivot 開啟時，選取 [進階]  索引標籤。
   
   ![PowerPivot [進階] 索引標籤](media/power-bi-hyperlinks-in-tables/createhyperlinkinpowerpivot3.png)
4. 將游標放在包含 URL 的資料行，其中的 URL 想要轉換成 Power BI 資料表中的超連結。
   
   > [!NOTE]
   > URL 的開頭必須是特定的前置詞。 如需完整清單，請參閱[考量與疑難排解](#considerations-and-troubleshooting)。
   > 
   
5. 在 [報表屬性]  群組中，選取 [資料類別目錄]  下拉式清單，然後選擇 [Web URL]  。 
   
   ![Excel 中的資料類別下拉式清單](media/power-bi-hyperlinks-in-tables/createhyperlinksnew.png)

6. 從 Power BI 服務或 Power BI Desktop，連接至或匯入此活頁簿。
7. 建立包含 [URL] 欄位的資料表視覺效果。
   
   ![在 Power BI 中建立包含 URL 欄位的資料表](media/power-bi-hyperlinks-in-tables/hyperlinksintables.gif)

## <a name="considerations-and-troubleshooting"></a>考量與疑難排解

URL 的開頭必須是下列其中一項：
- http
- https
- mailto
- ftp
- 新聞
- telnet

問：在資料表或矩陣中，我是否可以使用自訂 URL 作為超連結？    
答：否。 您可以使用連結圖示。 如果您需要針對超連結使用自訂文字，且您的 URL 清單很短，請考慮改用文字方塊。


## <a name="next-steps"></a>後續步驟
[Power BI 報表的視覺效果](../visuals/power-bi-report-visualizations.md)

[Power BI 服務中的設計工具基本概念](../fundamentals/service-basic-concepts.md)

有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)
