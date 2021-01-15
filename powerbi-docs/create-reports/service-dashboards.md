---
title: Power BI 設計工具的儀表板簡介
description: 儀表板是 Power BI 服務的重要功能。 它們是透過視覺效果來說故事的單一頁面，通常稱為畫布。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 01/08/2021
LocalizationGroup: Dashboards
ms.openlocfilehash: 2d5eb4047b467544110a5802fa1d41b7ed65bb6a
ms.sourcegitcommit: f791eef8e885f18c48997c9af63ab56211f1ceb8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2021
ms.locfileid: "98053343"
---
# <a name="introduction-to-dashboards-for-power-bi-designers"></a>Power BI 設計工具的儀表板簡介

Power BI 「儀表板」是透過視覺效果來說故事的單一頁面，通常稱為畫布。 因為受限於一個頁面，所以設計良好儀表板只包含該故事的重點。 讀者可以檢視相關報表來取得詳細資料。

![儀表板](media/service-dashboards/power-bi-dashboard2.png)

儀表板功能僅限於 Power BI 服務。 它們在 Power BI Desktop 中無法使用。 雖然您無法在行動裝置上建立儀表板，但可以在該處[檢視和共用](../consumer/mobile/mobile-apps-view-dashboard.md)儀表板。

## <a name="dashboard-basics"></a>儀表板的基本概念 

您在儀表板上看到的視覺效果稱為「磚」。 您會從報表將磚「釘選」到儀表板。 如果您不熟悉 Power BI，請參閱 [Power BI 服務中的設計工具基本概念](../fundamentals/service-basic-concepts.md)來打好基礎。

儀表板上的視覺效果來自報表，而每份報表都是以一個資料集為基礎。 您可以將儀表板想成是進入基礎報表和資料集的一種方法。 選取視覺效果會帶您前往效果所依據的報表 (和資料集)。

![顯示儀表板、報表、資料集之間關聯性的圖表](media/service-dashboards/power-bi-diagram.png)

## <a name="advantages-of-dashboards"></a>儀表板的優點
儀表板是很棒的方式，一眼就可以監視企業，以及查看所有最重要的計量。 儀表板上的視覺效果可以來自一或多個基礎資料集，以及來自一或多份基礎報表。 儀表板將內部部署和雲端的資料結合在一起，提供不受資料位置限制的合併檢視。

儀表板不只是好看的圖片。 其具有高度互動性，且磚會隨著基礎資料變更來更新。

## <a name="who-can-create-a-dashboard"></a>誰可以建立儀表板？
能夠建立儀表板的能力視為「建立者」功能，需要報表的編輯權限。 報表的建立者，以及由建立者授予存取權限的同事皆會有編輯權限。 例如，如果 David 在 workspaceABC 中建立報表，並將您新增為該工作區的成員，您和 David 都會有編輯權限。 反過來說，如果報表是直接與您共用，或是搭配 [Power BI 應用程式](../collaborate-share/service-create-distribute-apps.md)與您共用 (在此情況下，您是「取用」該報表)。 您可能將無法將磚釘選到儀表板。 

> [!IMPORTANT]
> 您需要 [Power BI Pro](../fundamentals/service-features-license-type.md) 授權，才能在工作區中建立儀表板。 您可以在您自己的 [我的工作區] 中建立儀表板，而不需要 Power BI Pro 授權。


## <a name="dashboards-versus-reports"></a>儀表板與報表
[報表](../consumer/end-user-reports.md)與儀表板看起來很相似，因為它們都是填滿視覺效果的畫布。 但有一些主要的差異，如下表所示。

| **功能** | **儀表板** | **報表** |
| --- | --- | --- |
| 頁面 |一個頁面 |一或多個頁面 |
| 資料來源 |每個儀表板一或多份報表以及一或多個資料集 |每份報表單一資料集 |
| Power BI Desktop 可用 |否 | 是。 可在 Power BI Desktop 中建置及檢視報表 |
| 訂閱 |是。 可訂閱儀表板 |是。 可訂閱報表頁面 |
| 篩選 |不會。 無法篩選或配量儀表板。 「可以」[在焦點模式中篩選儀表板磚](../consumer/end-user-focus.md#working-in-focus-mode)，但無法儲存篩選。 |是。 有多種不同方法可篩選、反白顯示及配量 |
| 精選 |是。 可將一個儀表板設為您的「精選」儀表板 |否 |
| 我的最愛 | 是。 可將多個儀表板設為「我的最愛」 | 是。 可將多個報表設為「我的最愛」 |
| 設定警示 |是。 在特定情況下可用於儀表板磚 |否 |
| 自然語言查詢 (問與答) |是 | 是，若您具有報表和基礎資料集的編輯權限 |
| 可以看到基礎資料集的資料表和欄位 |不會。 可以匯出資料，但看不到儀表板本身的資料表和欄位 |是 |


## <a name="next-steps"></a>後續步驟
* 使用[範例儀表板](sample-tutorial-connect-to-the-samples.md)其中一項教學課程來熟悉儀表板。
* 了解[儀表板磚](service-dashboard-tiles.md)。
* 想要追蹤個別的儀表板磚，並在它達到某個閾值時收到電子郵件？ [在磚上建立警示](service-set-data-alerts.md)。
* 了解如何使用 [Power BI 問與答](power-bi-tutorial-q-and-a.md)提出與您的資料相關的問題，然後接收視覺效果的回應。
