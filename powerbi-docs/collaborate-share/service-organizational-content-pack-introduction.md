---
title: Power BI 中的組織內容套件簡介
description: 閱讀以了解如何將您的儀表板、報表、Excel 活頁簿和資料集封裝到可與同事共用的組織內容套件中。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 01/12/2021
LocalizationGroup: Share your work
ms.openlocfilehash: 038a0c57fe5994b2b15b64dfe67f3eda77ef86f2
ms.sourcegitcommit: ab28cf07b483cb4b01a42fa879b788932bba919d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2021
ms.locfileid: "98227092"
---
# <a name="intro-to-organizational-content-packs-in-power-bi"></a>Power BI 中的組織內容套件簡介

> [!NOTE]
> 組織內容套件即將淘汰。 如果您尚未開始，現在是將您的內容套件升級為應用程式的好時機。 如需時間表，請參閱[宣告 Power BI 系統管理員可升級傳統工作區](https://powerbi.microsoft.com/blog/announcing-power-bi-admins-can-upgrade-classic-workspaces-and-roadmap-update/) (英文) 此部落格文章的＜工作區升級藍圖＞一節。
> 

您有透過電子郵件向小組定期發佈報表嗎？ 改為嘗試：封裝您的儀表板、報表、Excel 活頁簿與資料集，然後將其發行到您的小組作為「組織內容套件」。 因為建立的內容套件全部都在 AppSource 內，所以您的小組很容易就可以找到。 因為它們是 Power BI 的一部分，所以能使用 Power BI 的所有功能，包括互動式資料瀏覽、新的視覺效果、問與答、與其他資料來源整合、資料重新整理等等。

![顯示組織內容套件的儀表板螢幕擷取畫面。](media/service-organizational-content-pack-introduction/power-bi-org-content-packs.png)

建立內容套件與共用儀表板或在工作區中於儀表板上進行共同作業不同。 閱讀[應該如何共同作業和共用儀表板和報表？](service-how-to-collaborate-distribute-dashboards-reports.md)，來為您的情況決定最佳選項。 

在 AppSource 中，您可瀏覽或搜尋發佈給整個組織、通訊群組或安全性群組以及[所屬 Microsoft 365 群組](https://support.office.com/article/Create-a-group-in-Office-365-7124dc4c-1de9-40d4-b096-e8add19209e9)的內容套件。 如果您不是某特定群組的成員，就看不到與該群組分享的內容套件。 所有的群組成員都有相同的權限，可以唯讀存取內容套件資料、報表、活頁簿和儀表板 (除了 SQL Server Analysis Services (SSAS) 資料來源以外，其權限是繼承自資料來源)。

儀表板、報表、Excel 活頁簿均為唯讀，但您可以從複製及使用儀表板與報表入手，開始建立您自己的個人化版本內容套件。

> [!NOTE]
> 僅有當您和同事具有 [Power BI Pro 授權](../fundamentals/service-features-license-type.md)時，才能使用組織內容套件。
> 
> 

## <a name="what-is-appsource"></a>什麼是 *AppSource*？
發行組織內容套件會將其新增至 AppSource。  這個集中式儲存機制讓成員輕鬆瀏覽及探索為他們發行的儀表板、報表和資料集。  

* 若要檢視 AppSource，請選取 [取得資料] > [我的組織] > [取得]。

## <a name="the-life-cycle-of-an-organizational-content-pack"></a>組織內容套件的生命週期
任何 Power BI Pro 的使用者都可以建立、發行並存取組織內容套件。 只有內容套件建立者才能修改活頁簿和資料集、排定重新整理，以及刪除。

生命週期看起來像這樣：

1. 在 Power BI Pro 中，Nate 建立了一個內容套件，並將其發行至「行銷」通訊群組中。 因為重新整理設定和資料集要一起繼承，所以只有 Nate 可以變更。
   
   > [!NOTE]
   > 如果 Nate 從其所在的 [Power BI 工作區](service-create-distribute-apps.md)中建立內容套件，則即使 Nate 離開群組，Power BI 工作區中的其他人也可以接管擁有權。
   > 
   > 
2. Nate 傳送郵件給通訊群組，告訴他們新內容套件的相關資訊。
3. 「行銷」通訊群組的成員 Jane 在 Power BI Pro 中搜尋並連線到 AppSource 中的內容套件。 Jane 拿到的是唯讀複本。 Jane 知道這是唯讀的，因為在導覽窗格中，儀表板名稱和報表名稱的左邊有共用圖示。 而當 Jane 選取儀表板時，鎖定圖示可讓 Jane 知道他們正在查看內容套件儀表板。 
4. 假設 Jane 決定進行自訂。 Jane 現在擁有自己的報表和儀表板複本。 Jane 的舉動不會影響來源、原始的內容套件或其他通訊群組成員。 他們現在各自使用自己的儀表板和報表複本。
5. Nate 更新了儀表板，並隨時準備發佈新版的內容套件。
   
   * 另一個通訊群組成員 Julio 並未自訂原始的內容套件。 新變更會自動套用至 Julio 的內容套件版本。  
   * Jane 並未自訂內容套件。 然後 Jane 會收到新版本的通知。  Jane 可以前往 AppSource 取得已更新的內容套件，而不會遺失個人化版本。 現在 Jane 有 2 個版本：個人化版本和更新的內容套件。
6. 假設 Nate 變更安全性設定。 Julio 和 Jane 便不再具有內容的存取權。 或是假設他們已從「行銷」通訊群組中移除。
   
   * Julio 並未自訂原始的內容套件，所以該內容就會自動移除。 
   * Jane 並未自訂內容套件。 當下次 Jane 開啟儀表板，原始內容套件中的所有磚都會消失，但從其他報表 (Jane 仍然擁有使用權限的報表) 釘選的磚仍會出現。 不再提供相關聯的報表和資料集 (且不再出現在他們的導覽窗格中)。
7. 或是 Nate 刪除了內容套件。
   
   * Julio 並未自訂原始的內容套件，所以該內容就會自動移除。 
   * Jane 並未自訂內容套件。 下次 Jane 開啟儀表板的話，原始內容套件中的所有磚都會消失，但從其他報表釘選的磚仍會出現。 不再提供相關聯的報表和資料集 (且不再出現在他們的導覽窗格中)。

## <a name="data-security"></a>資料安全性
所有通訊群組成員的資料權限都和內容套件建立者一樣。 唯一的例外狀況是 SQL Server Analysis Services (SSAS) 內部部署表格式資料集。 因為報表及儀表板即時連線至內部部署 SSAS 模型，所以會使用每個個別通訊群組成員認證來判斷他們可以存取的資料。

## <a name="next-steps"></a>後續步驟
* [建立和發佈組織內容套件](service-organizational-content-pack-create-and-publish.md)
* [在 Power BI 中建立和散發應用程式](service-create-distribute-apps.md) 
* [Power BI 服務中的設計工具基本概念](../fundamentals/service-basic-concepts.md)
* 有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)
