---
title: Power BI 內嵌式分析 API 使用即時資料的自動保留原則，以便取得更佳的內嵌 BI 見解
description: 了解 Power BI 服務中的自動保留原則。 使用 Power BI 內嵌式分析，以便取得更佳的內嵌 BI 見解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 81c975332abc4cb599a7172f1697c1b06ea34eba
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887722"
---
# <a name="automatic-retention-policy-for-real-time-data"></a>即時資料的自動保留原則

在 Power BI 服務的自動保留原則是查詢字串參數，讓預設保留原則可自動清除舊資料，同時保持新資料持續進入您的儀表板。 第一個保留原則稱為 *先進先出 (FIFO)*。 當這原則啟用時，直到達到 200,000 個資料列之前，會將資料收集在資料表中。 一旦資料超過 200,000 個資料列，最舊的資料列將從資料集中移除。 這使得 200,000 和 210,000 個資料列之間只保留最新的資料。  
  
<center>

![保留原則](media/api-Automatic-retention-policy-for-real-time-data/retention-policy.png) 

</center>

當您第一次建立資料集時，即啟用保留原則。 您所要做的就是將 "default retention policy" 查詢參數新增至 POST 資料集呼叫，並將其設為 *basicFIFO*。  

```console
POST https://api.powerbi.com/v1.0/myorg/datasets?defaultRetentionPolicy={None | basicFIFO}
```
