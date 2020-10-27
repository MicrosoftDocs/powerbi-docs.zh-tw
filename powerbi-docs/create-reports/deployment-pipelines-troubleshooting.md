---
title: 部署管線疑難排解
description: 針對 Power BI 中的部署管線進行疑難排解
author: KesemSharabi
ms.author: kesharab
ms.topic: troubleshooting
ms.service: powerbi
ms.subservice: powerbi-service
ms.date: 09/15/2020
ms.openlocfilehash: 0a90c03c516b64e5a0a81c6a2bbdf0049d48b76f
ms.sourcegitcommit: be0971576a3f1af7a064371c9cf27dd462dfca82
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2020
ms.locfileid: "92080246"
---
# <a name="deployment-pipelines-troubleshooting"></a>部署管線疑難排解

使用此文章來針對部署管線中的問題進行疑難排解。

## <a name="general"></a>一般

### <a name="whats-deployment-pipelines-in-power-bi"></a>什麼是 Power BI 中的部署管線

若要了解 Power BI 中的部署管線，請參閱[部署管線概觀](deployment-pipelines-overview.md)。

### <a name="how-do-i-get-started-with-deployment-pipelines"></a>我要如何開始使用部署管線？

使用[開始使用指示](deployment-pipelines-get-started.md)開始使用部署管線。

### <a name="why-cant-i-see-the-deployment-pipelines-button"></a>為什麼我看不到 [部署管線] 按鈕？

如果不符合下列條件，則您無法看到 [部署管線] 按鈕。

* 您是 Power BI [Pro 使用者](../admin/service-admin-purchasing-power-bi-pro.md)

* 您所屬的組織有 Premium 容量

* 只能將工作區指派給單一管線

* 您是新工作區的管理員

### <a name="why-cant-i-see-the-pipeline-stage-tag-in-my-workspace"></a>為什麼無法在 [我的工作區] 中看到管線階段標籤

部署管線會在指派給管線的工作區中顯示管線階段標籤。 「開發」和「測試」階段的標籤一律可見。 然而，如果您具有[管線的存取權](deployment-pipelines-process.md#user-with-pipeline-access)，或者身為[工作區管理員](deployment-pipelines-process.md#workspace-admin)，您只能看見「生產」標籤。

> [!div class="mx-imgBorder"]
> ![生產環境管線工作區中生產標籤的螢幕擷取畫面。](media/deployment-pipelines-troubleshooting/production-tag.png)

## <a name="licensing"></a>授權

### <a name="what-licenses-are-needed-to-work-with-deployment-pipelines"></a>需要哪些授權才能使用部署管線？

若要使用部署管線，您必須是具有 [Premium 容量](../admin/service-premium-what-is.md)的 [Pro 使用者](../admin/service-admin-purchasing-power-bi-pro.md)。 如需詳細資訊，請參閱[存取部署管線](deployment-pipelines-get-started.md#accessing-deployment-pipelines)。

### <a name="what-type-of-capacity-can-i-assign-to-a-workspace-in-a-pipeline"></a>我可以將哪些類型的容量指派給管線中的工作區？

部署管線中的所有工作區都必須位於專用容量內，管線才能正常運作。 不過，您可以針對管線中的不同工作區使用不同的容量。 您也可以在相同管線中的不同工作區使用不同的容量類型。

若要進行開發及測試，您可以針對每個使用者將 A 或 EM 容量與 Pro Power BI 帳戶一起使用。

針對生產環境工作區，您需要 P 容量。 如果您是透過內嵌應用程式發佈內容的 ISV，您也可以使用 A 或 EM 容量來進行生產。

## <a name="technical"></a>技術

### <a name="why-cant-i-see-all-my-workspaces-when-i-try-to-assign-a-workspace-to-a-pipeline"></a>當我嘗試將工作區指派給管線時，為什麼看不到我的所有工作區？

若要將工作區指派給管線，必須符合下列條件：

* 工作區是[新的工作區體驗](../collaborate-share/service-create-the-new-workspaces.md)

* 您是工作區的管理員

* 工作區未指派至任何其他管線

* 工作區位於 [Premium 容量](../admin/service-premium-what-is.md)上

不符合這些條件的工作區不會顯示在您可以選取的工作區清單中。

### <a name="how-can-i-assign-workspaces-to-all-the-stages-in-a-pipeline"></a>如何將工作區指派給管線中的所有階段？

您可以為每個管線指派一個工作區。 將工作區指派給管線之後，您就可以將其部署到下一個管線階段。 第一次部署時，會使用來源階段中的項目複本來建立新的工作區。 系統會保留所複製項目的關聯性。 如需詳細資訊，請參閱如何[將工作區指派給部署管線](deployment-pipelines-get-started.md#step-2---assign-a-workspace-to-a-deployment-pipeline)。

### <a name="why-did-my-first-deployment-fail"></a>為什麼我的第一次部署會失敗？

您的第一次部署可能因為許多原因而失敗。 下表列出其中一些原因。

|Error  |動作  |
|---------|---------|
|您沒有 [Premium 容量權限](deployment-pipelines-process.md#creating-a-premium-capacity-workspace)。     |若要取得 Premium 容量權限，請要求容量管理員將您的工作區新增至容量，或要求容量的指派權限。 工作區在容量中之後，請重新部署。        |
|您沒有工作區權限。     |若要進行部署，您必須是工作區成員。 請要求您的工作區管理員授與您適當的權限。         |
|您的 Power BI 管理員已停用工作區的建立。     |請連絡您的 Power BI 管理員以尋求支援。         |
|您的工作區不是[新的工作區體驗](../collaborate-share/service-create-the-new-workspaces.md)。     |在新的工作區體驗中建立您的內容。 如果您的內容位於傳統工作區中，您可以將其[升級](../collaborate-share/service-upgrade-workspaces.md)為新的工作區體驗。         |
|您正在使用[選擇性部署](deployment-pipelines-get-started.md#selective-deployment)，而不是選取內容的資料集。     |請執行下列其中一項： </br></br>取消選取連結至資料集的內容。 未選取的內容 (例如報表或儀表板) 將不會複製到下一個階段。 </br></br>選取連結至所選內容的資料集。 您的資料集將會複製到下一個階段。         |

### <a name="im-getting-a-warning-that-i-have-unsupported-artifacts-in-my-workspace-when-im-trying-to-deploy-how-can-i-know-which-artifacts-are-not-supported"></a>在我嘗試部署時收到警告，指出我的工作區中有「不支援的成品」。 我要如何知道不支援哪些成品？

如需部署管線中不支援之項目與成品的完整清單，請參閱下列各節：

* [不支援的項目](deployment-pipelines-process.md#unsupported-items)

* [未複製的項目屬性](deployment-pipelines-process.md#item-properties-that-are-not-copied)

### <a name="why-did-my-deployment-fail-due-to-broken-rules"></a>為什麼我的部署因為規則中斷而失敗？

如果您在設定資料集規則時遇到問題，請瀏覽[資料集規則](deployment-pipelines-get-started.md#step-4---create-dataset-rules)，並確定您遵循[資料集規則限制](deployment-pipelines-get-started.md#dataset-rule-limitations)。

如果您的部署先前已成功，且由於規則中斷而突然失敗，則可能是因為資料集正在重新發佈。 下列對來源資料集所做的變更會導致部署失敗：

**參數規則**

* 已移除的參數

* 已變更的參數名稱

**資料來源規則**

您的資料集規則遺漏值。 如果您的資料集已變更，可能就會發生這種情況。

![在部署因連結中斷而失敗時所顯示之無效規則錯誤的螢幕擷取畫面。](media/deployment-pipelines-troubleshooting/broken-rule.png)

當先前成功的部署因為連結中斷而失敗時，會顯示警告。 您可以選取 [設定規則]，瀏覽至 [部署設定] 窗格，其中會標示失敗的資料集。 當您選取資料集時，會標示中斷的規則。

若要成功部署，請修正或移除中斷的規則，然後重新部署。

### <a name="how-can-i-change-the-data-source-in-the-pipeline-stages"></a>如何變更管線階段中的資料來源？

您無法在 Power BI 服務中變更資料來源連線。

如果您想要變更測試階段或生產階段中的資料來源，您可以使用[資料集規則](deployment-pipelines-get-started.md#step-4---create-dataset-rules) 或 [API](/rest/api/power-bi/datasets/updateparametersingroup) \(英文\)。 資料集規則只會在下一次部署之後生效。

### <a name="i-fixed-a-bug-in-production-but-now-i-cant-select-the-deploy-to-previous-stage-button-why-is-it-greyed-out"></a>我已修正生產環境中的錯誤 (Bug)，但現在我無法選取 [部署至上一個階段] 按鈕。 為什麼該按鈕顯示為灰色？

您只能回溯部署到空的階段。 如果您在測試階段中有內容，就無法從生產環境進行回溯部署。

建立管線之後，請使用開發階段來開發您的內容，並使用測試階段來進行檢閱和測試。 您可以在這些階段修正錯誤 (Bug)，然後將已修正的環境部署至生產階段。

>[!NOTE]
>回溯部署僅支援[完整部署](deployment-pipelines-get-started.md#deploying-all-content)。 其不支援[選擇性部署](deployment-pipelines-get-started.md#selective-deployment)

### <a name="does-deployment-pipelines-support-multi-geo"></a>部署管線支援多地理位置嗎？

支援多地理位置。 在不同地理位置的階段之間部署內容可能需要較長的時間。

## <a name="permissions"></a>權限

### <a name="what-is-the-deployment-pipelines-permissions-model"></a>什麼是部署管線權限模型？

部署管線權限模型會在[權限](deployment-pipelines-process.md#permissions)一節中說明。

### <a name="who-can-deploy-content-between-stages"></a>哪些人可以在階段之間部署內容？

內容可以部署到空的階段或包含內容的階段。 內容必須位於 [Premium 容量](../admin/service-premium-what-is.md)。

* **部署到空的階段** - 任何 [Pro 使用者](../admin/service-admin-purchasing-power-bi-pro.md) (來源工作區中的成員或管理員)。

* **部署到具有內容的階段** - 任何 [Pro 使用者](../admin/service-admin-purchasing-power-bi-pro.md) (來源與目標部署階段中兩個工作區的成員或管理員)。

* **覆寫資料集** - 即使資料集並未變更，部署也會覆寫包含在目標階段中的每個資料集。 使用者必須是部署中指定之所有目標階段資料集的擁有者。

### <a name="which-permissions-do-i-need-to-configure-dataset-rules"></a>我需要哪些權限來設定資料集規則？

若要在部署管線中設定資料集規則，您必須是資料集擁有者。

### <a name="why-cant-i-see-workspaces-in-the-pipeline"></a>為什麼我看不到管線中的工作區？

管線與工作區權限會分開管理。 您可能具有管線權限，但不具有工作區權限。 如需詳細資訊，請檢閱[權限](deployment-pipelines-process.md#permissions)一節。

## <a name="next-steps"></a>後續步驟

>[!div class="nextstepaction"]
>[部署管線簡介](deployment-pipelines-overview.md)

>[!div class="nextstepaction"]
>[開始使用部署管線](deployment-pipelines-get-started.md)

>[!div class="nextstepaction"]
>[了解部署管線程序](deployment-pipelines-process.md)

>[!div class="nextstepaction"]
>[部署管線最佳做法](deployment-pipelines-best-practices.md)
