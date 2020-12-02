---
title: 使用備用電子郵件地址
description: 使用備用電子郵件地址
author: mihart
ms.author: mihart
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/23/2019
LocalizationGroup: Troubleshooting
ms.openlocfilehash: b03ecff1bcb74789adfea640c0279b568a09ffc7
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96409071"
---
# <a name="use-an-alternate-email-address"></a>使用備用電子郵件地址

當您註冊 Power BI 時，您必須提供電子郵件地址。 根據預設，Power BI 使用此地址來傳送有關服務中活動的更新給您。 例如，當有人傳送共用邀請給您時，便會傳送到此地址。

在某些情況下，您可能想要讓這些電子郵件傳送到備用電子郵件地址，而非您用來註冊的電子郵件地址。 本文說明如何在 Microsoft 365 與在 PowerShell 中指定備用地址。 本文也說明 Azure Active Directory (Azure AD) 解析電子郵件地址的方式。

> [!NOTE]
> 指定備用地址不會影響 Power BI 用於電子郵件訂閱、服務更新、電子報與其他促銷通訊的電子郵件地址。 那些通訊一律會傳送到您在註冊 Power BI 時使用的電子郵件地址。

## <a name="use-microsoft-365"></a>使用 Microsoft 365

若要在 Microsoft 365 中指定備用地址，請遵循下列步驟。

1. 開啟帳戶的[個人資訊](https://portal.office.com/account/#personalinfo)頁面。 若應用程式提示您，請以您用於 Power BI 的電子郵件地址和密碼進行登入。

1. 在左側功能表上，選取 [個人資訊]。

1. 在 [連絡人詳細資料] 區段中，選取 [編輯]。

    若無法編輯詳細資料，這表示系統管理員正在管理電子郵件地址。 與您的系統管理員連絡，更新您的電子郵件地址。

    ![[連絡人詳細資料] 對話方塊的螢幕擷取畫面，其中顯示如何指定替代電子郵件。](media/service-admin-alternate-email-address-for-power-bi/contact-details.png)

1. 請在 [備用電子郵件] 欄位中，輸入想要 Microsoft 365 用於 Power BI 更新的電子郵件地址。

## <a name="use-powershell"></a>使用 PowerShell

若要在 PowerShell 中指定備用電子郵件地址，請使用 [Set-AzureADUser](/powershell/module/azuread/set-azureaduser/) 命令。

```powershell
Set-AzureADUser -ObjectId john@contoso.com -OtherMails "otheremail@somedomain.com"
```

## <a name="email-address-resolution-in-azure-ad"></a>Azure AD 中的電子郵件地址解析

若要擷取 Power BI 的 Azure AD 內嵌權杖，您可以使用以下三種不同類型的電子郵件地址：

* 與使用者 Azure AD 帳戶建立關聯的主要電子郵件地址

* UserPrincipalName (UPN) 電子郵件地址

* *其他電子郵件地址* 陣列屬性

Power BI 會根據下列順序選取要使用的電子郵件：

1. 如果 Azure AD 使用者物件中存在 mail 屬性，則 Power BI 會在電子郵件地址中使用該 mail 屬性。

1. 如果 UPN 電子郵件「不是」 **\*.onmicrosoft.com** 網域電子郵件地址 ("\@" 符號後面的資訊)，則 Power BI 會在電子郵件地址中使用該郵件屬性。

1. 若 Azure AD 使用者物件中存在「其他電子郵件地址」陣列屬性，Power BI 會使用該清單中的第一個電子郵件 (因為此屬性中可能包含電子郵件的清單)。

1. 如果上述條件都不存在，Power BI 會使用 UPN 地址。

有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)
