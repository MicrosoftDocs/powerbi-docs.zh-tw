---
title: 在 Power BI Desktop 中連線到 Google BigQuery 資料庫
description: 在 Power BI Desktop 中輕鬆連線到 Google BigQuery 並加以使用
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 05/08/2019
LocalizationGroup: Connect to data
ms.openlocfilehash: 7cffba9178d4eec0bfd468040b7551768aab7f1d
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96405874"
---
# <a name="connect-to-a-google-bigquery-database-in-power-bi-desktop"></a>在 Power BI Desktop 中連線到 Google BigQuery 資料庫
在 Power BI Desktop 中，您可以連線到 Google **BigQuery** 資料庫並使用基礎資料，如同 Power BI Desktop 中的任何其他資料來源。

## <a name="connect-to-google-bigquery"></a>連線到 Google BigQuery
若要連線到 Google **BigQuery** 資料庫，請從 Power BI Desktop 的 [首頁]  功能區選取 [取得資料]  。 從左側類別中選取 [資料庫]  ，然後您會看到 **Google BigQuery**。

![Google BigQuery 的 [取得資料] 對話方塊](media/desktop-connect-bigquery/connect_bigquery_01.png)

在出現的 [Google BigQuery]  視窗中，登入您的 Google BigQuery 帳戶，然後選取 [連線]  。

![登入 Google BigQuery](media/desktop-connect-bigquery/connect_bigquery_02.png)

登入後，您就會看到下列視窗指出您已通過驗證。 

![已登入 Google](media/desktop-connect-bigquery/connect_bigquery_02b.png)

成功連接後，[導覽器]  視窗隨即出現，並顯示伺服器上可用的資料，您可以從中選取一或多個要匯入 **Power BI Desktop** 並在其中使用的項目。

![來自 Google BigQuery 的資料](media/desktop-connect-bigquery/connect_bigquery_03.png)

## <a name="considerations-and-limitations"></a>考量與限制
使用 Google **BigQuery** 連接器時，有幾項限制和考量必須注意：

* Google BigQuery 連接器可以在 Power BI Desktop 和 Power BI 服務中使用。 在 Power BI 服務中，連接器可透過 Power BI 到 Google BigQuery 的雲端對雲端連線進行存取。

* 您可以將 Power BI 與 Google BigQuery **計費專案** 搭配使用。 根據預設，Power BI 會使用針對使用者所傳回清單中的第一個專案。 

  若要自訂搭配 Power BI 使用計費專案時的計費專案行為，請在 [來源] 步驟的底層 M 中指定下列選項，這可以使用 Power BI Desktop 中的 **Power Query 編輯器** 來自訂：

  ```
  Source = GoogleBigQuery.Database([BillingProject="Include-Billing-Project-Id-Here"])
  ```

  從 2020 年 9 月版本開始，我們已啟用對 [Google BigQuery Storage API](https://cloud.google.com/bigquery/docs/reference/storage) 的支援。 這項功能預設為啟用，並由稱為 "UseStorageApi" 的選擇性布林引數所控制。 某些客戶若使用細微權限，可能會遇到此功能的問題。 如果發生這種情況，您可能會看到下列錯誤訊息：

  `ERROR [HY000] [Microsoft][BigQuery] (131) Unable to authenticate with Google BigQuery Storage API. Check your account permissions`

  您可以透過調整 Storage API 的使用者權限來解決此問題。 指派這些 Storage API 權限：

  - `bigquery.readsessions.create` - 透過 BigQuery Storage API 建立新的讀取工作階段。
  - `bigquery.readsessions.getData` - 透過 BigQuery Storage API 從讀取工作階段讀取資料。
  - `bigquery.readsessions.update` - 透過 BigQuery Storage API 更新讀取工作階段。

  這些權限通常是在 BigQuery.User 角色中提供。 如需詳細資訊，請參閱 [Google BigQuery 預先定義的角色與權限](https://cloud.google.com/bigquery/docs/access-control)。
  
  如果上述步驟無法解決問題，或您想要停用儲存體 API 的支援，請將查詢變更如下：
  ```
  Source = GoogleBigQuery.Database([UseStorageApi=false])
  ```
  或者，如果已經在使用計費專案，請將查詢變更如下：
  ```
  Source = GoogleBigQuery.Database([BillingProject="Include-Billing-Project-Id-Here", UseStorageApi=false])
  ```

## <a name="next-steps"></a>後續步驟
您可以使用 Power BI Desktop 連接至各式各樣的資料。 如需有關資料來源的詳細資訊，請參閱下列資源︰

* [Power BI Desktop 是什麼？](../fundamentals/desktop-what-is-desktop.md)
* [Power BI Desktop 中的資料來源](desktop-data-sources.md)
* [使用 Power BI Desktop 合併資料並使其成形](desktop-shape-and-combine-data.md)
* [在 Power BI Desktop 中連接至 Excel 活頁簿](desktop-connect-excel.md)   
* [直接將資料輸入 Power BI Desktop 中](desktop-enter-data-directly-into-desktop.md)   
