---
title: 圖格錯誤的疑難排解
description: 圖格在 Power BI 中嘗試進行重新整理時可能遇到的常見錯誤
author: davidiseminger
ms.author: davidi
ms.reviewer: kayu
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: troubleshooting
ms.date: 12/06/2018
LocalizationGroup: Troubleshooting
ms.openlocfilehash: f82c6c97b954745e264fe213b5070a9a498de939
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410704"
---
# <a name="troubleshooting-tile-errors"></a>圖格錯誤的疑難排解
以下是您在使用圖格時可能發生的常見錯誤和說明。

> [!NOTE]
> 如果您遇到以下未列出的錯誤，且其造成問題您的問題，可以在[社群網站](https://community.powerbi.com/)尋求進一步協助，也可以建立[支援票證](https://powerbi.microsoft.com/support/)。
> 
> 

## <a name="errors"></a>錯誤
**Power BI 載入模型時發生未預期的錯誤。請再試一次。**
或 **無法擷取資料模型。請連絡儀表板擁有者，確定資料來源與模型存在且可供存取。**

我們無法存取您的資料，因為無法連線到資料來源。 如果資料來源已移除、重新命名、移動、離線或變更權限，就會發生此問題。 請檢查來源是否仍處於我們所指向的位置，且您仍有存取權限。 如果這部分沒有問題，可能是來源速度較慢。 請等到來源上的負載較小時再試。 如果是內部部署來源，資料來源擁有者應可提供更詳細的資訊。

**您無權檢視此磚或開啟活頁簿。**

請連絡儀表板擁有者，確定您帳戶的資料來源與模型存在且可供存取。

**Power BI 視覺效果已由系統管理員停用。**

Power BI 系統管理員已為組織或安全性群組停用 Power BI 視覺效果。
您將無法使用 [Microsoft marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) 的 Power BI 視覺效果，或從檔案匯入私人視覺效果。 您僅可以使用預先封裝的視覺效果集。


**資料圖形必須包含至少一個群組或輸出資料的計算。請連絡儀表板擁有者。**

我們沒有任何資料可以顯示，因為查詢為空白。 請嘗試從欄位清單將某些欄位加入視覺效果中並重新釘選。

**無法顯示資料，因為 Power BI 無法判斷兩個或多個欄位之間的關聯性。**

您嘗試使用不相關資料表中的兩個或多個欄位。 您必須從視覺效果中移除不相關的欄位，然後再建立資料表之間的關聯性。 進行變更後，您即可重新將欄位新增至視覺效果。 您可以在 Power BI Desktop 或 Power Pivot for Excel 中完成這項作業。 [深入了解](../transform-model/desktop-create-and-manage-relationships.md)

**主座標軸與副座標軸中的群組重疊。主座標軸中的群組不能具有與副座標軸中之群組相同的索引鍵。**

這通常是暫時性的問題。 通常，在您將資料列的群組移至資料行時會發生此情況。 在此情況下，當您移動完所有群組時，錯誤應該就會消失。 如果您仍然看到此訊息，請嘗試切換資料列和資料行之間的欄位或軸圖例，或從視覺效果中移除欄位。  

**此視覺效果已超出可用資源。請嘗試篩選以減少顯示的資料量。**

您的視覺效果已嘗試查詢太多資料，因此我們無法以可用的資源完成結果。 請嘗試篩選視覺效果，以減少結果中的資料量。

**無法識別下列欄位：{0}。請以存在於資料集中的欄位更新視覺效果。**

您可能已刪除或重新命名欄位。 您可以從視覺效果移除中斷的欄位、加入不同的欄位，並重新將其釘選。

**無法擷取此視覺效果的資料。請再試一次。**

這通常是暫時性的問題。 如果您稍後再試，卻仍看到此訊息，請連絡支援人員。

**啟用單一登入 (SSO) 之後，圖格會繼續顯示未篩選的資料。**

如果底層資料集設定為使用 DirectQuery 模式或透過內部部署資料閘道的 Analysis Services 即時連線，就可能發生這種情況。 在此案例中，為資料來源啟用 SSO 之後，圖格會繼續顯示未篩選的資料，直到下一個圖格重新整理到期為止。 在下一個圖格重新整理時，Power BI 會使用已設定的 SSO，而圖格則會顯示根據使用者身分識別篩選的資料。 

若要立即查看已篩選的資料，您可以透過選取儀表板右上方的 [更多選項]  (...)，然後選取 [重新整理儀表板磚]  ，以強制執行磚重新整理。

身為資料集擁有者，您也可以變更磚重新整理頻率，並將它設定為15分鐘，以加速磚重新整理。 選取 Power BI 服務右上角的齒輪圖示，然後選取 [設定]  。 在 [設定]  頁面上，選取 [資料集]  索引標籤。展開 [排定的快取重新整理]  並變更 [重新整理頻率]  。 請務必在 Power BI 執行下一個磚重新整理之後，將設定重設為原始的重新整理頻率。

> [!NOTE]
> [排定的快取重新整理]  區段僅適用於 DirectQuery/LiveConnection 模式中的資料集。 匯入模式中的資料集不需要個別的磚重新整理，因為磚會在下一次排程的資料重新整理期間自動重新整理。

## <a name="contact-support"></a>連絡支援人員
如果您仍遇到問題，請[連絡支援人員](https://support.powerbi.com)以進一步調查。

## <a name="next-steps"></a>後續步驟
[為內部部署資料閘道進行疑難排解](service-gateway-onprem-tshoot.md)  
[對 Power BI Personal Gateway 進行疑難排解](service-admin-troubleshooting-power-bi-personal-gateway.md)  
有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)
