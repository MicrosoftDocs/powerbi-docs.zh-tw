---
title: 服務主體限制
description: 服務主體限制
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 06/06/2020
ms.custom: include file
ms.openlocfilehash: 8e50a529bfd398a4075ebf049ee4aec1bcf48b4d
ms.sourcegitcommit: cd64ddd3a6888253dca3b2e3fe24ed8bb9b66bc6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/03/2020
ms.locfileid: "84315747"
---
## <a name="considerations-and-limitations"></a>考量與限制

* 服務主體只會使用[新的工作區](../collaborate-share/service-create-the-new-workspaces.md)。
* 使用服務主體時，不支援 [我的工作區]。
* 需要專用容量才能移至生產環境。
* 您無法使用服務主體登入 Power BI 入口網站。
* 需有 Power BI 管理員權限，才能在 Power BI 管理入口網站的開發人員設定中啟用服務主體。
* [為組織內嵌](../developer/embedded/embed-sample-for-your-organization.md)應用程式無法使用服務主體。
* 不支援[資料流程](../transform-model/service-dataflows-overview.md)管理。
* 服務主體目前不支援任何管理員 API。
* 搭配 [Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-overview) 資料來源使用服務主體時，服務主體本身必須具有 Azure Analysis Services 執行個體權限。 基於此目的使用包含服務主體的安全性群組將無法正常運作。