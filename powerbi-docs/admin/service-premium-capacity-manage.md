---
title: 管理 Microsoft Power BI Premium 容量
description: 說明 Power BI Premium 容量的管理工作。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: conceptual
ms.date: 11/11/2020
ms.custom: ''
LocalizationGroup: Premium
ms.openlocfilehash: ced239ba0ac8f34314caf559a04126bf64ca7c50
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96412337"
---
# <a name="managing-premium-capacities"></a>管理 Premium 容量

管理 Power BI Premium 牽涉到建立、管理和監視 Premium 容量。 本文提供容量的概觀；如需逐步指示，請參閱[設定和管理容量](service-admin-premium-manage.md)。

## <a name="creating-and-managing-capacities"></a>建立和管理容量

Power BI 管理入口網站的 [容量設定] 頁面會顯示已購買的 V 核心數目和可用的 Premium 容量。 此頁面可供全域管理員或 Power BI 服務管理員從可用的 V 核心建立 Premium 容量，或修改現有的 Premium 容量。

> [!NOTE]
> Power BI Premium 最近已發行名叫 **Premium Gen2** 的新版本 Premium，其目前處於預覽狀態。 Premium Gen2 將能簡化 Premium 容量的管理，並減少管理負擔。 如需詳細資訊，請參閱 [Power BI Premium 第 2 代 (預覽)](service-premium-what-is.md#power-bi-premium-generation-2-preview)。

建立 Premium 容量時，系統管理員必須定義：

- 容量名稱 (在租用戶內是唯一的)。
- 容量管理員。
- 容量大小。
- 資料落地的區域。

必須至少指派一個容量管理員。 指派為容量管理員的使用者可以：

- 將工作區指派給容量。
- 管理使用者權限，以新增額外的容量管理員或具有指派權限的使用者 (讓他們可以將工作區指派給容量)。
- 管理工作負載，以設定編頁報表和資料流程工作負載的記憶體使用量上限。
- 重新啟動容量，因為系統超載而重設所有作業。

除非在工作區權限中明確指派，否則容量管理員無法存取工作區內容。 他們也無法存取所有的 Power BI 管理區域 (除非已明確指派)，例如使用計量、稽核記錄檔或租用戶設定。 重要的是，容量管理員沒有建立新容量或調整現有容量大小的權限。 管理員是按每個容量來指派，確保他們只能檢視和管理指派給他們的容量。

容量大小選取自可用的 SKU 選項清單，其受限於集區中可用的 V 核心數目。 您可以從集區建立多個容量，這可能來自一或多個已購買的 SKU。 例如，P3 SKU (32 個 V 核心) 可用來建立三個容量：一個 P2 (16 個 V 核心) 和兩個 P1 (2 x 8 個 V 核心)。 如[最佳化 Premium 容量](service-premium-capacity-optimize.md)一文所述，藉由建立較小的容量，可以達到更佳的效能和規模。 下圖顯示虛構組織 Contoso 的範例設定，其中包含五個 Premium 容量 (3 個 P1 及 2 個 P3，每個內含多個工作區)，以及共用容量中的數個工作區。

![虛構組織 Contoso 的範例設定](media/service-premium-capacity-manage/contoso-organization-example.png)

Premium 容量可以指派給 Power BI 租用戶主要區域以外的區域，稱為多地理位置。 多地理位置可讓您控制已定義地理區域中 Power BI 內容所在的資料中心。 進行多地理位置部署的原因通常是為了公司或政府的合規性，而不是效能和規模。 報表與儀表板載入等動作，仍然牽涉到向主要區域要求中繼資料。 若要深入了解，請參閱 [Power BI Premium 的多地理位置支援](service-admin-premium-multi-geo.md)。

Power BI 服務管理員和全域管理員可修改 Premium 容量。 具體來說，他們可以：

- 將容量大小變更為相應增加或相應減少資源。
- 新增或移除容量管理員。
- 新增或移除具有指派權限的使用者。
- 新增或移除額外的工作負載。
- 變更區域。

需要有指派權限，才能將工作區指派給特定的 Premium 容量。 權限可以授與給整個組織、特定使用者或群組。

根據預設，Premium 容量支援與執行中 Power BI 查詢相關聯的工作負載。 Premium 容量也支援額外的工作負載：**AI (認知服務)** 、**編頁報表** 及 **資料流程**。 每個工作負載都需要設定工作負載所能使用的最大記憶體 (以總可用記憶體百分比表示)。 請務必了解，增加的最大記憶體配置可能會影響可以裝載的作用中模型數目，以及重新整理的輸送量。 

記憶體會以動態方式配置給資料流程，但會以靜態方式配置給編頁報表。 以靜態方式配置最大記憶體的原因是，編頁報表是在容量的安全容納空間內執行。 設定編頁報表記憶體時應特別小心，因為它會減少用於載入模型的可用記憶體。 若要深入了解，請參閱[預設記憶體設定](service-admin-premium-workloads.md#default-memory-settings)。

您可以刪除 Premium 容量，而不會導致刪除其工作區和內容。 相反地，它會將任何指派的工作區移至共用容量。 在不同區域中建立 Premium 容量時，工作區會移至主要區域的共用容量。

### <a name="assigning-workspaces-to-capacities"></a>將工作區指派給容量

您可以在 Power BI 管理入口網站中將工作區指派給 Premium 容量，或針對工作區，在 [工作區] 窗格中進行指派。

容量管理員以及全域管理員或 Power BI 服務管理員都可在 Power BI 管理入口網站中大量指派工作區。 大量指派可套用至：

- **依使用者選取工作區** - 這些使用者擁有的所有工作區 (包括個人工作區) 都會指派給 Premium 容量。 當工作區已指派給不同的 Premium 容量時，這會包含工作區的重新指派。 此外，也會將工作區指派權限指派給使用者。

- **特定工作區**
- **整個組織的工作區** - 所有工作區 (包括個人工作區) 都會指派給 Premium 容量。 所有目前和未來的使用者都會獲指派工作區指派權限。 不建議使用此方法。 慣用方法是更具針對性的方法。

如果使用者是工作區管理員又具有指派許可權，就可以使用 [工作區] 窗格，將工作區新增至 Premium 容量。

![使用 [工作區] 窗格將工作區指派給 Premium 容量](media/service-premium-capacity-manage/assign-workspace-capacity.png)

工作區管理員可以從容量中移除工作區 (到共用容量)，而不需要指派權限。 從專用容量中移除工作區，可有效地將工作區重新放置到共用容量。 請注意，從 Premium 容量中移除工作區可能會產生負面結果，例如，共用內容變成無法供 Power BI 免費授權使用者使用，或已排程的重新整理在超過共用容量支援的額度時暫停。

在 Power BI 服務中，可透過裝飾工作區名稱的菱形圖示，輕鬆地識別指派給 Premium 容量的工作區。

![識別指派給 Premium 容量的工作區](media/service-premium-capacity-manage/premium-diamond-icon.png)

## <a name="monitoring-capacities"></a>監視容量

監視 Premium 容量可讓系統管理員了解如何執行容量。 您可以使用 Power BI 管理入口網站或 **Power BI Premium 容量計量** (Power BI) 應用程式監視容量。

### <a name="power-bi-admin-portal"></a>Power BI 管理入口網站

在管理入口網站中，針對每個容量，[健康情況] 索引標籤會提供容量和每個已啟用工作負載的摘要計量。 計量顯示過去七天的平均值。  

在容量層級上，計量是所有已啟用工作負載的累計。 提供下列計量：

- **CPU 使用率** - 提供平均 CPU 使用率，以容量的總可用 CPU 百分比表示。  
- **記憶體使用量** - 提供平均記憶體使用量 (以 GB 為單位)，以容量的可用記憶體總計表示。 

針對每個已啟用的工作負載，會提供 CPU 使用率和記憶體使用量，以及一些工作負載特定計量。 例如，針對資料流程工作負載，[總計數] 會顯示每個資料流程的重新整理總數，而 [平均持續時間] 則會顯示資料流程重新整理的平均持續時間。

![入口網站中的 [容量健康情況] 索引標籤](media/service-premium-capacity-manage/admin-portal-health-dataflows.png)

若要深入了解每個工作負載的所有可用計量，請參閱[在管理入口網站中監視容量](service-admin-premium-monitor-portal.md)。

Power BI 管理入口網站中的監視功能用來提供主要容量計量的快速摘要。 為了更詳細地監視，建議您使用 **Power BI Premium 容量計量** 應用程式。

### <a name="power-bi-premium-capacity-metrics-app"></a>Power BI Premium 容量計量應用程式

[Power BI Premium 容量計量應用程式](https://appsource.microsoft.com/en-us/product/power-bi/pbi_pcmm.capacity-metrics-dxt?tab=Overview)是可供容量管理員使用的 Power BI 應用程式，安裝方式就像其他 Power BI 應用程式一樣。 其中包含儀表板和報表。

![Power BI Premium 容量計量應用程式](media/service-premium-capacity-manage/capacity-metrics-app.png)

當應用程式開啟時，會載入儀表板以顯示許多磚，這些磚代表使用者為容量管理員之所有容量的彙總檢視。儀表板版面配置包含五個主要區段：

- **概觀** - 應用程式版本、容量和工作區數目
- **系統摘要** - 記憶體和 CPU 等計量
- **資料集摘要** - 資料集、DQ/LC、重新整理及查詢數目等計量
- **資料流程摘要** - 資料流程數目和資料集等計量
- **編頁報表摘要** - 重新整理和檢視等計量

已從中釘選儀表板磚的基礎報表，可以按一下任一儀表板磚進行存取。 它會針對每個儀表板區段提供更詳細的觀點，並支援互動式篩選。 

透過依日期範圍、容量、工作區和工作負載 (報表、資料集、資料流程) 設定交叉分析篩選器，以及選取報表視覺效果中的項目交叉篩選報表頁面，即可達成篩選。 交叉篩選是一種強大的技術，可以將範圍縮小到特定的時段、容量、工作區、資料集等，而且在執行根本原因分析時非常有用。

如需應用程式中儀表板和報表計量的詳細資訊，請參閱[使用應用程式監視 Premium 容量](service-admin-premium-monitor-capacity.md)。

### <a name="interpreting-metrics"></a>解譯計量

應該要監視計量，才能基本了解資源使用量和工作負載活動。 如果容量變慢，請務必了解要監視哪些計量，以及您可得出的結論。

在理想的情況下，查詢應該在一秒內完成，以提供回應式體驗給報表使用者，並啟用更高的查詢輸送量。 當背景處理程序 (包括重新整理) 需要較長的時間才能完成時，通常比較不重要。

一般來說，緩慢的報告可能表示容量過熱。 當報表無法載入時，這表示容量過熱。 在這兩種情況下，根本原因可能是由許多因素所造成，包括：

- **失敗的查詢** 清楚顯示出記憶體壓力，而且無法將模型載入記憶體中。 Power BI 服務會嘗試在失敗前載入模型 30 秒。

- **過多的查詢等候時間** 可能是由於數個原因所造成：
  - Power BI 服務需要先收回模型，再載入待查詢的模型 (請記得較高的資料集收回率本身並不表示容量壓力，除非伴隨著指出記憶體過度置換的長時間查詢等候時間)。
  - 模型載入時間 (尤其是等待將大型模型載入記憶體中)。
  - 長時間執行的查詢。
  - 太多 LC\DQ 連線 (超過容量限制)。
  - CPU 飽和度。
  - 頁面上具有過多視覺效果的複雜報表設計 (請記得每個視覺效果都是一個查詢)。

- **查詢時間長** 可能表示模型設計並未最佳化，特別是當多個資料集在容量中為使用中，而只有一個資料集的查詢時間長時。 這表明容量有足夠的資源，而所討論的資料集處於次佳狀況，或者只是緩慢。 長時間執行的查詢可能會造成問題，因為它們會阻礙其他處理程序對所需資源的存取。
- **長時間重新整理等候時間** 指出由於有許多耗用記憶體的使用中模型而導致記憶體不足，或是有問題的重新整理封鎖了其他重新整理 (超過平行重新整理限制)。

[最佳化 Premium 容量](service-premium-capacity-optimize.md)一文涵蓋如何使用計量的詳細說明。

## <a name="acknowledgments"></a>通知

本文是由資料平台 MVP 暨 [Bitwise Solutions](https://www.bitwisesolutions.com.au/) 的獨立 BI 專家 Peter Myers 所撰寫。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [最佳化 Premium 容量](service-premium-capacity-optimize.md)   
> [!div class="nextstepaction"]
> [設定 Premium 容量中的工作負載](service-admin-premium-workloads.md)   

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)

Power BI 已推出 Power BI Premium Gen2 作為預覽供應項目，其能透過對下列領域的改進來改善 Power BI Premium 體驗：
* 效能
* 個別使用者授權
* 範圍更大的擴縮
* 改善的計量
* 自動調整
* 降低管理負擔

如需 Power BI Premium Gen2 的詳細資訊，請參閱 [Power BI Premium 第 2 代 (預覽)](service-premium-what-is.md#power-bi-premium-generation-2-preview)。
