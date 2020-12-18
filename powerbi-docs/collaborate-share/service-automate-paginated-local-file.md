---
title: 使用 Power Automate 將編頁報表儲存到本機資料夾
description: 在此文章中，您會使用範本來設定將編頁報表以所需的格式週期性地匯出到您的檔案系統。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 12/08/2020
LocalizationGroup: Get started
ms.openlocfilehash: a30f0df972c375af4fb284ce3bba5372870d6efb
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2020
ms.locfileid: "97098584"
---
# <a name="save-a-power-bi-paginated-report-to-a-local-folder--with-power-automate"></a>使用 Power Automate 將 Power BI 編頁報表儲存到本機資料夾

透過 [Power Automate](/power-automate/getting-started)，您可以將 Power BI 編頁報表以各種支援的格式自動匯出，並分散至各種案例。 在此文章中，您會使用範本來設定將編頁報表以所需的格式週期性地匯出到您的檔案系統。 若這是您第一次在 Power Automate 流程中使用 [Export to File for Paginated Reports] \(針對編頁報表匯出至檔案\) 動作，請參閱＜必要條件＞。

:::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-overview.png" alt-text="設定編頁報表的週期性匯出。":::

在尋找 Power BI 編頁報表的其他 Power Automate 範本嗎？ 請參閱[使用 Power Automate 匯出 Power BI 編頁報表](service-automate-paginated-integration.md)。

## <a name="prerequisites"></a>Prerequisites  

若要遵循此做法，請確定您有：

- 您的 Power BI 租用戶中至少有一個工作區受保留容量所支援。 此容量可以是 A4/P1 – A6/P3 SKU 中的任何一個。 深入了解 [Power BI Premium 中編頁報表的保留容量](../admin/service-premium-what-is.md#paginated-reports)。
- 存取 Power Automate 中的標準連接器，其隨附於任何 Office 365 訂閱。

## <a name="save-a-power-bi-paginated-report-to-a-local-folder"></a>將 Power BI 編頁報表儲存到本機資料夾

1. 選取 [Save a Power BI paginated report to a local file system] \(將 Power BI 編頁報表儲存到本機檔案系統\) 範本。 請務必登入 Power BI 並連線到本機檔案系統。 選取 [繼續]。 

    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-save-report-local-file-1.png" alt-text="將 Power BI 編頁報表儲存到本機檔案系統。":::

2. 您可能需要選取 [新增新連線] 來連線到您的檔案系統。 
1. 輸入 [連線名稱] 與所需 [根資料夾] 的路徑，然後輸入您的 [使用者名稱] 與 [密碼] 來驗證。 如果您是使用內部部署的資料閘道，請從下拉式清單中選取一個 **閘道**。

    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-set-file-system-2.png" alt-text="輸入 [連線名稱] 與 [根資料夾]。":::
 
3. 若要設定流程的 [週期] 頻率，請從 [頻率] 下拉式清單中選取選項，然後輸入所需的 [間隔] 值。  

    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-recurrence-frequency-3.png" alt-text="為流程選取週期頻率。":::

4. 您也可以選擇性地選取 [顯示進階選項]。 設定其他 [週期] 參數，例如 [時區]、[開始時間]、[在這幾天內]、[在這幾小時內]，以及 [在這幾分鐘內]。 
 
    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-recurrence-advanced-4.png" alt-text="設定週期的進階選項。":::

5. 在 [工作區] 方塊中，選取保留容量中報表所在的工作區。 在 [報表] 方塊中，選取工作區中您想要匯出的編頁報表。 在 [匯出格式] 方塊中，選取所需的匯出格式。 您可以選擇指定編頁報表的參數。 若要查看參數的詳細描述，請參閱 [Power BI REST API 的連接器參考](/connectors/powerbi/#export-to-file-for-paginated-reports)。  
 
    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-select-workspace-report-5.png" alt-text="選取工作區與報表。":::

6. 在 [建立檔案] 對話方塊的 [資料夾路徑] 中，選取您要匯出編頁報表的目標資料夾。
 
    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-create-file-6.png" alt-text="選取您要匯出編頁報表的目標資料夾":::

7. Power Automate 會自動為您產生 [檔案名稱] 與 [檔案內容]。 您可以修改 [檔案名稱]，但請保留動態產生的 [檔案內容] 值。
8. 當您完成時，請選取 [下一步] 或 [儲存]。 Power Automate 會建立並評估流程。
9. 如果 Power Automate 找到錯誤，請選取 [編輯流程] 來加以修正。 否則，請選取 [上一步] 箭號以檢視流程詳細資料，並執行新流程。
10. 當您執行流程時，Power Automate 會將指定格式的編頁報表匯出至您檔案系統中的選取資料夾。

    :::image type="content" source="media/service-automate-paginated-local-file/paginated-local-file-exported-10.png" alt-text="Power Automate 以指定格式匯出編頁報表。":::

## <a name="next-steps"></a>後續步驟

- [使用 Power Automate 匯出 Power BI 編頁報表](service-automate-paginated-integration.md)
- [開始使用 Power Automate](/power-automate/getting-started/)
- 有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)

