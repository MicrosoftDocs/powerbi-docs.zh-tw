---
title: 什麼是 Azure Power BI Embedded 與內嵌式分析 | Microsoft Docs
description: Power BI Embedded 旨在作為一項內嵌式分析，以簡化 ISV 和開發人員使用 Power BI 功能的方式，協助其快速地將令人讚嘆的視覺效果、報表和儀表板新增至他們的應用程式。 了解如何使用 Power BI Embedded 來運用內嵌式分析軟體、內嵌式分析工具，或內嵌式商業智慧工具。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: nishalit
ms.service: powerbi
ms.subservice: powerbi-developer
ms.devlang: csharp, javascript
ms.topic: overview
ms.custom: seodec18
ms.date: 12/10/2018
ms.openlocfilehash: fb2c9046b5812ae027e60f5661c50f573bea8976
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96417236"
---
# <a name="what-is-power-bi-embedded-in-azure"></a>Azure 中的 Power BI Embedded 是什麼？

Power BI Embedded 旨在透過內嵌式分析簡化 ISV 和開發人員使用 Power BI 功能的方式。 Power BI Embedded 可協助您快速地將令人讚嘆的視覺效果、報表和儀表板新增至您的應用程式，藉以簡化 Power BI 功能。 類似於 Microsoft Azure 上使用如機器學習服務和 IoT 之類的服務來建置應用程式的方式。 透過在其應用程式中啟用輕鬆巡覽資料探勘，ISV 可讓其客戶在內容中進行快速、明智的決策。

> [!VIDEO https://www.youtube.com/embed/iEHfUuoZseo]

在 2017 年 5 月，我們已宣告將 Power BI 與 Power BI Embedded 服務聚合。 此聚合提供一個 API 介面、一組一致的功能，並可存取這兩種服務中的最新功能。 此外，我們還引進了以容量為基礎的定價模型，簡化 Power BI 的使用方式。

使用 Power BI Embedded，ISV 和開發人員可獲得額外的彈性，供他們使用 Power BI API 在其應用程式中內嵌智慧。 ISV 和開發人員可以利用最少的開發工作來加快應用程式上市的速度，並藉由在其應用程式中導入 Microsoft 的世界級分析引擎，讓自己脫穎而出。 同樣地，開發人員可以花時間專注於其解決方案，以滿足客戶需求，而不是開發視覺化的分析功能。 此外，Power BI Embedded 可讓您在已使用的熟悉開發環境 (Visual Studio 與 Azure) 中工作。

您是否有使用 Power BI Premium 內嵌 Power BI 內容的現有應用程式？ 如果您是提供應用程式的 ISV 或開發人員，或是使用它們的組織，則不需要採取任何動作。 您和您的客戶可以在不中斷的情況下繼續使用這些應用程式。 如果您有 Power BI 工作區集合上所建置的現有應用程式，並需要利用聚合的 API 介面和以容量作為基礎的新型 Azure SKU，請瀏覽文件以取得移轉指導方針。

## <a name="comparing-power-bi-embedded-with-power-bi-premium"></a>比較 Power BI Embedded 與 Power BI Premium

**Power BI Embedded** 適用於獨立軟體廠商 (ISV) 和為其客戶建置應用程式的開發人員。 它可用來作為協力廠商商業智慧服務，讓您將應用程式資料視覺化，而不是自行建置該服務。 Power BI Embedded 是平台即服務 (PaaS) 分析解決方案，開發人員可以在這個解決方案中為客戶將報表和儀表板嵌入應用程式。 **Power BI Premium** 則是軟體即服務 (SaaS) 分析解決方案，為組織提供最重要商務資料的單一檢視。 

[Power BI Embedded](https://azure.microsoft.com/pricing/details/power-bi-embedded/)　是隨用隨付功能，而 [Power BI Premium](https://powerbi.microsoft.com/calculator/) 則需要支付每月費用。 您可以觀看這個[影片](https://www.youtube.com/watch?v=0y2oJikC6Xc&t=0s&list=PLv2BtOtLblH1dQPV49Ni12olDcUoW-GEl&index=3)以深入了解它們的比較方式。

## <a name="easy-to-use-tools"></a>簡單易用的工具

Power BI Embedded 可讓您專注於拿手項目：建置絕佳的應用程式。 您可以使用已具備的工具和技巧，利用 Power BI Embedded 進行管理和開發。

* [**Azure 入口網站**](https://portal.azure.com/)：Web 架構應用程式，可用來管理所有的 Azure 服務
* [**Visual Studio Code**](https://code.visualstudio.com/docs)：支援延伸模組的可下載之免費開放原始碼的程式碼編輯器，適用於 Windows、macOS 和 Linux
* [**Power BI Desktop**](https://powerbi.microsoft.com/desktop/)：可下載的免費工具，可使用視覺分析建立豐富的互動式報表

使用 REST API，Power BI Embedded 允許使用任何語言進行開發。

## <a name="engage-with-the-power-bi-engineering-team"></a>洽詢 Power BI 工程小組

* [社群](https://community.powerbi.com/)：提出 Power BI 問題
* [Power BI 想法](https://ideas.powerbi.com)：要求並票選功能
* [Reddit](https://www.reddit.com/r/PowerBI/)：討論 Power BI

## <a name="next-steps"></a>後續步驟

如需容量節點的詳細資料，請參閱[定價頁面](https://azure.microsoft.com/pricing/details/power-bi-embedded/)。

若要建立 Power BI Embedded 容量，請參閱[在 Azure 入口網站中建立 Power BI Embedded 容量](azure-pbie-create-capacity.md)

若要開始內嵌 Power BI 內容，請參閱[教學課程：為您的客戶將 Power BI 報表、儀表板或磚內嵌至應用程式](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding-content/)。
