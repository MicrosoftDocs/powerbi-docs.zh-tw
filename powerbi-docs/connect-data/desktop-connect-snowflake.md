---
title: 在 Power BI Desktop 中連接到 Snowflake 運算倉儲
description: 在 Power BI Desktop 中輕鬆連接並使用 Snowflake 運算倉儲
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 01/04/2021
LocalizationGroup: Connect to data
ms.openlocfilehash: 377ede2171a721a33aa0b70819ef511d721f2590
ms.sourcegitcommit: f7330dabb9cd8bce90bb2efec3e3273a11578f10
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2021
ms.locfileid: "99494435"
---
# <a name="connect-to-snowflake-in-power-bi-desktop"></a>在 Power BI Desktop 中連接到 Snowflake
在 Power BI Desktop 中，您可以連接至 **Snowflake** 運算倉儲並使用基礎資料，就像 Power BI Desktop 中的任何其他資料來源。 

## <a name="connect-to-a-snowflake-computing-warehouse"></a>連接至 Snowflake 運算倉儲
若要連接到 **Snowflake** 運算倉儲，請從 Power BI Desktop 的 [首頁] 功能區選取 [取得資料]。 從左側類別中選取 [資料庫]，然後您會看到 **Snowflake**。

![[取得資料] 對話方塊的螢幕擷取畫面，其中顯示 [Snowflake] 資料庫選取項目。](media/desktop-connect-snowflake/connect-snowflake-2b.png)

在顯示的 [Snowflake] 視窗中，將您的 Snowflake 伺服器名稱鍵入或貼上方塊中，然後選取 [確定]。 請注意，您可以選擇直接將資料 [匯入] Power BI 中，也可以使用 [DirectQuery]。 您可以深入了解[如何使用 DirectQuery](desktop-use-directquery.md)。 請注意，AAD SSO 僅支援 DirectQuery。

![[Snowflake] 對話方塊的螢幕擷取畫面，其中顯示已選取的 [匯入] 選項按鈕。](media/desktop-connect-snowflake/connect-snowflake-3.png)

收到提示時，請放入您的使用者名稱和密碼。

![[Snowflake] 認證提示的螢幕擷取畫面，其中顯示 [使用者名稱] 和 [密碼] 欄位。](media/desktop-connect-snowflake/connect-snowflake-4.png)

> [!NOTE]
> 一旦在特定 **Snowflake** 伺服器輸入使用者名稱與密碼，Power BI Desktop 便會在後續連接嘗試中使用與其相同的認證。 您可以前往 **[檔案] > [選像和設定] > [資料來源設定]** 修改認證。
> 
> 

如果您想要使用 [Microsoft 帳戶] 選項，則 Snowflake 端必須設定 Snowflake AAD 整合。 若要這麼做，請閱讀 [Snowflake 文件有關該主題](https://docs.snowflake.net/manuals/user-guide/oauth-powerbi.html#power-bi-sso-to-snowflake)的 "Getting Started" 一節。

![Snowflake 連接器中的 Microsoft 帳戶驗證類型。](media/desktop-connect-snowflake/connect-snowflake-6.png)


成功連接後，[導覽器] 視窗隨即出現，並顯示伺服器上可用的資料，您可以從中選取一或多個要匯入 **Power BI Desktop** 並在其中使用的項目。

![ODBC 錯誤 28000 導致連線失敗。](media/desktop-connect-snowflake/connect-snowflake-5.png)

您可以 **載入** 選取的資料表，將整個資料表帶入 **Power BI Desktop** 中，也可以 **編輯** 查詢以開啟 **查詢編輯器**，以便您篩選並縮小搜尋範圍到一組您想要使用的資料，然後將該組精簡的資料載入 **Power BI Desktop** 中。

## <a name="custom-roles"></a>自訂角色

雪花式連接器中的「自訂角色」支援目前只適用于基本驗證。 這將在不久的將來解決。

## <a name="next-steps"></a>後續步驟
您可以使用 Power BI Desktop 連接至各式各樣的資料。 如需有關資料來源的詳細資訊，請參閱下列資源︰

* [Power BI Desktop 是什麼？](../fundamentals/desktop-what-is-desktop.md)
* [Power BI Desktop 中的資料來源](desktop-data-sources.md)
* [使用 Power BI Desktop 合併資料並使其成形](desktop-shape-and-combine-data.md)
* [在 Power BI Desktop 中連接至 Excel 活頁簿](desktop-connect-excel.md)   
* [直接將資料輸入 Power BI Desktop 中](desktop-enter-data-directly-into-desktop.md)   
