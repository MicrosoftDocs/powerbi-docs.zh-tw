---
title: 使用動態繫結連接報表與資料集
description: 了解如何使用動態繫結內嵌報表。
author: KesemSharabi
ms.author: kesharab
ms.topic: how-to
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 11/07/2019
ms.openlocfilehash: 5b386800c37f80e7b33dc55bb691eed6606c04a1
ms.sourcegitcommit: 30d0668434283c633bda9ae03bc2aca75401ab94
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2020
ms.locfileid: "96906787"
---
# <a name="connect-a-report-to-a-dataset-using-dynamic-binding"></a>使用動態繫結連接報表與資料集 

當報表連接到資料集時，您可以使用動態繫結。 報表與資料集之間的連接稱為 *繫結*。 當繫結在內嵌時決定 (而非預先決定) 時，該繫結即稱為動態繫結。

當使用「動態繫結」內嵌 Power BI 報表時，可以透過使用者的認證，將同一份報表連接到不同的資料集。

這表示您可以使用一份報表來顯示不同資訊，視其所連線的資料集而定。 例如顯示零售銷售值的報表，當連線到不同的零售商資料集時，就能產生不同結果，其取決於其所連線的零售商資料集。

報表和資料集不需要位於相同的工作區。 這兩個工作區 (一個包含報表，一個包含資料集) 必須指派給[容量](azure-pbie-create-capacity.md)。

請在內嵌時，確定您 *具備足夠的權限產生權杖*，而且能 *調整設定物件*。

## <a name="generating-a-token-with-sufficient-permissions"></a>具備足夠的權限產生權杖

「為組織內嵌」及「為客戶內嵌」兩種案例皆支援動態繫結。 下表描述各情境的注意事項。

|案例  |資料擁有權  |權杖  |需求  |
|---------|---------|---------|---------|
|針對組織進行內嵌    |使用者擁有資料         |Power BI 使用者的存取權杖         |其 Azure AD 權杖經使用的使用者，必須具有所有成品的適當權限。         |
|針對客戶進行內嵌     |應用程式擁有資料         |非 Power BI 使用者的存取權杖         |必須同時包含報表和動態繫結資料集的權限。 使用[可以為多個項目產生內嵌權杖的 API](/rest/api/power-bi/embedtoken/generatetoken) 來產生可以支援多項成品的內嵌權杖。         |

## <a name="adjusting-the-config-object"></a>調整設定物件
將 `datasetBinding` 新增至設定物件。 請參考下列範例。

```javascript
var config = {
    type: 'report',
    tokenType: models.TokenType.Embed,
    accessToken: accessToken,
    embedUrl: embedUrl,
    id: "reportId", // The wanted report id
    permissions: permissions,

    // -----  Adjustment required for dynamic binding ---- //
    datasetBinding: {
        datasetId: "notOriginalDatasetId",  // </The wanted dataset id
    }
    // ---- End of dynamic binding adjustment ---- //
};

// Get a reference to the embedded report HTML element
var embedContainer = $('#embedContainer')[0];

// Embed the report and display it within the div container
var report = powerbi.embed(embedContainer, config);
```

## <a name="next-steps"></a>後續步驟

如果您不熟悉如何在 Power BI 中內嵌，請檢閱這些教學課程，以了解如何內嵌您的 Power BI 內容：
* [教學課程：為您的客戶，將 Power BI 內容內嵌至應用程式](embed-sample-for-customers.md)
* [教學課程：針對組織將 Power BI 內容內嵌至應用程式](embed-sample-for-your-organization.md)