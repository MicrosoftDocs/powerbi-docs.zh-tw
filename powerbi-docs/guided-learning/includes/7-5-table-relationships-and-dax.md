---
ms.openlocfilehash: 679c3e8c3d94c93899e9dcfae1e57f4b678fb218
ms.sourcegitcommit: a5853ef44ed52e80eabee3757bb6887fa400b75b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73799728"
---
Power BI 可讓您建立多個資料表之間的關聯性，包括資料來源完全不同的資料表之間的關聯性。 您可以在 Power BI Desktop 的 [關聯性]  檢視中，查看任何資料模型的關聯性。

![](media/7-5-table-relationships-and-dax/dax-relationships_1.png)

## <a name="dax-relational-functions"></a>DAX 關聯式函數
DAX 具有**關聯式函數**，可讓您與已建立關聯性的資料表進行互動。

您可以傳回資料行的值，或您可以使用 DAX 函數傳回具有關聯性的所有資料列。

例如，**RELATED** 函式會遵循關聯性並傳回資料行的值，而 **RELATEDTABLE** 會遵循關聯性，並傳回經篩選只包含相關資料列的整個資料表。

![](media/7-5-table-relationships-and-dax/dax-relationships_2.png)

**RELATED** 函數適用於 *多對一* 關聯性，而 **RELATEDTABLE** 適用於 *一對多* 關聯性。

您可以使用關聯式函數建立包含多個資料表值的運算式。 不論關聯性的鏈結長度為何，DAX 皆會以此等函數傳回結果。

> 影片內容感謝下列提供者的協助 [Alberto Ferrari、SQLBI](https://www.sqlbi.com/learning-dax)
> 
> 

