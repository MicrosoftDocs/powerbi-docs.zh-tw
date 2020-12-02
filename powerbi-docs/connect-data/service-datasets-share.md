---
title: 共用資料集
description: 身為資料集擁有者，您可以建立和共用您的資料集，讓其他人也可以使用。 了解如何共用它們。
author: paulinbar
ms.author: painbar
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 04/30/2020
LocalizationGroup: Share your work
ms.openlocfilehash: c73c5b1b803b73742f6f13456b07a2060f5757e4
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410405"
---
# <a name="share-a-dataset"></a>共用資料集

身為 Power BI Desktop 中的「資料模型」建立者，您會建立可在 Power BI 服務中發佈的「資料集」。 其他報表建立者可以使用您的資料集作為其自有報表的基礎。 在此文章中，您將了解如何共用您的資料集。 若要了解如何授與及移除您資料集的存取權，請參閱[建置權限](service-datasets-build-permissions.md)。

## <a name="steps-to-sharing-your-dataset"></a>共用資料集的步驟

1. 開始方式為使用 Power BI Desktop 中的資料模型建立 .pbix 檔案。 如果您打算將此資料集提供給其他人建立報表，您可能甚至無法在 .pbix 檔案中設計報表。

    最佳做法是將 .pbix 檔案儲存至 Microsoft 365 群組。

1. 將 .pbix 檔案發佈到 Power BI 服務中的[新工作區體驗](../collaborate-share/service-create-the-new-workspaces.md)。
    
    此工作區的其他成員，已經可以根據此資料集在其他工作區中建立報表。 您可以使用工作區內容清單中資料集上的 [管理權限] 選項，將資料集存取權提供給其他使用者。 

1. 您也可以從此工作區[發佈應用程式](../collaborate-share/service-create-distribute-apps.md)。 當您這麼做時，您可以在 [權限] 頁面上指定誰具有權限來進行哪些項目。

    > [!NOTE]
    > 如果您選取 [整個組織]，組織中將沒有任何人具有建置權限。 此為已知的問題。 因此，請在 [特定的個人或群組] 中指定電子郵件地址。  如果您希望整個組織都具有建置權限，請指定整個組織的電子郵件別名。

    ![設定應用程式權限](media/service-datasets-build-permissions/power-bi-dataset-app-permission-new-look.png)

1. 選取 [發佈應用程式]，或 [更新應用程式] (如果已發佈)。

## <a name="track-your-dataset-usage"></a>追蹤您的資料集使用方式

當您在工作區中擁有共用資料集時，您可能需要知道其他工作區中的哪些報表以該資料集為基礎。

1. 在資料集清單檢視中，選取 [檢視相關項目]。

    ![檢視相關項目圖示](media/service-datasets-build-permissions/power-bi-dataset-view-related-to-dataset.png)

1. [相關內容] 對話方塊會顯示所有相關項目。 在此清單中，您會看到此工作區與 [其他工作區] 中的相關項目。
 
    ![[相關內容] 對話方塊](media/service-datasets-build-permissions/power-bi-dataset-related-workspaces.png)

## <a name="limitations-and-considerations"></a>限制與考量
共用資料集的注意事項︰

* 當透過管理權限、共用報表或儀表板，或發佈應用程式來共用資料集時，除非使用[資料列層級安全性 (RLS)](../admin/service-admin-rls.md) 限制存取權，否則即會授與整個資料集的存取權。 報表作者可以使用相關功能，來自訂使用者的報表檢視或報表互動體驗，例如隱藏資料行、限制對視覺效果的動作等。 這些自訂的使用者體驗，不會限制使用者在資料集中可以存取哪些資料。 您可以在資料集內使用[資料列層級安全性 (RLS)](../admin/service-admin-rls.md)，根據每個人的認證來判斷其可存取哪些資料。

## <a name="next-steps"></a>後續步驟

- [跨工作區使用資料集](service-datasets-across-workspaces.md)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
