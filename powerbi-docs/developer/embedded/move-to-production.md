---
title: 將 Power BI 內嵌式分析應用程式移至生產環境，以取得更佳的內嵌 BI 見解
description: 了解將 Power BI 應用程式移至生產環境所需的步驟。 使用 Power BI 內嵌式分析，以便取得更佳的內嵌 BI 見解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.topic: tutorial
ms.service: powerbi
ms.subservice: powerbi-developer
ms.custom: seodec18
ms.date: 06/02/2020
ms.openlocfilehash: 71eff0f09c0e34ffd8789f1b56347d754b6589bc
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97886664"
---
# <a name="move-your-embedded-app-to-production"></a>將內嵌應用程式移至生產環境

在完成應用程式的開發之後，若要移至生產環境，您必須為工作區配置容量。

> [!Important]
> 所有工作區 (一個包含報表或儀表板，另一個包含資料集) 必須指派給一個容量。

## <a name="create-a-capacity"></a>建立容量

透過建立容量，您即可為客戶提供資源。 有兩種類型的容量可供選擇：

* **Power BI Premium** - 兩個 SKU 系列 (*EM* 和 *P*) 中可用的租用戶層級 Microsoft 356 訂閱。內嵌 Power BI 內容時，此解決方案稱為「Power BI 內嵌」。 如需此訂用帳戶的詳細資訊，請參閱[什麼是 Power BI Premium？](../../admin/service-premium-what-is.md)

* **Azure Power BI Embedded** - 您可以在 [Microsoft Azure 入口網站](https://portal.azure.com)中購買容量。 此訂用帳戶會使用 *A* SKU。 如需如何建立 Power BI Embedded 容量的詳細資料，請參閱 [Create Power BI Embedded capacity in the Azure portal](azure-pbie-create-capacity.md) (在 Azure 入口網站中建立 Power BI Embedded 容量)。

    > [!NOTE]
    > 在 A SKU 中，您無法使用免費的 Power BI 授權存取 Power BI 內容。

### <a name="capacity-specifications"></a>容量規格

下表描述每個 SKU 的資源和限制。 若要判斷最符合需求的容量，請參閱[我該為案例購買哪一種 SKU](./embedded-faq.md#which-solution-should-i-choose) 資料表。

| 容量節點 | V 核心總數 | 後端 V 核心 | RAM (GB) | 前端 V 核心 | DirectQuery/即時連線 (每秒) | 模型重新整理平行處理原則 |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0.5 | 2.5 | 0.5 | 3.75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7.5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| | | | | | | |

## <a name="development-testing"></a>開發測試

若要進行開發測試，您可搭配 Pro 授權使用內嵌試用權杖。 若要在生產環境中進行內嵌，請使用容量。

Power BI「服務主體」或「主使用者」(主帳戶) 可產生的內嵌試用權杖數有所限制。 請使用[可用功能](/rest/api/power-bi/availablefeatures/getavailablefeatures) API 來檢查目前內嵌使用量的百分比。 使用量會針對每個服務主體或主帳戶顯示。

若在測試時用盡內嵌權杖，則需要購買 Power BI Embedded 或 Premium [容量](embedded-capacity.md)。 使用容量可產生的內嵌權杖數沒有限制。

## <a name="assign-a-workspace-to-a-capacity"></a>將工作區指派給容量

建立容量之後，您可以將工作區指派到該容量。

您必須將所有包含與內嵌內容 (包括資料集、報表和儀表板) 相關之 Power BI 資源的工作區指派給容量。 例如，如果內嵌報表和繫結至該報表的資料集位於不同工作區，則必須將這兩個工作區指派給容量。

### <a name="assign-a-workspace-to-a-capacity-using-a-service-principal"></a>使用服務主體將工作區指派給容量

若要使用[服務主體](embed-service-principal.md)將容量指派至工作區，請使用 [Power BI REST API](/rest/api/power-bi/capacities/groups_assigntocapacity)。 使用 Power BI REST API 時，請務必使用[服務主體物件識別碼](embed-service-principal.md)。

### <a name="assign-a-workspace-to-a-capacity-using-a-master-user"></a>使用主使用者將工作區指派給容量

請遵循下列步驟，使用 **主使用者** 將容量指派給工作區。

1. 在 [Power BI 服務] 中開啟工作區，選取 

1. 在 **Power BI 服務** 中，展開 工作區，然後選取用於內嵌內容之工作區的省略符號。 然後選取 [編輯工作區]。

    >[!div class="mx-imgBorder"]
    >:::image type="content" source="media/move-to-production/workspace-settings.png" alt-text="螢幕擷取畫面，其中顯示 Power BI 服務入口網站中的 [工作區設定] 功能表。":::

2. 選取 [Premium] 索引標籤，然後執行下列動作：

    * 啟用 [容量]。

    * 選取您建立的容量。

    * 選取 [儲存]。

    >[!div class="mx-imgBorder"]
    >:::image type="content" source="media/move-to-production/premium-tab.png" alt-text="螢幕擷取畫面，其中顯示 Power BI 服務入口網站中的工作區 Premium 設定索引標籤。":::

    將工作區指派給容量之後，工作區旁邊會出現一個菱形 

    >[!div class="mx-imgBorder"]
    >:::image type="content" source="media/move-to-production/premium-workspace.png" alt-text="螢幕擷取畫面，其中顯示 Power BI 服務入口網站中具有 Premium 容量的工作區旁邊有一個菱形。":::

## <a name="next-steps"></a>後續步驟

>[!div class="nextstepaction"]
>[Power BI 內嵌式分析中的容量和 SKU](embedded-capacity.md)

>[!div class="nextstepaction"]
>[Power BI 內嵌式分析中的容量規劃](embedded-capacity-planning.md)

>[!div class="nextstepaction"]
>[產生內嵌權杖時的考量](generate-embed-token.md)