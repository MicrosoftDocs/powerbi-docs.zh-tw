---
title: Power BI 視覺效果指南
description: 了解如何將自訂視覺效果發佈至 Microsoft AppSource 供其他人探索及透過購買來使用。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 08/12/2020
ms.openlocfilehash: 427fba66b34fefb0b7ca9d70a29b08ebe7d743cb
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96416132"
---
# <a name="guidelines-for-power-bi-visuals"></a>Power BI 視覺效果指南
在將 Power BI 視覺效果[發佈](office-store.md)至 Microsoft AppSource 供其他人探索及使用之前，請務必遵循指導方針，以便為使用者打造絕佳體驗。

## <a name="power-bi-visuals-with-additional-purchases"></a>需要另外購買的 Power BI 視覺效果

您可以提交可在 Marketplace (Microsoft AppSource) 上免費使用的 Power BI 視覺效果。 您也可以提交具有「可能需要個別購買」價格標籤的 Power BI 視覺效果到 Microsoft AppSource。 「可能需要個別購買」的 Power BI 視覺效果，類似於 Office 市集中的在應用程式內購買 (IAP) 增益集。 

類似於免費的 Power BI 視覺效果，IAP Power BI 視覺效果也可以受到認證。 在提交 IAP Power BI 視覺效果以進行認證前，請確認其符合[認證要求](power-bi-custom-visuals-certified.md)。

### <a name="what-is-a-power-bi-visual-with-iap-features"></a>什麼是具有 IAP 功能的 Power BI 視覺效果？

IAP Power BI 視覺效果是提供「免費功能」的「免費」視覺效果。 IAP Power BI 視覺效果也有一些進階功能，但這些功能可能必須另外付費。 在 Power BI 視覺效果的描述中，開發人員必須告知使用者需要另行購買才能使用的功能。 目前，Microsoft 不提供原生 API 以支援購買應用程式與增益集。

對於這些購買項目，開發人員可以使用任何第三方付款系統。 如需詳細資訊，請參閱[我們的市集原則](/legal/marketplace/certification-policies#11002-displaying-ads) \(英文\)。


>[!IMPORTANT]  
> 若您將 Power BI 視覺效果從免費更新為「可能需要另外購買」，則使用者仍一定會收到如更新前的同等級免費功能。 您可以在現有的免費功能之上新增選用進階付費功能。

### <a name="watermarks"></a>浮水印

您可以使用浮水印，以便客戶能繼續免費使用 IAP 的進階功能。 

在購買前，浮水印可用來展示 Power BI 視覺效果的完整功能。 

* 僅可在不具有效授權情況下使用的付費功能上使用浮水印。
* 浮水印不適用於具有「免費」  價格標籤的 Power BI 視覺效果。
* 當使用者使用免費功能時，您無法在 IAP 視覺效果中使用浮水印。 

### <a name="pop-up-window"></a>快顯視窗

當 Power BI IAP 視覺效果使用無效 (或過期) 的授權時，您可以使用快顯視窗來說明如何購買授權。

### <a name="submission-process"></a>提交程序

依照[提交程序](office-store.md#submitting-to-appsource)，然後瀏覽至 [產品設定]  索引標籤，並選取 [我的產品需要訂購服務]  核取方塊。

在 Power BI 視覺效果經過驗證及核准之後，IAP Power BI 視覺效果的 Microsoft AppSource 清單會在定價選項下方指出「可能需要個別購買」。

## <a name="context-menu"></a>捷徑功能表
操作功能表是當使用者將滑鼠停留在視覺效果上時所顯示的右鍵功能表。
所有 Power BI 視覺效果都應該啟用操作功能表，以提供一致的體驗。
請參閱[本文](https://github.com/Microsoft/PowerBI-visuals/blob/gh-pages/tutorials/building-bar-chart/adding-context-menu-to-the-bar.md)了解如何新增內容功能表。

>[!div class="mx-imgBorder"]
>![Power BI 視覺效果操作功能表的螢幕擷取畫面。](media/guidelines-powerbi-visuals/context-menu.png)

## <a name="commercial-logo"></a>商業標誌
本節描述在 Power BI 視覺效果中心新增商業標誌的規格。 商業標誌並非必要。 如已新增，則必須遵循這些指導方針。

> [!NOTE]
> * 在本文中，商業標誌意指下圖所示的任何商業公司圖示。
> * 本文中使用的 Microsoft 商業標誌僅為範例用途。 搭配 Power BI 視覺效果來使用您自己的商業標誌。

> [!IMPORTANT]
> 商業標誌「僅可在編輯模式中」使用。 商業標誌「無法」在檢視模式中顯示。

### <a name="commercial-logo-type"></a>商業標誌類型

商業標誌有三種類型：
* **標誌**：標誌是由兩個鎖定在一起的項目、一個圖示和一個名稱所組成。

    ![Microsoft 標誌的螢幕擷取畫面。](media/guidelines-powerbi-visuals/microsoft-logo.png)

* **符號**：不含任何文字的圖形。

    ![Microsoft 符號的螢幕擷取畫面。](media/guidelines-powerbi-visuals/microsoft-symbol.png)

* **商標**：不含圖示的標誌，僅以文字組成。

    ![沒有圖示的 Microsoft 標誌螢幕擷取畫面。](media/guidelines-powerbi-visuals/microsoft-logotype.png)

### <a name="commercial-logo-color"></a>商業標誌色彩

使用商業標誌時，標誌色彩必須為灰色 (十六進位色彩 #C8C8C8)。 請勿為商業標誌新增效果 (例如漸層)。

* **標誌**

    ![灰色 Microsoft 標誌的螢幕擷取畫面。](media/guidelines-powerbi-visuals/grey-microsoft-logo.png)

* **符號**：不含任何文字的圖形。

    ![灰色 Microsoft 符號的螢幕擷取畫面。](media/guidelines-powerbi-visuals/grey-microsoft-symbol.png)

* **商標**：不含圖示的標誌，僅以文字組成。

    ![沒有圖示的灰色 Microsoft 標誌螢幕擷取畫面。](media/guidelines-powerbi-visuals/grey-microsoft-logotype.png)

> [!TIP]
> * 如果 Power BI 視覺效果包含圖形，則建議為標誌新增白色背景 (邊界為 10 像素)。
> * 建議為標誌新增下陰影 (不透明度 30% 的黑色)。

### <a name="commercial-logo-size"></a>商業標誌大小

Power BI 視覺效果需要兩個商業標誌，一個用於大型圖格，另一個用於小型圖格。 請將標誌放置於頂端或右下角的周框方塊內 (邊界為 4 像素)。

下表描述 Power BI 視覺效果的大小考量。

|設定  |小型 Power BI 視覺效果  |大型 Power BI 視覺效果  |
|---------|---------|---------|
|「標誌寬度」    |最多 240 像素         |大於 240 像素         |
|「標誌高度」     |最多 160 像素         |大於 160 像素         |
|「周框方塊大小」     |40 x 15 像素         |101 x 30 像素         |
|「商業標誌範例」     |![小版 Microsoft 商業標誌的螢幕擷取畫面。](media/guidelines-powerbi-visuals/grey-microsoft-symbol.png)         |![Microsoft 商業標誌的螢幕擷取畫面。](media/guidelines-powerbi-visuals/grey-microsoft-logo.png)         |
|「周框方塊範例」    |![小型標誌尺寸的螢幕擷取畫面。](media/guidelines-powerbi-visuals/small-logo-box.png)         |![大型標誌尺寸的螢幕擷取畫面。](media/guidelines-powerbi-visuals/big-logo-box.png)         |
|    |         |         |

### <a name="commercial-logo-behavior"></a>商業標誌行為

商業標誌僅可在編輯模式中使用。 按一下時，商業標誌只能包含下列功能：

* 按一下商業標誌會重新導向至您的網站

* 按一下商業標誌會開啟具有其他資訊的快顯視窗。 快顯視窗應分成兩個區段：
    * 可包含商業標誌、視覺效果和市場評等的行銷區域。
    * 可包含資訊和連結的資訊區域。    


### <a name="things-to-avoid"></a>應避免事項

* 商業標誌無法在檢視模式中顯示。

* 動畫商業標誌可以顯示最多五秒的動畫。

* 如果 Power BI 視覺效果在閱讀模式中包含資訊圖示 (i)，則應符合商業標誌的色彩、大小和位置規定，如上所述。

* 請避免使用彩色或黑色商業標誌。 商業標誌必須是灰色 (十六進位色彩 #C8C8C8)。

    ![未經授權的彩色 Microsoft 標誌螢幕擷取畫面。](media/guidelines-powerbi-visuals/no-color-logo.png) ![未經授權的黑色 Microsoft 標誌螢幕擷取畫面](media/guidelines-powerbi-visuals/black-logo.png)

* 具有漸層或強烈陰影等效果的商業標誌。

    ![未經授權的 Microsoft 標誌樣式範例螢幕擷取畫面。](media/guidelines-powerbi-visuals/no-style-logo.png)

## <a name="best-practices"></a>最佳做法

請在發佈 Power BI 視覺效果時考慮下列建議，以便為使用者提供絕佳的體驗。

### <a name="visual-landing-page"></a>視覺效果登陸頁面

利用登陸頁面向使用者釐清可如何使用 Power BI 視覺效果，以及何處可購買授權。 不要包含會自動觸發的影片。 請只新增可協助改善使用者體驗的資料，例如授權購買詳細資料的相關資訊或連結，以及如何使用 IAP 功能。

### <a name="license-key-and-token"></a>授權金鑰和權杖

為了使用者方便起見，請在格式窗格頂端新增授權金鑰或權杖相關欄位。

## <a name="faq"></a>常見問題集

如需 Power BI 視覺效果的詳細資訊，請參閱[需要另外購買的 Power BI 視覺效果常見問題集](power-bi-custom-visuals-faq.md#visuals-with-additional-purchases)。

## <a name="next-steps"></a>後續步驟

了解如何將 Power BI 視覺效果發佈至 Microsoft AppSource 以供其他人探索及使用。

>[!div class="nextstepaction"]
>[發佈 Power BI 視覺效果](office-store.md)