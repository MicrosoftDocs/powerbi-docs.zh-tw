---
title: 減少 Excel 活頁簿的大小以在 Power BI 中檢視
description: 減少 Excel 活頁簿的大小以在 Power BI 中檢視
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 01/10/2019
LocalizationGroup: Data from files
ms.openlocfilehash: 9996b8e3f571a04dc41d138947532f3ab402057a
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96404080"
---
# <a name="reduce-the-size-of-an-excel-workbook-to-view-it-in-power-bi"></a>減少 Excel 活頁簿的大小以在 Power BI 中檢視
所有小於 1 GB 的 Excel 活頁簿都可上傳至 Power BI。 Excel 活頁簿可以包含兩個部分：資料模型和報表的其他部分 — 核心工作表內容。 如果報表符合下列大小限制，您就可以將它儲存到 **商務用 OneDrive**，然後從 Power BI 連接到它並於 Excel Online 中檢視：

* 整份活頁簿的上限是 1 GB。
* 核心工作表內容的上限是 30 MB。

## <a name="what-makes-core-worksheet-contents-larger-than-30-mb"></a>核心工作表內容大於 30 MB 的原因
以下是使得核心工作表內容大於 30 MB 的項目：

* 映像。
* 加上陰影的儲存格。 [移除儲存格陰影格式](https://support.office.com/article/Add-or-change-the-background-color-of-cells-ac10f131-b847-428f-b656-d65375fb815e)。
* 彩色的工作表。 [移除工作表背景](https://support.office.com/article/add-or-remove-a-sheet-background-3577a762-8450-4556-96a2-cc265abc00a8)。
* 文字方塊。
* 美工圖案。

建議您盡可能移除這些項目。 

如果報表包含資料模型，您可有其他選擇： 

* 移除 Excel 工作表中的資料，將它改儲存在資料模型中。 如需詳細資訊，請參閱下文＜移除工作表的資料＞。 
* [建立記憶體有效率的資料模型](https://support.office.com/article/Create-a-memory-efficient-Data-Model-using-Excel-2013-and-the-Power-Pivot-add-in-951c73a9-21c4-46ab-9f5e-14a2833b6a70)來減少報表的整體大小。

若要進行前述任何變更，您必須在 Excel 中編輯活頁簿。

詳細資訊請參閱 [SharePoint Online 的 Excel 活頁簿檔案大小限制](https://support.office.com/article/File-size-limits-for-workbooks-in-SharePoint-Online-9e5bc6f8-018f-415a-b890-5452687b325e)。

## <a name="remove-data-from-worksheets"></a>移除工作表的資料
如果從 [Power Query] 索引標籤或 [Excel 資料] 索引標籤將資料匯入 Excel，此活頁簿在 Excel 資料表和資料模型中可能會有相同的資料。 Excel 工作表中的大型資料表可能會使得核心工作表內容超過 30 MB。 在 Excel 中移除資料表並在資料模型中保存資料，可大幅減少報表的核心工作表內容。 

將資料匯入 Excel 時，請依照下列提示作業：

* **在 Power Query 中**：取消選取 [載入至工作表]  方塊。
  
  資料會只匯入資料模型，Excel 工作表中沒有任何資料。
* **從 [Excel 資料] 索引標籤**，如果您先前在匯入精靈中選取了 [資料表]  ：移至 [現有連線]  \> 按一下連線 \> [只建立連線]  。 刪除於初始匯入期間建立的原始資料表。
* **從 [Excel 資料] 索引標籤**：不要核取 [匯入資料]  方塊中的 [資料表]  。

## <a name="workbook-size-optimizer"></a>活頁簿大小最佳化工具
如果您的活頁簿包含資料模型，您就可以執行活頁簿大小最佳化工具，以減少您的活頁簿大小。 [下載活頁簿大小最佳化工具](https://www.microsoft.com/download/details.aspx?id=38793)。

## <a name="related-info"></a>相關資訊
[建立記憶體效率高的資料模型](https://support.office.com/article/Create-a-memory-efficient-Data-Model-using-Excel-2013-and-the-Power-Pivot-add-in-951c73a9-21c4-46ab-9f5e-14a2833b6a70)

[在 Power BI Desktop 中使用商務用 OneDrive 連結](desktop-use-onedrive-business-links.md)

