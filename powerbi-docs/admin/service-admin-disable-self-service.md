---
title: 啟用或停用自助式註冊與購買
description: 系統管理員如何關閉使用者註冊 Power BI 服務和購買或升級授權之功能的做法資訊。
author: mihart
ms.author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 04/08/2020
ms.custom: licensing support
LocalizationGroup: Administration
ms.openlocfilehash: ff695d49caeab7bed88b932cec6aaec11ec4df29
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96413671"
---
# <a name="enable-or-disable-self-service-sign-up-and-purchasing"></a>啟用或停用自助式註冊與購買

在大多數組織中，預設會啟用自助式註冊。 您組織中的個別使用者可以使用其工作或學校帳戶來註冊 Power BI。 如果使用者嘗試使用需要 Pro 授權的功能，系統可能也會提供使用者直接購買 Power BI Pro 授權的選項。 身為管理員，您可以決定是要啟用還是停用自助式註冊。 您也可以控制組織中的使用者是否能夠自助購買來取得自己的授權。

> [!NOTE]
>如果您透過 Microsoft 雲端方案提供者 (CSP) 取得 Power BI，則此設定可能會停用以阻止使用者個別註冊。 您的 CSP 也可能會作為您組織的全域管理員，您必須與其聯絡來協助您變更此設定。
>
>

您需使用 PowerShell 命令來變更控制自助式註冊與購買的設定。 有兩個控制組織中使用者是否能夠進行自助式註冊或自助式購買的設定。

- 如果您想要停用所有自助式註冊，請使用 Azure AD PowerShell 命令來變更 Azure Active Directory 中名為 **AllowAdHocSubscriptions** 的設定。 請依照此文章中的步驟來[啟用或停用自助式註冊](#enable-or-disable-self-service-signup)。 此選項會關閉「所有」Microsoft 雲端式應用程式與服務的自助式註冊功能。

- 如果您想要防止使用者購買自己的 Pro 授權，請使用 MSCommerce PowerShell 命令來變更 **AllowSelfServicePurchase** 設定。 此設定可讓您關閉特定產品的自助式購買功能。 請依照此文章中的步驟來[啟用或停用 Power BI Pro 授權的自助式購買](#enable-or-disable-self-service-purchase)。

## <a name="enable-or-disable-self-service-signup"></a>啟用或停用自助式註冊

如果已啟用自助式註冊，則 **AllowAdHocSubscriptions** 的值會是 *true*。 讓我們看看當您將此設定變更為 *false* 時，會發生什麼情況：

- 如果您將設定從 true 變更為 false，組織中的新使用者便無法個別註冊。 所有在您變更設定前便已註冊 Power BI 的使用者則會保有其授權。

- 如果您將設定變更為 false，則已經具備 Power BI (免費) 授權的使用者仍可註冊個人 Power BI Pro 試用版。

- 管理員必須將所有 Power BI 授權指派給需要授權的新使用者。

### <a name="before-you-begin"></a>開始之前

這些步驟會使用 Azure Active Directory PowerShell 命令來變更 **AllowAdHocSubscriptions** 設定的值。 您必須安裝 Azure AD PowerShell 模組，才能使用這些命令。 如需有關使用 PowerShell 的詳細資訊，請參閱[開始使用 Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell?view=powershell-7)。

若要安裝 Azure AD 模組，請以系統管理員身分啟動 Windows PowerShell。 確定您的本機執行原則允許您執行指令碼。 如果遇到問題，請參閱 [PowerShell 執行原則](/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7#powershell-execution-policies)，以了解如何變更您的本機原則。

請執行下列命令來安裝 Azure AD 模組：

```powershell
Install-Module MSOnline
```

### <a name="change-the-self-service-signup-policy"></a>變更自助式註冊原則

在 PowerShell 中，執行下列命令來連線到 Azure AD：

```powershell
Connect-MsolService
```

在登入對話方塊中輸入您的管理員認證，完成任何可能需要的雙重要素驗證。 驗證之後，您會回到 PowerShell 視窗。

若要檢視目前的設定，請執行下列命令。 藉由使用 "fl" 參數可將輸出經由管道傳送到格式化清單。

```powershell
Get-MsolCompanyInformation | fl AllowAdHocSubscriptions
```

若要變更目前的設定，請執行此命令：

```powershell
Set-MsolCompanySettings -AllowAdHocSubscriptions $false
```

執行此命令之後，就會停用所有使用者的自助式註冊功能。 若要重新開啟該功能，請再次執行此命令，並將值設定為 $true。

## <a name="enable-or-disable-self-service-purchase"></a>啟用或停用自助式購買

如果已啟用自助式購買，則 **AllowSelfServicePurchase** 的值會是 *true*。 讓我們看看當您將此設定變更為 *false* 時，會發生什麼情況：

- 如果您將設定從 true 變更為 false，則組織中的使用者便無法購買自己的 Power BI Pro 授權。 所有在您變更設定前便已購買授權的使用者則會保有其授權。

- 如果您將設定變更為 false，具備 Power BI (免費) 授權的使用者並無法取得個人 Power BI Pro 授權。 

- 管理員必須將 Pro 授權指派給所有需要授權的使用者。

### <a name="before-you-begin"></a>開始之前

這些步驟會使用 MSCommerce PowerShell 命令來變更 **AllowSelfServicePurchase** 設定的值。 您必須安裝 MSCommerce PowerShell 模組，才能使用這些命令。 如需有關使用 PowerShell 的詳細資訊，請參閱[開始使用 Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell?view=powershell-7)。

若要安裝 MSCommerce 模組，請以系統管理員身分啟動 Windows PowerShell。 確定您的本機執行原則允許您執行指令碼。 如果遇到問題，請參閱 [PowerShell 執行原則](/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7#powershell-execution-policies)，以了解如何變更您的本機原則。

請執行下列命令來安裝 MSCommerce 模組：

```powershell
Install-Module -name MSCommerce
```

### <a name="change-the-self-service-signup-policy"></a>變更自助式註冊原則

在 PowerShell 中，執行下列命令來進行連線：

```powershell
Connect-MSCommerce
```

在登入對話方塊中輸入您的管理員認證，完成任何可能需要的雙重要素驗證。 驗證之後，PowerShell 視窗會顯示成功連線。

若要檢視目前的設定，請執行下列命令。 為了防止文字被截斷，可使用 "fl" 參數將輸出經由管道傳送到格式化清單。

```powershell
Get-MSCommercePolicy -PolicyId AllowSelfServicePurchase | fl
```

您可以透過提供個別產品的 **ProductId**，停用個別產品的允許自助式購買設定。 若要變更 Power BI 服務的目前設定，請執行此命令：

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0L3PB -Enabled $False
```

執行此命令之後，就會停用所有使用者的 Power BI 自助式購買功能。 若要重新開啟該功能，請再次執行此命令，並將值設定為 $true。

## <a name="next-steps"></a>後續步驟

如需有關 Power BI 及 Power Platform 其餘部分中自助式購買的詳細資訊，請參閱下列文章：

- [自助式購買常見問題集](/microsoft-365/commerce/subscriptions/self-service-purchase-faq?view=o365-worldwide#admin-capabilities) \(部分機器翻譯\)
- [使用 MSCommerce PowerShell 模組的 AllowSelfServicePurchase](/microsoft-365/commerce/subscriptions/allowselfservicepurchase-powershell?view=o365-worldwide) \(部分機器翻譯\)