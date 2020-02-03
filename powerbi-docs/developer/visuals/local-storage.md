---
title: Power BI 視覺效果中的本機存放區 API
description: 本文描述如何使用 Power BI 視覺效果 API 取得瀏覽器本機存放區的存取權
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 01/21/2019
ms.openlocfilehash: 7665f0c8e3c909263f194a0fd54a54ed2a752c8c
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76819092"
---
# <a name="local-storage-api"></a>本機存放區 API

本機存放區 API 是自訂視覺效果可用以要求主機在裝置存放區儲存或載入資料的 API。 為區隔不同視覺效果類型之間的存放區存取權，所以予以隔離。

## <a name="sample"></a>範例

如果自訂視覺效果在每次呼叫 update 方法時都應增加一些計數器，卻又應該保留計數器值，且不在每次視覺效果啓動時重設：

```typescript
export class Visual implements IVisual {
        // ...
        private updateCountName: string = 'updateCount';
        private updateCount: number;
        private storage: ILocalVisualStorageService;
        // ...

        constructor(options: VisualConstructorOptions) {
            // ...
            this.storage = options.host.storageService;
            // ...

            this.storage.get(this.updateCountName).then(count =>
            {
                this.updateCount = +count;
            })
            .catch(() =>
            {
                this.updateCount = 0;
                this.storage.set(this.updateCountName, this.updateCount.toString());
            });
            // ...
        }

        public update(options: VisualUpdateOptions) {
            // ...
            this.updateCount++;
            this.storage.set(this.updateCountName, this.updateCount.toString());
            // ...
        }
}
```

## <a name="known-limitations-and-issues"></a>已知限制及問題

預設不針對自訂視覺效果啟動本機存放區 API。 如果想要針對自己的自訂視覺效果啟動該 API，請將要求傳送給 Power BI 自訂視覺效果支援 (`pbicvsupport@microsoft.com`)。  
**請注意，您的視覺效果應該在 [AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?product=power-bi-visuals) 中提供，且[經過認證](https://powerbi.microsoft.com/en-us/documentation/powerbi-custom-visuals-certified/)。**
