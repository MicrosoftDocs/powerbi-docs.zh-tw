---
title: 自動為客戶設定範本應用程式安裝
description: 了解如何將範本應用程式安裝的設定自動化。
author: paulinbar
ms.author: painbar
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 11/23/2020
ms.openlocfilehash: 33de464a1bb1389fadfbc7a85ded9365321e0a62
ms.sourcegitcommit: 932f6856849c39e34229dc9a49fb9379c56a888a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97926295"
---
# <a name="automated-configuration-of-a-template-app-installation"></a>自動設定範本應用程式安裝

範本應用程式是一種讓客戶能夠從其資料取得見解的絕佳方式。 範本應用程式會將客戶連線到其資料，以便快速啟動並執行。 範本應用程式會為客戶提供預先建立的報表，讓客戶可視需要加以自訂。

客戶不一定熟悉連線到其資料所需的詳細資料。 當客戶安裝範本應用程式而必須提供這些詳細資料時，可能會對其造成困擾。

如果您是資料服務提供者，並已建立範本應用程式來協助客戶在服務上使用其資料，您就可以讓客戶更輕鬆地安裝範本應用程式。 您可將範本應用程式參數的設定自動化。 當客戶登入入口網站時，只需選取您已備妥的特殊連結即可。 此連結能夠：

- 啟動自動化，其會收集所需的資訊。
- 預先設定範本應用程式參數。
- 將客戶重新導向至可安裝應用程式的 Power BI 帳戶。

客戶只需要選擇 [安裝]、驗證其資料來源，就大功告成了！

客戶體驗圖解如下。

![使用自動安裝應用程式的使用者體驗圖解。](media/template-apps-auto-install/high-level-flow.png)

本文描述將範本應用程式安裝設定自動化所需的基本流程、必要條件，以及主要步驟與 API。 如果想要立刻深入了解並開始使用，則可跳至[教學課程](template-apps-auto-install-tutorial.md)，在該教學課程中，您可使用我們已備妥的簡單範例應用程式 (使用 Azure 函數)，以將範本應用程式安裝的設定自動化。

## <a name="basic-flow"></a>基本流程

自動化範本應用程式安裝設定的基本流程如下：

1. 使用者登入 ISV 的入口網站，然後選取提供的連結。 自動化流程會隨即開始。 ISV 的入口網站會在此階段準備使用者特定設定。

1. ISV 會根據在 ISV 租用戶中所註冊的[服務主體 (僅適用於應用程式權杖)](../embedded/embed-service-principal.md)，取得「僅適用於應用程式」權杖。

1. ISV 會透過 [Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/) 建立「安裝票證」，其中包含 ISV 所準備的使用者特定參數設定。

1. ISV 會使用包含安裝票證的 ```POST``` 重新導向方法，將使用者重新導向至 Power BI。

1. 使用者會藉由安裝票證而重新導向至其 Power BI 帳戶，並收到安裝範本應用程式的提示。 當使用者選取 [安裝] 後，即會開始安裝範本應用程式。

>[!Note]
>儘管參數值是由 ISV 在建立安裝票證期間所設定，但資料來源的相關認證只能由使用者在安裝最後階段提供。 這種處理方式可避免認證暴露給協力廠商，並確保使用者與範本應用程式資料來源之間的連線處於安全狀態。

## <a name="prerequisites"></a>Prerequisites

需要具備下列必要條件，才能提供預先設定的範本應用程式安裝體驗：

* Power BI Pro 授權。 如果您沒有註冊 Power BI Pro，請先[註冊免費試用](https://powerbi.microsoft.com/pricing/)再開始進行操作。
* 已設定的 Azure Active Directory (Azure AD) 租用戶。 如需設定租用戶的指示，請參閱[建立 Azure Active Directory 租用戶](https://docs.microsoft.com/power-bi/developer/embedded/create-an-azure-active-directory-tenant)。
* 已在上述租用戶中註冊的 **服務主體 (僅適用於應用程式權杖)** 。 如需詳細資訊，請參閱[使用服務主體與應用程式祕密內嵌 Power BI 內容](https://docs.microsoft.com/power-bi/developer/embedded/embed-service-principal)。 請務必將應用程式註冊為 **伺服器端 Web 應用程式**。 您註冊伺服器端 Web 應用程式，以建立應用程式祕密。 在此流程中，您需要儲存「應用程式識別碼」(ClientID) 與「應用程式祕密」(ClientSecret)，以供稍後的步驟執行。
* 已就緒供安裝的 **已參數化範本應用程式**。 所要建立的範本應用程式其租用戶，必須是您在 Azure AD 中註冊應用程式的相同租用戶。 如需詳細資訊，請參閱[範本應用程式祕訣](https://docs.microsoft.com/power-bi/connect-data/service-template-apps-tips)或[在 Power BI 中建立範本應用程式](https://docs.microsoft.com/power-bi/connect-data/service-template-apps-create)。 您必須記下範本應用程式中的下列資訊，以便進行後續步驟：
     * 在建立應用程式後，於[定義範本應用程式屬性](../../connect-data/service-template-apps-create.md#define-the-properties-of-the-template-app)流程結尾安裝 URL 中顯示的「應用程式識別碼」、「套件金鑰」，以及「擁有者識別碼」。 您也可以選取範本應用程式[版本管理](../../connect-data/service-template-apps-create.md#manage-the-template-app-release)中的 [取得連結]，以取得相同的連結。
    * 在範本應用程式資料集中定義的「參數名稱」。 參數名稱是區分大小寫的字串，且可在[定義範本應用程式的屬性](../../connect-data/service-template-apps-create.md#define-the-properties-of-the-template-app)時，從 [參數設定] 索引標籤中取得，或從 Power BI 中的資料集設定取得。

    >[!NOTE]
    >如果範本應用程式已準備好進行安裝，則即使該範本應用程式尚未在 AppSource 上開放使用，您也可以在其中測試預先設定的安裝應用程式。 若要讓租用戶以外的使用者能夠使用自動安裝應用程式來安裝範本應用程式，則必須在 [Power BI Apps 市集](https://app.powerbi.com/getdata/services)中開放使用該範本應用程式。 在使用您正在建立的自動安裝應用程式來發佈範本應用程式之前，請務必先將其發佈到[合作夥伴中心](https://docs.microsoft.com/azure/marketplace/partner-center-portal/create-power-bi-app-offer)。

## <a name="main-steps-and-apis"></a>主要步驟與 API

下列各節會描述將範本應用程式安裝設定自動化的主要步驟，以及所需的 API。 雖然大部分的步驟都是使用 [Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/) 來完成，但此處所述的程式碼範例是使用 .NET SDK 所撰寫。

## <a name="step-1-create-a-power-bi-client-object"></a>步驟 1：建立 Power BI 用戶端物件

若要使用 Power BI REST API，則必須從 Azure AD 取得[服務主體](../embedded/embed-service-principal.md)的「存取權杖」。 您需要先為您的 Power BI 應用程式取得 [Azure AD 存取權杖](../embedded/get-azuread-access-token.md#access-token-for-non-power-bi-users-app-owns-data)，才可呼叫 [Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/)。
您需要建立 Power BI 用戶端物件，以讓您與 [Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/) 互動，才能使用存取權杖建立 Power BI 用戶端。 你可以將 **AccessToken** 與 **Microsoft.Rest.TokenCredentials** 物件包裝在一起來建立 Power BI 用戶端物件。

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.Rest;
using Microsoft.PowerBI.Api.V2;

var tokenCredentials = new TokenCredentials(authenticationResult.AccessToken, "Bearer");

// Create a Power BI client object. It's used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Your code goes here.
}
```

## <a name="step-2-create-an-install-ticket"></a>步驟 2：建立安裝票證

建立安裝票證，其用於將使用者重新導向至 Power BI。 此作業所使用的 API 是 **CreateInstallTicket** API。
* [範本應用程式 CreateInstallTicket](https://docs.microsoft.com/rest/api/power-bi/templateapps/createinstallticket)

您可從[範例應用程式](https://github.com/microsoft/Template-apps-examples/tree/master/Developer%20Samples/Automated%20Install%20Azure%20Function/InstallTemplateAppSample)中的 [InstallTemplateApp/InstallAppFunction.cs](https://github.com/microsoft/Template-apps-examples/blob/master/Developer%20Samples/Automated%20Install%20Azure%20Function/InstallTemplateAppSample/InstallTemplateApp/InstallAppFunction.cs) 檔案，取得為範本應用程式安裝與設定建立安裝票證的範例。


下列程式碼範例說明如何使用範本應用程式 **CreateInstallTicket** REST API。
```csharp
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

// Create Install Ticket Request.
InstallTicket ticketResponse = null;
var request = new CreateInstallTicketRequest()
{
    InstallDetails = new List<TemplateAppInstallDetails>()
    {
        new TemplateAppInstallDetails()
        {
            AppId = Guid.Parse(AppId),
            PackageKey = PackageKey,
            OwnerTenantId = Guid.Parse(OwnerId),
            Config = new TemplateAppConfigurationRequest()
            {
                Configuration = Parameters
                                    .GroupBy(p => p.Name)
                                    .ToDictionary(k => k.Key, k => k.Select(p => p.Value).Single())
            }
        }
    }
};

// Issue the request to the REST API using .NET SDK.
InstallTicket ticketResponse = await client.TemplateApps.CreateInstallTicketAsync(request);
```

## <a name="step-3-redirect-users-to-power-bi-with-the-ticket"></a>步驟 3：使用票證將使用者重新導向至 Power BI

完成建立安裝票證之後，您即可使用該票證將使用者重新導向至 Power BI，以繼續安裝及設定範本應用程式。 您需要將安裝票證包含在範本應用程式安裝 URL 的要求本文中，並對其使用 ```POST``` 方法重新導向來完成。

使用 ```POST``` 要求發行重新導向的方法有相當多種。 您可根據情況，以及使用者與入口網站或服務的互動方式來選擇任一種方法。

例如一個主要用於測試目的簡單範例，其使用具有隱藏欄位的表單，在載入時自動提交這些隱藏欄位。

```javascript
<html>
    <body onload='document.forms["form"].submit()'>
        <!-- form method is POST and action is the app install URL -->
        <form name='form' action='https://app.powerbi.com/....' method='post' enctype='application/json'>
            <!-- value should be the new install ticket -->
            <input type='hidden' name='ticket' value='H4sI....AAA='>
        </form>
    </body>
</html>
```

下列是[範例應用程式](https://github.com/microsoft/Template-apps-examples/tree/master/Developer%20Samples/Automated%20Install%20Azure%20Function/InstallTemplateAppSample)回應的範例，這些回應包含安裝票證，且會自動將使用者重新導向至 Power BI。 此 Azure 函數的回應如同在以上 HTML 範例中見，是相同的自動自我提交表單。

```csharp
...
    return new ContentResult() { Content = RedirectWithData(redirectUrl, ticket.Ticket), ContentType = "text/html" };
}

...

public static string RedirectWithData(string url, string ticket)
{
    StringBuilder s = new StringBuilder();
    s.Append("<html>");
    s.AppendFormat("<body onload='document.forms[\"form\"].submit()'>");
    s.AppendFormat("<form name='form' action='{0}' method='post' enctype='application/json'>", url);
    s.AppendFormat("<input type='hidden' name='ticket' value='{0}' />", ticket);
    s.Append("</form></body></html>");
    return s.ToString();
}
```

>[!Note]
>使用 ```POST``` 瀏覽器重新導向的方法有相當多種， 但仍建議根據服務需求與限制，一律使用最安全的方法。 請記住，某些不安全的重新導向方法可能會導致暴露使用者或服務，進而產生安全性問題。

## <a name="step-4-move-your-automation-to-production"></a>步驟 4：將自動化移至生產

當您設計的自動化已準備就緒時，請務必將其移至生產。

## <a name="next-steps"></a>後續步驟

* 參閱[教學課程](template-apps-auto-install-tutorial.md)，其使用簡單的 Azure 函數來將範本應用程式安裝設定自動化。
* 有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)。
