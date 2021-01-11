---
title: Power BI 內嵌式分析中，用於取得更佳內嵌 BI 見解之 Power BI 視覺效果相關的常見問題集
description: 瀏覽 Power BI 視覺效果相關的常見問題與答案清單。 使用 Power BI 內嵌式分析，以便取得更佳的內嵌 BI 見解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.custom: ''
ms.date: 09/30/2020
ms.openlocfilehash: b2bfac5cbd3ce9b850e42ebf25c63b6e22fbeb68
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97884916"
---
# <a name="power-bi-visuals-faq"></a>Power BI 視覺效果常見問題集

## <a name="organizational-power-bi-visuals"></a>組織 Power BI 視覺效果

管理入口網站可為您的組織管理 Power BI 視覺效果。

### <a name="how-can-the-admin-manage-organizational-power-bi-visuals"></a>系統管理員如何管理組織 Power BI 視覺效果？

在管理入口網站中的 [組織視覺效果]  索引標籤底下，系統管理員可以查看並[管理企業中的所有組織 Power BI 視覺效果](../../admin/organizational-visuals.md#organizational-visuals)。 這包括新增、停用、啟用及刪除 Power BI 視覺效果。

組織中的使用者可以輕鬆地找到 Power BI 視覺效果，然後直接從 Power BI Desktop 或服務將它們匯入其報表中。

一旦系統管理員上傳新版本的組織 Power BI 視覺效果之後，組織中的每個人都會獲得相同的更新版本。 使用更新 Power BI 視覺效果的所有報表也都會自動更新。

使用者可以在內建的 Power BI Desktop 與 Power BI 服務組織存放區中，於 [我的組織]  索引標籤下找到組織 Power BI 視覺效果。 

### <a name="if-an-admin-uploads-a-power-bi-visual-from-the-public-marketplace-to-the-organization-store-using-add-visual--from-appsource-is-it-automatically-updated-once-a-vendor-updates-the-visual-in-the-public-marketplace"></a>如果系統管理員使用 [新增視覺效果] > [從 AppSource]，將 Power BI 視覺效果從公用市集上傳到組織存放區，那麼當供應商在公用市集中更新該視覺效果時，組織存放區中的視覺效果是否也會自動更新？

是，視覺效果會從公用市集自動更新。 如果視覺效果已經過認證，則會保留憑證，包括匯出至 PDF 或 PowerPoint 等其他功能。

### <a name="is-there-a-way-to-disable-the-organization-store"></a>是否有停用組織存放區的方法？

否，使用者一定會在 Power BI Desktop 和 Power BI 服務中看到 [我的組織]  索引標籤。 如果系統管理員從管理入口網站停用或刪除所有組織 Power BI 視覺效果，組織存放區將會是空的。
  
### <a name="if-the-admin-disables-power-bi-visuals-from-the-admin-portal-tenant-settings-do-users-still-have-access-to-the-organizational-power-bi-visuals"></a>如果系統管理員從管理入口網站 ([租用戶設定]) 停用 Power BI 視覺效果，使用者是否仍可以存取組織 Power BI 視覺效果？

是，如果系統管理員從管理入口網站停用 Power BI 視覺效果，其不會影響組織的存放區。

某些組織會停用 Power BI 視覺效果，並僅啟用由 Power BI 系統管理員匯入與上傳到組織存放區的精選視覺效果。

Power BI Desktop 並未強制停用管理入口網站中的 Power BI 視覺效果。 Desktop 使用者仍可在其報表中新增並使用公用 Marketplace 中的 Power BI 視覺效果。 但是，這些公用的 Power BI 視覺效果會在發佈至 Power BI 服務後停止轉譯，並發出適當的錯誤訊息。 

在強制執行管理入口網站中的 Power BI 視覺效果設定時，Power BI 服務中的使用者將無法從公用市集匯入 Power BI 視覺效果。 只能匯入來自組織存放區中的視覺效果。

### <a name="what-are-the-advantages-of-power-bi-visuals-in-the-organizational-store"></a>組織存放區中的 Power BI 視覺效果有何優點？

* 每個人都會取得相同的視覺效果版本，這是由 Power BI 系統管理員所控制。系統管理員在管理入口網站中更新視覺效果版本後，組織中的所有使用者會自動取得更新版本。

* 無需透過電子郵件或共用資料夾共用視覺效果檔案。 所有登入的成員都能看見組織存放區供應項目。

* 安全性和可支援性，組織 Power BI 視覺效果的新版本會在所有報表中自動更新。

* 系統管理員可以控制在整個組織中可用的 Power BI 視覺效果。

* 系統管理員可以從管理入口網站啟用/停用視覺效果以進行測試。

## <a name="certified-power-bi-visuals"></a>經認證的 Power BI 視覺效果

### <a name="what-are-certified-power-bi-visuals"></a>什麼是經認證的 Power BI 視覺效果？

經認證的 Power BI 視覺效果是符合特定[需求](power-bi-custom-visuals-certified.md)，且由 Microsoft 所認證的 Power BI 視覺效果。

在[市集](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals)中，經認證的 Power BI 視覺效果具有表示它們為已認證的黃色徽章。

Microsoft 並非協力廠商 Power BI 視覺效果的作者。 我們建議客戶直接連絡作者以確認協力廠商視覺效果的功能。

### <a name="what-tests-are-done-during-the-certification-process"></a>認證流程期間會完成哪些測試？

認證流程測試包括但不限於： 
* 程式碼檢閱
* 靜態程式碼分析
* 資料外洩
* 資料模糊
* 滲透測試
* 存取 XSS 測試
* 惡意資料插入
* 輸入驗證
* 功能測試
 
### <a name="are-certified-power-bi-visual-checked-again-with-every-new-submission-upgrade"></a>是否會在每次重新提交 (升級) 經認證的 Power BI 視覺效果時再次進行檢查？

是。 每當經認證的視覺效果有新版本提交至市集時，視覺效果的版本更新都會經過相同認證檢查。

版本更新認證是自動的。 如果發生導致拒絕更新的違規時，系統會傳送電子郵件給開發人員以說明需要修正的項目。

### <a name="can-a-certified-power-bi-visual-stop-lose-its-certification-after-a-new-update"></a>經認證的 Power BI 視覺效果取得新的更新之後是否會失去其認證？

不會，並不會發生這樣的事。 經認證的視覺效果，不會在取得新的更新之後失去其認證。 該更新會受到拒絕。
 
### <a name="do-i-need-to-share-my-code-in-a-public-repository-if-im-certifying-my-power-bi-visual"></a>如果我要對自己的 Power BI 視覺效果進行認證，是否需要在公用存放庫中共用我的程式碼？

不用，您不必公開共用自己的程式碼。

請提供讀取權限以檢查 Power BI 視覺效果程式碼。 例如，使用 GitHub 中的私人存放庫。
 
### <a name="does-a-certified-power-bi-visual-have-to-be-in-the-marketplace"></a>經認證的 Power BI 視覺效果是否必須位於市集中？

是。 無法對私人視覺效果進行認證。
 
### <a name="how-long-does-it-take-to-certify-my-visual"></a>認證我的視覺效果需要多少時間？

認證新的 Power BI 視覺效果 (第一次認證) 可能需要最多四週的時間。 

認證 Power BI 視覺效果的更新版本可能需要最多三週的時間。 

### <a name="does-the-certification-process-ensure-that-there-is-no-data-leakage"></a>認證程序是否能保證不會發生資料外洩？

執行的測試設計為檢查不會存取外部服務或資源的視覺效果。 

Microsoft 並非協力廠商 Power BI 視覺效果的作者。 我們建議客戶直接連絡作者以確認協力廠商 Power BI 視覺效果的功能。
 
### <a name="are-uncertified-power-bi-visuals-safe-to-use"></a>使用未經認證的 Power BI 視覺效果是否安全？

未經認證的 Power BI 視覺效果不一定不安全。

有些視覺效果無法通過認證，因為不符合一或多個[認證需求](power-bi-custom-visuals-certified.md#certification-requirements)。 例如，連接到地圖視覺效果或使用商業程式庫的視覺效果等外部服務。
 
## <a name="visuals-with-additional-purchases"></a>需要另外購買的視覺效果

### <a name="what-is-a-visual-with-additional-purchases"></a>什麼是需要另外購買的視覺效果？

具有其他購買的視覺效果很類似應用程式內購買 (IAP) 增益集。 這些增益集會包含 [可能需要個別購買]  價格標記。

IAP Power BI 視覺效果是免費且可下載的 Power BI 視覺效果。 使用者不須支付任何費用，便能從市集下載那些 Power BI 視覺效果。

IAP 視覺效果可讓您選擇在應用程式內購買進階功能。  

### <a name="what-is-changing-in-the-submission-process"></a>提交程序將有何變更？

將 IAP Power BI 視覺效果提交至市集的程序，與提交免費 Power BI 視覺效果的程序相同。 您可以使用[合作夥伴中心](/partner-center/)來提交 Power BI 視覺效果以進行認證。


註冊您的 Power BI 視覺效果時，請瀏覽至 [產品設定]  索引標籤，然後選取 [我的產品需要訂購服務]  核取方塊。

### <a name="what-should-i-do-beforesubmittingmy-iap-power-bi-visual"></a>在提交 IAP Power BI 視覺效果之前，我該做些什麼？

如果您正在處理 IAP Power BI 視覺效果，請確定其符合[指導方針](guidelines-powerbi-visuals.md)。  

> [!NOTE]
> 具有額外 IAP 功能的 Power BI 免費視覺效果，必須保留先前所提供的相同免費功能。 您可以在舊的免費功能之上新增選擇性的進階付費功能。 我們建議將具有進階功能的 IAP Power BI 視覺效果提交為新的 Power BI 視覺效果，而不要更新舊的免費版本。

### <a name="do-iap-power-bi-visuals-need-to-be-certified"></a>IAP Power BI 視覺效果是否需要通過認證？

[認證](power-bi-custom-visuals-certified.md)程序是選擇性的。 開發人員可自行決定是否要為其 IAP Power BI 視覺效果取得認證。

### <a name="can-i-get-my-iap-power-bi-visual-certified"></a>IAP Power BI 視覺效果是否可以獲得認證？

是，在 AppSource 小組核准您的 IAP Power BI 視覺效果之後，您即可提交 Power BI 視覺效果以進行[認證](power-bi-custom-visuals-certified.md)。

認證是選擇性的程序，您可自行決定是否要為您的您的 IAP 視覺效果取得認證。

## <a name="additional-questions"></a>其他問題

### <a name="how-to-get-support"></a>如何取得支援？

如果您有任何疑問、意見或問題，歡迎連絡 Power BI 視覺效果支援小組：pbicvsupport@microsoft.com。  

## <a name="next-steps"></a>後續步驟

如需詳細資訊，請前往[針對您的 Power BI 視覺效果進行疑難排解](power-bi-custom-visuals-troubleshoot.md)。