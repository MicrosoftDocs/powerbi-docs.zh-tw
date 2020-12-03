---
title: 避免在列印編頁報表時出現空白頁面
description: 設計分頁報表以避免列印時顯示空白頁面的指引。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 01/14/2020
ms.openlocfilehash: 0fa886973105bdb4bc8a35f145168c1775ca12cb
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418455"
---
# <a name="avoid-blank-pages-when-printing-paginated-reports"></a>避免在列印編頁報表時出現空白頁面

本文適用於設計 Power BI [分頁報表](../paginated-reports/paginated-reports-report-builder-power-bi.md)的報表作者。 其中提供的建議可協助您在將報表匯出成強制分頁格式 (例如 PDF 或 Microsoft Word) 或列印時避免出現空白頁面。

## <a name="page-setup"></a>版面設定

報表頁面的大小屬性會決定頁面方向、維度和邊界。 存取這些報表屬性的方式：

- 使用報表的 **屬性頁面**：以滑鼠右鍵按一下報表畫布外部的暗灰色區域，然後選取 [報表屬性]  。
- 使用 [[屬性]  ](../paginated-reports/paginated-reports-report-design-view.md#4-properties-pane) 窗格：按一下報表畫布外部的暗灰色區域以選取報表屬性。 確認 [屬性]  窗格已開啟。

在報表的 [屬性]  頁面中，[版面設定]  頁面會提供一個容易使用的介面，供您查看及更新版面設定屬性。

![影像顯示報表屬性視窗，並醒目提示 [版面設定] 頁面。](media/report-paginated-blank-page/report-page-setup-properties.png)

務必正確設定所有頁面大小屬性：

|屬性|建議|
|---------|---------|
|頁面單位|選取相關單位：英吋或公分。|
|方向|選取正確的選項：直向或橫向。|
|紙張大小|選取紙張大小，或指派自訂寬度和高度值。|
|邊界|為左邊、右邊、上面和下面的邊界設定適當值。|
|||

## <a name="report-body-width"></a>報表主體寬度

頁面大小屬性會決定報表物件的可用空間。 報表物件可以是資料區、資料視覺效果或其他報表項目。

輸出空白頁面的常見原因是報表主體寬度「超過可用的頁面空間」  。

您只能使用 [屬性]  窗格來查看和設定報表主體寬度。 首先，按一下報表主體空白區域中的任何位置。

![影像顯示 [屬性] 窗格，並醒目提示報表主體寬度屬性。](media/report-paginated-blank-page/report-body-properties-width.png)

確定寬度值未超過可用的頁面寬度。 遵循下列公式：

```Report body width <= Report page width - (Left margin + Right margin)```

> [!NOTE]
> 當您想要移除的空間中已經有報表物件時，您無法縮小報表主體寬度。 在縮小寬度之前，您必須先重新置放這些物件或調整其大小。
>
> 此外，當您加入新物件或調整現有物件的大小或將其重新置放時，報表主體寬度也會自動增加。 報表設計師一律可擴大主體來容納其內含物件的位置和大小。

## <a name="report-body-height"></a>報表主體高度

輸出空白頁面的另一個原因是，報表主體中最後一個物件的後方有多餘空間。

我們建議您一律降低主體高度，以移除任何尾端空格。

![影像顯示報表設計。 醒目顯示 Tablix 資料區底下的空間，並標示為不必要。](media/report-paginated-blank-page/report-body-remove-trailing-space.png)

## <a name="page-break-options"></a>分頁符號選項

每個資料區域和資料視覺效果都有分頁符號選項。 您可以在其屬性頁面或 [屬性]  窗格中存取這些選項。

請確定未在非必要情況下啟用 [在後方加入分頁符號]  屬性。

![影像顯示 Tablix 屬性視窗。 [在後方加入分頁符號] 屬性已啟用。](media/report-paginated-blank-page/data-region-page-break-option-after.png)

## <a name="consume-container-whitespace"></a>使用容器空白字元

如果空白頁面問題持續發生，您也可以嘗試停用報表的 **ConsumeContainerWhitespace** 屬性。 此作業只能在 [屬性]  窗格中設定。

![影像顯示 [屬性] 窗格，並醒目提示 ConsumeContainerWhitespace 屬性。](media/report-paginated-blank-page/report-properties-consumecontainerwhitespace.png)

此項目預設為啟用。 其指出是否應該使用容器 (例如，報表主體或矩形) 中的最小空白字元。 只有內容右側和下方的空白字元會受到影響。

## <a name="printer-paper-size"></a>印表機紙張大小

最後，如果您要將報表列印成紙張，請確定印表機已載入正確的紙張。 實體紙張大小應對應至[報表紙張大小](#page-setup)。

## <a name="next-steps"></a>後續步驟

如需本文的詳細資訊，請參閱下列資源：

- [什麼是 Power BI Premium 中的編頁報表？](../paginated-reports/paginated-reports-report-builder-power-bi.md)
- [Power BI 分頁報表中的分頁](../paginated-reports/paginated-reports-pagination.md)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com)
