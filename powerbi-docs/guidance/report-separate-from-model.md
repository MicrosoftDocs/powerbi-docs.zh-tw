---
title: 在 Power BI Desktop 中將報表與模型分開
description: 在 Power BI Desktop 中將報表與模型分開的指引。
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 04/11/2020
ms.openlocfilehash: 20e674765d2a908ff1952b0f316d125d0e3c5bd3
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99088296"
---
# <a name="separate-reports-from-models-in-power-bi-desktop"></a>在 Power BI Desktop 中將報表與模型分開

建立新 Power BI Desktop 解決方案時，其中一個您需要執行的首要工作是「取得資料」。 取得資料可能導致兩種截然不同的結果。 它可能：

- 建立與已發佈之模型的[即時連線](../connect-data/desktop-report-lifecycle-datasets.md)，此模型可能是 Power BI 資料集或裝載於遠端的 Analysis Services 模型。
- 開始新模型的開發，此模型可能是匯入、DirectQuery 或複合模型。

此文章與第二種案例相關。 其中提供有關報表與模型是否應合併成單一 Power BI Desktop 檔案的指引。

## <a name="single-file-solution"></a>單一檔案解決方案

當只有一個以模型為基礎的報表時，_單一檔案解決方案_ 可順利運作。 在此情況下，模型與報表可能都是同一人的工作成果。 我們將其定義為「個人 BI」  解決方案，但報表可以與其他人共用。 這類解決方案可代表角色範圍報表或業務挑戰的單次評量 — 通常描述為「臨機操作」  報表。

:::image type="content" source="media/report-separate-from-model/single-file-solution.png" alt-text="一個單一檔案包含由同一人所開發的模型與報表。" border="true":::

## <a name="separate-report-files"></a>個別的報表檔案

在下列情況下，將模型與報表開發分成個別的 Power BI Desktop 檔案是合理的：

- 資料模型製造者與報表作者為不同人。
- 已知模型將在現在或未來成為多個報表的來源。

:::image type="content" source="media/report-separate-from-model/separate-report-files.png" alt-text="PBIX 檔案有三個。第一個只包含模型。其他兩個只包含報表，且即時連線到 Power BI 服務中所裝載的模型。報表由不同人所開發。" border="true":::

資料模型製造者仍可使用 Power BI Desktop 報表製作體驗來測試及驗證其模型設計。 不過，在將其檔案發佈至 Power BI 服務之後，他們就應立即將報表自工作區中移除。 並且在每次重新發佈和覆寫資料集時，都必須記得移除報表。

### <a name="preserve-the-model-interface"></a>保留模型介面

有時，模型變更是不可避免的。 資料模型製造者必須小心，而不要破壞模型介面。 如果破壞介面，相關報表視覺效果或儀表板磚可能也會受到破壞。 損毀的視覺效果會顯示為錯誤，而可能導致報表作者或取用者受挫。 更糟的是，可能降低資料可信度。

因此，請謹慎管理模型變更。 可能的話，請避免下列變更：

- 重新命名資料表、資料行、階層、階層層級或量值。
- 修改資料行資料類型。
- 修改量值運算式，使其傳回不同的資料類型。
- 將量值移至不同的主資料表。 這是因為移動量值可能會破壞以量值主資料表名稱完整限定量值的報表範圍量值。 我們不建議您使用完整量值名稱來撰寫 DAX 運算式。 如需詳細資訊，請參閱[DAX：資料行和量值參考](dax-column-measure-references.md)。

新增資料表、資料行、階層、階層層級或量值是安全的，但有一種例外狀況：新量值名稱可能與報表範圍量值名稱相衝突。 為避免衝突，建議報表作者在其報表中定義量值時採用命名慣例。 他們可以在報表範圍的量值名稱前面加上底線或一些其他字元。

如果您必須對模型進行重大變更，建議您執行下列其中一個動作：

- [檢視 Power BI 服務中資料集的相關內容](../consumer/end-user-related.md)。
- 探索 Power BI 服務中的[資料譜系](../collaborate-share/service-data-lineage.md)檢視。

這兩個選項都可讓您快速識別所有相關的報表和儀表板。 資料譜系檢視可能是較佳的選擇，因為很容易查看每個相關成品的連絡人。 事實上，它是一個會開啟以連絡人為收件者之電子郵件訊息的超連結。

建議您連絡每個相關成品的擁有者，以讓他們知道任何已計畫的重大變更。 如此一來，他們就能做好準備來修正和重新發佈其報表，而有助於將停機時間和挫敗情況降到最低。

## <a name="next-steps"></a>後續步驟

如需本文的詳細資訊，請參閱下列資源：

- [從 Power BI Desktop 連線到 Power BI 服務中的資料集](../connect-data/desktop-report-lifecycle-datasets.md)
- [檢視 Power BI 服務中的相關內容](../consumer/end-user-related.md)
- [資料譜系](../collaborate-share/service-data-lineage.md)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com/)
