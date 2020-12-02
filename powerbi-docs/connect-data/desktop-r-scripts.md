---
title: 在 Power BI Desktop 中執行 R 指令碼
description: 在 Power BI Desktop 中執行 R 指令碼
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 01/14/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 604e90cf2f2c1010559c70df67a6cd54ac08fa36
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96404540"
---
# <a name="run-r-scripts-in-power-bi-desktop"></a>在 Power BI Desktop 中執行 R 指令碼

您可以直接在 Power BI Desktop 執行 R 指令碼，並將產生的資料集匯入 Power BI Desktop 資料模型。

## <a name="install-r"></a>安裝 R

若要在 Power BI Desktop 執行 R 指令碼，您需要在本機電腦上安裝 R。 您可以從許多位置免費下載並安裝 R，包括 [Microsoft R 應用程式網路](https://mran.revolutionanalytics.com/download/)以及 [CRAN 存放庫](https://cran.r-project.org/bin/windows/base/)。 目前的版本支援在安裝路徑中使用 Unicode 字元和空格 (空白字元)。

## <a name="run-r-scripts"></a>執行 R 指令碼

您只要使用 Power BI Desktop 中的幾個步驟，就可以執行 R 指令碼並建立資料模型。 您可以使用這個資料模型，建立報表並在 Power BI 服務上共用它們。 Power BI Desktop的 R 指令碼現在支援包含小數點 (.) 和逗號 (，) 的數字格式。

### <a name="prepare-an-r-script"></a>準備 R 指令碼

若要在 Power BI Desktop 執行 R 指令碼，請在本機 R 開發環境中建立指令碼，並確定已順利執行。

若要在 Power BI Desktop 執行該指令碼，請確定該指令碼可在新的和未修改的工作區中順利執行。 此先決條件表示所有套件和相依性都必須明確地載入並執行。 您可以使用 `source()` 執行相依的指令碼。

當您在 Power BI Desktop 準備和執行 R 指令碼時，會有一些限制：

* 因為只有資料框架會匯入，因此請記得使用資料框架來代表您要匯入至 Power BI 的資料。
* 類型為 [複雜] 和 [向量] 的資料行不會匯入，並且它們會在建立的資料表中以錯誤值取代。
* `N/A` 值會轉譯為 Power BI Desktop 中的 `NULL` 值。
* R 指令碼若執行超過 30 分鐘就會逾時。
* 在 R 指令碼中的互動式呼叫 (例如等待使用者輸入) 會中止指令碼執行。
* 在 R 指令碼中設定工作目錄時，您「必須」  定義工作目錄的完整路徑，而非相對路徑。

### <a name="run-your-r-script-and-import-data"></a>執行 R 指令碼並匯入資料

現在您可以執行 R 指令碼，將資料匯入至 Power BI Desktop：

1. 在 Power BI Desktop 中，選取 [取得資料]  ，選擇 [其他]   > [R 腳本]  ，然後選取 [連接]  ：

    ![連線到 R 指令碼，[其他] 類別，[取得資料] 對話方塊，Power BI Desktop](media/desktop-r-scripts/r-scripts-1.png)

2. 如果在您的本機電腦上安裝 R，只要將您的指令碼複製到指令碼視窗，然後選取 [確定]  。 已安裝的最新版本會顯示為 R 引擎。

    ![[R 指令碼] 對話方塊，Power BI Desktop](media/desktop-r-scripts/r-scripts-2.png)

3. 選取 [確定]  來執行 R 指令碼。 當指令碼順利執行時，您可以選擇要加入 Power BI 模型之產生的資料框架。

您可以控制要使用哪一個 R 安裝來執行指令碼。 若要指定 R 安裝設定，請選取 [檔案]   > [選項及設定]   > [選項]  ，然後選取 [R 指令碼]  。 在 [R 指令碼選項]  底下，[偵測到的 R 主目錄]  下拉式清單會顯示您目前的 R 安裝選項。 如果未列出您想要的 R 安裝，請選擇 [其他]  ，然後在 [設定 R 主目錄]  中，瀏覽至或進入自己慣用的 R 安裝資料夾。

![[R 指令碼] 選項，[選項] 對話方塊，Power BI Desktop](media/desktop-r-scripts/r-scripts-4.png)

### <a name="refresh"></a>Refresh

您可以在 Power BI Desktop 中重新整理 R 指令碼。 當您重新整理的 R 指令碼時，Power BI Desktop 會在 Power BI Desktop 環境中再次執行 R 指令碼。

## <a name="next-steps"></a>後續步驟

請看看下列有關 Power BI 中 R 的其他資訊。

* [使用 R 建立 Power BI 視覺效果](../create-reports/desktop-r-visuals.md)
* [在 Power BI 使用外部 R IDE](desktop-r-ide.md)
