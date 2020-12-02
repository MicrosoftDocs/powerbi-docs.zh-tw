---
title: Power BI 中受信任的第三方連接器
description: 如何在 Power BI 中信任已簽署的第三方連接器
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: conceptual
ms.date: 04/3/2019
LocalizationGroup: Connect to data
ms.openlocfilehash: aa135853119615c8be626699daffca88c03633fb
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410865"
---
# <a name="trusted-third-party-connectors"></a>受信任的第三方連接器

## <a name="why-do-you-need-trusted-third-party-connectors"></a>為什麼您需要信任的第三方連接器？

在 Power BI 中，我們通常會建議將「資料延伸模組安全性」層級保持在較高的層級，以避免載入未經 Microsoft 認證的程式碼。 不過，在許多情況下，您可能會想要載入特定連接器，也就是您所撰寫的連接器，或由 Microsoft 憑證路徑以外的顧問或廠商提供給您的連接器。

指定連接器的開發人員可以使用憑證來簽署它，並提供您在不降低您的安全性設定的情況下安全地載入該連接器所需的資訊。

如果您想要深入了解安全性設定，可以在[這裡](./desktop-connector-extensibility.md)閱讀相關資訊。

## <a name="using-the-registry-to-trust-third-party-connectors"></a>使用登錄來信任第三方連接器

在 Power BI 中信任第三方連接器的方式，是透過在指定的登錄值中列出您想要信任之憑證的指紋來完成。 如果此指紋符合您要載入的連接器上憑證的指紋，您就可以在 Power BI 的「建議使用」安全性層級中載入它。 

登錄路徑為 HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Power BI Desktop。 請確定路徑存在，或加以建立。 我們之所以選擇這個位置，是因為它主要是由 IT 原則控制，而且需要有本機電腦管理的存取權才能編輯。 

![未設定信任的第三方金鑰的 Power BI Desktop 登錄](media/desktop-trusted-third-party-connectors/desktoptrustedthird1.png)

在以上指定的路徑下加入新的值。 類型應該是「多字串值」(REG_MULTI_SZ)，而且應該稱為 “TrustedCertificateThumbprints” 

![有一個信任的第三方連接器項目但沒有金鑰的 Power BI Desktop 登錄](media/desktop-trusted-third-party-connectors/desktoptrustedthird2.png)

新增您想要信任之憑證的指紋。 您可以使用 “\0” 做為分隔符號來新增多個憑證，或在登錄編輯程式中，以滑鼠右鍵按一下 -> [修改]，並將每個指紋放在新的一行。 範例指紋取自自我簽署憑證。 

 ![已設定信任的第三方金鑰的 Power BI Desktop 登錄](media/desktop-trusted-third-party-connectors/desktoptrustedthird3.png)

如果您已正確遵循指示，且開發人員已獲得適當的指紋，您現在應該能夠安全地信任使用相關聯憑證簽署的連接器。

## <a name="how-to-sign-connectors"></a>如何簽署連接器

如果有您或開發人員需要簽署的連接器，則可以在[這裡](/power-query/handlingconnectorsigning)的 Power Query 文件中閱讀其相關資訊。