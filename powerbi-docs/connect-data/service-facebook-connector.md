---
title: 第三方服務：適用於 Power BI Desktop 的 Facebook 連接器
description: 第三方服務：適用於 Power BI Desktop 的 Facebook 連接器
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 02/20/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 4f1faf585643c593e194e965dff2bb29988e27d4
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96402562"
---
# <a name="use-the-facebook-connector-for-power-bi-desktop"></a>使用適用於 Power BI Desktop 的 Facebook 連接器
**Power BI Desktop** 中的 Facebook 連接器依賴 Facebook 圖形 API。 因此，功能與可用性可能會隨著時間而變化。

您可以看到[適用於 Power BI Desktop 的 Facebook 連接器相關教學課程](desktop-tutorial-facebook-analytics.md).

> [!IMPORTANT]
> **Facebook 資料連接器的淘汰通知：** 自 2020 年 4 月起，在 Excel 中從 Facebook 匯入和重新整理資料功能，將無法正常運作。 在此之前您仍可以使用 Facebook「取得 & 轉換 (Power Query)」  連接器， 而在該日期之後，您將會無法連線至 Facebook，且會收到錯誤訊息。 我們建議您儘快修改或移除所有仍在使用 Facebook 連接器的「取得 & 轉換 (Power Query)」  查詢，以避免非預期的結果。


Facebook 的 Graph API v1.0 已於 2015 年 4 月 30 日過期。 Power BI 針對 Facebook 連接器在幕後使用圖形 API，可讓您連接到資料並進行分析。

2015 年 4 月 30 日以前建置的查詢可能無法繼續運作或會傳回較少的資料。 2015 年 4 月 30 日之後，Power BI 對 Facebook API 的所有呼叫都使用 v2.8。 如果您的查詢建置在 2015 年 4 月 30 日之前，而且您之後都未使用，您可能需要重新驗證，以核准我們要求的新權限集。

雖然我們嘗試一有變更即發行更新，但是應用程式開發介面變更的方式可能會影響我們產生查詢的結果。 在某些情況下，可能不再支援某些查詢。 由於這種相依性，我們無法保證您使用這個連接器的查詢結果。

如需 Facebook API 變更的詳細資訊，請參閱[這裡](https://developers.facebook.com/docs/apps/changelog#v2_0).

