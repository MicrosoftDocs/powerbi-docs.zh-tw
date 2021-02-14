---
title: 針對 Power BI 從檔案取得資料
description: 了解如何從 Excel、Power BI Desktop 和 CSV 檔案取得資料並放入 Power BI
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 05/08/2019
LocalizationGroup: Data from files
ms.openlocfilehash: 2ed532986dd31e97e535f27d70c9f5cfd8c66fd5
ms.sourcegitcommit: 24887643bd3e1b3749ce325dc0ae407432d7fee4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100489869"
---
# <a name="get-data-from-files-for-power-bi"></a>針對 Power BI 從檔案取得資料
![Excel、Power BI Desktop 與 CSV 圖示](media/service-get-data-from-files/file_icons.png)

在 Power BI 中，您可以連接到或匯入三種檔案類型的資料和報表。

* Microsoft Excel (.xlsx 或 .xlsm)
* Power BI Desktop (.pbix)
* 逗點分隔值 (.csv)

## <a name="what-does-get-data-from-a-file-really-mean"></a>從檔案取得資料真正所指為何？
您在 Power BI 中瀏覽的資料來自於資料集。 但若要有資料集，您必須先取得一些資料。 在本文中，我們把重點放在從檔案取得資料。

為了進一步了解資料集的重要性，以及如何為資料集取得資料，就讓我們以汽車為例。 當您坐在車內查看儀表板時， 就像是坐在電腦前查看 Power BI 的儀表板。 儀表板會顯示汽車的所有性能：引擎迴轉有多快、溫度、目前的排檔、車速等等。

在 Power BI 中，資料集就像是車內的引擎。 資料集提供 Power BI 儀表板中所顯示的資料、度量和資訊。 您的引擎 (或資料集) 當然需要燃料，而在 Power BI 中，該燃料就是資料。 您的車子具備可將汽油提供給引擎的油箱。 在 Power BI 中也是一樣，您需要內含資料的油箱，以將資料提供給資料集。 在本例中，該油箱是 Power BI Desktop 檔案、Excel 活頁簿檔案或 .CSV 檔案。

我們可以更進一步說明。 車內的油箱必須加滿汽油。 Power BI Desktop、Excel 或 .CSV 檔案的汽油是來自其他資料來源的資料。 我們從其他資料來源取得資料並放入 Excel、Power BI Desktop 或 .CSV 檔案。 如果它是 Excel 活頁簿或 .CSV 檔案，我們可以手動輸入多列資料。 或者，我們可以連接到外部資料來源，以查詢資料並載入我們的檔案。 一旦檔案具有一些資料，我們就能將其放入 Power BI 作為資料集。

> [!NOTE]
> Excel 活頁簿中的資料必須在資料表中，或在資料模型中，Power BI 才能將其匯入。
> 
> 

## <a name="where-your-file-is-saved-makes-a-difference"></a>檔案的儲存位置會形成差異
**本機** - 如果您將檔案儲存到電腦上的本機磁碟或組織中的其他位置，您可以從 Power BI 將檔案「匯入」Power BI。 您的檔案實際上會保留在本機磁碟，因此不是真的將整個檔案匯入 Power BI。 真正發生的情況是在 Power BI 網站中建立新的資料集，並將資料和資料模型 (在某些情況下) 載入資料集。 如果您的檔案有任何報表，這些報表會顯示在 Power BI 網站的 [報表] 下。

**Onedrive-商務** –如果您有商務用 onedrive，並使用您用來登入 Power BI 的相同帳戶進行登入，則這是在 Excel、Power BI Desktop 或中保持工作最有效的方式。CSV 檔案和您的資料集、報表和儀表板 Power BI 同步。由於 Power BI 和 OneDrive 都在雲端中，Power BI 每隔一小時就會連接到 OneDrive 上的檔案。 如果發現任何變更，便會自動更新 Power BI 中的資料集、報表和儀表板。

**OneDrive - 個人** - 如果您將檔案儲存到自己的 OneDrive 帳戶，則可以利用許多與使用商務用 OneDrive 相同的優點。 最大的差異是當您第一次連接到檔案時 (使用 [取得資料] > [檔案] > [OneDrive - 個人])，需要使用 Microsoft 帳戶登入 OneDrive，這通常與用來登入 Power BI 的帳戶不同。 當您使用 Microsoft 帳戶登入 OneDrive 時，請務必選取 [讓我保持登入] 選項。 如此一來，Power BI 每隔約一小時就會連接到您的檔案，以確保您在 Power BI 中的資料集保持同步。

**SharePoint 小組網站** - 將 Power BI Desktop 檔案儲存到 SharePoint - 小組網站與儲存到商務用 OneDrive 大致相同。 最大的差異是從 Power BI 連接到檔案的方式。 您可以指定 URL 或連接到根資料夾。

## <a name="ready-to-get-started"></a>準備開始使用了嗎？
請參閱下列文章，以深入了解如何將檔案放入 Power BI。

* [從 Excel 活頁簿檔案取得資料](service-excel-workbook-files.md)
* [從 Power BI Desktop 檔案取得資料](service-desktop-files.md)
* [從逗點分隔值檔案取得資料](service-comma-separated-value-files.md)

