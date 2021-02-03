---
title: 取得更佳的內嵌式 BI 見解：針對客戶在 Power BI 內嵌式分析應用程式中內嵌內容
description: 了解如何將報表、儀表板或磚內嵌至 Power BI 內嵌分析範例。 使用 Power BI 內嵌式分析，取得更佳的內嵌 BI 見解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.topic: tutorial
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: seodec18
ms.date: 12/22/2020
ms.openlocfilehash: 28081342763ca297648f67f953a29b46d02bf478
ms.sourcegitcommit: 2e81649476d5cb97701f779267be59e393460097
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/02/2021
ms.locfileid: "99494588"
---
# <a name="tutorial-embed-power-bi-content-using-a-sample-embed-for-your-customers-application"></a>教學課程：使用「對客戶進行內嵌」範例應用程式內嵌 Power BI 內容

**內嵌式分析** 和 **Power BI Embedded** (Azure 供應項目) 可讓您將 Power BI 的內容 (例如報表、儀表板和磚) 內嵌到應用程式中。

在本教學課程中，您將了解如何：

>[!div class="checklist"]
>* 設定您的內嵌環境。
>* 設定「對客戶進行內嵌」(也稱為「應用程式擁有資料」) 範例應用程式。

若要使用您的應用程式，使用者將不需要登入 Power BI 或擁有 Power BI 授權。

如果您是獨立軟體廠商 (ISV) 或開發人員，而且想要為協力廠商建立應用程式，建議使用「對客戶進行內嵌」方法來內嵌您的 Power BI 內容。

## <a name="code-sample-specifications"></a>程式碼範例規格

本教學課程包含在下列其中一個架構中為 *您的客戶* 範例應用程式設定內嵌的指示：

* .NET Framework
* .NET Core
* Java
* Node JS
* Python

程式碼範例支援下列瀏覽器：

* Microsoft Edge
* Google Chrome
* Mozilla Firefox

## <a name="prerequisites"></a>必要條件

開始進行本教學課程之前，請確認您具有Power BI 和下列程式碼相依性：

* **Power BI 相依性**

    * 您自己的 [Azure Active Directory 租用戶](create-an-azure-active-directory-tenant.md)。

    * 若要對 Power BI 驗證您的應用程式，您需要下列其中一項：

        * [服務主體](embed-service-principal.md) - Azure Active Directory (Azure AD) [服務主體物件](/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object)，可讓 Azure AD 驗證您的應用程式。

        * [Power BI Pro](../../admin/service-admin-purchasing-power-bi-pro.md) 授權 - 這會是您的 **主要使用者**，而您的應用程式會使用此授權向 Power BI 驗證。

        * Power BI [Premium Per User (PPU)](../../admin/service-premium-per-user-faq.md) 授權 - 這會是您的 **主要使用者**，而您的應用程式會使用此授權向 Power BI 驗證。

    >[!NOTE]
    >若要[移至實際執行環境](move-to-production.md)，您將需要[容量](embedded-capacity.md)。

* **程式碼相依性**

    # <a name="net-core"></a>[.NET Core](#tab/net-core)
    
    * [.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) (或更高版本)
    
    * 整合式開發環境 (IDE)。 建議您使用下列其中一項：
    
        * [Visual Studio](https://visualstudio.microsoft.com/)
    
        * [Visual Studio Code](https://code.visualstudio.com/)

    # <a name="net-framework"></a>[.NET Framework](#tab/net-framework)
    
    * [.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/)
    
    * [Visual Studio](https://visualstudio.microsoft.com/)

    # <a name="java"></a>[Java](#tab/java)
    
    * [JDK (或 JRE)](https://www.oracle.com/java/technologies/)
    
    * [Eclipse IDE](https://www.eclipse.org/downloads/packages/) - 確認您擁有 *Eclipse for Java EE Developers* (企業版)
    
    * [Apache Tomcat Binary Distributions](https://tomcat.apache.org/)
    
    # <a name="node-js"></a>[Node JS](#tab/node-js)
    
    * [.NET Framework 4.8](https://dotnet.microsoft.com/download/dotnet-framework/)
    
    * 整合式開發環境 (IDE)。 建議您使用下列其中一項：
    
        * [Visual Studio](https://visualstudio.microsoft.com/)
    
        * [Visual Studio Code](https://code.visualstudio.com/)
    
    # <a name="python"></a>[Python](#tab/python)
    
    * [Python 3](https://www.python.org/downloads/) (或更高版本)
    
        >[!NOTE]
        >* 如果您是第一次安裝 *Python*，請選取 [Add Python to PATH] \(將 Python 新增至 PATH\) 選項，將安裝新增至 `PATH` 變數。
        >* 如果您已安裝 *Python*，請確認 `PATH` 變數包含其安裝路徑。 如需詳細資訊，請參閱 [Excursus:Setting environment variables](https://docs.python.org/3/using/windows.html#excursus-setting-environment-variables) (附錄：設定環境變數) Python 文件 (此連結指的是 Python 3)。
    
    * 整合式開發環境 (IDE)。 建議您使用下列其中一項：
    
        * [Visual Studio](https://visualstudio.microsoft.com/)
    
        * [Visual Studio Code](https://code.visualstudio.com/)
    
    ---

## <a name="method"></a>方法

若要建立「對客戶進行內嵌」範例應用程式，請遵循下列步驟：

1. [選取您的驗證方法](#step-1---select-your-authentication-method)。

2. [註冊 Azure AD 應用程式](#step-2---register-an-azure-ad-application)。

3. [建立 Power BI 工作區](#step-3---create-a-power-bi-workspace)。

4. [建立及發佈 Power BI 報表](#step-4---create-and-publish-a-power-bi-report)。

5. [取得內嵌參數值](#step-5---get-the-embedding-parameter-values)。

6. [服務主體 API 存取](#step-6---service-principal-api-access)
 
7. [啟用工作區存取](#step-7---enable-workspace-access)。

8. [內嵌內容](#step-8---embed-your-content)。

## <a name="step-1---select-your-authentication-method"></a>步驟 1 - 選取您的驗證方法

您的內嵌解決方案會根據所選取的驗證方法而有所不同。 因此，請務必了解驗證方法之間的差異，並決定哪一種方法最適合您的解決方案。

下表描述 [服務主體](embed-service-principal.md)與 **主要使用者** 驗證方法之間的一些主要差異。

|考量  |服務主體  |主要使用者  |
|---------|---------|---------|
|機制     |Azure AD 應用程式的[服務主體物件](/azure/active-directory/develop/app-objects-and-service-principals#service-principal-object)可讓 Azure AD 針對 Power BI 驗證您的內嵌解決方案應用程式。        |您的 Azure AD 應用程式會使用 Power BI 使用者的認證 (使用者名稱和密碼) 針對 Power BI 進行驗證。         |
|安全性     |「服務主體」是 Azure AD 建議的授權方法。 如果您使用服務主體，則可以使用「應用程式祕密」或「憑證」來進行驗證。</br></br>本教學課程僅描述如何搭配使用「服務主體」與「應用程式祕密」。 若要使用「服務主體」和「憑證」進行內嵌，請參閱[搭配憑證的服務主體](embed-service-principal-certificate.md)一文。         |一般認為此驗證方法不像使用「服務主體」那麼安全。 這是因為您必須小心處理「主要使用者」認證 (使用者名稱和密碼)。 例如，您不得在內嵌應用程式中將其公開，而且應該經常變更密碼。         |
|Azure AD 委派的權限 |不需要。 |您的「主要使用者」或系統管理員必須授與同意，才能讓您的應用程式存取 Power BI REST API [權限](/azure/active-directory/develop/v2-permissions-and-consent) (也稱為範圍)。 例如，*Report.ReadWrite.All*。 |
|Power BI 服務存取 |您無法使用「服務主體」來存取 Power BI 服務。|您可以使用「主要使用者」認證來存取 Power BI 服務。|
|授權     |不需要 Pro 授權。 您可以從任何自己是成員或系統管理員的工作區使用內容。         |需要 [Power BI Pro](../../admin/service-admin-purchasing-power-bi-pro.md) 授權。         |

## <a name="step-2---register-an-azure-ad-application"></a>步驟 2 - 註冊 Azure AD 應用程式

向 Azure AD 註冊應用程式可讓您：
> [!div class="checklist"]
>* 建立應用程式的身分識別
>* 讓您的應用程式存取 [Power BI REST API](/rest/api/power-bi/)
>* 如果您使用「主要使用者」 - 指定應用程式的 [Power BI REST 權限](/azure/active-directory/develop/v2-permissions-and-consent)

[!INCLUDE[Register Azure AD app](../../includes/embed-tutorial-register-app.md)]

>[!NOTE]
>在註冊應用程式之前，您必須決定要使用哪種驗證方法：「服務主體」或「主要使用者」。

## <a name="step-3---create-a-power-bi-workspace"></a>步驟 3 - 建立 Power BI 工作區

[!INCLUDE[Create a Power BI workspace](../../includes/embed-tutorial-create-workspace.md)]

## <a name="step-4---create-and-publish-a-power-bi-report"></a>步驟4 - 建立及發佈 Power BI 報表

[!INCLUDE[Create a Power BI report](../../includes/embed-tutorial-create-report.md)]

## <a name="step-5---get-the-embedding-parameter-values"></a>步驟 5 - 取得內嵌參數值

若要內嵌內容，您必須取得特定的參數值。 下表顯示所需的值，並指出它們是否適用于 *服務主體* 驗證方法、 *主要使用者* 驗證方法，或兩者皆適用。

在內嵌內容之前，請確定您擁有下列所有值。 某些值會根據您使用的驗證方法而有所不同。

|參數   |服務主體   |主要使用者  |
|-------------------|---|---|
|[用戶端識別碼](#client-id) |![適用。](../../media/yes.png) |![適用。](../../media/yes.png) |
|[Workspace ID](#workspace-id) \(工作區識別碼\)     |![適用。](../../media/yes.png) |![適用。](../../media/yes.png) |
|[Report ID](#report-id) \(報表識別碼\)           |![適用。](../../media/yes.png) |![適用。](../../media/yes.png) |
|[用戶端密碼](#client-secret) |![適用。](../../media/yes.png) |![不適用。](../../media/no.png) |
|[租用戶識別碼](#tenant-id)                 |![適用。](../../media/yes.png) |![不適用。](../../media/no.png) |
|[Power BI 使用者名稱](#power-bi-username-and-password)   |![不適用。](../../media/no.png) |![適用。](../../media/yes.png) |
|[Power BI 密碼](#power-bi-username-and-password)   |![不適用。](../../media/no.png) |![適用。](../../media/yes.png) |

### <a name="client-id"></a>用戶端識別碼

>[!TIP]
>**適用於︰** ![適用。](../../media/yes.png)服務主體 ![適用。](../../media/yes.png)主要使用者

[!INCLUDE[Get the client ID](../../includes/embed-tutorial-client-id.md)]

### <a name="workspace-id"></a>工作區識別碼

>[!TIP]
>**適用於︰** ![適用。](../../media/yes.png)服務主體 ![適用。](../../media/yes.png)主要使用者

[!INCLUDE[Get the workspace ID](../../includes/embed-tutorial-workspace-id.md)]

### <a name="report-id"></a>報表識別碼

>[!TIP]
>**適用於︰** ![適用。](../../media/yes.png)服務主體 ![適用。](../../media/yes.png)主要使用者

[!INCLUDE[Get the report ID](../../includes/embed-tutorial-report-id.md)]

### <a name="client-secret"></a>用戶端密碼

>[!TIP]
>**適用於︰** ![適用。](../../media/yes.png)服務主體 ![不適用。](../../media/no.png)主要使用者

[!INCLUDE[Get the client secret](../../includes/embed-tutorial-client-secret.md)]

### <a name="tenant-id"></a>租用戶識別碼

>[!TIP]
>**適用於︰** ![適用。](../../media/yes.png)服務主體 ![不適用。](../../media/no.png)主要使用者

若要取得租用戶識別碼 GUID，請遵循下列步驟：

1. 登入 [Microsoft Azure](https://ms.portal.azure.com/#allservices)。

2. 搜尋 **應用程式註冊**，然後選取 [應用程式註冊] 連結。

3. 選取您用來內嵌 Power BI 內容的 Azure AD 應用程式。

4. 從 [概觀] 區段中，複製 [目錄 (租用戶) 識別碼] GUID。

### <a name="power-bi-username-and-password"></a>Power BI 使用者名稱及密碼

>[!TIP]
>**適用於︰** ![不適用。](../../media/no.png)服務主體 ![適用。](../../media/yes.png)主要使用者

針對您要作為 **主要使用者** 的 Power BI 使用者，取得其「使用者名稱」和「密碼」。 這是 Power BI 服務中您用來建立工作區並將報表上傳到其中的相同使用者。

## <a name="step-6---service-principal-api-access"></a>步驟 6 - 服務主體 API 存取

>[!TIP]
>**適用於︰** ![適用。](../../media/yes.png)服務主體 ![不適用。](../../media/no.png)主要使用者
>
>只有當您使用「服務主體」驗證方法時，此步驟才有意義。 如果您使用「主要使用者」，請略過此步驟，並繼續進行[步驟 7 - 啟用工作區存取](#step-7---enable-workspace-access)。

若要讓 Azure AD 應用程式能夠存取 Power BI 內容和 API，Power BI 系統管理員必須在 Power BI 系統管理員入口網站中啟用服務主體存取權。 如果您不是租用戶的系統管理員，請讓租用戶的系統管理員為您啟用「租用戶設定」。
        
1. 在「Power BI 服務」中，選取 [設定] > [設定] > [系統管理員入口網站]。
        
    :::image type="content" source="media/embed-sample-for-customers/admin-settings.png" alt-text="此螢幕擷取畫面顯示 Power BI 服務 [設定] 功能表中的系統管理員設定功能表選項":::
        
2. 選取 [租用戶設定]，然後向下捲動至 [開發人員設定] 區段。
        
3. 展開 [允許服務主體使用 Power BI API]，並啟用此選項。
        
    :::image type="content" source="media/embed-sample-for-customers/developer-settings.png" alt-text="此螢幕擷取畫面顯示如何在 Power BI 服務的 [租用戶設定] 功能表選項中啟用 [開發人員設定] 選項":::
        
>[!NOTE]
>使用「服務主體」時，建議您使用「安全性群組」來限制其對租用戶設定的存取權。 若要深入了解這項功能，請參閱[服務主體](embed-service-principal.md)一文中的下列小節：
> * [建立 Azure AD 安全性群組](embed-service-principal.md#step-2---create-an-azure-ad-security-group)
>* [啟用 Power BI 服務系統管理員設定](embed-service-principal.md#step-3---enable-the-power-bi-service-admin-settings)

## <a name="step-7---enable-workspace-access"></a>步驟 7 - 啟用工作區存取

若要啟用 Azure AD 應用程式存取成品 (例如 Power BI 服務中的報表、儀表板和資料集)，請將「服務主體」或「主要使用者」新增為您工作區的「成員」或「系統管理員」。

1. 登入 Power BI 服務。

2. 捲動至您想要啟用存取權的工作區，然後從 [更多] 功能表中，選取 [工作區存取權]。

    :::image type="content" source="media/embed-service-principal/workspace-access.png" alt-text="螢幕擷取畫面顯示 Power BI 工作區之更多功能表中的 [工作區存取] 按鈕。":::

3. 在 [存取] 窗格中，視您使用的驗證方法而定，將「服務主體」或「主要使用者」複製到 [輸入電子郵件地址] 文字方塊。

    >[!NOTE]
    >如果您使用「服務主體」，其名稱就是您提供給 Azure AD 應用程式的名稱。

4. 選取 [新增]。

## <a name="step-8---embed-your-content"></a>步驟 8 - 內嵌您的內容

Power BI Embedded 範例應用程式可讓您建立「對客戶進行內嵌」 Power BI 應用程式。

請遵循下列步驟來修改「對客戶進行內嵌」範例應用程式，以內嵌您的 Power BI 報表。  

[!INCLUDE[Embedding steps](../../includes/embed-tutorial-embedding-steps.md)]

4. 視您想要讓應用程式使用的語言而定，開啟下列其中一個資料夾：

    * .NET Core
    * .NET Framework
    * Java
    * Node JS
    * Python

    >[!NOTE]
    >*適用于您客戶的內嵌* 範例應用程式只支援以上所列的架構。 *回應* 範例應用程式只支援 *[您組織](embed-sample-for-your-organization.md)* 解決方案的內嵌。

5. 開啟 **對客戶進行內嵌** 資料夾。

# <a name="net-core"></a>[.NET Core](#tab/net-core)

6. 使用下列其中一種方法，開啟「對客戶進行內嵌範例應用程式」：

    * 如果您使用的是 [Visual Studio](https://visualstudio.microsoft.com/)，請開啟 **AppOwnsData.sln** 檔案。

    * 如果您是使用 [Visual Studio Code](https://code.visualstudio.com/)，請開啟 [ **AppOwnsData** ] 資料夾。

7. 開啟 **appsettings.json**。

8. 根據您的驗證方法，填入下列參數值：

    |參數            |服務主體  |主要使用者  |
    |---------------------|---------|---------|
    |`AuthenticationMode` |ServicePrincipal         |MasterUser         |
    |`ClientId`           |您的 Azure AD 應用程式[用戶端識別碼](#client-id)         |您的 Azure AD 應用程式[用戶端識別碼](#client-id)         |
    |`TenantId`           |您的 Azure AD [租用戶識別碼](#tenant-id)         |N/A         |
    |`PbiUsername`        |N/A         |您的「主要使用者」使用者名稱，請參閱 [Power BI 使用者名稱和密碼](#power-bi-username-and-password)         |
    |`PbiPassword`        |N/A         |您的「主要使用者」密碼，請參閱 [Power BI 使用者名稱和密碼](#power-bi-username-and-password)         |
    |`ClientSecret`       |您的 Azure AD [用戶端祕密](#client-secret)         |N/A         |
    |`WorkspaceId`        |內嵌報表所在工作區的識別碼，請參閱[工作區識別碼](#workspace-id)          |內嵌報表所在工作區的識別碼，請參閱[工作區識別碼](#workspace-id)         |
    |`ReportId`           |所要內嵌報表的識別碼，請參閱[報表識別碼](#report-id)            |所要內嵌報表的識別碼，請參閱[報表識別碼](#report-id)         |

9. 選取適當的選項來執行專案：

    * 如果您使用 **Visual Studio**，請選取 [IIS Express] (播放)。

    * 如果您使用 **Visual Studio Code**，請選取 [執行] > [開始偵錯]。

# <a name="net-framework"></a>[.NET Framework](#tab/net-framework)

6. 使用 [Visual Studio](https://visualstudio.microsoft.com/)，開啟 **AppOwnsData.sln** 檔案。

7. 開啟 **Web.config**。

8. 根據您的驗證方法，填入下列參數值：

    |參數            |服務主體  |主要使用者  |
    |---------------------|---------|---------|
    |`authenticationType` |ServicePrincipal         |MasterUser         |
    |`applicationId`           |您的 Azure AD 應用程式[用戶端識別碼](#client-id)         |您的 Azure AD 應用程式[用戶端識別碼](#client-id)         |
    |`workspaceId`        |內嵌報表所在工作區的識別碼，請參閱[工作區識別碼](#workspace-id)          |內嵌報表所在工作區的識別碼，請參閱[工作區識別碼](#workspace-id)         |
    |`reportId`           |所要內嵌報表的識別碼，請參閱[報表識別碼](#report-id)            |所要內嵌報表的識別碼，請參閱[報表識別碼](#report-id)         |
    |`pbiUsername`        |N/A         |您的「主要使用者」使用者名稱，請參閱 [Power BI 使用者名稱和密碼](#power-bi-username-and-password)         |
    |`pbiPassword`        |N/A         |您的「主要使用者」密碼，請參閱 [Power BI 使用者名稱和密碼](#power-bi-username-and-password)         |
    |`applicationSecret`       |您的 Azure AD [用戶端祕密](#client-secret)         |N/A         |
    |`tenant`           |您的 Azure AD [租用戶識別碼](#tenant-id)         |N/A         |

9. 選取 [IIS Express] (播放) 以執行專案。

# <a name="java"></a>[Java](#tab/java)

6. 開啟 **Eclipse**，並遵循下方所述的指示。

    >[!NOTE]
    >適用於 Java「對客戶進行內嵌範例應用程式」的指示，請參閱 [Eclipse IDE for Java EE Developers](https://www.eclipse.org/downloads/packages/) (企業版)。 如果您使用不同的應用程式，則必須自行設定。

7. 將 Tomcat 伺服器新增至 Eclipse：

    a. 選取 [Window] \(視窗\) > [Show View] \(顯示檢視\) > [Servers] \(伺服器\)。

    b. 在 [Servers] \(伺服器\) 索引標籤中，選取 [No servers are available.Click this link to create new server] \(沒有可用的伺服器。按一下此連結以建立新的伺服器\)。

    c. 在 [Define a New Server] \(定義新的伺服器\) 視窗中，展開 [Apache]，然後選取您要在電腦上執行的 Tomcat 伺服器。 例如，*Tomcat v9.0 Server*。

    d. 選取 [下一步]  。

    e. 在 [Tomcat Server] \(Tomcat 伺服器\) 視窗中，選取 [Browse] \(瀏覽\)，然後巡覽至包含 Tomcat 伺服器的資料夾。

    f. 在 [Tomcat Server] \(Tomcat 伺服器\) 視窗中，選取 [Installed JREs] \(安裝的 JRE\)。

    g. 在 [Installed JREs] \(安裝的 JRE\) 視窗中，選取可用的 *jre*，然後選取 [Apply and Close] \(套用並關閉\)。

    h. 在 [Tomcat Server] \(Tomcat 伺服器\) 視窗中，選取 [Finish] \(完成\)。 您就能夠在 [Servers] \(伺服器\) 索引標籤中看到 Tomcat 伺服器。

8. 在 Eclipse 中開啟專案：

    >[!IMPORTANT]
    >如果您的路徑名稱太長，Eclipse 可能會發生問題。 若要避免這個問題，請確認範例應用程式資料夾在電腦資料夾結構中的巢狀層級並未太深。

    a. 選取 [File] \(檔案\)，然後選取 [Open Projects from File System] \(從檔案系統開啟專案\)。

    b. 在 [Import Projects form File System or Archive] \(從檔案系統或封存匯入專案\) 視窗中，選取 [Directory] \(目錄\) 並開啟 **AppOwnsData** 資料夾。

    c. 選取 [完成]。

9. 將 Tomcat 伺服器新增至專案：

    a. 在 [Package Explorer] \(套件總管\) 窗格中，以滑鼠右鍵按一下 **AppOwnsData**，然後選取 [Properties] \(屬性\)。

    b. 在 [Properties for AppOwnesData] \(AppOwnesData 的屬性\) 視窗中，選取 [Targeted Runtimes] \(目標執行階段\)，然後選取 [Apache Tomcat]。 此選項會包含您所使用的 *Apache tomcat* 版本，例如 *apache tomcat 9.0*。

    c. 選取 [Apply and Close] \(套用並關閉\)。

10. 填入必要的參數

    a. 在 [Package explorer] \(套件總管\) 中，展開 **AppOwnsData** 專案。

    b. 展開 [Java Resources] \(Java 資源\)。

    c. 展開 **src**。

    d. 展開 **com.embedsample.appoensdata.config**。

    e. 開啟 **Config.java**。

    f. 根據您的驗證方法，填入下列參數值：

    |參數            |服務主體  |主要使用者  |
    |---------------------|---------|---------|
    |`authenticationType` |ServicePrincipal         |MasterUser         |
    |`workspaceId`        |內嵌報表所在工作區的識別碼，請參閱[工作區識別碼](#workspace-id)          |內嵌報表所在工作區的識別碼，請參閱[工作區識別碼](#workspace-id)         |
    |`reportId`           |所要內嵌報表的識別碼，請參閱[報表識別碼](#report-id)            |所要內嵌報表的識別碼，請參閱[報表識別碼](#report-id)         | 
    |`clientId`           |您的 Azure AD 應用程式[用戶端識別碼](#client-id)         |您的 Azure AD 應用程式[用戶端識別碼](#client-id)         |
    |`pbiUsername`        |N/A         |您的「主要使用者」使用者名稱，請參閱 [Power BI 使用者名稱和密碼](#power-bi-username-and-password)         |
    |`pbiPassword`        |N/A         |您的「主要使用者」密碼，請參閱 [Power BI 使用者名稱和密碼](#power-bi-username-and-password)         |
    |`tenantId`           |您的 Azure AD [租用戶識別碼](#tenant-id)         |N/A         |
    |`appSecret`       |您的 Azure AD [用戶端祕密](#client-secret)         |N/A         |

11. 執行專案

    a. 在 [套件總管] 中，以滑鼠右鍵按一下 **AppOwnesData**。

    b. 選取 [執行身分]  > [對伺服器執行]。

    c. 在 [對伺服器執行] 視窗上，選取 [選擇現有的伺服器]，然後選取 [Tomcat] 伺服器。

    d. 選取 [完成]。

# <a name="node-js"></a>[Node JS](#tab/node-js)

6. 使用您慣用的 IDE，開啟 **應用程式擁有資料** 資料夾。 建議您使用下列其中一項：

    * [Visual Studio](https://visualstudio.microsoft.com/)

    * [Visual Studio Code](https://code.visualstudio.com/)

7. 藉由執行下列命令，開啟終端並安裝必要的相依性：`npm install`。

8. 展開 **Config** 資料夾，然後開啟 **config.json**。

9. 根據您的驗證方法，填入下列參數值：

    |參數            |服務主體  |主要使用者  |
    |---------------------|---------|---------|
    |`authenticationMode` |ServicePrincipal         |MasterUser         |
    |`clientId`           |您的 Azure AD 應用程式[用戶端識別碼](#client-id)         |您的 Azure AD 應用程式[用戶端識別碼](#client-id)         |
    |`workspaceId`        |內嵌報表所在工作區的識別碼，請參閱[工作區識別碼](#workspace-id)          |內嵌報表所在工作區的識別碼，請參閱[工作區識別碼](#workspace-id)         |
    |`reportId`           |所要內嵌報表的識別碼，請參閱[報表識別碼](#report-id)            |所要內嵌報表的識別碼，請參閱[報表識別碼](#report-id)         |
    |`pbiUsername`        |N/A         |您的「主要使用者」使用者名稱，請參閱 [Power BI 使用者名稱和密碼](#power-bi-username-and-password)         |
    |`pbiPassword`        |N/A         |您的「主要使用者」密碼，請參閱 [Power BI 使用者名稱和密碼](#power-bi-username-and-password)         |
    |`clientSecret`       |您的 Azure AD [用戶端祕密](#client-secret)         |N/A         |
    |`tenantId`           |您的 Azure AD [租用戶識別碼](#tenant-id)         |N/A         |

10. 執行下列動作來執行專案：

    a. 在 IDE 終端中，執行 `npm start`。

    b. 在瀏覽器中開啟新的索引標籤，並巡覽至 `http://localhost:5300`。

# <a name="python"></a>[Python](#tab/python)

6. 開啟 [PowerShell] 或 [命令提示字元]。

7. 確認您是在 **Python** > **對客戶進行內嵌** 資料夾，且 **requirements.txt** 檔案位於該資料夾中，然後執行 `pip3 install -r requirements.txt`。

8. 使用您慣用的 IDE，開啟 **應用程式擁有資料** 資料夾。 建議您使用下列其中一項：

    * [Visual Studio](https://visualstudio.microsoft.com/)

    * [Visual Studio Code](https://code.visualstudio.com/)

9. 開啟 **config.py**。

10. 根據您的驗證方法，填入下列參數值：

    |參數            |服務主體  |主要使用者  |
    |---------------------|---------|---------|
    |`AUTHENTICATION_MODE` |ServicePrincipal         |MasterUser         |
    |`WORKSPACE_ID`        |內嵌報表所在工作區的識別碼，請參閱[工作區識別碼](#workspace-id)          |內嵌報表所在工作區的識別碼，請參閱[工作區識別碼](#workspace-id)         |
    |`REPORT_ID`           |所要內嵌報表的識別碼，請參閱[報表識別碼](#report-id)            |所要內嵌報表的識別碼，請參閱[報表識別碼](#report-id)         |
    |`TENANT_ID`           |您的 Azure AD [租用戶識別碼](#tenant-id)         |N/A         |
    |`CLIENT_ID`           |您的 Azure AD 應用程式[用戶端識別碼](#client-id)         |您的 Azure AD 應用程式[用戶端識別碼](#client-id)         |
    |`CLIENT_SECRET`       |您的 Azure AD [用戶端祕密](#client-secret)         |N/A         |
    |`POWER_BI_USER`        |N/A         |您的「主要使用者」使用者名稱，請參閱 [Power BI 使用者名稱和密碼](#power-bi-username-and-password)         |
    |`POWER_BI_PASS`        |N/A         |您的「主要使用者」密碼，請參閱 [Power BI 使用者名稱和密碼](#power-bi-username-and-password)         |

11. 儲存檔案。

12. 執行下列動作來執行專案：

    a. 在 [PowerShell] 或 [命令提示字元] 中，巡覽至 **Python** > **對客戶進行內嵌** > **AppOwnesData** 資料夾，然後執行 `flask run`。

    b. 在瀏覽器中開啟新的索引標籤，並巡覽至 `http://localhost:5300`。

---

## <a name="developing-your-application"></a>開發您的應用程式

設定並執行「對客戶進行內嵌」範例應用程式之後，您就可以開始開發自己的應用程式。

[!INCLUDE[Move to production](../../includes/embed-tutorial-production.md)]

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
>[移至生產環境](move-to-production.md)

>[!div class="nextstepaction"]
>[為組織內嵌](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
>[為客戶內嵌編頁報表](embed-paginated-reports-customers.md)

> [!div class="nextstepaction"]
>[為組織內嵌分頁報表](embed-paginated-reports-organization.md)

>[!div class="nextstepaction"]
>[詢問 Power BI 社群](https://community.powerbi.com/)