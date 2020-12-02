---
title: 透過問與答提出問題的祕訣與訣竅
description: 透過 Power BI 中的問與答提出問題的秘訣和訣竅
author: mihart
ms.author: mihart
ms.reviewer: Mohammad.ali
ms.service: powerbi
ms.subservice: pbi-explore
ms.topic: how-to
ms.date: 09/23/2020
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 7757c883daee390b8cdcc93e0d6b9f8376d53f62
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96389820"
---
# <a name="tips-for-asking-questions-in-power-bi-qa"></a>在 Power BI 問與答中詢問問題的秘訣

[!INCLUDE[consumer-appliesto-yyny](../includes/consumer-appliesto-yyny.md)]

## <a name="words-and-terminology-that-qa-recognizes"></a>問與答可辨識的字組與專有名詞
此頁面上列出的關鍵字不是全部的關鍵字。  想知道 Power BI 能否辨識關鍵字的最佳辦法，就是在問題方塊中輸入關鍵字。  如果單字或字詞呈現灰色，則 Power BI 無法辨識它。

下列清單使用現在式，但所有時態在大部分情況下皆可辨識。 例如，"is" 包括：**are**、**was**、**were**、**will be**、**have**、**has**、**had**、**will have**、**has got**、**do**、**does**、**did**。  而 "sort" 包括：**sorted** 與 **sorting**。  Power BI 也可辨識且包含單字的單複數形態。 

> [!NOTE]
> 現在 [iPad、iPhone 及 iPod Touch 裝置上的 iOS 版 Microsoft Power BI 應用程式](mobile/mobile-apps-ios-qna.md)也提供問與答。
>  


|類別  |關鍵字  |
|---------|---------|---------|
|**彙總**     | total、sum、amount、number、quantity、count、average、most、least、fewest、largest、smallest、highest、biggest、maximum、max、greatest、lowest、littlest、minimum、min          |
|     |         |         
**冠詞**     |  a、an、the              |
|     |         |         
|**空白和布林值**     |   blank、empty、null、前綴 "non" 或 "non-"、empty string、empty text、true、t、false、f          |
|     |         |         |
|**比較**     |   vs、versus、compared to、compared with            |
|     |         |         |
|**連接詞**     |  and、or、each of、with、versus、&、and、but、nor、along with、in addition to       |         
|          |         |
|**縮寫**     |  問與答可辨識幾乎所有的縮寫，請試試看。以下是一些範例：didn't、haven't、he'd、he's、isn't、it's、she'll、they'd、weren't、who's、won't、wouldn't          |
|        |         |
|**日期**     |       Power BI 可辨識大部分的日期字詞 (day、week、month、year、quarter、decade、...) 和許多不同的日期格式 (請見下文)。 Power BI 也會辨識下列關鍵字：MonthName、Days 1-31、decade。 範例：January 3rd of 1995、January 3rd 1995、jan 03 1995、3 Jan 1995、the 3rd of January、January 1995、1995 January、1995-01、01/1995、月份名稱         |
|        |         |
|**相對日期**     |   today、right now、current time、yesterday、tomorrow、the current、next、the coming、last、previous、ago、before now、sooner than、after、later than、from、at、on、from now、after now、in the future、past、last、previous、within、in、over、N days ago、N days from now、next、once、twice。|
|    |  範例︰count of orders in the past 6 days。  |            |
|        |         |
|**相等 (範圍)**     |   in、equal to、=、after、is more than、in、between、before  |
|  |範例：Order year is before 2012? (訂購年份是在 2012 前的？) Price equals between 10 and 20? (大於等於 10、小於等於 20 的價格？) Is the age of John greater than 40? (John 超過 40 歲了嗎？) Total sales in 200-300? (介於 200-300 之間的銷售總額？)              |
|        |         |
|**相等 (值)**     |   is、equal、equal to、in、of、for、within、is in、is on |
|   | 範例：哪些產品是綠色的？ Order date equals 2012. (訂單日期為 2012 年。) Is the age of John 40? (John 40 歲嗎？) Total sales that aren't equal to 200? (不等於 200 的總銷售額？) Order date of 1/1/2016. (訂單日期是 2016 年 1 月 1 日。) 10 in price? (價格為 10？) Green for color? (顏色是綠色嗎？) 10 in price? (價格為 10？)              |
|        |         |
|**名稱**     |       如果資料集中的資料行包含片語 "name" (例如 EmployeeName)，則問與答了解該資料行中的值是名稱。 您可以問問題如 "which employees are named robert" (叫 robert 的員工是誰)。          |
|        |         |
**代名詞**  | he、him、himself、his、she、herself、her、hers、it、itself、its、they、their、them、themselves、theirs、this、these、that、those
|**查詢命令**     |    sorted、sort by、direction、group、group by、by、show、list、display、give me、name、just、only、arrange、rank、compare、to、with、against、alphabetically、ascending、descending、order             |
|        |         |
|**範圍**     |      greater、more、larger、above、over、>、less、smaller、fewer、below、under、<、at least、no less than、>=、at most、no more than、<=、in、between、in the range of、from、later、earlier、sooner、after、on、at、later than、after、since、starting with、starting from、ending with           |
|        |         |
**時間**  |am、pm、o'clock、noon、midnight、hour、minute、second、hh:mm:ss  |
|  |  範例：10 pm、10:35 pm、10:35:15 pm、10 o clock、noon、midnight、hour、minute、second。  |
|  |  |
|**前 N 個**     |     (順序、排名)：top、bottom、highest、lowest、first、last、next、earliest、newest、oldest、latest、most recent、next            |
|        |         |
|**視覺效果類型**     |  所有視覺效果類型對於 Power BI 都是原生的。  如果是 [視覺效果] 窗格中的選項，就可以包含在問題中。  此規則例外狀況是已手動新增至 [視覺效果] 窗格的 [Power BI 自訂視覺效果](../developer/visuals/power-bi-custom-visuals.md)。  |
|  |  範例︰以橫條圖依月份和銷售總額顯示區域資料               |
|        |         |
|**Wh (關係詞、限定詞)**  | when、where、which、who、whom、how many、how much、how many times、how often、how frequently、amount、number、quantity、how long、what                |

## <a name="qa-helps-you-phrase-the-question"></a>問與答可協助您將問題分段
問與答會盡全力了解並回答所提出的問題。 它會嘗試以數種方式去了解。 針對所有片語，您都可以完整、部分或完全不接受該動作。 當您輸入問題時，問與答會：

* 自動完成單字與問題。 它會使用各種策略，包括自動完成辨識單字、儲存的問題，以及傳回有效回應之先前使用的問題。 如果有一個以上的自動完成選項可使用，則選項會出現在下拉式清單中。
* 更正拼字。
* 以視覺效果形式提供回答的預覽結果。 視覺效果會在您鍵入及編輯問題時更新 (不用等您按下 Enter 鍵)。
* 將游標移回 [問題] 方塊時，從基礎資料集建議取代的字詞。
* 依據基礎資料集中的資料，再次陳述問題。 問與答會將您使用的單字取代為來自基礎資料集的同義字。 透過閱讀重新陳述的內容，您可以知道問與答是否了解您的問題。 
* 將不了解的字組加上雙底線。
* 將不了解的字組加上單底線。
* 在找不到字詞或問題沒有得到結果時，讓您連絡報表或儀表板擁有者。

## <a name="dont-stop-now"></a>不立即停止
問與答顯示您的結果之後，持續保存交談內容！ 使用視覺效果的互動功能與問答集，發掘更多深入資訊。

## <a name="next-steps"></a>後續步驟
回到 [Power BI 中的問與答](end-user-q-and-a.md)  

[Power BI - 基本概念](end-user-basic-concepts.md)  

有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)

