---
title: 在 Power BI 內嵌式分析的 Power BI 視覺效果中，使用 SVG 公用程式以取得更佳內嵌 BI 見解的簡介
description: 本文描述如何使用 SVG 公用程式以簡化 Power BI 視覺效果的 SVG 操作。 使用 Power BI 內嵌式分析，以便取得更佳的內嵌 BI 見解。
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: cf798ae13d874e354f6941d50982bfe26d73424d
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887745"
---
# <a name="svg-utils"></a>SVG 公用程式

SVG 公用程式是可簡化 Power BI 視覺效果 SVG 操作的一組函式和類別

## <a name="installation"></a>安裝

若要安裝套件，您應該在具有目前視覺效果的目錄中執行下列命令：

```bash
npm install powerbi-visuals-utils-svgutils --save
```

## <a name="cssconstants"></a>CssConstants

`CssConstants` 模組提供可搭配類別選取器使用的特殊函式和介面。

`powerbi.extensibility.utils.svg.CssConstants` 模組提供下列函式與介面：

## <a name="classandselector"></a>ClassAndSelector

此介面描述類別選取器的通用屬性。

```typescript
interface ClassAndSelector {
  class: string;
  selector: string;
}
```

### <a name="createclassandselector"></a>createClassAndSelector

此函式會使用指定的類別名稱建立 ClassAndSelector 執行個體。

```typescript
function createClassAndSelector(className: string): ClassAndSelector;
```

範例：

```typescript
import { CssConstants } from "powerbi-visuals-utils-svgutils";
import createClassAndSelector = CssConstants.createClassAndSelector;
import ClassAndSelector = CssConstants.ClassAndSelector;

let divSelector: ClassAndSelector = createClassAndSelector("sample-block");

divSelector.selector === ".sample-block"; // returns: true
divSelector.class === "sample-block"; // returns: true
```

## <a name="manipulation"></a>manipulation

`manipulation` 提供一些特殊的函式來產生搭配 SVG 轉換屬性使用的字串。

此課程模組提供下列函式：

### <a name="translate"></a>translate

此函式會建立搭配 SVG 轉換屬性使用的轉譯字串。

```typescript
function translate(x: number, y: number): string;
```

範例：

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translate(100, 100);

// returns: translate(100,100)
```

### <a name="translatexwithpixels"></a>translateXWithPixels

此函式會建立搭配 SVG 轉換屬性使用的 translateX 字串。

```typescript
function translateXWithPixels(x: number): string;
```

範例：

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translateXWithPixels(100);

// returns: translateX(100px)
```

### <a name="translatewithpixels"></a>translateWithPixels

此函式會建立搭配 SVG 轉換屬性使用的轉譯字串。

```typescript
function translateWithPixels(x: number, y: number): string;
```

範例：

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translateWithPixels(100, 100);

// returns: translate(100px,100px)
```

### <a name="translateandrotate"></a>translateAndRotate

此函式會建立搭配 SVG 轉換屬性使用的平移旋轉字串。

```typescript
function translateAndRotate(
  x: number,
  y: number,
  px: number,
  py: number,
  angle: number
): string;
```

範例：

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.translateAndRotate(100, 100, 50, 50, 35);

// returns: translate(100,100) rotate(35,50,50)
```

### <a name="scale"></a>級別

此函式會建立搭配 CSS 轉換屬性使用的調整規模字串。

```typescript
function scale(scale: number): string;
```

範例：

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.scale(50);

// returns: scale(50)
```

### <a name="transformorigin"></a>transformOrigin

此函式會建立搭配 CSS transform-origin 屬性使用的以原點為中心轉換字串。

```typescript
function transformOrigin(xOffset: string, yOffset: string): string;
```

範例：

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.transformOrigin(5, 5);

// returns: 5 5
```

### <a name="flushalld3transitions"></a>flushAllD3Transitions

此函式會強制完成每項 D3 轉換。

```typescript
function flushAllD3Transitions(): void;
```

範例：

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.flushAllD3Transitions();

// forces every transition of D3 to complete
```

### <a name="parsetranslatetransform"></a>parseTranslateTransform

此函式會剖析值為 "translate(x,y)" 的轉換字串。

```typescript
function parseTranslateTransform(input: string): { x: string; y: string };
```

範例：

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.parseTranslateTransform("translate(100px,100px)");

// returns: { "x":"100px", "y":"100px" }
```

### <a name="createarrow"></a>createArrow

此函式會建立箭號。

```typescript
function createArrow(
  width: number,
  height: number,
  rotate: number
): { path: string; transform: string };
```

範例：

```typescript
import { manipulation } from "powerbi-visuals-utils-svgutils";
// ...

manipulation.createArrow(10, 20, 5);

/* returns: {
    "path": "M0 0L0 20L10 10 Z",
    "transform": "rotate(5 5 10)"
}*/
```

## <a name="rect"></a>Rect

`Rect` 模組會提供一些操控矩形的特殊函式。

此課程模組提供下列函式：

### <a name="getoffset"></a>getOffset

此函式會傳回矩形的位移。

```typescript
function getOffset(rect: IRect): IPoint;
```

範例：

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getOffset({ left: 25, top: 25, width: 100, height: 100 });

/* returns: {
    x: 25,
    y: 25
}*/
```

### <a name="getsize"></a>getSize

此函式會傳回矩形的大小。

```typescript
function getSize(rect: IRect): ISize;
```

範例：

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getSize({ left: 25, top: 25, width: 100, height: 100 });

/* returns: {
    width: 100,
    height: 100
}*/
```

### <a name="setsize"></a>setSize

此函式會修改矩形的大小。

```typescript
function setSize(rect: IRect, value: ISize): void;
```

範例：

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

let rectangle = { left: 25, top: 25, width: 100, height: 100 };

Rect.setSize(rectangle, { width: 250, height: 250 });

// rectangle === { left: 25, top: 25, width: 250, height: 250 }
```

### <a name="right"></a>向右

此函式會傳回矩形的右邊位置。

```typescript
function right(rect: IRect): number;
```

範例：

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.right({ left: 25, top: 25, width: 100, height: 100 });

// returns: 125
```

### <a name="bottom"></a>下

此函式會傳回矩形的底部位置。

```typescript
function bottom(rect: IRect): number;
```

範例：

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.bottom({ left: 25, top: 25, width: 100, height: 100 });

// returns: 125
```

### <a name="topleft"></a>topLeft

此函式會傳回矩形的左上位置。

```typescript
function topLeft(rect: IRect): IPoint;
```

範例：

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.topLeft({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 25, y: 25 }
```

### <a name="topright"></a>topRight

此函式會傳回矩形的右上位置。

```typescript
function topRight(rect: IRect): IPoint;
```

範例：

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.topRight({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 125, y: 25 }
```

### <a name="bottomleft"></a>bottomLeft

此函式會傳回矩形的左下位置。

```typescript
function bottomLeft(rect: IRect): IPoint;
```

範例：

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.bottomLeft({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 25, y: 125 }
```

### <a name="bottomright"></a>bottomRight

此函式會傳回矩形的右下位置。

```typescript
function bottomRight(rect: IRect): IPoint;
```

### <a name="example"></a>範例

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.bottomRight({ left: 25, top: 25, width: 100, height: 100 });

// returns: { x: 125, y: 125 }
```

### <a name="clone"></a>clone

此函式會建立矩形的複本。

```typescript
function clone(rect: IRect): IRect;
```

範例：

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.clone({ left: 25, top: 25, width: 100, height: 100 });

/* returns: {
    left: 25, top: 25, width: 100, height: 100}
*/
```

### <a name="tostring"></a>toString

此函式會將矩形轉換成字串。

```typescript
function toString(rect: IRect): string;
```

範例：

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.toString({ left: 25, top: 25, width: 100, height: 100 });

// returns: {left:25, top:25, width:100, height:100}
```

### <a name="offset"></a>Offset

此函式會將指定的位移套用至矩形。

```typescript
function offset(rect: IRect, offsetX: number, offsetY: number): IRect;
```

範例：

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.offset({ left: 25, top: 25, width: 100, height: 100 }, 50, 50);

/* returns: {
    left: 75,
    top: 75,
    width: 100,
    height: 100
}*/
```

### <a name="add"></a>add

此函式會將第一個矩形新增至第二個矩形。

```typescript
function add(rect: IRect, rect2: IRect): IRect;
```

範例：

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.add(
  { left: 25, top: 25, width: 100, height: 100 },
  { left: 50, top: 50, width: 75, height: 75 }
);

/* returns: {
    left: 75,
    top: 75,
    height: 175,
    width: 175
}*/
```

### <a name="getclosestpoint"></a>getClosestPoint

此函式會傳回矩形上最接近指定點的點。

```typescript
function getClosestPoint(rect: IRect, x: number, y: number): IPoint;
```

範例：

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getClosestPoint({ left: 0, top: 0, width: 100, height: 100 }, 50, 50);

/* returns: {
    x: 50,
    y: 50
}*/
```

### <a name="equal"></a>equal

此函式會比較矩形，如果矩形相同則傳回 true。

```typescript
function equal(rect1: IRect, rect2: IRect): boolean;
```

範例：

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.equal(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 50, top: 50, width: 100, height: 100 }
);

// returns: false
```

### <a name="equalwithprecision"></a>equalWithPrecision

此函式會考慮值的有效位數以比較矩形。

```typescript
function equalWithPrecision(rect1: IRect, rect2: IRect): boolean;
```

範例：

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.equalWithPrecision(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 50, top: 50, width: 100, height: 100 }
);

// returns: false
```

### <a name="isempty"></a>isEmpty

此函式會檢查矩形是否為空白。

```typescript
function isEmpty(rect: IRect): boolean;
```

範例：

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.isEmpty({ left: 0, top: 0, width: 0, height: 0 });

// returns: true
```

### <a name="containspoint"></a>containsPoint

此函式會檢查矩形是否包含點。

```typescript
function containsPoint(rect: IRect, point: IPoint): boolean;
```

範例：

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.containsPoint(
  { left: 0, top: 0, width: 100, height: 100 },
  { x: 50, y: 50 }
);

// returns: true
```

### <a name="isintersecting"></a>isIntersecting

此函式會檢查矩形是否與其他物件相交。

```typescript
function isIntersecting(rect1: IRect, rect2: IRect): boolean;
```

範例：

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.isIntersecting(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 0, top: 0, width: 50, height: 50 }
);

// returns: true
```

### <a name="intersect"></a>intersect

此函式會傳回矩形的交集。

```typescript
function intersect(rect1: IRect, rect2: IRect): IRect;
```

範例：

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.intersect(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 0, top: 0, width: 50, height: 50 }
);

/* returns: {
    left: 0,
    top: 0,
    width: 50,
    height: 50
}*/
```

### <a name="combine"></a>combine

此函式會合併矩形。

```typescript
function combine(rect1: IRect, rect2: IRect): IRect;
```

範例：

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.combine(
  { left: 0, top: 0, width: 100, height: 100 },
  { left: 0, top: 0, width: 50, height: 120 }
);

/* returns: {
    left: 0,
    top: 0,
    width: 100,
    height: 120
}*/
```

### <a name="getcentroid"></a>getCentroid

此函式會傳回矩形的中心點。

```typescript
function getCentroid(rect: IRect): IPoint;
```

範例：

```typescript
import { shapes } from "powerbi-visuals-utils-svgutils";
import Rect = shapes.Rect;
// ...

Rect.getCentroid({ left: 0, top: 0, width: 100, height: 100 });

/* returns: {
    x: 50,
    y: 50
}*/
```

## <a name="pointer"></a>指標

`pointer` 模組會提供取得指標位置的特殊函式。

此模組提供下列函式：

### <a name="getcoordinates"></a>getCoordinates

此函式會傳回指標的位置。

```typescript
function getCoordinates(rootNode: Element, isPointerEvent: boolean): number[];
```

範例：

```typescript
import { pointer } from "powerbi-visuals-utils-svgutils";

let bodySelection = d3.select("body");

bodySelection
  .append("div")
  .style({
    width: "100px",
    height: "100px",
    "background-color": "green"
  })
  .on("click", () => {
    pointer.getCoordinates(bodySelection.node(), true);
  });

// click element, after that you will get position of the pointer
```
