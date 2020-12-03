---
title: 關聯性疑難排解指導方針
description: 對模型關聯性問題進行疑難排解的指導方針。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 03/02/2020
ms.openlocfilehash: e8f76bf1e1947815176a1b24be2b758489093071
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418524"
---
# <a name="relationship-troubleshooting-guidance"></a>關聯性疑難排解指導方針

此文章以使用 Power BI Desktop 的資料模型製作人員為目標。 其能為您提供如何對在開發模型及報表時可能會遇到的特定問題進行疑難排解的指導方針。

[!INCLUDE [relationships-prerequisite-reading](includes/relationships-prerequisite-reading.md)]

## <a name="troubleshooting-checklist"></a>疑難排解檢查清單

將報表視覺效果設定為使用來自兩個 (或多個) 資料表的欄位，且其無法呈現正確的結果 (或是任何結果) 時，問題很可能與模型關聯性有關。

在此情況下，以下是您應該遵循的一般疑難排解檢查清單。 您可以逐步執行檢查清單，直到找出問題為止。

1. 將視覺效果切換為資料表或矩陣，或是開啟 [查看資料] 窗格，因為在可以看見查詢結果的情況下，您便能較輕鬆地對問題進行疑難排解
1. 如果有空白的查詢結果，請切換至 [資料] 檢視，並確認資料表中已載入資料列
1. 切換至 [模型] 檢視，您可以輕鬆查看關聯性並迅速判斷其屬性
1. 確認資料表之間存在關聯性
1. 確認基數屬性已正確設定；如果某個「多」端的資料行目前包含唯一的值，且錯誤地設定為「單」端，便代表那些屬性可能是錯誤的
1. 確認關聯性為作用中 (實線)
1. 確認篩選方向支援傳播 (解讀箭頭符號)
1. 確認相關聯的資料行是正確的，方法是選取關聯性或將游標暫留於其上方，以顯示相關聯的資料行
1. 確認相關聯的資料行資料類型是相同的，或至少是相容的；有可能會將文字資料行相關聯至整數資料行，但篩選將無法找到可以傳播的相符項目
1. 切換至 [資料] 檢視，並確認可以在相關聯的資料行中找到相符的值

## <a name="troubleshooting-guide"></a>疑難排解指南

以下是問題與可能解決方案的清單。

|問題|可能的原因|
|---------|---------|
|視覺效果未顯示任何結果|- 模型尚未載入資料<br />- 篩選內容中不存在任何資料<br />- 已強制執行資料列層級安全性<br />- 未在資料表之間傳播關聯性；請「遵循上述的檢查清單」 <br />- 已強制執行資料列層級安全性，但未啟用雙向關聯性的傳播；請參閱[使用 Power BI Desktop 的資料列層級安全性 (RLS)](../create-reports/desktop-rls.md)|
|視覺效果針對每個群組都顯示相同的值 |- 不存在關聯性<br />- 未在資料表之間傳播關聯性；請「遵循上述的檢查清單」 |
|視覺效果會顯示結果，但結果不正確|- 視覺效果的設定不正確<br />- 測量邏輯不正確<br />- 需要重新整理模型資料<br />- 來源資料不正確<br />- 關聯性資料行的關聯性不正確 (例如，將 **ProductID** 資料行對應至 **CustomerID**)<br />- 其為兩個 DirectQuery 資料表之間的關聯性，且關聯性的「單」端資料行包含重複的值|
|出現空白群組或交叉分析篩選器/篩選項目，且來源資料行沒有包含空白|- 其為一般關聯性，且「多」端資料行包含未儲存在「單」端資料行中的值；請參閱 [Power BI Desktop 中的模型關聯性 (一般關聯性)](../transform-model/desktop-relationships-understand.md#regular-relationships)<br />- 其為一般一對一關聯性，且相關聯的資料行包含空白；請參閱 [Power BI Desktop 中的模型關聯性 (一般關聯性)](../transform-model/desktop-relationships-understand.md#regular-relationships)<br />- 非作用中關聯性「多」端資料行存有空白，或具有未儲存在「單」端上的值|
|視覺效果遺漏資料|- 已套用不正確/未預期的篩選<br />- 已強制執行資料列層級安全性<br />- 其為受限關聯性，且相關聯的資料行中具有空白，或資料完整性問題；請參閱 [Power BI Desktop 中的模型關聯性 (受限關聯性)](../transform-model/desktop-relationships-understand.md#limited-relationships)<br />- 其為兩個 DirectQuery 資料表之間的關聯性；關聯性已設定為[採用參考完整性](../transform-model/desktop-relationships-understand.md#assume-referential-integrity)，但有資料完整性問題 (相關聯的資料行中具有不相符的值)|
|未正確強制執行資料列層級安全性|- 未在資料表之間傳播關聯性；請「遵循上述的檢查清單」 <br />- 已強制執行資料列層級安全性，但未啟用雙向關聯性的傳播；請參閱[使用 Power BI Desktop 的資料列層級安全性 (RLS)](../create-reports/desktop-rls.md)|
|||

## <a name="next-steps"></a>後續步驟

如需本文的詳細資訊，請參閱下列資源：

- [Power BI Desktop 中的模型關聯性](../transform-model/desktop-relationships-understand.md)
- 有任何問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com/)
