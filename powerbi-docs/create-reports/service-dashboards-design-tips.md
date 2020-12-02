---
title: 設計絕佳 Power BI 儀表板的秘訣
description: 設計絕佳 Power BI 儀表板的秘訣
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 08/14/2019
LocalizationGroup: Dashboards
ms.openlocfilehash: d1e2a3b304d7d92ee6443e288d77599cb734ff1a
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96388693"
---
# <a name="tips-for-designing-a-great-power-bi-dashboard"></a>設計絕佳 Power BI 儀表板的秘訣
現在您已經建立儀表板，及新增了某些圖格，請思考如何讓您的儀表板不只是好看，同時功能也更強。 一般而言，這代表將突顯最重要的資訊，讓它簡潔且整齊。

![行銷和銷售範例儀表板](media/service-dashboards-design-tips/power-bi-marketing-sample-dashboard.png)

> [!TIP]
> 喜歡這個儀表板？ 您可以從 AppSource 下載這個儀表板及相關報表。 請移至 [取得資料]   > [服務]  。 搜尋 [Microsoft 範例 - 銷售與行銷]   > [立即取得]  。

以下是儀表板的幾個祕訣。

## <a name="dashboard-design-best-practices-video"></a>儀表板設計最佳做法影片

請觀看 [Power BI 中的儀表板設計最佳做法](https://www.youtube.com/watch?v=-tdkUYrzrio)這段影片，以取得 SQLBI.com 的 Marco Russo 所提供設計祕訣。

## <a name="consider-your-audience"></a>請考慮您的對象
什麼關鍵度量能幫助他們做出決策？ 他們將如何使用儀表板？ 哪些已了解的或文化特性的假設可能會影響設計選擇？ 哪些資訊是您的對象邁向成功所需？

請記得，儀表板是概觀，是用來監控資料目前狀態的單一位置。 儀表板以基礎報表和資料集為基礎，這些項目通常包含大量詳細資料。 讀者可以從您的儀表板鑽研報表。 因此除非讀者需要監視詳細資料，否則不要將詳細資料放在儀表板上。

儀表板會在哪裡顯示？ 如果儀表板位於大型監視器上，您可以在上面放置更多的內容。 但是，如果讀者在其平板電腦上進行檢視，則磚較少的儀表板更易於閱讀。

## <a name="tell-a-story-on-one-screen"></a>在一個畫面上訴說故事
因為儀表板的用意是要一目瞭然地顯示重要資訊，所以在一個畫面上有全部的圖格最為理想。 可以避免在儀表板上使用捲軸嗎？

儀表板過於雜亂嗎？  移除必要資訊以外的所有內容，可更加輕鬆地讀取和解譯。

## <a name="make-use-of-full-screen-mode"></a>使用全螢幕模式
呈現儀表板時，以[全螢幕模式](../consumer/end-user-focus.md)顯示儀表板，不會分散注意力。

## <a name="accent-the-most-important-information"></a>強調說明最重要的資訊
如果儀表板上的文字和視覺效果大小都一樣，您的讀者會很難專注於最重要的內容。 例如，卡片視覺效果是凸顯重要數字的好方法：  
![卡片視覺效果](media/service-dashboards-design-tips/pbi_card.png)

但請務必提供內容。  

了解[只用一個數字來建立磚](../visuals/power-bi-visualization-card.md).

## <a name="place-the-most-important-information"></a>放置最重要的資訊
大部分的人從上往下讀取。 因此，將最高層級的資料放置在左上角，且當您順著對象閱讀的方向移動時，會顯示詳細資料 (由左到右、由上到下)。

## <a name="use-the-right-visualization-for-the-data"></a>針對資料使用合適的視覺效果
請不要只是為了不同而讓視覺效果不同。  視覺效果應該要能繪製圖片，且應該要很容易「閱讀」及解譯。  對某些資料和視覺效果而言，簡單的圖形視覺效果已經綽綽有餘。 但是其他資料可能需要更複雜的視覺效果 - 請務必使用標題和標籤，以及使用其他自訂項目，以協助讀者。  

* 請小心使用看起來很不錯但難以閱讀的視覺效果，例如 3D 圖表。 
* 了解圓形圖、環圈圖、量表圖和其他圓弧圖表類型並不是資料視覺效果的最佳做法，可能會令人失望。 圓形圖最適合具有少於八個類別目錄的量值。 因為人類無法以並排方式比較值，所以在圓形圖中比較值，會比在橫條圖和直條圖中比較值更困難。 圓形圖適於檢視部分與整體的關聯性，而不是用於部分比較。 量表圖非常適合用來在目標內容中顯示目前狀態。
* 軸的圖表刻度、圖表維度次序，以及在圖表內維度值所用的色彩務必保持一致。
* 請務必小心地編碼量化資料。 顯示數字時，不要超過三或四個數字。 量值應在小數點及千位或百萬數等左邊顯示為一或兩個數字，也就說可以將量值顯示為 3.4 百萬，而不要顯示為 3,400,000。
* 請勿混合精確度和時間的等級。 請確定時間框架可讓人充分了解。 不要讓上個月的圖表緊鄰從該年度指定月份篩選出的圖表。
* 在折線圖或橫條圖之類的圖表上，請勿在相同刻度上混合大量值和小量值。 例如，一個量值可能數以百萬計，而其他量值以千為單位。 如果刻度太大，會很難看到以千為單位的量值差異。 如果您需要混合，請選擇允許使用第二個軸的視覺效果。
* 不要擾亂包含不必要資料標籤的圖表。 橫條圖中的值通常易於了解，而不需顯示實際數目。
* 請注意[圖表如何排序](../consumer/end-user-change-sort.md)。 如果您想要強調最高或最低數字，請依量值排序。 如果您想要讓使用者在許多其他類別目錄內快速尋找特定分類，請依軸排序。  

如需更多特定視覺效果的指引，請參閱[ Power BI 中的視覺效果類型](../visuals/power-bi-visualization-types-for-reports-and-q-and-a.md).  

## <a name="learn-more-about-dashboard-design"></a>深入了解儀表板設計
若要精通絕佳儀表板設計的藝術，請考量了解視覺認知的基本格式塔原則 (Gestalt Principle)，以及了解如何清楚說明內容中可付諸行動的資訊。 幸好到處都有大量的資源可供使用，且散佈在我們的部落格內。 幾本我們最喜愛的書籍包括：

* *Information Dashboard Design* ，作者：Stephen Few  
* *Show Me the Numbers* ，作者：Stephen Few  
* 《現在看到了吧？量化分析視覺化訣竅》(*Now You See It*)，作者：Stephen Few  
* 《資訊圖像化設計》(*Envisioning Information*)，作者：Edward Tufte  
* *Advanced Presentations by Design* ，作者：Andrew Abela   

## <a name="next-steps"></a>後續步驟
[從報表建立儀表板](service-dashboard-create.md)  
[Power BI 服務中的設計工具基本概念](../fundamentals/service-basic-concepts.md)  
有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)
