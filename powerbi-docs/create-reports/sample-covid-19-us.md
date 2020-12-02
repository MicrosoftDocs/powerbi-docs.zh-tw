---
title: 適用於美國州和地方政府的 COVID-19 追蹤範例
description: 下載並修改具有 COVID-19 全球大流行美國州和地方資料的範例報表。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: maggies
ms.custom: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 04/28/2020
LocalizationGroup: Samples
ms.openlocfilehash: e6f8e02efa7dc2e56a945aaffcf22d8497052404
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96396007"
---
# <a name="covid-19-tracking-sample-for-us-state-and-local-governments"></a>適用於美國州和地方政府的 COVID-19 追蹤範例

Power BI 小組已建立 COVID-19 追蹤範例，讓美國州和地方政府能夠發佈或自訂關於 COVID-19 的互動式報表。 使用 Power BI Desktop，他們可以分析 COVID-19 資料並加以視覺化，以在城市、郡/縣、州/省和國家層級保持社群資訊流通。 然後使用 Power BI 的發佈到 Web 功能，他們可以共用報表以通知公民。 本文提供不同的選項，其可供在自己的公開案例、部落格或網站中使用 Power BI 的互動式視覺效果。

:::image type="content" source="media/sample-covid-19-us/covid-19-us-tracking-sample.png" alt-text="具有美國資料的 COVID-19 範例":::

本文涵蓋下列操作說明：

- 複製內嵌程式碼，並將其放在您自己的網站上。 
- 進行自訂，例如格式化特定狀態。
- 發佈至 Power BI 服務。
- 發佈到 Web。 
- 使用來自其他來源的資料來混合此資料。 

## <a name="prerequisites"></a>必要條件

在開始使用 Power BI 訴說您的故事之前，您必須先具備下列必要條件：

- 下載免費的 [Power BI Desktop](https://powerbi.microsoft.com/desktop/) 應用程式。
- 註冊 [Power BI 服務](https://powerbi.microsoft.com/get-started/)。

## <a name="option-1-pre-built-embed-code"></a>選項 1：預先建置的內嵌程式碼

Microsoft 已發佈範例報表，並建立了發佈到 Web 內嵌程式碼。 您可以使用內嵌程式碼來內嵌完整範例 (包括國家檢視)，並向下切入至您自己網站中的州/省和郡/縣層級。 發佈此資料之前，建議您先檢閱本文中的[免責聲明](#disclaimers)。

若要在您的網站上包含互動式圖形，請將下列內嵌程式碼複製並貼到您希望圖形顯示在網頁上的位置。  

```
<iframe width="1600" height="900" src="https://app.powerbi.com/view?r=eyJrIjoiMmI2ZjExMzItZTcwNy00YmUwLWFlMTAtYTUxYzVjODZmYjA5IiwidCI6ImMxMzZlZWMwLWZlOTItNDVlMC1iZWFlLTQ2OTg0OTczZTIzMiIsImMiOjF9" frameborder="0" allowFullScreen="true"></iframe>
```

內嵌程式碼是您可以插入至任何 HTML 網頁的 HTML iFrame 元素。 調整提供的 iFrame 寬度和高度，使其符合您的網站。 範例報表是以 16:9 的比例撰寫，因此請選擇保留此維度的大小。 正確實作時圖形會顯示，但不會有任何額外的灰色框線。 在進行這些變更時，[檢閱 iFrame 調整大小祕訣和訣竅](../collaborate-share/service-publish-to-web.md#tips-for-iframe-height-and-width)會很有用。

## <a name="option-2-customize-the-sample-power-bi-file"></a>選項 2：自訂範例 Power BI 檔案

Power BI 檔案包含 .pbix 檔案格式 (可在 Power BI Desktop 中編輯) 的資料和互動式圖形。  

一般的自訂是將報表篩選為特定狀態，然後為您的自訂報表建立您自己的發佈到 Web 內嵌程式碼。

USAFacts 資料是以需要歸屬的「創用 CC 授權條款 (Creative Commons License)」來提供。 發佈此資料之前，請先檢閱[免責聲明](#disclaimers)。

若要開始使用，請[下載 .pbix 檔案 (這裡)](https://go.microsoft.com/fwlink/?linkid=2125058)。

### <a name="update-your-report"></a>更新報表 

1. 下載最新版本的免費應用程式，[Power BI Desktop](https://powerbi.microsoft.com/desktop/) (如果尚未這麼做)。 

2. 下載 [.pbix 檔案](https://go.microsoft.com/fwlink/?linkid=2125058) (如果尚未這麼做)，然後在 Power BI Desktop 中開啟。

3. 若要將報表篩選為特定狀態，請選取箭號以展開 [篩選] 窗格。

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-filters-pane.png" alt-text="展開 [篩選] 窗格":::

4. 選取您感興趣的狀態。 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-filter-selection.png" alt-text="選取狀態":::

5. 若要儲存您的檔案，請選取 [檔案]   >  [儲存]  。 

### <a name="refresh-your-report"></a>重新整理報表 

1. 選取 [重新整理]  按鈕。

    :::image type="content" source="media/sample-covid-19-us/power-bi-desktop-refresh-button.png" alt-text="重新整理按鈕":::

2. 選取 [匿名]   >  [連線]  。 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-azure-blob.png" alt-text="選取匿名":::

 
3. 選取 [忽略隱私權等級]  ，如果顯示 > [儲存]  。 

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-privacy-levels.png" alt-text="設定隱私權等級":::

### <a name="publish-your-report-to-the-power-bi-service"></a>將報表發佈至 Power BI 服務

一旦您根據自己的喜好自訂報表，請[依照這裡所述的步驟發佈報表](../create-reports/desktop-upload-desktop-files.md)至 Power BI 服務。

### <a name="configure-scheduled-refresh"></a>設定排程的重新整理

若要將報表中的資料保持在最新狀態，您可以在發佈報表之後[設定排程重新整理](../connect-data/refresh-scheduled-refresh.md)。

當您遵循這些步驟時，請選擇下列選項：

1. 資料來源認證驗證方法：匿名
2. 此資料來源的隱私權等級設定：公用

若要測試重新整理設定，請選取資料集項目的 [[立即重新整理]](../connect-data/refresh-data.md#data-refresh) 選項。

每次執行排程時，就會載入重新整理的資料。 基礎資料是由 USAFacts 提供，且可能不會像重新整理排程一樣頻繁更新。 檢查 [USAFacts 網站](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/) (英文)，以了解基礎資料上次更新的時間。 

如果您想要在您的網站上發佈自訂報表，最好將排程重新整理設定為與 USAFacts 資料更新一樣的執行頻率。 由於 USAFacts 可能會在每天的不同時間重新整理其資料，因此您可能會想要設定每天數次重新整理。 

### <a name="create-a-publish-to-web-embed-code"></a>建立發佈到 Web 內嵌程式碼 

若要在您自己的網站中內嵌您的自訂報表，請遵循如何[建立您自己的發佈到 Web 內嵌程式碼](../collaborate-share/service-publish-to-web.md#create-embed-codes-with-publish-to-web)指示。

發行內嵌程式碼之後，您可以使用 [確認] 對話方塊上的 iFrame 來內嵌至您的網站。

如果您在 Power BI Desktop 中對報表進行變更，您可以發佈並取代 Power BI 服務中的現有報表。 內嵌程式碼不會變更。 報表變更或重新整理的資料需要大約一小時才會出現在您的網站上。 

## <a name="option-3-mash-up-data-from-another-source"></a>選項 3：從另一個來源混合資料 

您也可以將此報表的資料與另一個來源的資料混合。 下列範例是以[約翰霍普金斯大學](https://github.com/CSSEGISandData/COVID-19) (英文) 的資料為基礎。 發佈此資料之前，建議您先檢閱本文中的[免責聲明](#disclaimers)。

1. 選取 [取得資料]   >  [Web]  。

    :::image type="content" source="media/sample-covid-19-us/power-bi-desktop-get-data.png" alt-text="取得資料按鈕":::

2. 輸入下列 URL︰

    ```
    https://raw.githubusercontent.com/CSSEGISandData/COVID-19/master/csse_covid_19_data/csse_covid_19_time_series/time_series_covid19_confirmed_global.csv
    ```

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-from-web.png" alt-text="從 Web 選取資料":::

3. 選取 [確定]  。 

    > [!NOTE]
    > 約翰霍普金斯大學發佈的連結可能會變更。 如需最新資訊，請參閱[約翰霍普金斯大學 GitHub 頁面](https://github.com/CSSEGISandData/COVID-19) (英文)。

4. 選取 [載入]  ，以載入全球所有確認案例的資料集。  

    :::image type="content" source="media/sample-covid-19-us/power-bi-covid-19-load-data.png" alt-text="從 Web 載入資料":::

    本文[從 Power BI Desktop 連線到網頁](../connect-data/desktop-connect-to-web.md)，提供從 Web 載入資料的詳細資訊。
    
然後，您可以使用 Power BI Desktop 將資料視覺化。 最後，使用 **選項 2：** [將您的報表發佈至 Power BI 服務](#publish-your-report-to-the-power-bi-service)中的步驟，發佈報表並且建立自訂內嵌程式碼。 

## <a name="option-4-use-the-covid-19-us-tracking-template-app"></a>選項 4：使用 COVID-19 美國追蹤報表範本應用程式

還有一個選項，Power BI 小組建立了 COVID-19 美國追蹤「範本應用程式」  ，其有助立即開始使用。 範本應用程式是特定資料來源其報表、儀表板和資料集的組合。 您可從 AppSource 下載並使用範本應用程式，或加以修改以符合需求，然後將其散發給同事。 

此 COVID-19 美國追蹤範本應用程式包含預先建置的 COVID-19 計量報表，可供直接使用、在 Power BI 服務中個人化或視需要下載以新增其他資料來源。 了解如何安裝 [COVID-19 美國追蹤範本應用程式](../connect-data/service-connect-to-covid-19-tracking.md)並立即開始使用。

## <a name="about-the-data-source-for-this-report"></a>關於此報表的資料來源
此互動式報表會彙總來自美國疾病管制與預防中心 (CDC)、州和地方層級公共衛生機構的資料。 郡/縣層級的資料會透過直接參考州和地方機構來確認 (連結)。

資料是由 USAFacts 所提供。 由於資料更新的頻率，可能不會反映政府組織或新聞媒體所回報的確切數字。 如需詳細資訊或下載資料，請造訪 [USAFacts 網站](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/) (英文)。 

## <a name="disclaimers"></a>免責聲明

此報表和資料皆為「連同其本身具有之一切瑕疵」依「現狀」提供，不具任何形式之擔保。 Microsoft 不提供任何明示擔保或保證，也不會明確否認所有默示擔保，包括適售性、適合特定用途，以及未侵權。

USAFacts 資料在「創用 CC 授權條款」之下提供。 若要進行使用，請將 USAFacts 引用為資料提供者，並連結回到 USAFacts。 如需確切的歸屬步驟，請參閱 USAFacts 頁面的 **#MadewithUSAFacts** 區段，[美國地區的冠狀病毒：州/省和郡/縣的 COVID-19 爆發對應](https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/) (英文)。

約翰霍普金斯大學資料為 copyright 2020 Johns Hopkins University, all rights reserved. 僅供教育和學術研究之用。 以下是混合範例中所示資料的完整[使用規定](https://github.com/CSSEGISandData/COVID-19/blob/master/README.md) (英文)。 [約翰霍普金斯大學網站](https://coronavirus.jhu.edu/map-faq.html) (英文) 提供詳細資訊。

## <a name="next-steps"></a>後續步驟

[取得 Power BI 範例](../create-reports/sample-datasets.md)




