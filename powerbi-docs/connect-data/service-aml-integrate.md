---
title: 教學課程：在 Power BI 中取用 Azure Machine Learning 模型
titleSuffix: Azure Machine Learning
description: 了解如何在 Power BI 中取用 Azure Machine Learning 模型。
services: machine-learning
ms.service: machine-learning
ms.subservice: core
ms.topic: tutorial
ms.author: samkemp
author: samuel100
ms.reviewer: sdgilley, maggies
ms.date: 02/17/2021
ms.openlocfilehash: 91ba29a09cfdd434c52794e83651736c2b796b1e
ms.sourcegitcommit: fb408dfd39943dbec990a16bcf204671beb4f0aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/18/2021
ms.locfileid: "100655653"
---
# <a name="tutorial-consume-azure-machine-learning-models-in-power-bi"></a>教學課程：在 Power BI 中取用 Azure Machine Learning 模型

此教學課程將逐步引導您建立以機器學習模型為基礎的 Power BI 報表。 完成本教學課程時，您將能夠：

> [!div class="checklist"]
> * 在 Power BI 中，對機器學習模型 (使用 Azure Machine Learning 部署) 進行評分。
> * 在 Power Query 編輯器中，連線到 Azure Machine Learning 模型。
> * 建立具有以該模型為基礎之視覺效果的報表。
> * 將該報表發佈至 Power BI 服務。
> * 針對報表設定排程重新整理。

## <a name="prerequisites"></a>Prerequisites

開始此教學課程之前，您需要：

- 在 Azure Machine Learning 中定型及部署機器學習模型。 使用下列三個 Azure Machine Learning 教學課程的其中一個： 

    - [選項 A：程式碼](/azure/machine-learning/tutorial-power-bi-custom-model)
    - [選項 B：設計工具](/azure/machine-learning/tutorial-power-bi-designer-model)
    - [選項 C：自動化 ML](/azure/machine-learning/tutorial-power-bi-automated-model)

- 註冊[免費試用 Power BI](https://app.powerbi.com/signupredirect?pbi_source=web)。
- 在本機電腦上[安裝 Power BI Desktop](https://powerbi.microsoft.com/desktop/)。

## <a name="create-the-data-model"></a>建立資料模型

開啟 Power BI Desktop 並選取 [取得資料]。 在 [取得資料] 對話方塊中，搜尋 **Web**。 選取 [Web] 來源 > [連線]。

:::image type="content" source="media/service-aml-integrate/pbi-get-data.png" alt-text="顯示 Web 資料的螢幕擷取畫面。":::

在 [從 Web] 對話方塊中，複製下列 URL 並貼到方塊中：

```txt 
https://www4.stat.ncsu.edu/~boos/var.select/diabetes.tab.txt
```

:::image type="content" source="media/service-aml-integrate/pbi-data.png" alt-text="顯示 Web URL 的螢幕擷取畫面。":::

選取 [確定]。

在 [**存取 Web 內容**] 中，選取 [**匿名**  >  **連接]**。

:::image type="content" source="media/service-aml-integrate/anonymous-access-web-content.png" alt-text="顯示 Web 內容匿名存取的螢幕擷取畫面。":::

選取 [轉換資料] 以開啟 [Power Query 編輯器] 視窗。

在 Power Query 編輯器的 [常用] 功能區中，選取 [Azure Machine Learning] 按鈕。

:::image type="content" source="media/service-aml-integrate/aml-button.png" alt-text="顯示 Power Query 編輯器的螢幕擷取畫面。":::

使用單一登入以登入您的 Azure 帳戶之後，您會看到可用服務的清單。 選取您從定型及部署機器學習模型教學課程中建立的 **my-sklearn-service**。 

Power Query 會自動為您填入資料行。 您還記得，在我們的服務結構描述中，有一個已指定輸入的 Python 裝飾項目。 選取 [確定]。

:::image type="content" source="media/service-aml-integrate/aml-pbi-run.png" alt-text="顯示 Azure Machine Learning 模型的螢幕擷取畫面。":::

選取 [確定] 會呼叫 Azure Machine Learning 服務。 其會針對資料和端點觸發有關資料隱私權的警告。

:::image type="content" source="media/service-aml-integrate/data_privacy_warning.png" alt-text="顯示隱私權警告的螢幕擷取畫面。":::

選取 [繼續]。 在下一個畫面中，選取 [略過這個檔案的隱私權等級檢查] > [儲存]。

對資料進行評分之後，Power Query 會另外建立一個名為 **AzureML.my-diabetes-model** 的資料行。

:::image type="content" source="media/service-aml-integrate/scored-data.png" alt-text="顯示已新增評分資料行的螢幕擷取畫面。":::

服務傳回的資料是一份 **清單**。 

> [!NOTE]
> 如果您已部署設計工具模型，就會看到一筆 **記錄**。

若要取得預測，請選取 [ **AzureML.my-糖尿病** ] 資料行標頭中的雙向箭號 > **展開至 [新增** 資料列]。

:::image type="content" source="media/service-aml-integrate/expand-column.png" alt-text="顯示展開資料行圖示的螢幕擷取畫面。":::

展開之後，您會在 [AzureML.my-diabetes-model] 資料行中看到預測。

:::image type="content" source="media/service-aml-integrate/after-expand.png" alt-text="顯示展開的螢幕擷取畫面。":::

遵循下列步驟以完成資料模型的清除作業。

1. 將 [AzureML.my-diabetes-model] 資料行重新命名為 **預測**。
1. 將 [Y] 資料行重新命名為 **實際**。
1. 變更 [實際] 資料行的類型：選取該資料行，然後在 [轉換] 功能區上，選取 [資料類型] > [十進位數字]。
1. 變更 [預測] 資料行的類型：選取該資料行，然後在 [轉換] 功能區上，選取 [資料類型] > [十進位數字]。
1. 在 [常用] 功能區中，選取 [關閉並套用]。

## <a name="create-a-report-with-visualizations"></a>建立具有視覺效果的報表

現在您可以建立一些視覺效果來顯示資料。

1. 在 [視覺效果] 窗格中，選取 [折線圖]。 
1. 選取折線圖視覺效果之後：
1. 將 [年齡] 欄位拖曳至 [軸]。
1. 將 [實際] 欄位拖曳至 [值]。
1. 將 [預測] 欄位拖曳至 [值]。

調整折線圖的大小以填滿頁面。 您的報表現在具有單一折線圖，其中包含兩條線，一條用於預測，另一條則用於實際值，依年齡分佈。

:::image type="content" source="media/service-aml-integrate/report-viz.png" alt-text="顯示報表視覺效果的螢幕擷取畫面。":::

## <a name="publish-the-report"></a>發佈報表

您可以視需要新增更多視覺效果。 為了簡單起見，在此教學課程中，我們將發佈報表。

1. 儲存報表。
1. 選取 [檔案] > [發佈] > [發行至 Power BI]。
1. 登入 Power BI 服務。
1. 選取 [我的工作區]。
1. 成功發佈報表之後，選取 [在 Power BI 中開啟 <MY_PBIX_FILE.pbix>] 連結。 報表會在瀏覽器的 Power BI 中開啟報表。

     :::image type="content" source="media/service-aml-integrate/publish-success.png" alt-text="顯示成功發佈的螢幕擷取畫面。":::

## <a name="enable-datasets-to-refresh"></a>讓資料集重新整理

在使用要評分的新資料重新整理資料來源的案例中，您需要更新認證，以便對資料進行評分。 

在 Power BI 服務內 [我的工作區] 的黑色標題列中，選取 [更多選項 (...)] > [設定] > [設定]。

:::image type="content" source="media/service-aml-integrate/settings-pbi.png" alt-text="顯示設定的螢幕擷取畫面。":::

選取 [資料集]、展開 [資料來源認證]，然後選取 [編輯認證]。

:::image type="content" source="media/service-aml-integrate/data-refresh.png" alt-text="顯示認證重新整理的螢幕擷取畫面。":::

遵循適用於 **azureMLFunctions** 和 **Web** 的指示。 請確定您會選取隱私權等級。 您現在可以為資料設定 [排程重新整理]。 選取 [重新整理頻率] 和 [時區]。 您也可以選取 Power BI 可傳送重新整理失敗通知的電子郵件地址。

:::image type="content" source="media/service-aml-integrate/schedule-refresh.png" alt-text="顯示資料集和評分重新整理的螢幕擷取畫面。":::

選取 [套用]  。

>[!NOTE]
> 重新整理資料時，其也會將資料傳送至您的 Azure Machine Learning 端點以進行評分。

## <a name="clean-up-resources"></a>清除資源

>[!IMPORTANT]
>您可以使用您所建立的資源，作為其他 Azure Machine Learning 教學課程和操作說明文章的先決條件。

如果您不打算使用您所建立的資源，請加以刪除，以免產生任何費用。

1. 在 Azure 入口網站中，選取最左邊的 [資源群組]  。
 
1. 從清單中，選取您所建立的資源群組。

1. 選取 [刪除資源群組]。

   ![在 Azure 入口網站中刪除資源群組選項的螢幕擷取畫面。](./media/service-aml-integrate/delete-resources.png)

1. 輸入資源群組名稱。 然後選取 [刪除]。
1. 在 Power BI 服務的 [我的工作區] 中，刪除報表及相關的資料集。 您不需要刪除您電腦上的 Power BI Desktop 或報表。 Power BI Desktop 免費。

## <a name="next-steps"></a>後續步驟

在此教學課程系列中，您已了解如何在 Power BI 中設定排程，讓您可在 Azure Machine Learning 中利用評分端點來對新資料進行評分。
