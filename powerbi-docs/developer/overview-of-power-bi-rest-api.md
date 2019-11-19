---
title: Power BI API 可以做些什麼
description: Power BI API 可以做些什麼
author: rkarlin
ms.author: rkarlin
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 03/25/2019
ms.openlocfilehash: 8a231a426823d40be34e900a32d06e5d5f77108b
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/09/2019
ms.locfileid: "73880496"
---
# <a name="what-can-developers-do-with-the-power-bi-api"></a>開發人員可如何利用 Power BI API？

使用 Power BI REST API，您就可以建立與 Power BI 報表、儀表板和圖格整合的應用程式。

使用 Power BI REST API，就可以在 Power BI 物件 (例如報表、資料集和工作區) 上執行管理工作。

以下是一些您可以使用 Power BI API 進行的操作。

| **深入了解** | **參考這項資訊** |
|----------------------------------------------------------------------------------|------------------------------------------------------------------------------------|
| 內嵌適用於 Power BI 使用者和非 Power BI 使用者的報表、儀表板和圖格。 | [如何內嵌 Power BI 儀表板、報表和磚](embedding-content.md) |
| 在 Power BI 物件上執行管理工作。 | [Power BI REST API 參考](https://docs.microsoft.com/rest/api/power-bi/) |
| 擴充現有商務工作流程，將關鍵資料推送至 Power BI 儀表板。 | [將資料推入儀表板中](walkthrough-push-data.md) |
| 向 Power BI 驗證。 | [向 Power BI 驗證](get-azuread-access-token.md) |

> [!NOTE]
> Power BI API 仍然將工作區稱為群組。 任何對群組的引述都表示您正在使用工作區。

## <a name="api-developer-tools"></a>API 開發人員工具

| 工具 | 描述 |  |  |
|-------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|---|---|
| [遊樂場工具](https://microsoft.github.io/PowerBI-JavaScript/demo) | 體驗使用 Power BI JavaScript API 的完整範例。 此工具也是一個可測試不同類型 Power BI Embedded 範例的快速方式。 |  |  |
| [Power BI JavaScript Wiki](https://github.com/Microsoft/powerbi-javascript/wiki) | 取得 Power BI JavaScript API 的詳細資訊。 |  |  |
| [Postman](https://www.getpostman.com/) | 執行要求、測試、偵錯、監視、執行自動化測試等。 |

## <a name="push-data-into-power-bi"></a>將資料推送至 Power BI

您可以使用 Power BI API 以[將資料推送至資料集](walkthrough-push-data.md)。 此功能可讓您將資料列新增至資料集內的資料表。 新資料接著會反映在儀表板的圖格中，以及報表的視覺效果內。

![推送資料範例](media/what-can-you-do/powerbi-push-data.png)

## <a name="github-repositories"></a>GitHub 存放庫

* [Power BI 開發人員範例](https://github.com/Microsoft/PowerBI-Developer-Samples)
* [.NET SDK](https://github.com/Microsoft/PowerBI-CSharp)
* [JavaScript API](https://github.com/Microsoft/PowerBI-JavaScript)

## <a name="next-steps"></a>後續步驟

* [將資料推送至資料集](walkthrough-push-data.md)
* [Developing a Power BI custom visual](visuals/custom-visual-develop-tutorial.md) (開發 Power BI 自訂視覺效果)
* [Power BI REST API 參考](rest-api-reference.md)
* [Power BI REST API](https://docs.microsoft.com/rest/api/power-bi/)

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
