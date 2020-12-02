---
title: Power BI Desktop 中的資料列層級安全性 (RLS) 指導方針
description: 使用 Power BI Desktop 在您的資料模型中強制執行資料列層級安全性 (RLS) 的指導方針。
author: paulinbar
ms.author: painbar
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 06/18/2020
ms.openlocfilehash: 3c8290391d549f4510b4f6ea6ee0fd596500045e
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410083"
---
# <a name="row-level-security-rls-guidance-in-power-bi-desktop"></a>Power BI Desktop 中的資料列層級安全性 (RLS) 指導方針

此文章以使用 Power BI Desktop 的資料模型製作人員為目標。 其會描述在資料模型中強制執行資料列層級安全性 (RLS) 的良好設計做法。

請務必了解 RLS 會篩選「資料表資料列」。 其無法設定來限制對模型物件的存取，這包括資料表、資料行或量值。

> [!NOTE]
> 此文章不會說明 RLS 或其設定方式。 如需詳細資訊，請參閱[使用 Power BI Desktop 的資料列層級安全性 (RLS) 來限制資料存取](../create-reports/desktop-rls.md)。
>
> 同時，其也不會涵蓋使用 Azure Analysis Services 或 SQL Server Analysis Services 在針對外部裝載模型的即時連線中強制執行 RLS 的內容。 在這些情況下，RLS 是由 Analysis Services 強制執行。 當 Power BI 使用單一登入 (SSO) 連線時，Analysis Services 將會強制執行 RLS (除非該帳戶具備系統管理員權限)。

## <a name="create-roles"></a>建立角色

您可以建立多個角色。 當您考慮單一報表使用者的權限需求時，請盡量建立能授與所有那些需求的單一角色，而不是使用報表使用者將會是多個角色之成員的設計。 這是因為報表使用者可能會對應至多個角色，無論是使用其使用者帳戶來直接對應，或是透過安全性群組成員資格來間接對應。 多個角色對應可能會導致非預期的結果。

將報表使用者指派至多個角色時，RLS 篩選會相加。 這表示報表使用者可以看見代表那些篩選之聯集的資料表資料列。 此外，在某些案例下，並無法保證報表使用者看不見某個資料表中的資料列。 因此，此情況與套用至 SQL Server 資料庫物件 (及其他權限模型) 的權限不同，並不適用「一旦拒絕便會一律拒絕」的原則。

假設有一個具有兩個角色的模型：名為 **Workers** 的第一個角色，會使用下列規則運算式來限制針對所有 **Payroll** 資料表資料列的存取：

```dax
FALSE()
```

> [!NOTE]
> 當規則的運算式評估為 **false** 時，將不會傳回任何資料表資料列。

但是，名為 **Managers** 的第二個角色，會使用下列規則運算式來允許針對所有 **Payroll** 資料表資料列的存取：

```dax
TRUE()
```

請注意：當報表使用者對應至這兩個角色時，其將能看見所有 **Payroll** 資料表資料列。

## <a name="optimize-rls"></a>將 RLS 最佳化

RLS 的運作方式是自動將篩選套用到每個 DAX 查詢，而這些篩選對查詢效能可能會有負面影響。 因此，有效率的 RLS 會取決於良好的模型設計。 請務必遵循模型設計指導方針，如下列文章中所述：

- [了解星型結構描述及其對 Power BI 的重要性](star-schema.md)
- 所有的關聯性指導方針文章都可以在 [Power BI 指導文件](./index.yml)中找到

一般而言，在維度類型資料表上強制執行 RLS 篩選的效率，會高於在事實類型資料表上執行的效率。 而且需要仰賴設計良好的關聯性，以確保 RLS 篩選能傳播到其他模型資料表上。 因此，在使用模型關聯性便能達到相同結果時，請避免使用 [LOOKUPVALUE](/dax/lookupvalue-function-dax) DAX 函數。

每當在 DirectQuery 資料表上強制執行 RLS 篩選，而且存在與其他 DirectQuery 資料表的關聯性時，請務必將來源資料庫最佳化。 這可能會涉及設計適當的索引，或是使用保存的計算資料行。 如需詳細資訊，請參閱 [Power BI Desktop 中的 DirectQuery 模型指導方針](directquery-model-guidance.md)。

### <a name="measure-rls-impact"></a>測量 RLS 的影響

您可以使用[效能分析器](../create-reports/desktop-performance-analyzer.md)在 Power BI Desktop 中測量 RLS 篩選的效能影響。 首先，請判斷未強制執行 RLS 時，報表視覺效果查詢的持續時間。 然後使用 [模型化] 功能區索引標籤上的 [檢視身分] 命令來強制執行 RLS，並判斷及比較查詢持續時間。

## <a name="configure-role-mappings"></a>設定角色對應

發佈至 Power BI 之後，您必須將成員對應至資料集角色。 只有資料集擁有者或工作區管理員可以將成員新增至角色。 如需詳細資訊，請參閱 [Power BI 的資料列層級安全性 (RLS) (管理模型的安全性)](../admin/service-admin-rls.md#manage-security-on-your-model)。

成員可以是使用者帳戶或安全性群組。 如果可以的話，建議您將安全性群組對應至資料集角色。 其會涉及在 Azure Active Directory 中管理安全性群組成員資格。 可能的話，其會將工作委派給您的網路系統管理員。

## <a name="validate-roles"></a>驗證角色

測試每個角色來確保其會正確篩選模型。 這可以透過使用 [模型化] 功能區索引標籤上的 [檢視身分] 命令來輕鬆完成。

當模型具有使用 [USERNAME](/dax/username-function-dax) DAX 函數的動態規則時，請務必針對預期的和「非預期的」值進行測試。 內嵌 Power BI 內容 (具體而言是使用[應用程式擁有資料](../developer/embedded/embedding.md#embedding-for-your-customers)案例) 時，應用程式邏輯可以將任何值傳遞為有效的身分識別使用者名稱。 可以的話，請盡可能確保意外或惡意的值所導致的篩選不會傳回任何資料列。

假設一個使用 Power BI 內嵌的範例，其中應用程式會將使用者的作業角色傳遞為有效的使用者名稱：其可以為 "Manager" 或 "Worker"。 Manager 可以看見所有資料列，但 Worker 只能看見 **Type** 資料行值為 "Internal" 的資料列。

會定義下列規則運算式：

```dax
IF(
    USERNAME() = "Worker",
    [Type] = "Internal",
    TRUE()
)
```

此規則運算式的問題，在於其所有值 (除了 "Worker" 之外) 都會傳回「所有資料表資料列」。 因此，非預期的值 (例如 "Wrker") 將會意外傳回所有資料表資料列。 因此撰寫會針對每個預期的值進行測試的運算式會比較安全。 在下列改善的規則運算式中，非預期的值將導致資料表不會傳回任何資料列。

```dax
IF(
    USERNAME() = "Worker",
    [Type] = "Internal",
    IF(
        USERNAME() = "Manager",
        TRUE(),
        FALSE()
    )
)
```

## <a name="design-partial-rls"></a>設計部分 RLS

有時候，計算需要未受 RLS 篩選限制的值。 例如，報表可能會需要顯示報表使用者銷售區域的收益與「所有收益」之間的比率。

雖然不可能讓 DAX 運算式覆寫 RLS (事實上，其甚至無法判斷是否已強制執行 RLS)，您可以使用摘要模型資料表。 系統會查詢摘要模型資料表以擷取「所有區域」的收益，且其不受任何 RLS 篩選所限制。

讓我們看看您可以如何實作此設計需求。 首先，請考慮下列模型設計：

:::image type="content" source="media/rls-guidance/mixed-rls-model.png" alt-text="顯示模型圖表的影像。其會在下列段落中描述。":::

模型包含四個資料表：

- **Salesperson** 資料表會針對每位銷售人員儲存一個資料列。 其會包含 **EmailAddress** 資料行，其中會儲存每位銷售人員的電子郵件地址。 這個資料表是隱藏的。
- **Sales** 資料表會針對每個訂單儲存一個資料列。 其會包含 **Revenue % All Region** 量值，這是設計來傳回報表使用者銷售區域的收益與全部區域的收益之間的比率。
- **Date** 資料表會針對每個日期儲存一個資料列，並允許對年份和月份進行篩選及分組。
- **SalesRevenueSummary** 是計算資料表。 其會儲存每個訂單日期的總收益。 這個資料表是隱藏的。

下列運算式會定義 **SalesRevenueSummary** 計算資料表：

```dax
SalesRevenueSummary =
SUMMARIZECOLUMNS(
    Sales[OrderDate],
    "RevenueAllRegion", SUM(Sales[Revenue])
)
```

> [!NOTE]
> [彙總資料表](../transform-model/desktop-aggregations.md)可以達成相同的設計需求。

下列 RLS 規則會套用至 **Salesperson** 資料表：

```dax
[EmailAddress] = USERNAME()
```

下表說明三種模型關聯性：

|關聯性|描述|
|---------|---------|
|![流程圖結束點 1。](media/common/icon-01-red-30x30.png)|**Salesperson** 和 **Sales** 資料表之間具有多對多關聯性。 RLS 規則會使用 [USERNAME](/dax/username-function-dax) DAX 函數來篩選隱藏 **Salesperson** 資料表的 **EmailAddress** 資料行。 **Region** 資料行值 (適用於報表使用者) 會傳播至 **Sales** 資料表。|
|![流程圖結束點 2。](media/common/icon-02-red-30x30.png)|**Date** 和 **Sales** 資料表之間具有一對多關聯性。|
|![流程圖結束點 3。](media/common/icon-03-red-30x30.png)|**Date** 和 **SalesRevenueSummary** 資料表之間具有一對多關聯性。|

下列運算式會定義 **Revenue % All Region** 量值：

```dax
Revenue % All Region =
DIVIDE(
    SUM(Sales[Revenue]),
    SUM(SalesRevenueSummary[RevenueAllRegion])
)
```

> [!NOTE]
> 請小心避免洩漏敏感性事實。 如果此範例中只有兩個區域，報表使用者便可以計算出另一個區域的收益。

## <a name="avoid-using-rls"></a>避免使用 RLS

在合理的情況下，請避免使用 RLS。 如果您只有會套用靜態篩選的少量簡單 RLS 規則時，請考慮改為發佈多個資料集。 所有的資料集都不會定義角色，因為每個資料集都包含適用於特定報表使用者對象的資料，而這些對象都具有相同的資料權限。 然後，針對每個對象建立單一工作區，並將存取權限指派給該工作區或應用程式。

例如，一家只有兩個銷售區域的公司，決定將「適用於每個銷售區域的」資料集發佈至不同的工作區。 資料集並不會強制執行 RLS。 不過，其會使用[查詢參數](/power-query/power-query-query-parameters) \(英文\) 來篩選來源資料。 如此一來，便會將相同的模型發佈至每個工作區，其只會具有不同的資料集參數值。 只會將其中一個工作區 (或已發佈的應用程式) 的存取權指派給銷售人員。

避免使用 RLS 有幾個相關聯的優勢：

- **改善查詢效能：** 其可能會因為較少的篩選而導致效能提升。
- **較小的模型：** 雖然其會產生更多的模型，但模型的大小會比較小。 較小的模型可以改善查詢和資料重新整理回應能力，特別是在裝載容量遇到資源壓力的情況下。 此外，將模型大小保持在容量所加諸的大小限制之下，也是件比較輕鬆的工作。 最後，在不同的容量上平衡工作負載會較為輕鬆，因為您可以在不同的容量上建立工作區，或是將工作區移至不同的容量上。
- **其他功能：** 可以使用無法搭配 RLS 運作的 Power BI 功能，例如 [發行至 Web](../collaborate-share/service-publish-to-web.md)。

不過，避免使用 RLS 有幾個相關聯的缺點：

- **多個工作區：** 需要針對每個報表使用者對象建立一個工作區。 如果已發佈應用程式，這也代表每個報表使用者對象都會有一個應用程式。
- **內容的重複：** 必須在每個工作區中建立報表和儀表板。 需要花費額外的作業和時間才能加以設定及維護。
- **高權限使用者：** 屬於多個報表使用者對象的高權限使用者，並無法看見彙總的資料檢視。 他們必須開啟來自不同工作區或應用程式的多個報表。

## <a name="troubleshoot-rls"></a>對 RLS 進行疑難排解

如果 RLS 產生非預期的結果，請檢查下列問題：

- 模型資料表之間，在資料行對應和篩選方向方面存在不正確的關聯性。
- 未正確設定 [雙向套用安全性篩選] 關聯性屬性。 如需詳細資訊，請參閱[雙向關聯性指導方針](relationships-bidirectional-filtering.md)。
- 資料表沒有包含任何資料。
- 將不正確的值載入資料表。
- 使用者已對應至多個角色。
- 模型包含彙總資料表，且 RLS 規則無法一致地篩選彙總和詳細資料。 如需詳細資訊，請參閱[在 Power BI Desktop 中使用彙總 (適用於彙總的 RLS)](../transform-model/desktop-aggregations.md#rls-for-aggregations)。

當特定使用者看不見任何資料時，這可能是因為其 UPN 並未儲存，或是以不正確的方式輸入。 這可能會因為其使用者帳戶因名稱變更而變更，所以突然發生。

> [!TIP]
> 基於測試目的，請新增會傳回 [USERNAME](/dax/username-function-dax) DAX 函數的量值。 您可以將其命名為類似 "Who Am I" (我是誰) 的名稱。 然後將該量值新增到報表中的卡片視覺效果，並將其發佈至 Power BI。

當特定使用者可以看見所有資料時，他們可能是直接存取工作區中的報表，且擁有資料集擁有者的身分。 RLS 只有在下列時機才會強制執行：

- 報表已在應用程式中開啟。
- 報表已在工作區中開啟，且使用者已對應至[檢視者角色](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces)。

## <a name="next-steps"></a>後續步驟

如需本文的詳細資訊，請參閱下列資源：

- [Power BI 的資料列層級安全性 (RLS)](../admin/service-admin-rls.md)
- [使用 Power BI Desktop 的資料列層級安全性 (RLS) 來限制資料存取](../create-reports/desktop-rls.md)
- [Power BI Desktop 中的模型關聯性](../transform-model/desktop-relationships-understand.md)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com/)
