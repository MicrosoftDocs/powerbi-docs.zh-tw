---
title: 取得更佳的內嵌式 BI 見解：Power BI 內嵌式分析中 Power BI 視覺效果的類型公用程式使用簡介
description: 本文描述如何使用 SVG 公用程式延伸 Power BI 視覺效果的基本類型。 使用 Power BI 內嵌式分析，取得更佳的內嵌式 BI 見解。
author: KesemSharabi
ms.author: kesharab
manager: rkarlin
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: 4f81f55f8d5cfc54020b3b4e02e8be55fb65b0d1
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888113"
---
# <a name="type-utils"></a>類型公用程式

TypeUtils 是擴展 Power BI 視覺效果基本類型的一組函式和類別。

## <a name="installation"></a>安裝

若要安裝套件，您應該在具有目前自訂視覺效果的目錄中執行下列命令：

npm install powerbi-visuals-utils-typeutils --save 此命令會安裝套件，並將該套件新增為 package.json 的相依性

## <a name="double"></a>Double

`Double` 能讓您掌控數值的有效位數。

此課程模組提供下列函式：

### <a name="pow10"></a>pow10

此函式會傳回 10 的乘冪。

```typescript
function pow10(exp: number): number;
```

範例：

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.pow10(25);

// returns: 1e+25
```

### <a name="log10"></a>log10

此函式會傳回該數值以 10 為底數的對數。

```typescript
function log10(val: number): number;
```

範例：

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.log10(25);

// returns: 1
```

## <a name="getprecision"></a>getPrecision

此函式會傳回 10 的乘冪，代表此數值的有效位數。

```typescript
function getPrecision(x: number, decimalDigits?: number): number;
```

範例：

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.getPrecision(562344, 6);

// returns: 0.1
```

### <a name="equalwithprecision"></a>equalWithPrecision

此函式會檢查兩個數值間的差異是否小於所提供有效位數。

```typescript
function equalWithPrecision(x: number, y: number, precision?: number): boolean;
```

範例：

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.equalWithPrecision(1, 1.005, 0.01);

// returns: true
```

### <a name="lesswithprecision"></a>lessWithPrecision

此函式會檢查第一個值是否小於第二個值。

```typescript
function lessWithPrecision(x: number, y: number, precision?: number): boolean;
```

範例：

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.lessWithPrecision(0.995, 1, 0.001);

// returns: true
```

### <a name="lessorequalwithprecision"></a>lessOrEqualWithPrecision

此函式會檢查第一個值是否小於或等於第二個值。

```typescript
function lessOrEqualWithPrecision(x: number, y: number, precision?: number): boolean;
```

範例：

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.lessOrEqualWithPrecision(1.005, 1, 0.01);

// returns: true
```

### <a name="greaterwithprecision"></a>greaterWithPrecision

此函式會檢查第一個值是否大於第二個值。

```typescript
function greaterWithPrecision(x: number, y: number, precision?: number): boolean;
```

範例：

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.greaterWithPrecision(1, 0.995, 0.01);

// returns: false
```

### <a name="greaterorequalwithprecision"></a>greaterOrEqualWithPrecision

此函式會檢查第一個值是否大於或等於第二個值。

```typescript
function greaterOrEqualWithPrecision(x: number, y: number, precision?: number): boolean;
```

範例：

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.greaterOrEqualWithPrecision(1, 1.005, 0.01);

// returns: true
```

### <a name="floorwithprecision"></a>floorWithPrecision

此函式會依提供的有效位數對此數值執行無條件捨去。

```typescript
function floorWithPrecision(x: number, precision?: number): number;
```

範例：

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.floorWithPrecision(5.96, 0.001);

// returns: 5
```

### <a name="ceilwithprecision"></a>ceilWithPrecision

此函式會依提供的有效位數對此數值執行 `ceils`。

```typescript
function ceilWithPrecision(x: number, precision?: number): number;
```

範例：

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ceilWithPrecision(5.06, 0.001);

// returns: 6
```

### <a name="floortoprecision"></a>floorToPrecision

此函式會將此數值無條件捨去到提供的有效位數。

```typescript
function floorToPrecision(x: number, precision?: number): number;
```

範例：

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.floorToPrecision(5.96, 0.1);

// returns: 5.9
```

### <a name="ceiltoprecision"></a>ceilToPrecision

此函式會將此數值 `ceils` 到提供的有效位數。

```typescript
function ceilToPrecision(x: number, precision?: number): number;
```

範例：

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ceilToPrecision(-506, 10);

// returns: -500
```

### <a name="roundtoprecision"></a>roundToPrecision

此函式會將此數值四捨五入到提供的有效位數。

```typescript
function roundToPrecision(x: number, precision?: number): number;
```

範例：

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.roundToPrecision(596, 10);

// returns: 600
```

### <a name="ensureinrange"></a>ensureInRange

此函式會傳回介於最小值和最大值之間的數值。

```typescript
function ensureInRange(x: number, min: number, max: number): number;
```

範例：

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.ensureInRange(-27.2, -10, -5);

// returns: -10
```

### <a name="round"></a>round

此函式會四捨五入此數值。

```typescript
function round(x: number): number;
```

範例：

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.round(27.45);

// returns: 27
```

### <a name="removedecimalnoise"></a>removeDecimalNoise

此函式會移除小數點後尾隨的零。

```typescript
function removeDecimalNoise(value: number): number;
```

範例：

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.removeDecimalNoise(21.493000000000002);

// returns: 21.493
```

### <a name="isinteger"></a>isInteger

此函式會檢查數值是否為整數。

```typescript
function isInteger(value: number): boolean;
```

範例：

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.isInteger(21.493000000000002);

// returns: false
```

### <a name="toincrement"></a>toIncrement

此函式會依提供的數值遞增數值，並傳回四捨五入的數值。

```typescript
function toIncrement(value: number, increment: number): number;
```

範例：

```typescript
import { double } from "powerbi-visuals-utils-typeutils";
// ...

double.toIncrement(0.6383723, 0.05);

// returns: 0.65
```

## <a name="prototype"></a>原型

`Prototype` 能讓您繼承物件。

此課程模組提供下列函式：

## <a name="inherit"></a>inherit

此函式會傳回以所提供物件為原型的新物件。

```typescript
function inherit<T>(obj: T, extension?: (inherited: T) => void): T;
```

範例：

```typescript
import { prototype } from "powerbi-visuals-utils-typeutils";
// ...

let base = { Microsoft: "Power BI" };

prototype.inherit(base);

/* returns: {
    __proto__: {
        Microsoft: "Power BI"
    }
}*/
```

## <a name="inheritsingle"></a>inheritSingle

此函式只會在原型未經設定的情況下，傳回以所提供物件為原型的新物件。

```typescript
function inheritSingle<T>(obj: T): T;
```

範例：

```typescript
import { prototype } from "powerbi-visuals-utils-typeutils";
// ...

let base = { Microsoft: "Power BI" };

prototype.inheritSingle(base);

/* returns: {
    __proto__: {
        Microsoft: "Power BI"
    }
}*/
```

## <a name="pixelconverter"></a>PixelConverter

`PixelConverter` 能讓您將像素轉換成點，並將點轉換成像素。

此課程模組提供下列函式：

## <a name="tostring"></a>toString

此函式會將素值轉換成字串。

```typescript
function toString(px: number): string;
```

範例：

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.toString(25);

// returns: 25px
```

## <a name="frompoint"></a>fromPoint

此函式會將提供的點值轉換成像素值，並傳回轉譯的字串。

```typescript
function fromPoint(pt: number): string;
```

範例：

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.fromPoint(8);

// returns: 33.33333333333333px
```

## <a name="frompointtopixel"></a>fromPointToPixel

此函式會將提供的點值轉換成像素值。

```typescript
function fromPointToPixel(pt: number): number;
```

範例：

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.fromPointToPixel(8);

// returns: 10.666666666666666
```

## <a name="topoint"></a>toPoint

此函式會將像素值轉換成點值。

```typescript
function toPoint(px: number): number;
```

範例：

```typescript
import { pixelConverter } from "powerbi-visuals-utils-typeutils";
// ...

pixelConverter.toPoint(8);

// returns: 6
```
