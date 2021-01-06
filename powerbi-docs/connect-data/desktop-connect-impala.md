---
title: 在 Power BI Desktop 中連線至 Impala 資料庫
description: 在 Power BI Desktop 中輕鬆連接到 Impala 資料庫並加以使用
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 01/04/2021
LocalizationGroup: Connect to data
ms.openlocfilehash: a9d817dc3e34cae2f496136fe19353ba5b993c8a
ms.sourcegitcommit: 932f6856849c39e34229dc9a49fb9379c56a888a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97926418"
---
# <a name="connect-to-an-impala-database-in-power-bi-desktop"></a>在 Power BI Desktop 中連線至 Impala 資料庫
在 Power BI Desktop 中，您可以連線至 **Impala 資料庫** 並使用基礎資料，就像在 Power BI Desktop 中使用任何其他資料來源。

## <a name="connect-to-an-impala-database"></a>連接到 Impala 資料庫
若要連線到 **Impala** 資料庫，請執行下列步驟： 

1. 從 Power BI Desktop 的 [常用]  功能區選取 [取得資料]  。 

2. 從左側的類別中選取 [資料庫]  。 然後您會看到 [Impala]  。

    ![取得資料](media/desktop-connect-impala/connect_impala_2.png)

3. 在顯示的 [Impala]  視窗中，將您的 Impala 伺服器名稱鍵入或貼上到方塊中。 然後選取 [確定]  。 您可以將資料直接 [匯入]  到 Power BI，或使用 **DirectQuery**。 深入了解[如何使用 DirectQuery](desktop-use-directquery.md)。

    ![Impala 視窗](media/desktop-connect-impala/connect_impala_3a.png)

4. 出現提示時，輸入您的認證，或以匿名方式連線。 Impala 連接器支援匿名、基本 (使用者名稱 + 密碼) 和 Windows 驗證。

    ![Impala 連接器](media/desktop-connect-impala/connect_impala_4.png)

    > [!NOTE]
    > 一旦您放入特定 **Impala** 伺服器的使用者名稱和密碼，Power BI Desktop 便會在後續連線嘗試中使用那些相同的認證。 您可以前往 **[檔案] > [選像和設定] > [資料來源設定]** 修改認證。


5. 連線之後，[瀏覽]  視窗隨即出現並顯示伺服器上可用的資料。 從此資料選擇元素，將它們匯入到 **Power BI Desktop** 中並在其中使用。

    ![[導覽器] 視窗](media/desktop-connect-impala/connect_impala_5.png)

## <a name="considerations-and-limitations"></a>考量與限制
使用 **Impala** 連接器時，有幾項限制和考量必須注意：

* 內部部署資料閘道支援 Impala 連接器，使用三種支援的驗證機制中的任何一種。

## <a name="next-steps"></a>後續步驟
使用 Power BI Desktop 可以連線到許多不同的資料來源。 如需有關資料來源的詳細資訊，請參閱下列資源︰

* [Power BI Desktop 是什麼？](../fundamentals/desktop-what-is-desktop.md)
* [Power BI Desktop 中的資料來源](desktop-data-sources.md)
* [使用 Power BI Desktop 合併資料並使其成形](desktop-shape-and-combine-data.md)
* [在 Power BI Desktop 中連接至 Excel 活頁簿](desktop-connect-excel.md)   
* [直接將資料輸入 Power BI Desktop 中](desktop-enter-data-directly-into-desktop.md)   
