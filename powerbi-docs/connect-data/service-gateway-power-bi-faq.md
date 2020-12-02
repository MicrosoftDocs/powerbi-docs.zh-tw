---
title: 內部部署資料閘道常見問題集 - Power BI
description: 本文是 Power BI 內部部署資料閘道的常見問題集。 本文會將 Power BI 中所使用閘道的常見問題集整合至同一個地方。
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: f9a51e6150c7ae351cea968c0d7ea39d2d0d6c32
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96392212"
---
# <a name="on-premises-data-gateway-faq---power-bi"></a>內部部署資料閘道常見問題集 - Power BI

[!INCLUDE [gateway-rewrite](../includes/gateway-rewrite.md)]

## <a name="power-bi"></a>Power BI

**問：** 我需要升級內部部署資料閘道 (個人模式) 嗎？

**答：** 不需要，您可以繼續使用 Power BI 的閘道 (個人模式)。

**問：** 安裝閘道和在 Power BI 服務中管理它是否需要任何特殊權限？

**答：** 不需要任何特殊權限。

**問：** 是否可以上傳具有連線到內部部署資料來源之 Power Pivot 資料模型的 Excel 活頁簿？ 針對此案例，我會需要閘道嗎？ 

**答：** 是，您可以上傳該活頁簿。 而且您不需要使用閘道。 但因為資料將會位在 Excel 資料模型中，所以 Power BI 中以 Excel 活頁簿為基礎的報表就不會是即時報表。 若要重新整理 Power BI 中的報表，您每次都必須重新上傳更新後的活頁簿。 或者，使用已排定重新整理的閘道。

**問：** 如果使用者共用具有 DirectQuery 連線的儀表板，其他使用者是否能在不具備相同權限的情況下查看資料？ 

**答：** 針對已連線至 Azure Analysis Services 的儀表板，使用者只能看到他們所能存取的資料。 如果使用者沒有相同的權限，他們將無法看到任何資料。 若是其他資料來源，所有使用者都將共用管理員針對該資料來源所輸入的認證。

**問：** 為何我無法連線至我的 Oracle 伺服器？ 

**答：** 您可能需要先安裝 Oracle 用戶端並使用適當的伺服器資訊設定 tnsnames.ora 檔案，才能連線至 Oracle 伺服器。 這是閘道外的個別安裝項目。 如需詳細資訊，請參閱[安裝 Oracle 用戶端](service-gateway-onprem-manage-oracle.md#install-the-oracle-client)。

**問：** 我正在使用 R 指令碼。 這受到支援嗎？

**解答**：只有個人模式才支援 R 指令碼。

## <a name="analysis-services-in-power-bi"></a>Power BI 中的 Analysis Services

**問：** 是否可以使用 msmdpump.dll 為 Analysis Services 建立自訂的有效使用者名稱對應？ 

**答：** 不會。 目前不支援這種使用方式。

**問：** 是否可以使用閘道來連線至多維度 (OLAP) 執行個體？ 

**答：** 是。 內部部署資料閘道同時支援對 Analysis Services 表格式和多維度模型的即時連線。

**問：** 如果我安裝閘道器的電腦與使用 Windows 驗證的內部部署伺服器位在不同網域，會發生什麼事？ 

**答：** 這種情況並不會有固定的答案。 這完全取決於兩個網域之間的信任關係。 如果兩個不同網域都位於受信任的網域模型，則此閘道或許可以連接至 Analysis Services 伺服器，且可以解析有效使用者名稱。 否則，您可能會登入失敗。

**問：** 如何知道哪些有效使用者名稱已傳遞至我的內部部署 Analysis Services 伺服器？ 

**答：** 我們已在 [疑難排解文章](service-gateway-onprem-tshoot.md)中回答這個問題。

## <a name="next-steps"></a>後續步驟

* [為內部部署資料閘道進行疑難排解](/data-integration/gateway/service-gateway-tshoot)

有其他問題嗎？ 試試 [Power BI 社群](https://community.powerbi.com/)。
