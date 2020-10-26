---
title: supportsKeyboardFocus 功能
description: 此文章說明如何使用 Power BI 視覺效果中的 supportsKeyboardFocus 功能與其需求。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 04/30/2020
ms.openlocfilehash: 1e5a4cf8c80d8123d39fd2ab76898abc0c439ad9
ms.sourcegitcommit: 50b21718a167c2b131313b4135c8034c6f027597
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/14/2020
ms.locfileid: "92049376"
---
# <a name="use-the-supportskeyboardfocus-feature"></a>使用 supportsKeyboardFocus 功能

此文章說明如何在 Power BI 視覺效果中使用 `supportsKeyboardFocus` 功能。
`supportsKeyboardFocus` 功能只允許使用鍵盤瀏覽視覺效果的資料點。

若要深入了解適用於視覺效果的鍵盤瀏覽，請參閱[鍵盤瀏覽](../../create-reports/desktop-accessibility-consuming-tools.md#keyboard-navigation)。

## <a name="example"></a>範例

開啟使用 `supportsKeyboardFocus` 功能的視覺效果。 選取視覺效果中的任何資料點，然後選取 Tab。每次您選取 Tab 時，焦點就會移至下一個資料點。選取 Enter 以選取反白顯示的資料點。

![支援鍵盤焦點範例](./media/supportskeyboardfocus-feature/supports-keyboard-focus-example.png)

## <a name="requirements"></a>需求

此功能需要 API 2.1.0 版或更高版本。

此功能可以套用至影像視覺效果以外的所有視覺效果。

## <a name="usage"></a>使用量

若要使用 `supportsKeyboardFocus` 功能，請將下列程式碼加入至您視覺效果的 *capabilities.json* 檔案。
此功能可讓視覺效果透過鍵盤瀏覽接收焦點。

```json
    {   
            ...
        "supportsKeyboardFocus": true
            ...
    }

```

## <a name="next-steps"></a>後續步驟

若要深入了解協助工具的詳細資訊，請參閱[針對協助工具設計 Power BI 報表](../../create-reports/desktop-accessibility-creating-reports.md)。

若要嘗試進行 Power BI 開發，請參閱[開發 Power BI 圓形卡片視覺效果](develop-circle-card.md)。
