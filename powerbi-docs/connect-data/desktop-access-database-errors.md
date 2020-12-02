---
title: 解決 Power BI Desktop 中的 Access 和 .XLS 匯入問題
description: 解決 Power BI Desktop 和 Power Query 中匯入 Access 資料庫和 .XLS 試算表的問題
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 10/21/2019
LocalizationGroup: Troubleshooting
ms.openlocfilehash: f8d24c672fa3e9d5cda007e061eac8c4ea9c6d4c
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96406035"
---
# <a name="troubleshoot-importing-access-and-excel-xls-files-in-power-bi-desktop"></a>針對 Power BI Desktop 中的 Access 和 Excel .xls 檔案匯入問題進行疑難排解

在 Power BI Desktop 中，Access 資料庫和舊版的 Excel 活頁簿 (Excel 97-2003 的 .XLS 檔案類型) 都使用「Access 資料庫引擎」。 有三種常見的狀況會妨礙 Access 資料庫引擎正常運作。

## <a name="situation-1-no-access-database-engine-is-installed"></a>狀況 1：未安裝 Access 資料庫引擎

如果 Power BI Desktop 錯誤訊息指出未安裝 Access 資料庫引擎，則必須安裝符合 Power BI Desktop 版本的 Access 資料庫引擎版本 (32 位元或 64 位元)。 您可以從[下載頁面](https://www.microsoft.com/download/details.aspx?id=13255)安裝 Access 資料庫引擎。

>[!NOTE]
>如果安裝的 Access 資料庫引擎位元版本與 Microsoft Office 安裝的位元版本不同，則 Office 應用程式就不能使用 Access 資料庫引擎。

## <a name="situation-2-the-access-database-engine-bit-version-32-bit-or-64-bit-is-different-from-your-power-bi-desktop-bit-version"></a>狀況 2：Access 資料庫引擎位元版本 (32 位元或 64 位元) 和 Power BI Desktop 的位元版本不同

這種情況通常發生在安裝的 Microsoft Office 版本是 32 位元，而安裝的 Power BI Desktop 版本是 64 位元。 相反的情況也可能發生，無論哪一種都會發生位元版本不符的情況。 如果您使用 Microsoft 365 訂用帳戶，請參閱[狀況 3](#situation-3-trouble-using-access-or-xls-files-with-a-microsoft-365-subscription) 以了解不同的問題和解決方法。 下列解決方案的任何一項，都可以解決位元版本不符的錯誤︰

### <a name="solution-1"></a>解決方案 1

將 Power BI Desktop 版本變更為符合 Microsoft Office 安裝的位元版本。 

1. 若要變更 Power BI Desktop 的位元版本，請解除安裝 Power BI Desktop，然後再安裝符合 Office 安裝的 Power BI Desktop 版本。 

1. 若要選取 Power BI Desktop 版本，請在 Power BI Desktop 下載頁面上選取 [進階下載選項]。
   
   ![Power BI Desktop 下載頁面上的 [進階下載選項]](media/desktop-access-database-errors/desktop-access-errors-1.png)
   
1. 在出現的下載頁面上選擇您的語言，然後選取 [下載]  按鈕。 
 
1. 在出現的畫面上，如需 32 位元版本請選取 PBIDesktop.msi 旁邊的核取方塊，如需 64 位元版本請選取 PBIDesktop_x64.msi 旁邊的核取方塊。 

   下列螢幕擷取畫面中選取了 64 位元版本。
   
   ![選擇 Power BI Desktop 下載類型](media/desktop-access-database-errors/desktop-access-errors-2.png)
   
   >[!NOTE]
   >如果您使用 32 位元版的 Power BI Desktop，則可能會在建立超大型資料模型時發生記憶體不足的問題。

### <a name="solution-2"></a>解決方案 2

將 Microsoft Office 位元版本變更為符合 Power BI Desktop 安裝的位元版本：

1. 解除安裝 Microsoft Office

2. 安裝符合 Power BI Desktop 安裝的 Office 版本。

### <a name="solution-3"></a>解決方案 3

如果在嘗試開啟 .XLS 檔案 (Excel 97-2003 活頁簿) 時發生錯誤，您可以在 Excel 中開啟 .XLS 檔案，並將其另存為 .XLSX 檔案，以避免使用 Access 資料庫引擎。

### <a name="solution-4"></a>解決方案 4

如果前三個解決方案皆不可行，則您可以安裝兩個版本的 Access 資料庫引擎。 不過，這不是建議的因應措施。 雖然兩個版本都安裝會解決 Power Query for Excel 和 Power BI Desktop 的這個問題，但會造成任何預設自動使用先安裝之 Access 資料庫引擎位元版本的應用程式錯誤和問題。 

若要安裝 Access 資料庫引擎的兩種位元版本，請遵循下列步驟：

1. 從[下載頁面](https://www.microsoft.com/download/details.aspx?id=13255)安裝 Access 資料庫引擎的兩種位元版本。 

1. 使用 */passive* 參數來執行每個版本的 Access 資料庫引擎。 例如：

   ```console
   c:\users\joe\downloads\AccessDatabaseEngine.exe /passive

   c:\users\joe\downloads\AccessDatabaseEngine_x64.exe /passive
   ```

## <a name="situation-3-trouble-using-access-or-xls-files-with-a-microsoft-365-subscription"></a>狀況 3︰無法搭配 Microsoft 365 訂閱使用 Access 或 .XLS 檔案

如果您使用 Microsoft 365 訂閱，不論是 **Office 2013** 或 **Office 2016**，Access 資料庫引擎提供者都是註冊在虛擬登錄位置中，而「只能」由 Microsoft Office 處理序存取。 因此，混搭引擎 (負責執行非 Office 365 Excel 和 Power BI Desktop 且不是 Office 處理序) 無法使用 Access 資料庫引擎提供者。

若要解決這種狀況，請[下載並安裝 Access 資料庫引擎可轉散發套件](https://www.microsoft.com/download/details.aspx?id=13255)，其與 Power BI Desktop 安裝的位元版本相符。 如需位元版本的詳細資訊，請參閱本文稍早的章節。

## <a name="other-situations-that-can-cause-import-issues"></a>可能造成匯入問題的其他狀況

我們致力於將 Access 或 .XLS 檔案所發生的問題涵蓋在本文中。 如果您遇到沒有涵蓋在本文中的問題，請將問題的相關提問提交至 [Power BI 支援](https://powerbi.microsoft.com/support/)。 我們經常檢視可能會影響眾多客戶的問題，並將它們包含在我們的文章內。

