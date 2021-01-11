---
title: 取得更佳的內嵌式 BI 見解：在 Power BI 內嵌式分析中新增操作功能表到 Power BI 視覺效果
description: 了解如何將操作功能表新增至 Power BI 視覺效果。 使用 Power BI 內嵌式分析，取得更佳的內嵌式 BI 見解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
manager: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 06/18/2019
ms.openlocfilehash: 1c19ba94588628e002cdb9e65f59bd4182020e1c
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888688"
---
# <a name="add-context-menu-to-power-bi-visual"></a>將操作功能表新增至 Power BI 視覺效果

您可以使用 `selectionManager.showContextMenu()` 搭配參數 `selectionId` 和位置 (作為 `{x:, y:}` 物件)，讓 Power BI 顯示視覺效果的操作功能表。

> [!IMPORTANT]
> `selectionManager.showContextMenu()` 是在視覺效果 API 2.2.0 中引進。

通常會新增為以滑鼠右鍵按一下的事件 (或長按觸控裝置) 操作功能表已新增至範例橫條圖以供參考：

```typescript
    public update(options: VisualUpdateOptions) {
        //...
        //handle context menu
        this.svg.on('contextmenu', () => {
            const mouseEvent: MouseEvent = d3.event as MouseEvent;
            const eventTarget: EventTarget = mouseEvent.target;
            let dataPoint = d3.select(eventTarget).datum();
            this.selectionManager.showContextMenu(dataPoint? dataPoint.selectionId : {}, {
                x: mouseEvent.clientX,
                y: mouseEvent.clientY
            });
            mouseEvent.preventDefault();
        });
```
