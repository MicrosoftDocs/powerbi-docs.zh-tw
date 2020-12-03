---
title: Power BI 報表伺服器中的 Always Encrypted
description: 本文詳述在使用資料來源類型 Microsoft SQL Server 和 Microsoft Azure SQL Database 時，Power BI 報表伺服器中的 Always Encrypted 支援。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: cfinlan
ms.service: powerbi
ms.subservice: powerbi-report-server
ms.topic: conceptual
ms.date: 01/22/2020
ms.openlocfilehash: 4851a20ecd406ffe2a460ba52833cca420b517da
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415534"
---
# <a name="always-encrypted-in-power-bi-report-server"></a>Power BI 報表伺服器中的 Always Encrypted

本文詳述在使用資料來源類型 Microsoft SQL Server 和 Microsoft Azure SQL Database 時，Power BI 報表伺服器中的 Always Encrypted 支援。 如需 SQL Server 中的 Always Encrypted 功能詳細資訊，請參閱 [Always Encrypted](/sql/relational-databases/security/encryption/always-encrypted-database-engine) 一文。

## <a name="always-encrypted-user-isolation"></a>Always Encrypted 使用者隔離

目前，如果使用者具有報表的存取權，Power BI 報表伺服器不會限制報表中 Always Encrypted 資料行的存取權。  因此，如果伺服器已透過資料行主要金鑰獲得對資料行加密金鑰的存取權，使用者便可以存取其可存取的報表所有資料行。

## <a name="always-encrypted-column-usage"></a>Always Encrypted 資料行使用方式

### <a name="key-storage-strategies"></a>金鑰儲存策略

|儲存體  |支援  |
|---------|---------|
|Windows 憑證存放區 | 有 |
|Azure Key Vault | 否 |
| 新一代的密碼編譯 (CNG) | 否 |

### <a name="certificate-storage-and-access"></a>憑證存放區和存取權

需要存取憑證的帳戶是服務帳戶。 憑證應儲存在本機電腦憑證存放區。 如需詳細資訊，請參閱：

- [設定報表伺服器服務帳戶](/sql/reporting-services/install-windows/configure-the-report-server-service-account-ssrs-configuration-manager) (設定管理員)
- SQL Server 文章「建立及儲存 Always Encrypted 的資料行主要金鑰」的[讓憑證可供應用程式和使用者使用](/sql/relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted#making-certificates-available-to-applications-and-users)一節。

### <a name="column-encryption-strategy"></a>資料行加密策略

在 Power BI 報表伺服器中，資料行加密策略可以是「決定性」  或「隨機化」  。 下表根據其使用的策略來詳述差異。

|使用  |具決定性  |隨機化  |
|---------|---------|---------|
|可以在查詢結果中以原狀讀取，例如 SELECT 陳述式。 | 有  | 有  |
|可以用作查詢內的 Group By 實體。 | 有 | 否 |
|除了 COUNT和 DISTINCT 以外，可以用作彙總欄位。 | 否，但是 COUNT 和 DISTINCT 除外 | 否 |
|可以用作報表參數 | 有 | 否 |

深入了解[決定性與隨機加密](/sql/relational-databases/security/encryption/always-encrypted-database-engine#selecting--deterministic-or-randomized-encryption)。

### <a name="parameter-usage"></a>參數使用方式

參數使用方式僅適用於決定性加密。

**單一值參數**。  您可以對 Always Encrypted 資料行使用單一值參數。

**多重值參數**。 您無法對 Always Encrypted 資料行使用具有超過一個值的多重值參數。

**串聯參數**。 如果下列「所有」  條件都滿足，您可以對 Always Encrypted 使用串聯參數：

- 所有 Always Encrypted 資料行都必須是使用決定性策略的 Always Encrypted。
- 對 Always Encrypted 資料行使用的所有參數都是單一值參數。
- 所有 SQL 比較都使用等於 (=) 運算子。

## <a name="datatype-support"></a>資料類型支援

| SQL 資料類型 | 支援讀取欄位 | 支援用作為 Group By 元素 | 支援的彙總 (COUNT、DISTINCT、MAX、MIN、SUM 等) | 支援使用參數透過相等來進行篩選 | 注意 |
| --- | --- | --- | --- | --- | --- |
| int | 有 | 有 | COUNT、DISTINCT | 是，以整數形式 |   |
| FLOAT | 有 | 有 | COUNT、DISTINCT | 是，以浮點數形式 |   |
| NVARCHAR | 有 | 有 | COUNT、DISTINCT | 是，以文字形式 | 確定性加密必須針對字元資料行使用 binary2 排序次序的資料行定序。 如需詳細資料，請參閱 SQL Server [Always Encrypted](/sql/relational-databases/security/encryption/always-encrypted-database-engine#selecting--deterministic-or-randomized-encryption) 一文。  |
| varchar | 有 | 有 | COUNT、DISTINCT | 否 |   |
| decimal | 有 | 有 | COUNT、DISTINCT | 否 |   |
| NUMERIC | 有 | 有 | COUNT、DISTINCT | 否 |   |
| datetime | 有 | 有 | COUNT、DISTINCT | 否 |   |
| datetime2 | 有 | 有 | COUNT、DISTINCT | 是，以日期/時間形式 | 如果資料行沒有毫秒有效位數，則受支援 (換句話說，沒有 datetime2(0)) |

## <a name="aggregation-alternatives"></a>彙總替代項目

針對決定性 Always Encrypted 資料行，目前唯一支援的彙總，是直接使用等於 (=) 運算子的彙總。 這項 SQL Server 限制是因為 Always Encrypted 資料行的本質。 使用者必須在報表內彙總，而不是在資料庫中。

## <a name="always-encrypted-in-connection-strings"></a>連接字串中的 Always Encrypted

您必須在 SQL Server 資料來源的連接字串中啟用 Always Encrypted。 深入了解啟用[應用程式查詢中的 Always Encrypted](/sql/relational-databases/security/encryption/develop-using-always-encrypted-with-net-framework-data-provider#enabling-always-encrypted-for-application-queries)。

## <a name="next-steps"></a>後續步驟

SQL Server 和 Azure SQL Database 中的 [Always Encrypted](/sql/relational-databases/security/encryption/always-encrypted-database-engine)

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)