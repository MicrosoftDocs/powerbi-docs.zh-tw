---
title: 在 Power BI 中建立範本應用程式
description: 如何在 Power BI 中建立可以散發給所有 Power BI 客戶的範本應用程式。
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: how-to
ms.date: 09/15/2020
ms.openlocfilehash: fc62d291b890d840b89997cd5d5253572f91bf3e
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410221"
---
# <a name="create-a-template-app-in-power-bi"></a>在 Power BI 中建立範本應用程式

Power BI「範本應用程式」讓 Power BI 合作夥伴撰寫少量程式碼或不用撰寫程式碼即可建置 Power BI 應用程式，並將應用程式部署至所有 Power BI 客戶。  本文包含建立 Power BI 範本應用程式的逐步指示。

如果您可建立 Power BI 報表及儀表板，即可成為「範本應用程式建置者」，且將分析內容建置並封裝在「應用程式」中。 您可以透過任何可用的平台 (例如 AppSource)，或在自己的 Web 服務中使用應用程式，將應用程式部署至其他 Power BI 租用戶。 身為建置者，您可以建立受保護的分析套件以供散發。

Power BI 管理員可管理並控制其組織中可建立及安裝範本應用程式的人員。 獲授權使用者可以安裝您的範本應用程式，加以修改並散發給其組織中的 Power BI 使用者。

## <a name="prerequisites"></a>必要條件

以下為建立範本應用程式的需求：  

- [Power BI Pro 授權](../fundamentals/service-self-service-signup-for-power-bi.md)
- [安裝 Power BI Desktop](../fundamentals/desktop-get-the-desktop.md) (選用)
- 熟悉 [Power BI 的基本概念](../fundamentals/service-basic-concepts.md)
- 公開共用範本應用程式的權限 (如需詳細資訊，請參閱 Power BI [管理入口網站、範本應用程式設定](../admin/service-admin-portal.md#template-apps-settings))

## <a name="create-the-template-workspace"></a>建立範本工作區

若要建立可以散發給其他 Power BI 租用戶的範本應用程式，您需要在其中一個新的工作區中建立範本應用程式。

1. 在 Power BI 服務中，選取 [工作區] > [建立工作區]。

    ![建立工作區](media/service-template-apps-create/power-bi-new-workspace.png)

2. 在 [建立工作區] 中，輸入工作區的名稱、描述 (選擇性) 及標誌影像 (選擇性)。

    ![試用新的工作區](media/service-template-apps-create/power-bi-upgrade-new.png)

4. 展開 [進階] 區段，然後選取 [開發範本應用程式]。

    ![開發範本應用程式](media/service-template-apps-create/power-bi-template-app-develop.png)

5. 選取 [儲存]。
>[!NOTE]
>您需要獲得 Power BI 系統管理員的權限，才能升階範本應用程式。

## <a name="add-content-to-the-template-app-workspace"></a>將內容新增至範本應用程式工作區

如同一般的 Power BI 工作區，下一個步驟是將內容新增至工作區。  

- 在工作區中[建立您的 Power BI 內容](index.yml)。

如果正在使用 Power Query 中的參數，請確認這些參數具有正確定義的類型 (例如文字類型)。 不支援 Any 及 Binary 類型。

[在 Power BI 中撰寫範本應用程式的提示](service-template-apps-tips.md)有建議，您可在建立範本應用程式的報表及儀表板時加以考慮。

## <a name="define-the-properties-of-the-template-app"></a>定義範本應用程式的屬性

既然您的工作區中已有內容，就可開始將它封裝進範本應用程式了。 第一步為建立測試範本應用程式，您只能從您租用戶上的組織內存取。

1. 在範本應用程式工作區中，選取 [建立應用程式]。

    ![建立應用程式](media/service-template-apps-create/power-bi-create-app.png)

    您可在這裡填入範本應用程式的其他建置選項，包含六個索引標籤：

    **商標**

    ![商標](media/service-template-apps-create/power-bi-create-branding.png)
    - 應用程式名稱
    - 描述
    - 支援網站 (將範本應用程式重新散發為組織的應用程式之後，連結會顯示在應用程式資訊下方)
    - 應用程式標誌 (45K 檔案大小限制、1:1 外觀比例、.png .jpg .jpeg 格式)
    - 應用程式佈景主題色彩

    **導覽**

    啟動 [新的瀏覽產生器]，您可在其中定義應用程式的導覽窗格 (請參閱本文中的[設計瀏覽體驗](../collaborate-share/service-create-distribute-apps.md#design-the-navigation-experience)以取得詳細資料)。

   ![設定應用程式登陸頁面](media/service-template-apps-create/power-bi-install-app-content.png)
    
    **應用程式登陸頁面：** 如果您決定退出瀏覽產生器，則可選擇選取應用程式登陸頁面。 定義要作為應用程式登陸頁面的報表或儀表板。 使用可提供正確印象的登陸頁面。

    **控制**

    設定應用程式使用者在應用程式內容使用上的一些限制。 您可以使用這項控制來保護應用程式中的智慧財產權。

    ![控制](media/service-template-apps-create/power-bi-create-control.png)

    >[!NOTE]
    >針對安裝應用程式的使用者，一律封鎖匯出至 .pbix 格式的功能。

    **參數**

    參數會在原始 .pbix 檔案中建立 (參閱[建立查詢參數](https://powerbi.microsoft.com/blog/deep-dive-into-query-parameters-and-power-bi-templates/) (英文) 以深入了解)。 您可使用此索引標籤上的功能，在應用程式安裝程式連線到其資料時，協助進行設定。

    您也可以在此索引標籤中提供應用程式文件的連結。

    ![參數](media/service-template-apps-create/power-bi-create-parameters.png)

    每個參數都有來自查詢，以及值欄位的名稱和描述。 在安裝期間，您有三種方式可取得參數的值。

    * 您可要求安裝程式輸入值。 在此情況下，您需要提供範例加以取代。 若要以這種方式設定參數，請核取 [必要] 核取方塊，然後在文字方塊中提供範例，其告知使用者所需值的種類。 例如：

       ![使用者需提供參數值的螢幕擷取畫面。](media/service-template-apps-create/power-bi-create-parameters-require-user.png)

    * 您可提供預先填入的值，讓安裝應用程式的使用者無法加以變更。 安裝應用程式的人員無法看見以這種方式所設定參數。 只有在確定預先填入的值適用於所有使用者時，才建議使用這個方法；否則，請使用前述需要使用者輸入的第一個方法。

       若要以這種方式設定參數，請在 [值] 文字方塊中輸入值，然後按一下鎖定圖示。 如此一來即無法變更該值。 例如：

       ![絕對參數值的螢幕擷取畫面。](media/service-template-apps-create/power-bi-create-parameters-absolute.png)

    * 您可提供使用者在安裝期間可以變更的預設值。 若要以這種方式設定參數，請在 [值] 文字方塊中輸入想要的預設值，且不選取鎖定圖示。 例如：

      ![可變更預設參數值的螢幕擷取畫面。](media/service-template-apps-create/power-bi-create-parameters-default.png)

    **驗證**
    
    在此索引標籤中，您可選取要使用的驗證方法。 可用選項取決於所使用的資料來源類型。

    ![選擇驗證方法的螢幕擷取畫面。](media/service-template-apps-create/power-bi-create-authentication.png)

    隱私權等級會自動設定：
   * 單一資料來源：自動設定為私人。
   * 多個匿名資料來源：自動設定為公用。

    **存取**
    
    在測試階段中，決定組織內哪些其他人員可安裝並測試應用程式。 放心，您之後隨時可以回來變更這些設定。 此設定不會影響分散式範本應用程式的存取。

    ![[存取] 索引標籤的螢幕擷取畫面。](media/service-template-apps-create/power-bi-create-access.png)

2. 選取 [建立應用程式]  。

    您會看到測試應用程式已就緒的訊息，還有供您複製並分享給應用程式測試者的連結。

    ![測試應用程式已就緒](media/service-template-apps-create/power-bi-template-app-test-ready.png)

    您也已經完成發行管理程序的第一步，將於以下說明該程序。

## <a name="manage-the-template-app-release"></a>管理範本應用程式發行

在公開發行這個範本應用程式前，建議您確認其已準備就緒。 Power BI 已建立 [發行管理] 窗格，供您遵循並檢查完整的應用程式發行路徑。 您也可以觸發階段之間的轉換。 常見的階段有：

- 產生測試應用程式：僅供組織內的測試使用。
- 將測試套件升至生產階段前：在您的組織外測試。
- 將生產階段前套件升至生產階段：生產階段版本。
- 刪除所有套件，或從先前的階段重新開始。

當您在發行階段之間移動時，URL 不會變更。 升階不會影響 URL 本身。

讓我們逐步了解各階段：

1. 在範本工作區中，選取 [發行管理]。

    ![發行管理圖示](media/service-template-apps-create/power-bi-release-management-icon.png)

2. 若已在上述＜定義範本應用程式的屬性＞一節中建立測試應用程式，請選取 [取得連結] ([測試] 旁邊的黃點即會隨即填滿)。

    如果尚未建立應用程式，請選取 [建立應用程式]。 這會回到範本應用程式的建立流程。

    ![建立應用程式、取得連結](media/service-template-apps-create/power-bi-dev-template-create-app-get-link.png)

4. 若要測試應用程式安裝體驗，請複製通知視窗中的連結，並貼到新的瀏覽器視窗。

    從這裡開始，您遵循的程序與客戶要遵循的程序相同。 請參閱[在組織中安裝並散發範本應用程式](service-template-apps-install-distribute.md)。

5. 在對話方塊中，選取 [安裝]。

    安裝成功後，您會看到新應用程式已就緒的通知。

6. 選取 [移至應用程式]。
7. 在 [開始使用新的應用程式] 中，您會看到與客戶所見相同的應用程式。

    ![開始使用新的應用程式](media/service-template-apps-create/power-bi-template-app-get-started.png)
8. 選取 [探索應用程式] 來以範例資料驗證測試應用程式。
9. 若要進行任何變更，請返回原始工作區中的應用程式。 並將測試應用程式更新到您滿意為止。
10. 當您準備好要將應用程式升階至生產階段前，以進一步在租用戶外部測試時，請返回 [發行管理] 窗格，並選取 [升階應用程式]。

    ![將應用程式升至生產階段前](media/service-template-apps-create/power-bi-template-app-promote.png)
    >[!NOTE]
    > 當應用程式升階時即可在組織外部公開取得。

    如果您未看到該選項，請連絡 Power BI 系統管理員，要求其授與您管理入口網站中的[範本應用程式開發權限](../admin/service-admin-portal.md#template-apps-settings)。
11. 選取 [升階] 來確認您的選擇。
12. 複製這個新的 URL 來分享至租用戶外部，以進行測試。 此連結也是您在建立[新的合作夥伴中心供應項目](/azure/marketplace/partner-center-portal/create-power-bi-app-offer)時所提交，用以開始在 AppSource 上散發您應用程式之程序的 URL。 您只需要將生產前的連結提交給合作夥伴中心。 只有在應用程式通過核准，您也收到其在 AppSource 中發佈的通知之後，您才可以將此套件升階到 Power BI 中的生產環境。
13. 當您的應用程式已準備好進入生產階段或透過 AppSource 分享時，請返回 [發行管理] 窗格，並選取 [生產階段前] 旁邊的 [升階應用程式]。
14. 選取 [升階] 來確認您的選擇。

    現在您的應用程式已經進入生產階段，並準備好散發。

    ![應用程式進入生產階段](media/service-template-apps-create/power-bi-template-app-production.png)

若要讓全球上千位 Power BI 使用者都能使用您的應用程式，建議您將應用程式提交至 AppSource。 如需詳細資料，請參閱 [Power BI 應用程式供應項目](/azure/marketplace/partner-center-portal/create-power-bi-app-offer)。

## <a name="next-steps"></a>後續步驟

請參閱[在您的組織中安裝、自訂及散發範本應用程式](service-template-apps-install-distribute.md)，了解客戶如何與範本應用程式互動。

如需散發應用程式的詳細資料，請參閱 [Power BI 應用程式供應項目](/azure/marketplace/partner-center-portal/create-power-bi-app-offer)。