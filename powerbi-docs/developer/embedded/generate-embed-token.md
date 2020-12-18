---
title: 在 Power BI 內嵌式分析中產生內嵌權杖的考量
description: 了解產生內嵌權杖的考量、限制及必要權限
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.custom: ''
ms.date: 10/15/2020
ms.openlocfilehash: 45a88d93e7ac5a63b269350451f39991ba153dd5
ms.sourcegitcommit: bbf7e9341a4e1cc96c969e24318c8605440282a5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2020
ms.locfileid: "97098022"
---
# <a name="considerations-when-generating-an-embed-token"></a>產生內嵌權杖時的考量

[產生權杖](/rest/api/power-bi/embedtoken)是可讓您產生權杖以將 Power BI 項目內嵌於 Web 應用程式或入口網站的 REST API。 該權杖是用來針對 Power BI 服務授權您的要求。

產生權杖 API 會使用單一身分識別 (主要使用者或服務主體) 來為個別使用者產生權杖，視該使用者在應用程式中的認證 (有效身分識別) 而定。

在成功驗證之後，便會授與相關資料的存取權。

>[!NOTE]
>產生權杖僅適用於您[為客戶進行內嵌](embed-sample-for-customers.md) (也稱為「應用程式擁有資料」案例) 的情況。

您可以使用下列 API 來產生權杖：

* [儀表板](/rest/api/power-bi/embedtoken/dashboards_generatetokeningroup)

* [資料集](/rest/api/power-bi/embedtoken/datasets_generatetokeningroup)

* [為多份報表產生權杖](/rest/api/power-bi/embedtoken/generatetoken)


* [報表建立](/rest/api/power-bi/embedtoken/reports_generatetokenforcreateingroup)

* [報表](/rest/api/power-bi/embedtoken/reports_generatetokeningroup)

* [磚](/rest/api/power-bi/embedtoken/tiles_generatetokeningroup)

## <a name="workspace-versions"></a>工作區版本

Power BI 具有兩種工作區版本，「傳統」工作區，以及「新」工作區。 您可以在[新工作區和傳統工作區的差異](../../collaborate-share/service-new-workspaces.md#new-and-classic-workspace-differences)中深入了解這兩種工作區之間的差異。

建立內嵌權杖時，不同的工作區會有不同的考量，且需要不同的權限。

|                  |「傳統」工作區 |「新」工作區|
|------------------|---------|--------|
|**考量**|<li>資料集和項目必須位於相同的工作區</li><li>無法使用服務主體</li>  |資料集和項目可以位於兩個不同的「新」工作區 |
|**工作區權限**|主要使用者必須是工作區的系統管理員  |服務主體或主要使用者至少必須是這兩個工作區的成員 |

>[!NOTE]
>* 您無法為[我的工作區](../../consumer/end-user-workspaces.md#types-of-workspaces)建立內嵌權杖。
>* 「項目」指的是如儀表板、磚、Q&A 或報表的 Power BI 項目。

## <a name="securing-your-data"></a>保護您的資料

建立解決方案時，請考慮使用這兩種方法來保護您的資料：

* [以工作區為基礎的隔離](embed-multi-tenancy.md#power-bi-workspace-based-isolation)

* [資料列層級安全性為基礎的隔離](embed-multi-tenancy.md#row-level-security-based-isolation)

如果您要使用 RLS 方法，請檢閱此文章結尾的 [RLS 考量與限制](generate-embed-token.md#row-level-security)。

## <a name="token-permissions"></a>權杖權限

在產生權杖 API 中，*GenerateTokenRequest* 區段會描述權杖權限。

>[!NOTE]
>此區段中所列出的權杖權限並不適用於[為多份報表產生權杖](/rest/api/power-bi/embedtoken/generatetoken) API。

### <a name="access-level"></a>存取層級

使用 *accessLevel* 參數來判斷使用者的存取層級。

* **View** - 授與使用者檢視權限。

* **Edit** - 授與使用者檢視及編輯權限 (僅適用於為報表產生內嵌權杖)。

    如果您是使用 [為多份報表產生權杖](/rest/api/power-bi/embedtoken/generatetoken) API，請使用 *allowEdit* 參數來為使用者授與檢視及編輯權限。

* **Create** - 授與使用者建立報表的權限 (僅適用於為建立報表產生內嵌權杖)。

    針對報表建立，您也必須提供 *datasetId* 參數。

### <a name="saving-a-copy-of-the-report"></a>儲存報表的複本

使用 *allowSaveAs* 布林值來讓使用者將報表儲存為新的報表。 根據預設，此設定值已設定為 *false*。

此參數僅適用於為報表產生內嵌權杖。

### <a name="row-level-security"></a>資料列層級安全性

透過使用[資料列層級安全性 (RLS)](embedded-row-level-security.md)，您可以選擇使用與您用來產生權杖的服務主體或主要使用者身分識別不同的身分識別。 透過使用此選項，您可以根據您的目標使用者顯示內嵌資訊。 例如，在您的應用程式中，您可以要求使用者登入，然後在登入的使用者是銷售員工時，顯示僅包含銷售資訊的報表。

如果您是使用 RLS，在某些情況下，您可以省略使用者的身分識別 (*EffectiveIdentity* 參數)。 這可讓權杖存取整個資料庫。 此方法可以用來為系統管理員及主管等使用者授與存取權，其將會具有檢視整個資料集的權限。 不過，您無法在所有案例中使用此方法。 下表會列出不同的 RLS 類型，並顯示可以在不指定使用者身分識別的情況下使用哪一種驗證方法。

下表也會顯示適用於每一種 RLS 類型的考量與限制。

|RLS 類型  |我是否可以在不指定有效使用者識別碼的情況下產生內嵌權杖？  |考量與限制  |
|---------|---------|---------|
|雲端資料列層級安全性 (雲端 RLS)      |✔ 主要使用者<br/>✖ 服務主體          |         |
|RDL (編頁報表)     |✖ 主要使用者<br/>✔ 服務主體        |您無法使用主要使用者來為 RDL 產生內嵌權杖。         |
|Analysis Services (AS) 內部部署即時連線    |✔ 主要使用者<br/>✖ 服務主體         |產生內嵌權杖的使用者也需要下列其中一種權限：<li>閘道管理員權限</li><li>資料來源模擬權限 (*ReadOverrideEffectiveIdentity*)</li>         |
|Analysis Services (AS) Azure 即時連線    |✔ 主要使用者<br/>✖ 服務主體         |無法覆寫產生內嵌權杖之使用者的身分識別。 可以使用自訂資料來實作動態 RLS 或安全篩選。<br/><br/>**注意：** 服務主體必須提供其物件識別碼作為有效身分識別 (RLS 使用者名稱)。         |
|單一登入 (SSO)     |✔ 主要使用者<br/>✖ 服務主體         |可以使用有效身分識別物件中的身分識別 Blob 屬性來提供明確 (SSO) 身分識別         |
|SSO 和雲端 RLS     |✔ 主要使用者<br/>✖ 服務主體         |您必須提供下列項目：<li>有效身分識別物件的身分識別 Blob 屬性中的明確 (SSO) 身分識別</li><li>有效 (RLS) 身分識別 (使用者名稱)</li>         |

>[!NOTE]
>服務主體必須一律提供下列項目：
>* 具有 RLS 資料集之任何項目的身分識別。
>* 針對 SSO 資料集，需要已定義使用者名稱屬性的有效 RLS 身分識別。

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
>[使用服務主體內嵌 Power BI 內容](embed-service-principal.md)