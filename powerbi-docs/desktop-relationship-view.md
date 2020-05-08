---
title: Power BI Desktop 中的模型檢視
description: Power BI Desktop 中的模型檢視
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/17/2020
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: ea568c061142e66e79351de8a6c0f0603a46f775
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "76753209"
---
# <a name="work-with-model-view-in-power-bi-desktop"></a>在 Power BI Desktop 中使用模型檢視

「模型檢視」  會顯示模型中的所有資料表、資料行及關聯性。 此檢視在模型包含許多資料表，且其關聯複雜時十分實用。

選取視窗側邊附近的**模型**圖示，以查看現有的模型檢視。 將游標暫留在關聯性線條上方，以顯示所使用的資料行。

![Power BI Desktop 中的模型檢視](media/desktop-relationship-view/model-view-full-screen.png)

在圖中，*Stores* 資料表具有一個 *StoreKey* 資料行，其與 *Sales* 資料表相關，而該資料表本身也具有一個 *StoreKey* 資料行。 兩個資料表具有「多對一」  (\*:1) 關聯性。 線條中間的箭號顯示篩選內容流向。 雙箭號表示交叉篩選方向設定為「雙向」  。

您可以按兩下關聯性，在 [編輯關聯性]  對話方塊中開啟該關聯性。 若要深入了解關聯性，請參閱[在 Power BI Desktop 中建立和管理關聯性](desktop-create-and-manage-relationships.md).
