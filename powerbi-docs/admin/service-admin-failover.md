---
title: Power BI 的高可用性、容錯移轉和災害復原常見問題集
description: 了解 Power BI 服務如何為其使用者提供高可用性，以及提供商務持續性和災害復原。
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 06/18/2020
ms.author: kfollis
LocalizationGroup: Administration
ms.openlocfilehash: 56ace35adf6a005c4370bf692d8851dc015688c0
ms.sourcegitcommit: e8b12d97076c1387088841c3404eb7478be9155c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85782339"
---
# <a name="power-bi-high-availability-failover-and-disaster-recovery-faq"></a>Power BI 的高可用性、容錯移轉和災害復原常見問題集

本文說明 Power BI 服務如何為其使用者提供高可用性，以及提供商務持續性和災害復原。 閱讀本文後，您應該更加了解如何達到高可用性、Power BI 會在什麼情況下執行容錯移轉，以及在進行容錯移轉時，預期服務會發生的情況。

## <a name="what-does-high-availability-mean-for-power-bi"></a>「高可用性」對 Power BI 來說代表什麼？

Power BI 是完全受控的軟體即服務 (SaaS)。  Microsoft 設計和操作此功能以從基礎結構失敗中復原，讓使用者一律能夠存取他們的報表。  [高達 99.9% 的 SLA](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=37) 支援此服務。

## <a name="what-is-a-power-bi-failover"></a>什麼是 Power BI 容錯移轉？

Power BI 會維護 Azure 資料中心 (也稱為區域) 內每個元件的多個執行個體，以確保商務持續性。 如果發生中斷或導致 Power BI 在某區域中無法存取或無法運作的問題，Power BI 就會使其在該區域中的所有元件失效轉移到備份執行個體。 容錯移轉可在新區域 (通常是在相同的地理位置，如 [Microsoft 信任中心](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location)所註明) 中，還原 Power BI 服務執行個體的可用性和可操作性。

容錯移轉 Power BI 服務執行個體僅支援「讀取作業」，這表示容錯移轉期間不支援下列作業：重新整理、報表發佈作業、儀表板或報表的修改，以及其他需要變更 Power BI 中繼資料 (例如，在報表中插入註解) 的作業。  顯示儀表板和報表等讀取作業 (並非根據對內部部署資料來源進行的 DirectQuery 或 Live Connect) 會繼續正常運作。

## <a name="how-are-backup-instances-kept-in-sync-with-my-data"></a>備份執行個體如何與我的資料保持同步？

所有 Power BI 服務元件都會定期同步處理其備份執行個體。 針對 Power BI 中上傳或變更的任何內容，我們擬訂 15 分鐘的時間點同步處理。 發生容錯移轉時，Power BI 會使用 [Azure 儲存體的異地備援複寫](/azure/storage/common/storage-redundancy-grs)和 [Azure SQL 的異地備援複寫](/azure/sql-database/sql-database-active-geo-replication)，以確保備份執行個體存在於其他區域，並可在發生容錯移轉時予以使用。

## <a name="where-are-the-failover-clusters-located"></a>容錯移轉叢集位於何處？

除非在 [Microsoft 信任中心](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location)內另行註明，否則備份執行個體位於您在組織註冊 Power BI 時所選取的相同地理位置 (地區) 中。 地區可包含數個區域，Microsoft 可能會將資料複寫到指定地區內的任一區域以進行資料復原。 Microsoft 不會在地區外複寫或移動客戶資料。 如需 Power BI 所提供地區與其中區域的對應，請參閱 [Microsoft 信任中心](https://www.microsoft.com/TrustCenter/CloudServices/business-application-platform/data-location)。

## <a name="how-does-microsoft-decide-to-fail-over"></a>Microsoft 如何決定容錯移轉？

有兩種不同的系統可指出何時可能需要容錯移轉：

- 我們外部和內部監視探查會指出缺乏可用性或無法正常運作。 這類指示會根據 Power BI 元件或某區域中一或多個 Power BI 相依服務中偵測到的中斷。
- Microsoft Azure 的中央作業小組通知我們在某個區域中發生嚴重中斷。

在這兩種情況下，Power BI 執行小組成員會制定進行容錯移轉的決策；決策本身並非自動化程序。 制定決策之後，容錯移轉的程序會就自動執行。

## <a name="how-do-i-know-power-bi-is-now-in-failover-mode"></a>如何知道 Power BI 現已處於容錯移轉模式？

Power BI 支援頁面 ([https://powerbi.microsoft.com/support/](https://powerbi.microsoft.com/support/)) 上已張貼通知。 該通知包含在容錯移轉期間無法使用的主要作業，包括發佈、重新整理、建立儀表板、複製儀表板和權限變更。

## <a name="how-long-does-it-take-power-bi-to-fail-over"></a>Power BI 需要多久時間進行容錯移轉？

在確認需要容錯移轉後，Power BI 需要約 15 分鐘時間才會再次運作。 確認是否需要容錯移轉的時間會根據中斷情況而有所不同。 

一旦執行了容錯移轉，Power BI 會使用 Azure 儲存體異地複寫來執行容錯移轉。 不過，這類複寫通常會有 15 分鐘的傳回點，[Azure 儲存體不保證此時間範圍](https://docs.microsoft.com/azure/storage/common/storage-redundancy)適用 SLA，因此 Power BI 也無法保證時間範圍。 

## <a name="what-happens-to-workspaces-and-reports-if-my-premium-capacity-becomes-unavailable"></a>如果我的 Premium 容量變得無法使用，工作區和報表會發生什麼情況？ 

如果 Premium 容量變得無法使用，工作區和報表會保持可存取狀態，而先前有權存取的所有 Power BI Pro 授權使用者都可看到這兩者。

## <a name="when-does-my-power-bi-instance-return-to-the-original-region"></a>我的 Power BI 執行個體何時返回至原始區域？

當導致容錯移轉的問題解決時，Power BI 服務執行個體就會返回其原始區域。 請檢查 Power BI 支援頁面：當問題解決時，Power BI 小組會移除描述容錯移轉的通知。 此時，作業應該會恢復正常。

## <a name="am-i-responsible-for-the-availability-of-my-power-bi-solution"></a>我是否要負責 Power BI 解決方案的可用性？

如果您組織中使用的 Power BI 解決方案牽涉到下列其中一個項目，您必須採取一些措施，以保證此解決方案會保持高可用性：

- 如果您的組織使用 Power BI Premium，您必須確定 Premium 容量會調整大小以符合部署的負載需求。  [Power BI Premium Planning and Deployment whitepaper](https://aka.ms/Premium-Capacity-Planning-Deployment) (Power BI Premium 規劃與部署的技術白皮書) 和 [Power BI Premium 容量計量應用程式](service-admin-premium-monitor-capacity.md)可協助您規劃和滿足此需求。 我們會經常在 Power BI 的計量應用程式和管理入口網站中新增新功能以提供協助。
- 如果您的組織使用內部部署資料閘道存取內部部署資料來源，您必須[依照本文所述](/data-integration/gateway/service-gateway-high-availability-clusters)設定閘道以支援高可用性。 無論您是在匯入模式下重新整理報表，還是使用 DirectQuery 或 Live Connect 來存取資料或資料模型，請遵循本指南中的指示。

## <a name="will-gateways-function-when-in-failover-mode"></a>閘道是否會在容錯移轉模式下運作？

不會。 來自內部部署資料來源 (根據 Direct Query 和 Live Connect 的任何報表與儀表板) 的所需資料，在容錯移轉期間都無法運作。 然而閘道器設定不會變更：當 Power BI 執行個體返回其原始狀態時，閘道就會回復為其正常功能。
