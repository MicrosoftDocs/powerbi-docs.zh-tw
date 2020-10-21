---
title: 在分頁報表中使用串聯參數
description: 使用串聯參數設計分頁報表的指引。
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/14/2020
ms.author: v-pemyer
ms.openlocfilehash: f239622d8b6012913298212790f7f9aa8c3115a5
ms.sourcegitcommit: 1428acb6334649fc2d3d8ae4c42cfbc17e8f7476
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2020
ms.locfileid: "92197648"
---
# <a name="use-cascading-parameters-in-paginated-reports"></a>在分頁報表中使用串聯參數

本文適用於設計 Power BI [分頁報表](../paginated-reports/paginated-reports-report-builder-power-bi.md)的報表作者。 其中會提供設計串聯參數的案例。 串聯參數是具有相依性的報表參數。 當報表使用者選取參數值時，這些值會用來設定另一個參數的可用值。

> [!NOTE]
> 本文並未介紹串聯參數及其設定方式。 如果您尚未完全熟悉串聯參數，建議您先閱讀[將串聯參數加入至報表 (報表產生器及 SSRS)](/sql/reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs)。

## <a name="design-scenarios"></a>設計案例

使用串聯參數的設計案例有兩種。 這些案例可以有效地用來執行下列動作：

- 篩選「大型項目集合」
- 顯示「相關的」項目

### <a name="example-database"></a>資料庫範例

本文中顯示的範例會以 Azure SQL Database 為基礎。 資料庫會記錄銷售作業，並且包含用來保存轉銷商、產品和銷售訂單的各種資料表。

名為**轉銷商**的資料表會為每個轉銷商儲存一筆記錄，而其中可包含數千筆記錄。 **轉銷商**資料表有這些資料行：

- ResellerCode (整數)
- ResellerName
- 國家/地區
- State-Province
- 城市
- 郵遞區號

另外還有一個名為**銷售**的資料表。 該資料表會儲存銷售訂單記錄，並在 **ResellerCode** 資料行上有**轉銷商**資料表的外部索引鍵關聯性。

### <a name="example-requirement"></a>需求範例

有一個要開發轉銷商資料報表的需求。 該報表必須設計為顯示單一轉銷商的資訊。 讓報表使用者輸入轉銷商代碼並不適合，因為他們很少會記住這些代碼。

## <a name="filter-large-sets-of-items"></a>篩選大型項目集合

讓我們來看一下三個範例，協助您了解如何限制大型的可用項目集合 (例如轉銷商)。 其中包括：

- [按照相關資料行篩選](#filter-by-related-columns)
- [按照群組資料行篩選](#filter-by-a-grouping-column)
- [按照搜尋模式篩選](#filter-by-search-pattern)

### <a name="filter-by-related-columns"></a>按照相關資料行篩選

在此範例中，報表使用者會與五個報表參數互動。 他們必須選取國家/地區、州/省、城市和郵遞區號。 然後最後一個參數會列出位於該地理位置的轉銷商。

![Power B I 分頁報表參數的螢幕擷取畫面，其中顯示依相關資料行進行篩選。](media/paginated-report-cascading-parameter/filter-by-related-columns-example.png)

以下是您可以用來開發串聯參數的方法：

1. 建立五個報表參數，並以正確的順序排序。
2. 使用下列查詢陳述式，建立可擷取不同國家/地區值的 **CountryRegion** 資料集：

    ```sql
    SELECT DISTINCT
      [Country-Region]
    FROM
      [Reseller]
    ORDER BY
      [Country-Region]
    ```

3. 使用下列查詢陳述式，建立可針對所選國家/地區擷取不同州/省值的 **StateProvince** 資料集：

    ```sql
    SELECT DISTINCT
      [State-Province]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
    ORDER BY
      [State-Province]
    ```

4. 使用下列查詢陳述式，建立可針對所選國家/地區和州/省擷取不同城市值的 **City** 資料集：

    ```sql
    SELECT DISTINCT
      [City]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
      AND [State-Province] = @StateProvince
    ORDER BY
      [City]
    ```

5. 繼續此模式，以建立 **PostalCode** 資料集。
6. 使用下列查詢陳述式，建立可針對所選地理位置值擷取所有轉銷商的 **Reseller** 資料集：

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      [Country-Region] = @CountryRegion
      AND [State-Province] = @StateProvince
      AND [City] = @City
      AND [PostalCode] = @PostalCode
    ORDER BY
      [ResellerName]
    ```

7. 針對每個資料集 (第一個除外)，將查詢參數對應至相對應的報表參數。

> [!NOTE]
> 這些範例中所顯示的所有查詢參數 (前面加上 @ 符號的參數) 可能會內嵌在 SELECT 陳述式內，或傳遞給預存程序。
>
> 一般而言，預存程序是比較好的設計方法。 因為其查詢計劃會經過快取以加快執行速度，並可讓您在需要時開發更精密的邏輯。 不過，閘道關聯式資料來源 (也就是 SQL Server、Oracle 和 Teradata) 目前不支援這些預存程序。
>
> 最後，必須有適當的索引，才能支援有效率的資料擷取。 否則，您報表參數的填入速度可能會很慢，而資料庫可能會變得負擔過重。 如需 SQL Server 索引編製的詳細資訊，請參閱 [SQL Server 索引架構和設計指南](/sql/relational-databases/sql-server-index-design-guide)。

### <a name="filter-by-a-grouping-column"></a>按照群組資料行篩選

在此範例中，報表使用者會與報表參數互動，以選取轉銷商的第一個字母。 第二個參數則會在名稱開頭為選取的字母時，列出轉銷商。

![Power B I 分頁報表參數的螢幕擷取畫面，其中顯示依群組資料行進行篩選。](media/paginated-report-cascading-parameter/filter-by-grouping-column-example.png)

以下是您可以用來開發串聯參數的方法：

1. 建立 **ReportGroup** 和 **Reseller** 報表參數，並以正確的順序排序。
2. 使用下列查詢陳述式，建立 **ReportGroup** 資料集來擷取所有轉銷商使用的前幾個字母：

    ```sql
    SELECT DISTINCT
      LEFT([ResellerName], 1) AS [ReportGroup]
    FROM
      [Reseller]
    ORDER BY
      [ReportGroup]
    ```

3. 使用下列查詢陳述式建立 **Reseller** 資料集，以擷取開頭為所選字母的所有轉銷商：

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      LEFT([ResellerName], 1) = @ReportGroup
    ORDER BY
      [ResellerName]
    ```

4. 將 **Reseller** 資料集的查詢參數對應至相對應的報表參數。

將群組資料行新增至 **Reseller** 資料表會更有效率。 若加以保存和編製索引，則可提供最佳結果。 如需詳細資訊，請參閱 [Specify Computed Columns in a Table](/sql/relational-databases/tables/specify-computed-columns-in-a-table)。

```sql
ALTER TABLE [Reseller]
ADD [ReportGroup] AS LEFT([ResellerName], 1) PERSISTED
```

此技術可以提供更高的可能。 請考慮使用下列指令碼，以新增群組資料行來依據「預先定義的一組字母」篩選轉銷商。 該指令碼也會建立索引，以有效率地擷取報表參數所需的資料。

```sql
ALTER TABLE [Reseller]
ADD [ReportGroup2] AS CASE
  WHEN [ResellerName] LIKE '[A-C]%' THEN 'A-C'
  WHEN [ResellerName] LIKE '[D-H]%' THEN 'D-H'
  WHEN [ResellerName] LIKE '[I-M]%' THEN 'I-M'
  WHEN [ResellerName] LIKE '[N-S]%' THEN 'N-S'
  WHEN [ResellerName] LIKE '[T-Z]%' THEN 'T-Z'
  ELSE '[Other]'
END PERSISTED
GO

CREATE NONCLUSTERED INDEX [Reseller_ReportGroup2]
ON [Reseller] ([ReportGroup2]) INCLUDE ([ResellerCode], [ResellerName])
GO
```

### <a name="filter-by-search-pattern"></a>按照搜尋模式篩選

在此範例中，報表使用者會與報表參數互動，以輸入搜尋模式。 第二個參數則會在名稱包含該模式時，列出轉銷商。

![Power B I 分頁報表參數的螢幕擷取畫面，其中顯示依搜尋模式進行篩選。](media/paginated-report-cascading-parameter/filter-by-search-pattern-example.png)

以下是您可以用來開發串聯參數的方法：

1. 建立 **Search** 和 **Reseller** 報表參數，並以正確的順序排序。
2. 使用下列查詢陳述式建立 **Reseller** 資料集，以擷取包含搜尋文字的所有轉銷商：

    ```sql
    SELECT
      [ResellerCode],
      [ResellerName]
    FROM
      [Reseller]
    WHERE
      [ResellerName] LIKE '%' + @Search + '%'
    ORDER BY
      [ResellerName]
    ```

3. 將 **Reseller** 資料集的查詢參數對應至相對應的報表參數。

> [!TIP]
> 您可以在此設計上做些改良，為您的報表使用者提供更多控制權。 此方法可讓他們定義自己的模式比對值。 例如，搜尋值 "red%" 將會篩選出名稱「開頭」為 "red" 字元的轉銷商。
>
> 如需詳細資訊，請參閱 [LIKE (Transact-SQL)](/sql/t-sql/language-elements/like-transact-sql#using-the--wildcard-character)。

以下是您可以讓報表使用者定義自有模式的方式。

```sql
WHERE
  [ResellerName] LIKE @Search
```

不過，許多非資料庫專家並不知道百分比 (%) 萬用字元的用處。 相反地，他們熟悉的是星號 (*) 字元。 藉由修改 WHERE 子句，您可以讓他們使用此字元。

```sql
WHERE
  [ResellerName] LIKE SUBSTITUTE(@Search, '%', '*')
```

## <a name="present-relevant-items"></a>顯示相關的項目

在此案例中，您可以使用事實資料來限制可用值。 報表使用者會看到已記錄活動的項目。

在此範例中，報表使用者會與三個報表參數互動。 前兩個會設定銷售訂單日期的日期範圍。 第三個參數接著會列出其訂單在該時段內建立的轉銷商。

![Power B I 分頁報表參數的螢幕擷取畫面，其中顯示三個報表參數：起始訂單日期、結束訂單日期和轉銷商。](media/paginated-report-cascading-parameter/filter-relevant-items-example.png)

以下是您可以用來開發串聯參數的方法：

1. 建立 **OrderDateStart**、**OrderDateEnd** 和 **Reseller** 報表參數，並以正確的順序排序。
2. 使用下列查詢陳述式建立 **Reseller** 資料集，以擷取在該日期期間建立訂單的所有轉銷商：

    ```sql
    SELECT DISTINCT
      [r].[ResellerCode],
      [r].[ResellerName]
    FROM
      [Reseller] AS [r]
    INNER JOIN [Sales] AS [s]
      ON [s].[ResellerCode] = [r].[ResellerCode]
    WHERE
      [s].[OrderDate] >= @OrderDateStart
      AND [s].[OrderDate] < DATEADD(DAY, 1, @OrderDateEnd)
    ORDER BY
      [r].[ResellerName]
    ```

## <a name="recommendations"></a>建議

我們建議您盡可能使用串聯參數來設計報表。 這是因為這些參數：

- 為您的報表使用者提供直覺且實用的體驗
- 效率高，因為這些參數會抓取較小的可用值集合

請務必使用下列方法將您的資料來源最佳化：

- 盡可能使用預存程序
- 加入適當的索引以提高資料擷取效率
- 具體化資料行值 (甚至是資料列)，以避免耗費資源的查詢時間評估

## <a name="next-steps"></a>後續步驟

如需本文的詳細資訊，請參閱下列資源：

- [Power BI Report Builder 中的報表參數](../paginated-reports/report-builder-parameters.md)
- [將串聯參數加入至報表 (報表產生器及 SSRS)](/sql/reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com)
