---
title: 變更 Power BI 報表的設定
description: 變更 Power BI 服務中報表的設定
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 10/14/2020
LocalizationGroup: Reports
ms.openlocfilehash: 996c4a1e7b2bdda0bfdfa0951afc7922b2996084
ms.sourcegitcommit: 00e3eb2ec4f18d48a73cfd020bb42d08e859ad06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/16/2021
ms.locfileid: "100531554"
---
# <a name="change-settings-for-power-bi-reports"></a>變更 Power BI 報表的設定

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] [!INCLUDE [yes-service](../includes/yes-service.md)]

透過 Power BI Desktop 和 Power BI 服務中的報表設定，您可控制報表讀者與報表互動的方式。 例如，您可讓讀者儲存報表的篩選、將報表中的視覺效果個人化，或將報表頁面顯示為橫跨報表底部的索引標籤，而不是沿著側邊顯示。

:::image type="content" source="media/power-bi-report-settings/service-report-settings-pane.png" alt-text="Power BI 服務中報表 [設定] 窗格的螢幕擷取畫面。":::

先閱讀下列文章可能有所幫助：

- [匯入資料集以在 Power BI 服務中建立報表](service-report-create-new.md)，以了解報表建立體驗。
- [Power BI 中的報表](../consumer/end-user-reports.md)，以了解報表讀者的體驗。

 現在就開始吧！

## <a name="prerequisites"></a>先決條件

- 若要使用 Power BI Desktop 建立報表，請參閱 [Desktop 的報表檢視](desktop-report-view.md)。
- [註冊 Power BI 服務](../fundamentals/service-self-service-signup-for-power-bi.md)。 
- 在 Power BI 服務中，您必須具有報表的編輯權限。 如需權限的詳細資料，請參閱[新工作區中的角色](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces)。
- 如果 Power BI 服務中還沒有報表，您可[安裝範例內容套件](sample-datasets.md#install-built-in-content-packs)，其中包含儀表板、報表及資料集。

## <a name="open-the-settings-pane-in-power-bi-desktop"></a>在 Power BI Desktop 中開啟設定窗格

1. 選取 [檔案] > [選項及設定] > [選項]。
1. 在 [目前檔案] 底下，選取 [報表設定]。

    :::image type="content" source="media/power-bi-report-settings/desktop-report-settings-pane.png" alt-text="Power BI Desktop 中 [報表設定] 窗格的螢幕擷取畫面":::

    本文的其餘部分列舉了一些特定報表設定。

## <a name="open-the-settings-pane-in-the-power-bi-service"></a>在 Power BI 服務中開啟 [設定] 窗格

1. 在報表閱讀檢視中，選取 [檔案] > [設定]。

    :::image type="content" source="media/power-bi-report-settings/service-report-file-settings.png" alt-text="[檔案] 功能表到 [設定] 的螢幕擷取畫面。":::

1. 在 [設定] 窗格中，您會看到可設定的一些切換參數，這些參數僅適用於這份報表。 本文的其餘部分列舉了其中一些參數。

## <a name="set-featured-content"></a>設定精選內容

您可以將儀表板、報表以及應用程式列為精選，使其出現在同事 Power BI [首頁] 頁面的 [精選] 區段中。 深入了解[如何精選內容](../collaborate-share/service-featured-content.md)。

## <a name="set-the-pages-pane"></a>設定頁面窗格

目前，您只能變更 Power BI 服務中的頁面窗格設定。 當將 **頁面窗格** 切換為開啟時，報表讀者會在閱讀檢視中看到報表頁面索引標籤沿著報表底部顯示，而不是沿著側邊顯示。 在編輯檢視中，報表頁面索引標籤已經沿著報表的底部顯示。

:::image type="content" source="media/power-bi-report-settings/report-settings-pages-pane.png" alt-text="設定頁面窗格的螢幕擷取畫面。":::

## <a name="control-filters"></a>控制項篩選

報表 [設定] 窗格中有三個設定，其用來控制讀者與報表篩選的互動。 下列連結會移至 [Power BI 報表中的篩選器的格式](power-bi-report-filter.md) ，以取得每個設定的詳細資料。

- **永續性篩選** 允許讀者 [在報表上儲存篩選](power-bi-report-filter.md#allow-saving-filters)。
- **篩選體驗** 還有兩個設定：
    
    允許報表讀者[變更篩選類型](power-bi-report-filter.md#restrict-changes-to-filter-type)。

    啟用[篩選窗格中的搜尋](power-bi-report-filter.md#filters-pane-search)。

## <a name="export-data"></a>匯出資料

根據預設，從報表的視覺效果中，[報表讀者可匯出摘要或基礎資料](../consumer/end-user-export.md)。 有了 **匯出資料**，您就可以讓讀者只匯出摘要資料，或完全不從報表中匯出資料。

## <a name="personalize-visuals"></a>將視覺效果個人化

允許讀者變更及個人化報表中的視覺效果。 深入了解[讓報表讀者個人化視覺效果](power-bi-personalize-visuals.md)。

## <a name="next-steps"></a>後續步驟

* [其他人首頁上的精選內容](../collaborate-share/service-featured-content.md)
* [讓報表讀者個人化報表中的視覺效果](power-bi-personalize-visuals.md)
* 有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)
