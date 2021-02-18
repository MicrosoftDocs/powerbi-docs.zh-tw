---
title: 瞭解內嵌 Power BI 應用程式所需的許可權權杖
description: 瞭解 Power BI 應用程式向 Azure 和 Power BI 服務驗證所需的權杖。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: amshuste
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 02/17/2021
ms.openlocfilehash: 6a7847b0e89086094220a51a4893ffffd59d5642
ms.sourcegitcommit: fb408dfd39943dbec990a16bcf204671beb4f0aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/18/2021
ms.locfileid: "100656557"
---
# <a name="embedded-analytics-application-tokens"></a>Embedded analytics 應用程式權杖

若要使用 Power BI 內容，您需要存取權杖。 根據您的解決方案，此權杖可以是 [Azure AD token](#azure-ad-token) 或內嵌 [權杖](#embed-token)。

如果您使用 [ *針對您的客戶進行內嵌* ] 解決方案，則會根據您的應用程式所產生的 *內嵌權杖* ，授與 web 應用程式使用者 Power BI 內容 (的存取權，例如報表、儀表板和磚) 。

>[!NOTE]
>*針對您的客戶* 解決方案使用「內嵌」時，您可以使用任何驗證方法來允許存取您的 web 應用程式。

如果您使用「 *針對您的組織進行內嵌* 」解決方案，您的 web 應用程式使用者將會使用自己的認證來驗證 Azure AD。 您的應用程式使用者將可存取 Power BI 可在 Power BI 服務上存取的內容。

## <a name="azure-ad-token"></a>Azure AD 權杖

針對您的 *客戶所內嵌* 並針對 *您的組織* 解決方案進行內嵌，您需要 [Azure AD 權杖](#azure-ad-token)。 所有 [REST API](/rest/api/power-bi/) 作業都需要此權杖，而且會在一小時後到期。

* 在 *適用于您客戶的內嵌* 中，會使用 Azure AD token 來產生 *內嵌權杖*。

* 在 *您組織的內嵌* 中，Azure AD 權杖可用來存取 Power BI。

## <a name="embed-token"></a>內嵌的權杖

當您 *針對客戶* 解決方案使用「內嵌」時，您的 web 應用程式必須知道其使用者可以存取哪些 Power BI 內容。 使用 [內嵌權杖](/rest/api/power-bi/embedtoken) REST api 來產生內嵌 *權杖*，以指定下列各項：

* 您的 web 應用程式使用者可以存取的內容。

* Web 應用程式使用者的存取層級 (查看、建立或編輯) 。

如需詳細資訊，請參閱 [產生內嵌權杖時的考慮](generate-embed-token.md)。

## <a name="authentication-flows"></a>驗證流程

本節說明為 *您的客戶內嵌* 的驗證流程，並將其 *內嵌到您的組織內嵌* 解決方案。

### <a name="embed-for-your-customers"></a>為您的客戶內嵌

*適用于您客戶* 解決方案的內嵌會使用非互動式驗證流程。 使用者不需要登入 Azure AD，即可存取 Power BI。 相反地，您的 web 應用程式會使用專用的 Azure AD 身分識別來對 Azure AD 進行驗證，並產生 *內嵌權杖*。 專用身分識別可以是下列其中一項：

* **[服務主體](embed-service-principal.md)**

    您的 web 應用程式會使用 Azure AD [服務主體物件](/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object) 來對 Azure AD 進行驗證，並取得 *僅限應用程式 Azure AD 權杖*。 這是 *僅限應用程式* 的驗證方法，建議 Azure AD。

    使用 *服務主體* 時，您必須在 Power BI 服務系統 *管理員* 設定中 [啟用 Power BI api 存取](embed-sample-for-customers.md#step-6---service-principal-api-access)。 這可讓您的 web 應用程式存取 Power BI REST Api。 若要在工作區上使用 API 作業， *服務主體* 必須是工作區的 *成員* 或系統 *管理員* 。

* **主要使用者**

    您的 web 應用程式會使用使用者帳戶來對 Azure AD 進行驗證，並取得 *Azure AD 權杖*。 *主要使用者* 必須有 [Power BI Pro](/power-bi/admin/service-admin-purchasing-power-bi-pro)或 [PREMIUM 每位使用者 (PPU)](/power-bi/admin/service-premium-per-user-faq)授權。

    使用 *主要使用者* 時，您必須定義應用程式的 [委派許可權](/azure/active-directory/develop/v2-permissions-and-consent) (也稱為範圍) 。 需要 *主要使用者* 或 *租* 使用者系統管理員，才能使用 Power BI REST api 來授與使用這些許可權的同意。

成功驗證 Azure AD 之後，您的 web 應用程式將會產生內嵌 [權杖](/rest/api/power-bi/embedtoken) ，以允許其使用者存取特定的 Power BI 內容。

>[!NOTE]
>* 若要使用 *適用于您客戶的內嵌* 解決方案進行內嵌，您需要具有 a、EM 或 P SKU 的容量。
>* 若要 [移至生產環境](move-to-production.md) ，您需要一個容量。

下圖顯示適用于 *您客戶* 解決方案的內嵌驗證流程。

>[!div class="mx-imgBorder"]
>:::image type="content" source="media\embed-tokens\paas-authentiction.png" alt-text="內嵌給客戶 Power bi embedded 分析解決方案的驗證流程圖表。":::

1. Web 應用程式使用者會對您的 web 應用程式進行驗證， () 的驗證方法。

2. 您的 web 應用程式會使用 *服務主體* 或 *主要使用者* 來對 Azure AD 進行驗證。

3. 您的 web 應用程式會從 Azure AD 取得 *Azure AD 權杖* ，並使用它來存取 Power BI REST api。 系統會根據您的驗證方法（也就是 *服務主體* 或 *主要使用者*）提供 Power BI REST api 的存取權。

4. 您的 web 應用程式會呼叫內嵌 [權杖](/rest/api/power-bi/embedtoken) REST API 作業，要求 *內嵌權杖*。 內嵌 *權杖* 會指定可以內嵌 Power BI 內容。

5. REST API 會將 *內嵌權杖* 傳回到您的 web 應用程式。

6. Web 應用程式會將內嵌權杖傳遞給使用者的網頁瀏覽器。

7. Web 應用程式使用者使用內嵌權杖來存取 Power BI。

### <a name="embed-for-your-organization"></a>為您的組織內嵌

*您組織* 解決方案的內嵌會使用互動式驗證流程。 您的使用者會使用其 Power BI 認證針對 Azure AD 進行驗證。 使用者必須將同意授與向 Azure AD 註冊應用程式時所設定的 API 許可權。 同意會在 [要求的 Microsoft *許可權* ] 對話方塊快顯視窗中授與。 授與同意之後，就可以內嵌 Power BI 的內容，例如 web 應用程式使用者可存取的報表和儀表板。

>[!div class="mx-imgBorder"]
>:::image type="content" source="media/embed-tokens/requested-premissions.png" alt-text="顯示 Microsoft 許可權要求的快顯視窗的螢幕擷取畫面，要求客戶授與存取 Power bi 的許可權。":::

>[!NOTE]
>* *您組織* 解決方案的內嵌不支援 sku。
>* 若要 [移至生產環境](move-to-production.md) ，您需要下列其中一項設定：
>    * 具有 Pro 授權的所有使用者。
>    * 具有 PPU 授權的所有使用者。
>    * [容量](embedded-capacity.md)。 此設定可讓所有使用者擁有免費授權。

下圖顯示針對組織方案進行 *內嵌* 的驗證流程範例。

>[!div class="mx-imgBorder"]
>:::image type="content" source="media/embed-tokens/saas-authentiction.png" alt-text="在您的組織中，Power bi embedded 分析解決方案內嵌的驗證流程圖表。":::

1. Web 應用程式使用者存取 web 應用程式。

2. Web 應用程式會將 web 應用程式使用者重新導向至 Azure AD。

3. Web 應用程式使用者會使用其 Power BI 認證來對 Azure AD 進行驗證。

4. Azure AD 會將 web 應用程式使用者重新導向至具有隱含授與案例中 Azure AD token (的 web 應用程式，則會將存取權杖傳回給使用者的瀏覽器) 。

5. Web 應用程式會將 Azure AD token 傳遞給使用者的網頁瀏覽器。

6. Power BI web 應用程式會使用 Azure AD 權杖來內嵌 Power BI 的內容，例如，web 應用程式使用者有權存取的報表和儀表板。

## <a name="next-steps"></a>下一步

>[!div class="nextstepaction"]
>[產生內嵌權杖時的考量](generate-embed-token.md)

>[!div class="nextstepaction"]
>[Power BI 內嵌式分析中的容量和 SKU](embedded-capacity.md)

>[!div class="nextstepaction"]
>[有其他問題嗎？請嘗試在 Power BI 社群提問](https://community.powerbi.com/)