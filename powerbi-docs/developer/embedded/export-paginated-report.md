---
title: 匯出 Power BI 內嵌式分析編頁報表 API 以獲得更好的內嵌 BI 見解
description: 了解如何匯出內嵌 Power BI 分頁報表。 使用 Power BI 內嵌式分析，取得更佳的內嵌 BI 見解。
author: KesemSharabi
ms.author: kesharab
ms.topic: how-to
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 04/05/2020
ms.openlocfilehash: befb64ec85c02f8993d828202df06aafc5901482
ms.sourcegitcommit: 84f0e7f31e62cae3bea2dcf2d62c2f023cc2d404
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2021
ms.locfileid: "98781525"
---
# <a name="export-paginated-report-to-file-preview"></a>將分頁報表匯出至檔案 (預覽)

`exportToFile` API 可供使用 REST 呼叫來匯出 Power BI 分頁報表。 支援下列檔案格式：
* **.pptx** (PowerPoint)
* **.pdf**
* **.xlsx** (Excel)
* **.dox** (Word)
* **.csv**
* **.xml**
* **.mhtml**
* **影像**
    * 匯出至影像時，請透過 `OutputFormat` 格式設定來設定影像格式
    * 支援的 OutputFormat 值包括：.bmp、.emf、.gif、.jpeg、.png 或 .tiff (預設)

## <a name="usage-examples"></a>使用範例

您可以透過各種方式來使用匯出功能。 以下是一些範例︰

* **[傳送至列印] 按鈕** - 在您的應用程式中，建立按一下以觸發匯出作業的按鈕。 作業可將已檢視的報表匯出為 .pdf 或 .pptx，當完成時，使用者會以下載項目的形式來接收檔案。 使用報表參數和格式設定，您可在特定狀態下匯出報表，包括篩選的資料、自訂頁面大小和其他特定格式設定。 因為 API 是非同步的，所以檔案可能需要一些時間才能使用。

* **電子郵件附件** - 以設定的間隔傳送自動電子郵件，並附加 .pdf 報表。 若要將每週報表自動傳送給主管，這個案例就很有用。

## <a name="using-the-api"></a>使用 API

該 API 是非同步的。 呼叫 [exportToFile](/rest/api/power-bi/reports/exporttofile) \(英文\) API 時，其會觸發匯出作業。 觸發匯出作業之後，請使用[輪詢](/rest/api/power-bi/reports/getexporttofilestatus) \(英文\) 來追蹤作業，直到完成為止。

當匯出完成時，輪詢 API 呼叫會傳回 [Power BI URL](/rest/api/power-bi/reports/getfileofexporttofile) \(英文\) 來取得檔案。 該 URL 在 24 小時內有效。

## <a name="supported-features"></a>支援的功能

### <a name="format-settings"></a>格式設定

為每個檔案格式指定各種格式設定。 所支援屬性和值相當於分頁報表 URL 參數的[裝置資訊參數](../../paginated-reports/report-builder-url-parameters.md#report-commands-rdl)。

以下是兩個範例，一個用來將報表中的前四個頁面匯出成 .pptx 檔案，另一個則用來將報表的第三頁匯出成 .jpeg 檔案。

**將前四個頁面匯出成 .pptx**

```json
{
      "format": "PPTX",
      "paginatedReportConfiguration":{
            "formatSettings":{
                  "UseReportPageSize": "true",
                  "StartPage": "1",
                  "EndPage": "4"
            }
      }
}
```

**將第三頁匯出成 .jpeg**

```json
{
      "format": "IMAGE",
      "paginatedReportConfiguration":{
            "formatSettings":{
                  "OutputFormat": "JPEG",
                  "StartPage": "3",
                  "EndPage": "3"
            }
      }
}
```

### <a name="report-parameters"></a>報表參數

您可使用 `exportToFile` API，以程式設計方式匯出具有一組報表參數的報表。 這是使用[報表參數](../../paginated-reports/paginated-reports-parameters.md)功能來完成。

以下是設定報表參數值的範例。

```json
{
      "format": "PDF",
      "paginatedReportConfiguration":{
            "parameterValues":[
                  {"name": "State", "value": "WA"},
                  {"name": "City", "value": "Seattle"},
                  {"name": "City", "value": "Bellevue"},
                  {"name": "City", "value": "Redmond"}
            ]
      }
}
```

### <a name="authentication"></a>驗證

您只能以使用者 (或主要使用者) 或者[服務主體](embed-service-principal.md)來進行驗證。

### <a name="row-level-security-rls"></a>資料列層級安全性 (RLS)

當使用已將資料列層級安全性 (RLS) 定義為資料來源的 Power BI 資料集時，您可匯出報表，其中顯示只有特定使用者才看得到的資料。 例如，如果您要匯出以區域角色定義的銷售報表，您可以透過程式設計方式篩選報表，以便只顯示特定區域。

若要使用 RLS 匯出，針對報表用來作為資料來源的 Power BI 資料集，您必須擁有其讀取權限。

以下是為 RLS 提供有效使用者名稱的範例。

```json
{
      "format": "PDF",
      "paginatedReportConfiguration":{
            "identities": [
                  {"username": "john@contoso.com"}
            ]
      }
}
```

### <a name="single-sign-on-sql-and-dataverse-sso"></a>單一登入 SQL 和 Dataverse (SSO) 

在 Power BI 中，您可以選擇使用 SSO 設定 OAuth。 當您這樣做時，用來查看報表的使用者認證會用來取出資料。 Requrest 標頭中的存取權杖不會用來存取資料，您必須使用 post 主體中的有效身分識別傳入權杖。

存取權杖會讓存取權杖變得令人困惑，因為它會取得您想要存取之資源的正確存取權杖。

- 針對 Azure SQL，資源為 `https://database.windows.net` 。
- 針對 Dataverse，資源是 `https://` 您環境的位址。 例如 `https://contoso.crm.dynamics.com`。

使用 [AuthenticationCoNtext. AcquireTokenAsync](https://docs.microsoft.com/dotnet/api/microsoft.identitymodel.clients.activedirectory.authenticationcontext.acquiretokenasync) 方法存取權杖 API。

以下範例提供具有存取權杖的有效使用者名稱。

```json
{
       "format":"PDF",
       "paginatedReportConfiguration":{
          "formatSettings":{
             "AccessiblePDF":"true",
             "PageHeight":"11in",
             "PageWidth":"8.5in",
             "MarginBottom":"2in"
          },
          "identities":[
             {
                "username":"john@contoso.com",
                "identityBlob": {
                "value": "eyJ0eX....full access token"
         }
        }
     ]
   }
}
```

## <a name="ppu-concurrent-requests"></a>PPU 並行要求數
使用 [Premium Per User (PPU)](../../admin/service-premium-per-user-faq.md) 時，`exportToFile` API 允許在五分鐘時間範圍內發出一個要求。 若五分鐘時間範圍內有多個 (多於一個) 要求，將會導致「太多要求」(429) 錯誤。

## <a name="code-examples"></a>程式碼範例

程式碼範例中使用的 Power BI API SDK 可在[這裡](https://www.nuget.org/packages/Microsoft.PowerBI.Api)下載。

當您建立匯出作業時，有三個要遵循的步驟：

1. 傳送匯出要求。
2. 輪詢。
3. 取得檔案。

此節提供每個步驟的範例。

### <a name="step-1---sending-an-export-request"></a>步驟 1 - 傳送匯出要求

第一個步驟是傳送匯出要求。 在此範例中，會針對特定頁面範圍、大小和報表參數值傳送匯出要求。

```csharp
private async Task<string> PostExportRequest(
    Guid reportId,
    Guid groupId)
{
    // For documentation purposes the export configuration is created in this method
    // Ordinarily, it would be created outside and passed in
    var paginatedReportExportConfiguration = new PaginatedReportExportConfiguration()
    {
        FormatSettings = new Dictionary<string, string>()
        {
            {"PageHeight", "14in"},
            {"PageWidth", "8.5in" },
            {"StartPage", "1"},
            {"EndPage", "4"},
        },
        ParameterValues = new List<ParameterValue>()
        {
            { new ParameterValue() {Name = "State", Value = "WA"} },
            { new ParameterValue() {Name = "City", Value = "Redmond"} },
        },
    };

    var exportRequest = new ExportReportRequest
    {
        Format = FileFormat.PDF,
        PaginatedReportExportConfiguration = paginatedReportExportConfiguration,
    };

    var export = await Client.Reports.ExportToFileInGroupAsync(groupId, reportId, exportRequest);

    // Save the export ID, you'll need it for polling and getting the exported file
    return export.Id;
}
```

### <a name="step-2---polling"></a>步驟 2 - 輪詢

在您傳送匯出要求之後，請使用輪詢來識別您要等候的匯出檔案何時就緒。

```csharp
private async Task<Export> PollExportRequest(
    Guid reportId,
    Guid groupId,
    string exportId /* Get from the ExportToAsync response */,
    int timeOutInMinutes,
    CancellationToken token)
{
    Export exportStatus = null;
    DateTime startTime = DateTime.UtcNow;
    const int secToMillisec = 1000;
    do
    {
        if (DateTime.UtcNow.Subtract(startTime).TotalMinutes > timeOutInMinutes || token.IsCancellationRequested)
        {
            // Error handling for timeout and cancellations
            return null;
        }

        var httpMessage = 
            await Client.Reports.GetExportToFileStatusInGroupWithHttpMessagesAsync(groupId, reportId, exportId);
            
        exportStatus = httpMessage.Body;
        if (exportStatus.Status == ExportState.Running || exportStatus.Status == ExportState.NotStarted)
        {
            // The recommended waiting time between polling requests can be found in the RetryAfter header
            // Note that this header is only populated when the status is either Running or NotStarted
            var retryAfter = httpMessage.Response.Headers.RetryAfter;
            var retryAfterInSec = retryAfter.Delta.Value.Seconds;

            await Task.Delay(retryAfterInSec * secToMillisec);
        }
    }
    // While not in a terminal state, keep polling
    while (exportStatus.Status != ExportState.Succeeded && exportStatus.Status != ExportState.Failed);

    return exportStatus;
}
```

### <a name="step-3---getting-the-file"></a>步驟 3 - 取得檔案

一旦輪詢傳回 URL，請使用此範例來取得已接收的檔案。

```csharp
private async Task<ExportedFile> GetExportedFile(
    Guid reportId,
    Guid groupId,
    Export export /* Get from the GetExportStatusAsync response */)
{
    if (export.Status == ExportState.Succeeded)
    {
        var httpMessage = 
            await Client.Reports.GetFileOfExportToFileInGroupWithHttpMessagesAsync(groupId, reportId, export.Id);

        return new ExportedFile
        {
            FileStream = httpMessage.Body,
            ReportName = export.ReportName,
            FileExtension = export.ResourceFileExtension,
        };
    }

    return null;
}

public class ExportedFile
{
    public Stream FileStream;
    public string ReportName;
    public string FileExtension;
}
```

### <a name="end-to-end-example"></a>端對端範例

這是匯出報表的端對端範例。 此範例包含下列階段：
1. [傳送匯出要求](#step-1---sending-an-export-request)。
2. [輪詢](#step-2---polling)。
3. [取得檔案](#step-3---getting-the-file)。

```csharp
private async Task<ExportedFile> ExportPaginatedReport(
    Guid reportId,
    Guid groupId,
    int pollingtimeOutInMinutes,
    CancellationToken token)
{
    try
    {
        var exportId = await PostExportRequest(reportId, groupId);

        var export = await PollExportRequest(reportId, groupId, exportId, pollingtimeOutInMinutes, token);
        if (export == null || export.Status != ExportState.Succeeded)
        {
           // Error, failure in exporting the report
            return null;
        }

        return await GetExportedFile(reportId, groupId, export);
    }
    catch
    {
        // Error handling
        throw;
    }
}
```

## <a name="limitations"></a>限制

服務主體不支援匯出具有 Power BI 資料集作為其資料來源的編頁報表。

## <a name="next-steps"></a>後續步驟

檢閱如何為您的客戶與組織內嵌內容：

> [!div class="nextstepaction"]
>[將報表匯出至檔案](export-to.md)

> [!div class="nextstepaction"]
>[對客戶進行內嵌](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[為組織內嵌](embed-sample-for-your-organization.md)
