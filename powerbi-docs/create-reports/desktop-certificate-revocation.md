---
title: Power BI Desktop 中的憑證撤銷檢查
description: 如何在 UI 和登錄中撤銷 Power BI Desktop 的憑證
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: conceptual
ms.date: 01/25/2021
LocalizationGroup: Create reports
ms.openlocfilehash: 482f0f8279de9818b631ff79e7b37a215e7397bd
ms.sourcegitcommit: 7ed995eed0fd6e718748accf87bae384211cd95d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2021
ms.locfileid: "99056994"
---
# <a name="certificate-revocation-in-power-bi-desktop"></a>Power BI Desktop 中的憑證撤銷

Power BI 提供兩種方式來啟用或停用憑證檢查。 在2020年11月，我們針對 Power BI Desktop 中的網頁連接引進了簡單的開啟/關閉憑證撤銷檢查。 現在您可以更精細地控制憑證撤銷檢查。

## <a name="simple-certificate-revocation"></a>簡易憑證撤銷

在 Power BI Desktop 的使用者介面中，您可以啟用或停用此功能。

- **在 [檔案**] 功能表上 > [**選項及設定]**  >  **選項** 中，選取 [**安全性**]，然後選取或清除 [**啟用憑證撤銷檢查**]。

## <a name="more-fine-grained-control"></a>更精細的控制

您可以使用第三個選項，更精細地控制憑證撤銷檢查。 

- **基本**  基本檢查會接受其撤銷狀態為未知的憑證，例如因為憑證未指定此憑證。 對於使用公司 proxy 伺服器的組織來說，這項檢查是很重要的。 這與選取 Power BI Desktop 中的核取方塊相同。
- **已停用** 與停用 Power BI Desktop 中的核取方塊相同。
- **全面** 您可以在 *完整* 模式中停用或啟用撤銷檢查，這樣就不會接受具有未知撤銷狀態的憑證。 


|憑證撤銷資訊狀態 | 全方位檢查 | 基本檢查 | 無 |
|---------|---------|---------|---------|
|已撤銷     |  ❌  | ❌  | ✔   |
|Unknown  |  ❌    |  ✔   |    ✔  |
|未撤銷  | ✔  |    ✔ |    ✔  |

簡單的 [啟用] 或 [停用] 核取方塊仍位於 Power BI Desktop 使用者介面中。 若要使用更精細的控制，請設定下列 DWORD 登錄值： `DisableCertificateRevocationCheck` 。 您可以在 Power BI Desktop 登錄機碼中設定這個值。 這是下列其中一項，視您的作業系統而定：

```
HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Microsoft Power BI Desktop
```

或：

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Power BI Desktop
```

將登錄值設定為下列其中一個值： 

|值  |模式  |組態  |
|---------|---------|---------|
|0     | 基本   | 接受具有未知撤銷狀態的憑證。 相當於啟用 Power BI Desktop 中的核取方塊。 |
|1     | 已停用  | 忽略所有撤銷檢查。 相當於停用 Power BI Desktop 中的核取方塊。  |
|2     | 完整  |  不需要撤銷憑證。 不接受具有未知撤銷狀態的憑證 |

設定此登錄設定，以充分利用更精細的控制。