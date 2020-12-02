---
title: 在 SharePoint 清單上建立報表
description: 本教學課程說明如何將 SharePoint 清單資料轉換成 Power BI 報表。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 01/10/2020
LocalizationGroup: Visualizations
ms.openlocfilehash: 5347405c13f71fa0932c48eb218618b28a9f03c8
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96404517"
---
# <a name="create-a-report-on-a-sharepoint-list"></a>在 SharePoint 清單上建立報表

由於 SharePoint Online 可讓使用者輕鬆更新，許多小組與組織都使用 SharePoint Online 的清單來儲存資料。  有些時候，圖表可讓使用者更快速了解資料，而不需要查看清單本身。 在本教學課程中，我們會說明如何將 SharePoint 清單資料轉換成 Power BI 報表。

請觀看這段五分鐘的教學課程影片，或向下捲動以瀏覽逐步指示。

<iframe width="400" height="450" src="https://www.youtube.com/embed/OZO3x2NF8Ak" frameborder="0" allowfullscreen></iframe>

## <a name="part-1-connect-to-your-sharepoint-list"></a>第 1 部分：連線至 SharePoint 清單

1. 如果還沒有 SharePoint 清單，您可以下載並安裝 [Power BI Desktop](https://powerbi.microsoft.com/desktop/)。
2. 開啟 Power BI Desktop，然後在功能區的 [首頁] 索引標籤中選取 [取得資料] > [其他]。
3. 依次選取 [線上服務]、[SharePoint Online 清單]。  

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-getdata.png" alt="Screenshot shows the Get Data dialog box with Online Services selected." width="350"/>

4. 選取 [連接]。
4. 尋找包含您清單的 SharePoint Online 網站位址 (也稱為 URL)。  您通常可以在 SharePoint Online 的頁面從瀏覽窗格選取 [首頁] (或頂端的網站圖示)，然後從網頁瀏覽器的網址列複製位址來取得網站位址。

   觀看此步驟的說明影片：
   <iframe width="400" height="300" src="https://www.youtube.com/embed/OZO3x2NF8Ak?start=48&end=90" frameborder="0" allowfullscreen></iframe>

5. 在 Power BI Desktop 中，將位址貼入 [開啟] 對話方塊中的 [網站 URL] 欄位。

6. 您不一定會看到如下圖所示的 SharePoint 存取畫面。  如果沒有看到此畫面，請跳至步驟 10。  如果看到了此畫面，請選取頁面左側的 [Microsoft 帳戶]。

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-auth1.png" alt="choose Microsoft account" width="500"/>

7. 選取 [登入]，然後輸入用來登入 Microsoft 365 的使用者名稱和密碼。

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-auth2.png" alt="sign in" width="500"/>

8. 完成登入後，請選取 [連線]。

9. 在 [導覽器] 左側，在想要連線的 SharePoint 清單旁選取核取方塊。

    <img src="media/desktop-sharepoint-online-list/desktop-sharepoint-online-list-select-list.png" alt="Screenshot shows the Navigator page with BudgetRequests selected." width="450"/>

10. 選取 [載入]。  Power BI 會將清單資料載入至新的報表。

## <a name="part-2-create-a-report"></a>第 2 部分：建立報表

1. 在左側選取 **資料** 圖示，以查看 SharePoint 清單資料是否已載入。

2. 在右側的 [欄位] 窗格中，確認包含數字的清單資料行顯示總和或 Sigma 圖示。  針對任何未顯示總和或 Sigma 圖示的清單資料行，請選取 [資料表] 檢視中的資料行標頭、[模型] 索引標籤，然後視資料而定，將 [資料類型] 變更為 [十進位數] 或 [整數]。  如果系統提示您確認變更，請選取 [是]。  如果數字是特殊格式 (例如貨幣)，您也可以設定 [格式] 來加以選擇。

   觀看此步驟的說明影片：
   <iframe width="400" height="300" src="https://www.youtube.com/embed/OZO3x2NF8Ak?start=147&end=204" frameborder="0" allowfullscreen></iframe>

3. 選取左側的 **報表** 圖示。
4. 選取要進行視覺化的資料行，方法是在右側 [欄位] 窗格中選取這些資料行旁的核取方塊。

   觀看此步驟的說明影片：
   <iframe width="400" height="300" src="https://www.youtube.com/embed/OZO3x2NF8Ak?start=215&end=252" frameborder="0" allowfullscreen></iframe>

5. 如有需要，您可以變更視覺效果類型。
6. 您可以取消選取現有的視覺效果，然後在 [欄位] 窗格中選取其他資料行的核取方塊，以在相同報表中建立多個視覺效果。
7. 選取 [儲存] 以儲存報表。
