---
title: 針對 Power BI 服務中以文字傳回的巢狀值進行疑難排解
description: 了解如何修正使用不正確的資料來源隱私權設定時，巢狀值會轉換成字串的問題
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.custom: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: troubleshooting
ms.date: 6/4/2019
LocalizationGroup: Reports
ms.openlocfilehash: b34f6ae838122b0b2036a953296d5032bdfe76b8
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96401366"
---
# <a name="troubleshooting-nested-values-returned-as-text-in-power-bi-service"></a>針對 Power BI 服務中以文字傳回的巢狀值進行疑難排解

## <a name="cause"></a>原因

在過去，Power BI 報表有時會在 Desktop 中成功重新整理，但在 Power BI 服務中失敗，並出現「我們無法將值 "[Table]" 轉換成類型 Table」之類的錯誤。 此錯誤的原因之一是，當資料隱私權防火牆緩衝處理資料來源時，巢狀的非純量值 (例如資料表、記錄、清單和函式) 會自動轉換成文字值 (例如 “[Table]” 或 “[Record]”)。

現在，Power BI 服務支援設定隱私權等級 (或完全關閉防火牆)，因此可在 Power BI 服務中將[資料來源隱私權設定](https://powerbi.microsoft.com/blog/privacy-levels-for-cloud-data-sources/)設為非私人來避免這類錯誤。

從 6 月開始，當防火牆緩衝處理巢狀資料表/記錄/清單/等時，Power BI 不會以無訊息方式將這類值轉換成文字，而是會產生下列錯誤： 

`We cannot return a value of type Table in this context`

## <a name="effect-on-loadrefresh"></a>對載入/重新整理的影響

雖然變更的動機是防火牆緩衝處理，但其影響也會延伸到載入/重新整理。 為了解決防火牆緩衝處理行為，我們也必須變更將巢狀資料表/記錄/等載入 PQ for Excel 中 Power BI 模型和 Excel 資料模型的行為。 之前，巢狀資料表/記錄/等會以文字值 (例如 “[Table]” 或 “[Record]”) 載入。 現在會將其視為錯誤，而導致在載入的資料表中出現 Null 值，並在載入結果中遞增錯誤計數。

由於這些錯誤只會在載入/重新整理期間出現，因此不會顯示在 Power Query 編輯器中。

### <a name="before"></a>之前

- 載入/重新整理未發生任何錯誤
- 載入的資料表包含 “[Table]”、“[Record]” 等
 

### <a name="after"></a>之後

- 載入/重新整理發生錯誤
- 載入的資料表包含 NULL (而不是 “[Table]”、“[Record]” 等)
 

## <a name="resolution"></a>解決方法

您想要載入包含非純量值 (例如資料表、清單、記錄等) 的資料行嗎？
如果是，您應該能夠藉由移除資料行來消除錯誤。
如果您無法移除資料行，您應該能夠藉由新增自訂資料行，然後使用類似下面範例的邏輯來複寫舊行為：

`if [MyColumn] is table then "[Table]" else if [MyColumn] is record then "[Record]" else if [MyColumn] is list then "[List]" else if [MyColumn] is function then "[Function]" else [MyColumn]`

如果您將所有資料來源隱私權設定設為私人，此問題是否會在 Power BI Desktop 中重現？
如果是，您應該能夠在 Power BI 服務中將其[資料來源隱私權設定](https://powerbi.microsoft.com/blog/privacy-levels-for-cloud-data-sources/)設為非私人來解決錯誤。
