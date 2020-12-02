---
title: 連接至 Power BI Desktop 中的資料
description: 連接至 Power BI Desktop 中的資料
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 01/21/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: a9fdb4e2ebd71d652c66220ad4a70473ef6dd764
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96411279"
---
# <a name="connect-to-data-sources-in-power-bi-desktop"></a>連接至 Power BI Desktop 的資料來源

透過 Power BI Desktop，您可以輕鬆地連接到持續擴展的資料世界。 如果您沒有 Power BI Desktop，您可以[下載](https://go.microsoft.com/fwlink/?LinkID=521662)並加以安裝。

Power BI Desktop 中有「各式各樣」  的可用資料來源。 下圖顯示如何藉由選取 [取得資料]   > [其他]   > [Web]  來連線至資料。

![從 Web 取得資料](media/desktop-connect-to-data/get-data-from-the-web.png)

## <a name="example-of-connecting-to-data"></a>連線到資料的範例

在本例中，我們將連接到 **Web** 資料來源。

想像您即將退休。 您想要住在有陽光充足、稅制合理且具備良好醫療照護的地方。 或者… 也許您是資料分析師，您想要該資訊來協助您的客戶，像是協助您的雨衣製造客戶以「經常」  下雨的地方為銷售目標。

無論如何，您都可以在下列 Web 資源中找到這些主題的相關有趣資料：

[https://www.bankrate.com/finance/retirement/best-places-retire-how-state-ranks.aspx](https://www.bankrate.com/finance/retirement/best-places-retire-how-state-ranks.aspx)

選取 [取得資料]   > [其他]   > [Web]  。 在 [從 Web]  中輸入位址。

![輸入 Web 來源位址](media/desktop-connect-to-data/connecttodata_3.png)

當您選取 [確定]  時，Power BI Desktop 的 [查詢]  功能就會開始運作。 Power BI Desktop 會連絡 Web 資源，[導覽器]  視窗會傳回它在該網頁找到的結果。 在本例中，Power BI Desktop 找到一個資料表和整份文件。 我們對資料表有興趣，因此我們從清單中選取該資料表。 [導覽器]  視窗會顯示預覽。

![導覽器中的資料預覽](media/desktop-connect-to-data/datasources_fromnavigatordialog.png)

此時，您可以從視窗的底部選取 [轉換資料]  ，先編輯查詢再載入資料表，或可直接載入資料表。

選取 [轉換資料]  以載入資料表並啟動 Power Query 編輯器。 隨即會顯示 [查詢設定]  窗格。 如果未顯示，請從功能區選取 [檢視]  ，然後選取 [查詢設定]  以顯示 [查詢設定]  窗格。 以下是其外觀。

![Power Query 編輯器與 [查詢設定]](media/desktop-connect-to-data/designer_gsg_editquery.png)

所有分數都是文字而非數字，我們需要使用數字。 沒問題。 只要以滑鼠右鍵按一下資料行標頭，然後選取 [變更類型]   > [整數]  就能加以變更。 若要選擇多個資料行，請先選取一個資料行，然後按住 Shift 鍵並選取其他相鄰的資料行，然後以滑鼠右鍵按一下資料行標頭，即可變更所有選取的資料行。 使用 Ctrl 鍵選擇不相鄰的資料行。

![將資料類型變更為整數](media/desktop-connect-to-data/designer_gsg_changedatatype.png)

在 [查詢設定]  中，[套用的步驟]  會反映任何所做變更。 當您對資料進行其他變更時，Power Query 編輯器會將這些變更記錄到 [套用的步驟]  區段中，您可以視需要在此進行調整、重新瀏覽、重新排列或刪除。

![套用的步驟](media/desktop-connect-to-data/designer_gsg_appliedsteps_changedtype.png)

資料表載入後仍可進行其他變更，但目前到此為止即可。 完成時，請從 [常用]  功能區選取 [關閉並套用]  ，Power BI Desktop 會套用這些變更並關閉 Power Query 編輯器。

![關閉並套用](media/desktop-connect-to-data/connecttodata_closenload.png)

載入資料模型之後，即可在 Power BI Desktop 的 [報表]  檢視中，將欄位拖曳到畫布上以開始建立視覺效果。

![將值拖曳至畫布](media/desktop-connect-to-data/connecttodata_dragontoreportview.png)

當然，這是具有單一資料連線的簡單模型。 大多數 Power BI Desktop 報表會連線到不同的資料來源、依您的需求成形並具有關聯性，以產生豐富的資料模型。

## <a name="next-steps"></a>後續步驟
您可以使用 Power BI Desktop 執行各種作業。 如需有關其功能的詳細資訊，請參閱下列資源：

* [Power BI Desktop 是什麼？](../fundamentals/desktop-what-is-desktop.md)
* [關於使用 Power BI Desktop 中的查詢編輯器](../transform-model/desktop-query-overview.md)
* [Power BI Desktop 中的資料來源](desktop-data-sources.md)
* [在 Power BI Desktop 中塑造及合併資料](desktop-shape-and-combine-data.md)
* [在 Power BI Desktop 中執行常見查詢工作](../transform-model/desktop-common-query-tasks.md)   

想要提供意見反應嗎？ 太棒了！ 使用 Power BI Desktop 的 [送出想法]  功能表項目或瀏覽 [Community Feedback](https://community.powerbi.com/t5/Community-Feedback/bd-p/community-feedback) (社群意見反應)。 我們期待您的留言！

![送出想法](media/desktop-connect-to-data/sendfeedback.png)
