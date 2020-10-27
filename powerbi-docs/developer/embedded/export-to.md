---
title: 匯出 Power BI 報表 API
description: 了解如何匯出內嵌 Power BI 報表
author: KesemSharabi
ms.author: kesharab
ms.topic: how-to
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 10/01/2020
ms.openlocfilehash: f997547bb61bf203f7806dbe68d45beb29c6538b
ms.sourcegitcommit: 59d07be9c3e4a2067f6d42c3002a194371bc4341
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2020
ms.locfileid: "92116446"
---
# <a name="export-power-bi-report-to-file-preview"></a>將 Power BI 報表匯出至檔案 (預覽)

`exportToFile` API 可讓您使用 REST 呼叫來匯出 Power BI 報表。 支援下列檔案格式：
* **.pptx** (PowerPoint)
* **.pdf**
* **.png**
    * 多頁報表在匯出為 .png 時會壓縮成 .zip 檔案
    * .zip 中的每個檔案都代表一張報表頁面
    * 頁面名稱與[取得頁面](/rest/api/power-bi/reports/getpages) \(英文\) 或[取得群組中的頁面](/rest/api/power-bi/reports/getpagesingroup) \(英文\) API 的傳回值相同

## <a name="usage-examples"></a>使用範例

您可以透過各種方式來使用匯出功能。 以下是一些範例︰

* **[傳送至列印] 按鈕** - 在您的應用程式中，建立按一下以觸發匯出作業的按鈕。 作業可以將已檢視的報表匯出為 .pdf 或 .pptx，當完成時，使用者會以下載項目的形式接收檔案。 您可以使用書籤，將報表以特定狀態匯出，包括已設定的篩選條件、交叉分析篩選器與其他設定。 因為 API 是非同步的，所以檔案可能需要一些時間才能使用。

* **電子郵件附件** - 以設定的間隔傳送自動電子郵件，並附加 .pdf 報表。 若要將每週報表自動傳送給主管，這個案例就很有用。

## <a name="using-the-api"></a>使用 API

使用 API 之前，請確認已啟用下列[系統管理租用戶設定](../../admin/service-admin-portal.md#tenant-settings)：
* **將報表匯出成 PowerPoint 簡報或 PDF 文件** - 預設為啟用。
* **將報表匯出為影像檔** - 只有 *.png* 才需要，預設停用。

該 API 是非同步的。 呼叫 [exportToFile](/rest/api/power-bi/reports/exporttofile) \(英文\) API 時，其會觸發匯出作業。 觸發匯出作業之後，請使用[輪詢](/rest/api/power-bi/reports/getexporttofilestatus) \(英文\) 來追蹤作業，直到完成為止。

在輪詢期間，API 會傳回代表已完成之工作量的數字。 每個匯出作業中的工作是根據報表所擁有的頁數來計算。 所有頁面都具有相同的權數。 例如，如果您要匯出包含 10 個頁面的報表，而輪詢傳回 70，這表示 API 已處理匯出作業中 10 個頁面的 7 個頁面。

當匯出完成時，輪詢 API 呼叫會傳回 [Power BI URL](/rest/api/power-bi/reports/getfileofexporttofile) \(英文\) 來取得檔案。 該 URL 在 24 小時內有效。

## <a name="supported-features"></a>支援的功能

### <a name="selecting-which-pages-to-print"></a>選取要列印的頁面

根據[取得頁面](/rest/api/power-bi/reports/getpages) \(英文\) 或[取得群組中的頁面](/rest/api/power-bi/reports/getpagesingroup) \(英文\) 傳回值，指定您要列印的頁面。 您也可以指定您要匯出的頁面順序。

### <a name="bookmarks"></a>書籤

[書籤](../../consumer/end-user-bookmarks.md)可用來以特定設定儲存報表，包括已套用的篩選條件與報表視覺效果的狀態。 您可以透過兩種方式，使用 [exportToFile](https://docs.microsoft.com/rest/api/power-bi/reports/exporttofile) \(英文\) API，以程式設計方式匯出報表的書籤：

* **匯出現有的書籤**

    若要匯出現有的[報表書籤](../../consumer/end-user-bookmarks.md#report-bookmarks)，請使用 `name` 屬性，此為您可以使用[書籤 JavaScript API](https://github.com/Microsoft/PowerBI-JavaScript/wiki/Bookmarks) \(英文\) 來取得的唯一 (區分大小寫) 識別碼。

* **匯出報表的狀態**

    若要匯出報表的目前狀態，請使用 `state` 屬性。 例如，您可以使用書籤的 `bookmarksManager.capture` 方法來擷取特定使用者對報表所作的變更，然後使用 `capturedBookmark.state`，將其以目前狀態匯出。

>[!NOTE]
>不支援[個人書籤](../../consumer/end-user-bookmarks.md#personal-bookmarks)與[永續性篩選](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/) \(英文\)。

### <a name="authentication"></a>驗證

您只能以使用者 (或主要使用者) 或者[服務主體](embed-service-principal.md)來進行驗證。

### <a name="row-level-security-rls"></a>資料列層級安全性 (RLS)

使用[資料列層級安全性 (RLS)](embedded-row-level-security.md)，您就可以匯出顯示只有特定使用者才看得到之資料的報表。 例如，如果您要匯出以區域角色定義的銷售報表，您可以透過程式設計方式篩選報表，以便只顯示特定區域。

若要使用 RLS 匯出，您也必須有下列權限：
* 報表所連接之資料集的寫入和再次共用權限
* 如果報表位於 v1 工作區上，您必須是工作區管理員
* 若報表位於 v2 工作區上，則您必須是該工作區的成員或管理員

### <a name="data-protection"></a>資料保護

.pdf 和 .pptx 格式支援[敏感度標籤](../../admin/service-security-sensitivity-label-overview.md)。 如果將具有敏感度標籤的報表匯出為 .pdf 或 .pptx，則所匯出檔案會顯示有敏感度標籤的報表。

具有敏感度標籤的報表無法使用[服務主體](embed-service-principal.md)匯出為 .pdf 或 .pptx。

### <a name="localization"></a>Localization

使用 `exportToFile` API 時，您可以傳遞所需的地區設定。 當地語系化設定會影響報表的顯示方式，例如，根據選取的地區設定來變更格式設定。

## <a name="concurrent-requests"></a>並行要求數

`exportToFile` 支援並行匯出作業要求。 下表顯示您可以同時執行的作業數目，視您的報表所在的 SKU 而定。 並行要求會參考報表頁面。 例如，在 A6 SKU 上的一個匯出要求中，將同時處理 20 頁。 這與傳送 20 個匯出要求 (每個頁面一個) 的時間大致相同。

超過其並行要求數目的作業不會終止。 例如，如果您在 A1 SKU 中匯出三個頁面，第一個作業將會執行，而後面兩個則會等候接下來的兩個執行循環。

|Azure SKU  |Office SKU  |並行報表頁面上限  |
|-----------|------------|-----------|
|A1         |EM1         |1          |
|A2         |EM2         |2          |
|A3         |EM3         |3          |
|A4         |P1          |6          |
|A5         |P2          |12         |
|A6         |P3          |24         |

## <a name="limitations"></a>限制

* 您要匯出的報表必須位於 Premium 或 Embedded 容量上。
* 您要匯出之報表的資料集必須位於 Premium 或 Embedded 容量上。
* 針對公開預覽版，每小時匯出的 Power BI 報表頁面數目限制為每容量 50 個。
* 匯出的報表不能超過 250 MB 的檔案大小。
* 匯出為 .png 時，不支援敏感性標籤。
* 匯出的報表可有 50 頁。 如果報表包含更多頁面，則 API 會傳回錯誤並取消匯出作業。
* 不支援[個人書籤](../../consumer/end-user-bookmarks.md#personal-bookmarks)與[永續性篩選](https://powerbi.microsoft.com/blog/announcing-persistent-filters-in-the-service/) \(英文\)。
* 不支援下面所列的 Power BI 視覺效果。 匯出包含這些視覺效果的報表時，包含這些視覺效果的報表部分將不會轉譯，而且會顯示錯誤符號。
    * 未經認證的 Power BI 視覺效果
    * R 視覺效果
    * PowerApps
    * Python 視覺效果
    * Visio

## <a name="code-examples"></a>程式碼範例

當您建立匯出作業時，有三個要遵循的步驟：

1. [傳送匯出要求](#step-1---sending-an-export-request)。
2. [輪詢](#step-2---polling)。
3. [取得檔案](#step-3---getting-the-file)。
4. [使用檔案資料流](#step-4---using-the-file-stream)。

此節提供每個步驟的範例。

### <a name="step-1---sending-an-export-request"></a>步驟 1 - 傳送匯出要求

第一個步驟是傳送匯出要求。 在此範例中，會針對特定頁面傳送匯出要求。

```csharp
private async Task<string> PostExportRequest(
    Guid reportId,
    Guid groupId,
    FileFormat format,
    IList<string> pageNames = null /* Get the page names from the GetPages REST API */)
{
    var powerBIReportExportConfiguration = new PowerBIReportExportConfiguration
    {
        Settings = new ExportReportSettings
        {
            Locale = "en-us",
        },
        // Note that page names differ from the page display names
        // To get the page names use the GetPages REST API
        Pages = pageNames?.Select(pn => new ExportReportPage(Name = pn)).ToList(),
    };

    var exportRequest = new ExportReportRequest
    {
        Format = format,
        PowerBIReportConfiguration = powerBIReportExportConfiguration,
    };

    // The 'Client' object is an instance of the Power BI .NET SDK
    var export = await Client.Reports.ExportToFileInGroupAsync(groupId, reportId, exportRequest);

    // Save the export ID, you'll need it for polling and getting the exported file
    return export.Id;
}
```

### <a name="step-2---polling"></a>步驟 2 - 輪詢

在您傳送匯出要求之後，請使用輪詢來識別您要等候的匯出檔案何時就緒。

```csharp
private async Task<HttpOperationResponse<Export>> PollExportRequest(
    Guid reportId,
    Guid groupId,
    string exportId /* Get from the PostExportRequest response */,
    int timeOutInMinutes,
    CancellationToken token)
{
    HttpOperationResponse<Export> httpMessage = null;
    Export exportStatus = null;
    DateTime startTime = DateTime.UtcNow;
    const int c_secToMillisec = 1000;
    do
    {
        if (DateTime.UtcNow.Subtract(startTime).TotalMinutes > timeOutInMinutes || token.IsCancellationRequested)
        {
            // Error handling for timeout and cancellations 
            return null;
        }

        // The 'Client' object is an instance of the Power BI .NET SDK
        httpMessage = await Client.Reports.GetExportToFileStatusInGroupWithHttpMessagesAsync(groupId, reportId, exportId);
        exportStatus = httpMessage.Body;

        // You can track the export progress using the PercentComplete that's part of the response
        SomeTextBox.Text = string.Format("{0} (Percent Complete : {1}%)", exportStatus.Status.ToString(), exportStatus.PercentComplete);
        if (exportStatus.Status == ExportState.Running || exportStatus.Status == ExportState.NotStarted)
        {
            // The recommended waiting time between polling requests can be found in the RetryAfter header
            // Note that this header is not always populated
            var retryAfter = httpMessage.Response.Headers.RetryAfter;
            var retryAfterInSec = retryAfter.Delta.Value.Seconds;
            await Task.Delay(retryAfterInSec * c_secToMillisec);
        }
    }
    // While not in a terminal state, keep polling
    while (exportStatus.Status != ExportState.Succeeded && exportStatus.Status != ExportState.Failed);

    return httpMessage;
}
```

### <a name="step-3---getting-the-file"></a>步驟 3 - 取得檔案

一旦輪詢傳回 URL，請使用此範例來取得已接收的檔案。

```csharp
private async Task<ExportedFile> GetExportedFile(
    Guid reportId,
    Guid groupId,
    Export export /* Get from the PollExportRequest response */)
{
    if (export.Status == ExportState.Succeeded)
    {
        // The 'Client' object is an instance of the Power BI .NET SDK
        var fileStream = await Client.Reports.GetFileOfExportToFileAsync(groupId, reportId, export.Id);
        return new ExportedFile
        {
            FileStream = fileStream,
            FileSuffix = export.ResourceFileExtension,
        };
    }
    return null;
}

public class ExportedFile
{
    public Stream FileStream;
    public string FileSuffix;
}
```

### <a name="step-4---using-the-file-stream"></a>步驟 4 - 使用檔案資料流

當您有檔案資料流時，您可以使用最符合您需求的方法來加以處理。 例如，您可以使用電子郵件來加以傳送，或是將其用來下載匯出的報表。

### <a name="end-to-end-example"></a>端對端範例

這是匯出報表的端對端範例。 此範例包含下列階段：
1. [傳送匯出要求](#step-1---sending-an-export-request)。
2. [輪詢](#step-2---polling)。
3. [取得檔案](#step-3---getting-the-file)。

```csharp
private async Task<ExportedFile> ExportPowerBIReport(
    Guid reportId,
    Guid groupId,
    FileFormat format,
    int pollingtimeOutInMinutes,
    CancellationToken token,
    IList<string> pageNames = null  /* Get the page names from the GetPages REST API */)
{
    const int c_maxNumberOfRetries = 3; /* Can be set to any desired number */
    const int c_secToMillisec = 1000;
    try
    {
        Export export = null;
        int retryAttempt = 1;
        do
        {
            var exportId = await PostExportRequest(reportId, groupId, format, pageNames);
            var httpMessage = await PollExportRequest(reportId, groupId, exportId, pollingtimeOutInMinutes, token);
            export = httpMessage.Body;
            if (export == null)
            {
                // Error, failure in exporting the report
                return null;
            }
            if (export.Status == ExportState.Failed)
            {
                // Some failure cases indicate that the system is currently busy. The entire export operation can be retried after a certain delay
                // In such cases the recommended waiting time before retrying the entire export operation can be found in the RetryAfter header
                var retryAfter = httpMessage.Response.Headers.RetryAfter;
                if(retryAfter == null)
                {
                    // Failed state with no RetryAfter header indicates that the export failed permanently
                    return null;
                }

                var retryAfterInSec = retryAfter.Delta.Value.Seconds;
                await Task.Delay(retryAfterInSec * c_secToMillisec);
            }
        }
        while (export.Status != ExportState.Succeeded && retryAttempt++ < c_maxNumberOfRetries);

        if (export.Status != ExportState.Succeeded)
        {
            // Error, failure in exporting the report
            return null;
        }

        var exportedFile = await GetExportedFile(reportId, groupId, export);

        // Now you have the exported file stream ready to be used according to your specific needs
        // For example, saving the file can be done as follows:
        /*
            var pathOnDisk = @"C:\temp\" + export.ReportName + exportedFile.FileSuffix;

            using (var fileStream = File.Create(pathOnDisk))
            {
                exportedFile.FileStream.CopyTo(fileStream);
            }
        */

        return exportedFile;
    }
    catch
    {
        // Error handling
        throw;
    }
}
```

## <a name="next-steps"></a>後續步驟

檢閱如何為您的客戶與組織內嵌內容：

> [!div class="nextstepaction"]
>[將編頁報表匯出至檔案](export-paginated-report.md)

> [!div class="nextstepaction"]
>[對客戶進行內嵌](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[為組織內嵌](embed-sample-for-your-organization.md)