---
title: 深入了解內部部署資料閘道
description: 本文探討內部部署閘道的深入資訊。 這會探討服務與 Azure Active Directory 之間的運作方式以及本機 Active Directory 使用 Analysis Services 時的運作方式
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: how-to
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 0964ad3e391c8e066c31ea7bb53f67e97f254422
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96392344"
---
# <a name="on-premises-data-gateway-in-depth"></a>深入了解內部部署資料閘道

[!INCLUDE [gateway-rewrite](../includes/gateway-rewrite.md)]

我們已將本文中資訊移動到 Power BI 和一般文件中的數篇文章。請前往每個標題下方的連結來尋找相關內容。

## <a name="how-the-gateway-works"></a>閘道的運作方式

請參閱[內部部署資料閘道架構](/data-integration/gateway/service-gateway-onprem-indepth)。

## <a name="list-of-available-data-source-types"></a>可用的資料來源類型清單

請參閱[管理資料來源](service-gateway-data-sources.md)。

## <a name="authentication-to-on-premises-data-sources"></a>內部部署資料來源的驗證

請參閱[內部部署資料來源的驗證](/data-integration/gateway/service-gateway-onprem-indepth#authentication-to-on-premises-data-sources)。

## <a name="authentication-to-a-live-analysis-services-data-source"></a>即時 Analysis Services 資料來源的驗證

請參閱[即時 Analysis Services 資料來源的驗證](service-gateway-enterprise-manage-ssas.md#authentication-to-a-live-analysis-services-data-source)。

## <a name="role-based-security"></a>角色型安全性

請參閱[角色型安全性](service-gateway-enterprise-manage-ssas.md#role-based-security)。

## <a name="row-level-security"></a>資料列層級安全性

請參閱[資料列層級安全性](service-gateway-enterprise-manage-ssas.md#row-level-security)。

## <a name="what-about-azure-active-directory"></a>Azure Active Directory 的情況為何？

請參閱 [Azure Active Directory](/data-integration/gateway/service-gateway-onprem-indepth#azure-active-directory)。

## <a name="how-do-i-tell-what-my-upn-is"></a>如何判斷我的 UPN 為何？

請參閱[如何判斷我的 UPN 為何？](/data-integration/gateway/service-gateway-onprem-indepth#how-do-i-tell-what-my-upn-is)。

## <a name="map-user-names-for-analysis-services-data-sources"></a>對應 Analysis Services 資料來源的使用者名稱

請參閱[對應 Analysis Services 資料來源的使用者名稱](service-gateway-enterprise-manage-ssas.md#map-user-names-for-analysis-services-data-sources)。

## <a name="synchronize-an-on-premises-active-directory-with-azure-active-directory"></a>同步處理內部部署 Active Directory 和 Azure Active Directory 

請參閱[同步內部部署 Active Directory 和 Azure Active Directory](/data-integration/gateway/service-gateway-onprem-indepth#synchronize-an-on-premises-active-directory-with-azure-active-directory)。

## <a name="what-to-do-next"></a>下一個步驟是什麼？

請參閱資料來源的相關文章：

[管理資料來源](service-gateway-data-sources.md)
[管理您的資料來源 - Analysis Services](service-gateway-enterprise-manage-ssas.md)  
[管理您的資料來源 - SAP HANA](service-gateway-enterprise-manage-sap.md)  
[管理您的資料來源 - SQL Server](service-gateway-enterprise-manage-sql.md)  
[管理您的資料來源 - Oracle](service-gateway-onprem-manage-oracle.md)  
[管理您的資料來源 - 匯入/已排程的重新整理](service-gateway-enterprise-manage-scheduled-refresh.md)  

## <a name="where-things-can-go-wrong"></a>可能發生錯誤之處

請參閱[針對內部部署資料閘道進行疑難排解](/data-integration/gateway/service-gateway-tshoot)及[針對閘道進行疑難排解 - Power BI](service-gateway-onprem-tshoot.md)。

## <a name="sign-in-account"></a>登入帳戶

請參閱[登入帳戶](/data-integration/gateway/service-gateway-onprem-indepth#sign-in-account)。

## <a name="windows-service-account"></a>Windows 服務帳戶

請參閱[變更內部部署資料閘道的服務帳戶](/data-integration/gateway/service-gateway-service-account)。

## <a name="ports"></a>連接埠

請參閱[連接埠](/data-integration/gateway/service-gateway-communication#ports)。

## <a name="forcing-https-communication-with-azure-service-bus"></a>強制與 Azure 服務匯流排進行 HTTPS 通訊

請參閱[強制與 Azure 服務匯流排進行 HTTPS 通訊](/data-integration/gateway/service-gateway-communication#force-https-communication-with-azure-service-bus)。

## <a name="support-for-tls-12"></a>對 TLS 1.2 的支援

請參閱[適用於閘道流量的 TLS 1.2](/data-integration/gateway/service-gateway-communication#tls-12-for-gateway-traffic)。

## <a name="how-to-restart-the-gateway"></a>如何重新啟動閘道

請參閱[重新啟動閘道](/data-integration/gateway/service-gateway-restart)。

## <a name="next-steps"></a>後續步驟

[什麼是內部部署資料閘道？](service-gateway-onprem.md)

有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)