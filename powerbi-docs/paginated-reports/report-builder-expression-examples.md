---
title: Power BI 報表產生器中的運算式範例
description: 在 Power BI Report Builder 的編頁報表中，經常使用運算式來控制內容和報表外觀。
ms.date: 11/08/2020
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: 87ddb651-a1d0-4a42-8ea9-04dea3f6afa4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 762949dcce178628d387cd8f88c60080f74c5bae
ms.sourcegitcommit: 37bd34053557089c4fbf0e05f78e959609966561
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2020
ms.locfileid: "94397338"
---
# <a name="expression-examples-in-power-bi-report-builder"></a>Power BI 報表產生器中的運算式範例

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

在 Power BI Report Builder 的編頁報表中，經常使用運算式來控制內容和報表外觀。 運算式都是以 Microsoft Visual Basic 撰寫，並可使用內建函式、自訂程式碼、報表和群組變數，以及使用者定義的變數。 運算式以等號 (=) 當做開頭。   

本主題提供可用於報表中一般工作的運算式範例。  
  
-   日期、字串、轉換和條件式 Visual Basic 函式的 [Visual Basic 函式](#VisualBasicFunctions)範例。  
  
-   [報表函數](#ReportFunctions) ：彙總和其他內建報表函數的範例。  
  
-   [報表資料的外觀](#AppearanceofReportData) ：變更報表外觀的範例。  
  
-   [屬性](#Properties) ：設定報表項目屬性來控制格式或可見性的範例。  
  
-   [參數](#Parameters) ：在運算式中使用參數的範例。  
  
-   [自訂程式碼](#CustomCode) ：內嵌自訂程式碼的範例。  
  
如需簡單和複雜運算式、運算式可用位置以及運算式中可包含參考型別的詳細資訊，請參閱 [Power BI 報表產生器中的運算式](report-builder-expressions.md)底下的主題。 
  
## <a name="functions"></a>函式  
 報表中的許多運算式都有包含函數， 您可以使用這些函數來格式化資料、套用邏輯以及存取報表中繼資料。 您可以撰寫運算式，使用來自 Microsoft Visual Basic 執行階段程式庫，以及來自 `xref:System.Convert` 和 `xref:System.Math` 命名空間的運算式。 您可以在自訂程式碼中新增函式的參考。 您也可以使用 Microsoft .NET Framework 中的類別，包括 `xref:System.Text.RegularExpressions`。  
  
##  <a name="visual-basic-functions"></a><a name="VisualBasicFunctions"></a> Visual Basic 函式  
 您可以使用 Visual Basic 函式來操作顯示在文字方塊中的資料，或是用於參數、屬性或其他報表區域的資料。 此章節提供示範其中一些函數的範例。 如需詳細資訊，請參閱 MSDN 上的 [Visual Basic 執行階段程式庫成員](/dotnet/visual-basic/language-reference/runtime-library-members) 。  
  
 .NET Framework 提供許多自訂格式選項，例如特定日期格式。 如需詳細資訊，請參閱[格式類型](/dotnet/standard/base-types/formatting-types)。  
  
### <a name="math-functions"></a>數學函數  
  
-   **Round** 函數可用來將數字四捨五入至最接近的整數。 下列運算式會將 1.3 四捨五入成 1。  
  
    ```  
    = Round(1.3)  
    ```  
  
     您也可以撰寫運算式來將值四捨五入至您所指定的倍數，類似於 Excel 中的 **MRound** 函數。 您可將值乘以一個可產生整數的因數，將數字四捨五入，然後再除以同一個因數。 例如，若要將 1.3 四捨五入到最接近的 .2 的倍數 (1.4)，請使用下列運算式：  
  
    ```  
    = Round(1.3*5)/5  
    ```  
  
###  <a name="date-functions"></a><a name="DateFunctions"></a> 日期函式  
  
-   **Today** 函數會提供目前的日期。 此運算式可用於文字方塊，以顯示報表中的日期，或根據目前的日期在參數中篩選資料。  
  
    ```  
    =Today()  
    ```  
  
-   使用 **DateInterval** 函式，拉出日期的特定部分。 以下是一些有效的 **DateInterval** 參數：

    -   DateInterval.Second
    -   DateInterval.Minute
    -   DateInterval.Hour
    -   DateInterval.Weekday
    -   DateInterval.Day
    -   DateInterval.DayOfYear
    -   DateInterval.WeekOfYear
    -   DateInterval.Month
    -   DateInterval.Quarter
    -   DateInterval.Year

    例如，此運算式會顯示今天日期之目前年份的週數：
  
    ```  
    =DatePart(DateInterval.WeekOfYear, today()) 
    ```  
  
-   **DateAdd** 函數在根據單一參數提供一個範圍的日期時很有用。 下列運算式提供在名為 *StartDate* 參數的日期六個月之後的日期。  
  
    ```  
    =DateAdd(DateInterval.Month, 6, Parameters!StartDate.Value)  
    ```  
  
-   **Year** 函數會顯示特定日期的年份。 您可以使用這個來將日期群組在一起，或是將年顯示為一組日期的標籤。 這個運算式會提供給定訂購日期群組的年份。 **Month** 函數和其他函數也可用來操作日期。 如需詳細資訊，請參閱 Visual Basic 文件。  
  
    ```  
    =Year(Fields!OrderDate.Value)  
    ```  
  
-   您可以在運算式中結合函數來自訂格式。 下列運算式會將日期的格式從「月-日-年」改成「月-週-週數」， 例如從 12/23/2009 改成 December Week 3：  
  
    ```  
    =Format(Fields!MyDate.Value, "MMMM") & " Week " &   
    (Int(DateDiff("d", DateSerial(Year(Fields!MyDate.Value),   
    Month(Fields!MyDate.Value),1), Fields!FullDateAlternateKey.Value)/7)+1).ToString  
    ```  
  
     當做為資料集中的導出欄位使用時，您可以在圖表中使用這個運算式，在每個月內逐週彙總值。  
  
-   下列運算式會將 SellStartDate 值格式化為 MMM-YY。 SellStartDate 欄位是 datetime 資料類型。  
  
    ```  
    =FORMAT(Fields!SellStartDate.Value, "MMM-yy")  
    ```  
  
-   下列運算式會將 SellStartDate 值格式化為 dd/MM/yyyy。 SellStartDate 欄位是 datetime 資料類型。  
  
    ```  
    =FORMAT(Fields!SellStartDate.Value, "dd/MM/yyyy")  
    ```  
  
-   **CDate** 函數會將值轉換成日期。 **Now** 函數會根據您的系統傳回包含目前日期和時間的日期值。 **DateDiff** 會傳回長數值，指定兩個日期值之間的時間間隔數。  
  
     下列範例顯示目前年度的開始日期  
  
    ```  
    =DateAdd(DateInterval.Year,DateDiff(DateInterval.Year,CDate("01/01/1900"),Now()),CDate("01/01/1900"))  
    ```  
  
-   下列範例會根據目前月份顯示上個月的開始日期。  
  
    ```  
    =DateAdd(DateInterval.Month,DateDiff(DateInterval.Month,CDate("01/01/1900"),Now())-1,CDate("01/01/1900"))  
    ```  
  
-   下列運算式會產生 SellStartDate 與 LastReceiptDate 之間的間隔年數。 這些欄位位於兩個不同的資料集：DataSet1 和 DataSet2 中。  
  
    ```  
    =DATEDIFF("yyyy", First(Fields!SellStartDate.Value, "DataSet1"), First(Fields!LastReceiptDate.Value, "DataSet2"))  
    ```  
  
-   **DatePart** 函數會傳回包含給定 Date 值之指定元件的整數值。下列運算式則會傳回 DataSet1 中 SellStartDate 第一個值的年份。 已指定資料集範圍，因為報表中有多個資料集。  
  
    ```  
    =Datepart("yyyy", First(Fields!SellStartDate.Value, "DataSet1"))  
  
    ```  
  
-   **DateSerial** 函數會傳回代表指定年、月、日，並將時間資訊設為午夜的 Date 值。 下列範例會根據目前月份顯示上個月的結束日期。  
  
    ```  
    =DateSerial(Year(Now()), Month(Now()), "1").AddDays(-1)  
    ```  
  
-   下列運算式會根據使用者選取的日期參數值，顯示各種日期。  
  
|範例描述|範例|  
|-------------------------|-------------|  
|昨天|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-1)`|  
|兩天前|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value)-2)`|  
|一個月前|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-1,Day(Parameters!TodaysDate.Value))`|  
|兩個月前|`=DateSerial(Year(Parameters!TodaysDate.Value),Month(Parameters!TodaysDate.Value)-2,Day(Parameters!TodaysDate.Value))`|  
|一年前|`=DateSerial(Year(Parameters!TodaysDate.Value)-1,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
|兩年前|`=DateSerial(Year(Parameters!TodaysDate.Value)-2,Month(Parameters!TodaysDate.Value),Day(Parameters!TodaysDate.Value))`|  
  
###  <a name="string-functions"></a><a name="StringFunctions"></a> 字串函式  
  
-   使用串連運算子和 Visual Basic 常數來合併多個欄位。 下列運算式會傳回兩個欄位，分別位於相同文字方塊中的不同行：  
  
    ```  
    =Fields!FirstName.Value & vbCrLf & Fields!LastName.Value   
    ```  
  
-   您可以使用 **Format** 函數，將字串中的日期與數字格式化。 下列運算式會以完整日期格式來顯示 *StartDate* 和 *EndDate* 參數的值：  
  
    ```  
    =Format(Parameters!StartDate.Value, "D") & " through " &  Format(Parameters!EndDate.Value, "D")    
    ```  
  
     如果文字方塊只包含日期或數字，您應該使用文字方塊的 Format 屬性來套用格式，而非使用文字方塊中的 **Format** 函數。  
  
-   **Right**、**Len** 和 **InStr** 函式在傳回子字串時很有用；例如，將 *DOMAIN*\\*使用者名稱* 修改成只有使用者名稱。 下列運算式會從名為\\User *的參數傳回字串中反斜線 (* ) 字元右邊的字串部分：  
  
    ```  
    =Right(Parameters!User.Value, Len(Parameters!User.Value) - InStr(Parameters!User.Value, "\"))  
    ```  
  
     下列運算式會產生與上一個運算式相同的值，但使用 .NET Framework `xref:System.String` 類別的成員，而不是 Visual Basic 函式：  
  
    ```  
    =Parameters!User.Value.Substring(Parameters!User.Value.IndexOf("\")+1, Parameters!User.Value.Length-Parameters!User.Value.IndexOf("\")-1)  
    ```  
  
-   顯示多重數值參數中所選的值。 下列範例會使用 **Join** 函數，將選定的 *MySelection* 參數值串連成單一字串，此字串可以設為報表項目中文字方塊值的運算式：  
  
    ```  
    = Join(Parameters!MySelection.Value)  
    ```  
  
     下列範例的作用與上述範例相同，也會在選取值清單前面顯示文字字串。  
  
    ```  
    ="Report for " & JOIN(Parameters!MySelection.Value, " & ")  
  
    ```  
  
-   來自 .NET Framework `xref:System.Text.RegularExpressions` 的 **Regex** 函式可用於變更現有字串的格式，例如設定電話號碼格式。 下列運算式使用 **Replace** 函數，將欄位中十位數電話號碼的格式從 "*nnn*-*nnn*-*nnnn*" 變更為 "(*nnn*) *nnn*-*nnnn*"：  
  
    ```  
    =System.Text.RegularExpressions.Regex.Replace(Fields!Phone.Value, "(\d{3})[ -.]*(\d{3})[ -.]*(\d{4})", "($1) $2-$3")  
    ```  
  
    > [!NOTE]  
    >  確認 Fields!Phone.Value 的值沒有額外的空格，而且為 `xref:System.String`。  
  
### <a name="lookup"></a>查閱  
  
-   您可以藉由指定索引鍵欄位，使用 **Lookup** 函數來從一對一關係的資料集 (如索引鍵-值組) 中擷取值。 下列運算式會顯示提供要比對的產品識別碼時，資料集 ("Product") 中的產品名稱：  
  
    ```  
    =Lookup(Fields!PID.Value, Fields!ProductID.Value, Fields.ProductName.Value, "Product")  
    ```  
  
### <a name="lookupset"></a>LookupSet  
  
-   您可以藉由指定索引鍵欄位，使用 **LookupSet** 函數來從一對多關係的資料集中擷取一組值。 例如，人員可以擁有多個電話號碼。 在下列範例中，假設 PhoneList 資料集在每一個資料列中包含人員識別碼和電話號碼。 **LookupSet** 會傳回值的陣列。 下列運算式會將傳回值結合成單一字串，並顯示 ContactID 指定之人員的電話號碼清單：  
  
    ```  
    =Join(LookupSet(Fields!ContactID.Value, Fields!PersonID.Value, Fields!PhoneNumber.Value, "PhoneList"),",")  
    ```  
  
###  <a name="conversion-functions"></a><a name="ConversionFunctions"></a> 轉換函式  
 您可以使用 Visual Basic 函式，將欄位從一種資料類型轉換成另一種資料類型。 轉換函數可用來將欄位的預設資料類型轉換為計算或結合文字時所需的資料類型。  
  
-   下列運算式會將常數 500 轉換成十進位類型，以便與 Value 欄位中的 Transact-SQL 貨幣資料類型進行比較來篩選運算式。  
  
    ```  
    =CDec(500)  
    ```  
  
-   下列運算式會顯示針對多重數值參數 *MySelection* 所選的值數目。  
  
    ```  
    =CStr(Parameters!MySelection.Count)  
    ```  
  
###  <a name="decision-functions"></a><a name="DecisionFunctions"></a> 決策函式  
  
-   **lif** 函數會根據運算式是否評估為 true 而傳回兩個值之一。 當 **超過 100 時，下列運算式會使用** lif **函數來傳回布林值** True `LineTotal` ， 否則它會傳回 **False**：  
  
    ```  
    =IIF(Fields!LineTotal.Value > 100, True, False)  
    ```  
  
-   使用多個 **IIF** 函數 (也稱為「巢狀 IIF」) 可以根據 `PctComplete`值傳回三個值之一。 您可以將下列運算式置入文字方塊的填滿色彩，依照文字方塊中的值而變更背景色彩。  
  
    ```  
    =IIF(Fields!PctComplete.Value >= 10, "Green", IIF(Fields!PctComplete.Value >= 1, "Blue", "Red"))  
    ```  
  
     大於或等於 10 的值會以綠色背景顯示、介於 1 和 9 之間的值以藍色背景顯示，小於 1 的值則以紅色背景顯示。  
  
-   另一種取得相同功能的方法，是使用 **Switch** 函數。 當測試的條件有三個或三個以上時， **Switch** 函數就很有用。 **Switch** 函數會傳回與數列中評估為 true 的第一個運算式相關聯的值：  
  
    ```  
    =Switch(Fields!PctComplete.Value >= 10, "Green", Fields!PctComplete.Value >= 1, "Blue", Fields!PctComplete.Value = 1, "Yellow", Fields!PctComplete.Value <= 0, "Red")  
    ```  
  
     大於或等於 10 的值會以綠色背景顯示、介於 1 和 9 之間的值以藍色背景顯示、等於 1 的值以黃色背景顯示，0 或小於 0 的值則以紅色背景顯示。  
  
-   測試 `ImportantDate` 欄位的值，如果超過一週，則傳回 "Red"，否則傳回 "Blue"。 這個運算式可用來控制報表項目中文字方塊的色彩屬性：  
  
    ```  
    =IIF(DateDiff("d",Fields!ImportantDate.Value, Now())>7,"Red","Blue")  
    ```  
  
-   測試 `PhoneNumber` 欄位的值，如果為 **Null** (在 Visual Basic 中為 **Nothing**)，則傳回 "No Value"，否則傳回電話號碼值。 這個運算式可用來控制報表項目中文字方塊的值。  
  
    ```  
    =IIF(Fields!PhoneNumber.Value Is Nothing,"No Value",Fields!PhoneNumber.Value)  
    ```  
  
-   測試 `Department` 欄位的值，並傳回子報表名稱或 **Null** (在 Visual Basic 中為 **Nothing**)。 此運算式可用於條件式鑽研子報表。  
  
    ```  
    =IIF(Fields!Department.Value = "Development", "EmployeeReport", Nothing)  
    ```  
  
-   測試欄位值是否為 Null。 此運算式可用來控制影像報表項目的 **Hidden** 屬性。 在下列範例中，只有當欄位 [LargePhoto] 的值不是 Null 時，才會顯示該欄位所指定的影像。  
  
    ```  
    =IIF(IsNothing(Fields!LargePhoto.Value),True,False)  
    ```  
  
-   **MonthName** 函數會傳回字串值，包含指定之月份的名稱。 下列範例會在欄位包含 0 的值時，於月份欄位中顯示 NA。  
  
    ```  
    IIF(Fields!Month.Value=0,"NA",MonthName(IIF(Fields!Month.Value=0,1,Fields!Month.Value)))  
  
    ```  
  
##  <a name="report-functions"></a><a name="ReportFunctions"></a> 報表函式  
 在運算式中，您可以加入在報表中操作資料之其他報表函數的參考。 此章節提供這些函數的其中兩個範例。 
  
###  <a name="sum"></a><a name="Sum"></a> Sum  
  
-   **Sum** 函數可以將群組或資料區域中的值加總。 群組的頁首或頁尾可以使用這個函數。 下列運算式會顯示 Order 群組或資料區域中資料的總和：  
  
    ```  
    =Sum(Fields!LineTotal.Value, "Order")  
    ```  
  
-   您也可以使用 **Sum** 函數進行條件式彙總計算。 例如，如果資料集有稱為 State 的欄位，而該欄位具有 Not Started、Started、Finished 等可能值，則下列運算式在置入群組頁首時，只會計算 Finished 值的彙總總和：  
  
    ```  
    =Sum(IIF(Fields!State.Value = "Finished", 1, 0))  
    ```  
  
###  <a name="rownumber"></a><a name="RowNumber"></a> RowNumber  
  
-   **RowNumber** 函數在用於資料區域內的文字方塊時，會為其中顯示此運算式的每個文字方塊執行個體顯示資料列號碼。 此函數對於計算資料表中的資料列數目非常有用。 它對於更複雜的工作也非常實用，例如，根據資料列數目提供分頁符號。 如需詳細資訊，請參閱這個主題中的 [分頁符號](#PageBreaks) 。  
  
     您所指定的 **RowNumber** 範圍會控制何時開始重新編號。 **Nothing** 關鍵字指出函數將從最外層資料區域中的第一個資料列開始計數。 若要在巢狀資料區域內開始計數，請使用資料區域的名稱。 若要在群組內開始計數，請使用群組的名稱。  
  
    ```  
    =RowNumber(Nothing)  
    ```  
  
##  <a name="appearance-of-report-data"></a><a name="AppearanceofReportData"></a> 報表資料的外觀  
 您可以使用運算式來操作報表中資料顯示的方式。 例如，可以在單一文字方塊中顯示兩個欄位的值、顯示有關報表的資訊，或影響報表中插入分頁符號的方式。  
  
###  <a name="page-headers-and-footers"></a><a name="PageHeadersandFooters"></a> 頁首和頁尾  
 設計報表時，您需要顯示報表的名稱以及報表尾的頁碼。 若要這麼做，您可以使用下列運算式：  
  
-   下列運算式提供報表的名稱和執行報表的時間。 它可以放置在報表尾的文字方塊中或是報表的主體中。 時間格式採用 .NET Framework 的簡短日期格式字串：  
  
    ```  
    =Globals.ReportName & ", dated " & Format(Globals.ExecutionTime, "d")  
    ```  
  
-   下列放在報表尾文字方塊中的運算式，提供報表的頁碼與總頁數。  
  
    ```  
    =Globals.PageNumber & " of " & Globals.TotalPages  
    ```  
  
 下列範例描述如何顯示一頁中頁首的第一個和最後一個值，與目錄清單中所找到的類似。 這個範例假設包含名稱為 `LastName`之文字方塊的資料區域。  
  
-   下列運算式放在頁首左側文字方塊中，用來提供頁面 `LastName` 文字方塊的第一個值：  
  
    ```  
    =First(ReportItems("LastName").Value)  
    ```  
  
-   下列運算式放在頁首右邊的文字方塊中時，會提供此頁上 `LastName` 文字方塊的最後一個值：  
  
    ```  
    =Last(ReportItems("LastName").Value)  
    ```  
  
 下列範例描述如何顯示總頁數。 這個範例假設包含名稱為 `Cost`之文字方塊的資料區域。  
  
-   下列運算式放在頁首或頁尾中，用來提供頁面 `Cost` 文字方塊中各個值的總和：  
  
    ```  
    =Sum(ReportItems("Cost").Value)  
    ```  
  
> [!NOTE]  
>  在頁首或頁尾中，每個運算式只能參考一個報表項目。 此外，您也可以在頁首或頁尾的運算式中參考文字方塊名稱，但不能參考文字方塊內實際的資料運算式。  
  
###  <a name="page-breaks"></a><a name="PageBreaks"></a> 分頁符號  
 在某些報表中，除了在群組或報表項目上放置分頁符號以外，您也可能會需要在指定資料列數目的結尾處放置分頁符號。 若要執行這個動作，請建立包含所要群組或細節記錄的群組，將分頁符號加入群組中，再依指定的資料列數，將群組運算式加入群組中。  
  
-   下列運算式放在群組運算式中，每 25 個資料列即指派一個數字。 為群組定義分頁符號時，這個運算式每隔 25 個資料列就會產生一個分頁符號。  
  
    ```  
    =Ceiling(RowNumber(Nothing)/25)  
    ```  
  
     若要讓使用者設定每頁資料列數的值，請建立名為 `RowsPerPage` 的參數，然後以該參數做為群組運算式的基礎，如下列運算式所示：  
  
    ```  
    =Ceiling(RowNumber(Nothing)/Parameters!RowsPerPage.Value)  
    ```  
  
##  <a name="properties"></a><a name="Properties"></a> 屬性  
 運算式不只用來顯示文字方塊中的資料。 運算式也可以用來變更將屬性套用至報表項目的方式。 您可以變更報表項目的樣式資訊，或是變更其可見性。  
  
###  <a name="formatting"></a><a name="Formatting"></a> 格式化  
  
-   當用在文字方塊的 Color 屬性時，下列運算式會依 `Profit` 欄位值而變更文字的色彩：  
  
    ```  
    =Iif(Fields!Profit.Value < 0, "Red", "Black")  
    ```  
  
     您也可以使用 Visual Basic 物件變數 `Me`。 這個變數是另一種參考文字方塊值的方式。  
  
     `=Iif(Me.Value < 0, "Red", "Black")`  
  
-   當用在資料區域中之報表項目的 BackgroundColor 屬性中，下列運算式會替代淡綠色和白色之間每個資料列的背景色彩：  
  
    ```  
    =Iif(RowNumber(Nothing) Mod 2, "PaleGreen", "White")  
    ```  
  
     如果您使用指定之範圍的運算式，可能必須指出彙總函式的資料集：  
  
    ```  
    =Iif(RowNumber("Employees") Mod 2, "PaleGreen", "White")  
    ```  
  
> [!NOTE]  
>  可用的色彩是來自 .NET Framework KnownColor 列舉。  
  
### <a name="chart-colors"></a>圖表色彩  
 若要指定形狀圖的色彩，您可以使用自訂程式碼控制色彩對應到資料點值的順序。 這有助於針對擁有相同類別目錄群組的多個圖表，使用一致的色彩。 
  
###  <a name="visibility"></a><a name="Visibility"></a> 可見性  
 您可以使用報表項目的可見性屬性，來顯示和隱藏報表中的項目。 在如資料表的資料區域中，您可以根據運算式中的值一開始便隱藏詳細資料列。  
  
-   當用於群組詳細資料列的初始可見性時，下列運算式會顯示 `PctQuota` 欄位超出 90% 之所有銷售的詳細資料列：  
  
    ```  
    =Iif(Fields!PctQuota.Value>.9, False, True)  
    ```  
  
-   下列運算式設定在資料表的 Hidden 屬性中時，只有當資料表有 12 個以上的資料列時，才會顯示該資料表：  
  
    ```  
    =IIF(CountRows()>12,false,true)  
    ```  
  
-   下列運算式設定在資料行的 **Hidden** 屬性中時，只有在從資料來源擷取資料之後報表資料集中有該欄位，才會顯示該資料行：  
  
    ```  
    =IIF(Fields!Column_1.IsMissing, true, false)  
    ```  
  
###  <a name="urls"></a><a name="Hyperlinks"></a> URL  
 您可以使用報表資料來自訂 URL，也可以條件式地控制是否要加入 URL 做為文字方塊的動作。  
  
-   當下列運算式做為文字方塊的動作時，會產生自訂的 URL，將 `EmployeeID` 資料集欄位指定為 URL 參數。  
  
    ```  
    ="https://adventure-works/MyInfo?ID=" & Fields!EmployeeID.Value  
    ```  
  
-   下列運算式會條件式地控制是否要在文字方塊中加入 URL。 這個運算式會根據名為 `IncludeURLs` 的參數，讓使用者決定是否要在報表中包含作用中的 URL。 這個運算式會設定為文字方塊的動作。 透過將參數設定為 False，然後再檢視報表，您可以將報表匯出為沒有超連結的 Microsoft Excel 格式。  
  
    ```  
    =IIF(Parameters!IncludeURLs.Value,"https://adventure-works.com/productcatalog",Nothing)  
    ```  
  
> [!NOTE]
>  Power BI 編頁報表不支援在 **Go To URL** 運算式中使用 JavaScript。  
  
##  <a name="report-data"></a><a name="ReportData"></a> 報表資料  
 您可以使用運算式來操作用於報表中的資料。 您可以參考參數和其他的報表資訊。 您甚至可以變更用來擷取報表資料的查詢。  
  
###  <a name="parameters"></a><a name="Parameters"></a> 參數  
 您可以在參數中使用運算式，以更改參數的預設值。 例如，您可以利用參數，根據用來執行報表的使用者識別碼來篩選特定使用者的資料。  
  
-   使用下列運算式做為參數的預設值時，收集執行報表之人員的使用者識別碼：  
  
    ```  
    =User!UserID  
    ```  
  
-   若要在報表的查詢參數、篩選運算式、文字方塊或其他區域中參考參數，請使用 **Parameters** 全域集合。 這個範例假設參數的名稱是 *Department*：  
  
    ```  
    =Parameters!Department.Value  
    ```  
  
-   您可以在報表中建立參數，但將其設為隱藏。 當報表在報表伺服器上執行時，參數不會出現在工具列中，且報表讀者無法變更預設值。 您可以使用設為預設值的隱藏參數做為自訂常數。 您可以在任何運算式中使用此值，欄位運算式也在內。 下列運算式會識別由名為 *ParameterField* 之參數的預設參數值所指定的欄位：  
  
    ```  
    =Fields(Parameters!ParameterField.Value).Value  
    ```  
  
##  <a name="custom-code"></a><a name="CustomCode"></a> 自訂程式碼  
 您可以使用內嵌在報表中的自訂程式碼。 
  
### <a name="using-group-variables-for-custom-aggregation"></a>使用群組變數進行自訂彙總  
 您可以初始化特定群組範圍本機之群組變數的值，然後在運算式中加入該變數的參考。 搭配自訂程式碼使用群組變數的其中一種方式是實作自訂彙總。 
  
## <a name="suppressing-null-or-zero-values-at-run-time"></a>在執行階段隱藏 Null 或零值  
 運算式中有些值可能會在報表處理時評估為 Null 或未定義。 這樣可能會造成執行階段錯誤，導致文字方塊中顯示 **#Error** ，而不是評估的運算式。 **IIF** 函數對於這種行為特別敏感，因為不像 If-Then-Else 陳述式， **IIF** 陳述式的每部分都會先進行評估 (包括函數呼叫)，才會傳遞至測試 **true** 或 **false** 的常式。 如果 `=IIF(Fields!Sales.Value is NOTHING, 0, Fields!Sales.Value)` 為 NOTHING， **陳述式會在轉譯的報表中產生** #Error `Fields!Sales.Value` 。  
  
 若要避免此種狀況，請使用下列其中一種策略：  
  
-   如果欄位 B 的值為 0 或未定義，則將分子設為 0，分母設為 1；否則將分子設為欄位 A 的值，分母設為欄位 B 的值。  
  
    ```  
    =IIF(Field!B.Value=0, 0, Field!A.Value / IIF(Field!B.Value =0, 1, Field!B.Value))  
    ```  
  
-   使用自訂程式碼函數來傳回運算式的值。 下列範例會傳回目前值和上一個值之間的百分比差異。 這可用來計算任兩個連續值之間的差異，並處理第一個比較的邊緣案例 (沒有上一個值時)，以及上一個值或目前值是否為 **Null** (在 Visual Basic 中為 **Nothing**) 的案例。  
  
    ```  
    Public Function GetDeltaPercentage(ByVal PreviousValue, ByVal CurrentValue) As Object  
        If IsNothing(PreviousValue) OR IsNothing(CurrentValue) Then  
            Return Nothing  
        Else if PreviousValue = 0 OR CurrentValue = 0 Then  
            Return Nothing  
        Else   
            Return (CurrentValue - PreviousValue) / CurrentValue  
        End If  
    End Function  
    ```  
  
     下列運算式顯示如何針對 "ColumnGroupByYear" 容器 (群組或資料區域)，從文字方塊呼叫此自訂程式碼。  
  
    ```  
    =Code.GetDeltaPercentage(Previous(Sum(Fields!Sales.Value),"ColumnGroupByYear"), Sum(Fields!Sales.Value))  
    ```  
  
     這有助於避免執行階段例外狀況。 您現在可以在文字方塊的 `=IIF(Me.Value < 0, "red", "black")` Color **屬性中使用類似** 的運算式，以便根據值大於或小於 0，有條件地顯示文字。  
  
## <a name="next-steps"></a>後續步驟

- [什麼是 Power BI Premium 中的編頁報表？](paginated-reports-report-builder-power-bi.md)
