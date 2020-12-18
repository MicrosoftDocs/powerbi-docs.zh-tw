---
title: 使用 Power Automate 匯出報表並以電子郵件傳送
description: 在此文章中，您會使用 Power Automate，在各種支援的案例中，以各種支援的格式自動匯出 Power BI 報表並進行散發。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 12/10/2020
LocalizationGroup: Get started
ms.openlocfilehash: 45bccbefc6e499375d33aa049ead8a6c6e47bc8c
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2020
ms.locfileid: "97098586"
---
# <a name="export-and-email-a-power-bi-report-with-power-automate"></a>使用 Power Automate 匯出 Power BI 報表並以電子郵件傳送

透過 [Power Automate](/power-automate/getting-started)，您可以在各種案例中，以各種格式自動匯出 Power BI 報表並進行散發。 在此文章中，您將從頭開始建立自己的流程。 您可以使用 [針對 Power BI 報表匯出至檔案] 動作，透過電子郵件自動散發 Power BI 報表。

:::image type="content" source="media/service-automate-power-bi-report-export/automate-power-bi-report-overview.png" alt-text="匯出報表並以電子郵件傳送的 Power Automate 步驟。":::

## <a name="prerequisites"></a>Prerequisites  

若要遵循此做法，請確定您有：

- 您的 Power BI 租用戶中至少有一個工作區受保留容量所支援。 此容量可以是 A1/EM1 - A6/P3 SKU 中的任何一個。 請前往 [Power BI Premium 中的保留容量](../admin/service-premium-what-is.md)閱讀更多內容。
- 存取 Power Automate 中的標準連接器，其隨附於任何 Office 365 訂閱。

## <a name="create-a-flow-from-scratch"></a>從頭建立流程 

在此工作中，您將從頭開始建立簡單的流程。 此流程每週都會將 Power BI 報表匯出為 PDF，並將其附加至電子郵件以進行傳送。  

1. 登入 Power Automate (flow.microsoft.com)。
2. 選取 [建立] > [預定流程]。 

    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-scheduled-flow-2.png" alt-text="在 Power Automate 中建立預定流程。":::

3. 在 [建置預定流程] 中，為流程命名。 
4. 在 [執行此流程] 中，選取流程的開始日期和時間以及重複的頻率。
5. 在 [在這幾天內] 中，選取您希望流程執行的日期，然後選取 [建立]。

    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-build-flow-5.png" alt-text="Power Automate，排程流程。":::

6. 在 [週期] 中，選取 [顯示進階選項]，然後在 [在這幾小時內] 和 [在這幾分鐘內] 中輸入值，以針對您的流程設定要執行的特定時間。
 
    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-recurrence-6.png" alt-text="在 Power Automate 中設定週期。":::

7. 選取 [新增步驟]。
8. 在 [選擇動作] 中，搜尋 **Power BI**，然後選取 [針對 Power BI 報表匯出至檔案]。
 
    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-choose-action-8.png" alt-text="在 Power Automate 中選擇動作。":::

9. 在 [針對 Power BI 報表匯出至檔案] 中，從下拉式清單選取 [工作區] 和 [報表]。
10. 針對您的 Power BI 報表選取所需的 [匯出格式]。
 
    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-export-file-10.png" alt-text="在 Power Automate 中選取匯出格式。":::

11. (選擇性) 在 [頁面 pageName -1] 欄位中，指定要匯出的特定頁面。 請注意，頁面名稱參數與顯示頁面名稱不同。 瀏覽至 Power BI 服務中的頁面，然後複製 URL 的最後部分，以尋找頁面名稱。
 
     :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-copy-url-11.png" alt-text="選取 URL 中的窗格名稱。":::

12. (選擇性) 在 [頁面書籤名稱] 欄位中，指定要顯示的特定書籤。 如同頁面名稱參數，您可以在報表 URL 中尋找書籤名稱參數。 您可以針對 Power BI 報表指定其他參數。 若要尋找這些參數的詳細描述，請參閱 [Power BI REST API 的連接器參考](/connectors/powerbi/#export-to-file-for-power-bi-reports)。

    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-bookmark-url-12.png" alt-text="選取 URL 中的書籤名稱。":::

13. 選取 [新增步驟]。
14. 在 [選擇動作] 中，搜尋 **Outlook**，然後選取 [傳送電子郵件 (V2)]。
15. 在 [傳送電子郵件 (V2)] 中，填妥電子郵件的 [收件人]、[主旨] 和 [本文] 欄位。
16. 選取 [顯示進階選項]。 在 [附件名稱 -1] 中，輸入附件的名稱。 在檔案名稱中，新增符合您所需 **匯出格式** 的副檔名 (例如 .PDF)。
17. 在 [附件內容] 中，選取 [檔案內容] 以附加您匯出的 Power BI 報表。  
 
    :::image type="content" source="media/service-automate-power-bi-report-export/automate-report-send-email-17.png" alt-text="選取您已匯出且要以電子郵件傳送的報表。":::

18. 當您完成時，選取 [下一步] 或 [儲存]。 Power Automate 會建立及評估流程，並讓您知道是否找到錯誤。
1. 若發生錯誤，請選取 [編輯流程] ****  加以修正。 否則，選取 [返回] 箭頭以檢視流程詳細資料，並執行新流程。
    當您執行流程時，Power Automate 會以指定的格式匯出 Power BI 報表，並依排程以電子郵件附件形式傳送該報表。  

## <a name="next-steps"></a>後續步驟

- [將 Power BI 資料警示與 Power Automate 整合](service-flow-integration.md)
- [開始使用 Power Automate](/power-automate/getting-started/)
- 有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)
