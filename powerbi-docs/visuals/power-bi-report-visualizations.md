---
title: Power BI 服務和 Desktop 中的報表視覺效果概觀
description: Microsoft Power BI 中的報表視覺效果概觀。
author: mihart
ms.author: mihart
ms.reviewer: mihart
featuredvideoid: ''
ms.service: powerbi
ms.subservice: pbi-visuals
ms.topic: how-to
ms.date: 05/05/2020
LocalizationGroup: Visualizations
ms.openlocfilehash: b6b4ebb7d07ec73f8b2c51b7b2fabb75b197d91f
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96387428"
---
# <a name="visualizations-in-power-bi-reports"></a>Power BI 報表的視覺效果

[!INCLUDE[consumer-appliesto-yyyn](../includes/consumer-appliesto-yyyn.md)]    

視覺效果會顯示在資料中探索到的見解。 Power BI 報表可能需要有一個視覺效果的單一頁面，或是它可能會有充滿視覺效果的頁面。 在 Power BI 服務中，視覺效果可以[從報表釘選至儀表板](../create-reports/service-dashboard-pin-tile-from-report.md)。

請務必區隔報表「設計師」和報表「取用者」。  如果您是建置或修改報表的人，您就是設計師。  設計師具有報表及其基礎資料集的編輯權限。 在 Power BI Desktop 中，這表示您可以在資料檢視中開啟資料集，並在報表檢視建立視覺效果。 在 Power BI 服務中，這表示您可以用[編輯檢視](../consumer/end-user-reading-view.md)在報表編輯器中開啟資料集或報表。 如果報表或儀表板已 [與您共用](../consumer/end-user-shared-with-me.md)，您就是報表 *取用者*。 您可以檢視報表及其視覺效果並與其互動，但無法與「設計工具」一樣進行許多變更。

有許多不同的視覺效果類型可以直接從 Power BI 的 [視覺效果] 窗格使用。

![具有每個視覺效果類型圖示的窗格](media/power-bi-report-visualizations/power-bi-icons.png)

您可從 [Microsoft AppSource 社群網站](https://appsource.microsoft.com) 取得更多 Power BI 視覺效果。 在 AppSource 中，您可以瀏覽並[下載](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) Microsoft 和社群所提供的 Power BI 視覺效果。

如果您是 Power BI 新手，或需要喚起記憶，請使用下列連結了解 Power BI 視覺效果的基本概念。  或者，使用我們的目錄 (沿著本文的左邊)，來找到更多有用的資訊。

## <a name="add-a-visualization-in-power-bi"></a>在 Power BI 中加入視覺效果

在報表的頁面上[建立視覺效果](power-bi-report-add-visualizations-i.md)。 瀏覽[可用視覺效果清單和可用視覺效果教學課程](power-bi-visualization-types-for-reports-and-q-and-a.md)。 

## <a name="upload-a-visualization-from-a-file-or-from-appsource"></a>從檔案或從 AppSource 上傳視覺效果

新增自行建立或在 [Microsoft AppSource 社群網站](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals) 中找到的視覺效果。 腦中充滿創造力嗎？ 深入探索我們的原始程式碼，並使用我們的[開發人員工具](../developer/visuals/environment-setup.md)來建立新的視覺效果類型，然後[將其與社群共用](../developer/visuals/office-store.md)。 若要深入了解開發 Power BI 視覺效果，請瀏覽[開發 Power BI 視覺效果](../developer/visuals/develop-circle-card.md)。

## <a name="personalize-your-visualization-pane"></a>將 [視覺效果] 窗格個人化

您可透過在 [視覺效果] 窗格中新增和移除 Power BI 視覺效果，將 [視覺效果] 窗格個人化。 如果您已從 [視覺效果] 窗格移除預設視覺效果，則可將窗格還原為預設，並取回所有的預設視覺效果。

### <a name="add-a-visual-to-the-visualization-pane"></a>將視覺效果新增至 [視覺效果] 窗格

如果您發現自己跨許多報表使用相同的視覺效果，則可將視覺效果新增至 [視覺效果] 窗格。 新增視覺效果適用於 AppSource 視覺效果、組織視覺效果，以及檔案中的視覺效果。 若要新增視覺效果，請以滑鼠右鍵按一下視覺效果。

![釘選到視覺效果窗格](media/power-bi-report-visualizations/power-bi-pin-custom-visual-option.png)

視覺效果一經釘選，就會上移以和其他預設視覺效果待在一起。 假設您已登入，則此視覺效果現在會繫結至您登入的帳戶，因此您建置的任何新報表都會自動包含此視覺效果。 您不再需要將經常使用的特定視覺效果新增至每一份報表。

![個人化的視覺效果窗格](media/power-bi-report-visualizations/power-bi-personalized-visualization-pane.png)

### <a name="remove-a-visual-from-the-visualization-pane"></a>從 [視覺效果] 窗格移除視覺效果

如果您經常停止使用某個視覺效果，則可在其上按一下滑鼠右鍵，並從 [視覺效果] 窗格中加以移除。 任何類型的視覺效果都可從 [視覺效果] 窗格中移除，包括預設視覺效果、檔案視覺效果、組織視覺效果和 AppSource 視覺效果。

![取消釘選到 [視覺效果] 窗格](media/power-bi-report-visualizations/unpin-visual.png)

### <a name="restore-the-visualization-pane"></a>還原 [視覺效果] 窗格

還原 [視覺效果] 窗格僅適用於預設視覺效果。 新增至 [視覺效果] 窗格的視覺效果不會受到影響，且可在 [視覺效果] 窗格中繼續提供使用。 如果想要從 [視覺效果] 窗格中移除 AppSource 視覺效果或檔案視覺效果，將必須手動執行此動作。

若要將 [視覺效果] 窗格還原為預設，請按一下更多選項，然後選取 [還原預設視覺效果]。

![將 [視覺效果] 窗格還原為預設](media/power-bi-report-visualizations/restore-default.png)

## <a name="change-the-visualization-type"></a>變更視覺效果類型

請嘗試[變更視覺效果的類型](power-bi-report-change-visualization-type.md)，查看何者最適合您的資料。

## <a name="pin-the-visualization"></a>釘選視覺效果

在 Power BI 服務中，當視覺效果是您想要的呈現方式時，就可以[將其釘選到儀表板](../create-reports/service-dashboard-pin-tile-from-report.md)作為磚。 如果在釘選之後變更報表中使用的視覺效果，並不會變更儀表板上的磚。 若其為折線圖，則會保持為折線圖，即使您在報表中將其變更為環圈圖也是一樣。

## <a name="limitations-and-considerations"></a>限制與考量
- 視資料來源和欄位 (量值或資料行) 數目而定，視覺效果載入可能很緩慢。  基於可讀性和效能考量，建議將視覺效果的欄位總數限制在 10-20。 

- 視覺效果上限是 100 個欄位 (量值或資料行)。 如果無法載入視覺效果，請減少欄位數目。

## <a name="next-steps"></a>後續步驟

* [Power BI 中的視覺效果類型](power-bi-visualization-types-for-reports-and-q-and-a.md)
* [Power BI 視覺效果](../developer/visuals/power-bi-custom-visuals.md)
