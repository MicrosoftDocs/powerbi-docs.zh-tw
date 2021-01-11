---
title: Power BI 內嵌式分析中，用於取得更佳內嵌 BI 見解的效能提示
description: 如何建置高效能的 Power BI 視覺效果。 使用 Power BI 內嵌式分析，以便取得更佳的內嵌 BI 見解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 04/20/2020
ms.openlocfilehash: c8bcf5e13ba769b976ab123adb3ba37f46b0359e
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97885928"
---
# <a name="how-to-build-a-high-performance-power-bi-visual"></a>如何建置高效能的 Power BI 視覺效果
本文將探討開發人員如何在轉譯視覺效果時達到高效能的技術。 

沒有人希望轉譯時視覺效果費時呈現，也不希望在轉譯時，可從程式碼中發揮最大效能變得很重要。 

> [!NOTE]
> 我們在持續改善和增強平台的過程中，會一直發行新版本的 API。 為能充分運用 Power BI 視覺效果的平台和功能集，建議隨時更新到最新的版本。
>
> 在最新的 **版本 2.1** 中，Power BI 的視覺效果載入時間平均改善了 20%。

## <a name="power-bi-visual-performance-tips"></a>Power BI 視覺效果效能祕訣
以下是有關如何達到最佳視覺效果效能的一些建議。 

### <a name="use-user-timing-api"></a>使用使用者計時 API
使用 **使用者計時 API** 來測量應用程式的 JavaScript 效能，可有助判斷指令碼的哪些部分需要最佳化。

如需詳細資訊，請參閱[使用者計時 API](https://msdn.microsoft.com/library/hh772738(v=vs.85).aspx)。

### <a name="review-animation-loops"></a>檢閱動畫迴圈
動畫迴圈會重新繪製未變更的項目嗎？ 

 - 問題：逐畫面繪製未變更的項目很浪費時間。

 - 解決方案：請選擇性地更新畫面。 
 
當想要建立靜態視覺效果的動畫時，建議將繪製程式碼一次全部放入一個 update 函式，然後重複使用動畫迴圈其每次反覆運算的新資料來進行呼叫。

不要考慮下列更新模式，請改為使用視覺化建構函式方法來繪製所有靜態項目，然後 update 函式只需要繪製變更的視覺效果項目。 

   > [!TIP]
   > 沒有效率的動畫迴圈常見於軸和圖例。

### <a name="cache-dom-nodes"></a>快取 DOM 節點 
從 DOM 擷取節點或節點清單時，必須考慮其能否在後續的計算中重複使用 (有時甚至是下一個迴圈反覆運算)。 只要不必在相關區域中新增或刪除其他節點，快取節點即可改善應用程式的整體效率。

為確保程式碼快速且不會拖慢瀏覽器速度，請保持最低限度的 DOM 存取。 

- 之前： 

   ```javascript
   public update(options: VisualUpdateOptions) { 
       let axis = $(".axis"); 
   }
   ```

- 之後： 

   ```javascript
   public constructor(options: VisualConstructorOptions) { 
       this.$root = $(options.element); 
       this.xAxis = this.$root.find(".xAxis"); 
   } 
 
   public update(options: VisualUpdateOptions) { 
       let axis = this.axis; 
   }
   ```

### <a name="avoid-dom-manipulation"></a>避免 DOM 操作 
盡可能限制 DOM 操作。  插入 `prepend()`、`append()` 和 `after()` 等作業非常耗時，除非必要，否則不建議使用。

例如：

  ```javascript
  for (let i=0; i<1000; i++) { 
      $('#list').append('<li>'+i+'</li>');
  }
  ```

使用 `html()` 並事先建置清單可加快上述範例的速度： 

  ```javascript
  let list = ''; 
  for (let i=0; i<1000; i++) { 
      list += '<li>'+i+'</li>'; 
  } 

  $('#list').html(list); 
  ```

### <a name="reconsider-jquery"></a>重新考慮 JQuery

限制 JS 架構並盡可能使用原生 JS，可增加可用的頻寬並減少處理額外負荷。 這也會限制舊版瀏覽器的相容性問題。 

如需詳細資訊，請參閱 [youmightnotneedjquery.com](http://youmightnotneedjquery.com/) 以取得函式替代範例，例如 JQuery 的 `show`、`hide`、`addClass` 等。  

### <a name="use-canvas-or-webgl"></a>使用 canvas 或 WebGL 
如需重複使用動畫，請考慮使用 **Canvas** 或 **WebGL**，而非 SVG。 與 SVG 不同，使用這些選項時，效能取決於大小而非內容。 

您可在 [SVG 與畫布：如何選擇](/previous-versions/windows/internet-explorer/ie-developer/samples/gg193983(v=vs.85)) (英文) 一文中深入了解兩者的差異。 

### <a name="use-requestanimationframe-instead-of-settimeout"></a>使用 requestAnimationFrame 而非 setTimeout 
如果使用 [requestAnimationFrame](https://www.w3.org/TR/animation-timing/) 更新螢幕動畫，則在瀏覽器呼叫另一個重繪 **之前**，會先呼叫動畫函式。

如需詳細資訊，請參閱使用 `requestAnimationFrame` 順暢處理動畫的此[範例](https://testdrive-archive.azurewebsites.net/Graphics/RequestAnimationFrame/Default.html)。

## <a name="next-steps"></a>後續步驟

在 [Power BI 最佳化指南](../../guidance/power-bi-optimization.md)中深入了解最佳化技術。