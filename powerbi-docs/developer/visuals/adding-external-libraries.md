---
title: 取得更佳的內嵌式 BI 見解：在 Power BI 內嵌式分析中新增外部程式庫到 Power BI 視覺效果
description: 此文章說明如何在 Power BI 視覺效果中使用外部程式庫。 使用 Power BI 內嵌式分析，取得更佳的內嵌式 BI 見解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 02/24/2020
ms.openlocfilehash: b9a443040384e4d38bd7440eae0a5582cc422836
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97889171"
---
# <a name="adding-external-libraries"></a>新增外部程式庫

此文章說明如何在 Power BI 視覺效果中使用外部程式庫。 其中包含從 Power BI 視覺效果的程式碼安裝、匯入及呼叫外部程式庫的相關資訊。

## <a name="javascript-libraries"></a>JavaScript 程式庫

1. 使用任何套件管理員 (例如 *npm* 或 *yarn*) 來安裝外部 JavaScript 程式庫。
2. 使用外部程式庫，將所需的模組匯入來源檔案。

>[!NOTE]
>如果您想要將輸入新增至 JavaScript 程式庫，並取得 IntelliSense 與編譯時間的安全性，請確定您已安裝適當的套件。

### <a name="installing-the-d3-library"></a>安裝 d3 程式庫

這是使用 [npm](https://www.npmjs.com/) \(英文\) 安裝 [d3 程式庫](https://www.npmjs.com/package/d3) \(英文\) 與 [@types/d3](https://www.npmjs.com/package/@types/d3) \(英文\) 套件的範例。

如需完整範例，請參閱 [Power BI 視覺效果](https://github.com/microsoft/powerbi-visuals-gantt/blob/master/src/gantt.ts#L29) \(英文\) 程式碼。

1. 安裝 *d3* 套件與 *d3 類型* 套件。

    ```powershell
    npm install d3@5 --save
    npm install @types/d3@5 --save
    ```

2. 在加以使用的檔案中匯入 *d3* 程式庫，例如 `visual.ts`。

    ```typescript
    import * as d3 from "d3";
    ```

## <a name="css-framework"></a>CSS 架構

1. 使用任何套件管理員 (例如 *npm* 或 *yarn*) 來安裝外部 CSS 架構。
2. 在視覺效果的 `.less` 檔案中，包含 `import` 陳述式。

### <a name="installing-bootstrap"></a>安裝啟動程序

這是使用 [npm](https://www.npmjs.com/) \(英文\) 安裝[啟動程序](https://www.npmjs.com/package/bootstrap) \(英文\) 的範例。

如需完整範例，請參閱 [Power BI 視覺效果](https://github.com/Microsoft/powerbi-visuals-sankey/blob/c8200da56913cd8b253be949a35fad0f4472b6de/style/visual.less#L32) \(英文\) 程式碼。

1. 安裝 *啟動程序* 套件。

    ```powershell
    npm install bootstrap --save
    ```

2. 在 `visual.less` 中包含 `import` 陳述式。

    ```less
    @import (less) "node_modules/bootstrap/dist/css/bootstrap.css";
    ```
