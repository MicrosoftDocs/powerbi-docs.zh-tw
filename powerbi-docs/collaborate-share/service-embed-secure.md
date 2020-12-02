---
title: 在安全入口網站或網站中內嵌報告
description: Power BI 內嵌功能可讓使用者輕鬆且安全地在內部入口網站中內嵌報表。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 04/27/2020
LocalizationGroup: Share your work
ms.openlocfilehash: a7f8c6d52acff8cbaaa00004448a3fae300afb9b
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411900"
---
# <a name="embed-a-report-in-a-secure-portal-or-website"></a>在安全入口網站或網站中內嵌報告

使用 Power BI 報表的全新 [內嵌] 選項，您可以輕鬆且安全地在內部入口網站中內嵌報表。 這些入口網站可以是 **雲端式** 或 **託管內部部署**，例如 SharePoint 2019。 內嵌報表會透過[資料列層級安全性 (RLS)](../admin/service-admin-rls.md) 遵守所有項目權限和資料安全性。 它們會提供不使用程式碼內嵌至任何接受 URL 或 iFrame 入口網站的功能。 

[內嵌] 選項支援 [URL 篩選](service-url-filters.md)及 URL 設定。 它可以讓您幾乎不使用任何程式碼來與入口網站整合，而只需要基本的 HTML 和 JavaScript 知識。

## <a name="how-to-embed-power-bi-reports-into-portals"></a>如何將 Power BI 報告內嵌到入口網站

1. 開啟 Power BI 服務中的報表。

2. 在 [更多選項 (...)] 功能表中，選取 [內嵌] >  [網站或入口網站]。

    ![網站或入口網站選項](media/service-embed-secure/power-bi-more-options-website.png)

2. 選取 [內嵌] 選項來開啟對話方塊，該對話方塊會提供您可以安全地用來內嵌報表的連結和 iFrame。

    ![[內嵌] 選項對話方塊](media/service-embed-secure/secure-embed-code-dialog.png)

3. 無論使用者是直接開啟報表 URL，還是開啟入口網站中的內嵌項目，報表存取都需要進行驗證。 若使用者尚未在其瀏覽器工作階段登入 Power BI，即會出現下列畫面。 當他們選取 [登入] 時，即會開啟一個新的瀏覽器視窗或索引標籤。 若他們並未收到登入提示，請讓他們檢查快顯封鎖程式。

    ![登入以檢視此報告](media/service-embed-secure/secure-embed-sign-in.png)

4. 在使用者登入後，會隨時開啟報表以顯示資料並允許進行頁面導覽和篩選設定。 只有具備檢視權限的使用者才能在 Power BI 中查看報表。 也都會套用所有[資料列層級安全性 (RLS)](../admin/service-admin-rls.md) 規則。 最後，使用者必須正確地取得授權：他們需要 Power BI Pro 授權，或報告必須位於 Power BI Premium 容量的工作區中。 每次使用者開啟新的瀏覽器視窗時，都需要登入。 但是，一旦登入，即會自動載入其他報表。

    ![內嵌報告](media/service-embed-secure/secure-embed-report.png)

5. 使用 iFrame 時，您可能需要編輯 **高度** 和 **寬度**，使其符合入口網站中的網頁。

    ![設定高度與寬度](media/service-embed-secure/secure-embed-size.png)

## <a name="granting-report-access"></a>授與報表存取權

[內嵌] 選項不會自動允許使用者檢視報表。 您可以在 Power BI 服務中設定檢視權限。

在 Power BI 服務中，您可以與需要存取的使用者共用內嵌報表。 若您使用 Microsoft 365 群組，則可將使用者列為工作區的成員。 如需詳細資訊，請參閱如何[在 Power BI 和 Microsoft 365 中管理工作區](service-manage-app-workspace-in-power-bi-and-office-365.md)。

## <a name="licensing"></a>授權

若要檢視內嵌報表，使用者需要 Power BI Pro 授權，或內容必須位於 [Power BI Premium 容量 (EM 或 P SKU)](../admin/service-admin-premium-purchase.md) 的工作區中。

## <a name="customize-your-embed-experience-using-url-settings"></a>使用 URL 設定自訂您的內嵌體驗

您可以使用內嵌 URL 的輸入設定來自訂使用者體驗。 在提供的 iFrame 中，您可以更新 URL 的 **src** 設定。

| 屬性  | 描述  |
|-----------|--------------|
| pageName  | 您可以使用 **pageName** 查詢字串參數來設定要開啟的報表頁面。 當在 Power BI 服務中檢視報表時，您可在報表 URL 的結尾處找到此值，如下所示。 |
| URL 篩選  | 您可以在您從 Power BI 收到的內嵌 URL 中使用 [URL 篩選](service-url-filters.md)來篩選內嵌內容。 透過這種方式，只需要基本 HTML 與 JavaScript 體驗，就可以建置只需要使用少數程式碼的整合。  |

## <a name="set-which-page-opens-for-an-embedded-report"></a>設定要為內嵌報表開啟的頁面 

當在 Power BI 服務中檢視報表時，您可在報表 URL 的結尾處找到 **pageName** 值。

1. 請在網頁瀏覽器中開啟 Power BI 服務的報表，然後複製網址列 URL。

    ![[報告] 區段](media/service-embed-secure/secure-embed-report-section.png)

2. 將 **pageName** 設定附加到 URL。

    ![附加 pageName](media/service-embed-secure/secure-embed-append-page-name.png)

## <a name="filter-report-content-using-url-filters"></a>使用 URL 篩選來篩選報告內容 

您可以使用 [URL 篩選](service-url-filters.md)來提供不同的報表檢視。 例如，下面的 URL 會篩選報告以顯示能源產業的資料。

使用 **pageName** 與 [URL Filters](service-url-filters.md) 的組合功能強大。 您可以使用基本 HTML 與 JavaScript 來建置體驗。

例如，以下是一個您可新增至 HTML 頁面的按鈕：

```html
<button class="textLarge" onclick='show("ReportSection", "Energy");' style="display: inline-block;">Show Energy</button>
```

當選取時，按鈕會呼叫函式以使用更新後的 URL 來更新 iFrame，該 URL 中包含能源產業的的篩選。

```javascript
function show(pageName, filterValue)

{

var newUrl = baseUrl + "&pageName=" + pageName;

if(null != filterValue && "" != filterValue)

{

newUrl += "&$filter=Industries/Industry eq '" + filterValue + "'";

}

//Assumes there's an iFrame on the page with id="iFrame"

var report = document.getElementById("iFrame")

report.src = newUrl;

}
```

![篩選](media/service-embed-secure/secure-embed-filter.png)

您可視需要新增所要的按鈕數目，以建立不需要撰寫太多程式碼的自訂體驗。 

## <a name="considerations-and-limitations"></a>考量與限制

* 安全內嵌案例支援編頁報表，也支援具有 URL 參數的編頁報表。 深入了解[在編頁報表的 URL 中傳遞報表參數](../paginated-reports/report-builder-url-pass-parameters.md)。

* 安全內嵌適用於發行到 Power BI 服務的報告。

* 每當使用者開啟新的瀏覽器視窗時，都必須登入以檢視報告。

* 在登入之後，某些瀏覽器會要求您重新整理頁面，特別是使用 InPrivate 或無痕模式時。

* 如果使用不支援的瀏覽器版本，您可能會遇到問題。 Power BI 支援[下列瀏覽器](../fundamentals/power-bi-browsers.md)。

* 不支援傳統 SharePoint Server，因為其需要早於 11 的 Internet Explorer 版本，或啟用相容性檢視模式。

* 為獲得單一登入體驗，請使用[內嵌在 SharePoint Online 中](service-embed-report-spo.md)選項，或使用[使用者擁有資料](../developer/embedded/embed-sample-for-your-organization.md)內嵌方法來建置自訂整合。 

* 隨著 [內嵌] 選項提供的自動驗證功能無法搭配 Power BI JavaScript API 使用。 針對 Power BI JavaScript API，請使用[使用者擁有資料](../developer/embedded/embed-sample-for-your-organization.md)內嵌方法。 

* 驗證權杖存留期會以您的 AAD 設定作為基礎進行控制。 驗證權杖過期時，使用者將需要重新整理瀏覽器來取得更新後的驗證權杖。 預設存留期是一個小時，但在您的組織中這段時間可以更短或是更長。  在此案例中，不能自動重新整理權杖。

## <a name="next-steps"></a>後續步驟

* [在 Power BI 中共用成品的方式](service-how-to-collaborate-distribute-dashboards-reports.md)

* [在 URL 中使用查詢字串參數來篩選報表](service-url-filters.md)

* [在 SharePoint Online 中嵌入報表網頁組件](service-embed-report-spo.md)

* [從 Power BI 發佈至 Web](service-publish-to-web.md)
