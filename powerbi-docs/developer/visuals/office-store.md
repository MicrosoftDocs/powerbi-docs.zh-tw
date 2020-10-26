---
title: 將 Power BI 視覺效果發佈至合作夥伴中心
description: 了解如何將自訂視覺效果發佈至合作夥伴中心供其他人探索及使用
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: how-to
ms.subservice: powerbi-custom-visuals
ms.date: 07/14/2020
ms.openlocfilehash: 55661d8faa39d26d19d15696252cf46b74c84a50
ms.sourcegitcommit: 50b21718a167c2b131313b4135c8034c6f027597
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/14/2020
ms.locfileid: "92049422"
---
# <a name="publish-power-bi-visuals-to-partner-center"></a>將 Power BI 視覺效果發佈至合作夥伴中心

一旦建立了 Power BI 視覺效果後，您可以將它發佈至 AppSource 供其他人探索及使用。 如需建立 Power BI 視覺效果的詳細資訊，請參閱[開發 Power BI 圓形卡片視覺效果](develop-circle-card.md)。

## <a name="what-is-appsource"></a>什麼是 AppSource？

您可以在 [AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals) \(英文\) 尋找適用於 Microsoft 產品與服務的 SaaS 應用程式與增益集。

![AppSource 中 Power BI 視覺效果的螢幕擷取畫面。](media/office-store/appsource-01.png)

## <a name="preparing-to-submit-your-power-bi-visual"></a>準備提交您的 Power BI 視覺效果

將 Power BI 視覺效果提交至 AppSource 之前，請確定您已閱讀 [Power BI 視覺效果指導方針](guidelines-powerbi-visuals.md)，而且[已測試您的自訂視覺效果](./submission-testing.md) \(英文\)。

當您準備好要提交 Power BI 視覺效果時，請確認您的視覺效果符合以下所列的所有需求。

| 項目 | 必要 | 描述 |
| --- | --- | --- |
| Pbiviz 套件 |是 |將您的 Power BI 視覺效果封裝成包含所有必要中繼資料的 Pbiviz 套件。<br>視覺效果名稱<br>顯示名稱<br>GUID<br>版本<br>描述<br>作者名稱和電子郵件 |
| .pbix 報表檔案範例 |是 |為展示您的視覺效果，您應該協助使用者熟悉該視覺效果。 強調視覺效果能為使用者帶來的價值，並提供使用方式及格式設定選項的範例。 您也可以在結尾新增「提示」  頁面，提供一些提示與祕訣，以及應避免的事項。<br>.pbix 報表範例檔案必須離線工作，不能有任何外部連線。 |
| 圖示 |是 |您應該包含店面中會出現的自訂視覺效果標誌。 格式可以是 .png、.jpg、.jpeg 或 .gif。 它必須剛好是 300 px (寬度) x 300 px (高度)。<BR>**重要！** 提交圖示之前，請仔細檢閱 [AppSource 市集影像指南](/office/dev/store/craft-effective-appsource-store-images) \(英文\)。 |
| 螢幕擷取畫面 |是 |提供至少一張螢幕擷取畫面。 格式可以是 .png、.jpg、.jpeg 或 .gif。 尺寸必須剛好為 1366 px (寬度) x 768 px (高度)。 檔案大小不能大於 1024 kb。<br>若要提供更好的使用體驗，請新增文字泡泡以表達每張螢幕擷取畫面所顯示重要功能的價值定位。 |
| 支援下載連結 |是 |為您的客戶提供支援 URL。 系統會輸入此連結作為您合作夥伴中心清單的一部分，當使用者在 AppSource 上存取您視覺效果的清單時會看到。 URL 的格式應該包含 https:// 或 http:// 。 |
| 隱私權文件連結 |是 |提供視覺效果隱私權原則的連結。 此連結會輸入為您合作夥伴中心清單的一部分，當使用者在 AppSource 上存取您視覺效果的清單時會看到。 連結的格式應該包含 https:// 或 http:// 。 |
| 使用者授權合約 (EULA) |是 |您必須為您的 Power BI 視覺效果提供 EULA 檔案。 您可以使用[標準合約](https://go.microsoft.com/fwlink/?linkid=2041178)、[Power BI 視覺效果合約](https://visuals.azureedge.net/app-store/Power%20BI%20-%20Default%20Custom%20Visual%20EULA.pdf)，或自己的 EULA。 |
| 影片連結 |否 |為提高使用者對您自訂視覺效果的興趣，請提供有關視覺效果的影片連結。 URL 的格式應該包含 https:// 或 http:// 。 |
| GitHub 儲存機制 |否 |共用具有您 Power BI 視覺效果及範例資料之 [GitHub](https://www.github.com) \(英文\) 存放庫的公用連結。 這可讓其他開發人員有機會提供意見反應，並為您的程式碼提出改進。 |

## <a name="getting-an-app-package-xml"></a>取得應用程式套件 XML

若要提交 Power BI 視覺效果，您需要來自 Power BI 小組的應用程式套件 XML。 若要取得應用程式套件 XML，請將電子郵件傳送至 Power BI 視覺效果提交小組 ([pbivizsubmit@microsoft.com](mailto:pbivizsubmit@microsoft.com))。

在建立 **pbiviz** 套件之前，必須在 **pbiviz.json** 檔案中填寫以下欄位：
* description
* supportUrl
* 編寫
* name
* 電子郵件

在您的電子郵件中附加 **pbiviz 檔案**與**範例報告 pbix 檔案**。 Power BI 小組會回覆指示和要上傳的應用程式套件 XML 檔案。 需要有此 XML 應用程式套件，才能透過 Office 開發人員中心提交您的視覺效果。

> [!NOTE]
> 為改善品質並確保現有的報告不中斷，現有視覺效果的更新經市集核准後，要再 2 週才會投放到生產環境。

## <a name="submitting-to-appsource"></a>提交至 AppSource

若要將您的 Power BI 視覺效果提交至 AppSource，您需要從 Power BI 小組取得應用程式套件，然後將它提交至合作夥伴中心。

### <a name="getting-the-app-package"></a>取得應用程式套件

您必須先將附有 **pbiviz** 檔案與 **pbix** 檔案的電子郵件傳送至 Power BI 小組，然後再提交至 AppSource。 這樣可讓 Power BI 小組將這些檔案上傳到公用的共用伺服器。 否則，市集就無法擷取檔案。 

Power BI 小組必須檢查檔案中是否有新的 Power BI 視覺效果提交、對現有 Power BI 視覺效果的更新，以及對已拒絕提交所做的修正。

### <a name="submitting-to-partner-center"></a>提交至合作夥伴中心

若要將您的 Power BI 視覺效果提交至合作夥伴中心，您必須向合作夥伴中心註冊。 如果您尚未註冊，請[在合作夥伴中心建立開發人員帳戶](/office/dev/store/open-a-developer-account) \(英文\)。

>[!NOTE]
>**個別的發行者**可以使用下列其中一種方法來提交 Power BI 視覺效果：
>* 如果您擁有舊的賣方儀表板帳戶，您可以繼續使用此帳戶的認證來登入合作夥伴中心。
>* 如果您沒有舊的賣方儀表板帳戶，且尚未註冊到合作夥伴中心，您將必須使用公司電子郵件來[在合作夥伴中心申請開發人員帳戶](/office/dev/store/open-a-developer-account) \(英文\)。

遵循下列步驟來將您的 Power BI 視覺效果提交至合作夥伴中心。 如需提交程序的詳細資訊，請參閱[透過合作夥伴中心將 Office 方案提交至 AppSource](/office/dev/store/use-partner-center-to-submit-to-appsource) \(英文\)。

1. 登入 [合作夥伴中心]  。

2. 在左側窗格上，選取 [OFFICE 市集]  。

3. 選取 [概觀]  。

4. 選取 [建立新的]  ，然後從下拉式功能表中選取 [Power BI 視覺效果]  。

    ![於合作夥伴中心的 [Office 市集] 索引標籤中建立新 Power BI 視覺效果的螢幕擷取畫面。](media/office-store/power-bi-visual.png)

5. 在 [建立新的 Power BI 視覺效果]  視窗中，輸入 Power BI 視覺效果的名稱，然後選取 [建立]  。

6. 選取 [套件]  ，並上傳您的 Power BI 視覺效果 XML 應用程式套件。

7. 選取 [內容]  並提供必要的資訊。

8. 如果您的產品需要額外購買，請選取 [產品設定]  並選取 [購買相關服務]  核取方塊。

9. (選擇性) 如果您想要[認證](power-bi-custom-visuals-certified.md)您的視覺效果，請選取 [產品設定]  ，然後選取 [Power BI 認證]  核取方塊。
    >[!TIP]
    >Power BI 認證程序可能需要一些時間。 如果您是在建立新的 Power BI 視覺效果，建議您在要求 Power BI 認證之前，先透過合作夥伴中心發佈您的 Power BI 視覺效果。 這可確保視覺效果的發佈不會延遲。

10. 選取 [產品設定]  ，然後按一下 [檢閱並發佈]  。


## <a name="tracking-submission-status-and-usage"></a>追蹤提交狀態和使用方式

您可以檢閱[驗證原則](/legal/marketplace/certification-policies#1180-power-bi-visuals)。

* 提交之後，您就能夠在[應用程式儀表板](https://sellerdashboard.microsoft.com/Application/Summary/)中檢視提交狀態。

* 若想要知道何時可從 AppSource 下載您的 Power BI 視覺效果，請查看 Power BI 視覺效果 [發行集時間軸](power-bi-custom-visuals-certified.md#publication-timeline)。

## <a name="certify-your-visual"></a>認證您的視覺效果

建立視覺效果之後，如果需要，可以為您的視覺效果[取得認證](power-bi-custom-visuals-certified.md)。

## <a name="next-steps"></a>後續步驟

* [開發 Power BI 圓形卡片視覺效果](develop-circle-card.md)

* [Power BI 中的視覺效果](../../visuals/power-bi-report-visualizations.md)  

* [Power BI 中的視覺效果](power-bi-custom-visuals.md)  

* [取得 Power BI 視覺效果認證](power-bi-custom-visuals-certified.md)

* 有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)