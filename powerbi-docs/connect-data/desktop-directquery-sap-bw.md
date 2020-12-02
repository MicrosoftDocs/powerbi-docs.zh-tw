---
title: Power BI 中的 DirectQuery 和 SAP Business Warehouse (BW)
description: 搭配 SAP Business Warehouse (BW) 使用 DirectQuery 時的考量
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 11/28/2018
LocalizationGroup: Connect to data
ms.openlocfilehash: 06824a11c2c186dd9ac199e8e9b8155d618b3a0d
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96405230"
---
# <a name="connect-to-sap-business-warehouse-by-using-directquery-in-power-bi"></a>在 Power BI 中使用 DirectQuery 連線到 SAP Business Warehouse
您可以使用 **DirectQuery** 直接連接到 **SAP Business Warehouse (BW)** 資料來源。 根據 SAP BW 的 OLAP/多維度本質，透過 SAP BW 的 DirectQuery 與透過關聯式來源 (例如 SQL Server) 的 DirectQuery 之間有許多重要差異。 這些差異摘要如下：

* 在透過關聯式來源的 **DirectQuery** 中有一組查詢 (如 [Get Data]\(取得資料) 或 [查詢編輯器] 對話方塊中所定義)，這些查詢會以邏輯方式定義欄位清單中可用的資料。 連接到 SAP BW 等 OLAP 來源時則「不同」。 相反地，使用 [Get Data]\(取得資料) 連接到 SAP 伺服器時，只要選取 InfoCube 或 BEx 查詢即可。 然後就會在欄位清單中提供所選 InfoCube/BEx 查詢的所有關鍵數據和維度。   
* 同樣地，連接到 SAP BW 時沒有 [查詢編輯器]。 選取 [編輯查詢] > [資料來源設定] 即可變更資料來源設定 (例如伺服器名稱)。 選取 [編輯查詢] > [管理參數] 即可變更任何參數的設定。
* 根據 OLAP 來源的獨特本質，除了加諸於 DirectQuery 的一般限制之外，還會套用其他限制 (適用於模型和視覺效果)。 本文稍後將說明這些限制。

此外，「請務必」了解 Power BI 不支援 SAP BW 的許多功能，而且由於 SAP BW 的公用介面本質，在許多重要情況下，透過 Power BI 查看的結果與使用 SAP 工具查看的結果不符。 本文稍後將說明這些限制。 您應該仔細檢閱這些限制和行為差異，以確保透過 Power BI 查看的結果，與 SAP 公用介面傳回的結果一樣經過正確解譯。  

> [!NOTE]
> 在 Power BI Desktop 的 2018 年 3 月更新之前，在 SAP BW 中使用 DirectQuery 的功能都是預覽版。 在預覽期間，意見反應和建議改善事項會提示對使用預覽版建立之報表有影響的變更。 既然已發行 SAP BW DirectQuery 正式發行版本 (GA)，您「必須」捨棄任何使用 SAP BW DirectQuery GA 預先版本建立的現有 (預覽式) 報表。 在使用 SAP BW DirectQuery GA 預先版本建立的報表中，這些 GA 預先版本報表在叫用重新整理時，會因為嘗試重新整理基礎 SAP BW Cube 已變更的中繼資料而發生錯誤。 請使用 GA 版本的 SAP BW DirectQuery，以空白報表重新建立這些報表。 

## <a name="additional-modeling-restrictions"></a>其他模型限制
在 Power BI 中使用 DirectQuery 連線到 SAP BW 時的其他主要模型限制如下：

* **不支援計算結果欄：** 已停用建立計算結果欄的功能。 也就是說，建立計算結果欄的群組和叢集將無法使用。
* **量值的其他限制：** 在可於量值中使用的 DAX 運算式上有其他限制，用以反映 SAP BW 所提供的支援層級。
* **不支援定義關聯性：** 無法在模型中定義外部 SAP 來源固有的關聯性及其他關聯性。
* **沒有資料檢視：** [資料檢視] 通常會顯示資料表中的詳細等級資料。 根據 SAP BW 等 OLAP 來源的本質，無法透過 SAP BW 使用此檢視。
* **資料行和量值的詳細資料是固定的：** 欄位清單中出現的資料行和量值清單由基礎來源決定，清單是固定的而且無法修改。 例如，您無法刪除資料行，也無法變更其資料類型 (不過可以重新命名)。
* **DAX 中的其他限制：** 可用於量值定義的 DAX 上還有其他限制，以反映來源中的限制。 例如，您無法對資料表使用彙總函式。

## <a name="additional-visualization-restrictions"></a>其他視覺效果限制
在 Power BI 中使用 DirectQuery 連接到 SAP BW 時的其他主要視覺效果限制如下：

* **沒有資料行彙總：** 您無法變更視覺效果上資料行的彙總，它一律為「不摘要」
* **已停用量值篩選：** 已停用量值篩選，以反映 SAP BW 所提供的支援。
* **複選及包含/排除：** 如果視覺效果上的資料點代表多個資料行的值，則會停用複選這些點的功能。 例如，假設有依國家/地區顯示銷售量的橫條圖並在圖例中含有類別，您無法選取 (USA, Bikes) 和 (France, Clothes) 點。 同樣地，您無法選取 (USA, Bikes) 點並將它從視覺效果中排除。 這兩項限制是為了反映 SAP BW 所提供的支援。

## <a name="support-for-sap-bw-features"></a>SAP BW 功能的支援
下表列出未完全支援或使用 Power BI 時會有不同行為的所有 SAP BW 功能。   

| 特徵 | 描述 |
| --- | --- |
| 本機計算 |BEx 查詢中所定義的本機計算，會變更透過 BEx Analyzer 等工具顯示的數字。 不過，這些計算不會反映在 SAP 透過公用 MDX 介面所傳回的數字中。 <br/> <br/> **因此，Power BI 視覺效果中所示的數字，不一定符合 SAP 工具中對應視覺效果中的數字。**<br/> <br/>  例如，從 BEx 查詢連接到查詢 Cube 以設定要累積的彙總 (也就是變動總合) 時，Power BI 會取得基底數字，並略過該設定。  分析師接著當然可在 Power BI 本機套用變動總合計算，但請務必小心謹慎處理未完成時的數字解譯方式。 |
| 彙總 |在某些情況下 (特別是處理多種貨幣時)，SAP 公用介面所傳回的彙總數字與 SAP 工具所示的數字不符。 <br/> <br/> **因此，Power BI 視覺效果中所示的數字，不一定符合 SAP 工具中對應視覺效果中的數字。** <br/> <br/> 例如，不同貨幣的總計在 BEx Analyzer 中會顯示為 "*"，但 SAP 公用介面會傳回該總計，而不會有任何資訊指出這是無意義的彙總數字。 因此，Power BI 會顯示此數字 (彙總 $、EUR 和 AUD 等)。 |
| 貨幣格式 |任何貨幣格式 (例如 $2,300 或 4000 AUD) 都不會反映在 Power BI 中。 |
| 測量單位 |測量單位 (例如 230 公斤) 不會反映在 Power BI 中。 |
| 索引鍵與文字 (短、中長、長) |對於 SAP BW 特性 (例如 CostCenter)，欄位清單會顯示單一資料行 [成本中心]。  使用該資料行會顯示預設文字。  藉由顯示隱藏的欄位，您也可能看到唯一名稱資料行 (傳回 SAP BW 所指派的唯一名稱且是唯一性基礎)。<br/> <br/>  無法使用索引鍵和其他文字欄位。 |
| 一個特性的多個階層 |在 **SAP** 中，一個特性可以有多個階層。 然後在 BEx Analyzer 等工具中，當查詢中包含一個特性時，使用者可以選取要使用的階層。 <br/> <br/> 在 **Power BI** 中，欄位清單中的各階層可視為相同維度上的不同階層。  不過，從相同維度上的兩個不同階層選取多個層級會導致 SAP 傳回空的資料。 |
| 不完全階層的處理方式 |![不完全內容的螢幕擷取畫面，其中顯示不完全階層的處理方式。](media/desktop-directquery-sap-bw/directquery-sap-bw_01.png) |
| 縮放係數/變換正負號 |在 SAP 中，關鍵數據可以有定義為格式選項的縮放係數 (例如 1000)，也就是說所有顯示都會依該係數縮放。 <br/> <br/> 同樣地，它可以有變換正負號的屬性集。 在 Power BI 中 (在視覺效果中或作為計算的一部分) 使用此關鍵數據會導致使用未縮放 (且未變換正負號) 的數字。 無法使用基礎縮放係數。 在 Power BI 視覺效果中，可在進行視覺格式設定的過程中控制顯示在軸 (K,M,B) 上的縮放單位。 |
| 其中的層級會動態出現/消失的階層 |一開始連接到 SAP BW 時會擷取階層的層級資訊，以產生欄位清單中的一組欄位。 這就是快取，如果層級集合變更，該組欄位在叫用 [重新整理] 之前都不會變更。 <br/> <br/> 這只可能發生在 **Power BI Desktop** 中。 發佈後，則無法在 Power BI 服務中叫用這類重新整理以反映層級的變更。 |
| 預設篩選 |BEx 查詢可以包含預設篩選，SAP BEx Analyzer 將自動套用這些篩選。 這些篩選不會公開，因此 Power BI 中的對等使用方式預設不會套用相同的篩選。 |
| 隱藏的關鍵數據 |BEx 查詢可以控制關鍵數據的可見度，而那些隱藏的數據將不會出現在 SAP BEx Analyzer 中。 透過公用 API 無法反映這點，因此這類隱藏的關鍵數據仍然會出現在欄位清單中。 不過，之後可在 Power BI 中隱藏這些數據。 |
| 數值格式 |任何數值格式 (十進位位數、小數點等) 都會自動反映在 Power BI 中。 不過，之後可在 Power BI 中控制這類格式。 |
| 階層版本控制 |SAP BW 允許維護不同版本的階層，例如 2007 版與 2008 版的成本中心階層。 由於公用 API 不會公開版本資訊，因此在 Power BI 中只會使用最新版本。 |
| 與時間相依的階層 |使用 Power BI 時，與時間相依的階層會依目前日期評估。 |
| 貨幣轉換 |SAP BW 支援根據 Cube 中保留的速率進行貨幣轉換。 公用 API 不會公開這類功能，因此無法在 Power BI 中使用。 |
| 排序次序 |您可以在 SAP 中定義特性的排序次序 (依文字或依索引鍵)。 此排序次序不會反映在 Power BI 中。 例如，月可能顯示為 “April”、“Aug” 等等。 <br/> <br/> 您無法在 Power BI 中變更此排序次序。 |
| 技術名稱 |在 [Get Data]\(取得資料) 中，會同時顯示特性/量值名稱 (描述) 和技術名稱。 欄位清單只會包含特性/量值名稱 (描述)。 |
| 屬性 |您無法在 Power BI 中存取特性的屬性。 |
| 終端使用者語言設定 |用來連接到 SAP BW 的地區設定會當作連接詳細資料的一部分來設定，而且不會反映最終報表取用者的地區設定。 |
| 文字變數 |SAP BW 允許欄位名稱包含變數的預留位置 (例如 "$YEAR$ Actuals")，之後會以選取的值取代該預留位置。 例如，如果選取 2016 年作為變數，BEx 工具中的欄位會顯示為 "2016 Actuals"。 <br/> <br/> Power BI 中的資料行名稱不會根據變數值變更，因此會顯示為 "$YEAR$ Actuals"。  不過，之後可在 Power BI 中變更此資料行名稱。 |
| 客戶結束變數 | 公用 API 不會公開「客戶結束」變數，因此 Power BI 不支援。 |
| 特性結構 | 基礎 SAP BW 來源中的任何特性結構，會導致在 Power BI 中公開的量值「爆發」。 例如，有 Sales 與 Costs 兩個量值，以及一個包含 Budget 和 Actual 的特性結構，則會公開四個量值：Sales.Budget、Sales.Actual、Costs.Budget、Costs.Actual。 |


## <a name="next-steps"></a>後續步驟
如需 DirectQuery 的詳細資訊，請參閱下列資源：

* [Power BI 中的 DirectQuery](desktop-directquery-about.md)
* [DirectQuery 支援的資料來源](power-bi-data-sources.md)
* [DirectQuery 和 SAP HANA](desktop-directquery-sap-hana.md)
