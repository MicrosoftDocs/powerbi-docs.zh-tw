---
title: 在 Power BI 內嵌式分析中取得驗證存取權杖，以取得更佳的內嵌 BI 見解
description: 推送資料的逐步解說 - 取得驗證存取權杖。 使用 Power BI 內嵌式分析，以便取得更佳的內嵌 BI 見解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: madia
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: tutorial
ms.date: 05/29/2019
ms.openlocfilehash: 22d30e14256a2e58e05e17207380842392fe0c23
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887400"
---
# <a name="step-2-get-an-authentication-access-token"></a>步驟 2：取得驗證存取權杖

本文是[將資料推送至 Power BI 資料集](walkthrough-push-data.md)系列的第二個步驟。

在步驟 1 中，[您已在 Azure AD 中註冊了用戶端應用程式](../embedded/register-app.md)。 在此步驟中，您會收到驗證存取權杖。 Power BI 應用程式會與 Azure Active Directory 整合，以提供應用程式的安全登入和授權。 您的應用程式使用者可以使用權杖來進行 Azure AD 驗證，並取得 Power BI 資源的存取權。

## <a name="get-an-authentication-access-token"></a>取得驗證存取權杖

開始之前，請確認您已完成[將資料推送至 Power BI 資料集](walkthrough-push-data.md)系列的[上一個步驟](../embedded/register-app.md)。 

此程序需要 Visual Studio 2015 或更新版本。

1. 在 Visual Studio 中，建立新的 C# **主控台應用程式** 專案。

2. 安裝[.NET NuGet 套件的 Azure AD 驗證程式庫](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/2.22.302111727)。 您的 .NET 應用程式需要此套件以取得驗證安全性權杖。 

     a. 選取 [工具]   > [NuGet 套件管理員]   > [套件管理員主控台]  。

     b. 輸入 **Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612**

     c. 在 Program.cs 中，新增 `using Microsoft.IdentityModel.Clients.ActiveDirectory;`。

3. 完成這些步驟之後，將所列的範例程式碼新增至 Program.cs。

4. 將 "{ClientID}" 取代為您在註冊應用程式時 ([上一篇系列文章](../embedded/register-app.md)) 取得的 **用戶端識別碼**。

5. 執行主控台應用程式，然後登入您的 Power BI 帳戶。 

   主控台視窗中應會顯示權杖字串。

**取得驗證安全性權杖的範例程式碼**

將此程式碼加入 Program {...}。

* 呼叫作業的權杖變數： 
  
  ```csharp
  private static string token = string.Empty;
  
  static void Main(string[] args)
  {
  }
  ```
* 在 static void Main(string[] args) 中：
  
  ```csharp
  static void Main(string[] args)
  {
    //Get an authentication access token
    token = GetToken();
  }
  ```
* 加入 GetToken() 方法：

```csharp
       #region Get an authentication access token
       private static async Task<string> GetToken()
       {
           // TODO: Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612
           // and add using Microsoft.IdentityModel.Clients.ActiveDirectory

           //The client id that Azure AD created when you registered your client app.
           string clientID = "{Client_ID}";

           //RedirectUri you used when you register your app.
           //For a client app, a redirect uri gives Azure AD more details on the application that it will authenticate.
           // You can use this redirect uri for your client app
           string redirectUri = "https://login.live.com/oauth20_desktop.srf";

           //Resource Uri for Power BI API
           string resourceUri = "https://analysis.windows.net/powerbi/api";

           //OAuth2 authority Uri
           string authorityUri = "https://login.microsoftonline.net/common/";

           //Get access token:
           // To call a Power BI REST operation, create an instance of AuthenticationContext and call AcquireToken
           // AuthenticationContext is part of the Active Directory Authentication Library NuGet package
           // To install the Active Directory Authentication Library NuGet package in Visual Studio,
           //  run "Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory" from the nuget Package Manager Console.

           // AcquireToken will acquire an Azure access token
           // Call AcquireToken to get an Azure token from Azure Active Directory token issuance endpoint
           AuthenticationContext authContext = new AuthenticationContext(authorityUri);
           var token = authContext.AcquireTokenAsync(resourceUri, clientID, new Uri(redirectUri)).Result.AccessToken;

           Console.WriteLine(token);
           Console.ReadLine();

           return token;
       }

       #endregion
```

取得驗證權杖之後，您可以呼叫任何 Power BI 作業。

本系列的下一篇文章說明如何[在 Power BI 中建立資料集](walkthrough-push-data-create-dataset.md)。


## <a name="complete-code-listing"></a>完整程式碼清單

```csharp
using System;
using Microsoft.IdentityModel.Clients.ActiveDirectory;

namespace walkthrough_push_data
{
    class Program
    {
        private static string token = string.Empty;

        static void Main(string[] args)
        {

            //Get an authentication access token
            token = GetToken();

        }

        #region Get an authentication access token
        private static async Task<string> GetToken()
        {
            // TODO: Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory -Version 2.21.301221612
            // and add using Microsoft.IdentityModel.Clients.ActiveDirectory

            //The client id that Azure AD created when you registered your client app.
            string clientID = "{Client_ID}";

            //RedirectUri you used when you register your app.
            //For a client app, a redirect uri gives Azure AD more details on the application that it will authenticate.
            // You can use this redirect uri for your client app
            string redirectUri = "https://login.live.com/oauth20_desktop.srf";

            //Resource Uri for Power BI API
            string resourceUri = "https://analysis.windows.net/powerbi/api";

            //OAuth2 authority Uri
            string authorityUri = "https://login.microsoftonline.com/common/";

            //Get access token:
            // To call a Power BI REST operation, create an instance of AuthenticationContext and call AcquireToken
            // AuthenticationContext is part of the Active Directory Authentication Library NuGet package
            // To install the Active Directory Authentication Library NuGet package in Visual Studio,
            //  run "Install-Package Microsoft.IdentityModel.Clients.ActiveDirectory" from the nuget Package Manager Console.

            // AcquireToken will acquire an Azure access token
            // Call AcquireToken to get an Azure token from Azure Active Directory token issuance endpoint
            AuthenticationContext authContext = new AuthenticationContext(authorityUri);
            var token = authContext.AcquireTokenAsync(resourceUri, clientID, new Uri(redirectUri)).Result.AccessToken;

            Console.WriteLine(token);
            Console.ReadLine();

            return token;
        }

        #endregion

    }
}
```



## <a name="next-steps"></a>後續步驟

* 此系列的下一篇文章為[在 Power BI 中建立資料集](walkthrough-push-data-create-dataset.md)
* [Power BI REST API 概觀](overview-of-power-bi-rest-api.md)  
* [Power BI REST API](/rest/api/power-bi/)  

有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)