---
title: 在 Power BI 內嵌式分析中，將資料推送至資料集，以取得更佳的內嵌 BI 見解
description: 將資料推送至 Power BI 資料集。 使用 Power BI 內嵌式分析，以便取得更佳的內嵌 BI 見解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: rkarlin
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: tutorial
ms.date: 05/22/2019
ms.openlocfilehash: 3c5805f4d498e8e2d8a788c5703a09a8109e024b
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887423"
---
# <a name="push-data-into-a-power-bi-dataset"></a>將資料推送至 Power BI 資料集

Power BI API 可讓您將資料推送到 Power BI 資料集。 在此文章中，我們將說明如何將包含「產品」資料表的「銷售行銷」資料集推送到現有的資料集。

開始之前，您需要 Azure Active Directory (Azure AD) 與 [Power BI 帳戶](../embedded/create-an-azure-active-directory-tenant.md)。

## <a name="steps-to-push-data-into-a-dataset"></a>將資料推送至資料集的步驟

* 步驟 1：[使用 Azure AD 註冊應用程式](../embedded/register-app.md)
* 步驟 2：[取得驗證存取權杖](walkthrough-push-data-get-token.md)
* 步驟 3：[在 Power BI 中建立資料集](walkthrough-push-data-create-dataset.md)
* 步驟 4：[取得資料集，以便將資料列加入 Power BI 資料表](walkthrough-push-data-get-datasets.md)
* 步驟 5：[將資料列加入 Power BI 資料表](walkthrough-push-data-add-rows.md)

下一節是有關資料推送的 Power BI API 作業的一般討論。

## <a name="power-bi-api-operations-to-push-data"></a>推送資料的 Power BI API 作業

透過 Power BI REST API，您可以將資料來源推送至 Power BI。 當應用程式將資料列新增到資料集時，儀表板磚會自動使用新資料更新。 若要推送資料，請使用 [PostDataset](/rest/api/power-bi/pushdatasets/datasets_postdataset) 與 [PostRows](/rest/api/power-bi/pushdatasets/datasets_postrows) 作業。 若要尋找資料集，請使用[取得資料集](/rest/api/power-bi/datasets/getdatasets)作業。 您可以傳遞群組識別碼來針對任何這些作業處理群組。 若要取得群組識別碼清單，請使用[取得群組](/rest/api/power-bi/groups/getgroups)作業。

以下是將資料推送至資料集的作業：

* [PostDataset](/rest/api/power-bi/pushdatasets/datasets_postdataset)
* [取得資料集](/rest/api/power-bi/datasets/getdatasets)
* [Post Rows](/rest/api/power-bi/pushdatasets/datasets_postrows)
* [取得群組](/rest/api/power-bi/groups/getgroups)

您可以將 JavaScript 物件標記法 (JSON) 字串傳遞至 Power BI 服務，在 Power BI 中建立資料集。 如需深入了解 JSON，請參閱 [JSON 簡介](https://json.org/)。

資料集的 JSON 字串具有下列格式：

**Power BI 資料集 JSON 物件**

```json
{"name": "dataset_name", "tables":
    [{"name": "", "columns":
        [{ "name": "column_name1", "dataType": "data_type"},
         { "name": "column_name2", "dataType": "data_type"},
         { ... }
        ]
      }
    ]
}
```

針對對於我們的「銷售行銷」資料集範例，您會傳遞 JSON 字串，如下所示。 在此範例中， **SalesMarketing** 是資料集名稱，而 **Product** 是資料表名稱。 定義資料表之後，您會定義資料表結構描述。 對於 **SalesMarketing** 資料集，資料表結構描述具有下列資料行：ProductID、Manufacturer、Category、Segment、Product 和 IsCompete。

**範例資料集物件 JSON**

```json
{
    "name": "SalesMarketing",
    "tables": [
        {
            "name": "Product",
            "columns": [
            {
                "name": "ProductID",
                "dataType": "int"
            },
            {
                "name": "Manufacturer",
                "dataType": "string"
            },
            {
                "name": "Category",
                "dataType": "string"
            },
            {
                "name": "Segment",
                "dataType": "string"
            },
            {
                "name": "Product",
                "dataType": "string"
            },
            {
                "name": "IsCompete",
                "dataType": "bool"
            }
            ]
        }
    ]
}
```

在 Power BI 資料表結構描述中，您可以使用下列資料類型。

## <a name="power-bi-table-data-types"></a>Power BI 資料表資料類型

| **Data type** | **限制** |
| --- | --- |
| Int64 |不允許 Int64.MaxValue 和 Int64.MinValue。 |
| Double |不允許 Double.MaxValue 和 Double.MinValue 值。 不支援 NaN。部分函式 (例如 Min、Max) 不支援 +Infinity 和 -Infinity。 |
| Boolean |無 |
| Datetime |在資料載入期間，會以一天時間分數將值量化為 1/300 秒 (3.33 毫秒) 的整數倍數。 |
| String |目前允許最多 12 萬 8 千個字元。 |

## <a name="learn-more-about-pushing-data-into-power-bi"></a>深入了解如何將資料推送至 Power BI

若要開始將資料推送至資料集，請參閱左側導覽窗格中的[步驟 1：在導覽窗格中，使用 Azure AD 註冊應用程式](../embedded/register-app.md)。

## <a name="next-steps"></a>後續步驟

* [註冊 Power BI](../embedded/create-an-azure-active-directory-tenant.md)  
* [JSON 簡介](https://json.org/)  
* [Power BI REST API 概觀](overview-of-power-bi-rest-api.md)  

有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)