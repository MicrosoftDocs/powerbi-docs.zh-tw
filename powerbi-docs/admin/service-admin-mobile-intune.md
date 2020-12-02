---
title: 使用 Microsoft Intune 設定行動裝置應用程式
description: 如何使用 Microsoft Intune 設定 Power BI 行動應用程式 這包括如何新增及部署應用程式， 以及如何建立行動應用程式原則來控制安全性。
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 09/25/2020
LocalizationGroup: Administration
ms.openlocfilehash: 6ca9b241fe2d6f2914a603e722f2dd2c216e05df
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96408772"
---
# <a name="configure-mobile-apps-with-microsoft-intune"></a>使用 Microsoft Intune 設定行動裝置應用程式

Microsoft Intune 可讓組織管理裝置和應用程式。 iOS 與 Android 版 Power BI 行動裝置應用程式與 Intune 整合。 這個整合可讓您在您的裝置上管理應用程式，並控制安全性。 您可以透過設定原則，控制像是要求存取 PIN、控制應用程式處理資料的方式，甚至是在未使用應用程式時加密應用程式資料等項目。

Microsoft Power BI 行動應用程式可供存取重要的商務資訊。 您可查看儀表板與報表並與其互動，取得組織所有的受控裝置與應用程式商務資料。 如需所支援 Intune 應用程式的詳細資訊，請參閱[受 Microsoft Intune 保護的應用程式](/intune/apps/apps-supported-intune-apps)。

## <a name="general-mobile-device-management-configuration"></a>一般行動裝置管理設定

本文假設您已正確設定 Intune 並向 Intune 註冊裝置。 此文章並不是要做為完整的 Microsoft Intune 設定指南。 如需有關 Intune 的詳細資訊，請參閱[什麼是 Intune？](/intune/introduction-intune/)。

Microsoft Intune 可與行動裝置管理 (MDM) 同時存在於 Microsoft 365 內。 若使用 MDM，則裝置將會顯示為已註冊 MDM，但可在 Intune 中加以管理。

Intune 管理員必須先將應用程式新增至 Intune，並將應用程式指派給使用者，終端使用者才能在其裝置上使用 Power BI 應用程式。

> [!NOTE]
> 設定 Intune 之後，會針對您 iOS 或 Android 裝置上的 Power BI 行動裝置應用程式關閉背景資料重新整理。 當您進入應用程式時，Power BI 會從網路上的 Power BI 服務重新整理資料。

## <a name="step-1-add-the-power-bi-app-to-intune"></a>步驟 1：將 Power BI 應用程式新增至 Intune

若要將 Power BI 應用程式新增至 Intune，請使用下列主題中提供的步驟：
- [將 iOS 市集應用程式新增至 Microsoft Intune](/intune/apps/store-apps-ios)
- [將 Android 市集應用程式新增至 Microsoft Intune](/intune/apps/store-apps-android)

## <a name="step-2-assign-the-app-to-your-end-users"></a>步驟 2:將應用程式指派給使用者

將 Power BI 應用程式新增至 Microsoft Intune 之後，您即可將應用程式指派給使用者和裝置。 請務必注意，不論裝置是否由 Intune 管理，您都可以將應用程式指派給裝置。

若要將 Power BI 應用程式指派給使用者和裝置，請參閱[使用 Microsoft Intune 將應用程式指派給群組](/intune/apps/apps-deploy)中提供的步驟。

## <a name="step-3-create-and-assign-app-protection-policies"></a>步驟 3：建立並指派應用程式防護原則

應用程式保護原則 (APP) 是確保組織資料能夠被保護或保留在受控應用程式中的規則。 原則可以是在使用者嘗試存取或移動「公司」資料時，強制執行的一項規則，或者是當使用者在應用程式內時，禁止執行或受到監視的一組動作。 受管理應用程式是已套用應用程式保護原則的應用程式，而且可由 Intune 管理。

行動應用程式管理 (MAM) 應用程式防護原則可讓您管理和保護應用程式內的組織資料。 透過不需註冊的 MAM (MAM-WE)，包含機密資料的工作或學校相關應用程式幾乎可在任何裝置上管理，包含攜帶您自己的裝置 (BYOD) 案例中的個人裝置。 如需詳細資訊，請參閱[應用程式防護原則概觀](/intune/apps/app-protection-policy)。

若要建立並指派 Power BI 應用程式的應用程式防護原則，請參閱[如何建立及部署應用程式保護原則](/intune/apps/app-protection-policies)中提供的步驟。

## <a name="step-4-use-the-application-on-a-device"></a>步驟 4：在裝置上使用應用程式

受管理應用程式是公司支援人員可以設定來協助保護公司資料的應用程式，您可以在該應用程式中存取這些資料。 當在裝置上的受控應用程式中存取公司資料時，您可能會注意到應用程式的運作方式與您所預期方式稍有不同。 例如，您可能無法複製並貼上受保護的公司資料，或可能無法將該資料儲存至特定位置。

若要了解使用者可如何在其裝置上使用 Power BI 應用程式，請參閱下列文章中提供的步驟：
- [在 iOS 裝置上使用受管理的應用程式](/intune-user-help/use-managed-apps-on-your-device-ios#how-do-i-get-managed-apps)
- [在 Android 裝置上使用受管理的應用程式](/intune-user-help/use-managed-apps-on-your-device-android)

## <a name="next-steps"></a>後續步驟

[如何建立及部署應用程式保護原則](/intune/app-protection-policies) 

[行動裝置的 Power BI 應用程式](../consumer/mobile/mobile-apps-for-mobile-devices.md)  

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)