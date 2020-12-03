---
title: Power BI Desktop 中的資料分類
description: Power BI Desktop 中的資料分類
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: how-to
ms.date: 01/15/2020
LocalizationGroup: Model your data
ms.openlocfilehash: d99eb0355d414a9e1627da0b5629eaf45cbaf18d
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415787"
---
# <a name="specify-data-categories-in-power-bi-desktop"></a>在 Power BI Desktop 中指定資料類別
在 Power BI Desktop 中，您可以指定資料行的「資料類別」，讓 Power BI Desktop 知道如何在視覺效果中處理其值。

當 Power BI Desktop 匯入資料時，會取得資料以外的其他資訊，例如資料表和資料行名稱，以及資料是否為主索引鍵。 有了該資訊之後，Power BI Desktop 便可做出某種程度的假設，讓您在建立視覺效果時可以有最佳的預設體驗。
例如，當某個資料行具有數字值時，您可能會想要以某種方式進行彙總，所以 Power BI Desktop 會將資料行置於 [視覺效果] 窗格的 [值] 區域中。 或者，針對資料行在折線圖上具有日期時間值，Power BI Desktop 會假設您可能要以此資料行作為時間階層軸。

不過有些情況較具挑戰性，例如地理位置。 請考慮以下來自 Excel 工作表的資料表：

![Excel 的螢幕擷取畫面，其中顯示要匯入 Power BI Desktop 的表格式資料。](media/desktop-data-categorization/datacategorizationtable.png)

Power BI Desktop 是否應該將 **GeoCode** 資料行中的代碼視為國家/地區或美國州名的縮寫？  由於這類代碼可能代表任何意思，因此並不清楚。 例如，AL 可能表示阿拉巴馬州或阿爾巴尼亞，AR 可能表示阿肯色州或阿根廷，CA 可能表示加州或加拿大。 當我們在地圖上繪製 GeoCode 欄位時，則需要加以區別。 

Power BI Desktop 是否應該顯示已醒目提示國家/地區的世界圖片？ 或是應該顯示已醒目提示各州的美國圖片？  您可以為這類資料指定資料類別。 資料分類會進一步精簡 Power BI Desktop 可用來提供最佳視覺效果的資訊。  

**指定資料類別**

1. 在 [報表] 檢視或 [資料] 檢視的 [欄位] 清單中，選取您要依不同分類排序的欄位。
2. 在功能區 [模型] 索引標籤的 [屬性] 區域中，選取 [資料類別] 旁的下拉式箭號。  此清單會顯示您可以為資料行選擇的資料類別。 若某些選項不適用於資料行的目前資料類型，則可能會停用這些選取項目。  例如，若資料行是日期或時間資料類型，則 Power BI Desktop 將無法供選擇地理資料類別。 
3. 選取您想要的類別。

   ![Power BI Desktop 的螢幕擷取畫面，其中顯示 [資料類別] 篩選。](media/desktop-data-categorization/desktop-data-categorization.png)

您可能也會想要了解 [Power BI 行動裝置應用程式的地理篩選](desktop-mobile-geofiltering.md)。