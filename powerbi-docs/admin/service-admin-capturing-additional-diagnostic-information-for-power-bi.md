---
title: 擷取其他診斷資訊
description: 這些指示提供兩個可能的選項，以從 Power BI Web 用戶端手動收集其他診斷資訊。
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 09/17/2019
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 856eb4ca9b8c8afab90d351b5a025c2198b393b1
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96413717"
---
# <a name="capture-additional-diagnostic-information-for-power-bi"></a>擷取 Power BI 的其他診斷資訊

本文提供從 Power BI Web 用戶端手動收集其他診斷資訊的指示。

1. 使用 Microsoft Edge 或 Internet Explorer 瀏覽至 [Power BI](https://app.powerbi.com)。

1. 按 **F12** 開啟 Microsoft Edge 開發人員工具。

   ![Microsoft Edge 開發人員工具 [元素] 索引標籤的螢幕擷取畫面。](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-developer-tools.png)

1. 切換至 [網路] 索引標籤。其中列出已經擷取的流量。

   ![Microsoft Edge 開發人員工具 [網路] 索引標籤的螢幕擷取畫面。](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab.png)

    您可以：

    * 在視窗中瀏覽，並重現任何可能遇到的問題。

    * 按 F12 可在工作階段期間隨時隱藏和顯示開發人員工具視窗。

1. 若要停止剖析工作階段，您可以在開發人員工具區域選取 [網路] 索引標籤上的紅色方塊。

   ![Microsoft Edge 開發人員工具 [網路] 索引標籤的螢幕擷取畫面，其中標示出停止圖示。](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-stop.png)

1. 選取磁碟片圖示，將資料匯出成 HTTP 封存 (HAR) 檔案。

   ![Microsoft Edge 開發人員工具 [網路] 索引標籤的螢幕擷取畫面，其中標示出磁碟片圖示。](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-save.png)

1. 提供檔案名稱並儲存 HAR 檔案。

    HAR 檔案會包含瀏覽器視窗和 Power BI 之間網路要求的所有相關資訊，包括：

    * 每個要求的活動識別碼。

    * 每個要求的精確時間戳記。

    * 傳回用戶端的所有錯誤資訊。

    這項追蹤也會包含用來填入畫面上所示視覺效果的資料。

1. 您可以提供 HAR 檔案以支援檢閱。

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
