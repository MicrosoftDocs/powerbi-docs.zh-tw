---
title: Power BI 與 Azure 輸出
description: 了解 Azure 的輸出費用，以及基於租用戶位置與 Power BI Premium 的 Power BI
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 01/19/2021
LocalizationGroup: Data from databases
ms.openlocfilehash: ec47968294e0fd905d1733bdb30ae1840069aed7
ms.sourcegitcommit: 96080432af4c8e3fe46c23274478ccffa0970efb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98597482"
---
# <a name="power-bi-and-azure-egress"></a>Power BI 與 Azure 輸出

從 Azure 資料中心移出 (輸出) 資料可能會產生頻寬費用。 當使用 Power BI 與 Azure 的資料來源時，您可以藉由確定您的 Power BI 租用戶位於與 Azure 資料來源相同區域，來避免 Azure 輸出費用。

當您將 Power BI 租用戶部署在與部署資料來源相同的 Azure 區域中時，不會因排程的重新整理和 DirectQuery 互動而產生輸出費用。 

## <a name="determining-where-your-power-bi-tenant-is-located"></a>判斷您的 Power BI 租用戶所在位置

若要了解 Power BI 租用戶所在位置，請參閱[我的 Power BI 租用戶位於何處](../admin/service-admin-where-is-my-tenant-located.md)一文。

針對 Power BI Premium 多地理位置客戶，如果您的 Power BI 租用戶並非位於某些 Azure 型資料來源最佳位置，您可以在所需的 Azure 區域部署 Power BI Premium 多地理位置，並從將 Power BI 租用戶和 Azure 資料來源放在相同 Azure 區域中受益。

## <a name="next-steps"></a>後續步驟

如需 Power BI Premium 或多地理位置的詳細資訊，請查看下列資源：

* [Azure 頻寬定價詳細資料](https://azure.microsoft.com/pricing/details/bandwidth/)
* [Microsoft Power BI Premium 是什麼？](../admin/service-premium-what-is.md)
* [如何購買 Power BI Premium](../admin/service-admin-premium-purchase.md)
* [Power BI Premium 的多地理位置支援 (預覽版)](../admin/service-admin-premium-multi-geo.md)
* [我的 Power BI 租用戶位於何處？](../admin/service-admin-where-is-my-tenant-located.md)
* [Power BI Premium 常見問題集](../admin/service-premium-faq.md)
