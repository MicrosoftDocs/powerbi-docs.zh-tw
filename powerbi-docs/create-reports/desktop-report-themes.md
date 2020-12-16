---
title: 在 Power BI Desktop 中使用報表主題
description: 了解如何在 Power BI Desktop 中使用自訂色彩調色盤，並將其套用至整個報表。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.custom: contperfq4
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 12/14/2020
LocalizationGroup: Create reports
ms.openlocfilehash: e38e88966066d2a4df3bbffbd32bdbb840affe02
ms.sourcegitcommit: 46cf62d9bb33ac7b7eae7910fbba6756f626c65f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97492211"
---
# <a name="use-report-themes-in-power-bi-desktop"></a>在 Power BI Desktop 中使用報表主題

透過 Power BI Desktop 的 *報表主題*，您可以將設計變更套用至整個報表，例如使用公司色彩、變更圖示集，或套用新的預設視覺效果格式。 當您套用報表主題時，報表中所有視覺效果都會使用所選主題中的色彩和格式作為其預設值。 有少數例外狀況，本文稍後將加以說明。

若要選取報表主題，您可以瀏覽至 [檢視] 功能區，然後選取功能區 [主題] 區段的下拉箭號按鈕，並選取您想要的主題。 可用主題和其他 Microsoft 產品 (例如 Microsoft PowerPoint) 中所見的主題類似。

![報表主題](media/desktop-report-themes/report-themes-01.png)

報表主題分成兩種類型：內建報表主題和自訂報表主題檔案。

- **內建** 報表主題提供隨 Power BI Desktop 安裝的各種預先定義色彩配置。 您可以直接從 Power BI Desktop 功能表中選取內建報表主題。

- **自訂** 報表主題則需要您調整目前的主題再儲存為自訂主題，或使用 JSON 檔案建立您自己的自訂主題來加以建立。 JSON 檔案可讓您更精確地控制報表主題的許多層面，如本文稍後所述。 

接下來先說明報表主題的運作方式，再跳到如何建立自訂報表主題。


## <a name="how-report-themes-work"></a>報表主題的運作方式

若要將報表主題套用至 Power BI Desktop 報表，您可以從下列選項中選取：

* 從 Power BI Desktop 內建[可用的內建報表主題](#built-in-report-themes)中選取
* 使用 [自訂主題] 對話方塊來自訂主題
* [匯入自訂主題 JSON 檔案](#import-custom-report-theme-files)。

我們會依序說明每個選項。

> [!NOTE]
> 主題只能在使用 Power BI Desktop 時套用。 您不能將主題套用於 Power BI 服務中的現有報表。 

### <a name="built-in-report-themes"></a>內建報表主題

若要從可用的內建報表主題中選取：

1. 從 [檢視] 功能區中，依序選取 [主題] 下拉箭號按鈕和 [切換主題]。

   ![顯示已選取 [檢視] 功能區的螢幕擷取畫面，其提供數個佈景主題。](media/desktop-report-themes/report-themes-02.png)

2. 從隨即顯示的下拉式功能表中，選取其中包含的主題。

   ![螢幕擷取畫面，其中顯示可供選取的已展開 Power BI 佈景主題。](media/desktop-report-themes/report-themes-03.png)

   您的報表主題此時會套用至報表。

    下表顯示可用的內建報表主題。
    
    | 內建報表主題 | 預設色彩序列 |
    |------ |---------- |
    | 預設 | ![預設](media/desktop-report-themes/report-themes-color-scheme-default.png)|
    | 高樓 | ![高樓](media/desktop-report-themes/report-themes-color-scheme-highrise.png)|
    | 高階主管 | ![高階主管](media/desktop-report-themes/report-themes-color-scheme-executive.png)|
    | 先驅| ![先驅](media/desktop-report-themes/report-themes-color-scheme-frontier.png)|
    | 創新 | ![創新](media/desktop-report-themes/report-themes-color-scheme-innovative.png)|
    | 盛開 | ![盛開](media/desktop-report-themes/report-themes-color-scheme-bloom.png)|
    | 潮汐| ![潮汐](media/desktop-report-themes/report-themes-color-scheme-tidal.png)|
    | 溫度 | ![溫度](media/desktop-report-themes/report-themes-color-scheme-temperature.png)|
    | 日光| ![日光](media/desktop-report-themes/report-themes-color-scheme-solar.png)|
    | 與眾不同 | ![與眾不同](media/desktop-report-themes/report-themes-color-scheme-divergent.png)|
    | 暴風雨 | ![暴風雨](media/desktop-report-themes/report-themes-color-scheme-storm.png)|
    | 傳統 | ![傳統](media/desktop-report-themes/report-themes-color-scheme-classic.png)|
    | 都會公園 | ![都會公園](media/desktop-report-themes/report-themes-color-scheme-city-park.png)|
    | 教室 | ![教室](media/desktop-report-themes/report-themes-color-scheme-classroom.png)|
    | 方便色盲人士辨識 | ![方便色盲人士辨識](media/desktop-report-themes/report-themes-color-scheme-colorblind-safe.png)|
    | 電光 | ![電光](media/desktop-report-themes/report-themes-color-scheme-electric.png)|
    | 高對比 | ![高對比](media/desktop-report-themes/report-themes-color-scheme-high-contrast.png)|
    | 日落 | ![日落](media/desktop-report-themes/report-themes-color-scheme-sunset.png)|
    | 暮光 | ![暮光](media/desktop-report-themes/report-themes-color-scheme-twilight.png)|
    
3. 您也可以從 [主題] 下拉式選單中選取 [佈景主題庫]，瀏覽 Power BI 社群成員所建立的主題集合。

   ![佈景主題庫](media/desktop-report-themes/report-themes-04.png)

    您可以從主題庫中選取喜歡的主題，並下載相關聯的 JSON 檔案。 

    若要安裝下載的檔案，請從 [主題] 下拉式選單中選取 [瀏覽主題]，瀏覽至 JSON 檔案的下載位置，然後加以選取，即可將主題匯入為 Power BI Desktop 的新主題。

    完成時，Power BI 會顯示匯入成功的對話方塊。

   ![成功匯入主題](media/desktop-report-themes/report-themes-05.png)

## <a name="customize-report-themes"></a>自訂報表主題

您可以透過直接在 Power BI Desktop 中進行的自訂，或透過報表主題 JSON 檔案，對 [視覺效果] 窗格的 [格式化] 區段中所列的多數項目進行自訂和標準化。 其目標是要讓您完整而精細地掌控報表的預設外觀及風格。

您可以使用下列兩種自訂報表主題的方式：

- [在 Power BI Desktop 中建立及自訂佈景主題](#create-and-customize-a-theme-in-power-bi-desktop)
- [建立自訂報表主題 JSON 檔案並加以自訂](#introduction-to-report-theme-json-files)

我們會依序在下列各節中說明每一種方法。

### <a name="create-and-customize-a-theme-in-power-bi-desktop"></a>在 Power BI Desktop 中建立及自訂佈景主題

若要直接在 Power BI Desktop 中自訂主題，您可以選取最符合喜好的主題，並進行一些調整。 首先選取最符合喜好的主題 (或直接從任何主題開始自訂)，然後採取下列步驟：

1. 從 [檢視] 功能區中，選取 [主題] 下拉按鈕，然後選取 [自訂目前的主題]。

   ![自訂主題](media/desktop-report-themes/report-themes-06.png)

2. 隨即會出現一個對話方塊，您可以在其中進行對目前主題的各種變更，然後將設定儲存為新的主題。

   ![自訂目前的主題](media/desktop-report-themes/report-themes-07.png)

可自訂的主題設定會位於下列類別下，反映在 [自訂主題] 視窗中：

- **名稱和色彩**：主題名稱和色彩設定包括 [主題色彩](#how-report-theme-colors-stick-with-your-reports)、人氣色彩、發散的色彩和 [結構色彩 (進階)](#setting-structural-colors)。
- **Text**：文字設定包括字型家族、大小和色彩，這會設定標籤、標題、卡片與 KPI 以及索引標籤標頭的 [主要文字類別預設值](#setting-formatted-text-defaults)。
- **視覺效果**：視覺效果設定包括背景、框線、標頭和工具提示。
- **頁面**：頁面項目設定包括底色圖案和背景。
- **篩選窗格**：篩選窗格設定包括背景色彩、透明度、字型和圖示色彩、大小、篩選卡片。

進行變之後，請選取 [套用並儲存]，以儲存您的主題。 您的主題現在已可在目前的報表中使用，且可以匯出。

以這種方式自訂目前的主題，可讓您輕鬆快速地自訂主題。 不過，您可以對主題進行更細微的調整，此時必須修改主題的 [JSON 檔案](#report-theme-json-file-format)。

> [!TIP]
> 您可以使用 [自訂主題] 對話方塊中控制項來自訂最常見的報表主題選項。 如需更多控制，您可以選擇性地匯出主題的 JSON 檔案，並藉由手動修改該檔案中的設定來進行微調。 您可以將微調的 JSON 檔案重新命名，然後加以匯入。

### <a name="import-custom-report-theme-files"></a>匯入自訂報表主題檔案

您也可以採取下列步驟匯入自訂報表主題檔案：

1. 選取 [檢視] 功能區，然後從 [主題] 下拉按鈕選取 [瀏覽主題]。

   ![匯入佈景主題](media/desktop-report-themes/report-themes-08.png)

   這會出現一個視窗，以供您瀏覽至 JSON 主題檔案的位置。

2. 在下圖中，有幾個假日主題檔案可供使用。 我們將為 3 月選擇假日主題 *St Patricks Day.json*。

   ![假日主題](media/desktop-report-themes/report-themes_4.png)

   順利載入主題檔案後，Power BI Desktop 會顯示成功訊息。

   ![成功匯入主題](media/desktop-report-themes/report-themes-05.png)

## <a name="introduction-to-report-theme-json-files"></a>報表主題 JSON 檔案的簡介

 當您開啟上一節所述的基本 JSON 檔案 (St Patricks Day.json) 時，檔案會顯示如下：

 ```json
    {
        "name": "St Patrick's Day",
        "dataColors": ["#568410", "#3A6108", "#70A322", "#915203", "#D79A12", "#bb7711", "#114400", "#aacc66"],
        "background":"#FFFFFF",
        "foreground": "#3A6108",
        "tableAccent": "#568410"
    }
```

此報表主題 JSON 檔案包含以下幾行：

- **name**：報表主題名稱。 此欄位是唯一的必要欄位。
- **dataColors**：要用於 Power BI Desktop 視覺效果資料的十六進位色彩代碼清單。 此清單可隨您的喜好包含任意數量的色彩。
- **background**、**firstLevelElements** 和 **tableAccent** 等：色彩類別。 色彩類別可讓您在報表中同時設定多種結構色彩。

您可以使用此 JSON 檔案作為基礎，以自行建立要匯入的自訂報表主題檔案。 如果您只想要調整報表的基本色彩，請變更檔案中的名稱和十六進位代碼。

在報表主題 JSON 檔案中，您只需定義您想要變更的格式。 您未在 JSON 檔案中指定的項目，都會還原為 Power BI Desktop 的預設設定。

建立 JSON 檔案的優點有很多。 例如，您可以指定讓所有圖表都使用字型大小 12、讓特定視覺效果使用特定字型家族，或關閉特定圖表類型的資料標籤。 使用 JSON 檔案時，您可以建立報表主題檔案而將您的圖表和報表標準化，以便讓組織的報表保持一致。

如需 JSON 檔案格式的詳細資訊，請參閱[報表主題 JSON 檔案格式](#report-theme-json-file-format)。

> [!NOTE]
> 您可以安心使用 [自訂主題](#create-and-customize-a-theme-in-power-bi-desktop) 對話方塊來修改自訂 JSON 報表主題。  該對話方塊不會修改其無法控制的主題設定，且會就地更新對報表主題所做的變更。

## <a name="how-report-theme-colors-stick-with-your-reports"></a>如何讓您的報表保有報表主題色彩

報表發佈至 Power BI 服務時，會保有其報表主題色彩。 [格式] 面板的 [資料色彩] 區段會反映您的報表主題。

若要檢視報表主題中的可用色彩：

1. 選取視覺效果。

2. 從 [視覺效果] 窗格的 [格式] 區段中，選取 [資料色彩]。

3. 選取項目的下拉式清單，以檢視報表主題的 **主題色彩** 資訊。

   ![佈景主題色彩](media/desktop-report-themes/report-themes-09.png)

在此處的範例中，當您從聖派翠克節報表主題中套用數種綠色和棕色色彩之後，請檢視主題色彩。 看到所有綠色嗎？ 這是因為這些色彩已包含在我們匯入並套用的報表主題中。

色彩調色盤中的色彩也會與目前的主題相對應。 例如，假設您為資料點選取了頂端列的第三個色彩。 之後，如果您變更為不同的主題，該資料點色彩將會自動更新為新主題中頂端列的第三個色彩，如同在 Microsoft Office 中變更主題時所看到的一樣。

設定報表主題會變更整個報表視覺效果中使用的預設色彩。 Power BI 會維護包含數百種色彩的清單，以確保視覺效果有許多獨特的色彩可顯示在報表中。 當 Power BI 將色彩指派給視覺效果的數列時，會根據指派數列色彩的先後順序來選取色彩。 當匯入主題時，會重設資料數列的色彩對應。 

Power BI 會追蹤動態數列的色彩，並針對其他視覺效果中的值使用相同色彩。 在「動態數列」中，視覺效果中所呈現的數列個數可能會根據量值、值或其他層面而變更。 例如，如果您在報表中「依區域顯示利潤」，則銷售區域數目可能是 5，或可能是 9。 區域數目是動態的，因此會被視為動態數列。 

相反地，對於「靜態數列」，數列數目為已知。 例如，「收益」和「營收」是靜態數列。 在靜態數列中，Power BI 會透過主題調色盤中的索引來指派色彩。 您可從 [資料色彩] 底下的 [格式化] 窗格中選取色彩，以覆寫預設的色彩指派。 您可能必須變更交叉分析篩選器選取項目，才能查看所有可能的數列值，並同時設定其色彩。 如果使用 [屬性] 窗格明確設定單一視覺效果，則所匯入主題不會套用至任何明確定義的色彩。 

若要允許主題套用至這些明確選取的色彩，請針對已明確設定色彩的視覺效果，使用 [資料色彩] 區段中的 [還原為預設]，以復原明確的色彩應用程式，並允許套用主題。


### <a name="situations-when-report-theme-colors-wont-stick-to-your-reports"></a>您的報表未保有報表主題色彩的情況

假設您使用色彩選擇器中的 [自訂色彩] 選項，將自訂色彩集 (或個別色彩) 套用至視覺效果中的特定資料點。 當您套用報表主題時，將「不會」覆寫該自訂的資料點色彩。

或者，假設您想要透過使用 [主題色彩] 區段來手動設定資料點色彩。 當您套用新的報表主題時，這些色彩並 *不會* 更新。 若要還原為您的預設色彩，以便在套用新的報表主題時加以更新，請選取 [還原為預設值]，或從色彩選擇器的 [主題色彩] 調色盤中選取色彩。

![還原為預設值](media/desktop-report-themes/report-themes-10.png)

許多 Power BI 視覺效果將不會套用至報表主題。

## <a name="custom-report-theme-files-you-can-use-right-now"></a>您可以立即使用的自訂報表主題檔案

要開始使用報表主題嗎？ 查看[主題資源庫](https://community.powerbi.com/t5/Themes-Gallery/bd-p/ThemesGallery)中的自訂報表主題，或查看下列現成的自訂報表主題 JSON 檔案，您可將其下載並匯入至 Power BI Desktop 報表：

- [波形主題](https://community.powerbi.com/t5/Themes-Gallery/Waveform/m-p/140536)。 在公告第一版報表主題的[部落格文章](https://powerbi.microsoft.com/blog/power-bi-desktop-march-feature-summary/)中即已介紹此報表主題。 [下載 Waveform.json](https://go.microsoft.com/fwlink/?linkid=843924)。

  ![Waveform.json 主題](media/desktop-report-themes/report-themes_10.png)

- [色盲無礙的主題](https://community.powerbi.com/t5/Themes-Gallery/Color-Blind-Friendly/m-p/140597)。
此報表主題可讓視障人士更容易閱讀。 [下載 ColorblindSafe-Longer.json](https://go.microsoft.com/fwlink/?linkid=843923)。

  ![ColorblindSafe-Longer.json 主題](media/desktop-report-themes/report-themes_11.png).

- Power View 主題，具備 Apothecary.json。 [下載 zip 檔案中的 Power View 主題](https://go.microsoft.com/fwlink/?linkid=843925)。

  ![Apothecary.json 主題](media/desktop-report-themes/report-themes_12.png)

- 情人節主題。

  ![情人節主題](media/desktop-report-themes/report-themes_13.png)

  以下是情人節 JSON 檔案的程式碼：

   ```json
       {
           "name": "Valentine's Day",
           "dataColors": ["#990011", "#cc1144", "#ee7799", "#eebbcc", "#cc4477", "#cc5555", "#882222", "#A30E33"],
           "background":"#FFFFFF",
           "foreground": "#ee7799",
           "tableAccent": "#990011"
       }
   ```

以下是您可以用來當作起點的更多報表主題：

- [Sunflower-twilight](https://community.powerbi.com/t5/Themes-Gallery/Sunflower-Twilight/m-p/140749)
- [Plum](https://community.powerbi.com/t5/Themes-Gallery/Plum/m-p/140711)
- [Autumn](https://community.powerbi.com/t5/Themes-Gallery/Autumn/m-p/140746)
- [High contrast](https://community.powerbi.com/t5/Themes-Gallery/Color-Blind-Friendly/m-p/140597)

報表主題可將您的 Power BI Desktop 報表設定為反映您、您的組織，甚至是當季或假日的色彩。

## <a name="export-report-themes"></a>匯出報表主題

您可以直接從 Power BI Desktop 將目前套用的報表主題匯出至 JSON 檔案。 匯出報表主題後，您可以在其他報表中加以重複使用。 此選項可讓您匯出大多數內建主題的 JSON 檔案。 唯一的例外是基底主題 (「傳統」和「預設」)，這些主題會在匯入時建置。

若要從 Power BI Desktop 匯出目前套用的主題：

1. 選取 [檔案] > [選項及設定] > [選項]。

2. 在 [預覽功能] 區段中，選取 [自訂目前的主題]，然後選取 [確定]。

   系統可能會提示您重新啟動 Power BI Desktop，以啟用預覽功能。 重新啟動後，您即可開始匯出目前套用的主題。

3. 從 [常用] 功能區中，選取 [切換主題] > [匯出目前的主題]。

4. 從 [另存新檔] 對話方塊中，瀏覽至用來儲存 JSON 檔案的目錄，然後選取 [儲存]。

## <a name="report-theme-json-file-format"></a>報表佈景主題 JSON 檔案格式

在其最基本的層級中，主題 JSON 檔案只有一個必要的行：**name**。

```json
{
    "name": "Custom Theme"
}
```

除了 **name** 以外，所有其他項目都是選擇性的；這代表您可以自行主題檔案新增要格式化的特定屬性，且能夠對其他項目繼續使用 Power BI 的預設值。

### <a name="setting-theme-colors"></a>設定主題色彩

在 **name** 底下，您可以新增下列基本資料色彩的相關屬性：

- **dataColors**：十六進位色彩代碼清單，可用來設定代表 Power BI Desktop 視覺效果資料的圖形色彩。 此清單可隨您的喜好包含任意數量的色彩。 使用過此清單中的所有色彩之後，如果視覺效果仍需要更多色彩，即會回頭使用 Power BI 的預設色彩調色盤。
- **good**、**neutral**、**bad**：這些屬性會設定瀑布圖和 KPI 視覺效果所使用的狀態色彩。
- **maximum**、**center**、**minimum**、**null**：這些色彩會設定 [設定格式化的條件] 對話方塊中的各種漸層色彩。

定義這些色彩的基本主題可能會顯示如下：

```json
{
    "name": "Custom Theme",
    "dataColors": [
        "#118DFF",
        "#12239E",
        "#E66C37",
        "#6B007B",
        "#E044A7",
        "#744EC2",
        "#D9B300",
        "#D64550",
        "#197278",
        "#1AAB40"
    ],
    "good": "#1AAB40",
    "neutral": "#D9B300",
    "bad": "#D64554",
    "maximum": "#118DFF",
    "center": "#D9B300",
    "minimum": "#DEEFFF",
    "null": "#FF7F48"
}
```

### <a name="setting-structural-colors"></a>設定結構色彩

接下來，您可以新增各種色彩類別，例如 **background** 和 **firstLevelElements**。 這些色彩類別會設定報表中項目的結構色彩，例如視覺效果項目的軸格線、醒目提示色彩和背景色彩。

下表顯示您可以格式化的六個色彩類別。  **色彩類別** 名稱會對應至 [自訂主題](#create-and-customize-a-theme-in-power-bi-desktop) 對話方塊中 [名稱和色彩] 區段 [進階] 子區段內的名稱。

|色彩類別  |其格式化的內容  |
|---------|---------|
| **firstLevelElements** <br> **foreground** (已淘汰) | 標籤背景色彩 (位於資料點之外時) <br> 趨勢線色彩 <br>  文字方塊預設色彩 <br> 資料表和矩陣值及合計字型色彩 資料橫條軸色彩 <br> 卡片資料標籤 <br> 量測計圖說文字值色彩 <br> KPI 目標色彩 <br>  KPI 文字色彩 <br> 交叉分析篩選器項目色彩 (處於焦點模式時)  <br> 交叉分析篩選器下拉式清單項目字型色彩 <br> 交叉分析篩選器數值輸入字型色彩 <br> 交叉分析篩選器標頭字型色彩 <br> 散佈圖比率行色彩 <br> 折線圖趨勢預測線條色彩 <br> 地圖指引線色彩 <br> 篩選窗格和卡片文字色彩|
| **secondLevelElements** <br> **foregroundNeutralSecondary** (已被取代) | 「淺色」[次要文字類別](#setting-formatted-text-defaults) <br> 標籤色彩  <br> 圖例標籤色彩 <br> 軸標籤色彩 <br> 資料表和矩陣標頭字型色彩 <br> 量測計目標和目標指引線色彩 <br>  KPI 趨勢軸色彩 <br> 交叉分析篩選器滑桿色彩 <br> 交叉分析篩選器項目字型色彩 <br> 交叉分析篩選器外框色彩 <br> 折線圖暫留色彩 <br> 多列卡片標題色彩 <br> 功能區圖表筆觸色彩 <br> 圖形地圖框線色彩 <br> 按鈕文字字型色彩 <br> 按鈕圖示線條色彩 <br> 按鈕外框色彩 |
| **thirdLevelElements** <br >**backgroundLight** (已淘汰) | 軸格線色彩 <br> 資料表和矩陣格線色彩 <br> 交叉分析篩選器標頭背景色彩 (處於焦點模式時)  <br> 多列卡片外框色彩  <br> 圖形填滿色彩 <br> 量測計背景色彩 <br> 已套用篩選卡片背景色彩 <br> 當背景 = FFFFFF： <br> 停用按鈕填滿色彩 <br> 停用按鈕外框色彩 <br> |
| **fourthLevelElements** <br> **foregroundNeutralTertiary** (已淘汰) | 圖例變暗色彩 <br> 卡片類別標籤色彩 <br> 多列卡片類別標籤色彩 <br> 多列卡片長條色彩 <br> 漏斗圖轉換率筆觸色彩 <br> 停用按鈕文字字型色彩 <br> 停用按鈕圖示線條色彩 <br> |
| **background** | 標籤背景色彩 (位於資料點之內時) <br> 交叉分析篩選器下拉式清單項目背景色彩  <br> 環圈圖筆觸色彩 <br> 樹狀圖筆觸色彩 <br> 組合圖背景色彩 <br> 按鈕填滿色彩 <br> 篩選窗格和可用篩選卡片背景色彩 |
| **secondaryBackground** <br> **backgroundNeutral** (已被取代) | 資料表和矩陣格線外框色彩 <br> 圖形地圖預設色彩 <br> 功能區圖表功能區填滿色彩 (關閉 [符合數列] 選項時) <br> 當背景 != FFFFFF： <br> 停用按鈕填滿色彩 <br> 停用按鈕外框色彩 <br> |
| **tableAccent** | 覆寫資料表和矩陣格線外框色彩 (若存在的話) |

以下是設定色彩類別的範例主題：

```json
{
    "name": "Custom Theme",
    "firstLevelElements": "#252423",
    "secondLevelElements": "#605E5C",
    "thirdLevelElements": "#F3F2F1",
    "fourthLevelElements": "#B3B0AD",
    "background": "#FFFFFF",
    "secondaryBackground": "#C8C6C4",
    "tableAccent": "#118DFF"
}
```

> [!TIP]
> 如果您想要製作「深色主題」，或有別於「白色」**背景** 樣式上一般「黑色」**firstLevelElements** 的其他彩色主題，也請務必設定其他結構色彩和 [主要文字類別色彩](#setting-formatted-text-defaults) 的值。  這可確保 (例如) 圖表上具有標籤背景的資料標籤會符合預期樣式且可供讀取，並確保軸格線可見。

### <a name="setting-formatted-text-defaults"></a>設定格式化文字預設值

接下來，您可以將文字類別新增至 JSON 檔案。 文字類別類似於色彩類別，但其主要用途是要讓您更新報表上文字群組的字型大小、色彩及系列。

文字類別共有 12 個，但您只需要設定四個類別 (稱為「主要類別」)，便能變更報表中的所有文字格式。  您可以在 [自訂主題](#create-and-customize-a-theme-in-power-bi-desktop) 對話方塊中的 [文字] 區段下，設定這四個主要類別：「一般」會對應至 **標籤**、「標題」會對應至 **標題**、「卡片與 KPI」會對應至 **圖說文字**，而「索引標籤標頭」會對應至 **標頭**。

其他的文字類別 (稱為「次要類別」) 會自動從其相關聯的主要類別衍生其屬性。 通常，和主要類別相比，次要類別會選取較淺的文字色彩，或較大或較小百分比的文字大小。

以「標籤」類別為例。 **標籤** 類別的預設格式為 Segoe UI、#252423 (深灰色色彩) 及 12 點。 此類別用來格式化資料表和矩陣中的值。 一般而言，資料表或矩陣中的總計會有類似的格式，但會以 **粗體標籤** 類別加粗，使其更為醒目。不過，您不需要在主題 JSON 中指定該類別；Power BI 會自動執行此動作。 之後，如果決定在主題中指定使用 14 點字型的標籤，您無須同時更新 **粗體標籤** 類別，因為其文字格式會繼承自 **標籤** 類別。

下表顯示下列資訊：

- 四個主要文字類別、其格式化的內容，及其預設設定
- 每個次要類別、其格式化的內容，及其唯一的預設設定 (與主要類別相比)

|主要類別  |次要類別  |JSON 類別名稱  | 預設設定  |相關聯的視覺效果物件  |
|---------|---------|---------|---------|---------|
| 註標 | N/A | callout | DIN <br> #252423 <br> 45pt |卡片資料標籤 <br> KPI 指標|
|標頭|N/A|header|Segoe UI Semibold <br> #252423 <br> 12pt |關鍵影響因素標頭 |
| 標題 || 標題 |DIN <br> #252423 <br> 12pt |類別目錄軸標題 <br> 值軸標題 <br> 多列卡片標題 * <br> 交叉分析篩選器標頭|
|-| 大標題 | largeTitle |14pt |視覺效果標題 |
|標籤 ||label |Segoe UI<br>#252423<br>10pt |資料表和矩陣資料行標頭 <br> 矩陣資料列標頭<br>資料表和矩陣格線<br>資料表和矩陣值 |
|-|半粗體 |semiboldLabel| Segoe UI Semibold | 關鍵影響因素設定檔文字
|-|大 |largeLabel |12pt | 多列卡片資料標籤 |
|-|小 |smallLabel |9pt |參考行標籤 * <br>交叉分析篩選器日期範圍標籤<br> 交叉分析篩選器數值輸入文字樣式<br>交叉分析篩選器搜尋方塊<br>關鍵影響因素影響因素文字|
|-|淺色 |lightLabel |#605E5C |圖例文字<br>按鈕文字<br>類別目錄軸標籤<br>漏斗圖資料標籤<br>漏斗圖轉換率標籤<br>量測計目標<br>散佈圖類別標籤<br>交叉分析篩選器項目|
|-|粗體 |boldLabel |Segoe UI Bold |矩陣小計<br>矩陣總計<br>資料表合計 |
|-|大和淺色 |largeLightLabel |#605E5C<br>12pt |卡片類別標籤<br>量測計標籤<br>多列卡片類別標籤 |
|-|小和淺色 |smallLightLabel |#605E5C<br>9pt |資料標籤<br>值軸標籤|

*\* 已加星號的項目也會根據報表主題的第一個資料色彩來著色。*

> [!TIP]
> 文字類別的「淺色」變化會從上面定義的[結構色彩](#setting-structural-colors)取其淺色。  如果您想要製作「深色主題」，也請務必設定下列色彩："firstLevelElements" (符合主要文字色彩)、"secondLevelElements" (符合文字預期的「淺色」)，以及 "background" (足以與第一層和第二層項目色彩形成對比)。

以下是僅設定主要文字類別的範例主題：

```json
{
    "name": "Custom Theme",
    "textClasses": {
        "callout": {
            "fontSize": 45,
            "fontFace": "DIN",
            "color": "#252423"
        },
        "title": {
            "fontSize": 12,
            "fontFace": "DIN",
            "color": "#252423"
        },
        "header": {
            "fontSize": 12,
            "fontFace": "Segoe UI Semibold",
            "color": "#252423"
        },
        "label": {
            "fontSize": 10,
            "fontFace": "Segoe UI",
            "color": "#252423"
        }
    }
}
```

由於次要類別繼承自主要類別，因此您不需要在主題檔案中加以設定。 不過，如果不喜歡繼承規則 (例如，如果不想要讓總計成為資料表中以粗體顯示的值)，您可明確地格式化主題檔案中的次要類別，如同格式化主要類別一般。

### <a name="setting-visual-property-defaults-visualstyles"></a>設定視覺效果屬性預設值 (`visualStyles`)

最後，若要建立延伸格式 JSON 檔案，以對報表中所有視覺效果格式進行更詳細且細微的控制，請在 JSON 檔案中新增 **visualStyles** 區段，以巢狀處理格式化詳細資料。 以下是 **visualStyles** 區段的樣板化範例：

```json
    "visualStyles": {
        "<visualName>": {
            "<styleName>": {
                "<cardName>": [{
                    "<propertyName>": <propertyValue>
                }]
            }
        }
    }
```

對於 **visualName** 和 **cardName** 區段，使用特定的視覺效果和卡片名稱。 **styleName** 目前一律是星號 (*)，但在未來的版本中，您將可為視覺效果建立不同的樣式，並為其命名 (類似於資料表和矩陣樣式功能)。 **propertyName** 是格式化選項的名稱，而 **propertyValue** 是該格式選項的值。

針對 **visualName** 和 **cardName**，如果您要將該設定套用至所有具有屬性的視覺效果或卡片，請使用以引號含括的星號。 如果您同時對視覺效果和卡片名稱使用星號，您基本上便是將設定全域套用至報表中，例如對所有視覺效果上的所有文字套用字型大小或特定字型家族。

以下是透過視覺效果樣式設定數個屬性的範例：

```json
{
   "name":"Custom Theme",
   "visualStyles":{
      "*": {
         "*": {
            "*": [{
                "wordWrap": true
            }],
            "categoryAxis": [{
                "gridlineStyle": "dotted"
            }],
            "filterCard": [
              {
                "$id": "Applied",
                "foregroundColor": {"solid": {"color": "#252423" } }
              },
              {
                "$id":"Available",
                "border": true
              }
            ]
         }
      },
      "scatterChart": {
         "*": {
            "bubbles": [{
                  "bubbleSize": -10
            }]
         }
      }
   }
}
```

此範例會進行下列設定：

- 在所有位置開啟自動換行
- 針對所有具有類別軸的視覺效果，將格線樣式設定為點線
- 針對可用及已套用的篩選卡片設定一些格式 (請注意，格式使用 "$id" 來設定不同版本的篩選卡片)
- 將散佈圖的泡泡大小設定為 -10。

> [!NOTE]
> 您只需指定要調整的格式化項目即可。 未包含在 JSON 檔案中的任何格式化項目，都會還原為其預設值和設定。

### <a name="visualstyles-definition-list"></a>`visualStyles` 定義清單

此區段中資料表會定義視覺效果名稱 (**visualName**)、卡片名稱 (**cardName**)、屬性名稱 (**propertyName**)，以及建立 JSON 檔案所需的列舉。

| visualName 值 |
| --- |
| areaChart |
| barChart |
| basicShape |
| card |
| clusteredBarChart |
| clusteredColumnChart |
| columnChart |
| comboChart |
| donutChart |
| filledMap |
| funnel |
| gauge |
| hundredPercentStackedBarChart |
| hundredPercentStackedColumnChart |
| image |
| KPI |
| lineChart |
| lineClusteredColumnComboChart |
| lineStackedColumnComboChart |
| map |
| multiRowCard |
| pieChart |
| pivotTable |
| ribbonChart |
| scatterChart |
| shapeMap |
| slicer |
| stackedAreaChart |
| tableEx |
| treemap |
| waterfallChart |

下表定義 **cardName** 值。 每個資料格中的第一個值是 JSON 檔案字詞。 第二個值是卡片名稱，如 Power BI Desktop 使用者介面中所顯示。

| cardName 值 |
| --- |
| axis：量測計軸 |
| breakdown：分解 |
| bubbles：泡泡 |
| calloutValue：圖說文字值 |
| card：card |
| cardTitle：卡片磚 |
| categoryAxis：X 軸 |
| categoryLabels：類別標籤 |
| columnFormatting：欄位格式化 |
| columnHeaders：資料行標題 |
| dataLabels：資料標籤 |
| fill：填滿 |
| fillPoint：填滿點 |
| forecast：趨勢預測 |
| general：一般 |
| goals：目標 |
| grid：格線 |
| header：標頭 |
| imageScaling：縮放 |
| indicator：指標 |
| items：項目 |
| labels：資料標籤 |
| legend：圖例 |
| lineStyles：圖形 |
| mapControls：地圖控制項 |
| mapStyles：地圖樣式 |
| numericInputStyle：數值輸入 |
| percentBarLabel：轉換速率標籤 |
| plotArea：繪圖區 |
| plotAreaShading：對稱網底 |
| ratioLine：比率行 |
| referenceLine：常數線 |
| ribbonChart：功能區 |
| rotation：旋轉 |
| rowHeaders：資料列標題 |
| selection：選取控制項 |
| sentimentColors：人氣色彩 |
| shape：圖形 |
| slider：滑桿 |
| status：色彩編碼 |
| subTotals：小計 |
| target：目標 |
| total：總計 |
| trend：趨勢線 |
| trendline：趨勢軸 |
| valueAxis：Y 軸 |
| values：值 |
| wordWrap：自動換行 |
| xAxisReferenceLine：X 軸常數線 |
| y1AxisReferenceLine：常數線 |
| zoom：縮放 |

### <a name="properties-within-each-card"></a>每張卡片中的屬性

下列區段定義每張卡片中的屬性。 卡片名稱後面會接著每個屬性名稱。 針對每個屬性：您會在格式化窗格顯示時看見的名稱、該格式化選項的功能描述，以及該格式化選項的類型。 此方法可讓您知道您在主題檔案中可以使用哪些種類的值。

當您使用 **dateTime** 時，日期必須是以單引號括住的 ISO 日期，並且以日期時間為開頭。 請參閱下列範例：

  "datetime'2011-10-05T14:48:00.000Z'"

布林值為 true 或 false。 字串必須以雙引號括住，例如 "this is a string"。 數字便是值本身，不會以引號括住。

色彩會使用下列格式，其中，自訂十六進位代碼應取代下列範例中的 "FFFFFF"：

```json
{ "solid": { "color": "#FFFFFF" } }
```

列舉 (最常用於下拉式清單格式選項) 代表它可以設定為窗格中所顯示的任何選項，例如針對圖例位置使用 "RightCenter"，或是針對圓形資料標籤使用 "Data value, percent of total"。 列舉選項會顯示在屬性清單下方。

```json
{
      "general":{
        "responsive": {
          "type": [
            "bool"
          ],
          "displayName": [
            "(Preview) Responsive"
          ],
          "description": [
            "The visual will adapt to size changes"
          ]
        },
        "legend": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "position": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Position"
          ],
          "description": [
            "Select the location for the legend"
          ]
        },
        "showTitle": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Title"
          ],
          "description": [
            "Display a title for legend symbols"
          ]
        },
        "labelColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        }
      },
      "categoryAxis": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "axisScale": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Scale type"
          ]
        },
        "start": {
          "type": [
            "numeric",
            "dateTime"
          ],
          "displayName": [
            "Start"
          ],
          "description": [
            "Enter a starting value (optional)"
          ]
        },
        "end": {
          "type": [
            "numeric",
            "dateTime"
          ],
          "displayName": [
            "End"
          ],
          "description": [
            "Enter an ending value (optional)"
          ]
        },
        "axisType": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Type"
          ]
        },
        "showAxisTitle": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Title"
          ],
          "description": [
            "Title for the X-axis",
            "Title for the Y-axis"
          ]
        },
        "axisStyle": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Style"
          ]
        },
        "labelColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "labelDisplayUnits": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Display units"
          ],
          "description": [
            "Select the units (millions, billions, etc.)"
          ]
        },
        "labelPrecision": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Value decimal places"
          ],
          "description": [
            "Select the number of decimal places to display for the values"
          ]
        },
        "concatenateLabels": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Concatenate labels"
          ],
          "description": [
            "Always concatenate levels of the hierarchy instead of drawing the hierarchy."
          ]
        },
        "preferredCategoryWidth": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Minimum category width"
          ]
        },
        "titleColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Title color"
          ]
        },
        "titleFontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "titleFontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Title text size"
          ]
        },
        "position": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Position"
          ],
          "description": [
            "Select left or right"
          ]
        },
        "color": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Select color for data labels"
          ]
        },
        "duration": {
          "type": [
            "numeric"
          ]
        }
      },
      "valueAxis": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "position": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Position"
          ],
          "description": [
            "Select left or right"
          ]
        },
        "axisScale": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Scale type"
          ]
        },
        "start": {
          "type": [
            "numeric",
            "dateTime"
          ],
          "displayName": [
            "Start"
          ],
          "description": [
            "Enter a starting value (optional)"
          ]
        },
        "end": {
          "type": [
            "numeric",
            "dateTime"
          ],
          "displayName": [
            "End"
          ],
          "description": [
            "Enter an ending value (optional)"
          ]
        },
        "showAxisTitle": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Title"
          ],
          "description": [
            "Title for the Y-axis",
            "Title for the X-axis"
          ]
        },
        "axisStyle": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Style"
          ]
        },
        "labelColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "labelDisplayUnits": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Display units"
          ],
          "description": [
            "Select the units (millions, billions, etc.)"
          ]
        },
        "labelPrecision": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Value decimal places"
          ],
          "description": [
            "Select the number of decimal places to display for the values"
          ]
        },
        "titleColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Title color"
          ]
        },
        "titleFontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "titleFontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Title text size"
          ]
        },
        "axisLabel": {
          "type": [
            "none"
          ],
          "displayName": [
            "Y-Axis (Column)"
          ]
        },
        "secShow": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show secondary"
          ]
        },
        "alignZeros": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Align zeros"
          ],
          "description": [
            "Align the zero tick marks for both value axes"
          ]
        },
        "secAxisLabel": {
          "type": [
            "none"
          ],
          "displayName": [
            "Y-Axis (Line)"
          ]
        },
        "secPosition": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Position"
          ],
          "description": [
            "Select left or right"
          ]
        },
        "secAxisScale": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Scale type"
          ]
        },
        "secStart": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Start"
          ],
          "description": [
            "Enter a starting value (optional)"
          ]
        },
        "secEnd": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "End"
          ],
          "description": [
            "Enter an ending value (optional)"
          ]
        },
        "secShowAxisTitle": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Title"
          ],
          "description": [
            "Title for the Y-axis"
          ]
        },
        "secAxisStyle": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Style"
          ]
        },
        "secLabelColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ]
        },
        "secFontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "secFontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "secLabelDisplayUnits": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Display units"
          ],
          "description": [
            "Select the units (millions, billions, etc.)"
          ]
        },
        "secLabelPrecision": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Value decimal places"
          ],
          "description": [
            "Select the number of decimal places to display for the values"
          ]
        },
        "secTitleColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Title color"
          ]
        },
        "secTitleFontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "secTitleFontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Title text size"
          ]
        }
      },
      "dataPoint": {
        "defaultColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Default color",
            "Default Column Color"
          ]
        },
        "fill": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Fill"
          ]
        },
        "defaultCategoryColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Default color",
            "Default Column Color"
          ]
        },
        "showAllDataPoints": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show all"
          ]
        }
      },
      "labels": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "showSeries": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "color": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Select color for data labels"
          ]
        },
        "labelDisplayUnits": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Display units"
          ],
          "description": [
            "Select the units (millions, billions, etc.)"
          ]
        },
        "labelPrecision": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Value decimal places"
          ],
          "description": [
            "Select the number of decimal places to display for the values"
          ]
        },
        "showAll": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Customize series"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "labelDensity": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Label density"
          ]
        },
        "labelOrientation": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Orientation"
          ]
        },
        "labelPosition": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Position"
          ]
        },
        "percentageLabelPrecision": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "% decimal places"
          ],
          "description": [
            "Select the number of decimal places to display for the percentages"
          ]
        },
        "labelStyle": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Label style"
          ]
        }
      },
      "lineStyles": {
        "strokeWidth": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Stroke width"
          ]
        },
        "strokeLineJoin": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Join type"
          ]
        },
        "lineStyle": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Line style"
          ]
        },
        "showMarker": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show marker"
          ]
        },
        "markerShape": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Marker shape"
          ]
        },
        "markerSize": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Marker size"
          ]
        },
        "markerColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Marker color"
          ]
        },
        "showSeries": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Customize series",
            "Show"
          ]
        },
        "shadeArea": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Shade area"
          ]
        }
      },
      "plotArea": {
        "transparency": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Transparency"
          ],
          "description": [
            "Set transparency for background color"
          ]
        }
      },
      "trend": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "displayName": {
          "type": [
            "text"
          ],
          "displayName": [
            "Name"
          ],
          "description": [
            "Set trend line name"
          ]
        },
        "lineColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Set trend line color"
          ]
        },
        "transparency": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Transparency"
          ],
          "description": [
            "Set transparency for trend line color"
          ]
        },
        "style": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Style"
          ],
          "description": [
            "Set trend line style"
          ]
        },
        "combineSeries": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Combine Series"
          ],
          "description": [
            "Show one trend line per series or combine"
          ]
        }
      },
      "y1AxisReferenceLine": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "value": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Value"
          ],
          "description": [
            "Set reference line numeric value"
          ]
        },
        "lineColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Set reference line color"
          ]
        },
        "transparency": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Transparency"
          ],
          "description": [
            "Set transparency for reference line color"
          ]
        },
        "style": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Line style"
          ]
        },
        "position": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Position"
          ],
          "description": [
            "Arrange relative to chart data points"
          ]
        },
        "dataLabelShow": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Data label"
          ],
          "description": [
            "Display a data label for the reference line"
          ]
        },
        "dataLabelColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Set the reference line data label color"
          ]
        },
        "dataLabelDecimalPoints": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Decimal Places"
          ]
        },
        "dataLabelHorizontalPosition": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Horizontal Position"
          ],
          "description": [
            "Set the horizontal position for the reference line data label"
          ]
        },
        "dataLabelVerticalPosition": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Vertical Position"
          ],
          "description": [
            "Set the vertical position for the reference line data label"
          ]
        },
        "dataLabelDisplayUnits": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Display units"
          ],
          "description": [
            "Select the units (millions, billions, etc.)"
          ]
        }
      },
      "referenceLine": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "displayName": {
          "type": [
            "text"
          ],
          "displayName": [
            "Name"
          ],
          "description": [
            "Set reference line name"
          ]
        },
        "value": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Value"
          ],
          "description": [
            "Set reference line numeric value"
          ]
        },
        "lineColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Set reference line color"
          ]
        },
        "transparency": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Transparency"
          ],
          "description": [
            "Set transparency for reference line color"
          ]
        },
        "style": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Line style"
          ]
        },
        "position": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Position"
          ],
          "description": [
            "Arrange relative to chart data points"
          ]
        },
        "dataLabelShow": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Data label"
          ],
          "description": [
            "Display a data label for the reference line"
          ]
        },
        "dataLabelColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Set the reference line data label color"
          ]
        },
        "dataLabelDecimalPoints": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Decimal Places"
          ]
        },
        "dataLabelHorizontalPosition": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Horizontal Position"
          ],
          "description": [
            "Set the horizontal position for the reference line data label"
          ]
        },
        "dataLabelVerticalPosition": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Vertical Position"
          ],
          "description": [
            "Set the vertical position for the reference line data label"
          ]
        },
        "dataLabelDisplayUnits": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Display units"
          ],
          "description": [
            "Select the units (millions, billions, etc.)"
          ]
        }
      },
      "line": {
        "lineColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Line color"
          ]
        },
        "transparency": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Transparency"
          ],
          "description": [
            "Set transparency for background color"
          ]
        },
        "weight": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Weight"
          ]
        },
        "roundEdge": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Round edges"
          ]
        }
      },
      "fill": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "fillColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Fill color"
          ]
        },
        "transparency": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Transparency"
          ],
          "description": [
            "Set transparency for background color"
          ]
        }
      },
      "rotation": {
        "angle": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Rotation"
          ]
        }
      },
      "categoryLabels": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "color": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Select color for data labels"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        }
      },
      "wordWrap": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        }
      },
      "dataLabels": {
        "color": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Select color for data labels"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        }
      },
      "cardTitle": {
        "color": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Select color for data labels"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        }
      },
      "card": {
        "outline": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Outline"
          ]
        },
        "outlineColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Outline color"
          ],
          "description": [
            "Color of the outline"
          ]
        },
        "outlineWeight": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Outline weight"
          ],
          "description": [
            "Thickness of the outline in pixels"
          ]
        },
        "barShow": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show bar"
          ],
          "description": [
            "Display a bar to the left side of the card as an accent"
          ]
        },
        "barColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Bar color"
          ]
        },
        "barWeight": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Bar thickness"
          ],
          "description": [
            "Thickness of the bar in pixels"
          ]
        },
        "cardPadding": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Padding"
          ],
          "description": [
            "Background"
          ]
        },
        "cardBackground": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Background"
          ]
        }
      },
      "percentBarLabel": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "color": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Select color for data labels"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        }
      },
      "axis": {
        "min": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Min"
          ]
        },
        "max": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Max"
          ]
        },
        "target": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Target"
          ]
        }
      },
      "target": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "color": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Select color for data labels"
          ]
        },
        "labelDisplayUnits": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Display units"
          ],
          "description": [
            "Select the units (millions, billions, etc.)"
          ]
        },
        "labelPrecision": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Value decimal places"
          ],
          "description": [
            "Select the number of decimal places to display for the values"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        }
      },
      "calloutValue": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "color": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Select color for data labels"
          ]
        },
        "labelDisplayUnits": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Display units"
          ],
          "description": [
            "Select the units (millions, billions, etc.)"
          ]
        },
        "labelPrecision": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Value decimal places"
          ],
          "description": [
            "Select the number of decimal places to display for the values"
          ]
        }
      },
      "forecast": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "displayName": {
          "type": [
            "text"
          ],
          "displayName": [
            "Name"
          ],
          "description": [
            "Set forecast name"
          ]
        },
        "confidenceBandStyle": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Confidence band style"
          ],
          "description": [
            "Set forecast confidence band style"
          ]
        },
        "lineColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Set forecast line color"
          ]
        },
        "transparency": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Transparency"
          ],
          "description": [
            "Set transparency for background color"
          ]
        },
        "style": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Line style"
          ]
        },
        "transform": {
          "type": [
            "queryTransform"
          ]
        }
      },
      "bubbles": {
        "bubbleSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Size"
          ]
        }
      },
      "mapControls": {
        "autoZoom": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Auto zoom"
          ]
        },
        "zoomLevel": {
          "type": [
            "numeric"
          ]
        },
        "centerLatitude": {
          "type": [
            "numeric"
          ]
        },
        "centerLongitude": {
          "type": [
            "numeric"
          ]
        }
      },
      "mapStyles": {
        "mapTheme": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Theme"
          ]
        }
      },
      "shape": {
        "map": {
          "type": [
            "geoJson"
          ]
        },
        "projectionEnum": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Projection"
          ],
          "description": [
            "Projection"
          ]
        }
      },
      "zoom": {
        "autoZoom": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Auto zoom"
          ],
          "description": [
            "Zoom in on shapes with available data"
          ]
        },
        "selectionZoom": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Selection zoom"
          ],
          "description": [
            "Zoom in on selected shapes"
          ]
        },
        "manualZoom": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Manual zoom"
          ],
          "description": [
            "Allow user to zoom and pan"
          ]
        }
      },
      "xAxisReferenceLine": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "value": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Value"
          ],
          "description": [
            "Set reference line numeric value"
          ]
        },
        "lineColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Set reference line color"
          ]
        },
        "transparency": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Transparency"
          ],
          "description": [
            "Set transparency for reference line color"
          ]
        },
        "style": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Line style"
          ]
        },
        "position": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Position"
          ],
          "description": [
            "Arrange relative to chart data points"
          ]
        },
        "dataLabelShow": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Data label"
          ],
          "description": [
            "Display a data label for the reference line"
          ]
        },
        "dataLabelColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Set the reference line data label color"
          ]
        },
        "dataLabelDecimalPoints": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Decimal Places"
          ]
        },
        "dataLabelHorizontalPosition": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Horizontal Position"
          ],
          "description": [
            "Set the horizontal position for the reference line data label"
          ]
        },
        "dataLabelVerticalPosition": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Vertical Position"
          ],
          "description": [
            "Set the vertical position for the reference line data label"
          ]
        },
        "dataLabelDisplayUnits": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Display units"
          ],
          "description": [
            "Select the units (millions, billions, etc.)"
          ]
        }
      },
      "fillPoint": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        }
      },
      "colorByCategory": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        }
      },
      "plotAreaShading": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "upperShadingColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Upper shading"
          ],
          "description": [
            "Shading color of the upper region"
          ]
        },
        "lowerShadingColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Lower shading"
          ],
          "description": [
            "Shading color of the lower region"
          ]
        },
        "transparency": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Transparency"
          ],
          "description": [
            "Set transparency for background color"
          ]
        }
      },
      "ratioLine": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "lineColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ],
          "description": [
            "Set reference line color"
          ]
        },
        "transparency": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Transparency"
          ],
          "description": [
            "Set transparency for line color"
          ]
        },
        "style": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Line style"
          ]
        }
      },
      "grid": {
        "outlineColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Outline color"
          ],
          "description": [
            "Color of the outline"
          ]
        },
        "outlineWeight": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Outline weight"
          ],
          "description": [
            "Thickness of the outline in pixels"
          ]
        },
        "gridVertical": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Vert grid"
          ],
          "description": [
            "Show/Hide the vertical gridlines"
          ]
        },
        "gridVerticalColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Vert grid color"
          ],
          "description": [
            "Color for the vertical gridlines"
          ]
        },
        "gridVerticalWeight": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Vert grid thickness"
          ],
          "description": [
            "Thickness of the vertical gridlines in pixels"
          ]
        },
        "gridHorizontal": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Horiz grid"
          ],
          "description": [
            "Show/Hide the horizontal gridlines"
          ]
        },
        "gridHorizontalColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Horiz grid color"
          ],
          "description": [
            "Color for the horizontal gridlines"
          ]
        },
        "gridHorizontalWeight": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Horiz grid thickness"
          ],
          "description": [
            "Thickness of the horizontal gridlines in pixels"
          ]
        },
        "rowPadding": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Row padding"
          ],
          "description": [
            "Padding in pixels applied to top and bottom of every row"
          ]
        },
        "imageHeight": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Image height"
          ],
          "description": [
            "The height of images in pixels"
          ]
        },
        "textSize": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Text Size"
          ]
        }
      },
      "columnHeaders": {
        "outline": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Outline"
          ]
        },
        "fontColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Font color"
          ],
          "description": [
            "Font color of the cells"
          ]
        },
        "backColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Background color"
          ],
          "description": [
            "Background color of the cells"
          ]
        },
        "wordWrap": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Word wrap"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "autoSizeColumnWidth": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Auto-size column width"
          ]
        },
        "urlIcon": {
          "type": [
            "bool"
          ],
          "displayName": [
            "URL icon"
          ],
          "description": [
            "Show an icon instead of the full URL"
          ]
        }
      },
      "values": {
        "outline": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Outline"
          ]
        },
        "backColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color scales"
          ]
        },
        "fontColorPrimary": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Font color"
          ],
          "description": [
            "Font color of the odd rows"
          ]
        },
        "backColorPrimary": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Background color"
          ],
          "description": [
            "Background color of the odd rows"
          ]
        },
        "fontColorSecondary": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Alternate font color"
          ],
          "description": [
            "Font color of the even rows"
          ]
        },
        "backColorSecondary": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Alternate background color"
          ],
          "description": [
            "Background color of the even rows"
          ]
        },
        "urlIcon": {
          "type": [
            "bool"
          ],
          "displayName": [
            "URL icon"
          ],
          "description": [
            "Show an icon instead of the full URL"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "wordWrap": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Word wrap"
          ]
        },
        "bandedRowHeaders": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Banded row style"
          ],
          "description": [
            "Apply banded row style to the last level of the row group headers, using the colors of the values."
          ]
        },
        "valuesOnRow": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show on rows"
          ],
          "description": [
            "Show values in row groups rather than columns"
          ]
        }
      },
      "total": {
        "outline": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Outline"
          ]
        },
        "fontColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Font color"
          ],
          "description": [
            "Font color of the cells"
          ]
        },
        "backColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Background color"
          ],
          "description": [
            "Background color of the cells"
          ]
        },
        "applyToHeaders": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Apply to labels"
          ]
        },
        "totals": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Totals"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        }
      },
      "columnFormatting": {
        "fontColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Font color"
          ],
          "description": [
            "Font color of the cells"
          ]
        },
        "backColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Background color"
          ],
          "description": [
            "Background color of the cells"
          ]
        },
        "styleHeader": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Color header"
          ]
        },
        "styleValues": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Color values"
          ]
        },
        "styleTotal": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Color total"
          ]
        },
        "styleSubtotals": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Color subtotals"
          ]
        }
      },
      "rowHeaders": {
        "outline": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Outline"
          ]
        },
        "fontColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Font color"
          ],
          "description": [
            "Font color of the cells"
          ]
        },
        "backColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Background color"
          ],
          "description": [
            "Background color of the cells"
          ]
        },
        "wordWrap": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Word wrap"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "stepped": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Stepped layout"
          ],
          "description": [
            "Render row headers with stepped layout"
          ]
        },
        "steppedLayoutIndentation": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Stepped layout indentation"
          ],
          "description": [
            "Set the indentation, in pixels, applied to row headers"
          ]
        },
        "urlIcon": {
          "type": [
            "bool"
          ],
          "displayName": [
            "URL icon"
          ],
          "description": [
            "Show an icon instead of the full URL"
          ]
        }
      },
      "subTotals": {
        "outline": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Outline"
          ]
        },
        "fontColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Font color"
          ],
          "description": [
            "Font color of the cells"
          ]
        },
        "backColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Background color"
          ],
          "description": [
            "Background color of the cells"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "fontSize": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "rowSubtotals": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Total row"
          ]
        },
        "columnSubtotals": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Total column"
          ]
        },
        "applyToHeaders": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Apply to labels"
          ]
        }
      },
      "selection": {
        "selectAllCheckboxEnabled": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Select All"
          ]
        },
        "singleSelect": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Single Select"
          ]
        }
      },
      "header": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "fontColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Font color"
          ],
          "description": [
            "Font color of the cells"
          ]
        },
        "background": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Background"
          ]
        },
        "outline": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Outline"
          ]
        },
        "textSize": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        }
      },
      "items": {
        "fontColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Font color"
          ],
          "description": [
            "Font color of the cells"
          ]
        },
        "background": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Background"
          ]
        },
        "outline": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Outline"
          ]
        },
        "textSize": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        }
      },
      "numericInputStyle": {
        "fontColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Font color"
          ],
          "description": [
            "Font color of the cells"
          ]
        },
        "textSize": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Text Size"
          ]
        },
        "fontFamily": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Font family"
          ]
        },
        "background": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Background"
          ]
        }
      },
      "slider": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        },
        "color": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Color"
          ]
        }
      },
      "dateRange": {
        "includeToday": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Include today"
          ]
        }
      },
      "sentimentColors": {
        "increaseFill": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Increase"
          ]
        },
        "decreaseFill": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Decrease"
          ]
        },
        "totalFill": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Total"
          ]
        },
        "otherFill": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Other"
          ]
        }
      },
      "breakdown": {
        "maxBreakdowns": {
          "type": [
            "integer"
          ],
          "displayName": [
            "Max breakdowns"
          ],
          "description": [
            "The number of individual breakdowns to show (rest grouped into Other)"
          ]
        }
      },
      "indicator": {
        "indicatorDisplayUnits": {
          "type": [
            "formatting"
          ],
          "displayName": [
            "Display units"
          ],
          "description": [
            "Select the units (millions, billions, etc.)"
          ]
        },
        "indicatorPrecision": {
          "type": [
            "numeric"
          ],
          "displayName": [
            "Value decimal places"
          ],
          "description": [
            "Select the number of decimal places to display for the values"
          ]
        },
        "kpiFormat": {
          "type": [
            "text"
          ],
          "displayName": [
            "Format"
          ]
        }
      },
      "trendline": {
        "show": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Show"
          ]
        }
      },
      "goals": {
        "showGoal": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Goal"
          ]
        },
        "showDistance": {
          "type": [
            "bool"
          ],
          "displayName": [
            "Distance"
          ]
        }
      },
      "status": {
        "direction": {
          "type": [
            "enumeration"
          ],
          "displayName": [
            "Direction"
          ]
        },
        "goodColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Good Color"
          ]
        },
        "neutralColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Neutral Color"
          ]
        },
        "badColor": {
          "type": [
            "fill"
          ],
          "displayName": [
            "Bad Color"
          ]
        }
      }
```



### <a name="enumerations-in-the-json-file"></a>JSON 檔案中的列舉
下列區段定義您可以用於 JSON 檔案中的列舉。

```json
    {
        "legend": {
            "position": [
                {
                    "value": "Top",
                    "displayName": "Top"
                },
                {
                    "value": "Bottom",
                    "displayName": "Bottom"
                },
                {
                    "value": "Left",
                    "displayName": "Left"
                },
                {
                    "value": "Right",
                    "displayName": "Right"
                },
                {
                    "value": "TopCenter",
                    "displayName": "Top Center"
                },
                {
                    "value": "BottomCenter",
                    "displayName": "Bottom Center"
                },
                {
                    "value": "LeftCenter",
                    "displayName": "Left Center"
                },
                {
                    "value": "RightCenter",
                    "displayName": "Right center"
                }
            ],
            "legendMarkerRendering": [
                {
                    "value": "markerOnly",
                    "displayName": "Markers only"
                },
                {
                    "value": "lineAndMarker",
                    "displayName": "Line and markers"
                },
                {
                    "value": "lineOnly",
                    "displayName": "Line only"
                }
            ]
        },
        "categoryAxis": {
            "axisScale": [
                {
                    "value": "linear",
                    "displayName": "Linear"
                },
                {
                    "value": "log",
                    "displayName": "Log"
                }
            ],
            "axisType": [
                {
                    "value": "Scalar",
                    "displayName": "Continuous"
                },
                {
                    "value": "Categorical",
                    "displayName": "Categorical"
                }
            ],
            "axisStyle": [
                {
                    "value": "showTitleOnly",
                    "displayName": "Show title only"
                },
                {
                    "value": "showUnitOnly",
                    "displayName": "Show unit only"
                },
                {
                    "value": "showBoth",
                    "displayName": "Show both"
                }
            ],
            "gridlineStyle": [
                {
                    "value": "dashed",
                    "displayName": "Dashed"
                },
                {
                    "value": "solid",
                    "displayName": "Solid"
                },
                {
                    "value": "dotted",
                    "displayName": "Dotted"
                }
            ],
            "position": [
                {
                    "value": "Left",
                    "displayName": "Left"
                },
                {
                    "value": "Right",
                    "displayName": "Right"
                }
            ]
        },
        "valueAxis": {
            "position": [
                {
                    "value": "Left",
                    "displayName": "Left"
                },
                {
                    "value": "Right",
                    "displayName": "Right"
                }
            ],
            "axisScale": [
                {
                    "value": "linear",
                    "displayName": "Linear"
                },
                {
                    "value": "log",
                    "displayName": "Log"
                }
            ],
            "axisStyle": [
                {
                    "value": "showTitleOnly",
                    "displayName": "Show title only"
                },
                {
                    "value": "showUnitOnly",
                    "displayName": "Show unit only"
                },
                {
                    "value": "showBoth",
                    "displayName": "Show both"
                }
            ],
            "gridlineStyle": [
                {
                    "value": "dashed",
                    "displayName": "Dashed"
                },
                {
                    "value": "solid",
                    "displayName": "Solid"
                },
                {
                    "value": "dotted",
                    "displayName": "Dotted"
                }
            ],
            "secPosition": [
                {
                    "value": "Left",
                    "displayName": "Left"
                },
                {
                    "value": "Right",
                    "displayName": "Right"
                }
            ],
            "secAxisScale": [
                {
                    "value": "linear",
                    "displayName": "Linear"
                },
                {
                    "value": "log",
                    "displayName": "Log"
                }
            ],
            "secAxisStyle": [
                {
                    "value": "showTitleOnly",
                    "displayName": "Show title only"
                },
                {
                    "value": "showUnitOnly",
                    "displayName": "Show unit only"
                },
                {
                    "value": "showBoth",
                    "displayName": "Show both"
                }
            ]
        },
        "lineStyles": {
            "strokeLineJoin": [
                {
                    "value": "miter",
                    "displayName": "Miter"
                },
                {
                    "value": "round",
                    "displayName": "Round"
                },
                {
                    "value": "bevel",
                    "displayName": "Bevel"
                }
            ],
            "lineStyle": [
                {
                    "value": "dashed",
                    "displayName": "Dashed"
                },
                {
                    "value": "solid",
                    "displayName": "Solid"
                },
                {
                    "value": "dotted",
                    "displayName": "Dotted"
                }
            ],
            "markerShape": [
                {
                    "value": "circle",
                    "displayName": "●"
                },
                {
                    "value": "square",
                    "displayName": "■"
                },
                {
                    "value": "diamond",
                    "displayName": "◆"
                },
                {
                    "value": "triangle",
                    "displayName": "▲"
                },
                {
                    "value": "x",
                    "displayName": "☓"
                },
                {
                    "value": "shortDash",
                    "displayName": " -"
                },
                {
                    "value": "longDash",
                    "displayName": "—"
                },
                {
                    "value": "plus",
                    "displayName": "+"
                }
            ]
        },
        "trend": {
            "style": [
                {
                    "value": "dashed",
                    "displayName": "Dashed"
                },
                {
                    "value": "solid",
                    "displayName": "Solid"
                },
                {
                    "value": "dotted",
                    "displayName": "Dotted"
            }
        ]
    },
    "y1AxisReferenceLine": {
        "style": [
            {
                "value": "dashed",
                "displayName": "Dashed"
            },
            {
                "value": "solid",
                "displayName": "Solid"
            },
            {
                "value": "dotted",
                "displayName": "Dotted"
            }
        ],
        "position": [
            {
                "value": "back",
                "displayName": "Behind"
            },
            {
                "value": "front",
                "displayName": "In Front"
            }
        ],
        "dataLabelText": [
            {
                "value": "Value",
                "displayName": "Value"
            },
            {
                "value": "Name",
                "displayName": "Name"
            },
            {
                "value": "ValueAndName",
                "displayName": "Name and Value"
            }
        ],
        "dataLabelHorizontalPosition": [
            {
                "value": "left",
                "displayName": "Left"
            },
            {
                "value": "right",
                "displayName": "Right"
            }
        ],
        "dataLabelVerticalPosition": [
            {
                "value": "above",
                "displayName": "Above"
            },
            {
                "value": "under",
                "displayName": "Under"
            }
        ]
    },
    "referenceLine": {
        "style": [
            {
                "value": "dashed",
                "displayName": "Dashed"
            },
            {
                "value": "solid",
                "displayName": "Solid"
            },
            {
                "value": "dotted",
                "displayName": "Dotted"
            }
        ],
        "position": [
            {
                "value": "back",
                "displayName": "Behind"
            },
            {
                "value": "front",
                "displayName": "In Front"
            }
        ],
        "dataLabelText": [
      {
        "value": "Value",
        "displayName": "Value"
      },
      {
        "value": "Name",
        "displayName": "Name"
      },
      {
        "value": "ValueAndName",
        "displayName": "Name and Value"
      }
    ],
    "dataLabelHorizontalPosition": [
      {
        "value": "left",
        "displayName": "Left"
      },
      {
        "value": "right",
        "displayName": "Right"
      }
    ],
    "dataLabelVerticalPosition": [
      {
        "value": "above",
        "displayName": "Above"
      },
      {
        "value": "under",
        "displayName": "Under"
      }
    ]
    },
    "labels": {
    "labelOrientation": [
      {
        "value": "vertical",
        "displayName": "Vertical"
      },
      {
        "value": "horizontal",
        "displayName": "Horizontal"
      }
    ],
    "labelPosition": [
      {
        "value": "Auto",
        "displayName": "Auto"
      },
      {
        "value": "InsideEnd",
        "displayName": "Inside End"
      },
      {
        "value": "OutsideEnd",
        "displayName": "Outside End"
      },
      {
        "value": "InsideCenter",
        "displayName": "Inside Center"
      },
      {
        "value": "InsideBase",
        "displayName": "Inside Base"
      }
    ],
    "labelStyle": [
      {
        "value": "Category",
        "displayName": "Category"
      },
      {
        "value": "Data",
        "displayName": "Data value"
      },
      {
        "value": "Percent of total",
        "displayName": "Percent of total"
      },
      {
        "value": "Both",
        "displayName": "Category, data value"
      },
      {
        "value": "Category, percent of total",
        "displayName": "Category, percent of total"
      },
      {
        "value": "Data value, percent of total",
        "displayName": "Data value, percent of total"
      },
      {
        "value": "Category, data value, percent of total",
        "displayName": "All detail labels"
      }
     ]
    },
    "card": {
        "outline": [
          {
            "value": "None",
            "displayName": "None"
          },
          {
            "value": "BottomOnly",
            "displayName": "Bottom only"
          },
          {
            "value": "TopOnly",
            "displayName": "Top only"
          },
          {
            "value": "LeftOnly",
            "displayName": "Left only"
          },
          {
            "value": "RightOnly",
            "displayName": "Right only"
          },
          {
            "value": "TopBottom",
            "displayName": "Top + bottom"
          },
          {
            "value": "LeftRight",
            "displayName": "Left + right"
          },
          {
            "value": "Frame",
            "displayName": "Frame"
          }
         ]
    },
    "imageScaling": {
        "imageScalingType": [
          {
            "value": "Normal",
            "displayName": "Normal"
          },
          {
            "value": "Fit",
            "displayName": "Fit"
          },
          {
            "value": "Fill",
            "displayName": "Fill"
          }
        ]
    },
    "forecast": {
        "confidenceBandStyle": [
          {
            "value": "fill",
            "displayName": "Fill"
          },
          {
            "value": "line",
            "displayName": "Line"
          },
          {
            "value": "none",
            "displayName": "None"
          }
        ],
        "style": [
          {
            "value": "dashed",
            "displayName": "Dashed"
          },
          {
            "value": "solid",
            "displayName": "Solid"
          },
          {
            "value": "dotted",
            "displayName": "Dotted"
          }
        ]
        },
        "mapStyles": {
        "mapTheme": [
          {
            "value": "aerial",
            "displayName": "Aerial"
          },
          {
            "value": "canvasDark",
            "displayName": "Dark"
          },
          {
            "value": "canvasLight",
            "displayName": "Light"
          },
          {
            "value": "grayscale",
            "displayName": "Grayscale"
          },
          {
            "value": "road",
            "displayName": "Road"
          }
        ]
    },
    "shape": {
        "projectionEnum": [
          {
            "value": "albersUsa",
            "displayName": "Albers USA"
          },
          {
            "value": "equirectangular",
            "displayName": "Equirectangular"
          },
          {
            "value": "mercator",
            "displayName": "Mercator"
          },
          {
            "value": "orthographic",
            "displayName": "Orthographic"
          }
        ]
        },
        "xAxisReferenceLine": {
        "style": [
          {
            "value": "dashed",
            "displayName": "Dashed"
          },
          {
            "value": "solid",
            "displayName": "Solid"
          },
          {
            "value": "dotted",
            "displayName": "Dotted"
          }
        ],
        "position": [
          {
            "value": "back",
            "displayName": "Behind"
          },
          {
            "value": "front",
            "displayName": "In Front"
          }
        ],
        "dataLabelText": [
          {
            "value": "Value",
            "displayName": "Value"
          },
          {
            "value": "Name",
            "displayName": "Name"
          },
          {
            "value": "ValueAndName",
            "displayName": "Name and Value"
          }
        ],
        "dataLabelHorizontalPosition": [
          {
            "value": "left",
            "displayName": "Left"
          },
          {
            "value": "right",
            "displayName": "Right"
          }
        ],
        "dataLabelVerticalPosition": [
          {
            "value": "above",
            "displayName": "Above"
          },
          {
            "value": "under",
            "displayName": "Under"
          }
        ]
        },
        "ratioLine": {
        "style": [
          {
            "value": "dashed",
            "displayName": "Dashed"
          },
          {
            "value": "solid",
            "displayName": "Solid"
          },
          {
            "value": "dotted",
            "displayName": "Dotted"
          }
        ]
        },
        "columnHeaders": {
        "outline": [
          {
            "value": "None",
            "displayName": "None"
          },
          {
            "value": "BottomOnly",
            "displayName": "Bottom only"
          },
          {
            "value": "TopOnly",
            "displayName": "Top only"
          },
          {
            "value": "LeftOnly",
            "displayName": "Left only"
          },
          {
            "value": "RightOnly",
            "displayName": "Right only"
          },
          {
            "value": "TopBottom",
            "displayName": "Top + bottom"
          },
          {
            "value": "LeftRight",
            "displayName": "Left + right"
          },
          {
            "value": "Frame",
            "displayName": "Frame"
          }
        ]
        },
        "values": {
        "outline": [
          {
            "value": "None",
            "displayName": "None"
          },
          {
            "value": "BottomOnly",
            "displayName": "Bottom only"
          },
          {
            "value": "TopOnly",
            "displayName": "Top only"
          },
          {
            "value": "LeftOnly",
            "displayName": "Left only"
          },
          {
            "value": "RightOnly",
            "displayName": "Right only"
          },
          {
            "value": "TopBottom",
            "displayName": "Top + bottom"
          },
          {
            "value": "LeftRight",
            "displayName": "Left + right"
          },
          {
            "value": "Frame",
            "displayName": "Frame"
          }
        ]
        },
        "total": {
        "outline": [
          {
            "value": "None",
            "displayName": "None"
          },
          {
            "value": "BottomOnly",
            "displayName": "Bottom only"
          },
          {
            "value": "TopOnly",
            "displayName": "Top only"
          },
          {
            "value": "LeftOnly",
            "displayName": "Left only"
          },
          {
            "value": "RightOnly",
            "displayName": "Right only"
          },
          {
            "value": "TopBottom",
            "displayName": "Top + bottom"
          },
          {
            "value": "LeftRight",
            "displayName": "Left + right"
          },
          {
            "value": "Frame",
            "displayName": "Frame"
          }
        ]
        },
        "rowHeaders": {
        "outline": [
          {
            "value": "None",
            "displayName": "None"
          },
          {
            "value": "BottomOnly",
            "displayName": "Bottom only"
          },
          {
            "value": "TopOnly",
            "displayName": "Top only"
          },
          {
            "value": "LeftOnly",
            "displayName": "Left only"
          },
          {
            "value": "RightOnly",
            "displayName": "Right only"
          },
          {
            "value": "TopBottom",
            "displayName": "Top + bottom"
          },
          {
            "value": "LeftRight",
            "displayName": "Left + right"
          },
          {
            "value": "Frame",
            "displayName": "Frame"
          }
        ]
        },
        "subTotals": {
        "outline": [
          {
            "value": "None",
            "displayName": "None"
          },
          {
            "value": "BottomOnly",
            "displayName": "Bottom only"
          },
          {
            "value": "TopOnly",
            "displayName": "Top only"
          },
          {
            "value": "LeftOnly",
            "displayName": "Left only"
          },
          {
            "value": "RightOnly",
            "displayName": "Right only"
          },
          {
            "value": "TopBottom",
            "displayName": "Top + bottom"
          },
          {
            "value": "LeftRight",
            "displayName": "Left + right"
          },
          {
            "value": "Frame",
            "displayName": "Frame"
          }
        ],
        "rowSubtotalsPosition": [
          {
            "value": "Top",
            "displayName": "Top"
          },
          {
            "value": "Bottom",
            "displayName": "Bottom"
          }
        ]
        },
        "general": {
        "orientation": [
          {
            "value": "vertical",
            "displayName": "Vertical"
          },
          {
            "value": "horizontal",
            "displayName": "Horizontal"
          }
        ]
        },
        "data": {
        "relativeRange": [
          {
            "value": "Last",
            "displayName": "Last"
          },
          {
            "value": "Next",
            "displayName": "Next"
          },
          {
            "value": "This",
            "displayName": "This"
          }
        ],
        "relativePeriod": [
          {
            "value": "None",
            "displayName": "Select"
          },
          {
            "value": "Days",
            "displayName": "Days"
          },
          {
            "value": "Weeks",
            "displayName": "Weeks"
          },
          {
            "value": "Calendar Weeks",
            "displayName": "Weeks (Calendar)"
          },
          {
            "value": "Months",
            "displayName": "Months"
          },
          {
            "value": "Calendar Months",
            "displayName": "Months (Calendar)"
          },
          {
            "value": "Years",
            "displayName": "Years"
          },
          {
            "value": "Calendar Years",
            "displayName": "Years (Calendar)"
          }
        ],
        "mode": [
          {
            "value": "Between",
            "displayName": "Between"
          },
          {
            "value": "Before",
            "displayName": "Before"
          },
          {
            "value": "After",
            "displayName": "After"
          },
          {
            "value": "Basic",
            "displayName": "List"
          },
          {
            "value": "Dropdown",
            "displayName": "Dropdown"
          },
          {
            "value": "Relative",
            "displayName": "Relative"
          },
          {
            "value": "Single",
            "displayName": "Single Value"
          }
        ]
        },
        "header": {
        "outline": [
          {
            "value": "None",
            "displayName": "None"
          },
          {
            "value": "BottomOnly",
            "displayName": "Bottom only"
          },
          {
            "value": "TopOnly",
            "displayName": "Top only"
          },
          {
            "value": "LeftOnly",
            "displayName": "Left only"
          },
          {
            "value": "RightOnly",
            "displayName": "Right only"
          },
          {
            "value": "TopBottom",
            "displayName": "Top + bottom"
          },
          {
            "value": "LeftRight",
            "displayName": "Left + right"
          },
          {
            "value": "Frame",
            "displayName": "Frame"
          }
        ]
        },
        "items": {
        "outline": [
          {
            "value": "None",
            "displayName": "None"
          },
          {
            "value": "BottomOnly",
            "displayName": "Bottom only"
          },
          {
            "value": "TopOnly",
            "displayName": "Top only"
          },
          {
            "value": "LeftOnly",
            "displayName": "Left only"
          },
          {
            "value": "RightOnly",
            "displayName": "Right only"
          },
          {
            "value": "TopBottom",
            "displayName": "Top + bottom"
          },
          {
            "value": "LeftRight",
            "displayName": "Left + right"
          },
          {
            "value": "Frame",
            "displayName": "Frame"
          }
        ]
        },
        "status": {
        "direction": [
          {
            "value": "Positive",
            "displayName": "High is good"
          },
          {
            "value": "Negative",
            "displayName": "Low is good"
          }
         ]
       }
    }
  }
}
```

## <a name="limitations-and-considerations"></a>限制與考量

如果您使用其中一個原始主題、「傳統」主題，或在上述其中一個主題上匯入的自訂主題，則無法使用 [主題] 對話方塊的 [文字] 區段來進行設定。

受此限制影響的內建主題包括下列主題：
* 傳統
* 都會公園
* 教室
* 方便色盲人士辨識
* 電光
* 高對比
* 日落
* 暮光

如果您使用其中一個受影響主題，且不需要修改文字設定，則可以安心使用對話方塊的其他索引標籤，而不會有任何問題。 不過，如果您想要搭配其中一個受影響的主題使用文字類別，您有兩個選擇：

- 若要啟用文字類別，則最簡單快速的方式是選取預設主題選項。
- 若要啟用 [文字] 索引標籤來保留目前的自訂主題：
  1. 匯出您目前的主題。
  1. 選取預設主題。
  1. 匯入您在第一個步驟中匯出的自訂主題。

您報表中的文字看起來會不同，但您將能夠存取 [主題] 對話方塊中的 [文字] 索引標籤。


