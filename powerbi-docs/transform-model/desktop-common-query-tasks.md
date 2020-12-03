---
title: 在 Power BI Desktop 中執行常見查詢工作
description: 在 Power BI Desktop 中執行常見查詢工作
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-transform-model
ms.topic: how-to
ms.date: 01/09/2020
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 2346118350ca589a25635db9da976fa917e3ff7b
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415948"
---
# <a name="perform-common-query-tasks-in-power-bi-desktop"></a>在 Power BI Desktop 中執行常見查詢工作

在 Power BI Desktop 的 Power Query 編輯器視窗中，有很多常用的工作。 此文章將示範這些常見工作，並提供其他資訊的連結。

這裡示範的常見查詢工作為：

* 連線至資料
* 資料成形及合併
* 將資料列分組
* 樞紐資料行
* 建立自訂資料行
* 查詢公式

我們將使用幾個資料連線來完成這些工作。 如果您想要自行逐步執行這些工作，可以下載或連接至資料。

第一個資料連線是 [Excel 活頁簿](https://download.microsoft.com/download/5/7/0/5701F78F-C3C2-450C-BCCE-AAB60C31051D/PBI_Edu_ELSi_Enrollment_v2.xlsx)，可下載並儲存在本機。 另一個則是其他 Power BI Desktop 文章中也會使用的 Web 資源：

<https://www.bankrate.com/retirement/best-and-worst-states-for-retirement/>

一般查詢工作會從連接到這兩個資料來源所需的步驟開始。

## <a name="connect-to-data"></a>連線至資料

若要連線到 Power BI Desktop 中的資料，請選取 [首頁]  ，然後選取 [取得資料]  。 Power BI Desktop 會呈現一個功能表，其中具有最常見的資料來源。 如需 Power BI Desktop 可連接的資料來源完整清單，請選取功能表尾端的 [其他]  。 如需詳細資訊，請參閱 [Power BI Desktop 中的資料來源](../connect-data/desktop-data-sources.md).

![[最常見] 資料來源功能表，[取得資料] 按鈕，Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_getdata.png)

若要開始，請選取 [Excel]  ，指定先前所述的 Excel 活頁簿，然後選取 [開啟]  。 查詢會檢查活頁簿，然後在您選擇資料表之後，於 [導覽器]  對話方塊中呈現所找到的資料。

![Excel 資料來源，[導覽器] 對話方塊，[取得資料]，Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_navigator.png)

您可以選取 [轉換資料]  來編輯、調整或「塑造」  資料，然後再載入到 Power BI Desktop。 當您使用要在載入之前先行削減的大型資料集時，編輯功能會特別有用。

連線到不同類型的資料也一樣簡單。 您也會想要連線到 Web 資源。 選擇 [取得資料]   > [其他]  ，然後選取 [其他]   > [Web]   > [連線]  。

![Web 資料來源，[取得資料] 對話方塊，Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_getdata_other.png)

[從 Web]  對話方塊隨即出現，您可以在這裡輸入網頁的 URL。

![[從 Web] 對話方塊，[Web] 資料來源，[取得資料]，Power BI Desktop](media/desktop-common-query-tasks/datasources_fromwebbox.png)

選取 [確定]  。 就像之前一樣，Power BI Desktop 會檢查網頁資料，並在 [導覽器]  對話方塊中顯示預覽選項。 當您選取資料表時，它會顯示資料的預覽。

其他資料連線也很類似。 如果需要驗證才能建立資料連線，Power BI Desktop 會提示您輸入適當的認證。

如需連接至 Power BI Desktop 資料的逐步示範，請參閱[連接至 Power BI Desktop 中的資料](../connect-data/desktop-connect-to-data.md).

## <a name="shape-and-combine-data"></a>資料成形及合併

您可以輕鬆地使用 Power Query 編輯器使資料成形及合併。 本節包含一些範例，說明如何塑造資料。 如需塑造與合併資料的更完整示範，請參閱[使用 Power BI Desktop 塑造及合併資料](../connect-data/desktop-shape-and-combine-data.md)。

在上一節中，您連線到兩組資料：Excel 活頁簿和 Web 資源。 在 Power Query 編輯器中載入資料之後，請從 [查詢]  窗格中的可用查詢中選取網頁查詢，如下所示：

![[查詢] 窗格，Power Query 編輯器，Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_querypaneloaded.png)

塑造資料時，您會將資料來源轉換成符合您需求的格式。

在 Power Query 編輯器中，許多命令位於功能區和內容功能表中。 例如，當您以滑鼠右鍵按一下資料行時，會顯示可將資料行移除的內容功能表。 您也可以選取某個資料行，然後從功能區的 [首頁]  索引標籤中選取 [移除資料行]  按鈕。

![[移除資料行] 命令，Power Query 編輯器，Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_removecolumns.png)

您可以在此查詢中，使用許多其他方式來塑造資料。 您可以從頂端或底部移除任何數目的資料列。 或者，可以新增或分割資料行、取代值，以及執行其他資料塑造工作。 有了這些功能，您就可以指導 Power Query 編輯器取得想要的資料。

## <a name="group-rows"></a>將資料列分組

在 Power Query 編輯器中，您可以將許多資料列的值分組成單一值。 此功能適用於彙總提供的產品數、總銷售額或學生人數。

在此範例中，您會將教育註冊資料集中的資料列分組。 資料來自 Excel 活頁簿， 而且已在 Power Query 編輯器中塑造，以便只取得您需要的資料行、將資料表重新命名，並執行一些其他轉換。

讓我們找出每一州有多少機構。 (機構可包括學區和其他教育機構，例如地區服務區等等。)選取 [機構識別碼 - 已指派 NCES \[區域\] 的最新可用年份]  資料行，然後選取功能區中 [轉換]  或 [首頁]  索引標籤中的 [分組方式]  按鈕。 (兩個索引標籤都提供 [分組方式]  選項。)

![螢幕擷取畫面顯示如何將資料表中的資料列分組。](media/desktop-common-query-tasks/commonquerytasks_groupby.png)

[分組方式]  對話方塊隨即出現。 當 Power Query 編輯器將資料列分組時，它會建立新的資料行，其中放入 **分組** 結果。 您可以以下列方式調整 **分組** 作業：

1. 未標記的下拉式清單會指定要分組的資料行。 Power Query 編輯器會將此值預設為選取的資料行，但您可以將它變更為資料表中的任何資料行。
2. **新增資料行名稱**：Power Query 編輯器會建議新資料行的名稱，這是根據它會套用至要分組之資料行的作業。 不過，您可以隨意命名新的資料行。
3. **作業**：您可以選擇該 Power Query 編輯器所套用的作業，例如 [總和]  、[中間值]  或 [計數相異資料列]  。 預設值為 [計數資料列]  。
4. [加入群組]  和 [加入彙總]  ：只有在您選取 [進階]  選項時，才可以使用這些按鈕。 您可以在單一作業中，對許多資料行進行群組作業 ([分組方式]  動作)，並使用這些按鈕建立幾個彙總。 Power Query 編輯器會根據您在此對話方塊中選取的項目，建立一個在多個資料行上運作的新資料行。

選取 [加入群組]  或 [加入彙總]  ，即可將多個群組或彙總加入至 **分組** 作業。 若要移除群組或匯總，請選取資料列右邊的省略號圖示 ( **...** )，然後選取 [刪除]  。 請繼續並使用預設值來嘗試 **分組方式** 作業，看看會發生什麼情況。

![螢幕擷取畫面顯示 [群組依據] 對話方塊，其中已標註 [加入群組] 和 [加入彙總]。](media/desktop-common-query-tasks/commonquerytasks_groupbynumbered.png)

當您選取 [確定]  時，查詢會執行 **分組方式** 作業並傳回結果。 哇，不得了，結果顯示俄亥俄、伊利諾州、德州和加州現在都有超過一千個機構！

![[計數資料行] 對話方塊，Power Query 編輯器，Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_groupedresult.png)

而且使用 Power Query 編輯器時，您隨時都可以移除最後一個資料塑造作業。 在 [查詢設定]  窗格的 [套用的步驟]  底下，選取最近完成的步驟旁邊的 [X]  。 請繼續實驗。 如果您對結果不滿意，請重做步驟，直到 Power Query 編輯器將資料塑造成您要的樣子。

## <a name="pivot-columns"></a>樞紐資料行

您可以對資料行進行樞紐分析，並建立資料表來包含資料行中每個唯一值的彙總值。 例如，為了解每個產品類別各有多少不同的產品，您可以快速建立資料表來完成此作業。

以下舉例說明。 以下的 **Products_by_Categories** 資料表已經塑造成只會顯示每個 (名稱) 唯一的產品，以及每個產品所屬的類別。 若要建立新的資料表，以顯示每個類別的產品計數 (根據 **CategoryName** 資料行)，請選取資料行，然後選取 [轉換]   > [樞紐資料行]  。

![[樞紐資料行] 命令，Power Query 編輯器，Power BI Desktop](media/desktop-common-query-tasks/pivotcolumns_pivotbutton.png)

[樞紐資料行]  對話方塊隨即出現，讓您知道哪些資料行的值將用來建立新的資料行 (1)。 (如果沒有顯示所需 **CategoryName** 的資料行名稱，請從下拉式清單選取。)當您展開 [進階選項]  (2) 時，可以選取將套用至彙總值 (3) 的函數。

![[樞紐資料行] 對話方塊，Power Query 編輯器，Power BI Desktop](media/desktop-common-query-tasks/pivotcolumns_pivotdialog.png)

當您選取 [確定]  時，查詢會根據 [樞紐資料行]  對話方塊所提供的轉換指示，顯示資料表。

![[樞紐資料行] 結果，Power Query 編輯器，Power BI Desktop](media/desktop-common-query-tasks/pivotcolumns_pivotcomplete.png)

## <a name="create-custom-columns"></a>建立自訂資料行

您可以在 Power Query 編輯器中，建立自訂公式，以在資料表中的多個資料行上運作。 然後將這類公式的結果放入新的 (自訂) 資料行中。 Power Query 編輯器可讓您輕鬆地建立自訂資料行。

在 Power Query 編輯器中使用 Excel 活頁簿資料，移至功能區上的 [加入資料行]  索引標籤，然後選取 [自訂資料行]  。

![[新增自訂資料行] 命令，Power Query 編輯器，Power BI Desktop](media/desktop-common-query-tasks/commonquerytasks_customcolumn.png)

下列對話方塊隨即顯示。 在這個範例中，我們會建立稱為 *Percent ELL* 的自訂資料行，它會計算英語學習者 (ELL) 佔總學生人數的百分比。

![[自訂資料行] 對話方塊，Power Query 編輯器，Power BI Desktop](media/desktop-common-query-tasks/customcolumn_addcustomcolumndialog.png)

和在 Power Query 編輯器中套用的任何其他步驟一樣，如果新的自訂資料行未提供您尋找的資料，可以刪除此步驟。 在 [查詢設定]  窗格的 [套用的步驟]  底下，選取 [已新增自訂]  步驟旁邊的 [X]  。

![[套用的步驟]，[查詢設定] 窗格，Power Query 編輯器，Power BI Desktop](media/desktop-common-query-tasks/customcolumn_addedappliedstep.png)

## <a name="query-formulas"></a>查詢公式

您可以編輯 Power Query 編輯器所產生的步驟。 您也可以建立自訂公式，讓您更準確地連線及塑造資料。 每當 Power Query 編輯器在資料上執行動作時，與動作相關聯的公式會顯示在 [公式列]。 若要檢視公式列，請移至功能區的 [檢視]  索引標籤，然後選取 [公式列]  。

![[公式列] 選項，Power Query 編輯器，Power BI Desktop](media/desktop-common-query-tasks/queryformulas_formulabar.png)

Power Query 編輯器會將每個查詢的所有套用步驟保留為您可以檢視或修改的文字。 您可以使用 [進階編輯器]  ，來查看或修改任何查詢的文字。 只要選取 [檢視]  ，然後選取 [進階編輯器]  。

![[進階編輯器] 命令，Power Query 編輯器，Power BI Desktop](media/desktop-common-query-tasks/queryformulas_advancededitorbutton.png)

以下就來看看 [進階編輯器]  ，其中顯示與 **USA\_StudentEnrollment** 查詢相關聯的查詢步驟。 這些步驟是以 Power Query 公式語言建立，這個語言常稱為 *M*。如需詳細資訊，請參閱 [深入了解 Power Query 公式](https://support.office.com/article/learn-about-power-query-formulas-6bc50988-022b-4799-a709-f8aafdee2b2f)。 若要檢視語言規格本身，請參閱 [Power Query M 語言規格](/powerquery-m/power-query-m-language-specification)。

![[進階編輯器] 對話方塊，Power Query 編輯器，Power BI Desktop](media/desktop-common-query-tasks/queryformulas_advancededitor.png)

Power BI Desktop 提供一組廣泛的公式類別。 如需詳細資訊和所有 Power Query 編輯器公式的完整參考，請參閱 [Power Query M 函式參考](/powerquery-m/power-query-m-function-reference)。

## <a name="next-steps"></a>後續步驟

您可以使用 Power BI Desktop 執行各種作業。 如需有關其功能的詳細資訊，請參閱下列資源：

* [Power BI Desktop 是什麼？](../fundamentals/desktop-what-is-desktop.md)
* [Power BI Desktop 的查詢概觀](desktop-query-overview.md)
* [Power BI Desktop 中的資料來源](../connect-data/desktop-data-sources.md)
* [在 Power BI Desktop 中連線至資料](../connect-data/desktop-connect-to-data.md)
* [使用 Power BI Desktop 合併資料並使其成形](../connect-data/desktop-shape-and-combine-data.md)
