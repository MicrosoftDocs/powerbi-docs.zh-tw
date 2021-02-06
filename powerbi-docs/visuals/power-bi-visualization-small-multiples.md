---
title: '在 Power BI (preview 中建立小型倍數) '
description: 小倍數（或 trellising）會將視覺效果分割成多個版本，並並排顯示，並依選定的維度將其資料分割在這些版本中。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: mihart
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 02/05/2021
LocalizationGroup: Visualizations
ms.openlocfilehash: bc1f890e588227f9d0dc30202474a8f77f93fc38
ms.sourcegitcommit: f17acb16018752c234db6bff1f51f5130be12c58
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/06/2021
ms.locfileid: "99617309"
---
# <a name="create-small-multiples-in-power-bi-preview"></a>在 Power BI (preview 中建立小型倍數) 

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

小倍數（或 trellising）會將視覺效果分割成多個版本。 版本會並存呈現，而資料會依所選的維度分割到這些版本。 例如，小型倍數可以跨產品線或區域分割「依類別銷售」直條圖。 在此預覽中，小型倍數有一小部分的功能，未來的版本將提供更多的功能。

:::image type="content" source="media/power-bi-visualization-small-multiples/small-mulitple-sales-category-region.png" alt-text="類別和區域小型倍數的螢幕擷取畫面。":::

## <a name="enable-the-preview-feature"></a>啟用預覽功能

**在 [檔案**] 功能表上，選取 [**選項及設定**  >  **選項**  >  **預覽功能**]，然後選取 [**小倍數**] 核取方塊。

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-enable-preview.png" alt-text="啟用小型倍數的預覽。":::

重新開機 Power BI Desktop，您就可以開始嘗試小倍數。

## <a name="create-small-multiples"></a>建立小倍數

目前，您可以在橫條圖、直條圖、折線圖和區域圖上建立小型倍數。 

若要開始使用，請建立上述其中一個視覺效果，並選擇您想要用來分割資料的欄位。 將該欄位拖曳到 [視覺效果] 窗格的 [欄位] 區段中的 **小倍數** 。 您的圖表會分割成2×2格線，並將資料分割成您選擇的維度。 方格會填滿小型倍數圖表。 它們是依您選擇的排序次序、從左至右，然後從上到下排序。

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-two-by-two-grid.png" alt-text="兩個方格中的小倍數。":::

您會看到軸已同步處理。 每個資料列的左邊都有一個 Y 軸，而每個資料行底部有一個 X 軸。

既然您已建立小倍數，請參閱 [Power BI (preview) 中與小型倍數互動的 ](power-bi-visualization-small-multiples-interact.md)方式。

## <a name="format-a-small-multiples-visual"></a>設定小型倍數視覺效果的格式

[格式化] 窗格中的一些新選項，可讓您控制方格的外觀和風格。

### <a name="change-the-grid-dimensions"></a>變更方格維度

您可以變更方格配置卡片中的方格維度：

:::image type="content" source="media/power-bi-visualization-small-multiples/small-multiple-grid-layout-card.png" alt-text="小型多重格線版面配置卡片。":::

預設值為2×2方格的小倍數，但您可以將資料列和資料行的數目調整為最多6×6。 當您向下滾動時，不符合該方格的任何倍數就會載入。


### <a name="adjust-the-small-multiples-titles"></a>調整小倍數的標題

如同其他視覺效果標題，您可以調整 **小型多重標題** 卡中小型多個標題的樣式和位置。

## <a name="preview-limitations"></a>預覽限制

雖然這項功能處於預覽狀態，但我們仍持續努力確定它能與其余的功能互動。 以下是一些目前的限制。

### <a name="fields-pane"></a>欄位窗格

- 日期和其他連續階層：假設您的視覺效果類似于 X 軸中有日期階層的折線圖。 當您對其進行小倍數時，Power BI 會將該軸從連續轉換成類別目錄軸。
- 顯示沒有資料的專案：此選項仍存在，但行為可能不符合您的預期。

### <a name="visual-interactions"></a>視覺效果互動

- 在類別目錄軸上滾動載入更多：在軸上具有許多類別的標準視覺效果中，當您在軸的結尾處滾動時，視覺效果會載入更多類別目錄。 目前，小倍數的視覺效果不會載入更多分類。
- 依量值排序小倍數：小型倍數的排序是新功能。 您可能預期會使用量值來排序您的小倍數。 目前，您只能依據欄位的自然排序次序來排序倍數。
- 以滑鼠右鍵按一下/內容功能表-> 分析：目前已停用。
- 以滑鼠右鍵按一下/內容功能表-> 摘要： [目前已停用]。
- 選取多個具有矩形 select 的資料點：目前已停用。
- 軸縮放：目前已停用。
- 協助工具：您可以調整鍵盤流覽和螢幕 readouts，以更有效地支援小型倍數帶至視覺效果的新「格線」圖層。 缺少某些行為，例如透過類別軸捲軸的鍵盤流覽。

### <a name="formatting-options"></a>格式化選項

**一般**

- 回應式切換：此選項仍存在，但行為可能不符合您的預期。 由於許多行動設備的住宿都系結到此切換，因此行動體驗也會與您在 Power BI Desktop 和 Power BI 服務中找到的體驗緊密地反映。
- 高密度取樣：折線圖的高密度取樣切換仍然存在，但小倍數目前不支援。

**軸**

- 串連標籤：目前已停用。

**總計標籤**

- 堆疊圖的標籤總計：目前已停用。

**縮放滑杆**

- 縮放滑杆：目前已停用。

**[分析] 窗格** 

- 趨勢線：目前已停用。
- 預測：目前已停用。

醒目提示標籤的動態格式：目前不支援。
服務可用性

## <a name="authoring-in-the-power-bi-service"></a>在 Power BI 服務中撰寫

當此功能處於預覽狀態時，不支援在 web 上撰寫小型倍數。 您可以使用小型倍數視覺效果來查看報表，甚至可以格式化視覺效果。 但是，您無法將標準視覺效果轉換成 Power BI 服務中的小型倍數視覺效果。 視覺效果在 [小倍數] 欄位中必須已經有一個欄位，否則該視覺效果將不會顯示小倍數。

## <a name="share-your-feedback"></a>分享您的意見反應

請讓我們知道您對小型倍數視覺效果的看法：

- [Power BI 社群](https://community.powerbi.com/)
- [Power BI 構想頁面](https://ideas.powerbi.com/ideas/) 

## <a name="next-steps"></a>下一步

[Power BI (preview 中的小型倍數互動) ](power-bi-visualization-small-multiples-interact.md)
