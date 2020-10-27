---
title: 個人化報表中的視覺效果
description: 建立您自己的報表檢視，而不需要進行編輯。
author: mihart
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: how-to
ms.date: 10/13/2020
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 718363da3bd1f66de199db8d854d8d23d6de3eb5
ms.sourcegitcommit: eab5a02520c421a57019595c03e9ecfdb41d52ad
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/20/2020
ms.locfileid: "92256727"
---
# <a name="personalize-visuals-in-a-report"></a>個人化報表中的視覺效果

[!INCLUDE[consumer-appliesto-ynny](../includes/consumer-appliesto-ynny.md)]

一個視覺效果不能滿足所有人的要求。 但當同事與您共用報表時，您可能會想要變更視覺效果，而不需要要求您的同事為您進行變更。 

您可能會想要切換軸上的內容、變更視覺效果類型，或將某些內容新增至工具提示中。 透過 **個人化此視覺效果** 功能，您可以自行進行變更，當您擁有所需的視覺效果時，請將其另存為 [書籤](end-user-bookmarks.md)，以供您返回。 您甚至不需要報表的編輯權限。

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize.png" alt-text="個人化視覺效果":::
 
## <a name="what-you-can-change"></a>您可以變更的內容

此功能可協助您透過臨機操作探索 Power BI 報表視覺效果，獲取深入見解。 以下是您可以進行的一些修改。 可用的選項會因視覺效果類型而異。 

- 變更視覺效果類型
- 切換量值或維度
- 新增或移除圖例
- 比較兩個或多個量值
- 變更彙總等等

這項功能不僅允許探索新功能。 也能讓您以各種方式擷取及共用您的變更：

- 擷取您的變更
- 共用您的變更
- 針對報表重設您的所有變更
- 針對視覺效果重設您的所有變更
- 清除您最近的變更

> [!IMPORTANT]
> 個人化視覺效果的功能必須由報表「設計師」啟用。 如果您看不到 [個人化此視覺效果] ![個人化此視覺效果圖示](media/end-user-personalize-visuals/power-bi-personalize-visual-icon.png) 圖示，則表示報表設計師尚未針對目前的報表啟用此功能。 請洽詢報表擁有者或您的 Power BI 管理員，以啟用此功能。 若要顯示報表擁有者的連絡人資訊，請從 Power BI 功能表列中選取報表的名稱。

## <a name="personalize-visuals-in-the-power-bi-service"></a>Power BI 服務中的個人化視覺效果

透過個人化視覺效果，您無須[離開報表閱讀檢視](end-user-reading-view.md)，就可以利用許多方式探索資料。 下列範例顯示修改視覺效果以符合您需求的不同方法。 

1. 在 Power BI 服務中，以閱讀檢視開啟報表。

2. 在視覺效果的功能表列中，選取 [個人化此視覺效果] ![個人化此視覺效果圖示](media/end-user-personalize-visuals/power-bi-personalize-visual-icon.png)圖示。 

### <a name="change-the-visualization-type"></a>變更視覺效果類型

您認為資料以堆疊直條圖顯示是否會更好？ 變更 **視覺效果類型** 。

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-change-visual-type.png" alt-text="個人化視覺效果":::
 
### <a name="swap-out-a-measure-or-dimension"></a>切換量值或維度
透過選取您要取代的欄位，然後選取不同的欄位，來取代 X 軸所使用的欄位。

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-change-axis.png" alt-text="個人化視覺效果":::
 
### <a name="add-or-remove-a-legend"></a>新增或移除圖例
您可以透過新增圖例，根據類別建立視覺效果色彩代碼。 在此範例中，我們根據公司名稱進行色彩編碼。 

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-change-legend.png" alt-text="個人化視覺效果":::

### <a name="change-the-placement-of-fields"></a>變更欄位的位置

使用拖放功能，您可以變更相同視覺效果屬性內欄位的位置，甚至可跨不同的視覺效果屬性進行變更。 例如，您可以將圖例中的欄位快速移至視覺效果的軸。

:::image type="content" source="media/end-user-personalize-visuals/personalize-drag-and-drop.png" alt-text="個人化視覺效果":::

您也可以快速地重新排序資料表或矩陣的欄。

:::image type="content" source="media/end-user-personalize-visuals/personalize-reorder-columns.png" alt-text="個人化視覺效果":::

### <a name="compare-two-or-more-different-measures"></a>比較兩個或多個不同的量值
您可以使用 [+] 圖示為視覺效果新增多個量值，以比較和對比不同量值的值。 若要移除量值，請選取 [更多選項 (...)]，然後選擇 [移除欄位]。

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-compare-measures.png" alt-text="個人化視覺效果":::

### <a name="change-aggregations"></a>變更彙總
透過變更 [個人化] 窗格中的彙總，變更量值的計算方式。 選取 [更多選項 (...)] 並選擇要使用的彙總。

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-change-aggregation.png" alt-text="個人化視覺效果":::

### <a name="capture-changes"></a>擷取變更 
使用個人書籤擷取您的變更，以回到個人化檢視。 選取 [書籤] > [個人書籤] 並指定書籤的名稱。 

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-bookmark.png" alt-text="個人化視覺效果":::
 
您也可以將書籤設定為預設檢視。

### <a name="share-changes"></a>共用變更 
您若擁有讀取及再次共用的權限，即可在共用報表時，選擇包含您的變更。

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-share-changes.png" alt-text="個人化視覺效果":::
 
### <a name="reset-all-your-changes-to-a-report"></a>重設報表的所有變更

從報表畫布的右上角，選取 [重設為預設值]。 這會移除報表中的所有變更，並設回作者上次儲存的報表檢視。

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-reset-all.png" alt-text="個人化視覺效果":::
 
### <a name="reset-all-your-changes-to-a-visual"></a>重設視覺效果的所有變更

從視覺效果的功能表列，選取 [重設此視覺效果]，以移除特定視覺效果的所有變更，並設回作者上次儲存的視覺效果檢視。

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-reset-visual.png" alt-text="個人化視覺效果":::
 
### <a name="clear-recent-changes"></a>清除最近的變更

選取橡皮擦圖示，清除您在開啟 [個人化] 窗格之後的所有最近變更。  

:::image type="content" source="media/end-user-personalize-visuals/power-bi-personalize-revert-changes.png" alt-text="個人化視覺效果":::

## <a name="limitations"></a>限制

此功能目前有一些要注意的限制。

- [個人化此視覺效果] 可以針對整個報表或特定視覺效果關閉。 若沒有可個人化視覺效果的選項，請洽詢 Power BI 管理員或報表擁有者。 若要顯示報表擁有者的連絡人資訊，請從 Power BI 功能表列中選取報表的名稱。
- 不會自動保存使用者的探索。 您需要將檢視儲存為個人書籤，才能擷取您的變更。
- 適用於 iOS 和 Android 平板電腦的 Power BI 行動裝置應用程式，以及 Power BI Windows 應用程式，都支援這項功能；手機的 Power BI 行動裝置應用程式不支援此功能。 但使用 Power BI 服務儲存在個人書籤中的任何視覺效果變更，都會呈現在所有 Power BI 行動裝置應用程式中。

## <a name="next-steps"></a>後續步驟
[將報表視覺效果複製為靜態影像](../visuals/power-bi-visualization-copy-paste.md)    
有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)
