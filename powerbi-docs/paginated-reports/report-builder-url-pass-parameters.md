---
title: 針對編頁報表在 URL 中傳遞報表參數 - Power BI 報表產生器
description: 本主題描述如何藉由將報表參數包含在報表 URL 中，來將其傳遞至報表。
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
author: maggiesMSFT
ms.author: maggies
ms.reviewer: cfinlan
ms.custom: ''
ms.date: 05/01/2020
ms.openlocfilehash: f103f29c61d1a4e4a5340d97598d80a86c708701
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/04/2020
ms.locfileid: "93298040"
---
# <a name="pass-a-report-parameter-in-a-url-for-a-paginated-report-in-power-bi"></a>針對 Power BI 中的編頁報表在 URL 中傳遞報表參數 

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

您可以藉由將報表參數包含在報表 URL 中，來將其傳遞至報表。 所有查詢參數都可以有相對應的報表參數。 因此，您可以藉由傳遞對應的報表參數，來將查詢參數傳遞至報表。 您必須在參數名稱前面加上 `rp:`，Power BI 才能在 URL 中加以識別。 

報表參數會區分大小寫，並使用下列特殊字元： 

- URL 中參數部分的空格會以加號 (+) 取代。  例如： 

    ```rp:Holiday=Christmas+Day```

- 字串中任何部分的分號會以字元 `%3A` 取代。

瀏覽器應該會自動執行正確的 URL 編碼。 您不需要手動編碼任何字元。 

若要設定 URL 內的報表參數，請使用以下語法： 

```
rp:parameter=value
```

例如，若要指定 [我的工作區] 報表中所定義兩個參數 "Salesperson" 和 "State"，您可以使用下列 URL： 

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:Salesperson=Tie+Bear&rp:State=Utah 
```

若要指定應用程式報表中所定義的相同兩個參數，您可以使用下列 URL： 

```
https://app.powerbi.com/groups/me/apps/xxxxxxx-c4c4-4217-afd9-3920a0d1e2b0/rdlreports/b1d5e659-639e-41d0-b733-05d2bca9853c?rp:Salesperson=Tiggee&rp:State=Utah 
```

若要為參數傳遞 Null 值，請使用下列語法： 

```
parameter:isnull=true
```

例如：

```
rp:SalesOrderNumber:isnull=true
```

若要傳遞布林值，請使用 0 表示 false，並使用 1 表示 true。 若要傳遞浮點值，請包含伺服器地區設定的小數分隔符號。

> [!NOTE]
> 如果報表包含具有預設值的報表參數，且 **Prompt** 屬性的值為 **false** (也就是未在報表管理員中選取 [提示使用者] 屬性)，則您無法在 URL 中傳遞該報表參數的值。 這可讓系統管理員選擇防止終端使用者新增或修改特定報表參數的值。
> 
> Power BI 不支援超過 2,000 個字元的查詢字串。  如果您使用 url 參數來檢視您的編頁報表，則可以超過此值。  如果您使用多重值參數，尤其如此。

## <a name="additional-examples"></a>其他範例 

下列 URL 範例包含多重值參數 "Salesperson”。 多重值參數的格式是針對每個值重複參數名稱。 

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:Salesperson=Tie+Bear&rp:Salesperson=Mickey 
```

下列 URL 範例會針對原生模式的報表伺服器，傳遞值為 "7/1/2005" 的單一參數 SellStartDate。

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:SellStartDate=7/1/2005
```

## <a name="next-steps"></a>後續步驟

- [Power BI 編頁報表中的 URL 參數](report-builder-url-parameters.md)
- [什麼是 Power BI Premium 中的編頁報表？](paginated-reports-report-builder-power-bi.md)
