---
title: Power BI 視覺效果專案結構
description: 本文將說明 Power BI 視覺效果專案的資料夾和檔案結構
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 01/12/2020
ms.openlocfilehash: 74fec4e7fae2fc8630592c435adb42b34c93ef43
ms.sourcegitcommit: 50b21718a167c2b131313b4135c8034c6f027597
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/14/2020
ms.locfileid: "92049353"
---
# <a name="power-bi-visual-project-structure"></a>Power BI 視覺效果專案結構

開始建立新 Power BI 視覺效果的最佳方式，就是使用 Power BI 視覺效果的 [pbiviz](https://www.npmjs.com/package/powerbi-visuals-tools) 工具。

若要建立新的視覺效果，請瀏覽至您想要放置 Power BI 視覺效果的目錄，然後執行命令：

`pbiviz new <visual project name>`

執行此命令會建立包含下列檔案的 Power BI 視覺效果資料夾：

```markdown
project
├───.vscode
│   ├───launch.json
│   └───settings.json
├───assets
│   └───icon.png
├───node_modules
├───src
│   ├───settings.ts
│   └───visual.ts
├───style
│   └───visual.less
├───capabilities.json
├───package-lock.json
├───package.json
├───pbiviz.json
├───tsconfig.json
└───tslint.json
```

## <a name="folder-and-file-description"></a>資料夾和檔案描述

本節會針對 Power BI 視覺效果 **pbiviz** 工具所建立的目錄，提供其中每個資料夾和檔案的資訊。  

### <a name="vscode"></a>.vscode

此資料夾包含 VS Code 專案設定。

若要設定您的工作區，請編輯 `.vscode/settings.json` 檔案。

如需詳細資訊，請參閱[使用者和工作區設定](https://code.visualstudio.com/docs/getstarted/settings)

### <a name="assets"></a>資產

此資料夾包含 `icon.png` 檔案。

Power BI 視覺效果工具會使用此檔案作為 [Power BI 視覺效果] 窗格中的新 Power BI 視覺效果圖示。

### <a name="src"></a>src

此資料夾包含視覺效果的原始程式碼。

在此資料夾中，Power BI 視覺效果工具會建立下列檔案：
* `visual.ts` - 視覺效果的主要原始程式碼。
* `settings.ts` - 視覺效果設定的程式碼。 檔案中的類別會提供用來定義[視覺效果屬性](./objects-properties.md#properties)的介面。

### <a name="style"></a>樣式

此資料夾包含會保存視覺效果樣式的 `visual.less` 檔案。

### <a name="capabilitiesjson"></a>capabilities.json

此檔案包含視覺效果的主要屬性和設定 (或[功能](./capabilities.md))。 此檔案允許視覺效果宣告支援的功能、物件、屬性和[資料檢視對應](./dataview-mappings.md)。

### <a name="package-lockjson"></a>package-lock.json

此檔案會針對 npm 修改 `node_modules` 樹狀結構或 `package.json` 檔案的任何作業自動產生。

如需此檔案的詳細資訊，請參閱官方 [npm-package-lock.json](https://docs.npmjs.com/files/package-lock.json) 文件。

### <a name="packagejson"></a>package.json

此檔案會描述專案套件。 其中包含專案的相關資訊，例如作者、描述和專案相依性。

如需此檔案的詳細資訊，請參閱官方 [npm-package.json](https://docs.npmjs.com/files/package.json.html) 文件。

### <a name="pbivizjson"></a>pbiviz.json

此檔案包含視覺效果中繼資料。

若要檢視 `pbiviz.json` 範例檔案及其中描述中繼資料項目的註解，請參閱[中繼資料項目](#metadata-entries)一節。

### <a name="tsconfigjson"></a>tsconfig.json

[TypeScript](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) 的組態檔。

此檔案必須包含 **\*.ts** 檔案的路徑，也就是視覺效果主要類別 (在 `pbiviz.json` 檔案 `visualClassName` 屬性中指定) 的所在位置。

### <a name="tslintjson"></a>tslint.json

此檔案包含 [TSLint 設定](https://palantir.github.io/tslint/usage/configuration/)。

## <a name="metadata-entries"></a>中繼資料項目

在 `pbiviz.json` 檔案中，下列程式碼標題中的註解會描述中繼資料項目。

> [!NOTE]
> * **pbiciz** 工具從 3.x.x 版開始，不再支援 `externalJS`。
> * 如需當地語系化的支援，[請將 Power BI 地區設定新增至您的視覺效果](./localization.md)。

```json
{
  "visual": {
     // The visual's internal name.
    "name": "<visual project name>",

    // The visual's display name.
    "displayName": "<visual project name>",

    // The visual's unique ID.
    "guid": "<visual project name>23D8B823CF134D3AA7CC0A5D63B20B7F",

    // The name of the visual's main class. Power BI creates the instance of this class to start using the visual in a Power BI report.
    "visualClassName": "Visual",

    // The visual's version number.
    "version": "1.0.0",
    
    // The visual's description (optional)
    "description": "",

    // A URL linking to the visual's support page (optional).
    "supportUrl": "",

    // A link to the source code available from GitHub (optional).
    "gitHubUrl": ""
  },
  // The version of the Power BI API the visual is using.
  "apiVersion": "2.6.0",

  // The name of the visual's author and email.
  "author": { "name": "", "email": "" },

  // 'icon' holds the path to the icon file in the assets folder; the visual's display icon.
  "assets": { "icon": "assets/icon.png" },

  // Contains the paths for JS libraries used in the visual.
  // Note: externalJS' isn't used in the Power BI visuals tool version 3.x.x or higher.
  "externalJS": null,

  // The path to the 'visual.less' style file.
  "style": "style/visual.less",

  // The path to the `capabilities.json` file.
  "capabilities": "capabilities.json",

  // The path to the `dependencies.json` file which contains information about R packages used in R based visuals.
  "dependencies": null,

  // An array of paths to files with localizations.
  "stringResources": []
}
```

## <a name="next-steps"></a>後續步驟

* 若要了解視覺效果、使用者和 Power BI 之間的互動，請參閱 [Power BI 視覺效果概念](./power-bi-visuals-concept.md)。

* 使用[逐步指南](./develop-circle-card.md)，從頭開始開發您自己的 Power BI 視覺效果。
