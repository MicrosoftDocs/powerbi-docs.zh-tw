---
title: 取得更佳的內嵌式 BI 見解：Power BI 內嵌式分析中的 Power BI 視覺效果進階編輯模式
description: 此文章討論如何在 Power BI 視覺效果中設定進階 UI 控制項。 使用 Power BI 內嵌式分析，取得更佳的內嵌式 BI 見解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 06/18/2019
ms.openlocfilehash: 02f02f23d3dfd7ec514e17d1bab17be715e9cd7d
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97889125"
---
# <a name="advanced-edit-mode-in-power-bi-visuals"></a>Power BI 視覺效果中的進階編輯模式

如果您的 Power BI 視覺效果中需要有進階 UI 控制項，您可以利用進階編輯模式。 當您處於報表編輯模式時，選取 [編輯] 按鈕，將編輯模式設定為 [進階]。 視覺效果可以使用 `EditMode` 旗標來判斷是否應顯示此 UI 控制項。

根據預設，視覺效果不支援進階編輯模式。 如果需要不同的行為，您可以透過設定 `advancedEditModeSupport` 屬性，在視覺效果的 *capabilities.json* 檔案中明確陳述。

可能的值包括：

- `0` - NotSupported

- `1` - SupportedNoAction

- `2` - SupportedInFocus

## <a name="enter-advanced-edit-mode"></a>進入進階編輯模式

下列情況會顯示 [編輯] 按鈕：

* *capabilities.json* 檔案中的 `advancedEditModeSupport` 屬性設定為 `SupportedNoAction` 或 `SupportedInFocus`。

* 視覺效果是以報表編輯模式來檢視。

如果 *capabilities.json* 檔案遺漏 `advancedEditModeSupport` 屬性，或該屬性設定為 `NotSupported`，則不會顯示 [編輯] 按鈕。

![進入編輯模式](media/advanced-edit-mode/edit-mode.png)

當您選取 [編輯] 時，視覺效果會進行 update() 呼叫，並將 EditMode 設為 `Advanced`。 取決於 *capabilities.json* 檔案中設定的值，會發生下列動作：

* `SupportedNoAction`：主機不需要採取進一步的動作。
* `SupportedInFocus`：主機會將視覺效果彈出到焦點模式中。

## <a name="exit-advanced-edit-mode"></a>結束進階編輯模式

下列情況會顯示 [回到報表] 按鈕：

* *capabilities.json* 檔案中的 `advancedEditModeSupport` 屬性設定為 `SupportedInFocus`。
