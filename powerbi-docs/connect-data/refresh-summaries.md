---
title: Power BI 的重新整理摘要
description: 了解如何使用 Power BI 中的重新整理摘要
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 08/27/2020
LocalizationGroup: Data refresh
ms.openlocfilehash: 285bc76ddb0a0afa571fba06096358c22781a121
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410773"
---
# <a name="refresh-summaries-for-power-bi"></a>Power BI 的重新整理摘要

您可在 Power BI 管理入口網站中找到 Power BI 的 [重新整理摘要] 頁面，這個頁面可供控制及提供重新整理排程、容量及潛在重新整理排程重疊的見解。 您可使用重新整理摘要頁面來判斷是否應調整重新整理排程、了解與重新整理問題建立關聯的錯誤碼，以及適當地管理資料重新整理排程。 

重新整理摘要頁面有兩個檢視：

* [歷程記錄] - 顯示您擔任系統管理員 Power BI Premium 容量的重新整理摘要歷程記錄。

* [排程] - 顯示排程重新整理的排程檢視，其中也會抽出過度訂閱的時段。

您也可以將重新整理事件的資訊匯出到 .CSV 檔案，其可提供重新整理事件或錯誤的重要資訊和見解，這些重新整理事件或錯誤可能會影響效能或完成排程的重新整理事件。

下列各節會逐一探討這些檢視。 

## <a name="refresh-history"></a>重新整理歷程記錄

您可按一下重新整理摘要頁面中的 [歷程記錄] 來選取 [歷程記錄] 檢視。

![重新整理摘要中的 [歷程記錄] 檢視](media/refresh-summaries/refresh-summaries-01a.jpg)

歷程記錄提供您具備系統管理員權限容量上最近排程重新整理的結果概觀。 您可透過按一下資料行來依據任何資料行進行排序。 您可選擇依照遞增排序、遞減，或使用文字篩選條件來依據資料行排序檢視。

![排序 [歷程記錄] 檢視](media/refresh-summaries/refresh-summaries-01b.jpg)

在歷程記錄檢視中，與指定重新整理建立關聯的資料是以每個排程重新整理最近 60 筆記錄為基礎。

您也可以將任何排程重新整理的資訊匯出至 .CSV 檔案，其中包含每個重新整理事件的錯誤訊息等詳細資訊。 匯出至 .CSV 檔案可供依據任何資料行來排序檔案、搜尋字詞、依據錯誤碼或擁有者排序等。 下圖顯示已匯出 .CSV 檔案的範例。 

![匯出重新整理的資訊](media/refresh-summaries/refresh-summaries-05.jpg)

使用匯出檔案中的資訊，您可檢閱容量、持續時間，以及為任何重新整理執行個體記錄的錯誤訊息。 


## <a name="refresh-schedule"></a>重新整理排程

您可按一下重新整理摘要中的 [排程] 來選取 [排程] 檢視。 [排程] 檢視會顯示當週的排程資訊，並細分為 30 分鐘的時段。 

![靠近顯示 [重新整理排程] 頁面 [排程] 索引標籤的螢幕擷取畫面。](media/refresh-summaries/refresh-summaries-02a.jpg)

[排程] 檢視非常適合用來判斷重新整理事件是否具備正確的間距，讓所有重新整理都能在不重疊的情況下完成，或判斷您是否排程了執行時間過長的重新整理事件而造成資源競爭。 若您發現此類資源競爭，則建議您調整重新整理排程來避免衝突或重疊，以讓排程重新整理可成功完成。 

![[重新整理排程] 頁面 [排程] 索引標籤的螢幕擷取畫面。](media/refresh-summaries/refresh-summaries-02.jpg)

[已預約的排程時間 (分鐘)] 資料行是每個相關聯資料集最高 60 筆記錄的平均值。 每 30 分鐘時段此數值是為所有排程在該時段啟動的排程重新整理，「以及」任何設為在「前一個」時段啟動，但是其平均持續時間溢出到所選取時段排程重新整理計算的總和。

*可用的重新整理時間 (分鐘)* 資料行是每個時段中可用於重新整理的分鐘數，減去該時段已排程的任何重新整理。 例如，如果您的 P2 訂用帳戶提供 12 個同時執行的重新整理，您會有 12 個 30 分鐘的時段，因此 12 次重新整理 x 30 分鐘 = 360 分鐘可用於該時段中的重新整理。 如果您在該時段有一個需要 20 分鐘的已預約重新整理，則該時段中的「可用的重新整理時間 (分鐘)」是 340 分鐘 (可用總時間 360 分鐘，減去 20 分鐘已預約 = 仍有 340 分鐘可用)。 

您可選取時段，然後選取相關聯的 [詳細資料] 按鈕來查看哪些排程重新整理事件參與已訂閱的重新整理時間，以及完成這些事件所耗費的時間長度。

讓我們看一下範例以了解其運作方式。 下列對話方塊會在選取星期日下午 8:30 時段，並按一下 [詳細資料] 時顯示。

![螢幕擷取畫面，其中顯示重新整理所選時間的詳細資料。](media/refresh-summaries/refresh-summaries-04.jpg)

這個時段內有三個會發生的排程重新整理事件。 

我們可透過查看 [排程時段] 資料行中的值來判斷排程重新整理 #1 和 #3 都針對此下午 8:30 時段進行排程。 其平均持續時間分別為 4 分 39 秒及六秒 (0:06)。 看來一切正常。

但是，雖然排程重新整理 #2 針對下午 8:00 時段進行排程，但因為其平均耗費超過 48 分鐘才完成 (可在 [平均持續時間] 資料行中查看)，所以該重新整理事件會溢出到下一個 30 分鐘時段。 

這不是件好事。 在此案例中系統管理員應連絡該排程重新整理執行個體的擁有者，建議擁有者為該排程重新整理尋找不同時段，或重新排程其他重新整理以避免重疊，或尋找其他解決方案來避免重疊。 


## <a name="next-steps"></a>後續步驟

- [Power BI 的資料重新整理](refresh-data.md)  
- [Power BI Gateway - Personal](service-gateway-personal-mode.md)  
- [內部部署資料閘道 (個人模式)](service-gateway-onprem.md)  
- [為內部部署資料閘道進行疑難排解](service-gateway-onprem-tshoot.md)  
- [對 Power BI Gateway - Personal 進行疑難排解](service-admin-troubleshooting-power-bi-personal-gateway.md)  

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)