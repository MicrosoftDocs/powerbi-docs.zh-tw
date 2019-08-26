---
ms.openlocfilehash: 0592cb7ef076f8094aca565d955cc238b2181068
ms.sourcegitcommit: f6ac9e25760561f49d4257a6335ca0f54ad2d22e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2019
ms.locfileid: "69560981"
---
## <a name="faq"></a>常見問題集
**問：** 如果先前曾在 Power BI 服務中建立了資料集的角色與規則會如何？ 如果什麼都不做，它們還可以運作嗎？  
**答：** 視覺效果不會正確轉譯。 您必須在 Power BI Desktop 內重新建立角色與規則，然後將其發行至 Power BI 服務。

**問：** 我可以為 Analysis Services 資料來源建立這些角色嗎？  
**答：** 如果已將資料匯入 Power BI Desktop，就可建立。 如果您使用的是即時連線，就無法在 Power BI 服務中設定 RLS。 這定義在內部部署 Analysis Services 模型中。

**問：** 我可以使用 RLS 來限制使用者能夠存取的資料行或量值嗎？  
**答：** 否，如果使用者具有特定資料列的存取權，就可以查看該資料列的所有資料行。

**問：** RLS 是否可讓我隱藏詳細資料，但允許存取以視覺效果摘要的資料？  
**答：** 否，您可以保護個別資料列，但使用者一律可以查看詳細資料或摘要的資料。

