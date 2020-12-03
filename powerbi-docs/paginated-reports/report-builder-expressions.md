---
title: Power BI 報表產生器中的運算式
description: 在整個 Power BI Report Builder 的編頁報表中會廣泛利用運算式來擷取、計算、顯示、分組、排序、篩選、參數化和格式化資料。
author: maggiesMSFT
ms.author: maggies
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 76d3ac86-650c-46fe-8086-8b3edcea3882
ms.openlocfilehash: 24f9348bf23c8e5748121f6967fe7c826984adb9
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96416339"
---
# <a name="expressions-in-power-bi-report-builder"></a>Power BI 報表產生器中的運算式

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

在整個 Power BI Report Builder 的編頁報表中會廣泛利用運算式來擷取、計算、顯示、分組、排序、篩選、參數化和格式化資料。 
  
許多報表項目屬性都可以設定為運算式。 運算式可協助您控制報表的內容、設計與互動性。 運算式都是以 Microsoft Visual Basic 撰寫，儲存在報表定義中，並會在您執行報表時由報表處理器評估。  
  
 報表不像 Microsoft Office Excel 等應用程式，可讓您直接在工作表中使用資料，而是要使用作為資料預留位置的運算式。 若要從評估的運算式查看實際資料，您必須預覽報表。 當您執行報表時，報表處理器會評估每個運算式，因為它會結合資料與報表配置元素，例如資料表和圖表。  
  
 當您設計報表時，系統會為您設定許多報表項目的運算式。 例如，當您將欄位從資料窗格拖曳到報表設計介面上的資料表資料格時，文字方塊值會設定為欄位的簡單運算式。 在下圖中，[報表資料] 窗格會顯示 ID、Name、SalesTerritory、Code 和 Sales 資料集欄位。 有三個欄位已加入資料表中：[Name]、[Code] 和 [Sales]。 設計介面上的標記 [Name] 代表基礎運算式 `=Fields!Name.Value`。  
  
![報表產生器的 [設計] 檢視](media/report-builder-expressions/report-builder-data-design-preview.png)
  
 當您預覽報表時，報表處理器會結合資料表資料區與資料連接中的實際資料，並針對結果集中的每個資料列顯示資料表中的資料列。  
  
 若要手動輸入運算式，請在設計介面上選取項目，然後使用快速鍵功能表和對話方塊來設定此項目的屬性。 當看到 [(fx)] 按鈕或是在下拉式清單中看到 `<Expression>` 值時，表示您可將屬性設為運算式。 
  
##  <a name="understanding-simple-and-complex-expressions"></a><a name="Types"></a> 了解簡單和複雜的運算式  
 運算式會以等號 (=) 開頭，並以 Microsoft Visual Basic 撰寫。 運算式可以包含常數、運算子及內建值 (欄位、集合和函數) 和外部或自訂程式碼參考的組合。  
  
 您可以使用運算式來指定許多報表項目屬性的值。 最常見的屬性為文字方塊與預留位置文字的值。 如果文字方塊只包含一個運算式，該運算式通常就是文字方塊屬性的值。 如果文字方塊包含多個運算式，每個運算式都是文字方塊中的預留位置文字值。  
  
 根據預設，運算式會以「簡單運算式」或「複雜運算式」的形式出現在報表設計介面上。  
  
-   **簡單** ：簡單運算式包含內建集合中單一項目的參考，例如資料集欄位、參數或內建欄位。 在設計介面上，簡單運算式會以方括號的形式出現。 例如， `[FieldName]` 相當於基礎運算式 `=Fields!FieldName.Value`。 當您建立報表配置，並將項目從 [報表資料] 窗格拖曳到設計介面時，系統會為您自動建立簡單運算式。 如需代表不同內建集合之符號的詳細資訊，請參閱 [了解簡單運算式中的字首符號](#DisplayText)。  
  
-   **複雜** ：複雜運算式包含多個內建參考、運算子和函數呼叫的參考。 當運算式值包含多個簡單參考時，複雜運算式會以 <\<Expr>> 的形式出現。 若要檢視運算式，請將滑鼠指標停留在該運算式上，然後使用工具提示。 若要編輯運算式，在 [運算式] 對話方塊中開啟該運算式。  
  
 下圖同時針對文字方塊和預留位置文字顯示一般的簡單運算式和複雜運算式。  
  
![報表產生器運算式預設格式](media/report-builder-expressions/report-builder-expression-default-format.png) 
  
 若要顯示範例值而非運算式的文字，請將格式套用到文字方塊或預留位置文字。 下圖顯示切換為顯示範例值的報表設計介面：  
  
![報表產生器運算式範例格式](media/report-builder-expressions/report-builder-expression-sample-values-format.png)  


## <a name="understanding-prefix-symbols-in-simple-expressions"></a><a name="DisplayText"></a> 了解簡單運算式中的前置符號  

簡單運算式會使用符號來指示參考是指向欄位、參數、內建集合還是報表項目集合。 下表顯示了顯示和運算式文字的範例：  
  
|Item|顯示文字範例|運算式文字範例|  
|----------|--------------------------|-----------------------------|  
|資料集欄位|`[Sales]`<br /><br /> `[SUM(Sales)]`<br /><br /> `[FIRST(Store)]`|`=Fields!Sales.Value`<br /><br /> `=Sum(Fields!Sales.Value)`<br /><br /> `=First(Fields!Store.Value)`|  
|報表參數|`[@Param]`<br /><br /> `[@Param.Label]`|`=Parameters!Param.Value`<br /><br /> `=Parameters!Param.Label`|  
|內建欄位|`[&ReportName]`|`=Globals!ReportName.Value`|  
|用於顯示文字的常值字元|`\[Sales\]`|`[Sales]`|  
  
##  <a name="writing-complex-expressions"></a><a name="References"></a> 撰寫複雜運算式  
 運算式可以包含函數、運算子、常數、欄位、參數、內建集合的項目，以及內嵌自訂程式碼或自訂組件的參考。  
  
 下表列出可以包含在運算式中的參考種類：  
  
|參考|說明|範例|  
|----------------|-----------------|-------------|  
|常數|描述可透過互動方式針對需要常數值的屬性而存取的常數，例如字型色彩。|`="Blue"`|  
|運算子|描述您可以用來結合運算式中參考的運算子。 例如， **&** 運算子用於串連字串。|`="The report ran at: " & Globals!ExecutionTime & "."`|  
|內建集合|描述可以包含在運算式中的內建集合，例如， `Fields`、 `Parameters`和 `Variables`。|`=Fields!Sales.Value`<br /><br /> `=Parameters!Store.Value`<br /><br /> `=Variables!MyCalculation.Value`|  
|內建報表和彙總函式|描述可以從運算式存取的內建函數，例如， `Sum` 或 `Previous`。|`=Previous(Sum(Fields!Sales.Value))`|  
|報表產生器中運算式內的自訂程式碼和組件參考 |描述如何存取內建 CLR 類別 `xref:System.Math` 和 `xref:System.Convert`、其它 CLR 類別、Visual Basic 執行階段程式庫函式，或是來自外部組件的方法。<br /><br /> 描述如何存取內嵌於報表，或在編譯後安裝在報表用戶端和報表伺服器上做為自訂組件的自訂程式碼。|`=Sum(Fields!Sales.Value)`<br /><br /> `=CDate(Fields!SalesDate.Value)`<br /><br /> `=DateAdd("d",3,Fields!BirthDate.Value)`<br /><br /> `=Code.ToUSD(Fields!StandardCost.Value)`|  
   
##  <a name="validating-expressions"></a><a name="Valid"></a> 驗證運算式  
 為特定的報表項目屬性建立運算式時，包含在運算式中的參考取決於報表項目屬性可以接受的值，以及評估屬性的範圍。 例如：  
  
-   根據預設，運算式 [Sum] 會計算評估運算式時範圍內資料的總和。 若是資料表資料格，範圍則視資料列和資料行群組成員資格而定。 
  
-   若是 Font 屬性的值，此值必須評估為字型的名稱。  
  
-   運算式語法是在設計階段進行驗證。 當您發行報表時，便會驗證運算式範圍。 若是與實際資料相關的驗證，則只能在執行階段偵測錯誤。 其中部分運算式在轉譯的報表中會產生 #Error 做為錯誤訊息。 

## <a name="next-steps"></a>後續步驟

- [什麼是 Power BI Premium 中的編頁報表？](paginated-reports-report-builder-power-bi.md)
