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
ms.openlocfilehash: 3d35df1c38a0a62325f88fa19ee7267a3b209647
ms.sourcegitcommit: f7330dabb9cd8bce90bb2efec3e3273a11578f10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2021
ms.locfileid: "99494487"
---
# <a name="scan-barcodes-from-the-mobile-app-to-get-filtered-data"></a>從行動應用程式掃描條碼以取得篩選的資料 
掃描真實世界中的條碼，直接取得 Power BI 行動裝置應用程式中已篩選的 BI 資訊。

適用於︰

| ![iPhone](./media/mobile-apps-qr-code/ios-logo-40-px.png) | ![iPad](./media/mobile-apps-qr-code/ios-logo-40-px.png) | ![Android 手機](././media/mobile-apps-qr-code/android-logo-40-px.png) | ![Android 平板電腦](././media/mobile-apps-qr-code/android-logo-40-px.png) |
|:--- |:--- |:--- |:--- |
|iPhone |iPad |Android 手機 |Android 平板電腦 |

假設您的組織所擁有的報表，其資料已 [在 Power BI Desktop 中標記為條碼資料](../../transform-model/desktop-mobile-barcodes.md)。 當您使用裝置上 Power BI 應用程式中的掃描器掃描產品條碼時，您會取得具有條碼資料的報表清單。 您可以開啟您要尋找的報表，自動篩選出您需要的資訊。

![產品條碼掃描的螢幕擷取畫面，其中顯示彩色飲料其條碼上的掃描器。](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-scanner.png)

以下是兩個條碼掃描適用的案例範例：
* 假設您正在檢查大型超市中的清查，而您想要取得特定產品的相關資訊（例如商店有多少庫存、哪些部門用來儲存專案）等等，您可以直接在行動裝置上開啟 Power BI 掃描器，並掃描專案的條碼。 您將會取得具有條碼資料的報表清單。 您可以選擇相關的報表，並開啟報表，篩選出相關的資料。
* 假設工廠的機器是以條碼識別，而這些機器的遙測正在處理並傳送至 Power BI。 當工程師離開檢查電腦狀態時，他們可以輕鬆地掃描機器的條碼，並取得有關其效能和狀態的 KPI 報告。

## <a name="scan-a-barcode-with-the-power-bi-scanner"></a>使用 Power BI 掃描器掃描條碼
1. 在導覽列上，點選 [更多選項] (...)，然後點選 [掃描器]。

    ![功能窗格上 [更多] 選項的螢幕擷取畫面，其中顯示掃描器選取項目。](media/mobile-apps-scan-barcode-iphone/power-bi-scanner.png)

1. 如果未啟用您的相機，您需要核准 Power BI 應用程式使用相機。 您只需要核准一次。 
1. 在您感興趣的專案上，將掃描器指向條碼。 您會看到具有條碼欄位的報表清單。
1. 尋找您要尋找的報表，並按一下以在裝置上開啟它，並根據您掃描的條碼自動篩選。 如果報表未包含條碼，您將會收到「無法篩選報表」訊息。 在此情況下，您可以返回清單並嘗試另一份報表。
    
>[!NOTE]
>如果只有一個具有條碼欄位的報表，您將不會收到報表清單，而是會直接開啟報表，並根據您掃描的條碼進行篩選。 如果報表未包含您掃描的條碼，您也會收到「無法篩選報表」訊息。

## <a name="filter-by-other-barcodes-while-in-a-report"></a>在報表中按其他條碼篩選
在裝置上查看按條碼篩選的報表時，您可能想要用不同條碼篩選相同的報表。

在報表的動作列上，按 [ **更多選項] ( ... )** 並尋找條碼圖示。

* 如果條碼圖示已填滿， ![已篩選圖示](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-filtered-icon-black.png)，則篩選條件為使用中，且報表已依條碼進行篩選。 
* 如果圖示為 clear ![未篩選圖示](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-unfiltered-icon.png)，則篩選條件未使用，且報表未依條碼進行篩選。 

無論何種狀況，都請點選圖示以開啟有浮動掃描器的小功能表。

* 將掃描器對焦到新項目，將報表的篩選條件變更為不同的條碼值。 
* 選取 \[Clear barcode filter] \(清除條碼篩選) 回到未經篩選的報表。
* 選取 \[Filter by recent barcodes] \(按最近的條碼篩選)，將報表篩選條件變更為目前工作階段內，您掃描過的其中一個條碼。

## <a name="clear-a-barcode-filter"></a>清除條碼篩選器
若要在篩選過的報表中清除條碼篩選：
1. 在報表的動作列上，按 [ **更多選項] ( ... )** 並尋找已篩選過的條碼掃描器圖示 ![ 圖示 ](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-filtered-icon-black.png) ，指出篩選作用中，並按一下以開啟掃描器。
1. 選取 \[Clear barcode filter] \(清除條碼篩選) 回到未經篩選的報表。

## <a name="limitations"></a>限制

* [篩選] 窗格不會提供條碼篩選的指示。 若要知道報表目前是否以條碼篩選，請查看條碼掃描器功能表項目上的圖示：

    ![已篩選圖示](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-filtered-icon-black.png) 指出目前以條碼篩選報表。
    
    ![未篩選圖示](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-unfiltered-icon.png) 指出報表目前未以條碼篩選。 
* 行動裝置應用程式僅針對在所有報表資料表中只有一個條碼資料行的報表支援條碼篩選。 如果您掃描的條碼有一個以上的條碼資料行，就不會進行篩選。

## <a name="issues-with-scanning-a-barcode"></a>條碼掃描問題
以下是當您掃描專案的條碼時，可能會遇到的一些 issus。

* 您收到訊息 **無法篩選報表-看起來就是此條碼不存在於報表資料中**：這表示您掃描的條碼值不會出現在您選擇要篩選的報表 datamodel 中。 比方說，如果您掃描的條碼未包含在報表中，就可能會發生這種情況。 您可以掃描不同的產品、選擇不同的報表 (如有多份報表可供選擇)，或檢視未經篩選的報表。

* 您會看到一則訊息 **看起來像您沒有任何可由條碼篩選的報表**：這表示您沒有任何已啟用條碼的報表。 條碼掃描器只能篩選具有 [條碼] 資料行的報表。 請確定您或報表擁有者已在 Power BI Desktop 中將資料行標記為 [條碼]。 深入了解[在 Power BI Desktop 中標記條碼欄位](../../transform-model/desktop-mobile-barcodes.md)

* 篩選會傳回空白狀態。 這可能表示您掃描的條碼值存在於模型中，但是報表中的所有或部分視覺效果都不會包含此值。 在此情況下，請嘗試查看其他報表頁面，或在 Power BI Desktop 中編輯您的報表以包含此值 

## <a name="next-steps"></a>後續步驟
* [在 Power BI Desktop 中標記條碼欄位](../../transform-model/desktop-mobile-barcodes.md)
* [Power BI 的儀表板磚](../end-user-tiles.md)
* [Power BI 中的儀表板](../end-user-dashboards.md)