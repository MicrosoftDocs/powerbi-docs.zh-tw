---
title: 服務主體建立應用程式
description: 服務主體建立應用程式
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 10/15/2020
ms.custom: include file
ms.openlocfilehash: 0f6c74ddc5a7decc8c1a6444568de44d3adbbc68
ms.sourcegitcommit: 8561902ef0ad63b0881187a22f25d1aa1ec3bcbc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/20/2020
ms.locfileid: "92210791"
---
## <a name="step-2---create-an-azure-ad-security-group"></a>步驟 2 - 建立 Azure AD 安全性群組

您的服務主體沒有任何 Power BI 內容和 API 的存取權。 若要給予服務主體存取權，請在 Azure AD 中建立安全性群組，並將您建立的服務主體新增至該安全性群組。

有兩種方法可建立 Azure AD 安全性群組：
* 手動 (在 Azure 中)
* 使用 PowerShell

### <a name="create-a-security-group-manually"></a>手動建立安全性群組

若要手動建立 Azure 安全性群組，請依照[使用 Azure Active Directory 建立基本群組並新增成員](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)一文中的指示進行。 

### <a name="create-a-security-group-using-powershell"></a>使用 PowerShell 建立安全性群組

以下範例指令碼可建立新的安全性群組，並將應用程式新增至該安全性群組。

>[!NOTE]
>如果您想要為整個組織啟用服務主體存取，請略過此步驟。

```powershell
# Required to sign in as admin
Connect-AzureAD

# Create an Azure AD security group
$group = New-AzureADGroup -DisplayName <Group display name> -SecurityEnabled $true -MailEnabled $false -MailNickName notSet

# Add the service principal to the group
Add-AzureADGroupMember -ObjectId $($group.ObjectId) -RefObjectId $($sp.ObjectId)
```

## <a name="step-3---enable-the-power-bi-service-admin-settings"></a>步驟 3 - 啟用 Power BI 服務系統管理員設定

若要讓 Azure AD 應用程式能夠存取 Power BI 內容和 API，Power BI 系統管理員必須在 Power BI 系統管理員入口網站中啟用服務主體存取權。

將您在 Azure AD 中建立的安全性群組新增至 [開發人員設定] 中的特定安全性群組區段。

>[!IMPORTANT]
>服務主體可以存取針對其啟用的任何租用戶設定。 根據您的系統管理員設定而定，這包括特定安全性群組或整個組織。
>
>若要將服務主體存取限制為特定的租用戶設定，僅允許存取特定安全性群組。 或者，您可以為服務主體建立專用的安全性群組，並將其從所需的租用戶設定中排除。

>[!div class="mx-imgBorder"]
>:::image type="content" source="../developer/embedded/media/embed-service-principal/admin-portal.png" alt-text="螢幕擷取畫面顯示 Power BI 入口網站內管理選項中的開發人員設定。":::

## <a name="step-4---add-the-service-principal-to-your-workspace"></a>步驟 4 - 將服務主體新增至您的工作區

若要啟用 Azure AD 應用程式存取成品 (例如 Power BI 服務中的報表、儀表板和資料集)，請將服務主體實體新增為您工作區的成員或系統管理員。

>[!NOTE]
>本節提供 UI 指示。 您也可以使用[群組 - 新增群組使用者 API](/rest/api/power-bi/groups/addgroupuser)，將服務主體新增至工作區。

1. 捲動至您想要啟用存取權的工作區，然後從 [更多] 功能表中，選取 [工作區存取權]。

    :::image type="content" source="../developer/embedded/media/embed-service-principal/workspace-access.png" alt-text="螢幕擷取畫面顯示 Power BI 入口網站內管理選項中的開發人員設定。":::

2. 以**管理員**或**成員**身分將服務主體新增至工作區。

    :::image type="content" source="../developer/embedded/media/embed-service-principal/add-service-principal-in-the-UI.png" alt-text="螢幕擷取畫面顯示 Power BI 入口網站內管理選項中的開發人員設定。":::