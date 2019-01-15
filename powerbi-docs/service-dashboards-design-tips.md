---
title: 設計絕佳 Power BI 儀表板的秘訣
description: 設計絕佳 Power BI 儀表板的秘訣
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/22/2018
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: a113cf75ae238b19cdc54b03ffc049bdcdfb8368
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2019
ms.locfileid: "54281796"
---
# <a name="tips-for-designing-a-great-power-bi-dashboard"></a>設計絕佳 Power BI 儀表板的秘訣
現在您已經建立儀表板，及新增了某些圖格，請思考如何讓您的儀表板不只是好看，同時功能也更強。 一般而言，這代表將最重要的資訊設定為待命，讓它簡潔且整齊。

以下是一些秘訣。

> [!TIP]
> 報表的許多設計準則也適用於儀表板。  閱讀我們的技術白皮書︰[報表和視覺效果的最佳設計準則](visuals/power-bi-visualization-best-practices.md)。
>
>

## <a name="watch-the-dashboard-makeover-webinarhttpsinfomicrosoftcomco-powerbi-wbnr-fy16-05may-12-dashboard-makeover-registrationhtml"></a>觀賞[儀表板改造網路研討會](https://info.microsoft.com/CO-PowerBI-WBNR-FY16-05May-12-Dashboard-Makeover-Registration.html)
了解 Microsoft 首席專案經理暨 Power BI 儀表板專家 Marc Reguera 如何[進行儀表板改造](https://info.microsoft.com/CO-PowerBI-WBNR-FY16-05May-12-Dashboard-Makeover-Registration.html)。

## <a name="consider-your-audience"></a>請考慮您的對象
什麼關鍵度量能幫助他們做出決策？ 他們將如何使用儀表板？ 哪些已了解的或文化特性的假設可能會影響設計選擇？ 哪些資訊是您的對象邁向成功所需？

請記得，儀表板是概觀，是用來監控資料目前狀態的單一位置。 儀表板以基礎報表和資料集為基礎，其中可包含大量詳細資料。 讀者可以從您的儀表板鑽研報表。 因此除非讀者需要監視詳細資料，否則不要將詳細資料放在儀表板上。

儀表板會在哪裡顯示？ 如果儀表板位於大型監視器上，您可以在上面放置更多的內容。 如果讀者將在平板電腦上檢視，則較少的圖格會更容易閱讀。

## <a name="tell-a-story-and-keep-it-to-one-screen"></a>說個故事並保存到一個畫面
因為儀表板的用意是要一目瞭然地顯示重要資訊，所以在一個畫面上有全部的圖格最為理想。 可以避免在儀表板上使用捲軸嗎？

儀表板過於雜亂嗎？  移除必要資訊以外的所有內容，可以更加輕鬆地讀取和解譯。

## <a name="make-use-of-full-screen-mode"></a>使用全螢幕模式
以[全螢幕](consumer/end-user-focus.md)顯示儀表板，不會分散注意力。

## <a name="make-the-most-important-information-biggest"></a>將最重要的資訊大小調整為最大
如果儀表板上的文字和視覺效果大小都一樣，您的讀者會很難專注於最重要的內容。 例如，卡片視覺效果是凸顯重要數字的好方法：  
![卡片視覺效果](media/service-dashboards-design-tips/pbi_card.png)

但請務必提供內容。  

了解[只用一個數字來建立磚](visuals/power-bi-visualization-card.md).

## <a name="put-the-most-important-information-in-the-upper-corner"></a>將最重要的資訊放在左上角
大部分的人從上往下讀取，所以將最高層級的詳細資料放置在頂端，並且當您順著對象閱讀的方向移動時，會顯示更多的詳細資料 (由左到右、由右到左)。

## <a name="use-the-right-visualization-for-the-data-and-format-it-for-easy-reading"></a>為資料使用正確的視覺效果，並將其格式化以方便閱讀
請不要只是為了不同而讓視覺效果不同。  視覺效果應該要能繪製圖片，且應該要很容易「閱讀」及解譯。  對某些資料和視覺效果而言，簡單的圖形視覺效果已經綽綽有餘。 但是其他資料可能需要更複雜的視覺效果 - 請務必使用標題和標籤，以及使用其他自訂項目，以協助讀者。  

* [選擇適當的資料視覺效果](https://www.youtube.com/watch?v=-tdkUYrzrio)。 請小心使用會扭曲實際情況的圖表，也就是立體圖表。 請記住，人腦很難解譯有圓弧的圖形。 圓形圖、環圈圖、量表圖和其他有圓弧的圖表類型可能很好看，但它們不是資料視覺效果的最佳做法。
* 軸的圖表刻度、圖表維度次序，以及在圖表內維度值所用的色彩務必保持一致。
* 請務必小心地編碼量化資料。 顯示數字時，不要超過三或四個數字。 量值應在小數點、千位數、百萬等左邊顯示為一或兩個數字，亦即可以將量值顯示為 3.4 百萬，而不要顯示為 3,400,000。
* 請勿混合精確度和時間的等級。 請確定時間框架可讓人充分了解。  不要讓上個月的圖表緊鄰從該年度指定月份篩選出的圖表。
* 在折線圖或橫條圖之類的圖表上，請勿在相同刻度混合大的和小的量值。  例如，一個量值可能數以百萬計，而其他量值以千為單位。  如果刻度太大，會很難看到以千為單位之量值的差異。  如果您需要混合，請選擇允許使用第二個軸的視覺效果。
* 不要擾亂包含不必要資料標籤的圖表。 橫條圖中的值通常易於了解，而不需顯示實際數目。
* 請注意[圖表如何排序](consumer/end-user-change-sort.md)。  如果您想要強調最高或最低數字，請依量值排序。  如果您想要在許多其他類別目錄內，能夠快速尋找特定分類，請依軸排序。  
* 圓形圖最適合具有少於八個類別目錄的量值。 因為您無法以並排方式比較值，所以在圓形圖中比較值，會比在橫條圖和直條圖中比較值更困難。 圓形圖適於檢視部分與整體的關聯性，而不是用於部分比較。 量表圖非常適合用來在目標內容中顯示目前狀態。

如需更多特定視覺效果的指引，請參閱[ Power BI 中的視覺效果類型](visuals/power-bi-visualization-types-for-reports-and-q-and-a.md).  

## <a name="learning-more-about-best-practice-dashboard-design"></a>深入了解儀表板設計最佳做法
若要精通絕佳儀表板設計的藝術，請考量了解視覺認知的基本格式塔原則 (Gestalt Principle)，以及了解如何清楚說明內容中可付諸行動的資訊。 幸好到處有大量的資源可供使用，且在我們的部落格內俯拾皆是。 幾本我們最喜愛的書籍包括：

* *Information Dashboard Design* ，作者：Stephen Few  
* *Show Me the Numbers* ，作者：Stephen Few  
* *Now You See It* ，作者：Stephen Few  
* *Envisioning Information* ，作者：Edward Tufte  
* *Advanced Presentations by Design* ，作者：Andrew Abela   

## <a name="next-steps"></a>後續步驟
[從報表建立儀表板](service-dashboard-create.md)  
[Power BI - 基本概念](consumer/end-user-basic-concepts.md)  
有其他問題嗎？ [試試 Power BI 社群](http://community.powerbi.com/)
