---
title: 在 Power BI 中使用客戶管理的金鑰
description: 了解如何在 Power BI 中使用客戶管理的金鑰。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 11/11/2020
LocalizationGroup: Premium
ms.openlocfilehash: 215c84b9af9d3b785c055d633a41b99bbea2bb2f
ms.sourcegitcommit: cc20b476a45bccb870c9de1d0b384e2c39e25d24
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94512577"
---
# <a name="use-customer-managed-keys-in-power-bi"></a>在 Power BI 中使用客戶管理的金鑰

Power BI 會加密「待用」與「處理中」的資料。 根據預設，Power BI 會使用 Microsoft 管理的金鑰來為您加密資料。 組織可以選擇使用自己的金鑰，加密使用者在 Power BI 間待用的內容，從報表影像到 Premium 容量中的匯入資料集。 

## <a name="why-use-customer-managed-keys"></a>為什麼要使用客戶管理的金鑰

使用 Power BI 客戶管理的金鑰 (CMK)，組織可以達到雲端服務提供者 (在此案例中為 Microsoft) 加密待用資料的合規性需求。 CMK 僅提供給新的 Power BI Premium 客戶，且可讓組織使用其提供及管理的金鑰來加密其 Power BI 使用者內容。 撤銷客戶管理的金鑰，會讓所有人在一小時內無法讀取 Power BI 中的使用者內容，包括 Microsoft。 相較於 BYOK 供應項目，除了匯入至 Premium 容量所裝載報表和資料集的客戶資料之外，CMK 也涵蓋由服務產生的使用者內容，其會實施更嚴格的快取原則，且只能套用單一金鑰來加密所有資料。


## <a name="how-to-use-customer-managed-keys"></a>如何使用客戶管理的金鑰
若要選擇使用 Power BI 客戶自控金鑰，則組織必須連絡組織的 Microsoft 帳戶管理員，以驗證組織是否符合啟用 CMK 所需的特定大小需求。  


## <a name="next-steps"></a>後續步驟

下列連結提供有關客戶管理金鑰的實用資訊：

* [攜帶您自己的加密金鑰以用於 Power BI](service-encryption-byok.md)
* [設定 Power BI Premium 的多地理位置支援](service-admin-premium-multi-geo.md)
* [容量的運作方式](service-premium-what-is.md#how-capacities-function)
* [累加式重新整理](service-premium-incremental-refresh.md)。
