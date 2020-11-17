---
title: 範例 Power BI 編頁報表
description: 本文會介紹如何下載及使用範例 Power BI 編頁報表。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: swgupt
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 11/10/2020
ms.openlocfilehash: cfa4b46e521079802ec87b63d6323e01213625c3
ms.sourcegitcommit: 132b3f6ba6d2b1948ddc15969d64cf629f7fb280
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94483816"
---
# <a name="sample-power-bi-paginated-reports"></a>範例 Power BI 編頁報表


[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)]

本文會提供數個範例 Power BI 編頁報表的相關資訊和連結，以供下載及探索。 這些資源會示範一般使用編頁報表的方式。

## <a name="prerequisites"></a>先決條件

- 您可在線上以現狀共用這些報表，而無需編輯。 但您需要有 Power BI Pro 授權才能執行此作業。 請註冊 [Power BI Pro 的免費試用版授權](../fundamentals/service-self-service-signup-for-power-bi.md#sign-up-for-an-individual-trial-of-power-bi-pro)。
- 您也需要存取 [Premium 容量](../admin/service-premium-what-is.md)中的 Power BI 工作區。
- 若要編輯這些報表，您必須從 Microsoft 下載中心[安裝 Power BI 報表產生器](https://aka.ms/pbireportbuilder)。
- 現在可從 GitHub 下載這些範例編頁報表了！ 您不需要有 GitHub 帳戶。 

## <a name="download-the-reports"></a>下載報表

您必須將存放庫下載為 zip 檔案，然後解壓縮，才能成功下載報表。 編頁報表為 .rdl 檔案。

1. 開啟 [Reporting Services GitHub 存放庫](https://github.com/microsoft/Reporting-Services)。
1. 選取綠色 [Code] (程式碼) 按鈕上的箭號 > [Download ZIP] (下載 ZIP)。

    :::image type="content" source="media/paginated-reports-samples/paginated-report-download-zip.png" alt-text="GitHub 存放庫的螢幕擷取畫面，包含範例 Power BI 編頁報表。":::
    
1. 開啟檔案，選取 [解壓縮全部]，然後選擇檔案的位置。 根據預設，資料夾名稱為 **Reporting-Services-master**。
1. 開啟 **Reporting-Services-master** 資料夾，然後開啟 **PaginatedReportSamples** 資料夾。

    >[!NOTE]
    >您可以刪除 **Reporting-Services-master** 資料夾中的所有其他資料夾。 這些資料夾包含了您不需要的其他範例。

1. 選取其中一個 .rdl 檔案，在 Power BI Report Builder 中開啟。
1. 現在您可以[將編頁報表發佈至 Power BI 服務](paginated-reports-save-to-power-bi-service.md)了。

## <a name="invoice"></a>Invoice

:::image type="content" source="media/paginated-reports-samples/paginated-report-invoice.png" alt-text="範例 Power BI 編頁報表發票的螢幕擷取畫面。":::


此分頁報表是獨立發票。 如果您想要可列印完美像素的發票，即適合使用這份報表。 需要顯示總銷售額，並詳細列出項目描述、數量、折扣和成本。

此範例強調建立真實發票的唯一特性，例如：  

- Tablix (資料表和矩陣下的資料區域)。 其會顯示動態產生的使用者特定內容及佈景主題。
- 放在報表主體 tablix 其每一個資料列中的矩形資料區域。
- 報表項目，例如文字方塊和線條。
- 以動態方式選取內容的報表參數。 所顯示內容會使用運算式預留位置套用至特定的主題。 

資料來源:包含在 .rdl 檔案中

## <a name="labels"></a>標籤

:::image type="content" source="media/paginated-reports-samples/paginated-report-labels.png" alt-text="編頁報表標籤的螢幕擷取畫面。":::

這是獨立的編頁報表範例。 其為多資料行報表，大小完全符合郵件標籤範本的列印版面配置。 

標籤報表很簡單，但建立編頁標籤有幾個唯一特性：

- 已定義資料行間距，固定資料行計數為 3 的 tablix。
- 在列印頁面各資料列和資料行間重複的矩形資料區域。
- 用以選取每個矩形資料區域所顯示內容的報表參數。

資料來源:包含在 .rdl 中

## <a name="mailing-letter"></a>郵寄信件

:::image type="content" source="media/paginated-reports-samples/paginated-report-letter.png" alt-text="範例 Power BI 編頁報表信件的螢幕擷取畫面。":::

這個獨立的編頁報表範例是專為建立真實郵寄信件所設計。 如果想要可列印動態內容的完美像素信件，即適合使用這份報表。

這個範例具有唯一特性，例如： 

- 矩形資料區域會放在報表主體的不同區段。 
- 用以個人化信件的圖片。 
- Tablix 資料區域 (資料表和矩陣下的資料區域)。 此 tablix 會顯示動態產生的使用者特定內容。
- 報表項目，例如文字方塊和線條。
- 以動態方式選取內容的報表參數。 所顯示內容會使用運算式預留位置套用至特定的主題。 

資料來源:包含在 .rdl 中

## <a name="transcript"></a>文字記錄

:::image type="content" source="media/paginated-reports-samples/paginated-report-transcript.png" alt-text="範例 Power BI 編頁報表文字記錄的螢幕擷取畫面。":::

如果想要可列印完美像素的文字記錄，即適合使用這份報表。 其必須包含動態內容，列出每個學生的計劃描述詳細資料和日期。

這個獨立分頁報表範例具有唯一特性，例如： 

- Tablix 資料區域 (資料表和矩陣下的資料區域)。 此 tablix 會使用巢狀資料列群組顯示動態產生的使用者特定內容。
- 矩形資料區域會放在報表主體的不同區段。
- 報表項目，例如文字方塊和線條。

資料來源:包含在 .rdl 中

## <a name="sales-performance"></a>銷售績效

:::image type="content" source="media/paginated-reports-samples/paginated-report-sales-performance.png" alt-text="範例 Power BI 編頁報表 [銷售業績] 的螢幕擷取畫面。":::

國家/地區銷售績效是獨立的編頁報表範例。 如果想要可列印完美像素的發票，以查看總銷售額和詳細資料，即適合使用這份報表。 展示的功能包括：

- 使用參數展開資料表的詳細資料。
- 頁首和頁尾。
- 使用運算式預留位置的報表項目，例如文字方塊、線條和矩形。
- 資料橫條。
- 趨勢線。
- 量測計面板。

資料來源:包含在 .rdl 中
  
## <a name="next-steps"></a>後續步驟

[檢視 Power BI 服務中的編頁報表](../consumer/paginated-reports-view-power-bi-service.md)

有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)
