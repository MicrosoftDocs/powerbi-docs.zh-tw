---
title: Power BI Premium 中的大型模型 (預覽)
description: 「大型模型」功能可讓 Power BI Premium 中的資料集成長到超過 10 GB 的大小。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: how-to
ms.date: 11/11/2020
LocalizationGroup: Premium
ms.openlocfilehash: 0bb6f7bf46875e0af7c09d221c73ae5e4b70b2df
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96412222"
---
# <a name="large-models-in-power-bi-premium-preview"></a>Power BI Premium 中的大型模型 (預覽)

Power BI 資料集可以將資料儲存在高度壓縮的記憶體內部快取中，以獲得最佳化的查詢效能，讓使用者能夠在大型資料集上快速互動。 「大型模型」功能可讓 Power BI Premium 中的資料集成長到超過 10 GB 的大小。 資料集的大小會改為受到 Power BI Premium 容量大小限制，這類似於 Azure Analysis Services 在模型大小限制方面的運作方式。 如需 Power BI Premium 中容量大小的詳細資訊，請參閱容量節點。 您可以為所有 Premium P SKU 和 Embedded A SKU 設定大型模型，但它們僅適用於[新的工作區](../collaborate-share/service-create-the-new-workspaces.md)。

大型模型不會影響 .PBIX 上傳大小 (限制為 10 GB)， 反而是在重新整理時，服務的資料集會成長到超過 10 GB。 您可以使用累加式重新整理來設定資料集，使其成長至超過 10 GB。

## <a name="enable-large-models"></a>啟用大型模型

若要建立可成長超過 10 GB 的資料集，請遵循下列步驟：

1. 在 Power BI Desktop 中建立資料集，並設定[累加式重新整理](service-premium-incremental-refresh.md)。

1. 將資料集發佈至 Power BI Premium 服務。

1. 藉由執行下列 PowerShell Cmdlet，啟用大型模型的資料集。 這些 Cmdlet 會讓 Power BI 將資料集儲存在 Azure Premium 檔案上，而不會強制執行 10 GB 的限制。

1. 根據累加式重新整理原則，叫用重新整理來載入歷程記錄資料。 第一次重新整理可能需要一段時間來載入歷程記錄。 後續重新整理可能較快，因為是累加式。

### <a name="powershell-cmdlets"></a>PowerShell Cmdlet

在目前版本的大型模型中，使用 PowerShell Cmdlet 來啟用 Premium 檔案儲存體的資料集。 您必須擁有容量管理員和工作區管理員的權限，才能執行 PowerShell Cmdlet。

1. 尋找資料集識別碼 (GUID)。 在工作區的 [資料集]  索引標籤的 資料集設定下，可以在 URL 中看到識別碼。

    ![資料集 GUID](media/service-premium-large-models/dataset-guid.png)

1. 在 PowerShell 管理提示中安裝 [MicrosoftPowerBIMgmt](/powershell/module/microsoftpowerbimgmt.data/) 模組。

    ```powershell
    Install-Module -Name MicrosoftPowerBIMgmt
    ```

1. 執行下列 Cmdlet 來登入及檢查資料集儲存模式。

    ```powershell
    Login-PowerBIServiceAccount

    (Get-PowerBIDataset -Scope Organization -Id <Dataset ID> -Include actualStorage).ActualStorage
    ```

    回應應該如下。 儲存模式是 ABF (Analysis Services 備份檔案)，這是預設值。

    ```
    Id                   StorageMode

    --                   -----------

    <Dataset ID>         Abf
    ```

1. 執行下列 Cmdlet 來將儲存模式設定為 Premium 檔案並檢查。 轉換成 Premium 檔案可能需要幾秒鐘的時間。

    ```powershell
    Set-PowerBIDataset -Id <Dataset ID> -TargetStorageMode PremiumFiles

    (Get-PowerBIDataset -Scope Organization -Id <Dataset ID> -Include actualStorage).ActualStorage
    ```

    回應應該如下。 儲存模式現在已設定為 Premium 檔案。

    ```
    Id                   StorageMode
    
    --                   -----------
    
    <Dataset ID>         PremiumFiles
    ```

您可以使用 [Get-PowerBIWorkspaceMigrationStatus](/powershell/module/microsoftpowerbimgmt.workspaces/get-powerbiworkspacemigrationstatus) Cmdlet 來檢查資料集與 Premium 檔案之間轉換的狀態。

## <a name="dataset-eviction"></a>資料集收回

Power BI 使用動態記憶體管理，從記憶體收回非使用中的資料集。 Power BI 收回資料集，讓它可以載入其他資料集來處理使用者查詢。 動態記憶體管理可讓資料集大小的總和明顯大於容量上可用的記憶體，但是單一資料集必須能放入記憶體中。 如需動態記憶體管理的詳細資訊，請參閱[容量的運作方式](service-premium-what-is.md#how-capacities-function)。

您應該考慮收回對大型模型的影響。 雖然資料集載入時間相當快速，但如果必須等候大量收回的資料集重載，可能還是會有明顯的延遲。 基於這個理由，以大型模型功能目前的形式來說，建議主要用於企業 BI 需求專用的容量，而不是混合了自助 BI 需求的容量。 企業 BI 需求專用的容量比較不會經常觸發收回而需要重載資料集。 另一方面，自助 BI 的容量可能會有許多較常載入和進出記憶體的小型資料集。

## <a name="checking-dataset-size"></a>查看資料集大小

載入歷程記錄資料之後，您可以使用 [SSMS](/sql/ssms/download-sql-server-management-studio-ssms) 透過 [XMLA 端點](service-premium-connect-tools.md)，在模型屬性視窗中查看估計的資料集大小。

![估計的資料集大小](media/service-premium-large-models/estimated-dataset-size.png)

您也可以從 SSMS 執行下列 DMV 查詢，以查看資料集大小。 加總輸出中的 DICTIONARY\_SIZE 和 USED\_SIZE 資料行，查看資料集的位元組大小。

```sql
SELECT * FROM SYSTEMRESTRICTSCHEMA
($System.DISCOVER_STORAGE_TABLE_COLUMNS,
 [DATABASE_NAME] = '<Dataset Name>') //Sum DICTIONARY_SIZE (bytes)

SELECT * FROM SYSTEMRESTRICTSCHEMA
($System.DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS,
 [DATABASE_NAME] = '<Dataset Name>') //Sum USED_SIZE (bytes)
```

## <a name="limitations-and-considerations"></a>限制與考量

使用大型模型時，請記住下列限制：

- **多地理位置支援**：啟用 Premium 檔案的資料集，在也啟用了 [多地理位置](service-admin-premium-multi-geo.md)的容量上會失敗。

- **下載至 Power BI Desktop**：如果資料集儲存在 Premium 檔案上，[下載為 .pbix](../create-reports/service-export-to-pbix.md) 檔案將會失敗。
- **支援的區域**：大型模型在支援進階檔案儲存體的所有 Azure 區域中受到支援。 若要深入了解，請參閱[依區域提供的產品](https://azure.microsoft.com/global-infrastructure/services/?products=storage)，並參閱下一節中的表格。


## <a name="availability-in-regions"></a>區域中的可用性

Power BI 中的大型模型僅適用於支援 [Azure Premium 檔案儲存體](/azure/storage/files/storage-files-planning#storage-tiers) \(部分機器翻譯\) 的特定 Azure 區域。

下列清單提供可以在 Power BI 中使用大型模型的區域。 大型模型不支援下列清單中的區域：


|Azure 區域  |Azure 區域縮寫  |
|---------|---------|
|澳大利亞東部     | australiaeast        |
|澳大利亞東南部     | australiasoutheast        |
|美國中部     | centralus        |
|東亞     | eastasia        |
|美國東部     | eastus        |
|美國東部 2     | eastus2        |
|日本東部     | japaneast        |
|日本西部     | japanwest        |
|南韓中部     | koreacentral        |
|南韓南部     | koreasouth        |
|美國中北部     | northcentralus        |
|北歐     | northeurope        |
|美國中南部     | southcentralus        |
|東南亞     | southeastasia        |
|英國南部     | uksouth        |
|英國西部     | ukwest        |
|西歐     | westeurope        |
|美國西部     | westus        |
|美國西部 2     | westus2        |



## <a name="next-steps"></a>後續步驟

下列連結提供的資訊有助於處理大型模型：

* [Azure Premium 檔案儲存體](/azure/storage/files/storage-files-planning#storage-tiers) \(部分機器翻譯\)
* [設定 Power BI Premium 的多地理位置支援](service-admin-premium-multi-geo.md)
* [攜帶您自己的加密金鑰以用於 Power BI](service-encryption-byok.md)
* [容量的運作方式](service-premium-what-is.md#how-capacities-function)
* [累加式重新整理](service-premium-incremental-refresh.md)。


Power BI 已推出 Power BI Premium Gen2 作為預覽供應項目，其能透過對下列領域的改進來改善 Power BI Premium 體驗：
* 效能
* 個別使用者授權
* 範圍更大的擴縮
* 改善的計量
* 自動調整
* 降低管理負擔

如需 Power BI Premium Gen2 的詳細資訊，請參閱 [Power BI Premium 第 2 代 (預覽)](service-premium-what-is.md#power-bi-premium-generation-2-preview)。