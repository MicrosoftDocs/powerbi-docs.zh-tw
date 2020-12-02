---
title: Power BI 計劃性維護
description: 系統管理員需了解 Power BI 計劃性維護如何影響其組織的相關資訊，以及可能需要採取的後續步驟。
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 10/30/2020
ms.custom: MC
ROBOTS: NOINDEX
LocalizationGroup: Admin
ms.openlocfilehash: d62b06e23f7e97141f6d10451e9d75f8fb9e417e
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96412314"
---
# <a name="power-bi-planned-maintenance"></a>Power BI 計劃性維護

對於 Power BI 服務的計劃性維護，是我們承諾為客戶提供可靠產品的必要部分。 進行計劃性維護時，您的組織將有一段時間無法使用 Power BI 服務。 使用者可能無法存取 Power BI 服務，而且背景作業可能失敗。 在維護時段之後，我們預期該服務會正常運作，而且互動式與背景作業都會成功。  

計劃在正常上班時間以外進行維護，有助於將對組織的任何影響降至最低。 對於使用者散佈全球的組織而言，我們承認「在正常上班時間以外」可能會對您產生不同的影響。 對您使用者造成的任何影響，我們深感抱歉。 我們正致力於改善 Power BI，並盡可能減少這些維護時段。

如果您的組織會受到影響，我們將提前通知您。 Microsoft 365 系統管理員將會在 Microsoft 365 訊息中心看到提前通知，並將收到電子郵件。 此外，具有頂級支援合約的客戶，將會透過其 Microsoft 帳戶小組收到通知。

## <a name="actions-to-take-now"></a>要立即採取的動作

* Microsoft 365 系統管理員應該[查看訊息中心](https://admin.microsoft.com/Adminportal/Home#/MessageCenter)，以取得有關 Power BI 計劃性維護的訊息。 與應該知道但可能無法存取訊息中心的人員分享訊息。
* 如果您不是 Microsoft 365 系統管理員，請與您的 IT 部門或內部支援小組連絡，以詢問任何即將進行的維護。

## <a name="actions-to-take-when-maintenance-is-complete"></a>維護完成時要採取的動作

* 使用者應該重新整理任何開啟的瀏覽器視窗。
* Power BI 行動裝置應用程式使用者將必須確認其使用的是最新版本並登出，然後重新登入應用程式。 請檢查您手機的應用程式市集或查看我們的 [Power BI 行動版](https://powerbi.microsoft.com/mobile/)頁面。
* 主動編輯或發佈使用組織視覺效果之報表的客戶 (無論是在本機或從 OneDrive 和 SharePoint 位置)，都將必須透過組織的視覺效果存放區重新匯入視覺效果，或在重新發佈之前下載已更新的 PBIX。 如需取得組織視覺效果的詳細資訊，請參閱[組織視覺效果](organizational-visuals.md)。
* 如果使用 [使用 Excel 分析] 功能的 Excel 活頁簿並未重新整理，您可能需要更新連接字串，或重新下載該資料集的 ODC 連線。 如需詳細資訊，請參閱[使用 Excel 分析](../collaborate-share/service-analyze-in-excel.md#connect-to-power-bi-data)。
* 完成維護時，連結至內容中內嵌的 Power BI 可能無法連線。 例如，SharePoint 或 Teams 中的內嵌連結可能會導致使用者錯誤。 若要解決此問題，您必須在 Power BI 中重新產生內嵌連結，然後更新其使用位置。 如需內嵌連結的詳細資訊，請參閱[在 SharePoint Online 中嵌入報表網頁組件](../collaborate-share/service-embed-report-spo.md)和[使用 Power BI 在 Microsoft Teams 中共同作業](../collaborate-share/service-collaborate-microsoft-teams.md)。
* 維護完成後，在維護前收集的部分使用量資料將無法使用。 此使用量資料包括：

  * [Power BI 活動記錄](service-admin-auditing.md#use-the-activity-log)。 使用者應該在維護前先下載活動記錄。 您也可以使用 [Office 365 稽核記錄資料](service-admin-auditing.md#access-your-audit-logs)取得對等的活動詳細資料。
  * [譜系檢視](../collaborate-share/service-data-lineage.md#explore-lineage-view)中的檢視計數
  * [資料保護計量報表](service-security-data-protection-metrics-report.md)
  * [使用計量 (預覽)](../collaborate-share/service-modern-usage-metrics.md)

## <a name="next-steps"></a>後續步驟

* [啟用服務中斷通知](service-interruption-notifications.md)
* [在訊息中心追蹤即將進行的變更](/microsoft-365/admin/manage/message-center) \(部分機器翻譯\)