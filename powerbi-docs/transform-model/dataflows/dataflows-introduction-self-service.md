---
title: 資料流程和自助資料準備簡介
description: 概述 Power BI 資料流程是什麼，以及使用 Power BI 流程的時機
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-dataflows
ms.topic: how-to
ms.date: 10/01/2020
LocalizationGroup: Data from files
ms.openlocfilehash: 5dde70b9834d990987e42c6aa945940a7f110949
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96416063"
---
# <a name="introduction-to-dataflows-and-self-service-data-prep"></a>資料流程和自助資料準備簡介

隨著資料量持續成長，將該資料整頓為語式正確且可操作之資訊的挑戰也會隨之增加。 我們想要備妥資料以供分析，以填入視覺效果、報表和儀表板，好讓我們可快速地將資料量轉換為可操作的深入解析。 若要針對 Power BI 中的巨量資料使用自助資料準備，只需按幾下，就能從資料移至 Power BI 深入解析。

![資料流程](media/dataflows-introduction-self-service-flow.png)

## <a name="when-to-use-dataflows"></a>如何使用資料流程

資料流程的設計旨在支援下列案例：

* 建立可重複使用的轉換邏輯，讓 Power BI 中的許多資料集和報表共用。 資料流程可提升基礎資料項目的重複使用性，避免為雲端或內部部署資料來源分別建立連線。

* 公開 Azure Data Lake Gen 2 儲存體中的資料，讓您將其他 Azure 服務連線到原始基礎資料。

* 透過強制分析師連線到資料流程而非基礎系統來建立單一事實來源，讓您可控制存取哪些資料，以及向報表建立人員公開資料的方式。 您也可以將資料對應到業界標準定義，讓您建立井然有序且經過整理的檢視，與其他 Power Platform 中的服務和產品搭配使用。

* 若想要使用大型資料磁碟區並大規模執行 ETL，搭配 Power BI Premium 的資料流程可更有效率地進行縮放，並提供更多彈性。 資料流程支援各種不同的雲端和內部部署來源。 

* 防止分析人員直接存取基礎資料來源。 因為報表建立人員可在資料流程上進行建置，其可能可供更方便地僅允許少數人員存取基礎資料來源，然後為分析師提供資料流程存取，使其可在資料流程上進行建置。 這種方法可減少基礎系統的負載，並可讓系統管理員可更細微地控制重新整理載入的時機。

一旦建立資料流程之後，即可使用 Power BI Desktop 和 Power BI 服務來建立可利用 Common Data Service 深入探索商業活動的資料集、報表、儀表板及應用程式。 直接從資料流程建立所在的工作區管理資料流程重新整理排程，就像您的資料集一樣。

## <a name="next-steps"></a>後續步驟
本文提供適用於 Power BI 中巨量資料的自助資料準備概觀，以及可加以使用的許多方式。 

下列文章提供資料流程和 Power BI 的詳細資訊：

* [建立資料流程](dataflows-create.md)
* [設定及取用資料流程](dataflows-configure-consume.md)
* [將資料流程儲存體設定為使用 Azure Data Lake Gen 2](dataflows-azure-data-lake-storage-integration.md)
* [資料流程的進階功能](dataflows-premium-features.md)
* [使用資料流程的 AI](dataflows-machine-learning-integration.md)
* [資料流程限制與考量](dataflows-features-limitations.md)
* [資料流程最佳做法](dataflows-best-practices.md)


如需 Common Data Service 的詳細資訊，您可以閱讀它的概觀文章：
* [Common Data Model - 概觀](/powerapps/common-data-model/overview)