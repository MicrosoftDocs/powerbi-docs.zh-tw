---
title: Power BI 視覺效果 API 變更記錄
description: 此文章說明不同版本 Power BI 視覺效果 API 的主要變更
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 03/13/2019
ms.openlocfilehash: c43542bc6c2bb0699403062f68024f9718bbbb60
ms.sourcegitcommit: 54e571a10b0fdde5cd6036017eac9ef228de5116
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501941"
---
# <a name="power-bi-visuals-api-changelog"></a>Power BI 視覺效果 API 變更記錄
此頁面包含 API 版本的快速摘要。 此處所列的版本會視為穩定，且不會變更。


## <a name="api-v340"></a>API v3.4.0
  * `fetchMoreData`：新的 `aggregateSegments` 參數 (預設為 true)，用於支援無彙總 fetchMoreData

## <a name="api-v320"></a>API v3.2.0
  * 支援 **[supportsMultiVisualSelection](./supportsmultivisualselection-feature.md)**

## <a name="api-v260"></a>API v2.6.0
  * 加入 **isInFocus** 以更新選項，並將 **switchFocusModeState** 方法加入至視覺效果主機
  * 支援 **小計** 自訂

## <a name="api-v250"></a>API v2.5.0
  * 支援[分析窗格](./analytics-pane.md)
  * 支援 `SelectionIdBuilder` **withMatrixNode** 與 **withTable** 方法
  * 不再支援 `DataRepetitionSelector` 介面，已由 `data.CustomVisualOpaqueIdentity` 介面取代

## <a name="api-v230"></a>API v2.3.0
  * **[登陸頁面 API](./landing-page.md)**
  * **[本機儲存體 API](./local-storage.md)**
  * **[Tuple 篩選 API (多個資料行篩選)](./filter-api.md#the-tuple-filter-api-multi-column-filter)**
  * **[轉譯事件 API](./event-service.md#render-events-in-power-bi-visuals)**

## <a name="api-v220"></a>API v2.2.0
  * 支援 **[從 DataView 還原 JSON 篩選](./filter-api.md#restore-the-json-filter-from-the-data-view)**
  * **[ContextMenu API](./context-menu.md)**

## <a name="api-v210"></a>API v2.1.0
  * 效能增強功能：
    * 載入時間更快
    * 較小的記憶體使用量
    * 最佳化的資料與事件交易  

**版本資訊**
* 重構的篩選 API 將在 API 2.2 中提供，而在 API 2.1 中不受支援。
* 視覺效果只會接收其功能中所宣告的 dataView 類型。 使用多個 dataView 類型的視覺效果將因此更新而中斷。
* 不再支援 `DataViewScopeIdentity` 介面，已由為 `data.DataRepetitionSelector` 介面取代。 如果您使用 `DataViewScopeIdentity` 介面的機碼屬性，您可以將其取代為 `JSON.stringify(identity)`
* `undefined` 已由 dataView 內的 `null` 取代。 使用 `var item in myArray` 逐一查看陣列時，其會略過 `undefined`，但不會略過 `null`。 此更新可能會中斷使用此模式的視覺效果。 請務必檢查陣列中的 `null`：
   ```typescript
   for (var item in myArray) {
     if (!item) {
       continue;
     }
     console.log(item);
   }
   ```
* `proto` 屬性不會再將隱藏的 metadata\data 儲存在 dataView 內。 透過 `proto` 存取屬性的視覺效果，可能因此更新而中斷。

## <a name="api-v1130"></a>API v1.13.0
* 支援 **[同步處理交叉分析篩選器](./enable-sync-slicers.md)** ，請注意，由於 PBI 目前程式碼狀態，這僅適用於單一欄位交叉分析篩選器， [深入了解](../../visuals/power-bi-visualization-slicers.md)。
* 協助工具：[高對比支援](./high-contrast-support.md) 
* 協助工具：允許鍵盤焦點旗標

## <a name="api-v1120"></a>API v1.12.0
* 支援佈景主題
* 支援 **[fetchMoreData](./fetch-more-data.md)** ，請注意， **擷取更多資料 API** 克服了 30K 個資料點的硬限制
* **[畫布工具提示 API](./add-tooltips.md#add-report-page-tooltips)**

## <a name="api-v1110"></a>API v1.11.0
* **[FilterManager API](./filter-api.md)**
* 支援 **[書籤](./bookmarks-support.md)** 

## <a name="api-v1100"></a>API v1.10.0
* 加入 `ILocalizationManager`
* **驗證 API**

## <a name="api-v190"></a>API v1.9.0
* **[launchUrl API](./launch-url.md)**

## <a name="api-v180"></a>API v1.8.0
* 支援功能結構描述中的新類型 **fillRule** (漸層)
* 支援物件屬性之功能結構描述中的 **規則** 屬性

## <a name="api-v170"></a>API v1.7.0
* 支援 **[RESJSON](./localization.md#resource-file)**

## <a name="api-v162"></a>API 1.6.2 版
* 支援 **[編輯模式](./advanced-edit-mode.md)** ，讓視覺效果進入視覺化編輯模式
* 支援以 html 為基礎的 **[互動式 (html) R Power BI 視覺效果](https://github.com/Microsoft/PowerBI-visuals/blob/master/RVisualTutorial/CreateRHTML.md)**

## <a name="api-v150"></a>API 1.5.0 版
* 支援 **[允許互動](./visuals-interactions.md)** 以實現視覺效果互動性

## <a name="api-v140"></a>API 1.4.0 版
* 支援 **[當地語系化](./localization.md)**

## <a name="api-v130"></a>API 1.3.0 版
* 支援 **[工具提示](./add-tooltips.md)**

## <a name="api-v120"></a>API 1.2.0 版
* 新增 **colorPalette** ，以管理您視覺效果上所使用的色彩。
* 支援 **多重選取項目** - selectionManager 可以接受 `SelectionId` 的陣列。
* 支援使用 R 指令碼的 **[R 視覺效果](https://github.com/Microsoft/PowerBI-visuals/blob/master/RVisualTutorial/CreateRHTML.md)**

## <a name="api-v110"></a>API 1.1.0 版
* 支援在 iFrame 中針對視覺效果進行偵錯
* 新增輕量沙箱，以更快地初始化 iFrame
* 修正 [Capabilities.objects 不支援 "text" 類型](https://github.com/Microsoft/PowerBI-visuals-tools/issues/12) \(英文\) 的問題
* 支援 `pbiviz update` 以更新視覺效果 API 類型定義與結構描述
* 支援 `pbiviz new` 中的 `--api-version` 旗標，以使用特定的 API 版本建立視覺效果
* 支援 API 1.2.0 版的 Alpha 版本

**視覺效果主機**
* 新增 **createSelectionIdBuilder** ，以建立用於資料選擇的唯一識別碼
* 新增 **createSelectionManager** 來管理視覺效果的選取狀態，並將變更傳達給視覺效果主機
* 新增用於視覺效果中的預設 **色彩** 陣列

## <a name="api-v100"></a>API 1.0.0 版
* 初始 API 版本
