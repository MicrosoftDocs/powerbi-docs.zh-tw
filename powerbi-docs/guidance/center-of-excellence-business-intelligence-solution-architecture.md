---
title: 卓越中心內的 BI 方案架構
description: 了解設計和開發強固 BI 平台時要考量的事項。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 11/11/2020
ms.openlocfilehash: 88d1e19435207ca094bd9cb1cba770c1cb54573f
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96394627"
---
# <a name="bi-solution-architecture-in-the-center-of-excellence"></a>卓越中心內的 BI 方案架構

本文的對象是 IT 專業人員和 IT 管理員。 您將了解 COE 中 BI 方案架構和所採用的不同技術。 這些技術包括 Azure、Power BI 和 Excel。 您可利用這些技術來傳遞可調整和資料驅動的雲端 BI 平台。

設計強固的 BI 平台，即如同建造將轉換和擴充來源資料連接到資料取用者的橋樑。 設計這種複雜的結構需要工程思維，雖然這種結構可能會是所設計結構中最富創意及成就感最高的 IT 結構。 在大型組織中，BI 方案架構可以包含下列各項：

- 資料來源
- 資料擷取
- 巨量資料/資料準備
- 資料倉儲
- BI 語意模型
- 報表

:::image type="content" source="media/center-of-excellence-business-intelligence-solution-architecture/azure-business-intelligence-platform.png" alt-text="顯示 BI 平台架構圖的圖表，從資料來源，到資料擷取、巨量資料、存放區、資料倉儲、BI 語意模型、報告和機器學習。":::

平台必須支援特定需求。 具體而言，其必須進行縮放及執行，以符合商務服務和資料取用者的預期。 同時，其必須從一開始便是安全的。 此外，其必須具備足夠的彈性以適應變更，因為隨著時間的進展，一定會有新的資料和主題領域上線。

## <a name="frameworks"></a>架構

在 Microsoft，我們從一開始便已藉由投資架構開發來採用類似系統的方法。 技術和商務程序架構可增加設計和邏輯的重複使用，並提供一致的結果。 其也提供利用許多技術的結構彈性，且透過可重複程序來簡化和減少工程的額外負荷。

我們已了解設計良好的架構可提高資料譜系、影響分析、商務邏輯維護、管理分類和簡化治理的可見度。 此外，也能加速開發且使大型小組的共同作業回應性更佳且更有效率。

我們將在本文中描述其中幾個架構。

## <a name="data-models"></a>資料模型

資料模型提供控制資料結構化和存取的方式。 針對商務服務和資料取用者，資料模型是其與 BI 平台的介面。

BI 平台可傳遞三種不同的模型類型：

- 企業模型
- BI 語意模型
- 機器學習 (ML) 模型

### <a name="enterprise-models"></a>企業模型

**企業模型** 是由 IT 架構師所建置及維護。 有時候這種模型也稱為維度模型或資料超市。 通常，資料會作為維度和事實資料表儲存在關聯式格式中。 這些資料表會儲存合併自許多系統並經過清理和擴充的資料，且其代表用於報告和分析的權威來源。

企業模型可傳遞一致和單一的資料來源來用於報告和 BI。 這些模型只需要建置一次，並可作為企業標準共用。 治理原則可確保資料安全，因此會根據需求對敏感性資料集的存取 (例如客戶資訊或財務資訊) 進行限制。 這種模型採用確保一致性的命名慣例，因此可進一步建立資料的可信度和品質。

在雲端 BI 平台中，企業模型可部署到 [Azure Synapse 中的 Synapse SQL 集區](/azure/synapse-analytics/sql-data-warehouse/sql-data-warehouse-overview-what-is#synapse-sql-pool-in-azure-synapse)。 Synapse SQL 集區接著會成為組織可信任的單一事實版本，用來取得快速且強固的見解。

### <a name="bi-semantic-models"></a>BI 語意模型

**BI 語意模型** 代表企業模型上的語意層。 這些模型由 BI 開發人員和商務使用者所建置及維護。 BI 開發人員會建立從企業模型取得來源資料的核心 BI 語意模型。 商務使用者可建立規模較小的獨立模型，或是使用部門或外部來源，延伸核心 BI 語意模型。 BI 語意模型通常會聚焦於單一主題領域，且通常會廣泛共用。

商務功能不單純是由資料啟用的，也是由描述概念、關係、規則和標準的 BI 語意模型所啟用。 透過這種方式，其可代表直覺且易於了解的結構，以定義資料關係並將商務規則作為計算封裝。 這些模型也可以強制施行細部資料權限，確保正確的人員能夠存取正確資料。 重要的是，這些模型可加速查詢效能，提供回應性極佳的互動分析，即使資料高達數 TB 也一樣。 與企業模型相似，BI 語意模型會採用命名慣例，確保一致性。

在雲端 BI 平台中，BI 開發人員可將 BI 語意模型部署到 [Azure Analysis Service](/azure/analysis-services/) 或 [Power BI Premium 容量](../admin/service-premium-what-is.md#reserved-capacities)。 若將其作為報告和分析層使用，則建議部署到 Power BI。 這些產品支援不同的儲存體模型，可供資料模型資料表快取資料或使用 [DirectQuery](directquery-model-guidance.md)，這是一種將查詢傳遞至基礎資料來源的技術。 當模型資料表代表大量資料，或需要傳遞近乎即時的結果時，DirectQuery 即為理想的儲存體模型。 您可合併兩個儲存體模式：[複合模型](composite-model-guidance.md)會在單一模型中合併使用不同儲存體模式的資料表。

針對大量查詢的模型，您可使用 [Azure Load Balancer](/azure/load-balancer/load-balancer-overview) 來將查詢負載平均分散到模型複本。 其也可供調整應用程式大小，並建立高度可用的 BI 語意模型。

### <a name="machine-learning-models"></a>機器學習模型

[**機器學習 (ML) 模型**](/windows/ai/windows-ml/what-is-a-machine-learning-model)是由資料科學家所建置和維護。 這些模型大多數都是從資料湖中原始來源開發的。

經過定型後的 ML 模型可揭露資料中模式。 在許多情況下，這些模式可用來進行預測，而這些預測則可以用來擴充資料。 例如，購買行為可用來預測客戶流失或細分客戶。 預測結果可新增到企業模型中，讓客戶區段進行分析。

在雲端 BI 平台中，您可使用 [Azure Machine Learning](/azure/machine-learning/overview-what-is-azure-ml) 來定型、部署、自動化、管理和追蹤 ML 模型。

## <a name="data-warehouse"></a>資料倉儲

BI 平台的中心則是資料倉儲，資料倉儲會裝載企業模型。 這是獲批准資料的來源 (作為記錄系統和中樞)，可提供企業模型以用於報告、BI 和資料科學。

許多商務服務 (包括企業營運 (LOB) 應用程式) 可依賴資料倉儲作為權威和經過治理的企業知識來源。

在 Microsoft，資料倉儲是裝載在 [Azure Data Lake Storage Gen2](/azure/storage/blobs/data-lake-storage-introduction) (ADLS Gen2) 和 Azure Synapse Analytics 中。

:::image type="content" source="media/center-of-excellence-business-intelligence-solution-architecture/azure-data-warehouse.png" alt-text="顯示 Azure Synapse Analytics 連線到 Azure Data Lake Storage Gen2 的影像。":::

- **ADLS Gen2** 讓 Azure 儲存體成為在 Azure 上建置企業資料湖的基礎。 其旨在服務數 PB 的資訊，同時維持數百 GB 的輸送量。 此外，其可提供低成本的儲存體容量和交易。 除此之外，其支援 Hadoop 相容存取，這可供管理及存取資料，就如同使用 Hadoop 分散式檔案系統 (HDFS) 一樣。 事實上，[Azure HDInsight](/azure/hdinsight/)、[Azure Databricks](/azure/azure-databricks/what-is-azure-databricks) 和 Azure Synapse Analytics 全部都可存取儲存在 ADLS Gen2 中的資料。 因此，在 BI 平台中，儲存原始來源資料、半處理或暫存資料，以及生產環境就緒資料是良好的選擇。 我們使用此項目來儲存所有的商務資料。
- **Azure Synapse Analytics** 是一種分析服務，可將企業資料倉儲和巨量資料分析整合在一起。 可讓您自由使用無伺服器隨選或佈建資源，隨意且大規模地查詢您的資料。 Synapse SQL 是一種 Azure Synapse Analytics 的元件，支援完整的 T-SQL 式分析，因此非常適合裝載構成維度和事實資料表的企業模型。 資料表可使用簡易的 [Polybase T-SQL](/sql/relational-databases/polybase/polybase-guide) 查詢從 ADLS Gen2 有效率地載入。 接著，您可使用 [MPP](/azure/synapse-analytics/sql-data-warehouse/massively-parallel-processing-mpp-architecture#synapse-sql-mpp-architecture-components) 來執行高效能的分析。

### <a name="business-rules-engine-framework"></a>商務規則引擎架構

我們開發了一種 **商務規則引擎** (BRE) 架構來分類任何可在資料倉儲層中實作的商務邏輯。 BRE 可代表許多事物，但在資料倉儲的內容中，其適用於在關聯式資料表中建立計算結果欄。 這些計算結果欄通常會以數學計算或使用條件陳述式的運算式來表示。

其目的是要從核心 BI 程式碼分離商務邏輯。 傳統上，商務規則是硬式編碼在 SQL 預存程序中，因此經常會在需要變更商務時導致需要更多的工作來進行維護。 在 BRE 中，商務規則會定義一次，並在套用到不同的資料倉儲實體時使用多次。 若計算邏輯需要變更，其只需要在一個位置更新，而無須在多個預存程序中更新。 此外還有另外一項優點：BRE 架構可為實作的商務邏輯帶來透明度和可見度，並可透過建立自我更新文件的一組報表來公開。

## <a name="data-sources"></a>資料來源

資料倉儲可合併幾乎任何資料來源的資料。 其大多數都是建置在 LOB 資料來源上，這是一種常見的關聯式資料庫，可儲存特定主題的資料，例如銷售、行銷、財務等。這些資料庫可為雲端裝載，或可位於內部部署中。 其他資料來源可以是以檔案為基礎，特別是 Web 記錄或裝置的 IOT 資料。 此外，資料可以來自軟體即服務 (SaaS) 廠商。

在 Microsoft中，我們的一部分內部系統會使用原始檔案格式，將作業資料直接輸出到 ADLS Gen2。 除了資料湖之外，其他來源系統也會構成關聯式 LOB 應用程式、Excel 活頁簿、其他檔案式來源、主要資料管理 (MDM) 和自訂資料存放庫。 MDM 存放庫可供管理主要資料，以確保資料的權威、標準化和驗證版本。

## <a name="data-ingestion"></a>資料擷取

資料會以定期基礎及根據商務的節奏，從來源系統進行擷取，並載入資料倉儲。 這可能是一天一次，或更頻繁的間隔。 資料擷取通常與擷取、轉換和載入資料相關。 或者，另一種方式是：擷取、載入和轉換資料。 其差異在於發生轉換的位置。 轉換適用於清理、符合、整合和標準化資料。 如需詳細資訊，請參閱[擷取、轉換和載入 (ETL)](/azure/architecture/data-guide/relational-data/etl)。

最後，目標是將正確的資料盡可能快速且有效率地載入企業模型。

在 Microsoft，我們使用 [Azure Data Factory](/azure/data-factory/introduction) (ADF)。 這些服務會用來排程和協調資料驗證、轉換並從外部來源系統將資料大量載入至資料湖。 其由自訂架構所管理，用來以平行和大規模的方式處理資料。 此外，也會進行完整的記錄來支援疑難排解、效能監視，以及在符合特定條件時觸發警示通知。

同時，[Azure Databricks](/azure/azure-databricks/what-is-azure-databricks) 會執行適用於資料科學的轉換，這是一種針對 Azure 雲端服務平台最佳化的 Apache Spark 式分析平台。 其也可以使用 Python notebook 來建置和執行 ML 模型。 來自這些 ML 模型的分數會載入資料倉儲，將預測與企業應用程式和報表整合。 因為 Azure Databricks 會直接存取資料湖檔案，其可消除並將複製或取得資料的需求降至最低。

:::image type="content" source="media/center-of-excellence-business-intelligence-solution-architecture/azure-data-ingestion.png" alt-text="顯示 Azure Data Factory 使用 Azure Databricks 針對 Azure Data Lake Storage Gen2 取得資料及協調資料管線的影像。":::

### <a name="ingestion-framework"></a>擷取架構

我們開發了 **擷取架構** 來作為一組設定資料表和程序。 其支援使用資料驅動方式快速取得大量資料，且僅需要極少的程式碼。 簡單而言，架構可簡化取得資料以載入資料倉儲的程序。

架構相依於儲存資料來源和資料目的地相關資訊 (例如來源類型、伺服器、資料庫、結構描述和資料表相關詳細資料) 的設定資料表。 這種設計方式表示無需開發特定 ADF 管線或 [SQL Server Integration Services (SSIS)](/sql/integration-services/sql-server-integration-services) 套件。 我們會改為以所選語言來撰寫的程序，以建立動態產生並在執行階段執行的 ADF 管線。 因此，資料擷取即成為可輕鬆作業化的設定練習。 傳統上，建立硬式編碼的 ADF 或 SSIS 套件需要大量的開發資源。

擷取架構也旨在簡化處理上游來源結構描述變更的程序。 在偵測到結構描述變更時，以手動或自動方式取得來源系統中新增屬性來更新設定資料相當容易。

### <a name="orchestration-framework"></a>協調流程架構

我們開發了 **協調流程架構** 來作業化和協調資料管線。 其使用相依於一組設定資料表的資料驅動設計。 這些資料表可儲存描述管線相依性的中繼資料，以及如何將來源資料對應到目標資料結構。 投資在開發這種調適性的架構顯然值回票價；現在已不再需要針對每個資料移動進行硬式編碼。

## <a name="data-storage"></a>資料儲存體

資料湖可儲存大量的原始資料以供稍後搭配暫存資料轉換使用。

在 Microsoft，我們使用 ADLS Gen2 作為單一事實來源。 其會將原始資料與暫存資料和生產就緒資料一同儲存。 其可為巨量資料分析提供高度可調整和符合成本效益的資料湖解決方案。 將高效能檔案系統與大規模的威力合併，其已針對資料分析工作負載進行最佳化，可加速見解的時間。

ADLS Gen2 提供兩個世界的最佳選項：其是 BLOB 儲存體，也是高效能的檔案系統命名空間，而我們會使用細部的存取權限來設定此命名空間。

經過精簡後的資料接著會儲存在關聯式資料庫中，以傳遞高效能、高度可調整的企業模型資料存放區，且兼具安全性、治理和可管理性。 主題特定的資料超市則會儲存在 Azure Synpase Analytics 中，並由 Azure Databricks 或 Polybase T-SQL 查詢載入。

## <a name="data-consumption"></a>資料耗用量

在報告層中，商務服務會取用來自資料倉儲的企業資料。 其也會直接存取資料湖中的資料，以進行臨機分析或資料科學工作。

細部權限會在所有層上強制施行：在資料湖、企業模型，以及 BI 語意模型中。 權限可確保資料取用者只會看見其具備存取權限的資料。

在 Microsoft，我們使用 Power BI 報表和儀表板，以及 [Power BI 編頁報表](../paginated-reports/paginated-reports-report-builder-power-bi.md)。 某些報告和臨機分析則會在 Excel 中完成，特別是財務報告。

我們會發佈資料字典，其提供資料模型的參考資訊。 這些字典可供使用者使用，以讓使用者探索 BI 平台的資訊。 字典記載了模型設計，可提供實體、格式、結構、資料譜系、關係和計算的描述。 我們使用 [Azure 資料目錄](/azure/data-catalog/overview)來讓資料來源易於探索及了解。

一般而言，資料取用模式會因角色而不同：

- **資料分析師** 會直接連線到核心 BI 語意模型。 當核心 BI 語意模型包含所有其需要的資料和邏輯時，資料分析師會使用即時連線來建立 Power BI 報表和儀表板。 當其需要使用部門資料延伸模型時，資料分析師會建立 Power BI [複合模型](composite-model-guidance.md)。 若需要試算表樣式的報表，資料分析師即會根據核心 BI 語意模型或部門 BI 語意模型，使用 Excel 產生報表。
- **BI 開發人員** 和作業報表作者會直接連線到企業模型。 這些開發人員會使用 Power BI Desktop 建立即時連線分析報表。 開發人員也可將作業類型的 BI 報表作為 Power BI 編頁報表編寫、使用 T-SQL 撰寫原生 SQL 查詢來存取 Azure Synapse Analytics 企業模型的資料，或是使用 DAX 或 MDX 存取 Power BI 語意模型的資料。
- **資料科學家** 會直接連線到資料湖中的資料。 資料科學家會使用 Azure Databricks 和 Python notebook 來開發 ML 模型，這些模型通常是實驗性的，且需要特殊技術才能用於生產用途。

:::image type="content" source="media/center-of-excellence-business-intelligence-solution-architecture/azure-data-warehouse-consumption.png" alt-text="圖片顯示搭配 Power BI、Excel 和 Azure Machine Learning 使用 Azure Synapse Analytics。":::

## <a name="next-steps"></a>後續步驟

如需本文的詳細資訊，請參閱下列資源︰

- [Azure 中搭配 Azure Synapse Analytics 的企業 BI](/azure/architecture/reference-architectures/data/enterprise-bi-synapse)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com/)

### <a name="professional-services"></a>專業服務

認證 Power BI 合作夥伴可協助貴組織成功設定 COE。 他們可為您提供符合成本效益的訓練或資料稽核。 若要與 Power BI 合作夥伴交流，請造訪 [Power BI 合作夥伴入口網站](https://powerbi.microsoft.com/partners/)。

您也可以與經驗豐富的諮詢合作夥伴進行互動。 他們可協助您[評定](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=assessment&country=ALL&region=ALL)、[評估](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=proof-of-concept&country=ALL&region=ALL)或[實作](https://appsource.microsoft.com/marketplace/consulting-services?product=power-bi&serviceType=implementation&country=ALL&region=ALL&page=1) Power BI。
