---
title: 在報表中的表格或矩陣中顯示影像
description: 在 Power BI Desktop 中，您會建立一個包含影像超連結的資料行。 然後在 Power BI Desktop 或 Power BI 服務中，將那些超連結新增至報表表格、矩陣、交叉分析篩選器或多列卡片以顯示影像。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 09/11/2019
LocalizationGroup: Visualizations
ms.openlocfilehash: 4ba0042804d366ddfd80935c48246cadeadf3614
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96417949"
---
# <a name="display-images-in-a-table-matrix-or-slicer-in-a-report"></a>在報表中的表格、矩陣或交叉分析篩選器中顯示影像

增強報表的一個好方法是將影像新增至其中。 頁面上的靜態影像適用於某些用途。 但有時候您會想要與報表中的資料相關的影像。 此主題將教您如何在表格、矩陣、交叉分析篩選器或多列卡片中顯示影像。 

![表格中的 URL 影像](media/power-bi-images-tables/power-bi-url-images-table.png)

## <a name="add-images-to-your-report"></a>將影像新增至您的報表

1. 建立包含影像 URL 的資料行。 如需相關需求，請參閱此文章稍後的[考量](#considerations)。

1. 選取該資料行。 在 [模型]  功能區上，針對 [資料類別]  選取 [影像 URL]  。

    ![將 [資料類別] 設定為 [影像 URL]](media/power-bi-images-tables/power-bi-set-url-image.png)

1. 將資料行新增至表格、矩陣、交叉分析篩選器或多列卡片。

    ![包含影像的交叉分析篩選器](media/power-bi-images-tables/power-bi-url-images-slicer.png)

## <a name="considerations"></a>考量

- 影像必須採用下列其中一種檔案格式：.bmp、.jpg、jpeg、.gif、.png 或 .svg
- URL 必須可匿名存取，而不是位於需要登入的網站上 (例如 SharePoint)。 不過，如果影像是裝載在 SharePoint 或 OneDrive 上，您可以取得直接指向它們的內嵌程式碼。 


## <a name="next-steps"></a>後續步驟

[頁面配置和格式設定](/learn/modules/visuals-in-power-bi/12-formatting)

[Power BI 服務中的設計工具基本概念](../fundamentals/service-basic-concepts.md)

有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)
