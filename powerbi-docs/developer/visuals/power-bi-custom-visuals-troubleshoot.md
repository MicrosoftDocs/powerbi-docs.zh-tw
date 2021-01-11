---
title: 取得更佳的內嵌式 BI 見解：在 Power BI 內嵌式分析中，針對開發 Power BI 視覺效果的問題進行疑難排解
description: 本文探討您開發或建立自訂 Power BI 視覺效果時，可能會遇到的幾個常見問題。 使用 Power BI 內嵌式分析，取得更佳的內嵌式 BI 見解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: troubleshooting
ms.date: 11/06/2018
ms.openlocfilehash: 440bb6648dca1eaa85b697a10e9fd41180c66d7e
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97888090"
---
# <a name="troubleshoot-power-bi-visuals"></a>疑難排解 Power BI 視覺效果

## <a name="debug"></a>偵錯

**找不到 pbiviz 命令 (或類似的錯誤)**

當您在終端機的命令列中執行 `pbiviz` 時，應該會看到說明畫面。 如果未顯示，表示安裝有誤。 請確定您至少已安裝 NodeJS 4.0 版。

**在 [視覺效果] 索引標籤中找不到偵錯視覺效果**

[視覺效果] 索引標籤中的偵錯視覺效果功能，看起來像個提示圖示。

![視覺效果選取項目](media/power-bi-custom-visuals-troubleshoot/powerbi-developer-visual-selection.png)

如果未顯示，請確定您已在 Power BI 設定中加以啟用。

> [!NOTE]
> 偵錯視覺效果功能目前僅可在 Power BI 服務中使用；Power BI Desktop 或行動裝置應用程式皆尚未提供。 封裝的視覺效果仍可在每個地方運作。

**聯繫不到視覺效果伺服器**

在終端機命令列中輸入 `pbiviz start` 命令，從視覺效果專案的根目錄執行視覺效果伺服器。 如果伺服器未在執行中，很可能是您未正確安裝 SSL 憑證。

如果您有任何問題或意見，歡迎連絡 Power BI 視覺效果支援小組：pbicvsupport@microsoft.com。

## <a name="next-steps"></a>後續步驟

如需詳細資訊，請前往 [Power BI 視覺效果常見問題集](power-bi-custom-visuals-faq.md#organizational-power-bi-visuals)。