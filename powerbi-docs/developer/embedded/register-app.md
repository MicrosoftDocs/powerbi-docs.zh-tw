---
title: 註冊應用程式，以在 Power BI 內嵌式分析應用程式中內嵌 Power BI 內容，取得更佳的內嵌 BI 見解
description: 了解如何在 Azure Active Directory 內註冊應用程式，以用來內嵌 Power BI 內容。 使用 Power BI 內嵌式分析，以便取得更佳的內嵌 BI 見解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: nishalit
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 04/02/2019
ms.openlocfilehash: 624e0a2838a08d1cf68ae58223fe979a56312b48
ms.sourcegitcommit: 1cad78595cca1175b82c04458803764ac36e5e37
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2021
ms.locfileid: "98565928"
---
# <a name="register-an-azure-ad-application-to-use-with-power-bi"></a>註冊要與 Power BI 搭配使用的 Azure AD 應用程式

您需要在 Azure 中註冊 Azure Active Directory (Azure AD) 應用程式，才能使用 Power BI 內嵌式分析。 Azure AD 應用程式會建立 Power BI REST 資源的權限，以便讓您存取 [Power BI REST API](/rest/api/power-bi/)。

## <a name="determine-your-embedding-solution"></a>決定您的內嵌解決方案

在註冊您的應用程式之前，請先決定下列哪一個解決方案最適合您：

* 為您的客戶內嵌
* 為您的組織內嵌

### <a name="embed-for-your-customers"></a>為您的客戶內嵌

如果您打算建立專為您的客戶設計的應用程式，請使用 [針對您的客戶進行內嵌](embed-sample-for-customers.md)解決方案 (又稱 *應用程式擁有資料*)。 使用者將不需要登入 Power BI 或具有 Power BI 授權，就可以使用您的應用程式。 您的應用程式將使用下列其中一種方法，針對 Power BI 進行驗證：

* **主要使用者** 帳戶 (用於登入 Power BI 的 Power BI Pro 授權)

* [服務主體](embed-service-principal.md)

「針對您的客戶進行內嵌」解決方案通常是由獨立軟體廠商 (ISV) 以及為協力廠商建立應用程式的開發人員所使用。

### <a name="embed-for-your-organization"></a>為您的組織內嵌

如果您打算建立需要使用者透過其認證來驗證 Power BI 的應用程式，請使用[針對您的組織進行內嵌](embed-sample-for-your-organization.md)解決方案 (又稱「使用者擁有資料」)。

「針對您的組織進行內嵌」解決方案通常是由企業與大型組織所使用，且適用於內部使用者。

## <a name="register-an-azure-ad-app"></a>註冊 Azure AD 應用程式

註冊 Azure AD 應用程式最簡單的方式，就是使用 [Power BI 內嵌安裝工具](https://app.powerbi.com/embedsetup)。 此工具使用簡單的圖形化介面，為內嵌式解決方案提供快速的註冊流程。

如果您要建立「針對您的組織進行內嵌」應用程式，並想要更充分掌控您的 Azure AD 應用程式，您可以在 Azure 入口網站中手動註冊。

> [!IMPORTANT]
> 註冊 Power BI 應用程式之前，您需要有 [Azure Active Directory 租用戶和組織使用者](create-an-azure-active-directory-tenant.md)。

# <a name="embed-for-your-customers"></a>[對客戶進行內嵌](#tab/customers)

這些步驟會說明如何為 Power BI 的[針對您的客戶進行內嵌](embed-sample-for-customers.md)解決方案，註冊 Azure AD 應用程式。

[!INCLUDE[registration tool step 1](../../includes/register-tool-step-1.md)]

2. 在 [選擇內嵌解決方案] 區段中，選取 [針對您的客戶進行內嵌]。

[!INCLUDE[registration tool step 3](../../includes/register-tool-step-3.md)]

4. 在「步驟 2 - 註冊應用程式」中，填寫下列欄位：

    * **應用程式名稱** - 為您的應用程式命名。

    * **API 存取** - 選取應用程式所需的 Power BI API (又稱範圍)。 您可以使用 [全選] 來選取所有 API。 如需 Power BI 存取權限的詳細資訊，請參閱 [Microsoft 身分識別平台端點中的權限和同意](/azure/active-directory/develop/v2-permissions-and-consent)。

5. 選取 [註冊]。

    您的 Azure AD 應用程式 [應用程式識別碼] 會顯示在 [摘要] 方塊中。 複製此值以供稍後使用。

[!INCLUDE[registration tool steps 6-7](../../includes/register-tool-steps-6-7.md)]

8. 在「步驟 5 - 授與權限」中，選取 [授與權限]，然後在快顯視窗中選取 [接受]。 這可讓您的 Azure AD 應用程式使用您已登入的使用者，來存取選取的 API (又稱範圍)。 此使用者也稱為 **主要使用者**。

9. (選擇性) 如果您建立了 Power BI 的工作區，並使用工具將內容上傳到其中，您現在可以選取 [下載範例應用程式]。 請務必記得複製 [摘要] 方塊中的所有資訊。

[!INCLUDE[registration tool note](../../includes/register-tool-note.md)]

# <a name="embed-for-your-organization"></a>[為組織內嵌](#tab/organization)

這些步驟會說明如何為 Power BI 的[針對您的組織進行內嵌](embed-sample-for-your-organization.md)解決方案，註冊 Azure AD 應用程式。

[!INCLUDE[registration tool step 1](../../includes/register-tool-step-1.md)]

2. 在 [選擇內嵌解決方案] 區段中，選取 [針對您的組織進行內嵌]。

[!INCLUDE[registration tool step 3](../../includes/register-tool-step-3.md)]

4. 在「步驟 2 - 註冊應用程式」中，填寫下列欄位：

    * **應用程式名稱** - 為您的應用程式命名。

    * **首頁 URL** - 輸入您的首頁 URL。

    * **重新導向 URL** - 在您登入後，當您的應用程式收到來自 Azure 的驗證碼時，您的應用程式使用者會由系統重新導向至此位址。 請選擇下列選項的其中一個：

        * **使用預設 URL** - 這個選項會自動建立並下載內嵌式分析應用程式範例。 預設的 URL 為 http://localhost:13526/ 。

        * **使用自訂 URL** - 如果您已經擁有內嵌式分析應用程式，也知道您想要用於重新導向 URL 的內容，請選取此選項。

    * **API 存取** - 選取應用程式所需的 Power BI API (又稱範圍)。 您可以使用 [全選] 來選取所有 API。 如需 Power BI 存取權限的詳細資訊，請參閱 [Microsoft 身分識別平台端點中的權限和同意](/azure/active-directory/develop/v2-permissions-and-consent)。

5. 選取 [註冊]。

    Azure AD 應用程式 [應用程式識別碼] 與 [應用程式祕密] 值會顯示在 [摘要] 方塊中。 請複製這些值以供稍後使用。

[!INCLUDE[registration tool steps 6-7](../../includes/register-tool-steps-6-7.md)]

8. (選擇性) 如果您建立了 Power BI 的工作區，並使用工具將內容上傳到其中，您現在可以選取 [下載範例應用程式]。 請務必記得複製 [摘要] 方塊中的所有資訊。

[!INCLUDE[registration tool note](../../includes/register-tool-note.md)]

# <a name="manual-registration"></a>[手動註冊](#tab/manual)

只有當打算建立下列其中一個解決方案時，才使用 Azure AD 手動應用程式註冊：

* 「為您的組織內嵌」應用程式。

* 搭配「服務主體」的「為您的客戶內嵌」應用程式。

    >[!NOTE]
    >如果選擇此選項，在註冊 Azure AD 應用程式之後，您必須對其[新增 Power BI 權限](#change-your-azure-ad-apps-permissions)。

如需如何在 Azure Active Directory 中註冊應用程式的詳細資訊，請參閱[向 Azure Active Directory 註冊應用程式](/azure/active-directory/develop/quickstart-v2-register-an-app)。

1. 登入 [Azure 入口網站](https://portal.azure.com)。

2. 在頁面的右上角選取您的帳戶，以選取您的 Azure AD 租用戶。

3. 選取 **應用程式註冊**。 如果您看不到此選項，請進行搜尋。
 
4. 在 [應用程式註冊] 中，選取 [新增註冊]。

5. 填寫下列欄位：

    * **名稱** - 為您的應用程式命名。

    * **支援的帳戶類型** - 選取可以使用應用程式的人員。

6. (選擇性) 在 [重新導向 URI]中，新增一組重新導向 URL。

7. 選取 [註冊]。 註冊應用程式之後，系統會將您導向至應用程式的概觀頁面，您可以在此頁面取得「應用程式識別碼」。

---

## <a name="change-your-azure-ad-apps-permissions"></a>變更您 Azure AD 應用程式的權限

註冊應用程式之後，您可以對其權限進行變更。 您可以透過程式設計的方式變更權限，或在 Azure 入口網站中進行此動作。

>[!NOTE]
>Azure AD 應用程式權限僅適用於搭配「主使用者」驗證方法的「為您的客戶內嵌」解決方案。

# <a name="azure"></a>[Azure](#tab/Azure)

在 Azure 入口網站中，您可以檢視您的應用程式，並且變更其權限。

1. 登入 [Azure 入口網站](https://portal.azure.com)。

2. 在頁面的右上角選取您的帳戶，以選取您的 Azure AD 租用戶。

3. 選取 **應用程式註冊**。 如果您看不到此選項，請進行搜尋。

4. 在 [擁有的應用程式] 索引標籤中，選取您的應用程式。 應用程式隨即會在 [概觀] 索引標籤中開啟，您可以在此檢視 [應用程式識別碼]。

5. 選取 [API 權限] 索引標籤。

6. 遵循下列步驟新增權限：

    1. 選取 [新增權限]，然後選取 [Power BI 服務]。

    2. 選取 [委派權限]，然後新增或移除您需要的特定權限。

    3. 完成後，選取 [新增權限] 以儲存變更。

7. 遵循下列步驟移除權限：

    1. 選取權限右邊的省略號 (...)。
    
    2. 選取 [移除權限]。
    
    3. 在 [移除權限] 快顯視窗中，選取 [是，移除]。

# <a name="http"></a>[HTTP](#tab/HTTP)

若要以程式設計方式變更 Azure AD 應用程式的權限，您必須取得租用戶內現有的服務主體 (使用者)。 如需如何執行這項作業的資訊，請參閱 [servicePrincipal](/graph/api/resources/serviceprincipal)。

1. 若要取得租用戶內的所有服務主體，請呼叫不包含 `{ID}` 的 `Get servicePrincipal` API。

2. 使用應用程式的 [應用程式識別碼] (`appId` 屬性)，檢查服務主體。

    ```json
    Post https://graph.microsoft.com/v1.0/servicePrincipals HTTP/1.1
    Authorization: Bearer ey..qw
    Content-Type: application/json
    {
    "accountEnabled" : true,
    "appId" : "{App_Client_ID}",
    "displayName" : "{App_DisplayName}"
    }
    ```

    >[!NOTE]
    >`displayName` 是選擇性的。

3. 將下列其中一個值指派給 `consentType`，將 Power BI 權限授與您的應用程式：

    * `AllPrincipals` - 只能由 Power BI 系統管理員用來代表租用戶中的所有使用者授與權限。

    * `Principal` - 代表特定使用者授與權限。 如果您使用此選項，請將 `principalId={User_ObjectId}` 屬性新增至要求主體。

     ```json
     Post https://graph.microsoft.com/v1.0/OAuth2PermissionGrants HTTP/1.1
     Authorization: Bearer ey..qw
     Content-Type: application/json
     {
     "clientId":"{Service_Plan_ID}",
     "consentType":"AllPrincipals",
     "resourceId":"c78a3685-1ce7-52cd-95f7-dc5aea8ec98e",
     "scope":"Dataset.ReadWrite.All Dashboard.Read.All Report.Read.All Group.Read Group.Read.All Content.Create Metadata.View_Any Dataset.Read.All Data.Alter_Any",
     "expiryTime":"2018-03-29T14:35:32.4943409+03:00",
     "startTime":"2017-03-29T14:35:32.4933413+03:00"
     }
     ```

    >[!NOTE]
    >* 如果您使用 **主要使用者**，您必須將權限授與主要帳戶，以避免出現 Azure AD 同意提示。
    >* `resourceId` *c78a3685-1ce7-52cd-95f7-dc5aea8ec98e* 是取決於租用戶，並非一體適用。 此值為 Azure AD 中「Power BI 服務」應用程式的 *objectId*。 若要從 Azure 入口網站取得此值，請瀏覽至 [[企業應用程式] > [所有應用程式]](https://portal.azure.com/#blade/Microsoft_AAD_IAM/StartboardApplicationsMenuBlade/AllApps)，然後搜尋「Power BI 服務」。

4. 將值指派給 `consentType`，授與應用程式權限給 Azure AD。

    ```json
    Post https://graph.microsoft.com/v1.0/OAuth2PermissionGrants HTTP/1.1
    Authorization: Bearer ey..qw
    Content-Type: application/json
    {
    "clientId":"{Service_Plan_ID}",
    "consentType":"AllPrincipals",
    "resourceId":"61e57743-d5cf-41ba-bd1a-2b381390a3f1",
    "scope":"User.Read Directory.AccessAsUser.All",
    "expiryTime":"2018-03-29T14:35:32.4943409+03:00",
    "startTime":"2017-03-29T14:35:32.4933413+03:00"
    }
    ```

# <a name="c"></a>[C#](#tab/CSharp)

您也可以使用 C# 來變更您的 Azure AD 應用程式權限。 如需詳細資訊，請參閱 [oAuth2PermissionGrant](/graph/api/oauth2permissiongrant-get) \(英文\) API。 如果您想要將部分流程自動化，這個方法就很有用。

如需有關 HTTP 要求的詳細資訊，請參閱 [HTTP 索引標籤](register-app.md?tabs=customers%2CHTTP#change-your-azure-ad-apps-permissions)。

```csharp
var graphClient = GetGraphClient();

currentState.createdApp = await graphClient.Applications
    .Request()
    .AddAsync(application);

System.Threading.Thread.Sleep(2000);

var passwordCredential = new PasswordCredential
{
    DisplayName = "Client Secret Created in C#"
};

currentState.createdSecret = await graphClient.Applications[currentState.createdApp.Id]
    .AddPassword(passwordCredential)
    .Request()
    .PostAsync();

var servicePrincipal = new ServicePrincipal
{
    AppId = currentState.createdApp.AppId
};

currentState.createdServicePrincipal = await graphClient.ServicePrincipals
    .Request()
    .AddAsync(servicePrincipal);

GraphServiceClient graphClient = new GraphServiceClient(authProvider);

// Use oAuth2PermissionGrant to change permissions
var oAuth2PermissionGrant = await graphClient.Oauth2PermissionGrants["{id}"]
               .Request()
               .GetAsync();
```

---

## <a name="next-steps"></a>後續步驟

>[!div class="nextstepaction"]
>[取得 Power BI 應用程式的 Azure AD 存取權杖](get-azuread-access-token.md)

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)