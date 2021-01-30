---
title: Power BI Desktop 中的 Analysis Services 多維度資料
description: Power BI Desktop 中的 SQL Server Analysis Services (SSAS) 多維度資料
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 01/15/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: b3ff42b33ccf2d93217d9d88ada4dfbe45a5436c
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99085444"
---
# <a name="connect-to-ssas-multidimensional-models-in-power-bi-desktop"></a>連線到 Power BI Desktop 中的 SSAS 多維度模型

使用 Power BI Desktop，您可以存取「SSAS 多維度模型」  ，通常稱為 *SSAS MD*。

若要連線至 SSAS MD 資料庫，請選取 [取得資料]  ，選擇 [資料庫]   > [SQL Server Analysis Services 資料庫]  ，然後選取 [連線]  ：

![SQL Server Analysis Services (SSAS) 資料庫，[取得資料] 對話方塊，Power BI Desktop](media/desktop-ssas-multidimensional/ssas-multidimensional-2.png)

Power BI 服務和 Power BI Desktop 皆支援即時連線模式中的 SSAS 多維度模型。 您也可以將使用即時模式中 **SSAS 多維度模型** 的報表發佈並上傳至 Power BI 服務。

## <a name="capabilities-and-features-of-ssas-md"></a>SSAS MD 的功能與特點

下列章節說明 Power BI 和 SSAS MD 連接的功能與特點。

### <a name="tabular-metadata-of-multidimensional-models"></a>多維度模型的表格式中繼資料

下表顯示多維度物件與表格式中繼資料之間傳回至 Power BI Desktop 的通信。 Power BI 會查詢表格式中繼資料的模型。 在您建立視覺效果 (例如資料表、矩陣、圖表或交叉分析篩選器) 時，Power BI Desktop 會根據傳回的中繼資料，對 SSAS 執行適當的 DAX 查詢。

| BISM 多維度物件 | 表格式中繼資料 |
| --- | --- |
| Cube |模型 |
| Cube 維度 |資料表 |
| 維度屬性 (索引鍵)、名稱 |行 |
| 量值群組 |資料表 |
| 量值 |量值 |
| 不含相關聯量值群組的量值 |在稱為「 *量值* 」的資料表內 |
| 量值群組 -> Cube 維度關聯性 |關聯性 |
| 檢視方塊 |檢視方塊 |
| KPI |KPI |
| 使用者/父子式階層 |階層 |

### <a name="measures-measure-groups-and-kpis"></a>量值、量值群組和 KPI

多維度 Cube 中的量值群組會作為資料表公開，位於 [欄位]  窗格中，旁邊含 Sigma (∑) 符號。 沒有相關聯量值群組的導出量值，會分組於表格式中繼資料中稱為「量值」  的特殊資料表下方。

若要在多維度模型中簡化複雜的模型，您可以在 Cube 中定義一組量值或 KPI，使其位於「顯示資料夾」  內。 Power BI 會辨識表格式中繼資料中的顯示資料夾，並在顯示資料夾中顯示量值和 KPI。 多維度資料庫中的 KPI 支援「值」  、「目標」  、「狀態圖形」  和「趨勢圖形」  。

### <a name="dimension-attribute-type"></a>維度屬性類型

多維度模型也支援與特定維度屬性類型相關聯的維度屬性。 例如，[地理位置]  維度中的「城市」  、「省/市」  、「國家/地區」  和「郵遞區號」  維度屬性，都有與其建立關聯的適當地理位置類型，會公開在表格式中繼資料中。 Power BI 會辨識中繼資料，讓您可以建立地圖視覺效果。 您可根據 Power BI 中 [欄位]  窗格中項目旁邊的「地圖」  圖示來辨識這些關聯。

當您提供包含影像 URL (統一資源定位器) 的欄位時，Power BI 也可以轉譯影像。 您可以在 SQL Server Data Tools 中 (或在 Power BI 中) 將這些欄位指定為 *ImageURL* 類型。 然後其類型資訊會在表格式中繼資料中提供給 Power BI。 Power BI 即可從 URL 擷取這些影像，並以視覺方式顯示。

### <a name="parent-child-hierarchies"></a>父子式階層

多維度模型支援父子式階層，可在表格式中繼資料中顯示為「階層」  。 父子式階層的每個層級，都會公開為表格式中繼資料中的隱藏資料行。 父子式維度的索引鍵屬性不會公開在表格式中繼資料中。

### <a name="dimension-calculated-members"></a>維度的導出成員

多維度模型支援建立各種「導出成員」  類型。 兩種最常見的導出成員類型為：

* 屬性階層上不屬於與「所有」  同層級的導出成員
* 使用者階層的導出成員

多維度模型會公開「屬性階層上的導出成員」  作為資料行的值。 如果公開這類型的導出成員，則您有幾個額外選項和條件約束：

* 維度屬性可以有選用的 *UnknownMember*。

* 包含導出成員的屬性，不可以是維度的索引鍵屬性，除非其是該維度唯一的屬性。

* 包含導出成員的屬性不可以是父子式屬性。

使用者階層的導出成員不會公開於 Power BI 中。 您可以改為連線至在使用者階層上包含導出成員的 Cube。 不過，如果導出成員不符合我們在前一個項目符號清單中所述的條件約束，您就無法看到這些導出成員。

### <a name="security"></a>安全性

多維度模型透過「角色」  支援維度和資料格層級的安全性。 當您使用 Power BI 連線至 Cube 時，會驗證和評估您是否有適當權限。 如果使用者套用了「維度安全性」  ，則 Power BI 中使用者無法看到個別的維度成員。 不過，當使用者定義了「資料格安全性」  權限，且其中某些資料格受到限制，則該使用者無法使用 Power BI 連線至 Cube。

## <a name="considerations-and-limitations"></a>考量與限制

使用 SSAS MD 具有某些限制：

* 只有 SQL Server 2014 的 Enterprise 和 BI 版本支援即時連線。 針對 SQL Server Standard 版本，則需要 SQL Server 2016 或更新版本才能進行即時連線。

* 「動作」  和「命名集」  不會公開至 Power BI。 若要建立視覺效果和報表，您仍然可以連線至同樣包含動作或命名集的 Cube。

* 當 Power BI 顯示 SSAS 模型的中繼資料時，您會偶爾無法從模型擷取資料。 如果您安裝了 32 位版本 (而不是 64 位元版本) 的 MSOLAP 提供者，就可能發生此情況。 安裝 64 位元版本可解決此問題。

* 在撰寫即時連線至 SSAS 多維度模型的報表時，您無法建立「報表層級」  量值。 唯一可用量值是 MD 模型中定義的量值。

## <a name="supported-features-of-ssas-md-in-power-bi-desktop"></a>Power BI Desktop 中 SSAS MD 支援的功能

此版本 SSAS MD 支援下列項目的使用。 如需這些功能的詳細資訊，請參閱[了解適用於多維度模型的 Power View](/sql/analysis-services/multidimensional-models/understanding-power-view-for-multidimensional-models)。

* 預設成員
* [維度屬性]
* 維度屬性類型
* 維度的導出成員：
  * 維度具有超過一個屬性時，必須是單一真實成員；
  * 不可以是維度的索引鍵屬性，除非其是唯一的屬性；以及
  * 不可以是父子式屬性。
* 維度安全性
* 顯示資料夾
* 階層
* ImageUrls
* KPI
* KPI 趨勢
* 量值 (不論有無量值群組)
* 量值作為變化

## <a name="troubleshooting"></a>疑難排解

下列清單描述了連線至 SQL Server Analysis Services (SSAS) 時的所有已知問題。

* **錯誤:無法載入模型結構描述** - 此錯誤通常會在不具有資料庫或 Cube 存取權的使用者連線至 Analysis Services 時發生。
