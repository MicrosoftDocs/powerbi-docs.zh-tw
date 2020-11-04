---
title: 在 Power BI 報表產生器中規劃報表
description: Power BI Report Builder 可讓您建立許多種類的編頁報表。 若要建立有用且易於了解的報表，最好先進行規劃。
ms.date: 07/25/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 79113505-1ce8-4f8c-9260-d861838f7813
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3f075372436723cd8952decd68ecc764bd6e92a0
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/04/2020
ms.locfileid: "93297743"
---
# <a name="planning-a-report-in-power-bi-report-builder"></a>在 Power BI 報表產生器中規劃報表

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

Power BI Report Builder 可讓您建立許多種類的編頁報表。 例如，您可以建立顯示摘要或詳細銷售資料、行銷和銷售趨勢、營運報表或儀表板的報表。 您也可以建立利用豐富文字格式 (例如銷售訂單、產品目錄或正式書信) 的報表。 所有這些報表都是使用報表產生器中相同基本建置組塊的不同組合而建立。 若要建立有用且易於了解的報表，先進行規劃是有效的方法。 以下是開始作業前可能要考量的部分事項：  
  
## <a name="in-what-format-do-you-want-the-report-to-appear"></a>您想要以何種格式來呈現報表？
  
您可以在瀏覽器 (例如 Power BI 入口網站) 中線上轉譯報表，或將其匯出為其他格式 (例如 Excel、Word 或 PDF)。 報表所採用的最終格式是一項重要的考量，因為並非所有匯出格式都可以提供所有功能。 
  
## <a name="in-what-structure-do-you-want-to-present-the-data"></a>您想要以何種結構來呈現資料？
  
您可以選擇表格式、矩陣 (類似交叉分析或樞紐分析表報表)、圖表、自由形式結構，或上述任何組合來展示資料。 如需詳細資訊，請參閱 [Power BI 報表產生器中的資料表、矩陣和清單](report-builder-tables-matrices-lists.md)。  
  
## <a name="how-do-you-want-your-report-to-look"></a>您想要如何呈現報表？
  
報表產生器提供許多報表項目，可加入報表使其更易於讀取、反白顯示主要資訊、協助您的對象導覽報表等等。 知道報表將以何種方式呈現，有助於判斷您是否需要文字方塊、矩形、影像和線條等報表項目。 您可能也想要顯示或隱藏項目、加入文件引導模式、包含鑽研報表或子報表，或連結到其他報表。   
  
## <a name="should-the-data-be-filtered"></a>應該篩選資料嗎？
  
您可以將報表的範圍縮小為特定的使用者或地點，或限制為特定的時間週期。 若要篩選報表資料，請使用參數僅擷取及顯示所要的資料。 如需詳細資訊，請參閱 [Power BI 報表產生器中的報表參數](paginated-reports-parameters.md)。  
  
## <a name="do-you-need-to-create-calculations"></a>您需要建立計算嗎？ 
  
有時候，您的資料來源和資料集並不包含完全符合報表需求的欄位。 在這種情況下，您可能需要建立自己的導出欄位。 例如，您可以將單價乘以數量以取得明細項目銷售量。 您也可使用運算式來提供條件式格式化和其他進階功能。 如需詳細資訊，請參閱 [Power BI 報表產生器中的運算式](report-builder-expressions.md)。  
  
## <a name="do-you-want-to-hide-report-items-initially"></a>一開始要隱藏報表項目嗎？
  
請考慮是否要在初次執行報表時隱藏報表項目，包括資料區、群組和資料行。 例如，可以一開始先展示摘要資料表，然後再向下鑽研到詳細資料。 
  
## <a name="how-are-you-going-to-deliver-your-report"></a>要以何種方式傳遞報表？  
  
您可以將報表儲存至本機電腦，繼續在本機使用或執行，以滿足您自己的資訊需求。 不過，若要與其他人共用您的報表，您需要將報表儲存至 Power BI。 將其儲存至 Power BI，可讓其他人在需要時執行。 或者您也可以設定訂閱，並將報表透過電子郵件傳遞給其他人。 如果想要，可以用特定的匯出格式傳遞報表。 
  
## <a name="next-steps"></a>後續步驟

- [什麼是 Power BI Premium 中的編頁報表？](paginated-reports-report-builder-power-bi.md)
