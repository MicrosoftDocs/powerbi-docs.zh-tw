---
title: 尋找已登入的 Power BI 使用者
description: 若為管理員，且想要查看誰已登入 Power BI，則可使用 Azure Active Directory 存取和使用情況報表。
author: kfollis
ms.author: kfollis
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: how-to
ms.date: 09/25/2020
LocalizationGroup: Administration
ms.openlocfilehash: 84d4b0ab295f003c34937084bd93dd6f27992c31
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96409278"
---
# <a name="find-power-bi-users-that-have-signed-in"></a>尋找已登入的 Power BI 使用者

若為組織的管理員，且想要查看誰已登入 Power BI，則可使用 [Azure Active Directory 存取和使用情況報表](/azure/active-directory/reports-monitoring/concept-sign-ins)。

> [!NOTE]
> **登入** 報表可提供有用的資訊，但無法識別每名使用者的授權類型。 請使用 Microsoft 365 系統管理中心來檢視授權。

## <a name="requirements"></a>需求

任何使用者都可查看自己的登入報表。若要查看所有使用者的報表，您必須是下列其中一種角色：全域管理員、安全性管理員、安全性讀取者、全域讀取者或報表讀取者。

## <a name="use-the-azure-active-directory-admin-center-to-view-sign-ins"></a>使用 Azure Active Directory 系統管理中心來查看登入

若要檢視登入活動，請遵循這些步驟。

1. 登入 [Azure Active Directory 系統管理中心](https://aad.portal.azure.com)，然後從入口網站功能表選取 [Azure Active Directory]。

1. 從資源功能表中，選取 [監視] > [登入]。
   
    ![醒目提示 Azure Active Directory 系統管理中心 [登入] 選項的螢幕擷取畫面。](media/service-admin-access-usage/azure-portal-sign-ins.png)

1. 根據預設，會顯示過去 24 小時內所有使用者與應用程式的登入。 若要選取不同的時段，請在工作窗格中選取 [日期]，然後選擇合宜的時段。 只能選擇過去七天內的資訊。 若只要查看 Power BI 的登入，請新增篩選。 選取 [新增篩選] > 選取 [應用程式] 作為篩選依據，然後選取 [套用]。 從工作窗格頂端選取 [應用程式名稱開頭]，然後輸入應用程式名稱。 選取 [套用]。

    **Microsoft Power BI** 會篩選與服務相關的登入活動。 **Power BI Gateway** 則會篩選內部部署資料閘道專用的登入活動。
   
    ![醒目提示 [應用程式] 欄位的登入篩選螢幕擷取畫面。](media/service-admin-access-usage/sign-in-filter.png)

## <a name="export-the-data"></a>匯出資料

您可以[下載兩種格式的登入報告](/azure/active-directory/reports-monitoring/quickstart-download-sign-in-report)：CSV 檔案或 JSON 檔案。

1. 從 [登入] 報表的命令列中，選取 [下載]，然後選取下列其中一個選項：

   * [CSV] 可下載目前篩選資料的 CSV 檔案。

   * [JSON] 可下載目前篩選資料的 JSON 檔案。

2. 輸入檔案名稱，然後選取 [下載]。

![資料匯出的螢幕擷取畫面，其中醒目提示 [下載] 選項。](media/service-admin-access-usage/download-sign-in-data-csv.png)

## <a name="data-retention"></a>資料保留

登入相關資料最多可保留七天，除非組織具有 Azure AD Premium 授權。 若使用 Azure AD Premium P1 或 Azure AD Premium P2，您即可看到過去 30 天內的資料。 如需詳細資訊，請參閱 [Azure Active Directory 報告保留原則](/azure/active-directory/reports-monitoring/reference-reports-data-retention)。

## <a name="next-steps"></a>後續步驟

[稽核使用者活動](service-admin-auditing.md)

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)