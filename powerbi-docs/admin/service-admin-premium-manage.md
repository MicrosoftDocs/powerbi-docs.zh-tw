---
title: 設定及管理 Power BI Premium 中的容量
description: 了解如何管理 Power BI Premium，以及讓整個組織存取內容。
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-premium
ms.topic: how-to
ms.date: 11/11/2020
LocalizationGroup: Premium
ms.openlocfilehash: 2eb1c5bd685cedabd96483867546c7578124af45
ms.sourcegitcommit: c33e53e1fab1f29872297524a7b4f5af6c806798
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/04/2021
ms.locfileid: "99532835"
---
# <a name="configure-and-manage-capacities-in-power-bi-premium"></a>設定及管理 Power BI Premium 中的容量

管理 Power BI Premium 牽涉到建立、管理和監視 Premium 容量。 本文提供逐步指示；如需容量的概觀，請參閱[管理 Premium 容量](service-premium-capacity-manage.md)。

了解如何管理提供內容專用資源的 Power BI Premium 和 Power BI Embedded 容量。

![Power BI 的容量設定畫面](media/service-admin-premium-manage/premium-capacity-management.png)

*容量* 是 Power BI Premium 和 [Power BI Embedded](../developer/embedded/azure-pbie-what-is-power-bi-embedded.md) 供應專案的核心。 它是一組專門保留供組織使用的資源集。 擁有容量可讓您將儀表板、報表和資料集發佈給整個組織的使用者，而不必為使用者一一購買授權。 它也會為容量中所裝載內容提供可靠且一致的效能。 如需詳細資訊，請參閱[什麼是 Power BI Premium？](service-premium-what-is.md)。

> [!NOTE]
> Power BI Premium 最近已發行名叫 **Premium Gen2** 的新版本 Premium，其目前處於預覽狀態。 Premium Gen2 將能簡化 Premium 容量的管理，並減少管理負擔。 如需詳細資訊，請參閱 [Power BI Premium 第 2 代 (預覽)](service-premium-what-is.md#power-bi-premium-generation-2-preview)。

## <a name="manage-capacity"></a>管理容量

在 Microsoft 365 中購買容量節點之後，請在 Power BI 管理入口網站中設定容量。 您可以在入口網站的 [容量設定] 區段中管理 Power BI Premium 容量。

![管理入口網站內的容量設定](media/service-admin-premium-manage/admin-portal-premium.png)

您可以選取容量的名稱來管理容量。 這會將您帶到容量管理畫面。

![選取容量名稱以移至容量指派畫面](media/service-admin-premium-manage/capacity-assignment.png)

如果未將任何工作區指派給容量，您會看到[將工作區指派給容量](#assign-a-workspace-to-a-capacity)的相關訊息。

### <a name="setting-up-a-new-capacity-power-bi-premium"></a>設定新的容量 (Power BI Premium)

管理入口網站會顯示您已使用和您仍然可用的「虛擬核心」(V 核心) 數目。 V 核心總數是根據您購買的進階 SKU 數。 例如，購買 P3 和 P2 會得到 48 個可用的核心，P3 有 32 個，P2 有 16 個。

![Power BI Premium 已使用和可使用的 V 核心](media/service-admin-premium-manage/admin-portal-v-cores.png)

如有可用的 V 核心，請執行下列步驟來設定新容量。

1. 選取 [設定新的容量]。

1. 提供您容量的名稱。

1. 定義誰是這個容量的管理員。

1. 選取容量大小。 可用的選項取決於您有多少可用的 V 核心。 您無法選取超過可用數量的選項。

    ![可用的 Premium 容量大小](media/service-admin-premium-manage/premium-capacity-size.png)

1. 選取 [設定]。

    ![設定新的容量](media/service-admin-premium-manage/set-up-capacity.png)

容量管理員以及 Power BI 管理員和 Microsoft 365 全域管理員，接著會看到管理入口網站中所列的容量。

### <a name="capacity-settings"></a>容量設定

1. 在 Premium 容量管理畫面的 [動作] 下方，選取 **齒輪圖示** 以檢閱和更新設定。 

    ![容量管理區中的容量動作](media/service-admin-premium-manage/capacity-actions.png)

1. 您可以看到誰是服務管理員、容量的 SKU/大小，以及容量所在的地區。

    ![容量設定](media/service-admin-premium-manage/capacity-settings.png)

1. 您也可以重新命名或刪除容量。

    ![Power BI Premium 中的容量設定 [刪除] 和 [套用] 按鈕](media/service-admin-premium-manage/capacity-settings-delete.png)

> [!NOTE]
> Power BI Embedded 容量設定是在 Microsoft Azure 入口網站中進行管理。

### <a name="change-capacity-size"></a>變更容量大小

Power BI 管理員和 Microsoft 365 全域管理員可變更 Power BI Premium 容量。 不是 Power BI 管理員或 Microsoft 365 全域管理員的容量管理員沒有此選項。

1. 選取 [變更容量大小]。

    ![變更 Power BI Premium 容量大小](media/service-admin-premium-manage/change-capacity-size.png)

1. 在 [變更容量大小] 畫面上，視情況升級或降級您的容量。

    ![變更 Power BI Premium 容量大小下拉式清單](media/service-admin-premium-manage/change-capacity-size2.png)

    系統管理員可隨意建立、調整大小和刪除節點，只要他們有必要的 V 核心數量。

    P SKU 無法降級為 EM SKU。 您可以將滑鼠暫留在任何已停用的選項上以查看說明。



> [!IMPORTANT]
> 如果 Power BI Premium 容量遇到高資源使用量，因而發生效能或可靠性問題，您可收到通知電子郵件以找出問題並加以解決。 如需詳細資訊，請參閱[容量和可靠性通知](service-interruption-notifications.md#capacity-and-reliability-notifications)。


### <a name="manage-user-permissions"></a>管理使用者權限

您可以指派其他容量管理員，以及指派具有「容量指派」權限的使用者。 如果具有指派權限的使用者是該工作區系統管理員，則其可將工作區指派給容量。 他們也可以將其個人的「我的工作區」指派給容量。 具有指派權限的使用者無法存取管理入口網站。

> [!NOTE]
> 針對 Power BI Embedded，容量管理員是在 Microsoft Azure 入口網站中定義。

在 [使用者權限] 下方，展開 [具有指派權限的使用者]，然後視情況新增使用者或群組。

![容量使用者權限](media/service-admin-premium-manage/capacity-user-permissions2.png)

## <a name="assign-a-workspace-to-a-capacity"></a>將工作區指派給容量

有兩種方式可將工作區指派給容量：在管理入口網站和從工作區。

### <a name="assign-from-the-admin-portal"></a>從管理入口網站指派

容量管理員以及 Power BI 管理員和 Microsoft 365 全域管理員，可在管理入口網站的 Premium 容量管理區段中大量指派工作區。 當您管理容量時，會看到可讓您指派工作區的 [工作區] 區段。

![容量管理的工作區指派區域](media/service-admin-premium-manage/capacity-manage-workspaces.png)

1. 選取 [指派工作區]。 此選項可以在多個位置中使用。

1. 選取 [套用對象] 的選項。

    ![指派工作區](media/service-admin-premium-manage/assign-workspaces.png)

   | 選取項目 | 描述 |
   | --- | --- |
   | **依使用者選取工作區** | 當您指派使用者或群組的工作區時，會將這些使用者所擁有的所有工作區都指派給進階容量，包括使用者的個人工作區。 就是使用者會自動取得工作區指派權限。<br>這包括已指派給不同容量的工作區。 |
   | **特定工作區** | 輸入要指派給所選取容量的特定工作區名稱。 |
   | **The entire organization's workspaces (整個組織的工作區)** | 將整個組織的工作區指派給 Premium 容量，會將組織中的所有工作區和「我的工作區」指派給這個 Premium 容量。 此外，所有目前和未來使用者都有權將個別工作區重新指派給這個容量。 |
   | | |

1. 選取 [ **套用**]。

### <a name="assign-from-workspace-settings"></a>從工作區設定進行指派

您也可以從該工作區的設定中，將工作區指派給 Premium 容量。 若要將工作區移至容量，您必須具有該工作區的管理員權限，同時具有該容量的容量指派權限。 請注意，工作區管理員一律可以從 Premium 容量中移除工作區。

1. 選取省略符號 **(. . .)** ，然後選取 [編輯工作區] 來編輯工作區。

    ![從省略符號操作功能表編輯工作區](media/service-admin-premium-manage/edit-app-workspace.png)

1. 在 [編輯工作區] 下方，展開 [進階]。

1. 選取您想要將這個工作區指派至其中的容量。

    ![容量選項下拉式清單](media/service-admin-premium-manage/app-workspace-advanced.png)

1. 選取 [儲存]。

儲存之後，工作區和其所有內容都會移至 Premium 容量，而不會干擾終端使用者的任何體驗。

## <a name="power-bi-report-server-product-key"></a>Power BI 報表伺服器產品金鑰

在 Power BI 管理入口網站的 [容量設定] 索引標籤上，您可以存取 Power BI 報表伺服器產品金鑰。 這只適用於全域管理員，或已獲指派 Power BI 服務系統管理員角色的使用者，如已購買 Power BI Premium SKU。

![[容量設定] 內的 Power BI 報表伺服器金鑰](media/service-admin-premium-manage/pbirs-product-key.png)

選取 [Power BI 報表伺服器金鑰] 會顯示一個包含產品金鑰的對話方塊。 您可以複製金鑰，並在安裝時使用。

![Power BI 報表伺服器產品金鑰](media/service-admin-premium-manage/pbirs-product-key-dialog.png)

如需詳細資訊，請參閱[安裝 Power BI 報表伺服器](../report-server/install-report-server.md)。

## <a name="next-steps"></a>後續步驟

[管理 Premium 容量](service-premium-capacity-manage.md)

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)

Power BI 已推出 Power BI Premium Gen2 作為預覽供應項目，其能透過對下列領域的改進來改善 Power BI Premium 體驗：
* 效能
* 個別使用者授權
* 範圍更大的擴縮
* 改善的計量
* 自動調整
* 降低管理負擔

如需 Power BI Premium Gen2 的詳細資訊，請參閱 [Power BI Premium 第 2 代 (預覽)](service-premium-what-is.md#power-bi-premium-generation-2-preview)。