---
title: 在 Power BI Desktop 中自訂工具提示
description: 使用拖放功能建立視覺效果的自訂工具提示
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-reports-dashboards
ms.topic: how-to
ms.date: 01/15/2020
LocalizationGroup: Create reports
ms.openlocfilehash: 18658937d1e53340f4bdd5075479bd2926f295bd
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96414200"
---
# <a name="customize-tooltips-in-power-bi-desktop"></a>在 Power BI Desktop 中自訂工具提示

工具提示很適合用來為視覺效果的資料點提供更多關聯式資訊和詳細資料。 下圖顯示套用至 Power BI Desktop 中圖表的工具提示。

![預設工具提示](media/desktop-custom-tooltips/custom-tooltips-1.png)

建立視覺效果時，預設的工具提示會顯示資料點的值與類別。 在許多情況下，自訂工具提示資訊很有用。 自訂工具提示為檢視視覺效果的使用者提供額外的上下文與資。 自訂工具提示可讓您指定額外的資料點，以當做工具提示的一部分顯示。

## <a name="how-to-customize-tooltips"></a>如何自訂工具提示

若要建立自訂工具提示，請在 [視覺效果]  窗格的 [欄位]  部分，將欄位拖曳到 [工具提示]  貯體，如下圖所示。 在下圖中，已將三個欄位放入 [工具提示]  貯體。

![新增工具提示欄位](media/desktop-custom-tooltips/custom-tooltips-2.png)

將工具提示新增到 [工具提示]  之後，當滑鼠暫留在視覺效果的資料點上時，就會顯示這些欄位的值。

![自訂工具提示](media/desktop-custom-tooltips/custom-tooltips-3.png)

## <a name="customizing-tooltips-with-aggregation-or-quick-measures"></a>使用彙總或快速量值來自訂工具提示

您可以透過選取彙總函式或「快速量值」  ，進一步自訂工具提示。 選取 [工具提示]  貯體中欄位旁邊的箭號。 然後，從可用選項中選取項目。

![含快速量值的工具提示](media/desktop-custom-tooltips/custom-tooltips-4.png)

您可以使用資料集中任何可用的欄位，透過許多方式自訂 [工具提示]，以便將資訊與見解快速傳遞給檢視儀表板或報表的使用者。
