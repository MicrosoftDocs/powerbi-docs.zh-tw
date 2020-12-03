---
title: 進行概念證明以移轉到 Power BI
description: 在移轉到 Power BI 時進行概念證明的指導方針。
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 08/20/2020
ms.openlocfilehash: 77174da7fd47470974a292ba98f6b50c268b04fd
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96419122"
---
# <a name="conduct-proof-of-concept-to-migrate-to-power-bi"></a>進行概念證明以移轉到 Power BI

本文說明 **階段 3**，其涉及在移轉到 Power BI 時，進行概念證明 (POC)，儘早降低風險及解決未知問題。

:::image type="content" source="media/powerbi-migration-proof-of-concept/migrate-to-powerbi-stage-3.png" alt-text="顯示 Power BI 移轉階段的影像。本文的重點在於階段 3。":::

> [!NOTE]
> 如需上圖的完整說明，請參閱 [Power BI 移轉概觀](powerbi-migration-overview.md)。

階段 3 的焦點在於儘早解決未知問題及降低風險。 技術 POC 有助於驗證假設。 其可以用互動方式配合解決方案部署規劃進行 (如[階段 2](powerbi-migration-planning.md) 所述)。

此階段的輸出是縮小範圍的 Power BI 解決方案，可解決初始開啟的問題，並準備好進行[階段 4](powerbi-migration-create-validate-content.md) 的額外工作，使其成為實際執行就緒狀態。

> [!IMPORTANT]
> 我們不打算將 POC 視為一次性的工作。 相反地，我們預期在實際執行就緒的解決方案中，視 POC 為早期重複項目。 在您的組織中，您可能會將此活動視為原型、試驗、模型、快速入門或最簡可行產品 (MVP)。 您不一定要進行 POC，甚至能以非正式方式執行。

> [!TIP]
> 本文中討論的大部分主題也適用於標準 Power BI 實作專案。 當您的組織對 Power BI 更有經驗後，POC 的需求也會降低。 然而，因為 Power BI 的快速發行步調與持續引進的新功能，您可能會為了學習目的而定期進行技術 POC。

## <a name="set-poc-goals-and-scope"></a>設定 POC 目標與範圍

當進行 POC 時，請專注於下列目標：

- 請確認有關功能運作方式的假設。
- 比較 Power BI 與舊版 BI 平台兩者在運作方式的差異，進行初步了解。
- 尋求主題專家來驗證對特定需求的初步了解。
- 建立具有實際資料的小型資料集，以了解及偵測資料結構、關聯性、資料類型或資料值的任何問題。
- 試驗並驗證模型計算所使用的 [DAX 語法](/dax/)運算式。
- 使用閘道 (若其為閘道來源) 測試資料來源連線。
- 使用閘道 (若其為閘道來源) 測試資料重新整理。
- 確認安全性設定，包含適用時的資料列層級安全性。
- 以版面配置與外觀決策進行實驗。
- 確認 Power BI 服務中的所有功能都如預期般運作。

POC 範圍取決於未知之處，或必須向同事驗證哪些目標。 若要降低複雜性，以範圍而言，請盡可能使 POC 更為精確。

通常在移轉時，因為有現行的解決方案能著手，所以需求已經很熟悉。 然而，取決於要進行的改善範圍或現有 Power BI 技能，POC 仍然會提供重要價值。 此外，具有取用者意見反應的快速原型設計可能適用於快速釐清需求，特別是在進行增強功能的情況下。

> [!IMPORTANT]
> 即使 POC 只包含資料的子集，或只包含有限的視覺效果，從開始到完成都加以採用是很重要的。 也就是說，從 Power BI Desktop 的開發，到 Power BI 服務中開發工作區的部署。 這是徹底達成 POC 目標的唯一方法。 尤其是當 Power BI 服務必須傳遞您之前未曾用過的重要功能時，例如使用單一登入的 DirectQuery 資料集。 在進行 POC 期間，把您的心思放在不太確定或是需要向其他人確認的部分。

## <a name="handle-differences-in-power-bi"></a>處理 Power BI 中的差異

Power BI 可用作 _模型工具_ 或作為 _報表工具_。 模型解決方案涉及開發資料模型，而報表解決方案則會連線至已部署的資料模型。

因為 Power BI 擁有極大的彈性，所以某些層面可能與您正在進行移轉的舊版 BI 平台截然不同。

### <a name="consider-redesigning-the-data-architecture"></a>請考慮重新設計資料架構

若您要從具有自身語意層的舊版 BI 平台進行移轉，則建立匯入資料集可能是個好選項。 Power BI 函式最適合使用[星型結構描述](star-schema.md)資料表設計。 因此，若舊版的語意層並非星型結構描述，則可能需要進行重新設計，才能完全受惠於 Power BI。 致力於定義遵守星狀結構描述設計原則的語意層 (包括關聯性、常用的量值，以及易記的組織術語)，作為絕佳的自助報表作者起點。

若您要從舊版 BI 平台進行移轉 (其報表會使用 SQL 查詢或預存程式來參考關聯式資料來源)，而且若您打算在 [DirectQuery 模式](../connect-data/desktop-use-directquery.md)中使用 Power BI，您可能可以達成接近資料模型的一對一轉移。

> [!CAUTION]
> 若您看到很多個組成單一匯入資料表的 Power BI Desktop 檔案建立，通常是設計不夠完善的指標。 若您注意到此情況，請調查使用[星型結構描述](star-schema.md)設計所建立的[共用資料集](../connect-data/service-datasets-across-workspaces.md)是否可以達成更好的結果。

### <a name="decide-how-to-handle-dashboard-conversions"></a>決定如何處理儀表板轉換

在 BI 產業中，儀表板是視覺效果的集合，可以在單一頁面上顯示關鍵計量。 然而，在 Power BI 中，儀表板代表的是特定的視覺效果功能，只能在 Power BI 服務中建立。 從舊版 BI 平台移轉儀表板時，您有兩個選擇：

1. 舊版儀表板可以重新建立為 Power BI _報表_。 大部分報表都會使用 Power BI Desktop 建立。 編頁報表與 Excel 報表也是替代選項。
2. 舊版儀表板可以重新建立為 Power BI _儀表板_。 [儀表板](../fundamentals/service-basic-concepts.md#dashboards)是 Power BI 服務的視覺效果功能。 儀表板視覺效果通常是透過釘選一或多個報表中的視覺效果、問與答，或快速見解來建立。

> [!TIP]
> 因為儀表板是 Power BI 內容類型，所以請避免在報表或儀表板名稱中使用 _儀表板_ 一詞。

### <a name="focus-on-the-big-picture-when-recreating-visuals"></a>重新建立視覺效果時，專注於整體情形

每個 BI 工具都有其優勢與專長領域。 基於此原因，您在舊版 BI 平台中所依賴的報表視覺效果，在 Power BI 中可能沒有接近的樣式。

重新建立報表視覺效果時，可以把更多焦點擺在報表所顯現的巨觀業務問題上。 如此一來，便能輕輕鬆鬆地完全複製每個視覺效果設計。 雖然內容取用者在使用移轉的報表時很注重一致性，但小心別花太多時間在瑣碎細節的爭論上。

## <a name="next-steps"></a>後續步驟

在 [Power BI 移轉系列的下一篇文章](powerbi-migration-create-validate-content.md)中了解階段 4，這與移轉到 Power BI 時建立並驗證內容相關。

其他實用資源包括：

- [Microsoft BI 轉換](center-of-excellence-microsoft-business-intelligence-transformation.md)
- [規劃 Power BI 企業部署白皮書](https://aka.ms/PBIEnterpriseDeploymentWP) (英文)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com/)

經驗豐富的 Power BI 合作夥伴可協助您的組織成功進行移轉程序。 若要與 Power BI 合作夥伴交流，請造訪 [Power BI 合作夥伴入口網站](https://powerbi.microsoft.com/partners/)。
