---
title: 依授權類型區分的 Power BI 服務功能
description: 在 Power BI 服務中，使用者的能力取決於其所擁有的個別使用者授權類型 (免費或 Pro)，以及其所互動的內容，是否位於指派給 Power BI Premium 容量的工作區中。
author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/11/2020
ms.author: kfollis
ms.custom: licensing support
LocalizationGroup: Get started
ms.openlocfilehash: 48e382db2866187f4394cf8a60789604f3d900b7
ms.sourcegitcommit: cc20b476a45bccb870c9de1d0b384e2c39e25d24
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94512784"
---
# <a name="power-bi-service-features-by-license-type"></a>依授權類型區分的 Power BI 服務功能

Power BI 個別使用者授權有兩種：免費和 Pro。 使用者需要哪種類型的授權，取決於內容的儲存位置及他們將與該內容互動的方式。 可以儲存內容的位置會取決於您組織的[授權類型](#licenses-and-license-types)。

## <a name="licenses-and-license-types"></a>授權和授權類型

其中一種授權類型是 [Power BI Premium](../admin/service-admin-premium-purchase.md) 容量型授權，其可讓具備免費授權的使用者操作已指派給 Premium 容量之工作區中的內容。 在 Premium 容量之外，具備免費授權的使用者則只能使用 Power BI 服務來連線到資料，然後在 [我的工作區] 中建立報表和儀表板。 這些使用者無法與其他人共用內容，或將內容發佈至其他工作區。 若要深入了解工作區類型，請參閱[工作區類型](../consumer/end-user-workspaces.md#types-of-workspaces)。 若要深入了解 Power BI Premium，請參閱[什麼是 Power BI Premium？](../admin/service-premium-what-is.md)

具有免費及 Pro 個別使用者授權的 Power BI 授權，只能使用共用且受限的容量來處理內容。 如果內容儲存在該共用容量中，則獲指派 Power BI Pro 授權的使用者只能與其他 Power BI Pro 使用者共同作業。 他們可以取用其他使用者所共用的內容、將內容發佈到應用程式工作區、共用儀表板，以及訂閱儀表板和報表。  當工作區在 Premium 容量中時，Pro 使用者可將內容散發給沒有 Power BI Pro 授權的使用者。

使用 Premium Per User 授權時，由具有 Premium Per User 授權的使用者所建立的內容，除非特別將該內容放置於裝載在 Premium 容量上的工作區中，否則就只能與其他具有 Premium 授權的使用者共用。 下表摘要說明每個授權類型的基本功能。 

| 授權類型 | 工作區在共用容量中時的功能 | 工作區在 Premium 容量中時的額外功能 |
| --------- | ----------- | ----------- |
| Power BI (免費) | 存取我的工作區中的內容 | 取用與其共用的內容 |
| Power BI Pro | 將內容發佈到其他工作區、共用儀表板、訂閱儀表板和報表、與具備 Pro 授權的使用者共用 | 將內容散發給具備免費授權的使用者 |

如需 Power BI Pro 與 Power BI Premium 的比較，請參閱 [Power BI 定價](https://powerbi.microsoft.com/pricing/)的＜Power BI 功能比較＞一節。

若要深入了解授權所提供的功能，請參閱[「取用者」與其他免費授權使用者可使用的 Power BI 功能清單](../consumer/end-user-features.md)及[「取用者」的授權和訂閱](../consumer/end-user-license.md)。

## <a name="next-steps"></a>後續步驟

* [以個人身分註冊 Power BI 服務](service-self-service-signup-for-power-bi.md)
* [Power BI Desktop 與 Power BI 服務的比較](service-service-vs-desktop.md)


Power BI 已推出 Power BI Premium Gen2 作為預覽供應項目，其能透過對下列領域的改進來改善 Power BI Premium 體驗：
* 效能
* 個別使用者授權
* 更大的規模
* 改善的計量
* 自動調整
* 降低管理負擔

如需 Power BI Premium Gen2 的詳細資訊，請參閱 [Power BI Premium 第 2 代 (預覽)](../admin/service-premium-what-is.md#power-bi-premium-generation-2-preview)。