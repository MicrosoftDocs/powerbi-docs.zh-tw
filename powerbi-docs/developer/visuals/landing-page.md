---
title: 在 Power BI 內嵌式分析中，將登陸頁面新增至您的 Power BI 視覺效果，以取得更佳的內嵌 BI 見解
description: 此文章說明如何將登陸頁面新增至 Power BI 視覺效果。 使用 Power BI 內嵌式分析，以便取得更佳的內嵌 BI 見解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 06/18/2019
ms.openlocfilehash: 4381ecf63c0864c4d68e48959efc14baa9d4553b
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97886342"
---
# <a name="add-a-landing-page-to-your-power-bi-visuals"></a>將登陸頁面新增至 Power BI 視覺效果

使用 API 2.3.0，您可以將登陸頁面新增至您的 Power BI 視覺效果。 若要這麼做，請將 `supportsLandingPage` 新增至功能，並將它設定為 true。 在您將資料新增至視覺效果之前，此動作會先將它初始化並更新。 因為視覺效果不再顯示浮水印，所以只要視覺效果沒有資料，您就可以讓它顯示您設計的登陸頁面。

```typescript
export class BarChart implements IVisual {
    //...
    private element: HTMLElement;
    private isLandingPageOn: boolean;
    private LandingPageRemoved: boolean;
    private LandingPage: d3.Selection<any>;

    constructor(options: VisualConstructorOptions) {
            //...
            this.element = options.element;
            //...
    }

    public update(options: VisualUpdateOptions) {
    //...
        this.HandleLandingPage(options);
    }

    private HandleLandingPage(options: VisualUpdateOptions) {
        if(!options.dataViews || !options.dataViews.length) {
            if(!this.isLandingPageOn) {
                this.isLandingPageOn = true;
                const SampleLandingPage: Element = this.createSampleLandingPage(); //create a landing page
                this.element.appendChild(SampleLandingPage);
                this.LandingPage = d3.select(SampleLandingPage);
            }

        } else {
                if(this.isLandingPageOn && !this.LandingPageRemoved){
                    this.LandingPageRemoved = true;
                    this.LandingPage.remove();
                }
        }
    }
```

下列影像顯示範例登陸頁面：

![登陸頁面的螢幕擷取畫面](media/landing-page/app-landing-page.png)
