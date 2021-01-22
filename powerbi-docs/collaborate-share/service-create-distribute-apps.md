---
title: 使用 Power BI 發佈應用程式
description: 了解如何發佈新的應用程式，亦即儀表板與內建瀏覽功能的報表集合。
author: maggiesMSFT
ms.author: maggies
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 03/23/2020
LocalizationGroup: Share your work
ms.openlocfilehash: 77f206ef59a4aa082e04053d28567480f4d01bb0
ms.sourcegitcommit: 77912d4f6ef2a2b1ef8ffccc50691fe5b38ee97a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/22/2021
ms.locfileid: "98687252"
---
# <a name="publish-an-app-in-power-bi"></a>使用 Power BI 發佈應用程式

在 Power BI 中，您可以建立正式封裝的內容，然後將它以 *應用程式* 的形態散發給廣大群眾。 您可以在 [工作區] 中建立應用程式，且在該處與您的同事在 Power BI 內容上共同作業。 然後，您可以將已完成的應用程式發佈到組織中的大型人員群組。 

![Power BI 應用程式](media/service-create-distribute-apps/power-bi-new-apps.png)

商務使用者通常需要多個 Power BI 儀表板和報表來執行業務。 透過 Power BI 應用程式，您可以建立多組儀表板和報表，然後將這些集合作為應用程式發佈至整個組織、特定人員或群組。 如果您是報表建立者或系統管理員，應用程式可讓您更輕鬆地管理這些集合的權限。

商務使用者取得您應用程式的不同方式：

- 他們可以從 Microsoft AppSource 尋找並安裝您的應用程式。
- 您可以向他們傳送直接連結。
- 如果 Power BI 系統管理員賦予您權限，您可以在您同事的 Power BI 帳戶中自動安裝應用程式。
- 當散發或更新應用程式時，Power BI 不會傳送任何電子郵件給內部使用者。 若將其散發給外部使用者，則這些外部使用者即會收到包含直接連結的電子郵件。 

您可以建立具備內建瀏覽功能的應用程式，讓使用者可以在您內容中輕鬆找到他們的方式。 其無法修改應用程式的內容。 但可以在 Power BI 服務或其中一個行動裝置應用程式中與其互動 - 自行篩選、醒目提示和排序資料。 他們會自動取得更新，而且您可以控制資料重新整理的頻率。 您也可以提供他們建置權限，讓他們連線到底層資料集，並在應用程式中建立報表的複本。 深入了解[建置權限](../connect-data/service-datasets-build-permissions.md)。

## <a name="licenses-for-apps"></a>應用程式的授權
您需要 Power BI Pro 授權才能建立或更新應用程式。 應用程式「取用者」有兩個選項。

* **選項 1** 此應用程式的工作區「非」位於 Power BI Premium 容量中：所有商務使用者都需要 Power BI Pro 授權才能檢視您的應用程式。 
* **選項 2** 此應用程式的工作區「位於」Power BI Premium 容量中：您組織中未具有 Power BI Pro 授權的商務使用者可以檢視應用程式內容。 但是，他們無法複製報表，或根據基礎資料集建立報表。 如需詳細資訊，請參閱[什麼是 Power BI Premium？](../admin/service-premium-what-is.md)。

## <a name="publish-your-app"></a>發佈您的應用程式
當工作區中的儀表板和報表就緒時，您可以選擇想要發佈的儀表板和報表，然後將它們發佈為應用程式。 

1. 在 [工作區] 清單檢視中，決定您想要 **包含在應用程式中** 的儀表板和報表。

    ![選取要發佈的儀表板](media/service-create-distribute-apps/power-bi-apps-incude-dashboard.png)

    如果您選擇不包含相關儀表板的報表，您會在報表旁看到警告。 您仍然可以發佈應用程式，但相關儀表板不會有該報表的磚。

    ![相關儀表板的警告](media/service-create-distribute-apps/power-bi-apps-report-warning.png)

2. 選取右上角的 [發佈應用程式] 按鈕，啟動在工作區中建立和發佈應用程式的程序。
   
    ![發佈應用程式](media/service-create-distribute-apps/power-bi-apps-publish-button.png)

3. 在 [安裝程式] 中，填寫名稱和描述，以利尋找應用程式。 您可以設定個人化的佈景主題色彩。 也可以新增支援網站的連結。
   
    ![建置應用程式](media/service-create-distribute-apps/power-bi-apps-build-your-apps.png)

4. 在 [瀏覽] 中，選取要發佈為應用程式一部分的內容。 然後，新增應用程式瀏覽，按節整理排列內容。 如需詳細資訊，請參閱本文中的[設計應用程式的瀏覽體驗](#design-the-navigation-experience)。
   
    ![應用程式瀏覽](media/service-create-distribute-apps/power-bi-apps-navigation.png)

5. 在 [權限] 上，決定誰可以存取應用程式，以及他們可以用它做什麼。 

    - 在[典型工作區](service-create-workspaces.md)中：您組織中的每個人、特定人員或 Azure Active Directory (Azure AD) 安全性群組。
    - 在[新體驗工作區](service-create-the-new-workspaces.md)中：特定人員、Azure AD 安全性群組和通訊群組清單，以及 Microsoft 365 群組。 系統會自動為所有工作區使用者授與對工作區應用程式的存取權。
    - 您可以透過授與建置權限，讓應用程式使用者連線到應用程式的基礎資料集。 他們會在搜尋共用資料集時看到這些資料集。 在本文中深入了解[允許使用者連線到應用程式的資料集](#allow-users-to-connect-to-datasets)。
    - 具備建置權限的使用者也可以擁有從此應用程式將報表複製到另一個工作區的權限。 在本文中深入了解[允許使用者複製應用程式中的報表](#allow-users-to-copy-reports)。
    
    >[!IMPORTANT]
    >若您的應用程式仰賴來自其他工作區的資料集，您必須負責確保所有應用程式使用者都能存取底層資料集。
    >如果應用程式或報表與資料集位於相同的工作區，請確定您也將與資料集建立關聯的報表新增至應用程式。

6. 如果您的 Power BI 管理員已在 Power BI 管理入口網站中為您啟用此設定，您就可以為收件者自動安裝應用程式。 深入了解本文中的[自動安裝應用程式](#automatically-install-apps-for-end-users)。

    ![應用程式權限](media/service-create-distribute-apps/power-bi-apps-permissions.png)

7. 當選取 [發佈應用程式] 時，會看到確認其已準備好要發佈的訊息。 在 [共用此應用程式] 對話方塊中，您可複製此應用程式其直接連結的 URL。
   
    ![應用程式完成](media/service-create-distribute-apps/power-bi-apps-success.png)

您可將該直接連結傳送給已共用的對象，也可以前往 [Download and explore more apps from AppSource] \(從 AppSource 下載和探索更多應用程式\)，在 [應用程式] 索引標籤中找到應用程式。 深入了解[商務使用者的應用程式體驗](../consumer/end-user-apps.md)。

## <a name="change-your-published-app"></a>變更已發佈的應用程式
在您發佈應用程式之後，可能想要進行變更或更新。 如果您是系統管理員或新工作區成員，就可以輕鬆更新。 

1. 開啟對應至應用程式的工作區。 
   
    ![開啟工作區](media/service-create-distribute-apps/power-bi-apps-open-workspace.png)

2. 對儀表板或報表執行您想要的任何變更。
 
    工作區是暫存區域；因此，您的變更在重新發佈之前不會在應用程式中生效。 這可讓您進行變更，而不影響已發佈的應用程式。  
 
    > [!IMPORTANT]
    > 如果您移除報表並更新應用程式，即使您將報表新增回應用程式，您的應用程式取用者仍會遺失所有自訂項目，例如書籤、註解等。  
 
3. 回到內容的工作區清單，然後選取右上角的 [更新應用程式]。
   
1. 更新 [安裝程式]、[瀏覽] 和 [權限] (如有需要)，然後選取 [更新應用程式]。
   
您已對其發佈應用程式的人員會自動看到應用程式更新版本。 

## <a name="design-the-navigation-experience"></a>設計導覽體驗
[新瀏覽產生器] 選項可讓您建置應用程式的自訂瀏覽。 自訂瀏覽可讓使用者更容易尋找及使用應用程式中內容。 現有的應用程式已關閉此選項，而新的應用程式預設開啟此選項。

當此選項關閉時，您可以選取 [應用程式登陸頁面] 為 [特定內容] (例如儀表板或報表)，或選取 [無]，向使用者顯示內容的基本清單。

當您開啟 [新瀏覽產生器] 時，您可以設計自訂的瀏覽。 根據預設，您在應用程式中包含的所有報表、儀表板和 Excel 活頁簿都會列為一般清單。 

![應用程式瀏覽](media/service-create-distribute-apps/power-bi-apps-navigation.png)

您可以進一步自訂應用程式瀏覽，藉由：

* 使用向上/向下鍵重新排列項目。 
* 重新命名 [報告詳細資料]、[儀表板詳細資料] 和 [活頁簿詳細資料] 中的項目。
* 隱藏瀏覽中的特定項目。
* 使用 [新增] 選項將 **各節** 新增至群組相關內容。
* 使用 [新增] 選項將「連結」新增至導覽窗格的外部資源。 

當您新增 **連結** 時，您可在 [連結詳細資料] 中選擇在何處開啟該連結。 根據預設，連結會在 [目前索引標籤] 中開啟，但您可以選取 [新索引標籤] 或 [內容區域]。 

### <a name="considerations-for-using-the-new-navigation-builder-option"></a>使用 [新瀏覽產生器] 選項的考量
使用 [新瀏覽產生器] 時，請牢記以下一般事項：

* 報表頁面會在應用程式瀏覽區域中顯示為可展開的區段。 當報表有一張可見頁面時，就只會顯示報表名稱。 按一下導覽中的報表名稱，就會開啟報表的第一頁。 

    > [!NOTE]
    > 報表可能只有一張可見頁面，因為您已使用按鈕或鑽研動作來設定瀏覽其餘頁面。

* 如果關閉新的瀏覽產生器，然後發佈或更新應用程式，則會遺失已建立的自訂內容。 例如，瀏覽項目的區段、排序、連結和自訂名稱全都會遺失。
* 有不使用應用程式產生器的選項可用。

當您將連結新增至應用程式瀏覽並選取 [內容區域] 選項時：
* 請確定連結可內嵌。 某些服務會在第三方網站中封鎖內嵌其內容，例如 Power BI。
* 在不支援的其他工作區中內嵌 Power BI 服務內容，例如報表或儀表板。 
* 從內部部署的部署，透過其原生內嵌 URL 內容內嵌 Power BI 報表伺服器內容。 使用[建立 Power BI 報表伺服器 URL](../report-server/quickstart-embed.md#create-the-power-bi-report-url) 中的這些步驟取得 URL。 請注意，因為適用一般驗證規則，所以檢視內容需要 VPN 連線到內部部署伺服器。 
* 在內嵌內容的頂端會顯示安全性警告，表示此非 Power BI 的內容。

## <a name="automatically-install-apps-for-end-users"></a>自動為終端使用者安裝應用程式
如果管理員授與您權限，您可以自動安裝應用程式，將它們「推播」給終端使用者。 這項推播功能，可讓您更容易向適當的人員或群組散發正確應用程式。 應用程式會自動出現在您終端使用者的應用程式內容清單中。 他們不必從 Microsoft AppSource 中尋找，或追蹤安裝連結。 請參閱 Power BI 管理入口網站文章，了解管理員如何[向終端使用者推播應用程式](../admin/service-admin-portal.md#push-apps-to-end-users)。

### <a name="how-to-push-an-app-automatically-to-end-users"></a>如何向使用者自動推播應用程式
系統管理員為您指派權限之後，您有新的選項用來 **自動安裝應用程式**。 當您核取此方塊並選取 [發佈應用程式] (或 [更新應用程式]) 後，就會將應用程式推播至在 [存取] 索引標籤之應用程式 [權限] 區段中定義的所有使用者或羣組。

![顯示 Power BI [發佈應用程式] 選項的螢幕擷取畫面，其中已選取 [自動安裝應用程式]。](media/service-create-distribute-apps//power-bi-apps-access.png)

### <a name="how-users-get-the-apps-that-you-push-to-them"></a>使用者如何取得您推播給他們的應用程式
應用程式推播後，就會自動出現在他們的 [應用程式] 清單中。 以此方式，您就可以讓組織中特定使用者或工作角色輕鬆取得他們需要的應用程式。

![顯示 Power BI [應用程式] 的螢幕擷取畫面，其中包含您已發佈的應用程式。](media/service-create-distribute-apps/power-bi-apps-left-nav.png)

### <a name="considerations-for-automatically-installing-apps"></a>自動安裝應用程式的考量
推送應用程式給終端使用者時，請記住下列事項：

* 自動為使用者安裝應用程式可能需要時間。 大部分的應用程式會立即為使用者安裝，但推播應用程式可能要花點時間。  這取決於應用程式中的項目數及有權存取的人數。 建議在使用者需要之前，於時間充足的下班時間推送應用程式。 與幾位使用者確認，再廣泛宣傳應用程式可供使用。

* 重新整理瀏覽器。 使用者可能需要重新整理，或關閉並重新開啟其瀏覽器，才能在 [應用程式] 清單中看到推送的應用程式。

* 如果使用者在 [應用程式] 清單中不能立即看到應用程式，則應該重新整理或關閉後重新開啟瀏覽器。

* 盡量不要造成使用者太多負擔。 請小心不要推送太多應用程式，這樣使用者才能認定預先安裝的應用程式對他們有用。 為調配時間，最好能控制誰可以將應用程式推送給終端使用者。 建立連絡點，將組織中的應用程式推播給使用者。

* 不會為未接受邀請的來賓使用者自動安裝應用程式。  

## <a name="allow-users-to-connect-to-datasets"></a>允許使用者連線到資料集

當您選取 [允許使用者連線到應用程式的基礎資料集] 時，您會提供應用程式使用者在那些資料集上的「建置權限」。 使用此權限，他們可以執行數種關鍵動作：

- [使用應用程式資料集](../connect-data/service-datasets-across-workspaces.md)作為他們報表的基礎。
- 在 Power BI Desktop 中以及 Power BI 服務內的 get-data 體驗中搜尋這些資料集。
- 以這些資料集為基礎建立報表和儀表板。

當您清除此選項時，您新增到應用程式的新使用者便不會取得建置權限。 但是，針對現有的應用程式使用者，基礎資料集上的權限不會變更。 您可以從不應繼續擁有該權限的應用程式使用者中手動移除建置權限。 深入了解[建置權限](../connect-data/service-datasets-build-permissions.md)。

## <a name="allow-users-to-copy-reports"></a>允許使用者複製報表

當您選取選項來 [允許使用者複製此應用程式中的報表] 時，使用者便可以將應用程式中任何報表儲存到他們的「我的工作區」或另一個工作區。 若要進行複製，使用者將需要 Pro 授權，即使原始報表位於 Premium 容量中的工作區也一樣。 他們接著可以根據其獨特需求自訂報表。 您必須先選取 [允許所有使用者使用組建權限來連線至應用程式的基礎資料集] 選項。 透過選取這些選項，您便可以啟用新的[從其他工作區複製報表](../connect-data/service-datasets-copy-reports.md)功能。

## <a name="unpublish-an-app"></a>解除發佈應用程式
工作區的任何成員都可以解除發佈應用程式。

>[!IMPORTANT]
>當您解除發佈應用程式時，應用程式使用者會失去其自訂項目。 他們會遺失所有與應用程式內容建立關聯的個人書籤、註解或訂閱。 只有在您需要移除應用程式時，才解除發佈該應用程式。
> 

* 在工作區中，選取右上角的省略符號 ( **...** ) > [解除發佈應用程式]。
  
    ![解除發佈應用程式](media/service-create-distribute-apps/power-bi-app-unpublish.png)

這個動作會解除安裝您發佈給每個人的應用程式，而且他們將無法再存取該應用程式。 它不會刪除工作區或其內容。

## <a name="view-your-published-app"></a>檢視已發佈的應用程式

當您的應用程式取用者開啟應用程式時，他們會看到您建立的導覽窗格，而不是標準的 Power BI 導覽窗格。 應用程式瀏覽會列出已定義區段中的報表和儀表板。 它也會列出每份報表的個別頁面，而不僅是報表名稱。 您可使用功能表列中的箭號來展開和摺疊左側導覽。

![具有瀏覽的應用程式](media/service-create-distribute-apps/power-bi-new-apps-navigation.png)

在全螢幕模式中，您可選取角落的選項來顯示或隱藏導覽。

![全螢幕導覽](media/service-create-distribute-apps/full-screen-app-show-navigation.png)

## <a name="considerations-and-limitations"></a>考量與限制
發佈應用程式時的重要事項：

* 權限頁面不會變更其他工作區的資料集權限。 您會看到一則警告，提醒您單獨授與這些資料集的存取權。 最佳做法是先連絡資料集擁有者，再開始建置應用程式，以確保應用程式的所有使用者都能存取這些資料集。 
* 在應用程式的存取清單中，您最多可以有 100 個使用者或群組。 不過，您可以讓超過 100 個使用者存取該應用程式。 若要這麼做，請使用一或多個包含所有所需使用者的使用者群組。
* 針對新的工作區體驗，如果新增至應用程式存取清單的使用者已經可以透過工作區存取應用程式，他們就不會顯示在應用程式的存取清單中。  
* [支援網站 URL] 會顯示在 [專案資訊卡] 中。
* 應用程式可選擇是否允許使用者使用共用權限來共用應用程式及應用程式的基礎資料集。 根據預設，新應用程式會關閉此選項。 建議關閉現有應用程式的這個選項，並更新基礎資料集的權限。 現有的應用程式之所以啟用此選項，是因為應用程式一開始即是設計來取代具有此行為的內容套件。
* 應用程式最多可以有 200 個儀表板。 

## <a name="next-steps"></a>後續步驟
* [建立工作區](service-create-workspaces.md)
* [在 Power BI 中安裝和使用應用程式](../consumer/end-user-apps.md)
* [外部服務的 Power BI 應用程式](../connect-data/service-connect-to-services.md)
* [Power BI 管理入口網站](../admin/service-admin-portal.md)
* 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
