---
title: 重新整理建立自 Power BI Desktop 檔案的資料集 - 本機
description: 重新整理建立自本機磁碟上 Power BI Desktop 檔案的資料集
author: davidiseminger
ms.author: davidi
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 06/04/2019
LocalizationGroup: Data refresh
ms.openlocfilehash: d836c8d85915332c58032cf535194ca5ce803567
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96404011"
---
# <a name="refresh-a-dataset-created-from-a-power-bi-desktop-file-on-a-local-drive"></a>重新整理建立自本機磁碟上 Power BI Desktop 檔案的資料集

## <a name="whats-supported"></a>支援的項目有哪些？

在 Power BI 中，從 Power BI Desktop 檔案建立的資料集支援 [立即重新整理] 和 [排程重新整理]，這些檔案是從本機磁碟匯入，本機磁碟使用 [取得資料]/查詢編輯器連接下列任何資料來源並載入資料︰

### <a name="power-bi-gateway---personal"></a>Power BI Gateway - Personal

- Power BI Desktop 的 [取得資料] 和查詢編輯器都會顯示所有的線上資料來源。
- Power BI Desktop 的 [取得資料] 和查詢編輯器都會顯示所有的內部部署資料來源，但 Hadoop 檔案 (HDFS) 與 Microsoft Exchange 除外。

<!-- Refresh Data sources-->
[!INCLUDE [refresh-datasources](../includes/refresh-datasources.md)]

> [!NOTE]
> 必須安裝並執行閘道器，才能讓 Power BI 連接至內部部署資料來源並重新整理資料集。
>
>

您可以選取 [首頁] 功能區的 [重新整理]  ，在 Power BI Desktop 手動執行一次性的重新整理。 當您在這裡選取 [重新整理]  時，就會使用原始資料來源的更新資料重新整理「檔案」  模型中的資料。 這類的重新整理，完全位於 Power BI Desktop 應用程式本身，不同於 Power BI 中的手動或排程重新整理，所以請務必了解此差異。

![Refresh](media/refresh-desktop-file-local-drive/pbix-refresh.png)

當您從本機磁碟機匯入 Power BI Desktop 檔案時，模型資料和其他相關資訊都會載入 Power BI 服務的資料集內。 在 Power BI 服務 (而非 Power BI Desktop) 中，因為 Power BI 服務中的報表是以該資料集為基礎，所以您會想要重新整理該資料集的資料。 因為資料來源位於外部，所以您可以使用 [立即重新整理]  手動重新整理資料集，或您可以使用 [排程重新整理]  設定重新整理排程。

當您重新整理資料集時，Power BI 不會連接到本機磁碟機上的檔案來查詢更新資料。 它會使用在資料集的資訊，直接連接到資料來源，以查詢更新資料，然後載入資料集。

> [!NOTE]
> 此資料集內重新整理的資料不會同步回到本機磁碟機上的檔案。
>
>

## <a name="how-do-i-schedule-refresh"></a>我要如何排程重新整理？

當您設定重新整理排程時，Power BI 會直接連接到資料來源，以使用資料集中的連線資訊和認證來查詢更新資料，然後將更新的資料載入資料集。 此外，也會更新任何在 Power BI 服務中該資料集上的報表和儀表板視覺效果。

如需如何設定排程重新整理的詳細資訊，請參閱[設定排程重新整理](refresh-scheduled-refresh.md)。

## <a name="when-things-go-wrong"></a>發生錯誤時

如果發生錯誤，問題通常起因於 Power BI 無法登入資料來源，或資料集連接至內部部署資料來源時，閘道器離線。 請確認 Power BI 可以登入資料來源。 如果您用以登入資料來源的密碼已變更，或 Power BI 從資料來源登出，請務必嘗試在 [資料來源認證] 中再次登入您的資料來源。

請務必核取 [傳送重新整理失敗通知電子郵件給我]  。 您會想要立刻知道排定的重新整理是否失敗。

## <a name="troubleshooting"></a>疑難排解

有時候重新整理資料可能不會如預期執行。 這通常是閘道連線問題之故。 請參閱閘道疑難排解文章，以取得工具和已知的問題。

- [為內部部署資料閘道進行疑難排解](service-gateway-onprem-tshoot.md)
- [對 Power BI Gateway - Personal 進行疑難排解](service-admin-troubleshooting-power-bi-personal-gateway.md)

有其他問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
