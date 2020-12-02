---
title: 在 Power BI 中使用 SAP HANA
description: 在 Power BI 中使用 SAP HANA
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 01/15/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: 708a4439262111954012c944a464dd8e59db8068
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96404448"
---
# <a name="connect-to-sap-hana-databases-in-power-bi"></a>在 Power BI 中連線到 SAP HANA 資料庫

使用 Power BI Desktop，您現在可以存取 *SAP HANA* 資料庫。 若要使用 SAP HANA，您必須在本機用戶端電腦安裝 SAP HANA ODBC 驅動程式，以便 Power BI Desktop SAP HANA 資料連線正常運作。 您可以從 [SAP 開發工具](https://tools.hana.ondemand.com/#hanatools)下載 SAP HANA Client 工具，其中包含必要的 ODBC 驅動程式。 或者，您也可以從 [SAP 軟體下載中心](https://support.sap.com/en/my-support/software-downloads.html)取得此檔案。 在軟體入口網站中，搜尋適用於 Windows 電腦的 *SAP HANA CLIENT*。 由於 SAP 軟體下載中心經常變更其結構，因此未提供瀏覽該網站的更具體指導方針。

若要連線至 SAP HANA 資料庫，請選取 [取得資料]  ，選擇 [資料庫]   > [SAP HANA 資料庫]  ，然後選取 [連線]  ：

![SAP HANA 資料庫，[取得資料] 對話方塊，Power BI Desktop](media/desktop-sap-hana/sap-hana-1.png)

當您連線至 SAP HANA 資料庫時，請指定伺服器名稱。 然後，在下拉式清單和輸入方塊中指定連接埠。

在此版本中，Power BI Desktop 和 Power BI 服務支援 [DirectQuery](desktop-directquery-sap-hana.md) 模式中的 SAP HANA。 您可以將在 DirectQuery 模式中使用 SAP HANA 的報表發佈並上傳至 Power BI 服務。 如果不在 DirectQuery 模式中使用 SAP HANA，您也可以將報表發佈並上傳至 Power BI 服務。

## <a name="supported-features-for-sap-hana"></a>SAP HANA 的支援功能

此版本包含許多 SAP HANA 的功能，如下列清單所示：

* 適用於 SAP HANA 的 Power BI 連接器使用 SAP ODBC 驅動程式來提供最佳使用者體驗。

* SAP HANA 同時支援 [DirectQuery] 和 [匯入] 選項。

* Power BI 支援 HANA 資訊模型 (例如分析和計算檢視)，並已將瀏覽最佳化。

* 透過 SAP HANA，您也可以使用直接 SQL 功能連線至資料列和資料行資料表。

* Power BI 包含 HANA 模型的最佳化瀏覽。

* Power BI 支援 SAP HANA 變數和輸入參數。

* Power BI 支援以 HDI 容器為基礎的計算檢視。

  * 以 HDI 容器為基礎的計算檢視支援已於 2019 年 8 月所發行 Power BI Desktop 中公開預覽。 若要存取 Power BI 中以 HDI 容器為基礎的計算檢視，請確定您要與 Power BI 搭配使用的 HANA 資料庫使用者具有權限，可存取儲存您所要存取檢視的 HDI 執行階段容器。 若要授與此存取權，請建立可存取您 HDI 容器的角色。 然後將此角色指派給您將與 Power BI 搭配使用的 HANA 資料庫使用者。 (就像平常一樣，此使用者也必須具有在 \_SYS\_BI 結構描述中讀取系統資料表的權限。)如需如何建立和指派資料庫角色的詳細指示，請參閱官方 SAP 文件。 [此 SAP 部落格文章](https://blogs.sap.com/2018/01/24/the-easy-way-to-make-your-hdi-container-accessible-to-a-classic-database-user/)可能是不錯的起點。

  * 針對將 HANA 變數附加至以 HDI 為基礎的計算檢視目前有一些限制。 這些限制是因為 HANA 端的錯誤。
  
    首先，您無法將 HANA 變數套用至以 HDI 容器為基礎計算檢視的共用資料行。 若要修正這項限制，請升級至 HANA 2 37.02 版和更新版本，或升級至 HANA 2 42 版和更新版本。 其次，變數和參數的多重輸入預設值目前不會在 Power BI UI 中顯示。 SAP HANA 中的錯誤會造成這項限制，但是 SAP 尚未公告修正。

## <a name="limitations-of-sap-hana"></a>SAP HANA 的限制

使用 SAP HANA 也會有一些限制，如下所示：

* NVARCHAR 字串會截斷成 4000 個 Unicode 字元的最大長度。
* 不支援 SMALLDECIMAL。
* 不支援 VARBINARY。
* 有效日期介於 1899/12/30 到 9999/12/31 之間。
* 因為 Excel 活頁簿會在目前時間重新整理，所以目前不支援使用 SSO 進行 SAP HANA 重新整理。 若要重新整理 Power BI 中的資料，您可使用具有 SAP Hana SSO 的 Power BI 報表。

## <a name="next-steps"></a>後續步驟

如需 DirectQuery 和 SAP HANA 的詳細資訊，請參閱下列資源：

* [DirectQuery 和 SAP HANA](desktop-directquery-sap-hana.md)
* [使用 Power BI 的 DirectQuery](desktop-directquery-about.md)
* [Power BI 資料來源](power-bi-data-sources.md)
* [啟用 SAP HANA 的加密](desktop-sap-hana-encryption.md)
