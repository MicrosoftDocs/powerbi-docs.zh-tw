---
title: DAX 範例模型
description: 支援參考文章的 DAX 範例模型。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 06/25/2020
ms.openlocfilehash: b2930003da1593ef5d5888c611af6700e00d3d07
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96394052"
---
# <a name="dax-sample-model"></a>DAX 範例模型

**Adventure Works DW 2020** Power BI Desktop 範例模型是設計來支援您的 DAX 學習。 此模型是以 AdventureWorksDW2017 的 [Adventure Works 資料倉儲範例](/sql/samples/adventureworks-install-configure#data-warehouse-downloads)為基礎，不過，已對資料進行修改以符合範例模型的目標。

## <a name="scenario"></a>案例

:::image type="content" source="media/dax-sample-model/adventure-works-logo-150x150.png" alt-text="顯示 Adventure Works 公司標誌的影像。":::

Adventure Works 公司代表一家自行車製造商，該公司向全球市場銷售自行車和配件。 該公司將其資料倉儲資料儲存在 Azure SQL Database 中。

## <a name="model-structure"></a>模型結構

此模型有七個資料表：

|資料表|描述|
|-----|-------|
|**Customer**|描述客戶及其地理位置。 客戶線上購買產品 (網際網路銷售)。|
|**Date**|**日期** 和 **銷售** 資料表之間有三個關聯性，適用於訂單日期、出貨日期和到期日。 訂單日期關聯性為作用中。 該公司使用從每年 7 月 1 日開始的會計年度報告銷售情況。 該資料表會使用 **日期** 資料行標示為日期資料表。|
|**產品**|僅儲存已完成的產品。|
|**轉售商**|描述轉銷商及其地理位置。 轉銷商銷售產品給客戶。|
|**Sales**|將資料列儲存在銷售單明細行粒紋中。 所有財務價值均以美元 (USD) 為單位。 最早的訂單日期是 2017 年 7 月 1 日，而最新的訂單日期是 2020 年 6 月 15 日。|
|**銷售單**|描述銷售單和訂單明細行號，以及銷售通路，也就是 **轉銷商** 或 **網際網路**。 這個資料表與 **銷售** 資料表具有一對一關聯性。|
|**銷售領域**|銷售領域會組織成群組 (北美洲、歐洲和太平洋地區)、國家/地區和區域。 僅美國銷售區域層級的產品。|

模型不包含任何 DAX 計算。

## <a name="download-sample"></a>下載範例

您可以在[這裡](https://aka.ms/dax-docs-sample-file)下載完整 Power BI Desktop 範例模型檔案。

## <a name="next-steps"></a>後續步驟

如需本文的詳細資訊，請參閱下列資源︰

- [資料分析運算式 (DAX) 參考](/dax/)
- 學習路徑：[在 Power BI Desktop 中使用 DAX](/learn/paths/dax-power-bi/) (英文)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com)