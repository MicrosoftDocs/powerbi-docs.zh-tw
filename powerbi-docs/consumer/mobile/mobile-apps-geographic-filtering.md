---
title: 在 Power BI 行動裝置應用程式中依地理位置篩選報表
description: 了解如何在 Power BI mobile apps 中，依地理位置篩選報表 (若報表擁有者已設定地理標記)。
author: paulinbar
ms.author: painbar
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 03/11/2020
ms.openlocfilehash: fe5ab9befcf54a617aefa5ad281872f45a59229c
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96388969"
---
# <a name="filter-a-report-by-geographic-location-in-the-power-bi-mobile-apps"></a>在 Power BI 行動裝置應用程式中依地理位置篩選報表
適用於：

| ![iPhone](./media/mobile-apps-geographic-filtering/iphone-logo-50-px.png) | ![iPad](./media/mobile-apps-geographic-filtering/ipad-logo-50-px.png) | ![Android 手機](./media/mobile-apps-geographic-filtering/android-phone-logo-50-px.png) | ![Android 平板電腦](./media/mobile-apps-view-dashboard/android-tablet-logo-50-px.png) | ![Windows 手機](./media/mobile-apps-geographic-filtering/win-10-logo-50-px.png) |
|:--- |:--- |:--- |:--- |:--- |
| iPhone |iPad |Android 手機 |Android 平板電腦 |Windows 10 手機 |

當您在行動裝置中查看 Power BI 報表時，是否看到右上角有小圖釘圖示？ 如果有的話，即可按您的地理位置來篩選該報表。

> [!NOTE]
> 只有在報表中的地理名稱是英文時 (例如 "New York City" 或 "Germany")，您才能依位置篩選報表。 Windows 10 平板電腦與電腦不支援地理篩選，但 Windows 10 手機支援。

>[!NOTE]
>**使用 Windows 10 行動裝置版手機** 的 Power BI 行動裝置應用程式支援，將於 2021 年 3 月 16 日停止。 [深入了解](/legal/powerbi/powerbi-mobile/power-bi-mobile-app-end-of-support-for-windows-phones)

## <a name="filter-your-report-by-your-geographic-location"></a>依地理位置篩選您的報表
1. 在行動裝置的 Power BI 行動裝置應用程式中，開啟報表。
2. 如果報表具有地理資料，您會看到訊息要求您允許 Power BI 存取您的位置。 按一下 [允許]  ，然後再次點選 [允許]  。
3. 點選圖釘 ![圖釘圖示](./media/mobile-apps-geographic-filtering/power-bi-mobile-geo-icon.png). 根據報表中的資料，您可以依城市、縣/市或國家/地區進行篩選。 篩選器只會列出符合您目前位置的選項。
   
    ![圖釘篩選](./media/mobile-apps-geographic-filtering/power-bi-mobile-geo-map-set-filter.png)

## <a name="why-dont-i-see-location-tags-on-a-report"></a>為何會在報表上看到位置標記？
您必須符合下列三項條件，才能看到位置標記。 

* 在 Power BI Desktop 中建立報表的人，必須將[地理資料分類](../../transform-model/desktop-mobile-geofiltering.md)為至少一個資料行，例如城市、縣/市或國家/地區。
* 您位在該資料行中具有資料的位置。
* 您使用下列其中一部行動裝置︰
  * iOS (iPad、iPhone、iPod)。
  * Android (手機、平板電腦)。
  * Windows 10 電話 (電腦和平板電腦等其他不支援地理篩選的 Windows 10 裝置)。

深入了解如何在 Power BI Desktop 中[設定地理篩選](../../transform-model/desktop-mobile-geofiltering.md)。

### <a name="next-steps"></a>後續步驟
* 透過行動裝置應用程式[實際連接 Power BI 資料](mobile-apps-data-in-real-world-context.md)
* [Power BI Desktop 中的資料分類](../../transform-model/desktop-data-categorization.md) 
* 有任何問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)