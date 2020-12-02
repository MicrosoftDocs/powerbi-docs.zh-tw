---
title: 針對共用儀表板和報表進行疑難排解
description: 如何解決與組織內外同事共用 Power BI 儀表板和報表的問題。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: troubleshooting
ms.date: 06/23/2020
LocalizationGroup: Share your work
ms.openlocfilehash: 89d0ddbbcdd5caf47256fc85864590e55a1caa86
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96406656"
---
# <a name="troubleshoot-sharing-dashboards-and-reports"></a>針對共用儀表板和報表進行疑難排解

以下是當您共用儀表板或報表時，或當其他人與您共用時，可能出現的一些常見問題。 

## <a name="dashboard-recipients-see-a-lock-icon-in-a-tile"></a>儀表板收件者在圖格中看到一個鎖定圖示

與您共用的人員在嘗試檢視報告時，可以看到儀表板中鎖定的圖格或「需要權限」訊息。

![Power BI 鎖定的圖格](media/service-share-dashboards/power-bi-locked_tile_small.png)

若是如此，您需要授與他們基礎資料集的權限。

1. 前往內容清單中的 [資料集] 索引標籤。

1. 選取資料集旁的省略符號 ( **...** )，然後選取 [管理權限]。

    ![管理權限](media/service-share-dashboards/power-bi-sharing-manage-permissions.png)

1. 選取 [新增使用者]。

    ![選取 [新增使用者]](media/service-share-dashboards/power-bi-share-dataset-add-user.png)

1. 輸入個人、通訊群組或安全性群組的完整電子郵件地址。 您無法共用動態通訊清單。

    ![新增電子郵件地址](media/service-share-dashboards/power-bi-add-user-dataset.png)

1. 選取 [新增]。

## <a name="i-cant-share-a-dashboard-or-report"></a>我無法共用儀表板或報表

若要共用儀表板或報表，您必須具備再次共用基礎內容 (亦即，任何相關報表和資料集) 的權限。 如果您看到無法共用的訊息，可請報表作者提供再次共用這些報表和資料集的權限。

![「無法共用」訊息](media/service-share-dashboards/power-bi-sharing-unable-to-share.png)

## <a name="i-dont-have-access-to-a-dashboard-or-report"></a>我無法存取儀表板或報表

如果您在選取報表或儀表板的連結時看到「要求存取」訊息，則表示您沒有檢視報表或儀表板的權限。 您必須[要求存取報表或儀表板的權限](service-request-access.md)。

## <a name="next-steps"></a>後續步驟

- [與同事和其他人共用 Power BI 儀表板和報表](service-share-dashboards.md)
- [應該如何共同作業和共用儀表板和報表？](service-how-to-collaborate-distribute-dashboards-reports.md)
-  [共用已篩選的 Power BI 報表](service-share-reports.md)
- 有問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)
