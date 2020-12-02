---
title: 在 Power BI Desktop 中連線到 Power Platform 資料流程所建立的資料
description: 輕鬆連線並使用 Power BI Desktop 中的資料流程
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-dataflows
ms.topic: how-to
ms.date: 10/01/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 5d9f477c8b058dbe9a71eec1307b4a32863307a1
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96392948"
---
# <a name="connect-to-data-created-by-power-platform-dataflows-in-power-bi-desktop"></a>在 Power BI Desktop 中連線到 Power Platform 資料流程所建立的資料
在 **Power BI Desktop** 中，您可以連線至 **Power Platform 資料流程** 建立的資料，就像連線到 Power BI Desktop 中的任何其他資料來源一樣。

![連線到資料流程](media/desktop-connect-dataflows/connect-dataflows_01.png)

**Power Platform 資料流程** 連接器可讓您在 Power BI 服務中連線到資料流程所建立的實體。 

## <a name="considerations-and-limitations"></a>考量與限制

若要使用 **Power Platform 資料流程連接器**，您必須執行最新版的 **Power BI Desktop**。 您可以隨時[下載 Power BI Desktop](../fundamentals/desktop-get-the-desktop.md) 將它安裝在您的電腦上，以確保您擁有最新的版本。  

> [!NOTE]
> 舊版的 Power Platform 資料流程連接器會要求您下載 .MEZ 檔案，並將其放在資料夾中。 目前的 **Power BI Desktop** 版本隨附 Power Platform 資料流程連接器，因此該檔案不再是必要檔案，而可能導致與隨附的連接器版本產生衝突。 如果您以手動方式該 .MEZ 檔案放到資料夾中，就「必須」從 [文件] > [Power BI Desktop] > [自訂連接器] 資料夾中刪除已下載的 .MEZ 檔案，以避免產生衝突。 

## <a name="desktop-performance"></a>Desktop 效能
**Power BI Desktop** 會在其安裝所在的電腦上本機執行。 資料流程的擷取效能取決於各種因素。 這些因素包括資料的大小、您電腦的 CPU 和 RAM、網路頻寬、與資料中心的距離，以及其他因素。

您可以改善資料流程的資料擷取效能。 例如，如果針對 **Power BI Desktop** 擷取的資料大小太大而無法在您的電腦上進行管理，您可以在資料流程中使用連結和計算實體來彙總資料 (在資料流程內)，並且只擷取預先備妥的彙總資料。 

使用該方式，就只會在資料流程中線上執行大型資料的處理，而不是在 **Power BI Desktop** 的執行中執行個體內本機執行。 該方法讓 Power BI Desktop 能夠擷取較少量的資料，並讓資料流程的體驗能夠持續迅速回應。

## <a name="additional-considerations"></a>其他考量

大部分資料流程位於 Power BI 服務租用戶中。 但是，**Power BI Desktop** 使用者無法存取儲存在 Azure Data Lake Storage Gen2 帳戶中的資料流程，除非他們是資料流程的擁有者，或已獲得資料流程之 CDM 資料夾的明確授權。 請考慮下列情況：

1.  Anna 建立新的工作區，並將其設定成在組織的 Data Lake 中儲存資料流程。
2.  Ben 是 Anna 所建立之工作區的成員，他想要使用 Power BI Desktop 和資料流程連接器，從 Anna 建立的資料流程取得資料。
3.  Ben 會收到錯誤，這是因為其未作為授權使用者新增至該資料流程在 Data Lake 中的 CDM 資料夾。

若要解決此問題，Ben 必須被授與 CDM 資料夾及其檔案的讀者權限。 您可在[設定及取用資料流程](dataflows/dataflows-configure-consume.md)中深入了解如何授與 CDM 資料夾的存取權限。




## <a name="next-steps"></a>後續步驟
您可搭配資料流程執行各式各樣有趣的作業。 如需詳細資訊，請檢閱下列來源：

* [資料流程和自助資料準備簡介](dataflows/dataflows-introduction-self-service.md)
* [建立資料流程](dataflows/dataflows-create.md)
* [設定及取用資料流程](dataflows/dataflows-configure-consume.md)
* [將資料流程儲存體設定為使用 Azure Data Lake Gen 2](dataflows/dataflows-azure-data-lake-storage-integration.md)
* [資料流程的進階功能](dataflows/dataflows-premium-features.md)
* [使用資料流程的 AI](dataflows/dataflows-machine-learning-integration.md)


以下還提供了一些與 **Power BI Desktop** 相關的文章，您可能會覺得它們很實用：

* [Power BI Desktop 中的資料來源](../connect-data/desktop-data-sources.md)
* [使用 Power BI Desktop 合併資料並使其成形](../connect-data/desktop-shape-and-combine-data.md)
* [直接將資料輸入 Power BI Desktop 中](../connect-data/desktop-enter-data-directly-into-desktop.md)