---
title: 何時使用 Power BI 中的編頁報表
description: 何時使用 Power BI 編頁報表的指導。
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/04/2020
ms.author: v-pemyer
ms.openlocfilehash: 169a94beab8cb5b4c44105aba4c1cdf02e902c06
ms.sourcegitcommit: 4ac9447d1607dfca2e60948589f36a3d64d31cb4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2020
ms.locfileid: "92916858"
---
# <a name="when-to-use-paginated-reports-in-power-bi"></a>何時使用 Power BI 中的編頁報表

本文適用於設計 Power BI 報表的報表作者。 其中提供建議來協助您選擇何時開發 [Power BI 編頁報表](../paginated-reports/paginated-reports-report-builder-power-bi.md)。

> [!NOTE]
> 需有 Power BI Premium 訂用帳戶才能發佈 Power BI 編頁報表。 只有當報表位於已啟用[編頁報表工作負載](../admin/service-admin-premium-workloads.md#paginated-reports)容量的工作區時才會轉譯。

Power BI 編頁報表已針對 **列印** 或 **PDF 產生** 進行最佳化。 其也能讓您產生高度格式化、細節完美的版面配置。 因此，編頁報表很適合用於營運報表，例如銷售發票。

相反地，Power BI 報表已針對 **探索和互動** 進行最佳化。 此外，其也可使用各式各樣的超現代化視覺效果來呈現您的資料。 因此，Power BI 報表非常適合分析報表，可讓您的報表使用者探索資料，以及發掘關聯性與模式。

我們建議您在下列情況中考慮使用 Power BI 編頁報表：

- 您知道報表必須列印，或以 PDF 文件的形式輸出。
- 資料格版面配置可以擴展並溢位。 假設 Power BI 報表中的資料表或矩陣無法動態調整大小以顯示所有資料—其會改為提供捲軸。 但是，如果列印，就無法捲動以顯示任何看不到的資料。
- Power BI 編頁特性和功能會以您偏好的方式運作。 本文稍後會說明許多這類報表案例。

## <a name="legacy-reports"></a>舊版報表

當您已經有 SQL Server Reporting Services (SSRS) [報表定義語言 (RDL)](/sql/reporting-services/reports/report-definition-language-ssrs) 報表時，您可以選擇將其重新開發為 [Power BI 報表](../consumer/end-user-reports.md)，或將其當作編頁報表遷移至 Power BI。 如需詳細資訊，請參閱[將 SQL Server Reporting Services 報表遷移到 Power BI](migrate-ssrs-reports-to-power-bi.md)。

發佈至 Power BI 工作區之後，編頁報表可與 Power BI 報表並存使用。 然後其可使用 [Power BI 應用程式](../collaborate-share/service-create-distribute-apps.md)輕鬆地散發。

您可以考慮重新開發 SSRS 報表，而不是進行遷移。 對於旨在提供分析體驗的報表而言，更是如此。 在這些情況下，Power BI 報表可能會提供更好的報表使用者體驗。

## <a name="paginated-report-scenarios"></a>編頁報表案例

當您想要開發 Power BI 編頁報表時，有許多吸引人的案例。 許多是 Power BI 報表不支援的功能或功能。

- **列印就緒** ：編頁報表已針對列印或 PDF 產生進行最佳化。 必要時，資料區域可以受控制的方式擴展並溢位至多個頁面。 您的報表版面配置可以定義邊界及頁首和頁尾。
- **轉譯格式** ：Power BI 可以不同的格式來呈現編頁報表。 這些格式包括 Microsoft Excel、Microsoft Word、Microsoft PowerPoint、PDF、CSV、XML 和 MHTML。 (MHTML 格式是由 Power BI 服務用來呈現報表。)您的報表使用者可以決定以適合的格式匯出。
- **精確版面配置** ：您可以設計高度格式化、細節完美的版面配置—達到以英吋或公分為單位設定的確切大小和位置。
- **動態版面配置** ：您可設定許多報表屬性來使用 VB.NET 運算式，以產生高度回應的版面配置。 運算式可以存取許多核心 .NET Framework 程式庫。
- **轉譯特定的版面配置** ：您可以根據套用的轉譯格式，使用運算式來修改報表版面配置。 例如，您可以設計報表，以在使用非互動式格式 (例如 PDF) 轉譯時，停用可見度切換 (以達成向下切入和向上切入)。
- **原生查詢** ：您不需要先開發 Power BI 資料集。 您可針對任何[支援的資料來源](../paginated-reports/paginated-reports-data-sources.md)，撰寫原生查詢 (或使用預存程序)。 查詢可以包含參數化。
- **圖形查詢設計工具** ：Power BI 報表產生器包含圖形查詢設計工具，可協助您撰寫和測試資料集查詢。
- **靜態資料集** ：您可以定義資料集，並將資料直接輸入報表定義中。 這項功能特別適用於支援示範，或提供概念證明 (POC)。
- **資料整合** ：您可以結合來自不同資料來源的資料，或搭配靜態資料集。 其做法是使用 VB.NET 運算式建立自訂欄位。
- **參數化** ：您可以設計高度自訂的參數化體驗，包括資料驅動和串聯參數。 也可以定義參數預設值。 這些體驗可設計為協助您的報表使用者快速設定適當的篩選條件。 此外，參數不需要篩選報表資料；其可用來支援「假設」案例，或動態篩選或樣式設定。
- **影像資料** ：當影像以二進位格式儲存在資料來源時，您的報表可以呈現影像。
- **自訂程式碼** ：您可以在報表中開發 VB.NET 函式的程式碼區塊，並在任何報表運算式中使用這些區塊。
- **子報表** ：您可以將其他 Power BI 編頁報表 (從相同的工作區) 內嵌至報表中。
- **彈性資料格** ：您可以使用 tablix 資料區域，對資料格版面配置進行精細的控制。 其也支援複雜的版面配置，包括巢狀和相鄰群組。 而且，其可設定為在多個頁面上列印時重複標題。 此外，其可內嵌子報表或其他視覺效果，包括資料橫條、走勢圖和指標。
- **空間資料類型** ：地圖資料區域可以將 [SQL Server 空間資料類型](/sql/relational-databases/spatial/spatial-data-sql-server)視覺化。 因此，GEOGRAPHY 和 GEOMETRY 資料類型可用來視覺化點、線條或多邊形。 您也可以將 ESRI 圖形檔案中定義的多邊形視覺化。
- **新式量測計** ：星形和線性量測計可用來顯示 KPI 值和狀態。 其甚至可以內嵌到方格資料區域中 (在群組內重複)。
- **HTML 轉譯** ：當文字儲存為 HTML 時，您可以顯示豐富格式的文字。
- **合併列印** ：您可以使用文字方塊預留位置，將資料值插入文字中。 如此一來，您就可以產生合併列印報表。
- **互動功能** ：互動式功能包括切換可見度 (以達成向下切入和向上切入)、連結、互動式排序和工具提示。 您也可以新增可在 Power BI 報表或其他 Power BI 編頁報表中鑽研的連結。 連結甚至可以跳至相同報表中的另一個位置。
- **訂用帳戶** ：Power BI 可將排程上的編頁報表當作電子郵件傳遞，並帶有任何支援格式的報表附件。
- **每個使用者的版面配置** ：您可以根據開啟報表的已驗證使用者，建立回應式報表版面配置。 您可以設計報表，以不同方式篩選資料、隱藏資料區域或視覺效果、套用不同的格式，或設定使用者特定的參數預設值。

## <a name="next-steps"></a>後續步驟

如需本文的詳細資訊，請參閱下列資源：

- [什麼是 Power BI Premium 中的編頁報表？](../paginated-reports/paginated-reports-report-builder-power-bi.md)
- [將 SQL Server Reporting Services 報表遷移到 Power BI](migrate-ssrs-reports-to-power-bi.md)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com/)
