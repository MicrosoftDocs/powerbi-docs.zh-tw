---
title: 在 Power BI 查詢編輯器中使用 Python
description: 在 Power BI Desktop 查詢編輯器中使用 Python 以進行進階分析
author: otarb
ms.author: otarb
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 06/18/2018
LocalizationGroup: Connect to data
ms.openlocfilehash: fac0b396abd6cde87e7e3b738e53480ce34eba88
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96405161"
---
# <a name="use-python-in-query-editor"></a>在查詢編輯器中使用 Python
您可以在 Power BI Desktop **查詢編輯器** 中使用 **Python**，這是統計學家、資料科學家和資料分析師廣泛使用的程式設計語言。 將 Python 整合到 **資料編輯器** 中，可讓您使用 Python 執行資料清理，以及在資料集執行進階資料成形與分析，包括補足遺漏的資料、預測及叢集等。 **Python** 是功能強大的語言，可用於 **查詢編輯器** 以準備您的資料模型及建立報表。

## <a name="installing-python"></a>安裝 Python
若要在 Power BI Desktop 的 **查詢編輯器** 中使用 **Python**，您必須在本機電腦上安裝 **Python**。 您可以從許多位置免費下載並安裝 **Python**，包括 [官方 Python 下載頁面](https://www.python.org/)以及 [Anaconda](https://anaconda.org/anaconda/python/)。

## <a name="using-python-in-query-editor"></a>在查詢編輯器中使用 Python
為了示範如何在 **查詢編輯器** 中使用 **Python**，我們會使用來自股市資料集的範例，您可以 [從這裡下載](https://download.microsoft.com/download/F/8/A/F8AA9DC9-8545-4AAE-9305-27AD1D01DC03/EuStockMarkets_NA.csv)該 .CSV 檔案並遵循指示。 本範例的步驟如下所示：

1. 首先，將您的資料載入 **Power BI Desktop**。 在此範例中，載入 *EuStockMarkets_NA.csv* 檔案，然後從 **Power BI Desktop** 的 [首頁] 功能區選取 [取得資料] > [CSV]。
   
   ![Power B I Desktop 中 [取得資料] 功能區的螢幕擷取畫面，其中顯示 [CSV] 選取項目。](media/desktop-python-in-query-editor/python-in-query-editor-1.png)
2. 選取檔案後選取 [開啟]，CSV 隨即顯示在 [CSV 檔案] 對話方塊中。
   
   ![[CSV 檔案] 對話方塊的螢幕擷取畫面，其中顯示選取的 CSV。](media/desktop-python-in-query-editor/python-in-query-editor-2.png)
3. 資料載入後，會出現在 Power BI Desktop 的 [欄位] 窗格中。
   
   ![[欄位] 窗格的螢幕擷取畫面，其中顯示已載入的資料。](media/desktop-python-in-query-editor/python-in-query-editor-3.png)
4. 您也可以從 **Power BI Desktop** 的 [首頁] 索引標籤選取 [編輯查詢]，以開啟 **查詢編輯器**。
   
   ![Power B I Desktop 中 [查詢編輯器] 的螢幕擷取畫面，其中顯示 [編輯查詢] 選取項目。](media/desktop-python-in-query-editor/python-in-query-editor-4.png)
5. 在 [轉換] 索引標籤中選取 [執行 Python 指令碼]，[執行 Python 指令碼] 編輯器隨即出現 (於下個步驟示範)。 請注意，第 15 和 20 列遺失了資料，您在下圖中無法看到的其他列亦然。 下方步驟示範 Python 可以 (將會) 如何為您補足這些資料列。
   
   ![[轉換] 索引標籤的螢幕擷取畫面，其中顯示資料列。](media/desktop-python-in-query-editor/python-in-query-editor-5.png)
6. 本範例會輸入下列指令碼：
   
    ```python
       import pandas as pd
       completedData = dataset.fillna(method='backfill', inplace=False)
       dataset["completedValues"] =  completedData["SMI missing values"]
   ```

   > [!NOTE]
   > 您的 Python 環境中必須安裝 *pandas* 程式庫，上述指令碼才能正常運作。 若要安裝 pandas，請在 Python 安裝中執行下列命令： |      > pip install pandas
   > 
   > 
   
   放入 [執行 Python 指令碼] 對話方塊時，程式碼看起來會像這樣：
   
   ![[執行 Python 指令碼] 對話方塊的螢幕擷取畫面，其中顯示指令碼。](media/desktop-python-in-query-editor/python-in-query-editor-5b.png)
7. 選取 [確定] 之後，**查詢編輯器** 會顯示有關資料隱私權的警告。
   
   ![[查詢編輯器] 窗格的螢幕擷取畫面，其中顯示有關資料隱私權的警告。](media/desktop-python-in-query-editor/python-in-query-editor-6.png)
8. 為使 Python 指令碼在 Power BI 服務中正常運作，所有資料來源都必須設為「公用」。 如需隱私權設定及其含意的詳細資訊，請參閱[隱私權等級](../admin/desktop-privacy-levels.md)。
   
   ![[隱私權等級] 對話方塊的螢幕擷取畫面，其中顯示已設定 [公用]。](media/desktop-python-in-query-editor/python-in-query-editor-7.png)
   
   請注意 [欄位] 窗格中稱為 *completedValues* 的新資料行。 請注意，這裡有多個遺失的資料項目，像是第 15 和 18 列。 請參閱下一節，查看 Python 如何處理該狀況。
   

在 Python 指令碼只有五行的情況下，**查詢編輯器** 會透過預測模型填入遺失的值。

## <a name="creating-visuals-from-python-script-data"></a>從 Python 指令碼資料建立視覺效果
現在我們可以建立視覺效果，以了解 Python 指令碼如何使用 *pandas* 程式庫補足遺失的值，如下圖所示：

![視覺效果的螢幕擷取畫面，其中顯示 pandas 程式庫的原始資料和已補足的遺失值。](media/desktop-python-in-query-editor/python-in-query-editor-8.png)

一旦完成該視覺效果以及其他要使用 **Power BI Desktop** 建立的任何視覺效果，您就可以儲存 **Power BI Desktop** 檔案 (儲存為 .pbix 檔案)，然後在 Power BI 服務中使用資料模型，包括屬於其中的 Python 指令碼。

> [!NOTE]
> 想查看完成這些步驟後的完成後 .pbix 檔案嗎？ 幸運的是，您可以在 [這裡](https://download.microsoft.com/download/A/B/C/ABCF5589-B88F-49D4-ADEB-4A623589FC09/Complete%20Values%20with%20Python%20in%20PQ.pbix)下載這些範例中使用的完成後 **Power BI Desktop** 檔案。

一旦將 .pbix 檔案上傳到 Power BI 服務，就必須再執行幾個步驟以 (在服務中) 啟用資料重新整理，並讓視覺效果在服務中保持更新 (資料需要 Python 存取權以更新視覺效果)。 其他步驟如下：

* **為資料集啟用排程重新整理** - 若要為所含資料集使用 Python 指令碼的活頁簿啟用排程重新整理，請參閱 [設定排程重新整理](refresh-scheduled-refresh.md)，其中也包括 **Personal Gateway** 的相關資訊。
* **安裝 Personal Gateway** - 檔案及 Python 安裝所在的電腦上必須安裝 **Personal Gateway**；Power BI 服務必須存取該活頁簿及重新轉譯任何更新的視覺效果。 您可以取得如何[安裝及設定 Personal Gateway](service-gateway-personal-mode.md) 的詳細資訊。

## <a name="limitations"></a>限制
建立於 **查詢編輯器** 並含有 Python 指令碼的查詢有幾項限制：

* 所有 Python 資料來源設定都必須設為「公用」，建立於 **查詢編輯器** 的查詢中其他所有步驟也都必須為公用。 若要取得資料來源設定，請在 **Power BI Desktop** 中選取 **[檔案] > [選像和設定] > [資料來源設定]** 。
  
  ![Power BI Desktop 中 [檔案] 功能表的螢幕擷取畫面，其中顯示 [資料來源設定] 選項。](media/desktop-python-in-query-editor/python-in-query-editor-9.png)
  
  從 [資料來源設定] 對話方塊選取資料來源，然後選取 [編輯權限...]，並確認 [隱私權等級] 已設為「公開」。
  
  ![[資料來源設定] 對話方塊的螢幕擷取畫面，其中顯示 [隱私權等級] 設定為 [公用]。](media/desktop-python-in-query-editor/python-in-query-editor-10.png)    
* 若要啟用 Python 視覺效果或資料集的排程重新整理，您必須啟用 [排程重新整理]，並在裝載活頁簿與 Python 安裝的電腦上安裝 **Personal Gateway**。 如需這兩者的詳細資訊，請參閱本文前一節，其中提供了深入了解各項的連結。
* 目前不支援巢狀資料表 (包含多個資料表的資料表) 

Python 和自訂查詢有各種用途，您可以用想要的呈現方式探索資料並使其成形。
