---
title: 什麼是 Power BI 範本應用程式？
description: 本文為 Power BI 範本應用程式的概觀。 了解如何撰寫少量程式碼或不需撰寫程式碼，即可建置 Power BI 應用程式，並將應用程式部署至所有 Power BI 客戶。
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 12/14/2020
ms.openlocfilehash: f9a3558bd83f9c2e263d69ad37c3e985c2c6199a
ms.sourcegitcommit: 96080432af4c8e3fe46c23274478ccffa0970efb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98597602"
---
# <a name="what-are-power-bi-template-apps"></a>什麼是 Power BI 範本應用程式？

新的 Power BI「範本應用程式」  讓 Power BI 合作夥伴撰寫少量程式碼或不用撰寫程式碼，即可建置 Power BI 應用程式，再將應用程式部署至所有 Power BI 客戶。  本文為 Power BI 範本應用程式的概觀。

身為 Power BI 合作夥伴，您可以為客戶建立一組現成可用的內容並自行發佈。  

您可以建置範本應用程式，讓客戶連線並在自己的帳戶內具現化。 身為領域專家，他們可將資料解除鎖定，讓其商務使用者都能輕鬆使用。  

將您的範本應用程式提交至合作夥伴中心。 然後，這些應用程式將可在 [Power BI 應用程式市集](https://app.powerbi.com/getdata/services)與 [Microsoft AppSource](https://appsource.microsoft.com/?product=power-bi) 中公開取得。 以下為公用範本應用程式建立體驗的高階說明。

## <a name="power-bi-apps-marketplace"></a>Power BI 應用程式市集

Power BI 範本應用程式可讓 Power BI Pro 或 Power BI Premium 使用者，透過預先封裝的儀表板與報表 (可以連線到即時資料來源) 取得即時見解。 許多 Power BI 應用程式都已經可以在 [Power BI 應用程式市集](https://app.powerbi.com/getdata/services)中取得。

:::row:::
    :::column:::
        [![Microsoft Project Web 應用程式](./media/service-template-apps-overview/project-web.png)](https://app.powerbi.com/groups/me/getapps/services/pbi_msprojectonline.pbi-microsoftprojectwebapp)
    :::column-end:::
    :::column:::
        [![Microsoft 365 使用情況分析 Web 應用程式](./media/service-template-apps-overview/microsoft365-usage-analytics.png)](https://app.powerbi.com/groups/me/getapps/services/cia_microsoft365.microsoft-365-usage-analytics)
    :::column-end:::
    :::column:::
        [![Dynamic 365 商務中心 - 銷售 Web 應用程式](./media/service-template-apps-overview/dynamics-sales.png)](https://app.powerbi.com/groups/me/getapps/services/microsoftdynsmb.businesscentral_sales)
    :::column-end:::
    :::column:::
        [![Microsoft Forms Pro 客戶滿意度 Web 應用程式](./media/service-template-apps-overview/forms-pro.png)](https://app.powerbi.com/groups/me/getapps/services/msfp.formsprocustomersatisfaction)
    :::column-end:::
:::row-end:::

 > [!NOTE] 
 > Marketplace 應用程式不適用於美國政府雲端執行個體。 如需詳細資料，請參閱[適用於美國政府客戶的 Power BI](../admin/service-govus-overview.md)。


## <a name="process"></a>處理序

開發並提交範本應用程式的一般程序牽涉到多個步驟。 某些階段可能包含同時進行的多項活動。


| 階段 | Power BI Desktop |  |Power BI 服務  |  |合作夥伴中心  |
|---|--------|--|---------|---------|---------|
| **One** | 以 .pbix 檔案建置資料模型及報表 |  | 建立工作區。 匯入 .pbix 檔案。 建立互補儀表板  |  | 註冊為合作夥伴 |
| **Two** |  |  | 建立測試套件並執行內部驗證        |  | |
| **Three** | |  | 將測試套件升至生產階段前，以在您的 Power BI 租用戶外進行驗證，並提交至 AppSource  |  | 使用您的生產階段前套件，建立 Power BI 範本應用程式供應項目並啟動驗證程序 |
| **Four** | |  | 將生產階段前套件升至生產階段 |  | 上線 |

## <a name="before-you-begin"></a>開始之前

若要建立範本應用程式，您需有建立權限。 如需詳細資料，請參閱 Power BI 管理入口網站、範本應用程式設定。 

若要將範本應用程式發佈至 Power BI 服務及 AppSource，您必須符合[成為合作夥伴中心發行者](/azure/marketplace/become-publisher)的要求。
 
## <a name="high-level-steps"></a>高階步驟

以下為高階步驟。 

1. [參閱需求](#requirements)確認您符合需求。 

2. 在 Power BI Desktop 中建置報表。 使用參數，以便將其儲存為他人可用的檔案。 

3. 為您 Power BI 服務 (app.powerbi.com) 上租用戶中的範本應用程式建立工作區。 

4. 匯入您的 .pbix 檔案，並將儀表板等內容新增至您的應用程式。 

5. 建立測試套件，以在您的組織內親自測試範本應用程式。 

6. 將測試應用程式提升至生產階段前，以提交該應用程式至 AppSource 進行驗證，以及在您自己的租用戶外測試。 

7. 將內容提交至[合作夥伴中心](/azure/marketplace/partner-center-portal/create-power-bi-app-offer)進行發佈。 

8. 讓您的供應項目在 AppSource 中「正式運作」，並在 Power BI 中將應用程式移至生產階段。

9. 現在您可以在生產階段前，於相同工作區開始開發下一個版本。 

## <a name="requirements"></a>需求

若要建立範本應用程式，您需有建立權限。 如需詳細資料，請參閱 Power BI [管理入口網站、範本應用程式設定](../admin/service-admin-portal.md#template-apps-settings)。

若要將範本應用程式發佈至 Power BI 服務及 AppSource，您必須符合[成為合作夥伴中心發行者](/azure/marketplace/become-publisher)的要求。
 > [!NOTE] 
 > 範本應用程式提交在[合作夥伴中心](/azure/marketplace/partner-center-portal/create-power-bi-app-offer)中進行管理。 使用相同的 Microsoft 開發人員中心註冊帳戶來登入。 您的 AppSource 供應項目應該只會共有一個 Microsoft 帳戶。 帳戶不應該適用於個別服務或供應項目。

## <a name="tips"></a>提示 

- 確認您的應用程式包含範例資料，讓所有人按一下即可開始使用。 
- 藉由將應用程式安裝在您的租用戶及次要租用戶中，來仔細檢查您的應用程式。 確認客戶只會看到您要他們看到的項目。 
- 將 AppSource 用作代管您應用程式的線上市集。 如此一來，所有使用 Power BI 的人員都可以找到您的應用程式。 
- 考慮針對個別特殊情況提供多個範本應用程式。 
- 啟用資料自訂，例如，支援透過安裝程式設定自訂連線及參數。
- 若您是 ISV，並透過 Web 服務散發您的應用程式，請考慮在安裝期間將參數設定自動化，以減輕您客戶的負擔，並增加成功安裝的可能性。 如需詳細資料，請參閱[將範本應用程式安裝設定自動化](../developer/template-apps/template-apps-auto-install.md)。

如需更多建議，請參閱[在 Power BI 中撰寫範本應用程式的提示](service-template-apps-tips.md)。

## <a name="known-limitations"></a>已知限制

| 功能 | 已知的限制 |
|---------|---------|
|內容：資料集   | 只應剛好出現一個資料集。 只允許 Power BI Desktop (.pbix 檔案) 中建置的資料集。 <br>不支援：來自其他範本應用程式的資料集、跨工作區資料集、編頁報表、Excel 活頁簿 |
|內容：儀表板 | 不允許即時磚 (也就是指不支援推送或串流資料集) |
|內容：資料流程 | 不支援：資料流程 |
|來自檔案的內容 | 只允許 PBIX 檔案。 <br>不支援：.rdl 檔案 (編頁報表)、Excel 活頁簿   |
| 資料來源 | 允許針對雲端排程的資料重新整理支援的資料來源。 <br>不支援： <li>即時連線 (非 Azure AS)</li> <li>內部部署資料來源 (不支援個人和企業閘道)</li> <li>即時 (不支援推送資料集)</li> <li>複合模型</li></ul> |
| 資料集：跨工作區 | 不允許跨工作區資料集  |
| 查詢參數 | 不支援：適用於資料集之類型 "Any"、"Date" 或 "Binary" 類型區塊重新整理作業的參數 |
| Power BI 視覺效果 | 只支援公開可用的 Power BI 視覺效果。 不支援[組織 Power BI 視覺效果](../developer/visuals/power-bi-custom-visuals-organization.md) |
| 主權雲端 | 範本應用程式無法在主權雲端中使用 |

## <a name="support"></a>支援
如需在開發期間的支援，請使用 [https://powerbi.microsoft.com/support](https://powerbi.microsoft.com/support)。 我們會主動監視及管理這個網站。 讓適當的小組可快速開始處理客戶事件。

## <a name="next-steps"></a>後續步驟

[建立範本應用程式](service-template-apps-create.md)