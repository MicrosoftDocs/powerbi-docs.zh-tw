---
title: 取得更佳的內嵌式 BI 見解：針對組織在 Power BI 內嵌式分析應用程式中內嵌內容
description: 了解如何使用內嵌式分析軟體、內嵌式分析工具，或內嵌式商業智慧工具，將 Power BI 整合到應用程式中。 使用 Power BI 內嵌式分析，取得更佳的內嵌式 BI 見解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: tutorial
ms.custom: seodec18
ms.date: 12/17/2020
ms.openlocfilehash: fbae63597ecf4ff36783ad83785f87c242359f90
ms.sourcegitcommit: 2e81649476d5cb97701f779267be59e393460097
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/02/2021
ms.locfileid: "99494931"
---
# <a name="tutorial-embed-power-bi-content-using-a-sample-embed-for-your-organization-application"></a>教學課程：使用 *適用于您組織* 應用程式的範例內嵌來內嵌 Power BI 內容

Power BI 內嵌式分析可讓您在應用程式中內嵌 Power BI 的內容，例如報表、儀表板和磚。

在本教學課程中，您將了解如何：

>[!div class="checklist"]
>* 設定您的內嵌環境。
>* 為 *您的組織* 設定內嵌 (也稱為 *使用者擁有資料*) 範例應用程式。

若要使用您的應用程式，您的使用者必須登入 Power BI。

「針對您的組織進行內嵌」解決方案通常是由企業與大型組織所使用，且適用於內部使用者。

## <a name="code-sample-specifications"></a>程式碼範例規格

本教學課程包含在下列其中一個架構中為組織範例應用程式設定內嵌 *的* 指示：

* .NET Framework
* .NET Core
* 回應 TypeScript

>[!NOTE]
>*.Net Core* 和 *.NET Framework* 範例可讓終端使用者在 Power BI 服務中，查看他們可存取的任何 Power BI 儀表板、報表或磚。 「 *回應 TypeScript* 」範例可讓您只內嵌一個報表，讓您的終端使用者在 Power BI 服務上已經有存取權。

程式碼範例支援下列瀏覽器：

* Microsoft Edge
* Google Chrome
* Mozilla Firefox

## <a name="prerequisites"></a>必要條件

開始進行本教學課程之前，請確認您具有Power BI 和下列程式碼相依性：

* **Power BI 相依性**

    * 您自己的 [Azure Active Directory 租用戶](create-an-azure-active-directory-tenant.md)。

    * 下列其中一個授權：

        * [Power BI Pro](../../admin/service-admin-purchasing-power-bi-pro.md)

        * [每位使用者 Premium (PPU) ](../../admin/service-premium-per-user-faq.md)

    >[!NOTE]
    >若要 [移至生產環境](move-to-production.md) ，您需要下列其中一項設定：
    >* 具有 Pro 授權的所有使用者。
    >* 具有 PPU 授權的所有使用者。
    >* [容量](embedded-capacity.md)。 此設定可讓所有使用者擁有免費授權。

* **程式碼相依性**

    # <a name="net-core"></a>[.NET Core](#tab/net-core)

    * [.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) (或更高版本)
    
    * 整合式開發環境 (IDE)。 建議您使用下列其中一項：

        * [Visual Studio](https://visualstudio.microsoft.com/)

        * [Visual Studio Code](https://code.visualstudio.com/)

    # <a name="net-framework"></a>[.NET Framework](#tab/net-framework)

    * [.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/)
    
    * [Visual Studio](https://visualstudio.microsoft.com/)

    # <a name="react-typescript"></a>[回應 TypeScript](#tab/react)

    * 文字編輯器

    * 命令列終端機 (或 PowerShell) 

---

## <a name="method"></a>方法

若要為 *您的組織* 範例應用程式建立內嵌，請遵循下列步驟：

1. [註冊 Azure AD 應用程式](#step-1---register-an-azure-ad-application)。

2. [建立 Power BI 工作區](#step-2---create-a-power-bi-workspace)。

3. [建立及發佈 Power BI 報表](#step-3---create-and-publish-a-power-bi-report)。

4. [取得內嵌參數值](#step-4---get-the-embedding-parameter-values)。

5. [內嵌內容](#step-5---embed-your-content)。

## <a name="step-1---register-an-azure-ad-application"></a>步驟 1-註冊 Azure AD 應用程式

使用 Azure AD 註冊您的應用程式，可讓您建立應用程式的身分識別。

[!INCLUDE[Register Azure AD app](../../includes/embed-tutorial-register-app.md)]

## <a name="step-2---create-a-power-bi-workspace"></a>步驟 2-建立 Power BI 工作區

[!INCLUDE[Create a Power BI workspace](../../includes/embed-tutorial-create-workspace.md)]

## <a name="step-3---create-and-publish-a-power-bi-report"></a>步驟 3-建立和發佈 Power BI 報表

[!INCLUDE[Create a Power BI report](../../includes/embed-tutorial-create-report.md)]

## <a name="step-4---get-the-embedding-parameter-values"></a>步驟 4-取得內嵌參數值

若要內嵌內容，您必須取得一些參數值。 您需要的參數值取決於您想要使用之範例應用程式的語言。 下表列出每個範例所需的參數值。

|參數  |.NET Core  |.NET Framework  |回應 TypeScript |
|---------|---------|---------|---------|
|[用戶端識別碼](#client-id) |![適用。](../../media/yes.png) |![適用。](../../media/yes.png)         |![適用。](../../media/yes.png) |
|[用戶端密碼](#workspace-id) |![適用。](../../media/yes.png) |![適用。](../../media/yes.png) |![不適用。](../../media/no.png) |
|[Workspace ID]() \(工作區識別碼\) |![不適用。](../../media/no.png) |![不適用。](../../media/no.png) |![適用。](../../media/yes.png) |
|[Report ID]() \(報表識別碼\) |![不適用。](../../media/no.png) |![不適用。](../../media/no.png) |![適用。](../../media/yes.png) |

### <a name="client-id"></a>用戶端識別碼

>[!TIP]
>**適用于：** ![適用 ](../../media/yes.png) 于 .。。NET Core ![ 適用于。 ](../../media/yes.png)NET Framework ![ 適用于。 ](../../media/yes.png)回應 TypeScript

[!INCLUDE[Get the client ID](../../includes/embed-tutorial-client-id.md)]

### <a name="client-secret"></a>用戶端密碼

>[!TIP]
>**適用于：** ![適用 ](../../media/yes.png) 于 .。。NET Core ![ 適用于。 ](../../media/yes.png)NET Framework ![ 並不適用于。 ](../../media/no.png)回應 TypeScript

[!INCLUDE[Get the client secret](../../includes/embed-tutorial-client-secret.md)]

### <a name="workspace-id"></a>工作區識別碼

>[!TIP]
>**適用于：** ![不適用 ](../../media/no.png) 于。NET Core 不 ![ 適用于。 ](../../media/no.png)NET Framework ![ 適用于。 ](../../media/yes.png)回應 TypeScript

[!INCLUDE[Get the workspace ID](../../includes/embed-tutorial-workspace-id.md)]

### <a name="report-id"></a>報表識別碼

>[!TIP]
>**適用于：** ![不適用 ](../../media/no.png) 于。NET Core 不 ![ 適用于。 ](../../media/no.png)NET Framework ![ 適用于。 ](../../media/yes.png)ReactTypeScript

[!INCLUDE[Get the report ID](../../includes/embed-tutorial-report-id.md)]

## <a name="step-5---embed-your-content"></a>步驟 5 - 內嵌內容

Power BI embedded 範例應用程式可讓您為 *組織* Power BI 應用程式建立內嵌。

請遵循下列步驟來修改 *您組織的內嵌* 範例應用程式，以內嵌您的 Power BI 報表。

[!INCLUDE[Embedding steps](../../includes/embed-tutorial-embedding-steps.md)]

4. 視您想要讓應用程式使用的語言而定，開啟下列其中一個資料夾：

    * .NET Core
    * .NET Framework
    * 回應-TS

    >[!NOTE]
    >*您組織的內嵌* 範例應用程式只支援上列架構。 *JAVA*、 *Node JS* 和 *Python* 範例應用程式，僅支援您的客戶解決方案的 *[內嵌](embed-sample-for-customers.md)*。

# <a name="net-core"></a>[.NET Core](#tab/net-core)

### <a name="configure-your-azure-ad-app"></a>設定您的 Azure AD 應用程式

[!INCLUDE[Configure the Azure AD authentication options](../../includes/embed-tutorial-org-azure-ad-app.md)]

5. 在 [ *平臺* 設定] 中，開啟您的 *Web* 平臺，然後在 [重新 **導向 uri** ] 區段中新增 `https://localhost:5000/signin-oidc` 。

    > [!NOTE]
    >如果您沒有 **Web** 平臺，請選取 [ **新增平臺** ]，然後在 [ *設定平臺* ] 視窗中選取 [ **Web**]。

6. 儲存您的變更。

:::image type="content" source="media/embed-sample-for-your-organization/azure-ad-net-configurations.png" alt-text="顯示 Azure AD 的應用程式驗證設定的螢幕擷取畫面，包括 .NET core 應用程式範例的 web 重新導向 U R I。":::

### <a name="configure-the-sample-embedding-app"></a>設定範例嵌入應用程式

1. 開啟 **您組織** 資料夾的 [內嵌]。

2. 使用下列其中一種方法開啟 *您組織的內嵌範例應用程式* ：

    * 如果您是使用 [Visual Studio](https://visualstudio.microsoft.com/)，請開啟 **UserOwnsData .sln** 檔案。

    * 如果您是使用 [Visual Studio Code](https://code.visualstudio.com/)，請開啟 [ **UserOwnsData** ] 資料夾。

3. 開啟 **appsettings.js開啟** 並填入下列參數值：

    * `ClientId` -使用 [用戶端識別碼](#client-id) GUID

    * `ClientSecret` -使用 [用戶端密碼](#client-secret)

### <a name="run-the-sample-app"></a>執行範例應用程式

1. 選取適當的選項來執行專案：

    * 如果您使用 **Visual Studio**，請選取 [IIS Express] (播放)。

    * 如果您使用 **Visual Studio Code**，請選取 [執行] > [開始偵錯]。

[!INCLUDE[The embedded application sample app interface](../../includes/embed-tutorial-org-sample-app.md)]

# <a name="net-framework"></a>[.NET Framework](#tab/net-framework)

### <a name="configure-your-azure-ad-app"></a>設定您的 Azure AD 應用程式

[!INCLUDE[Configure the Azure AD authentication options](../../includes/embed-tutorial-org-azure-ad-app.md)]

5. 在 [ *平臺* 設定] 中，設定下列各項：

    1. 在您的 *Web* 平臺中，于 [重新 **導向 uri** ] 區段中新增 `https://localhost:44300/` 。

        > [!NOTE]
        >如果您沒有 **Web** 平臺，請選取 [ **新增平臺** ]，然後在 [ *設定平臺* ] 視窗中選取 [ **Web**]。
    
    2. 在 [ *隱含授與] 和 [混合式流程*] 中，啟用 [ **識別碼權杖** ] 選項。
    
6. 儲存您的變更。

:::image type="content" source="media/embed-sample-for-your-organization/azure-ad-framework-configurations.png" alt-text="顯示 Azure AD 的應用程式驗證設定的螢幕擷取畫面，包括 web 重新導向 U R I 和 .NET framework 應用程式範例的選取存取權杖選項。":::

### <a name="configure-the-sample-embedding-app"></a>設定範例嵌入應用程式

1. 開啟 **您組織** 資料夾的 [內嵌]。

2. 使用 [Visual Studio](https://visualstudio.microsoft.com/)開啟 **UserOwnsData .sln** 檔案。

3. 開啟 **Web.config** 並填入下列參數值：

    * `clientId` -使用 [用戶端識別碼](#client-id) GUID

    * `clientSecret` -使用 [用戶端密碼](#client-secret)

### <a name="run-the-sample-app"></a>執行範例應用程式

1. 選取 [IIS Express] (播放) 以執行專案。

[!INCLUDE[The embedded application sample app interface](../../includes/embed-tutorial-org-sample-app.md)]

# <a name="react-typescript"></a>[回應 TypeScript](#tab/react)

### <a name="configure-your-azure-ad-app"></a>設定您的 Azure AD 應用程式

[!INCLUDE[Configure the Azure AD authentication options](../../includes/embed-tutorial-org-azure-ad-app.md)]

5. 在 [ *平臺* 設定] 中，設定您的 **Web** 平臺，如下所示：

    1. 在 [重新 **導向 uri** ] 中 `https://localhost:3000` ，新增並選取 [ **設定**]。

        > [!NOTE]
        >如果您沒有 **Web** 平臺，請選取 [ **新增平臺** ]，然後在 [ *設定平臺* ] 視窗中選取 [ **Web**]。

    2. 在 *隱含授與和混合式流程* 中，同時啟用這兩個選項：
        * **存取權杖**
        * **識別碼權杖**
    
6. 儲存您的變更。

:::image type="content" source="media/embed-sample-for-your-organization/azure-ad-react-configurations.png" alt-text="顯示 Azure AD 的應用程式驗證設定的螢幕擷取畫面，包括針對 localhost 3000 設定的 web 重新導向 U R I。":::

### <a name="configure-the-sample-embedding-app"></a>設定範例嵌入應用程式

1. 開啟 **您組織** 的 [內嵌]  >  **UserOwnsData**  >  **src** 資料夾。

2. 使用文字編輯器開啟 **config.xml** 檔案，並填入下列參數值：

    * `clientId` -使用 [用戶端識別碼](#client-id) GUID

    * `workspaceId` -使用 [工作區識別碼](#client-secret)

    * `reportId` -使用 [報表識別碼](#report-id)

3. 儲存檔案。

### <a name="run-the-sample-app"></a>執行範例應用程式

1. 在中開啟終端機，並流覽至 **您的組織 UserOwnsData 的 [內嵌**]  >  ****。

2. 藉由執行下列命令來安裝必要的相依性：

   `npm install`

3. 執行下列命令來執行應用程式：

   `npm run start`

    >[!NOTE]
    >在您第一次登入時，系統會提示您允許應用程式的 Azure AD 許可權。

---

## <a name="developing-your-application"></a>開發您的應用程式

設定並執行「對客戶進行內嵌」範例應用程式之後，您就可以開始開發自己的應用程式。

[!INCLUDE[Move to production](../../includes/embed-tutorial-production.md)]

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
>[移至生產環境](move-to-production.md)

>[!div class="nextstepaction"]
>[對客戶進行內嵌](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[為客戶內嵌編頁報表](embed-paginated-reports-customers.md)

> [!div class="nextstepaction"]
>[為組織內嵌分頁報表](embed-paginated-reports-organization.md)

>[!div class="nextstepaction"]
>[詢問 Power BI 社群](https://community.powerbi.com/)