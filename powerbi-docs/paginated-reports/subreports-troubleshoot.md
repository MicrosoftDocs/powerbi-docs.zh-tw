---
title: 針對 Power BI 分頁報表中的子報表進行疑難排解
description: 了解使用子報表時常見問題的解決方案，子報表是位於編頁報表內部的報表項目。
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: troubleshooting
ms.date: 04/29/2020
ms.openlocfilehash: 06d9b0fc60d9b44f98108cf46bc35c5de15316d6
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/04/2020
ms.locfileid: "93297997"
---
# <a name="troubleshoot-subreports-in-power-bi-paginated-reports"></a>針對 Power BI 分頁報表中的子報表進行疑難排解

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

有時候在使用分頁報表的子報表時，您可能會得得非預期的結果，或功能不如預期。 本文提供子報表常見問題的解決方案。 「子報表」  是一個報表項目，其會在主分頁報表的主體內顯示另一份報表。 如需背景資料，請參閱 [Power BI 分頁報表的子報表](subreports.md)。

## <a name="subreport-couldnt-be-found"></a>找不到子報表

**說明：** 不會轉譯子報表。 而是出現錯誤訊息。

### <a name="message"></a>訊息

「在指定位置 'CustomerDetails' 找不到子報表 'Subreport1'。 請驗證子報表已發佈，且名稱正確無誤。」

### <a name="possible-reasons"></a>可能的原因

- 具有指定名稱的子報表和主報表不在相同工作區或應用程式中。
- 使用者無權存取子報表。
- 主報表的子報表數目已達到子報表限制 (50 份子報表)。

### <a name="troubleshooting-steps"></a>疑難排解步驟

**在工作區中**

- 請驗證存有錯誤訊息中指名的報表。 名稱不區分大小寫。

**在應用程式中**

- 請驗證應用程式中存有錯誤訊息指名的報表。 如需進一步協助，請連絡應用程式的作者。

**如果報表已共用**

1. 請驗證錯誤訊息指名的報表已與您共用。
2. 如果報表存在，請驗證主報表和子報表的擁有者名稱是否相同。 然後以該資訊連絡主報表的擁有者。

## <a name="subreport-renders-with-unexpected-content"></a>子報表轉譯非預期的內容

### <a name="possible-reason"></a>可能的原因

Power BI 可供使用者在相同工作區中有多份具有相同名稱的報表

### <a name="troubleshooting-steps-for-report-authors"></a>疑難排解步驟 (適用於報表作者)

1. 在 Power BI Report Builder 中開啟主報表，然後決定子報表的名稱。
2. 尋找工作區中具有相同名稱的報表。
3. 找出預期的報告，並重新命名其餘報表。

**針對非作者：** 連絡作者。

## <a name="data-retrieval-fails"></a>擷取資料失敗

**說明：** 轉譯子報表時，擷取資料失敗。 不會轉譯子報表。 而是出現錯誤訊息。

### <a name="message"></a>訊息

「擷取子報表 'Subreport1' 資料失敗，其位於：'InvoiceDetails'。 請檢查記錄檔以取得詳細資訊。」

### <a name="troubleshooting-steps"></a>疑難排解步驟

與資料存取發生問題的報表其一般疑難排解步驟相同。

## <a name="rendering-fails-unspecified-parameters"></a>轉譯失敗：未指定的參數

**說明：** 子報表轉譯因未指定的參數而失敗。 子報表具有強制參數，但主報表並未全部設定。

### <a name="message"></a>訊息 
「子報表 'Subreport1' 未指定一或多個參數，其位於：'SubreportAWithDS'。」

### <a name="troubleshooting-steps-for-the-report-author"></a>疑難排解步驟 (適用於報表作者)

1. 在 Power BI Report Builder 中開啟主報表。
2. 在 Power BI Report Builder 中開啟子報表。
3. 請驗證主報表中，於子報表報表項目內傳遞的參數集與子報表中參數集相符。

**針對非作者：** 連絡作者。

## <a name="rendering-fails-recursion-limit"></a>轉譯失敗：遞迴限制

**說明：** 子報表轉譯因遞迴限制而失敗。 子報表的巢狀深度不能超過 20 層。

### <a name="message"></a>訊息

「報表或子報表的遞迴子報表 'Subreport1'，超過允許的遞迴限制上限。」

### <a name="troubleshooting-steps-for-report-authors"></a>疑難排解步驟 (適用於報表作者)

- 減少巢狀。
- 重新設計報表結構。

## <a name="other-errors"></a>其他錯誤

**說明：** 不屬於前述任一類別的錯誤。

### <a name="message"></a>訊息

「錯誤：無法顯示子報表。」

### <a name="possible-reasons"></a>可能的原因

- 子報表轉譯期間發生多個錯誤，例如，參數與資料擷取問題不相符。
- 未預期的錯誤。

### <a name="troubleshooting-steps-for-report-authors"></a>疑難排解步驟 (適用於報表作者)

1. 驗證是否可以直接轉譯子報表。
2. 如果子報表可以轉譯，請檢查子報表和主報表中的參數。
3. 確定主報表的唯一子報表不超過 50 份，且子報表的巢狀不超過 20 層。
4. 如果無法解決此問題，請連絡 Power BI 支援。

**針對非作者：** 連絡作者。

## <a name="next-steps"></a>後續步驟

[Power BI 分頁報表中的子報表](subreports.md)

[檢視 Power BI 服務中的編頁報表](../consumer/paginated-reports-view-power-bi-service.md)

有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)
