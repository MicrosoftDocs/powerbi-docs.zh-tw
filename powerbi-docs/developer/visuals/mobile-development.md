---
title: Power BI 內嵌式分析中，用於取得更佳內嵌 BI 見解的行動裝置開發
description: 如何建立易於行動裝置使用的 Power BI 視覺效果。 使用 Power BI 內嵌式分析，以便取得更佳的內嵌 BI 見解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 03/12/2019
ms.openlocfilehash: 63d2366f91398878af231c8dbb6ed07e8e623a03
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97885537"
---
# <a name="how-to-create-mobile-friendly-power-bi-visuals"></a>如何建立易於行動裝置使用的 Power BI 視覺效果
使用行動裝置在 Power BI 中扮演著重要的角色。 其中一個優點是隨時隨地都能連線到資料。

開發人員在建立 Power BI 視覺效果時，必須盡可能地為大量使用者解決每一種行動裝置的特殊限制，以提供最佳的行動裝置體驗。

使用[適用於 Windows、iOS 和 Android 的 Power BI 應用程式](../../consumer/mobile/mobile-apps-for-mobile-devices.md)，讓商務使用者只要輕輕一按，就能隨時掌握資料的完整觀點。

## <a name="requirements"></a>需求

開發易於行動裝置使用的視覺效果需要滿足下列條件：

- 轉譯

  Power BI 視覺效果必須在所有支援的行動裝置上轉譯 (包括支援的瀏覽器和應用程式)，且要能夠順利地在報表、儀表板中或以 [焦點]  模式執行。 

- 互動式

  互動式功能的提供方式必須與桌面裝置相同。 所有在桌面瀏覽器上處理的事件都必須受到支援，或具有適用於行動裝置的類似事件處理常式。
  
  例如，資料點的基本瀏覽與選取項目，應該要具有與桌面瀏覽器相同的功能。 如果使用 **Ctrl** 進行視覺效果支援多重選取，開發人員就必須考慮為行動裝置新增類似的事件處理常式。

  下表提供行動裝置上的對應事件清單。

  | 滑鼠事件名稱 | 觸控事件名稱 |
  |:----------------:|:----------------:|
  | `click` | `click` |
  | `mousemove` | `touchmove` |
  | `mousedown` | `touchstart` |
  | `mouseup` | `touchend` |
  | `dblclick` | 使用外部程式庫 |
  | `contextmenu` | 使用外部程式庫 |
  | `mouseover` | `touchmove` |
  | `mouseout` | `touchmove` (或外部程式庫) |
  | `wheel` | `NaN` |

  > [!NOTE]
  > 並非所有行動或觸控式螢幕裝置都支援滑鼠 (或具有 *mouse* 前置詞) 事件。 在這種情況下，即會同時處理「滑鼠」  和「觸控」  事件。

## <a name="optional"></a>選用
下列選項可選擇性使用，並用來建立更佳的終端使用者體驗。

- 轉譯

  若要支援規模較小的視覺效果，請嘗試新增可變更的格式選項，讓使用者能夠調整每個項目的大小。 例如，將格式選項新增至標籤，以便在報表和儀表板中使用。 此動作可供使用者針對各自的行動裝置自訂視覺效果。
  
  同樣設定也可套用至桌面瀏覽器中的視覺效果，並在必要時加以覆寫，以調整為較小型螢幕也適用的視覺效果。

  > [!NOTE]
  > 若要最佳化 **焦點** 模式中的視覺效果，則需同時考慮直向與橫向螢幕大小方向，請參閱 [以焦點模式顯示內容](../../consumer/end-user-focus.md)。

- 互動式

  考慮是否新增行動裝置限定的事件處理常式，例如拖曳和滾動。

- 容錯移轉

  視覺效果若無法在行動裝置上轉譯，則會顯示描述性的錯誤。

## <a name="supported-browsers-and-devices"></a>支援的瀏覽器和裝置
Power BI 視覺效果必須在所有支援 Power BI 應用程式的裝置上轉譯。如需詳細資訊，請參閱[支援 Power BI 的瀏覽器](../../fundamentals/power-bi-browsers.md)和 [Power BI 行動裝置應用程式](../../consumer/mobile/mobile-apps-for-mobile-devices.md)。

針對 Windows、iOS 和 Android 裝置的最新模型進行測試時，開發人員需慎重考慮品質層面。

## <a name="next-steps"></a>後續步驟
若要開始使用，請參閱[開發 Power BI 圓形卡片視覺效果](./develop-circle-card.md)。