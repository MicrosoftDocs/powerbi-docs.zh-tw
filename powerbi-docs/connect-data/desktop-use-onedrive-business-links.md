---
title: 在 Power BI Desktop 中使用商務用 OneDrive
description: 在 Power BI Desktop 中使用商務用 OneDrive
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 05/27/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 70607632dd4e93d1b0d5e53f19ef697c6599128d
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410842"
---
# <a name="use-onedrive-for-business-links-in-power-bi-desktop"></a>在 Power BI Desktop 中使用商務用 OneDrive
許多人都將 Excel 活頁簿儲存在可與 Power BI Desktop 完美搭配的商務用 OneDrive 中。 有了 Power BI Desktop，您可以使用儲存在商務用 OneDrive 中的 Excel 檔案線上連結來建立報表和視覺效果。 您可以使用商務用 OneDrive 群組帳戶，或您個人的商務用 OneDrive 帳戶。

從商務用 OneDrive 取得線上連結需要幾個特定步驟。 下列各節說明這些步驟，可讓您在不同電腦中，與同事共用群組中的檔案連結。

## <a name="get-a-link-from-excel"></a>從 Excel 取得連結
1. 使用瀏覽器瀏覽至您商務用 OneDrive 位置。 以滑鼠右鍵按一下要使用的檔案，並選取 [在 Excel 中開啟]。
   
   > [!NOTE]
   > 您的瀏覽器介面看起來可能不完全與下圖相同。 您可以透過許多方法，針對在您商務用 OneDrive 瀏覽器介面中的檔案選取 [在 Excel 中開啟]。 您可以使用可讓您在 Excel 中開啟檔案的任何選項。
   
   ![瀏覽器中 OneDrive 的螢幕擷取畫面，其中顯示 [在 Excel 中開啟] 選項。](media/desktop-use-onedrive-business-links/odb-links_02.png)

2. 在 Excel 中，選取 [檔案] > [資訊]，然後選取 [複製路徑] 按鈕，如下圖所示。
   
   ![[資訊] 功能表的螢幕擷取畫面，其中顯示 [複製路徑] 按鈕選取項目。](media/desktop-use-onedrive-business-links/onedrive-copy-path.png)

## <a name="use-the-link-in-power-bi-desktop"></a>在 Power BI Desktop 中使用連結
在 Power BI Desktop 中，您可以使用您剛才複製到剪貼簿的連結。 請採取下列步驟：

1. 在 Power BI Desktop 中，選取 [取得資料] > [Web]。
   
   ![Power BI Desktop 中 [取得資料] 功能區的螢幕擷取畫面，其中顯示 [Web] 選取項目。](media/desktop-use-onedrive-business-links/power-bi-web-link-onedrive.png)
2. 選取 [基本] 選項後，將連結貼入 [從 Web] 對話方塊。
3. 移除連結結尾的 *?web=1* 字串，讓 Power BI Desktop 可正確地瀏覽至您的檔案，然後選取 [確定]。
   
    ![[從 Web] 對話方塊的螢幕擷取畫面，其中顯示如何從 [URL] 欄位移除字串。](media/desktop-use-onedrive-business-links/power-bi-web-link-confirmation.png) 
4. 如果 Power BI Desktop 提示輸入認證，請選擇 [Windows] (適用於內部部署 SharePoint 網站) 或 [組織帳戶] (適用於 Microsoft 365 或商務用 OneDrive 網站)。
   
   ![Power BI Desktop 認證提示的螢幕擷取畫面，其中顯示 [Windows] 或 [組織帳戶] 選取項目。](media/desktop-use-onedrive-business-links/odb-links_06.png)

   [導覽器] 視窗隨即顯示，可讓您從在 Excel 活頁簿中找到的資料表、工作表和範圍清單進行選取。 您可以從該處使用商務用 OneDrive 檔案，如同任何其他 Excel 檔案。 您可以建立報表並將其用於資料集，如同使用任何其他資料來源。

> [!NOTE]
> 若要使用商務用 OneDrive 檔案作為 Power BI 服務中的資料來源，並為該檔案啟用 [服務重新整理]，請確定您在進行重新整理的設定時選取 [OAuth2] 作為 [驗證方法]。 否則您可能會在嘗試連線或重新整理時遇到錯誤 (例如「無法更新資料來源認證」)。 選取 **OAuth2** 作為驗證方法，就能解決該項認證錯誤。
>
