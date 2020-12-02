---
title: 搭配使用外部 R IDE 與 Power BI
description: 您可以啟動外部 IDE，然後搭配 Power BI 使用它
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 05/08/2019
LocalizationGroup: Connect to data
ms.openlocfilehash: 21b46a0c7637509fa54c3d7ed2b5551cde05f784
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96404862"
---
# <a name="use-an-external-r-ide-with-power-bi"></a>搭配使用外部 R IDE 與 Power BI
透過 **Power BI Desktop**，您可以使用您的外部 R IDE (整合式開發環境) 來建立並精簡 R 指令碼，然後在 Power BI 中使用這些指令碼。

![[選項] 對話方塊的螢幕擷取畫面，其中顯示 [偵測到的 R I D E] 欄位中所輸入的 [R Studio]。](media/desktop-r-ide/r-ide_1a.png)

## <a name="enable-an-external-r-ide"></a>啟用外部 R IDE
先前，您得在 **Power BI Desktop** 中使用 R 指令碼編輯器才能建立和執行 R 指令碼。 發行後，您就可以從 **Power BI Desktop** 啟動外部 R IDE，並將您的資料自動匯入及顯示在 R IDE 中。 您可以在該處修改外部 R IDE 中的指令碼，然後將其貼回 **Power BI Desktop** 以建立 Power BI 視覺效果和報表。

自 2016 年 9 月發行的 **Power BI Desktop** (版本 2.39.4526.362) 起，您可以指定想要使用的 R IDE，並使其自動從 **Power BI Desktop** 啟動。

### <a name="requirements"></a>需求
若要使用這項功能，您需要在本機電腦上安裝 **R IDE**。 **Power BI Desktop** 不會包含、部署或安裝 R 引擎，所以您必須在本機電腦上個別安裝 **R**。 您可以使用下列選項選擇要使用哪項 R IDE︰

* 您可以安裝您最喜愛的 R IDE，其中有許多為免費使用，例如 [Revolution Open 下載頁面](https://mran.revolutionanalytics.com/download/) 及 [CRAN Repository](https://cran.r-project.org/bin/windows/base/)。
* **Power BI Desktop** 也支援 [R Studio](https://www.rstudio.com/) 和 **Visual Studio 2015** 與 [*R Tools for Visual Studio*](/visualstudio/rtvs) 編輯器。
* 您也可以安裝不同的 R IDE，並讓 **Power BI Desktop** 啟動該 **R IDE**，方法是進行下列其中一項︰
  
  * 您可建立 **.R** 檔與您想要 **Power BI Desktop** 啟動的外部 IDE 之間的關聯。
  * 您可以指定 **Power BI Desktop** 應該啟動的.exe，方法是從 [選項] 對話方塊的 [R 指令碼選項] 區段選取 [其他]。 您可前往 [檔案] > [選項和設定] > [選項]，即可看見 [選項] 對話方塊。
    
    ![[選項] 對話方塊的螢幕擷取畫面，其中顯示在 [偵測到的 R I D E] 欄位中輸入的 [其他]，以輸入慣用的 R I D E。](media/desktop-r-ide/r-ide_1b.png)

如果您已安裝多個的 R IDE，您可以指定要啟動哪一項，方法是從 [選項] 對話方塊的 [偵測到的 R IDE] 下拉式清單中加以選取。

根據預設，**Power BI Desktop** 將會啟動 **R Studio** 作為外部 R IDE (如果它安裝在本機電腦上)；如果未安裝 **R Studio**，而您具有 **Visual Studio 2015** 與 **R Tools for Visual Studio**，則會改為啟動該項。 如果上述所有 R IDE 皆未安裝，就會啟動與 **.R** 檔案相關聯的應用程式。

如果沒有 **.R** 檔案關聯存在，可以在 [選項] 對話方塊的 [瀏覽至您慣用的 R IDE] 區段中指定自訂 IDE 的路徑。 您也可以啟動不同的 R IDE，方法是選取 **Power BI Desktop** 中 **啟動 R IDE** 箭號圖示旁邊的 **設定** 齒輪圖示。

## <a name="launch-an-r-ide-from-power-bi-desktop"></a>從 Power BI Desktop 啟動 R IDE
請執行下列步驟，以從 **Power BI Desktop** 啟動 R IDE：

1. 將資料載入 **Power BI Desktop**。
2. 從 [欄位] 窗格中選取幾個您想要使用的欄位。 如果您尚未啟用指令碼視覺效果，系統會提示您執行這項操作。
   
   ![[啟用指令碼視覺效果] 對話方塊的螢幕擷取畫面，其提示啟用指令碼視覺效果。](media/desktop-r-ide/r-ide_3.png)
3. 啟用指令碼視覺效果後，您可以從 [視覺效果] 窗格中選取 R 視覺效果，這會建立準備好顯示指令碼結果的空白 R 視覺效果。 [R 指令碼編輯器] 窗格也會出現。
   
   ![[視覺效果] 窗格的螢幕擷取畫面，其中顯示空白的 R 視覺效果。](media/desktop-r-ide/r-ide_4.png)
4. 現在您可以選取要在 R 指令碼中使用的欄位。 當您選取欄位時，[R 指令碼編輯器] 欄位會自動根據您選取的欄位建立指令碼。 您可以直接在 [R 指令碼編輯器] 窗格中建立 (或貼上) R 指令碼，也可以將其保留空白。
   
   ![[視覺效果] 窗格的螢幕擷取畫面，其中顯示具有 R 指令碼編輯器中指令碼的空白 R 視覺效果。](media/desktop-r-ide/r-ide_5.png)
   
   > [!NOTE]
   > R 視覺效果的預設彙總類型為「不摘要」。
   > 
   > 
5. 您現在可以直接從 **Power BI Desktop** 啟動 R IDE。 選取 [R 指令碼編輯器] 標題列右邊的 [啟動 R IDE] 按鈕，如下所示。
   
   ![[R I D E] 窗格的螢幕擷取畫面，其中顯示如何從 [R I D E] 按鈕啟動 R I D E。](media/desktop-r-ide/r-ide_6.png)
6. Power BI Desktop 會啟動您指定的 R IDE，如下圖所示 (在此圖中，**RStudio** 是預設的 R IDE )。
   
   ![在 Power B I Desktop 中啟動 R I D E 的螢幕擷取畫面，其中顯示其在 [R Studio] 中。](media/desktop-r-ide/r-ide_7.png)
   
   > [!NOTE]
   > **Power BI Desktop** 新增會指令碼的前三行，以便在您執行指令碼之後從 **Power BI Desktop** 匯入您的資料。
   > 
   > 
7. 您在 **Power BI Desktop** **R 指令碼編輯器窗格** 中建立的任何指令碼，會從 R IDE 的第 4 行開始出現。 此時，您可以在 R IDE 中建立 R 指令碼。 在 R IDE 中完成 R 指令碼之後，您需要將其複製並貼回 **Power BI Desktop** 的 [R 指令碼編輯器] 窗格中，**Power BI Desktop** 自動產生的前三行指令碼「除外」。 請勿將指令碼前三行複製回 **Power BI Desktop**，這幾行只用於將資料從 **Power BI Desktop** 匯入 R IDE 中。

### <a name="known-limitations"></a>已知的限制
從 Power BI Desktop 直接啟動 R IDE 有一些限制︰

* 不支援自動將您的指令碼從 R IDE 匯出到 **Power BI Desktop** 中。
* 不支援 **R 用戶端** 編輯器 (RGui.exe)，因為編輯器本身並不支援開啟檔案。

## <a name="next-steps"></a>後續步驟
請看看下列有關 Power BI 中 R 的其他資訊。

* [在 Power BI Desktop 中執行 R 指令碼](desktop-r-scripts.md)
* [使用 R 建立 Power BI 視覺效果](../create-reports/desktop-r-visuals.md)
