---
title: Power BI 分頁報表中的子報表
description: 在本文中，您會了解 Power BI 服務中編頁報表支援的資料來源。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
ms.date: 04/29/2020
ms.openlocfilehash: d2cd4e9f5d6cb8872e266fabacb9f8a5a3e318cb
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/04/2020
ms.locfileid: "93298008"
---
# <a name="subreports-in-power-bi-paginated-reports"></a>Power BI 分頁報表中的子報表

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

「子報表」  是分頁報表項目，其會在主要分頁報表的主體內顯示另一份分頁報表。 報表中子報表的概念類似於網頁中的框架。 用於在報表中內嵌報表。 任何報表皆可作為子報表使用。 您要將顯示為子報表的報表，儲存在與父報表相同的 Premium 工作區中。 您可以設計父報表來傳遞參數給子報表。 子報表可使用參數來篩選每一個子報表執行個體中的資料，以在資料區域內重複。  
  
 ![分頁報表中的子報表](media/subreports/paginated-report-subreport.png "分頁報表子報表")  
  
 在此圖中，[銷售訂單] 主報表中顯示的連絡資訊實際上來自 [連絡人] 子報表。  
  
您可在 Power BI Report Builder 中建立及修改分頁報表定義 (.rdl) 檔。 您可將儲存在 SQL Server Reporting Services 中子報表上傳至 Power BI 服務的 Premium 工作區。 主要報表和子報表必須發佈至同一工作區。 安裝 [Power BI Report Builder](https://aka.ms/pbireportbuilder)。
  
## <a name="work-with-report-builder-and-the-power-bi-service"></a>使用 Report Builder 和 Power BI 服務

Power BI Report Builder 可處理電腦上的分頁報表 (也稱為本機報表)，也可處理 Power BI 服務中的報表。  當第一次開啟 Report Builder 時，系統會要求登入您的 Power BI 帳戶。 否則，請選取右上角的 [登入]  。

:::image type="content" source="media/subreports/report-builder-sign-in.png" alt-text="登入 Power BI":::

登入之後，即會在 Power BI Report Builder 的 [Power BI 服務]  選項中，看到 [檔案]  功能表的 [開啟]  和 [另存新檔]  選項。 當選取 [Power BI 服務]  選項儲存報表時，即會建立 Power BI Report Builder 和 Power BI 服務之間的即時連線。 

:::image type="content" source="media/subreports/report-builder-subreport-open-service.png" alt-text="從 Power BI 服務開啟":::

## <a name="save-a-local-report-to-the-power-bi-service"></a>將本機報表儲存至 Power BI 服務

您必須先建立子報表和主報表這兩份報表，並將其儲存到相同的 Power BI Premium 工作區，才可將子報表新增至主報表。 

1. 若要開啟現有的本機報表，請在 [檔案]  功能表上，選取 [開啟]   > [此電腦]  ，然後選取一個 .rdl 檔案。  

2. 在 [檔案]  功能表上，選取 [另存新檔]   > [Power BI 服務]  。  如需詳細資訊，請參閱[將分頁報表發佈至 Power BI 服務](paginated-reports-save-to-power-bi-service.md)。

    > [!NOTE]
    > 您也可從 Power BI 服務中開始上傳報表。 詳細資料另請參閱[將分頁報表發佈至 Power BI 服務](paginated-reports-save-to-power-bi-service.md)一文。

3. 在 [另存新檔]  對話方塊中，選取可儲存分頁報表的 Power BI Premium 工作區。  Premium 工作區在名稱旁邊有一個鑽石圖示 ![Premium 鑽石圖示](media/subreports/report-builder-premium-diamond.png)。

    :::image type="content" source="media/subreports/report-builder-subreport-save-as-service.png" alt-text="另存新檔至 Power BI 服務":::

4. 選取 [儲存]  。

## <a name="add-a-subreport-to-a-report"></a>將子報表新增至報表

將這兩份報表儲存到相同的 Premium 工作區後，即可將其中一份新增到另一份作為子報表。 有兩種方式可以新增子報表。 

1. 在 [插入]  功能區中，選取 [子報表]  按鈕，或以滑鼠右鍵按一下報表畫布，然後選取 [插入]   > [子報表]  。

    :::image type="content" source="media/subreports/report-builder-insert-subreport.png" alt-text="在報表中插入子報表":::

    [子報表屬性]  對話方塊隨即開啟。  

2. 選取 [瀏覽]  按鈕 > 巡覽至要當作子報表使用的報表 > 在 [名稱]  文字方塊中指定子報表的名稱。

3. 視需要設定其他屬性，包括[參數](#use-parameters-in-subreports)。

## <a name="use-parameters-in-subreports"></a>在子報表中使用參數  
 若要從父報表傳遞參數至子報表，請在做為子報表使用的報表中定義一個報表參數。 當您在父報表中放置子報表時，您可以選取報表參數，以及要從父報表中傳遞給子報表中之報表參數的值。  
  
> [!NOTE]  
> 您從子報表中選取的參數是「報表」  參數，而不是「查詢」  參數。  
  
 子報表可放在報表主體或資料區域中。 如果將子報表放在資料區域中，子報表就會在資料區域中重複群組或資料列的每一個執行個體。 您可將群組或資料列中的值傳遞至子報表。 在子報表值屬性中，對包含要傳遞給子報表參數的值欄位使用欄位運算式。  
  
 如需使用參數和子報表的詳細資訊，請參閱 SQL Server Reporting Services 文件的[新增子報表和參數](/sql/reporting-services/report-design/add-a-subreport-and-parameters-report-builder-and-ssrs)。  

## <a name="preview-paginated-reports-in-report-builder"></a>在 Report Builder 中預覽分頁報表

您可在 Report Builder 中預覽報表。

- 從 [常用]  功能區中選取 [執行]  。 

因為 Report Builder 是設計工具，所以預覽的報表和使用 Power BI 服務所轉譯報表看起來可能有所不同。

### <a name="notes-about-previewing"></a>預覽注意事項

- Report Builder 不會儲存報表所用資料來源的認證。  Report Builder 會在預覽期間要求提供每一組認證。  
- 如果報表資料來源為內部部署，則必須在將報表儲存至 Power BI 工作區後設定閘道。
- 如果 Report Builder 在預覽期間發生錯誤，則其會傳回一般訊息。  如果錯誤難以偵錯，請考慮使用 Power BI 服務來轉譯報表。  

## <a name="considerations"></a>考量

### <a name="maintaining-the-connection"></a>維持連線

當關閉檔案後，Report Builder 不會保持與 Power BI 的連線。  您可使用本機主報表搭配儲存在 Power BI 工作區中的子報表。 請務必先將主報表儲存至 Power BI 工作區，再關閉報表。  否則，您會在預覽期間接獲「找不到」訊息，因為沒有 Power BI 服務的即時連線。  如果發生這種情況，請移至子報表並選取其 [屬性]。  再次從 Power BI 服務中開啟子報表。  這會重新建立連線，但所有其他子報表應該都沒問題。

### <a name="renaming-a-subreport"></a>重新命名子報表

如要重新命名工作區中的子報表，則必須修正主報表中的名稱參考。 否則，將不會轉譯子報表。 主報表仍會轉譯，但子報表項目會有錯誤訊息。

## <a name="migrate-large-reports"></a>移轉大型報表

如要將大型報表移轉至 Power BI，請考慮使用 [RdlMigration 工具](../guidance/migrate-ssrs-reports-to-power-bi.md)。  RdlMigration 工具已更新，可處理重複的子報表名稱。  當兩個或多個報表共用同一名稱，但位於不同子目錄時，就會發生重複的子報表名稱。  如果這些名稱不是唯一的，則僅辨識第一份子報表。

如果您想要使用 Report Builder 來移轉大型報表，則建議先處理子報表。 將每一個報表儲存到 Power BI 工作區，可避免任何重複的報表名稱。

## <a name="share-reports-with-subreports"></a>與子報表共用報表

如前所述，主要報表和子報表必須位於相同的工作區中。 否則，將不會轉譯子報表。 共用主報表時，您也需要共用子報表。 如果您在應用程式中共用主報表，請務必也將子報表包含在該應用程式中。 如果直接與使用者或使用者群組共用主報表，請務必也和相同的一組使用者或使用者群組共用每個子報表。
  
## <a name="next-steps"></a>後續步驟

[針對 Power BI 分頁報表中的子報表進行疑難排解](subreports-troubleshoot.md)

[檢視 Power BI 服務中的編頁報表](../consumer/paginated-reports-view-power-bi-service.md)

有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)