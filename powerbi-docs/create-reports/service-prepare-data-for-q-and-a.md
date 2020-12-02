---
title: 讓 Excel 資料適用於 Power BI 的問與答
description: 如何讓資料適用於 Power BI 的問與答
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 05/13/2019
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 41672fa809544198a053ae41f935e890d83cfa72
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96388095"
---
# <a name="make-excel-data-work-well-with-qa-in-power-bi"></a>讓 Excel 資料適用於 Power BI 的問與答
如果您是建立資料模型的人員，或要建立搭配 Power BI 使用的 Excel 活頁簿，請繼續閱讀...

在 Power BI 中，問與答可搜尋結構化的資料，並為您的問題選擇適當的視覺效果，就是這一點讓它成為大家愛用的工具。   

問與答可以處理任何已上傳的 Excel 檔案 (有資料表、範圍或包含 PowerPivot 模型)，但是最佳化和資料清除執行愈多次，問與答的效能就愈穩固。  如果您計劃根據您的資料集來共用報表和儀表板，您會希望同事能輕鬆地詢問問題並取得優質的答案。

## <a name="how-qa-works-with-excel"></a>問與答在 Excel 的運作方式
問與答有一組可在您的資料中運作的功能，可了解核心自然語言。 它會搜尋 Excel 資料表、資料行和導出欄位名稱之內容相關的關鍵字。 它也有內建如何篩選、排序、彙總、群組和顯示資料的相關知識。 

例如，在一個名為「銷售」的 Excel 資料表，其資料行為「產品」、「月」、「單位銷售」、「銷售毛額」和「利潤」，您可以詢問有關任何這些實體的問題。  您可以要求顯示銷售額、各月份的總計收益、依單位銷售排序產品等等。 深入了解[在儀表板和報表中使用問與答](power-bi-tutorial-q-and-a.md)以及[問與答查詢中可以指定的視覺效果類型](../visuals/power-bi-visualization-types-for-reports-and-q-and-a.md)。

## <a name="prepare-an-excel-dataset-for-qa"></a>準備適用於問與答的 Excel 資料集
問與答依賴資料表、資料行和導出欄位的名稱，藉此回應特定資料的問題，這表示您如何在活頁簿中命名實體會相當重要！

以下是在您的活頁簿中善加利用問與答的一些秘訣。

* 請確定您的資料位於 Excel 資料表中。 以下是[如何建立 Excel 資料表](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-e81aa349-b006-4f8a-9806-5af9df0ac664)的說明.
* 請確定您的資料表、資料行和導出欄位的名稱在自然的談話中合理。
  
  例如，如果您有包含銷售資料的資料表時，請將資料表命名為「銷售額」。 「年」、「產品」、「銷售代表」和「金額」等資料行名稱可適用於問與答。

* 如果您的活頁簿有 PowerPivot 資料模型，您就可以更進一步地最佳化。 深入了解我們內部團隊之自然語言專家的 [Demystifying Power BI Q&A part 2](https://powerbi.microsoft.com/blog/demystifying-power-bi-q-amp-a-part-2/) (揭密 Power BI 問與答第 2 部分)。

* 在 Power BI Desktop 中開啟資料集並建立新的資料行、建立量值、串連欄位以建立唯一的值、依類型 (例如日期、字串、地理位置、影像、URL) 分類資料等。

## <a name="next-steps"></a>後續步驟

- [取用者問與答](../consumer/end-user-q-and-a.md)  
- [在儀表板和報表中使用問與答](power-bi-tutorial-q-and-a.md)
- [準備適用於問與答的內部部署資料集](service-q-and-a-direct-query.md)   
- [取得 Power BI 的資料](../connect-data/service-get-data.md)  

有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)
