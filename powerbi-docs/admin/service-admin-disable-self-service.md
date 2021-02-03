---
title: 啟用或停用自助式註冊與購買
description: 系統管理員如何關閉使用者註冊 Power BI 服務和購買或升級授權之功能的做法資訊。
author: mihart
ms.author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 01/31/2021
ms.custom: licensing support
LocalizationGroup: Administration
ms.openlocfilehash: 80e263cc6e67c28b7593fcf10aea4c81c9f4af86
ms.sourcegitcommit: f7330dabb9cd8bce90bb2efec3e3273a11578f10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2021
ms.locfileid: "99494297"
---
# <a name="enable-or-disable-self-service-sign-up-and-purchasing"></a>啟用或停用自助式註冊與購買

## <a name="what-is-self-service"></a>什麼是自助服務？

自助指的是，組織中的個人 (公司或學校) 註冊以使用其組織的訂用帳戶所付費的服務，或使用免費的服務，而不要求其組織代表他們採取行動。 個人會前往 Microsoft 網站，尋找組織提供的雲端服務，並使用其組織電子郵件地址來註冊該服務。 

在許多情況下，組織會支付該服務訂用帳戶的費用。 在其他情況下，個人是第一位使用者，而且會成為服務的系統管理員。 若為試用版或免費授權，則不需要購買。 但是針對 Power BI Pro，組織須負責支付每月費用。 

身為 Microsoft 365 系統管理員，您可以看到註冊試用版、授權和訂用帳戶的人員。

> [!NOTE]
> 自助式註冊僅適用于商業雲端客戶，而非國家雲端或政府客戶。

## <a name="when-to-use-self-service-sign-up-and-purchase"></a>使用自助式註冊和購買的時機

### <a name="self-service-is-a-good-idea"></a>自助服務是個不錯的主意： 

- 在較大型且非集中式的組織中， (公司或學校) ，其中的個人通常會有彈性地購買 SaaS (軟體即服務) 授權以供自己使用。 
- 適用于只需要購買一或 Power BI Pro 多個授權的一位或小型組織。
- 對於嘗試 Power BI 的個人來說，在為整個組織購買訂用帳戶之前，請先熟練。
- 適用于目前具有 Power BI 免費授權的使用者，現在想要建立並共用內容，並將自己升級為 Power BI Pro 試用版。 

### <a name="you-may-want-to-disable-self-service-when"></a>在下列情況中，您可能會想要停用自助服務：

- 您的組織已有符合規範、法規、安全性和治理需求的採購流程。 您必須確保所有 Power BI Pro 授權都會根據定義的進程核准及管理。 
- 您的組織具有新 Power BI Pro 使用者的需求，例如資料保護原則的強制定型或使用者確認。
- 因為資料隱私權或其他考慮，所以您的組織禁止使用 Power BI 服務，且需要嚴格地控制 Power BI 免費授權的指派。
- 若要確保所有 Power BI Pro 授權都落在 enterprise 合約下，以利用經過協商/折扣的授權費率。
- 對於具有 Power BI 免費授權的目前使用者，系統會提示他們嘗試或直接購買 Power BI Pro 授權。 您的組織可能不希望這些使用者升級，因為安全性、隱私權或費用。


## <a name="enable-and-disable-self-service"></a>啟用及停用自助服務

身為管理員，您可以決定是要啟用還是停用自助式註冊。 您也可以判斷組織中的使用者是否可以進行自助式購買，以取得自己的授權。 

關閉自助式註冊，讓使用者無法瀏覽 Power BI 以進行資料視覺化和分析。 如果您封鎖個別註冊，則您可以為組織取得 Power BI (免費) 授權，並指派給所有使用者。 

> [!NOTE]
>如果您透過 Microsoft 雲端解決方案提供者 (CSP) 取得 Power BI，可能會停用此設定，以防止使用者個別註冊。 您的 CSP 也可能會作為您組織的全域管理員，您必須與其聯絡來協助您變更此設定。
>


 您將使用 PowerShell 命令來變更控制自助式註冊和購買的設定。 

- 如果您想要停用所有自助式註冊，請使用 Azure AD PowerShell 命令來變更 Azure Active Directory 中名為 **AllowAdHocSubscriptions** 的設定。 請依照此文章中的步驟來[啟用或停用自助式註冊](#enable-or-disable-self-service-sign-up-for-your-organization)。 此選項會關閉「所有」Microsoft 雲端式應用程式與服務的自助式註冊功能。

- 如果您想要防止使用者購買自己的 Pro 授權，請使用 MSCommerce PowerShell 命令來變更 **AllowSelfServicePurchase** 設定。 此設定可讓您關閉特定產品的自助式購買功能。 請依照此文章中的步驟來[啟用或停用 Power BI Pro 授權的自助式購買](#enable-or-disable-self-service-purchase-in-your-organization)。

## <a name="enable-or-disable-self-service-sign-up-for-your-organization"></a>啟用或停用組織的自助式註冊

如果已啟用自助式註冊，則 **AllowAdHocSubscriptions** 的值會是 *true*。 讓我們看看當您將此設定變更為 *false* 時，會發生什麼情況：

- 您組織中的新使用者會被封鎖而無法個別註冊。 在您變更設定之前註冊 Power BI 的任何使用者都會保留其授權。

- 已 Power BI (免費) 授權的使用者仍可註冊個別 Power BI Pro 試用版。

- 系統管理員必須將所有 Power BI 授權指派給需要一個的新使用者。

### <a name="before-you-begin"></a>開始之前

這些步驟會使用 Azure Active Directory PowerShell 命令來變更 **AllowAdHocSubscriptions** 設定的值。 您必須安裝 Azure AD PowerShell 模組，才能使用這些命令。 如需有關使用 PowerShell 的詳細資訊，請參閱[開始使用 Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。

若要安裝 Azure AD 模組，請以系統管理員身分啟動 Windows PowerShell。 確定您的本機執行原則允許您執行指令碼。 如果遇到問題，請參閱 [PowerShell 執行原則](/powershell/module/microsoft.powershell.core/about/about_execution_policies#powershell-execution-policies)，以了解如何變更您的本機原則。

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

## <a name="enable-or-disable-self-service-purchase-in-your-organization"></a>在您的組織中啟用或停用自助式購買

如果已啟用自助式購買，則 **AllowSelfServicePurchase** 的值會是 *true*。 讓我們看看當您將此設定變更為 *false* 時，會發生什麼情況：

- 組織中的使用者會遭到封鎖，而無法購買自己的 Power BI Pro 授權。 在您變更設定之後，任何已購買授權的使用者都會保留其授權。

- 具有 Power BI (免費) 授權的使用者無法取得個別 Power BI Pro 授權。 

- 系統管理員必須將 Pro 授權指派給所有需要的使用者。

### <a name="before-you-begin"></a>開始之前

這些步驟會使用 MSCommerce PowerShell 命令來變更 **AllowSelfServicePurchase** 設定的值。 您必須安裝 MSCommerce PowerShell 模組，才能使用這些命令。 如需有關使用 PowerShell 的詳細資訊，請參閱[開始使用 Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)。

若要安裝 MSCommerce 模組，請以系統管理員身分啟動 Windows PowerShell。 確定您的本機執行原則允許您執行指令碼。 如果遇到問題，請參閱 [PowerShell 執行原則](/powershell/module/microsoft.powershell.core/about/about_execution_policies#powershell-execution-policies)，以了解如何變更您的本機原則。

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

## <a name="what-to-do-if-individuals-have-already-used-self-service"></a>如果個人已使用自助服務，該怎麼辦？

自助式註冊和購買都預設為啟用。 這可讓組織中的個人已經有 Power BI 的授權和訂閱。 無論您是否採取任何動作，都需要清楚瞭解已經存在的內容。

透過自助式註冊加入您租用戶的使用者，將獲指派一份專用授權，而您可以在系統管理儀表板的有效使用者窗格中加以篩選。 若要建立這個新檢視，請依照下列步驟執行。

1. 巡覽至 MIcrosoft 365 系統管理中心。

1. 請在瀏覽窗格中選取 [使用者] > [作用中使用者]。

1. 在 [Views] 功能表上，選取 [ **加入自訂視圖**]。

1. 為新的檢視命名，然後在 [已指派的產品授權] 下選取 [Power BI (免費)] 或 [Power BI Pro]。

    每個檢視只能選取一個授權。 如果您的組織同時有 [Power BI (免費)] 與 [Power BI Pro] 授權，則您可以建立兩個檢視。

1. 輸入您想要的任何其他條件，然後選取 [新增]。

    建立新檢視之後，即可在 [檢視] 功能表中取得該檢視。


    > [!NOTE]
    > 如果您的組織沒有連線到您電子郵件網域的 Microsoft 365 環境，則自助使用者會新增至僅限雲端的新使用者目錄。 您可能需要尋找、索取及 [接管已建立的](https://docs.microsoft.com/azure/active-directory/users-groups-roles/domains-admin-takeover)租使用者。 

## <a name="next-steps"></a>後續步驟

如需有關 Power BI 及 Power Platform 其餘部分中自助式購買的詳細資訊，請參閱下列文章：

- [自助式購買常見問題集](/microsoft-365/commerce/subscriptions/self-service-purchase-faq#admin-capabilities) \(部分機器翻譯\)
- [使用 MSCommerce PowerShell 模組的 AllowSelfServicePurchase](/microsoft-365/commerce/subscriptions/allowselfservicepurchase-powershell) \(部分機器翻譯\)