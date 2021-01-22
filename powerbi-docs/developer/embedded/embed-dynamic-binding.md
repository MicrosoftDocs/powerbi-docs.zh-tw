---
title: 使用動態繫結連線 Power BI 報表與資料集
description: 了解如何使用 Power BI 內嵌式分析中的動態繫結來內嵌 Power BI 報表。
author: KesemSharabi
ms.author: kesharab
ms.topic: conceptual
ms.service: powerbi
ms.subservice: powerbi-developer
ms.date: 01/17/2021
ms.openlocfilehash: 0bc33ed37e389b42f5c27f8271cc461eb99e229a
ms.sourcegitcommit: 1cad78595cca1175b82c04458803764ac36e5e37
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2021
ms.locfileid: "98565810"
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

若要讓動態繫結能夠正常運作，您必須將 `datasetBinding` 新增至設定物件。 若要了解如何完成此步驟，請參閱[將資料集動態繫結至報表](/javascript/api/overview/powerbi/bind-report-datasets)。 

## <a name="next-steps"></a>後續步驟

如果不熟悉如何在 Power BI 中內嵌，請複習下列教學課程，了解如何內嵌 Power BI 內容。

>[!div class="nextstepaction"]
>[將客戶的 Power BI 內容內嵌至應用程式](embed-sample-for-customers.md)

>[!div class="nextstepaction"]
>[為組織將 Power BI 內容內嵌至應用程式](embed-sample-for-your-organization.md)