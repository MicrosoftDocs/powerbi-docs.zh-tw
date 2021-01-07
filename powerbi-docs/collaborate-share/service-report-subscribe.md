---
title: 為您自己和其他人訂閱報表和儀表板
description: 了解如何為您自己和其他人訂閱 Power BI 報表頁面、儀表板或編頁報表的快照集。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 12/18/2020
LocalizationGroup: Common tasks
ms.openlocfilehash: 4a8234176dd44fd265ff2d4a6af8e1b5568a642c
ms.sourcegitcommit: b8e4dd67c59db079fdfa82a8a01c2a28fd1673ca
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2020
ms.locfileid: "97699258"
---
# <a name="subscribe-yourself-and-others-to-reports-and-dashboards-in-the-power-bi-service"></a>為您自己和其他人訂閱 Power BI 服務中的報表和儀表板

您可以為自己和同事訂閱對您來說最重要的報表頁面、儀表板和編頁報表。 Power BI 電子郵件訂閱可供：

- 決定收到電子郵件的頻率︰每天、每週、每小時、每月，或在初始資料重新整理後一天一次。
- 選擇 [每日]、[每週]、[每小時] 或 [每月] 時，選擇要接收電子郵件的時間。
- 為每個 Power BI 報表或儀表板設定 24 個不同的訂閱。  您可為編頁報表設定的訂閱數目沒有上限。
- 使用此服務傳送附有報表影像及報表連結的郵件。  在安裝 Power BI 應用程式的行動裝置上，選取此連結會啟動 Power BI 應用程式 (而不是在 Power BI 網站上開啟報表或儀表板)。
- 包含完整報表的附件。
- 如果 Power BI 內容託管於 Premium 容量中，請將電子郵件傳送給租使用者外部的使用者。  系統管理員可以利用 Power BI 系統管理中心內現有的外部共用控制設定，控制可傳送電子郵件訂閱給外部使用者的人員存取權。

![儀表板的電子郵件快照集](media/service-report-subscribe/power-bi-subscriptions-email.png)

## <a name="requirements"></a>需求

可以 **建立** 訂用帳戶的人：

- 具有 Power BI Pro 授權的使用者
- 在 Premium 工作區或應用程式中檢視內容的使用者也可以訂閱位於該處的內容，甚至不需要 Power BI Pro 授權。

您不需要內容 (儀表板或報表) 的編輯權限，即可為您自己建立訂用帳戶，但您必須擁有編輯權限，才能為其他人建立訂用帳戶。

## <a name="subscribe-to-a-dashboard-report-page-or-paginated-report"></a>訂閱儀表板、報表頁面或編頁報表

不論您是要訂閱儀表板、報表或編頁報表，程序都很相似。 同樣的按鈕可讓您訂閱 Power BI 服務的儀表板與報表。

訂閱編頁報表則略有不同。 如需詳細資訊，請參閱[為您自己和其他人訂閱 Power BI 服務中的編頁報表](../consumer/paginated-reports-subscriptions.md)。

![選取訂閱圖示](media/service-report-subscribe/power-bi-subscribe-orientation.png).

1. 開啟儀表板或報表。
2. 從頂端功能表列，選取 [訂閱] 或選取信封圖示 :::image type="icon" source="media/service-report-subscribe/power-bi-icon-envelope.png" border="false":::。

    ![訂閱圖示](media/service-report-subscribe/power-bi-subscribe-icon.png)

1. 使用黃色的滑桿開啟和關閉訂閱。 將滑桿設定為 [關閉] 不會刪除訂閱。 若要刪除訂閱，請選取垃圾桶圖示。

2. 您的電子郵件地址已位於 [訂閱] 方塊中。 您可在訂閱中新增其他電子郵件地址，但僅限於同一個網域。 若報表或儀表板託管於 [Premium 容量](../admin/service-premium-what-is.md)中，您就可以使用個人電子郵件地址與群組別名訂閱，無論其是否位在網域中。 若報表或儀表板不是託管於 Premium 容量中，則您可使用其他人的名義來訂閱，但這些人也必須具有 Power BI Pro 授權。 如需詳細資料，請參閱下方的[考量與疑難排解](#considerations-and-troubleshooting)。

3. 填寫電子郵件 [主旨] 和 [訊息] 詳細資料。

4. 為訂閱選取 [頻率]：[每天]、[每小時]、[每週]、[每月] 或 [資料重新整理後 (每天)]。 若只在特定日子接收訂閱電子郵件，請選取 [每小時] 或 [每週]，然後選取想要接收電子郵件的日子。 例如，如果您只想在工作日收到訂閱電子郵件，請選取 [每週]，然後清除 [週六] 和 [週日] 的方塊。 如果您選取 [每月]，請輸入想要在每月的幾號或哪幾號收到訂閱電子郵件。

5. 如果您選擇 [每天]、[每小時]、[每月] 或 [每週]，也可以為訂閱選擇 [排程的時間]。 您將於每小時整點，或在 15、30 或 45 分時加以執行。 請選取上午 (AM) 或下午/晚上 (PM)。 您也可以指定時區。 如果您選擇 [每小時]，請選取想要開始訂閱的 [排程時間]，系統即會在該時間之後每小時執行。

6. 根據預設，訂用帳戶開始日期是您建立訂用帳的日期。 您可以選擇選取結束日期。 如果您未設定結束日期，則結束日期自動設為開始日期的一年後。 您可以在訂用帳戶結束之前，隨時將它變更為未來的任何日期 (最多至 9999 年)。 當訂用帳戶達到結束日期時，即會停止直到您重新啟用為止。 在排程結束日期之前，您會收到通知，詢問您是否要加以延長。

    在下方的螢幕擷取畫面中，您可以注意到當您在訂閱報表時，實際上是在訂閱報表「頁面」。 若要訂閱報表中的多個頁面，您可以選取 [完整報表附件] 或選取 [新增另一個訂用帳戶] 來設定新的訂用帳戶。

    ![訂閱窗格](media/service-report-subscribe/power-bi-email.png)

1. (選擇性) 選取是否包含返回 Power BI 內容的連結，以及是否要讓使用者存取您以其名義訂閱的內容。  如果選擇包含連結，為獲得最佳體驗，請確定所有使用者都可以存取報表。

1. (選擇性) 選取是否要將「完整報表」新增為附件，而非僅新增單一報表頁面。 選擇 [PDF] 或 [PowerPoint]。 附件的大小限制為不超過 20 頁且小於 25 MB。 附件會遵守報表的所有隱私權標籤。

1. 選取 [儲存後關閉]。 針對您所選取的頻率和時間，這些訂用帳戶會收到儀表板或報表頁面的電子郵件和快照集。 總之，您可以針對每個報表或儀表板建立最多 24 個訂用帳戶，而且可以為每個訂用帳戶提供唯一的收件者、時間和頻率。 所有設定為 [在資料重新整理後] 的儀表板或報表訂閱，在第一次排程重新整理之後仍只會傳送一封電子郵件。

    > [!NOTE]
    > 如果您在儲存和關閉後編輯訂閱，則不論先前選項為何，都會為使用者提供存取您訂閱內容的選項。
    >



    > [!TIP]
    > 想要立即/隨時從訂用帳戶傳送電子郵件嗎？ 請為想傳送的儀表板或報表訂閱選取 [立即執行]。 您會看到通知顯示電子郵件正在傳送至屬於該特定訂用帳戶的所有人。 執行此動作不會計入您每天每報表或儀表板的 24 個排程訂閱執行限制。 這不會觸發基礎資料集的資料重新整理。
    >

## <a name="manage-your-subscriptions"></a>管理您的訂閱

只有建立訂閱的使用者能夠進行管理。 有兩條路徑可到達管理您訂用帳戶的畫面。 首先，請選取 [訂閱電子郵件] 對話方塊中的 [管理所有訂閱] (請參閱以上的步驟 4)。 接下來，請從頂端功能表列選取 Power BI 齒輪圖示 ![齒輪圖示](media/service-report-subscribe/power-bi-settings-icon.png)，然後選擇 [設定]。

![選取 [設定]](media/service-report-subscribe/power-bi-subscribe-settings.png)

顯示的訂閱會因目前作用中工作區而異。 若要一次查看所有工作區的全部訂閱，[我的工作區] 必須為作用中。 如需了解工作區，請參閱 [Power BI 中的工作區](service-create-workspaces.md)。

![查看 [我的工作區] 中的所有訂閱](media/service-report-subscribe/power-bi-subscriptions.png)

訂閱會因下列任一狀況而結束：

- Pro 授權到期。
- 擁有者刪除儀表板或報表。
- 用來建立訂閱的使用者帳戶遭刪除。

Power BI 系統管理員可使用 Power BI 的稽核記錄來檢視訂閱詳細資料。 這些詳細資料包括：

- 建立者
- 建立日期
- 訂閱的內容
- 收件者
- 頻率
- 修改者
- 修改日期

## <a name="considerations-and-troubleshooting"></a>考量與疑難排解

### <a name="general"></a>一般

- 如同其他 BI 產品，您為訂閱所設定時間就是訂閱開始處理的時間。  當報表處理完成時，訂閱會排入佇列並傳送給電子郵件收件者。  我們致力於盡快處理和傳遞所有的訂閱。 但是，有時候在尖峰需求時，由於 Power BI 一次能傳送的訂閱數量有限，因此您可能會察覺到較長的延遲。 針對處理和傳送報表，大多數客戶都不會遇到延遲超過 15 分鐘的情況。 但針對特定時間和使用量龐大的租用戶，延遲最長可達 30 分鐘。  我們從不預期在排程訂閱之後，於傳遞上的延遲超過 60 分鐘。  若您遇到長時間的延遲，請先確認 `no-reply-powerbi@microsoft.com` 地址位於您的安全寄件者清單中，而且未遭到電子郵件提供者封鎖。  如果電子郵件並未遭到封鎖，請連絡 Power BI 支援人員尋求協助。
- 目前，訂閱自己以外的使用者時，除編頁報表外，不支援使用即時連線資料集的報表和儀表板電子郵件訂閱。 您可使用自己的安全性內容來為其他人訂閱編頁報表。 深入了解[訂閱編頁報表](../consumer/paginated-reports-subscriptions.md)。
- 如果超過兩個月未瀏覽某些儀表板和報表，Power BI 會自動暫停重新整理與這些儀表板和報表建立關聯的資料集。 不過，如果您新增儀表板或報表的訂閱，即使有段時間未瀏覽也不會暫停。
- 如果未收到訂閱電子郵件：

    - 請確定使用者主體名稱 (UPN) 可接收電子郵件。
    - 雖然您有 Power BI Pro 授權，但可能沒有 Microsoft Exchange 授權。 如果沒有 Microsoft Exchange 授權，則 Azure Active Directory 帳戶可能沒有指定電子郵件或備用電子郵件地址。 在此情況下，雖然訂閱似乎已送出，但您永遠不會收到複本。  如果 Power BI 系統管理員指派電子郵件地址，則 Power BI 會在您下次登入時同步更新，並將該電子郵件地址用於訂閱。

- 若您的儀表板或報表處於 Premium 容量中，您可以使用群組電子郵件別名進行訂閱，而不必為各同事的電子郵件一一訂閱。 別名會以目前使用中的目錄為準。
- 若內容不在 Premium 容量中，則只有 Power BI Pro 使用者會收到電子郵件訂閱。
- 訂閱目前不支援書籤。
- 當您編輯現有的訂閱時，一律會顯示啟用提供報表/儀表板存取權的選項。  如果您清除此選項並儲存訂閱，即會儲存該狀態。 不過，當您重新編輯報表時，預設又會勾選此選項。
- 如果有備用電子郵件地址，但沒有主要電子郵件地址，Power BI 會使用備用電子郵件地址來傳遞訂閱。
- 如果您為外部使用者訂閱報表或儀表板，則當您選取訂用帳戶窗格中的 [儲存後關閉] 之後，外部使用者將會立即收到共用通知。 此通知只會傳送給外部使用者，而不會傳送給內部使用者，因外部使用者需要邀請連結才能檢視報表或儀表板。 

### <a name="dashboards"></a>儀表板

- 傳送給使用者的訂閱電子郵件中，釘選磚超過 25 個，或是有 4 個以上釘選即時報表頁面的儀表板可能不會完整呈現。 訂閱超過這些磚數目的儀表板不會遭到封鎖。 不過，如果您遇到問題，則會視為不受支援。 請考慮據此修改使其落在支援的範圍內。
- 在少數情況下，可能需要超過 15 分鐘的時間，收件者才會收到電子郵件訂閱。 如果發生這種情況，建議您在不同時間執行資料重新整理和電子郵件訂閱，以確保準時傳遞。 若問題持續發生，請連絡 Power BI 支援人員。
- 針對儀表板電子郵件訂閱，如果有任何磚套用資料列層級安全性 (RLS)，則不會顯示這些磚。
- 針對儀表板訂閱，尚不支援某些磚類型。 其中包括：串流資料磚、影片磚及自訂的 Web 內容磚。
- 如與租用戶外部的同事共用儀表板，「除非」此儀表板位在 Premium 工作區或應用程式中，否則無法也為該位同事建立訂閱。 因此，如果您是 `aaron@contoso.com`，則可與 `anyone@fabrikam.com` 共用，但尚無法為 `anyone@fabrikam.com` 訂閱，而他們也無法訂閱共用的內容。

### <a name="reports"></a>報表

- 針對報表電子郵件訂閱，如果資料集使用 RLS，您可以為自己建立訂閱。 除編頁報表外，您無法為其他人訂閱套用資料列層級安全性 (RLS) 的報表。 您可使用自己的安全性內容來為其他人訂閱編頁報表。 深入了解[訂閱編頁報表](../consumer/paginated-reports-subscriptions.md)。
- 報表頁面訂閱會繫結至報表頁面的名稱。 如果您訂閱報表頁面，然後將它重新命名，您必須重新建立訂用帳戶。
- 您的組織可能會在 Azure Active Directory 進行某些設定，而這可能會限制在 Power BI 中使用電子郵件訂閱的功能。 這些限制包括但不限於存取資源時的多重要素驗證或 IP 範圍限制。
- 電子郵件訂用帳戶不支援大部分[自訂視覺效果](../developer/visuals/power-bi-custom-visuals.md)。 其中一個例外是[「已認證」](../developer/visuals/power-bi-custom-visuals-certified.md)的自訂視覺效果。
- 電子郵件訂用帳戶目前不支援 R 支援的自訂視覺效果。
- 電子郵件訂閱傳送時會使用報表的預設篩選器和交叉分析篩選器狀態。 在訂閱之後對預設值所做的所有變更，均不會顯示在電子郵件中。 編頁報表支援此功能，且可供針對每個訂閱設定特定參數值。
- 假設您的報表會與 Analysis Services 即時連線，而且您已將訂閱設定為在資料重新整理之後執行。 其將會在輪詢 Analysis Services 執行個體，且 Power BI 服務首次於您的內部部署模型中偵測到變更時執行。  Power BI 每小時都會在 Analysis Services 資料模型中檢查一次變更，以判斷何時傳送訂閱。
- 符合下列三個條件的報表可使用完整報表附件功能：

    - 位於 [Power BI Premium 或 Premium Per User](../admin/service-premium-what-is.md) 的已升級工作區中。 
    - 附件檔案大小低於 25 MB。
    - 報表少於 20 頁。 
    
    如果報表不符合這三個條件，則無法建立附件格式的完整報表訂閱。 任何現有的附件格式完整報表訂用帳戶都會遭到停用，且您會收到一封電子郵件，說明該錯誤。
    
## <a name="next-steps"></a>後續步驟

- [Power BI 服務中的編頁報表：為自己和其他人訂閱](../consumer/paginated-reports-subscriptions.md)
- 有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 閱讀[儀表板電子郵件訂閱的相關 Power BI 部落格文章](https://powerbi.microsoft.com/blog/introducing-dashboard-email-subscriptions-a-360-degree-view-of-your-business-in-your-inbox-every-day/)
