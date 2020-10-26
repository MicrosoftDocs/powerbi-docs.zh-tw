---
title: 使用服務主體和應用程式祕密內嵌 Power BI 內容
description: 了解如何使用 Azure Active Directory 應用程式服務主體和應用程式祕密，驗證內嵌的分析。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.custom: ''
ms.date: 10/15/2020
ms.openlocfilehash: 6f6a13f239d1bcfa7731361f4efcd129da7e2031
ms.sourcegitcommit: 1428acb6334649fc2d3d8ae4c42cfbc17e8f7476
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2020
ms.locfileid: "92197720"
---
# <a name="embed-power-bi-content-with-service-principal-and-an-application-secret"></a>使用服務主體和應用程式祕密內嵌 Power BI 內容

[!INCLUDE[service principal overview](../../includes/service-principal-overview.md)]

本文說明使用「應用程式識別碼」和「應用程式祕密」來進行服務主體驗證。

>[!NOTE]
>建議您使用憑證來保護您的後端服務，而不使用祕密金鑰。
>* [深入了解如何使用祕密金鑰或憑證從 Azure AD 取得存取權杖](/azure/architecture/multitenant-identity/client-assertion)。
>* [使用服務主體和憑證內嵌 Power BI 內容](embed-service-principal-certificate.md)。

## <a name="method"></a>方法

若要使用服務主體和具有內嵌分析的應用程式識別碼，請遵循下列步驟：

1. 建立 [Azure AD 應用程式](/azure/active-directory/manage-apps/what-is-application-management)。

    1. 建立 Azure AD 應用程式的祕密。
    
    2. 取得應用程式的「應用程式識別碼」和「應用程式祕密」。

    >[!NOTE]
    >**步驟 1**中描述這些步驟。 如需建立 Azure AD 應用程式的詳細資訊，請參閱[建立 Azure AD 應用程式](/azure/active-directory/develop/howto-create-service-principal-portal) (部分機器翻譯) 一文。

2. 建立 Azure AD 安全性群組。

3. 啟用 Power BI 服務系統管理員設定。

4. 將服務主體新增至您的工作區。

5. 內嵌內容。

> [!IMPORTANT]
> 一旦您啟用要與 Power BI 搭配使用的服務主體，應用程式的 AD 使用權限就不再生效。 然後，應用程式的使用權限會透過 Power BI 系統管理入口網站管理。

## <a name="step-1---create-an-azure-ad-app"></a>步驟 1 - 建立 Azure AD 應用程式

使用下列其中一種方法來建立 Azure AD 應用程式：

* 在 [Microsoft Azure 入口網站](https://portal.azure.com/#allservices)中建立應用程式

* 使用 [PowerShell](/powershell/azure/create-azure-service-principal-azureps) 建立應用程式。

### <a name="creating-an-azure-ad-app-in-the-microsoft-azure-portal"></a>在 Microsoft Azure 入口網站中建立 Azure AD 應用程式

[!INCLUDE[service create app](../../includes/service-principal-create-app.md)]

7. 按一下 [憑證與祕密] 索引標籤。

     ![顯示 Azure 入口網站中某個應用程式的 [憑證及祕密] 窗格的螢幕擷取畫面。](media/embed-service-principal/certificates-and-secrets.png)


8. 按一下 [新增用戶端密碼]

    ![顯示 [憑證及祕密] 窗格中 [新增用戶端密碼] 按鈕的螢幕擷取畫面。](media/embed-service-principal/new-client-secret.png)

9. 在 [新增用戶端密碼] 視窗中，輸入描述，指定您要讓用戶端密碼到期的時間，然後按一下 [新增]。

10. 複製並儲存 [用戶端密碼] 值。

    ![顯示 [憑證及祕密] 窗格中已模糊處理之祕密值的螢幕擷取畫面。](media/embed-service-principal/client-secret-value.png)

    >[!NOTE]
    >在您離開此視窗之後，用戶端密碼值將會隱藏，而且您將無法再次檢視或複製。

### <a name="creating-an-azure-ad-app-using-powershell"></a>使用 PowerShell 建立 Azure AD 應用程式

本節包含使用 [PowerShell](/powershell/azure/create-azure-service-principal-azureps) 建立新 Azure AD 應用程式的範例指令碼。

```powershell
# The app ID - $app.appid
# The service principal object ID - $sp.objectId
# The app key - $key.value

# Sign in as a user that's allowed to create an app
Connect-AzureAD

# Create a new Azure AD web application
$app = New-AzureADApplication -DisplayName "testApp1" -Homepage "https://localhost:44322" -ReplyUrls "https://localhost:44322"

# Creates a service principal
$sp = New-AzureADServicePrincipal -AppId $app.AppId

# Get the service principal key
$key = New-AzureADServicePrincipalPasswordCredential -ObjectId $sp.ObjectId
```
[!INCLUDE[service create steps two, three and four](../../includes/service-principal-create-steps.md)]

## <a name="step-5---embed-your-content"></a>步驟 5 - 內嵌內容

您可以在範例應用程式或您自己的應用程式中內嵌內容。

* [使用範例應用程式來內嵌內容](embed-sample-for-customers.md#embed-content-using-the-sample-application)
* [在應用程式中內嵌內容](embed-sample-for-customers.md#embed-content-within-your-application)

您的內容內嵌之後，您就可以[移至生產環境](embed-sample-for-customers.md#move-to-production)。

[!INCLUDE[service principal limitations](../../includes/service-principal-limitations.md)]

## <a name="next-steps"></a>後續步驟

>[!div class="nextstepaction"]
>[註冊應用程式](register-app.md)

> [!div class="nextstepaction"]
>[適用於您客戶的 Power BI Embedded](embed-sample-for-customers.md)

>[!div class="nextstepaction"]
>[Azure Active Directory 中的應用程式和服務主體物件](/azure/active-directory/develop/app-objects-and-service-principals)

>[!div class="nextstepaction"]
>[搭配服務主體使用內部部署資料閘道的資料列層級安全性](embedded-row-level-security.md#on-premises-data-gateway-with-service-principal)

>[!div class="nextstepaction"]
>[使用服務主體和憑證內嵌 Power BI 內容](embed-service-principal-certificate.md)