---
title: 從 Power BI 視覺效果匯出資料
description: 從報表視覺效果和儀表板視覺效果匯出資料，並在 Excel 中檢視。
author: msftrien
manager: kvivek
ms.reviewer: tessa
featuredvideoid: jtlLGRKBvXY
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: how-to
ms.date: 09/09/2020
ms.author: rien
LocalizationGroup: Visualizations
ms.openlocfilehash: bbeabcd3cbdc04378ea90908703744489371b11f
ms.sourcegitcommit: 5ccab484cf3532ae3a16acd5fc954b7947bd543a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/06/2020
ms.locfileid: "93412962"
---
# <a name="export-the-data-that-was-used-to-create-a-visualization"></a>匯出用於建立視覺效果的資料

> [!IMPORTANT]
> 並非所有使用者都可以檢視或匯出所有資料。 報表設計師和系統管理員在建置儀表板和報表時，有一些可採取的保護措施。 某些資料受到限制、隱藏或保密，若無特殊權限則無法查看或匯出。 

## <a name="who-can-export-data"></a>誰可以匯出資料

如果您有資料的權限，您就可以查看並匯出 Power BI 用來建立視覺效果的資料。 資料通常為保密，或僅限於特定使用者。 在此情況下，您無法查看或匯出該資料。 如需詳細資料，請參閱本文件結尾的＜限制和考量＞一節。 


## <a name="viewing-and-exporting-data"></a>檢視和匯出資料

如果想要查看 Power BI 用來建立視覺效果的資料，[您可以在 Power BI 中顯示該資料](service-reports-show-data.md)。 您也可以將該資料匯出至 Excel，作為 *.xlsx* 或 *.csv* 檔案。 匯出資料的選項需要 Pro 或 Premium 授權，以及資料集和報表的編輯權限。 如果可存取儀表板或報表，但資料分類為「高度機密」，則 Power BI 不允許匯出資料。

觀看 Will 從其報表的其中一個視覺效果中匯出資料、將資料儲存為 *.xlsx* 檔案，並在 Excel 中開啟它。 然後遵循影片下方的逐步指示親自試試看。 請注意，這部影片使用舊版的 Power BI。

<iframe width="560" height="315" src="https://www.youtube.com/embed/KjheMTGjDXw" frameborder="0" allowfullscreen></iframe>

## <a name="export-data-from-a-power-bi-dashboard"></a>從 Power BI 儀表板匯出資料

1. 選取視覺效果右上角的 [更多動作] (...)。

    ![箭號指向省略符號按鈕的視覺效果螢幕擷取畫面。](media/power-bi-visualization-export-data/pbi-export-tile3.png)

1. 選擇 [匯出至 .csv] 選項。

    ![標示 [匯出資料] 選項的省略符號下拉式清單螢幕擷取畫面。](media/power-bi-visualization-export-data/power-bi-export-data.png)

1. Power BI 會將資料匯出至 *.csv* 檔案。 如果您已篩選視覺效果，則 .csv 匯出也會一併篩選。 

1. 您的瀏覽器會提示您儲存檔案。  儲存之後，請在 Excel 中開啟 *.csv* 檔案。

    ![顯示所匯出資料的 .csv 檔案螢幕擷取畫面。](media/power-bi-visualization-export-data/pbi-export-to-excel.png)

## <a name="export-data-from-a-report"></a>從報表匯出資料

若要跟著做，請在 [編輯] 檢視中開啟 Power BI 服務中的[採購分析範例報表](../create-reports/sample-procurement.md)。 新增空白的報表頁面。 然後遵循以下步驟來新增彙總、階層和視覺效果層級篩選。

### <a name="create-a-stacked-column-chart"></a>建立堆疊直條圖

1. 建立新的 [堆疊直條圖]。

    ![群組直條圖範本的螢幕擷取畫面。](media/power-bi-visualization-export-data/power-bi-clustered.png)

1. 從 [欄位] 窗格，選取 [位置] > [城市]、[位置] > [國家/地區] 和 [發票] > [折扣百分比]。  您可能必須將 [折扣百分比] 移到 [值] 區。

    ![利用所標示 [城市] 和 [折扣百分比計數] 建置的視覺效果螢幕擷取畫面。](media/power-bi-visualization-export-data/power-bi-build.png)

1. 將 [折扣百分比] 的彙總從 [計數] 變更為 [平均]。 在 [值] 區中，選取 [折扣百分比] 右邊的箭號 (可能是 [折扣百分比計數])，然後選擇 [平均]。

    ![已標示 [平均] 選項的彙總清單螢幕擷取畫面。](media/power-bi-visualization-export-data/power-bi-export-data6.png)

1. 將篩選條件新增至 [城市]、選取所有城市，然後移除 [亞特蘭大]。

    ![已標示所清除 [喬治亞州亞特蘭大] 核取方塊的城市篩選條件螢幕擷取畫面。](media/power-bi-visualization-export-data/power-bi-filter.png)

   
1. 在階層中向下切入一個層級。 開啟切入，並向下切入至 [城市] 層級。 

    ![向下切入至城市層級視覺效果的螢幕擷取畫面。](media/power-bi-visualization-export-data/power-bi-drill.png)

現在我們已經準備好試用這兩個選項來匯出資料。

### <a name="export-_summarized__-data"></a>匯出「*_摘要_*」*_資料
如果您想要匯出在該視覺效果中所看到內容的資料，請選取此「*摘要資料*」*_的選項。  此類型匯出只會顯示用於建立視覺效果的資料 (資料行和量值)。  如果視覺效果具有彙總，則您會匯出彙總的資料。 例如，如果您有顯示四個橫條的橫條圖，就會取得四列 Excel 資料。 Power BI 服務以 *.xlsx* 和 *.csv* 提供摘要資料，Power BI Desktop 則以 .csv 提供。

1. 選取視覺效果右上角的省略符號。 選取 [匯出資料]。

    ![右上角已標示省略符號按鈕和 [匯出資料] 選項的螢幕擷取畫面。](media/power-bi-visualization-export-data/power-bi-export-data2.png)

    在 Power BI 服務中，由於視覺效果具有彙總 (您已將 [計數] 變更為 [平均])，因此您有兩個選項：

    - **摘要資料**

    - **基礎資料**

    如需了解彙總的協助，請參閱 [Power BI 中的彙總](../create-reports/service-aggregates.md)。


    > [!NOTE]
    > 在 Power BI Desktop 中，您只能將摘要資料匯出為 .csv 檔案。 
    
    
1. 從 [匯出資料] 中，選取 [摘要資料]、選擇 *.xlsx* 或 *.csv*，然後選取 [匯出]. Power BI 會匯出資料。

    ![已標示 [摘要資料]、 xlsx 和 [匯出] 選項的 [匯出資料] 螢幕擷取畫面。](media/power-bi-visualization-export-data/power-bi-export-data5.png)

1. 當您選取 [匯出] 時，瀏覽器會提示您儲存檔案。 儲存之後，請在 Excel 中開啟檔案。

    ![Excel 輸出的螢幕擷取畫面。](media/power-bi-visualization-export-data/power-bi-export-data9.png)

    在此範例中，我們的 Excel 匯出會顯示每個城市的總計。 因為我們篩選掉了亞特蘭大，所以它不包含在結果中。 試算表的第一列會顯示 Power BI 擷取資料時所使用的篩選條件。
    
    - 所有階層使用的資料都會進行匯出，而非只有視覺效果目前鑽研層級所使用的資料。 例如，我們已向下切入至城市層級，但我們的匯出也包含國家/地區資料。  

    - 我們的匯出資料會進行彙總。 針對每個城市，我們會獲得一個資料列的總計。

    - 由於我們已將篩選條件套用至視覺效果，因此匯出的資料會匯出為已篩選。 請注意，第一個資料列會顯示 **套用的篩選條件：城市不是喬治亞州亞特蘭大**。 

### <a name="export-_underlying__-data"></a>匯出「*_基礎_*」*_資料

如果您想要查看視覺效果中的資料「*_和_*」資料集中其他資料，請選取此選項 (如需詳細資料，請參閱以下圖表)。 如果您的視覺效果具有彙總，選取「*基礎資料*」*_將會移除彙總。 在此範例中，Excel 匯出會為資料集裡的每個城市資料列顯示一個資料列，以及該單一項目的折扣百分比。 Power BI 會將資料扁平化，而不會將資料彙總。  

當您選取 [匯出] 時，Power BI 會將資料匯出到 *.xlsx* 檔案，且您的瀏覽器會提示您儲存檔案。 儲存之後，請在 Excel 中開啟檔案。

1. 選取視覺效果右上角的省略符號。 選取 [匯出資料]。

    ![右上角已標示省略符號按鈕和 [匯出資料] 選項的螢幕擷取畫面。](media/power-bi-visualization-export-data/power-bi-export-data2.png)

    在 Power BI 服務中，由於視覺效果具有彙總 (您已將 [計數] 變更為 [平均])，因此您有兩個選項：

    - **摘要資料**

    - **基礎資料**

    如需了解彙總的協助，請參閱 [Power BI 中的彙總](../create-reports/service-aggregates.md)。


    > [!NOTE]
    > 在 Power BI Desktop 中，您只會有匯出摘要資料的選項。 
    
    
1. 從 [匯出資料] 選取 [基礎資料]，然後選取 [匯出]。 Power BI 會匯出資料。

    ![已呼叫出基礎資料的 [匯出資料] 螢幕擷取畫面。](media/power-bi-visualization-export-data/power-bi-underlying.png)

1. 當您選取 [匯出] 時，瀏覽器會提示您儲存檔案。 儲存之後，請在 Excel 中開啟檔案。

    ![顯示所匯出資料的 .xlsx 檔案螢幕擷取畫面。](media/power-bi-visualization-export-data/power-bi-excel.png)
    
    - 此螢幕擷取畫面只會顯示 Excel 檔案的一小部分，該 Excel 檔案具有超過 100,000 個資料列。  
    
    - 所有階層使用的資料都會進行匯出，而非只有視覺效果目前鑽研層級所使用的資料。 例如，我們已向下切入至城市層級，但我們的匯出也包含國家/地區資料。  

    - 由於我們已將篩選條件套用至視覺效果，因此匯出的資料會匯出為已篩選。 請注意，第一個資料列會顯示 **套用的篩選條件：城市不是喬治亞州亞特蘭大**。 

## <a name="customize-the-export-data-user-experience"></a>自訂匯出資料使用者體驗

除非 [資料列層級安全性 (RLS)](../admin/service-admin-rls.md) 有所限制，否則獲得報表存取權的使用者即 **獲得整個基礎資料集的存取權**。 報表作者和 Power BI 系統管理員可以使用下述功能自訂使用者體驗。

- 報表作者可以[決定使用者可使用哪些「匯出選項」](#set-the-export-options)。  

- Power BI 系統管理員可以為組織關閉部分或所有資料匯出選項。  

- 資料集擁有者可以設定資料列層級安全性 (RLS)。 RLS 會限制唯讀使用者的存取權。 但如果您已將應用程式工作區設定為讓成員具有編輯權限，則 RLS 角色不會套用至成員。 如需詳細資訊，請參閱[資料列層級安全性](../admin/service-admin-rls.md)。

- 報表作者可以隱藏資料行，使其不顯示於 [欄位] 清單中。 如需詳細資訊，請參閱[資料集屬性](../developer/automation/api-dataset-properties.md)


**這些自訂的使用者體驗，不會限制使用者在資料集中可以存取的資料。請在資料集內使用 [資料列層級安全性 (RLS)](../admin/service-admin-rls.md)，讓每個人的認證判斷可以存取的資料。**

## <a name="protect-data-when-it-is-exported-out-of-power-bi"></a>從 Power BI 匯出資料時加以保護

- 報表作者可以使用 Microsoft Azure 資訊保護[敏感度標籤](../admin/service-security-data-protection-overview.md)來分類及標示報表。 若敏感度標籤具有保護設定，當將報表資料匯出到 Excel、PowerPoint 或 PDF 檔案時，Power BI 將會套用這些保護設定。 只有授權的使用者可以開啟受保護的檔案。

- 安全性與 Power BI 系統管理員可以使用 [Microsoft Cloud App Security](../admin/service-security-data-protection-overview.md) 來監視使用者的存取和活動、執行即時的風險分析，以及設定標籤專屬的控制措施。 例如，組織可以使用 Microsoft Cloud App Security 設定原則，防止使用者將 Power BI 的敏感性資料從下載到非受控裝置。

## <a name="export-underlying-data-details"></a>匯出基礎資料詳細資料

選取 [基礎資料] 時可看到的內容會不同。 了解這些詳細資料可能需要您系統管理員或 IT 部門的協助。 


>



| 視覺效果包含 | 匯出時將看到的內容  |
|---------------- | ---------------------------|
| 彙總 | 「第一個」彙總以及該彙總之整個資料表中的非隱藏資料 |
| 彙總 | 相關資料 - 如果視覺效果使用之其他資料表中的資料與包含彙總的資料表 *有關* (只要該關聯性是 \*:1 或 1:1) |
| 量值* | 視覺效果中的所有量值，「和」包含視覺效果中所使用量值之任何資料表的所有量值 |
| 量值* | 來自資料表 (其中包含該量值) 的所有非隱藏資料 (只要該關聯性是 \*:1 或 1:1) |
| 量值* | 所有資料表中與透過 \*:1 或 1:1 鏈結包含量值的資料表相關的所有資料 |
| 僅限量值 | 所有相關資料表中的所有非隱藏資料行 (用來展開量值) |
| 僅限量值 | 針對模型量值的任何重複資料列的摘要資料 |

\* 在 Power BI Desktop 或服務的報表檢視中，「量值」會顯示在 [欄位] 清單中，且具有計算機圖示![顯示圖示](media/power-bi-visualization-export-data/power-bi-calculator-icon.png)。 量值可以在 Power BI Desktop 中建立。

### <a name="set-the-export-options"></a>設定匯出選項

Power BI 報表設計者會控制可供取用者使用的資料匯出選項類型。 這些選項包括：

- 允許終端使用者從 Power BI 服務或 Power BI 報表伺服器匯出摘要資料

- 允許終端使用者從服務或報表伺服器匯出摘要資料與基礎資料

- 不允許終端使用者從服務或報表伺服器匯出任何資料

    > [!IMPORTANT]
    > 我們建議報表設計師重新瀏覽舊報表，並視需要手動重設匯出選項。

若要設定下列選項：

1. 在 Power BI Desktop 開始。

1. 從左上角，選取 [檔案] > [選項和設定] > [選項]。

1. 在 [目前檔案] 底下，選取 [報表設定]。

    ![Desktop 報表設定](media/power-bi-visualization-export-data/desktop-report-settings.png)

1. 從 [匯出資料] 區段中選取項目。

您也可以從 Power BI 服務中更新這項設定。

請務必注意，如果 Power BI 管理入口網站設定與用於匯出資料的報表設定發生衝突，管理設定將會覆寫匯出資料設定。

## <a name="limitations-and-considerations"></a>限制與考量
這些限制和考量適用於 Power BI Desktop 和 Power BI 服務，包括 Power BI Pro 和 Premium。

- 若要從視覺效果匯出資料，您需要具有[基礎資料集的建置權限](../connect-data/service-datasets-build-permissions.md)。

-  **Power BI Desktop** 和 **Power BI 服務** 可以從 [匯入模式報表] 匯出至 *.csv* 的資料列數上限為 30,000。

- 應用程式可以從 [匯入模式報表] 匯出至 *.xlsx* 檔案的資料列數上限為 150,000。

- 若為下列情況，使用「基礎資料」匯出將無法運作：

  - 版本早於 2016 年。

  - 模型中的資料表沒有唯一索引鍵。
    
  -  管理員或報表設計者已停用這項功能。

- 如果您針對 Power BI 正要匯出的視覺效果啟用 [顯示沒有資料的項目] 選項，則使用「基礎資料」匯出將無法運作。

- 使用 DirectQuery 時，Power BI 可匯出的最大資料量為 16 MB 未壓縮資料。 非預期結果可能是所匯出資料列數小於 150,000 筆的資料列數上限。 可能原因如下：

    - 資料行過多。 請嘗試減少資料行數目，再匯出一次。

    - 有難以壓縮的資料。

    - 其他因素可能是增加檔案大小，以及減少 Power BI 可以匯出的資料列數。

- 如果視覺效果使用多個資料表中的資料，而且資料模型中的這些資料表沒有任何關聯性，則 Power BI 只會匯出第一個資料表的資料。

- 目前不支援 Power BI 視覺效果和 R 視覺效果。

- 在 Power BI 中，您可以按兩下欄位和輸入新名稱來重新命名欄位 (資料行)。 Power BI 會將新名稱稱之為「別名」。 Power BI 報表可具有重複的欄位名稱，但 Excel 不允許重複。 因此，當 Power BI 將資料匯出至 Excel 時，欄位別名會還原成原始的欄位 (資料行) 名稱。  

- 如果 *.csv* 檔案中有 Unicode 字元，Excel 中的文字可能無法正常顯示。 Unicode 的範例包括貨幣符號和外文。 您可以在 [記事本] 中開啟檔案，Unicode 即會正確顯示。 如果您想要在 Excel 中開啟檔案，因應措施是匯入 *.csv*。 若要將檔案匯入至 Exce：

  1. 開啟 Excel。

  1. 移至 [資料] 索引標籤。
  
  1. 選取 [取得外部資料] >  [從文字]。
  
  1. 移至儲存檔案的本機資料夾，然後選取 *.csv*。

- 匯出為 .csv 時，某些字元會在開頭加入 **'** 進行逸出，以避免在 Excel 中開啟時作為指令碼執行。 發生這種情況的時機：
  - 資料欄在資料模型中定義為「文字」類型，**和**
  - 文字的第一個字元是下列其中一個符號： **=、@、+、-**

- Power BI 系統管理員可以停用匯出資料。

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)