---
title: 從 Power BI 行動裝置應用程式掃描條碼
description: 掃描實際的條碼可直接前往 Power BI 行動裝置應用程式中篩選過的 BI 資訊。
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 12/02/2019
ms.openlocfilehash: 5d1534ec3b6ccdf730cd2b255ba1142e80a6f9f9
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96413096"
---
# <a name="scan-a-barcode-with-your-device-from-the-power-bi-mobile-app"></a>使用裝置從 Power BI 行動裝置應用程式掃描條碼
掃描實際的條碼可直接前往 Power BI 行動裝置應用程式中篩選過的 BI 資訊。


適用於︰

| ![iPhone](./media/mobile-apps-qr-code/ios-logo-40-px.png) | ![iPad](./media/mobile-apps-qr-code/ios-logo-40-px.png) | ![Android 手機](././media/mobile-apps-qr-code/android-logo-40-px.png) | ![Android 平板電腦](././media/mobile-apps-qr-code/android-logo-40-px.png) |
|:--- |:--- |:--- |:--- |
|iPhone |iPad |Android 手機 |Android 平板電腦 |

假設有同事[在 Power BI Desktop 報表中標記了條碼欄位](../../transform-model/desktop-mobile-barcodes.md)，然後與您共用報表。 

![產品條碼掃描的螢幕擷取畫面，其中顯示彩色飲料其條碼上的掃描器。](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-scanner.png)

當您使用裝置上 Power BI 應用程式中的掃描器掃描產品條碼時，您就會看到具有該條碼的報表 (或報表清單)。 您可以開啟篩選出該條碼的報表。

## <a name="scan-a-barcode-with-the-power-bi-scanner"></a>使用 Power BI 掃描器掃描條碼
1. 在導覽列上，點選 [更多選項] (...)，然後點選 [掃描器]。

    ![功能窗格上 [更多] 選項的螢幕擷取畫面，其中顯示掃描器選取項目。](media/mobile-apps-scan-barcode-iphone/power-bi-scanner.png)

2. 如果未啟用您的相機，您需要核准 Power BI 應用程式使用相機。 您只需要核准一次。 
4. 將掃描器對準產品的條碼。 您會看到與條碼建立關聯的報表清單。
5. 點選報表名稱在裝置上開啟此報表，即會根據該條碼自動篩選。

## <a name="filter-by-other-barcodes-while-in-a-report"></a>在報表中按其他條碼篩選
在裝置上查看按條碼篩選的報表時，您可能想要用不同條碼篩選相同的報表。

* 若條碼圖示有篩選條件 ![已篩選圖示](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-filtered-icon-black.png)，則篩選條件為使用中，且報表已依條碼進行篩選。 
* 若圖示未包含篩選條件 ![未篩選圖示](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-unfiltered-icon.png)，則篩選條件未使用，且報表未依條碼進行篩選。 

無論何種狀況，都請點選圖示以開啟有浮動掃描器的小功能表。

* 將掃描器對焦到新項目，將報表的篩選條件變更為不同的條碼值。 
* 選取 \[Clear barcode filter] \(清除條碼篩選) 回到未經篩選的報表。
* 選取 \[Filter by recent barcodes] \(按最近的條碼篩選)，將報表篩選條件變更為目前工作階段內，您掃描過的其中一個條碼。

## <a name="issues-with-scanning-a-barcode"></a>條碼掃描問題
以下是掃描產品條碼時，可能會看到的一些訊息。

### <a name="couldnt-filter-report"></a>「無法篩選報表...」
您選擇要篩選的報表，其資料模型基礎不包含此條碼值。 例如，報表不包含產品「礦泉水」。  

### <a name="allsome-of-the-visuals-in-the-report-dont-contain-any-value"></a>報表的全部/某些視覺效果不包含任何值
您掃描的條碼值位在模型中，但報表的全部/某些視覺效果不包含此值，因此篩選會傳回空白狀態。 請嘗試查詢其他報表頁面，或在 Power BI Desktop 中編輯報表使其包含此值。 

### <a name="looks-like-you-dont-have-any-reports-that-can-be-filtered-by-barcodes"></a>「您似乎沒有任何可供條碼篩選的報表。」
這表示您沒有任何使用條碼的報表。 條碼掃描器只能篩選具有 [條碼] 資料行的報表。  

請確定您或報表擁有者已在 Power BI Desktop 中將資料行標記為 [條碼]。 深入了解[在 Power BI Desktop 中標記條碼欄位](../../transform-model/desktop-mobile-barcodes.md)

### <a name="couldnt-filter-report---looks-like-this-barcode-doesnt-exist-in-the-report-data"></a>「無法篩選報表，此條碼似乎不存在於報表資料中。」
您選擇要篩選的報表，其資料模型基礎不包含此條碼值。 例如，報表不包含產品「礦泉水」。 您可以掃描不同的產品、選擇不同的報表 (如有多份報表可供選擇)，或檢視未經篩選的報表。 

## <a name="next-steps"></a>後續步驟
* [在 Power BI Desktop 中標記條碼欄位](../../transform-model/desktop-mobile-barcodes.md)
* [Power BI 的儀表板磚](../end-user-tiles.md)
* [Power BI 中的儀表板](../end-user-dashboards.md)
