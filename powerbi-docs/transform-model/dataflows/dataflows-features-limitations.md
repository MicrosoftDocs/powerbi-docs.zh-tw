---
title: 資料流程限制，以及支援的連接器和功能
description: 資料流程的所有功能概觀
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-dataflows
ms.topic: how-to
ms.date: 10/01/2020
LocalizationGroup: Data from files
ms.openlocfilehash: 762a45dc48bd78ffebcbe68ef2f5ed216ec3cc51
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96416086"
---
# <a name="dataflows-limitations-and-considerations"></a>資料流程限制與考量

在撰寫、重新整理和進行容量管理時，使用者需牢記幾個資料流程限制，如下列各節中所述。

## <a name="dataflow-authoring"></a>資料流程撰寫

撰寫資料流程時，使用者應注意下列考量事項：

* 撰寫資料流程是在 Power Query Online (PQO) 環境中執行的；請參閱 [Power Query 限制](/power-query/power-query-online-limits)中描述的限制。
由於資料流程撰寫是在 Power Query Online (PQO) 環境中執行的，因此對資料流程工作負載設定執行的更新只會影響重新整理，而不會影響撰寫體驗

* 資料流程只能由其擁有者修改

* 資料流程無法在 [我的工作區] 中使用

* 使用閘道資料來源的資料流程不支援針對相同資料來源使用多個認證

* 使用 Web.Page 連接器需要閘道

## <a name="api-considerations"></a>API 考量

您可在 [REST API 參考](/rest/api/power-bi/dataflows) (英文) 中找到支援資料流程 REST API 的詳細資訊。 以下是一些要記住的考量：

* 匯出和匯入資料流程會提供該資料流程新的識別碼

* 匯入包含連結實體的資料流程不會修正資料流程內現有參考 (這些查詢應在匯入資料流程前手動修正)

* 若資料流程最初是使用匯入 API 建立的，則可使用 *CreateOrOverwrite* 參數來覆寫資料流程

## <a name="dataflows-in-shared"></a>共用中的資料流程

共用容量中的資料流程具有一些限制：

* 重新整理資料流程時，共用中的逾時為每個實體 2 小時，每個資料流程 3 小時
* 無法在共用資料流程中建立連結的實體，雖然只要在查詢上停用 [啟用載入] 屬性，連結的實體即可存在於資料流程中
* 無法在共用資料流程中建立計算實體
* AutoML 和認知服務無法在共用資料流程中使用
* 累加式重新整理無法在共用資料流程中使用

## <a name="dataflows-in-premium"></a>Premium 中的資料流程

存在於 Premium 中的資料流程包含下列限制及考量。

**重新整理和資料考量：**

* 重新整理資料流程時，逾時為 24 小時 (不區分實體和/或資料流程)

* 將資料流程從累加式重新整理原則變更為一般重新整理時，將會卸除所有資料，反之亦然

* 修改資料流程的結構描述會卸除所有資料

**連結和計算實體：**

* 連結實體最多可以向下到 32 的參考深度

* 不允許連結實體循環相依性

* 連結的實體無法與資料取自內部部署資料來源的一般實體相連

* 在資料流程中使用查詢 (例如：查詢「A」) 來計算另一個查詢 (查詢「B」) 時，查詢「B」會成為計算實體。 計算的實體不能參考內部部署來源。


**計算引擎：**

* 使用計算引擎時，資料擷取的時間會增加約 10% 到 20%。

  1. 這僅適用於計算引擎上的第一個資料流程，以及從資料來源讀取資料
  2. 使用來源一的後續資料流程不會產生相同損失

* 只有特定作業會使用計算引擎，且只有在透過連結的實體使用或作為計算實體使用時才會使用計算引擎。 您可在[此部落格文章](http://petcu40.blogspot.com/2019/06/m-folding-in-enhanced-engine-of-power.html)中取得可用作業的完整清單。


**容量管理：**

* 根據設計，Premium Power BI 容量具備內部資源管理員，該資源管理員會在容量記憶體過低時，透過不同方式進行節流。

  1. 針對資料流程，節流壓力會減少可用的 M 容器數
  2. 資料流程的記憶體可設為 100%，並具備對資料大小而言大小適當的容器，工作負載即會適當地管理容器數

* 您可透過將配置到工作負載其總記憶體量除以配置到容器的記憶體量，以取得適當的容器數目

## <a name="dataflow-usage-in-datasets"></a>資料集中的資料流程使用方式

* 在 Power BI Desktop 中建立資料集，然後將其發佈到 Power BI 服務時，請確保在 Power BI Desktop 中針對資料流程資料來源使用的認證與將資料集發佈到服務時所使用認證相同。
  1. 若無法確保這些認證相同，便會在資料集重新整理時產生「找不到金鑰」錯誤

## <a name="next-steps"></a>後續步驟
下列文章提供資料流程和 Power BI 的詳細資訊：

* [資料流程和自助資料準備簡介](dataflows-introduction-self-service.md)
* [建立資料流程](dataflows-create.md)
* [設定及取用資料流程](dataflows-configure-consume.md)
* [將資料流程儲存體設定為使用 Azure Data Lake Gen 2](dataflows-azure-data-lake-storage-integration.md)
* [資料流程的進階功能](dataflows-premium-features.md)
* [使用資料流程的 AI](dataflows-machine-learning-integration.md)
* [資料流程最佳做法](dataflows-best-practices.md)