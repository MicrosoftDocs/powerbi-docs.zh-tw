---
title: Power BI 報表產生器中的報表資料
description: 您在 Power BI Report Builder 中設計報表的第一個步驟，便是建立代表基礎報表資料的資料來源和資料集。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.custom: seodec18
ms.date: 08/04/2020
ms.openlocfilehash: 97b93f23c8070af1b514032cea122b257097d664
ms.sourcegitcommit: 9d033abd9c01a01bba132972497dda428d7d5c12
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96120637"
---
# <a name="report-data-in-power-bi-report-builder"></a>Power BI 報表產生器中的報表資料

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

報表資料可以來自您組織中的多個資料來源。 您在設計報表時的第一個步驟，便是建立代表基礎報表資料的資料來源和資料集。 每個資料來源包含資料連接資訊。 每個資料集都包含查詢命令，定義要作為資料來源資料使用的欄位集。 若要視覺化每個資料集的資料，請新增資料區域 (例如資料表、矩陣、圖表或地圖)。 處理報表時，查詢會在資料來源上執行，且每個資料區會視需要展開，以顯示資料集的查詢結果。  

了解如何[在 Power BI 報表產生器中為分頁報表建立內嵌資料來源](paginated-reports-embedded-data-source.md)。


##  <a name="terms"></a><a name="BkMk_ReportDataTerms"></a> 詞彙  
  
- **資料連線。** 也稱為「資料來源」  。 資料連線包含名稱和相依於連線類型的連線屬性。 根據設計，資料連線不會包含認證。 資料連線不會指定要從外部資料來源擷取何種資料。 若要執行這項操作，您可以在建立資料集時指定查詢。  
  
- **連接字串。** 連接字串是連線到資料來源時所需要連線屬性的字串版本。 連線屬性會因資料連線類型而不同。 

    > [!NOTE]
    > 資料來源連接字串不能以運算式為基礎。
  
- **內嵌資料來源。** 也稱為 *「報表特定資料來源」*(report-specific data source)。 在報表中定義而且僅供該報表使用的資料來源。  
  
- **認證。** 認證是驗證資訊，您必須提供這項資訊才能存取外部資料。  
  
##  <a name="tips-for-specifying-report-data"></a><a name="BkMk_ReportDataTips"></a> 指定報表資料的提示

 使用下列資訊可以設計您的報表資料策略。  
  
- **篩選資料** ：在查詢或在報表中，可以篩選報表資料。 您可以使用資料集及查詢變數以建立串聯參數，並提供使用者從數千個選取中減少選擇項目的能力，以選取便於管理的數字。 您可以根據所指定的參數值或其他值，篩選資料表或圖表中的資料。  
  
- **參數** ：包含查詢變數的資料集查詢命令會自動建立相符的報表參數。 您也可以手動建立參數。 檢視報表時，報表工具列會顯示參數。 使用者可以選取值，以控制報表資料或報告的外觀。 若要為特定對象自訂報表資料，您可以建立一組具有連結到相同報表定義之不同預設值的報表參數，或是使用內建的 **UserID** 欄位。 
  
- **群組及彙總值** ：在查詢或在報表中，可以分組及彙總報表資料。 若您彙總查詢中的數值，可繼續合併有意義條件約束內報表中的數值。  
  
- **排序資料** ：在查詢或在報表中，可以排序報表資料。 在資料表中，您也可以加入互動式排序按鈕，讓使用者可以控制排序次序。  
  
- **以運算式為基礎的資料** ：因為多數的報表屬性可以運算式為基礎，而且運算式可以包含資料集欄位及報表參數的參考，您可以寫入強大的運算式以控制報表資料及外觀。 您可以提供使用者透過定義參數控制所看見資料的能力。  
  
- **顯示資料集中的資料** ：資料集中的資料通常會顯示在一個或多個資料區，例如資料表及圖表。  
  
- **顯示多個資料集之中的資料**  ：您可以在一個以查閱其他資料集中的數值或彙總值為基礎之資料集的資料區中，寫入運算式。 您可以包含以一個資料集為基礎之資料表中的子報表，以顯示來自不同資料來源的資料。  
  
 使用下列清單以協助定義報表資料的來源。  
  
- 了解組織的軟體資料層架構，以及資料類型所造成之可能發生的問題。 了解資料延伸模組及資料處理延伸模組會如何影響查詢結果。 資料類型在資料來源、資料提供者及儲存於報表定義 (.rdl) 檔案的資料類型之間會有所差異。  
  
- 資料來源和資料集都會在報表中撰寫，並發佈到 Power BI 服務。 發佈後，您可以在 Power BI 服務，或是在您的企業閘道中直接設定認證。 

## <a name="next-steps"></a>後續步驟

- [什麼是 Power BI Premium 中的編頁報表？](paginated-reports-report-builder-power-bi.md)  
- [編頁報表的資料擷取指引](../guidance/report-paginated-data-retrieval.md)
