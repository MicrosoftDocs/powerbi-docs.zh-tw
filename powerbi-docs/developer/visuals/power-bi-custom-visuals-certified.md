---
title: 經認證的 Power BI 視覺效果
description: 提交自訂視覺效果進行認證的需求和程序，以及經認證的 Power BI 視覺效果清單。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 03/08/2020
ms.openlocfilehash: bbca1802b1136c4e9e16e70ab87ab7554612c037
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96386700"
---
# <a name="get-a-power-bi-visual-certified"></a>取得 Power BI 視覺效果認證

經認證的 Power BI 視覺效果是 [AppSource](https://appsource.microsoft.com/en-us/marketplace/apps?page=1&product=power-bi-visuals) 中的 Power BI 視覺效果，符合 Microsoft Power BI 小組[程式碼需求](#certification-requirements)。 這些視覺效果會經過測試，以驗證它們不會存取外部服務或資源，而且它們會遵循安全的程式碼模式和指導方針。

Power BI 視覺效果一旦經過認證，便能提供更多的功能。 例如，您可以[匯出至 PowerPoint](../../consumer/end-user-powerpoint.md)，也可以在使用者[訂閱報表頁面](../../consumer/end-user-subscribe.md)時所收到的電子郵件中顯示視覺效果。

認證程序是選擇性的。 未經認證的 Power BI 視覺效果，不一定是不安全的 Power BI 視覺效果。 有些 Power BI 視覺效果未經過認證，因為其不符合一或多個[認證需求](power-bi-custom-visuals-certified.md#certification-requirements) \(英文\)。 例如，連接至外部服務的對應 Power BI 視覺效果，或使用商業程式庫的 Power BI 視覺效果。

> [!NOTE]
> Microsoft 並非協力廠商 Power BI 視覺效果的作者。 若要確認第三方視覺效果的功能，請直接連絡視覺效果的作者。

## <a name="certification-requirements"></a>認證需求

若要讓您的 Power BI 視覺效果[通過認證](#get-a-power-bi-visual-certified)，您的 Power BI 視覺效果必須符合此節所列的需求。 

### <a name="general-requirements"></a>一般需求

Power BI 視覺效果必須由合作夥伴中心核准。 我們建議您的 Power BI 視覺效果已在 [AppSource](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) 中。 若要了解如何將 Power BI 視覺效果發佈至 AppSource，請參閱[將 Power BI 視覺效果發佈至合作夥伴中心](office-store.md)。

在提交您的 Power BI 視覺效果以獲得認證之前，請確認它符合 [Power BI 視覺效果的指導方針](guidelines-powerbi-visuals.md)。

提交 Power BI 視覺效果時，請確定編譯的套件完全符合已提交的套件。

### <a name="code-repository-requirements"></a>程式碼存放庫需求

雖然您不需要在 GitHub 中公開共用程式碼，但是程式碼存放庫必須可供 Power BI 小組檢閱。 執行此動作的最佳方式是在 GitHub 中提供原始程式碼 (JavaScript 或 TypeScript)。

存放庫必須包含下列項目：
* 僅限一個 Power BI 視覺效果的程式碼。 不能包含多個 Power BI 視覺效果或不相關的程式碼。
* 名為 **certification** 的分支 (必須是小寫)。 此分支中的原始程式碼必須符合已提交的套件。 如果您要重新提交 Power BI 視覺效果，則只能在下一次提交程序期間更新此程式碼。

如果您的 Power BI 視覺效果使用私人 npm 套件或 git 子模組，您必須提供其他存放庫 (包含此程式碼) 的存取權。

若要了解 Power BI 視覺效果存放庫的外觀，請檢閱 GitHub 存放庫中的 [Power BI 視覺效果範例橫條圖](https://github.com/microsoft/PowerBI-visuals-sampleBarChart) \(英文\)。

### <a name="file-requirements"></a>檔案需求

使用最新版本的 API 來撰寫 Power BI 視覺效果。

存放庫必須包含下列檔案：
* **.gitignore** - 將 `node_modules`、`.tmp` 與 `dist` 新增至此檔案。 程式碼不能包含 *node_modules*、 *.tmp* 或 *dist* 資料夾。
* **capabilities.json** - 如果您要提交較新版本的 Power BI 視覺效果，並變更此檔案中的屬性，請確認它們不會中斷現有使用者的報告。
* **pbiviz.json** 
* **package.json**. 視覺效果必須已安裝下列套件：
   * ["tslint"](https://www.npmjs.com/package/tslint) \(英文\) - 5.18.0 版或更新版本
   * ["typescript"](https://www.npmjs.com/package/typescript) \(英文\) - 3.0.0 版或更新版本
   * ["tslint-microsoftcontrib"](https://www.npmjs.com/package/tslint-microsoft-contrib) \(英文\) - 6.2.0 版或更新版本
   * 檔案必須包含用於執行 linter 的命令 - `"lint": "tslint -c tslint.json -p tsconfig.json"`
* **package-lock.json**
* **tsconfig.json**

### <a name="command-requirements"></a>命令需求

請確定下列命令不會傳回任何錯誤。

* `npm install`
* `pbiviz package`
* `npm audit` - 不得傳回任何層級為高或中的警告。
* [Microsoft 提供的 TSlint](https://www.npmjs.com/package/tslint-microsoft-contrib)，且必須具有[必要設定](https://github.com/microsoft/PowerBI-visuals-sampleBarChart/blob/master/tslint.json)。 此命令不得傳回任何 lint 錯誤。

### <a name="compiling-requirements"></a>編譯需求

使用最新版本的 [powerbi-visuals-tools](https://www.npmjs.com/package/powerbi-visuals-tools) 來撰寫 Power BI 視覺效果。

您必須使用 `pbiviz package` 來編譯您的 Power BI 視覺效果。 如果您要使用自己的組建指令碼，請提供 `npm run package` 自訂組建命令。

### <a name="source-code-requirements"></a>原始程式碼需求

確認您遵循 [Power BI 視覺效果其他認證](/legal/marketplace/certification-policies#1200-power-bi-visuals-additional-certification)原則清單。 如果您的提交未遵循這些指導方針，合作夥伴中心的拒絕電子郵件將會包含此連結中所列的原則號碼。

依照下列程式碼需求，確定您的程式碼符合 Power BI 認證原則。  

**必要**
* 只能使用公用的可檢閱 OSS 元件，例如公用 JavaScript 或 TypeScript 程式庫。
* 程式碼必須支援[轉譯事件 API](event-service.md)。
* 請確定已安全地操作 DOM。 請先對使用者輸入或使用者資料使用清理，再將其新增至 DOM。
* 使用[範例報告](https://github.com/Microsoft/PowerBI-visuals/raw/gh-pages/assets/reports/large_data.pbix)作為測試資料集。

**不允許**
* 存取外部服務或資源。 例如，不能從 Power BI 將任何 HTTP/S 或 WebSocket 要求發送到任何服務。
* 使用 `innerHTML` 或 `D3.html(user data or user input)`。
* 瀏覽器主控台中任何輸入資料的 JavaScript 錯誤或例外狀況。
* 任意或動態程式碼，例如 `eval()`、不安全地使用 `settimeout()`、`requestAnimationFrame()`、`setinterval(user input function)`，以及使用者輸入或使用者資料。
* 縮短 JavaScript 檔案或專案。

## <a name="submitting-a-power-bi-visual-for-certification"></a>提交 Power BI 視覺效果進行認證

您可以透過合作夥伴中心，要求 Power BI 小組認證您的 Power BI 視覺效果。

>[!TIP]
>Power BI 認證程序可能需要一些時間。 如果您是在建立新的 Power BI 視覺效果，建議您在要求 Power BI 認證之前，先透過合作夥伴中心發佈您的 Power BI 視覺效果。 這可確保視覺效果的發佈不會延遲。

要求 Power BI 認證：

1. 登入合作夥伴中心。
2. 在 [概觀]  頁面上選擇您的 Power BI 視覺效果，然後移至 [產品設定]  頁面。
3. 選取 [要求 Power BI 認證]  核取方塊。
4. 在 [檢閱並發佈]  頁面上的 [認證注意事項]  文字方塊中，提供原始程式碼的連結和存取該程式碼所需的認證。

### <a name="private-repository-submission-process"></a>私人存放庫提交程序

如果您使用 GitHub 之類的私人存放庫來提交您的 Power BI 視覺效果進行認證，請遵循此節中的指示。
1. 針對驗證小組建立新的帳戶。
2. 針對您的帳戶設定[雙因素驗證](https://help.github.com/github/authenticating-to-github/securing-your-account-with-two-factor-authentication-2fa) \(英文\)。
3. [產生一組新的復原碼](https://help.github.com/github/authenticating-to-github/configuring-two-factor-authentication-recovery-methods#generating-a-new-set-of-recovery-codes) \(英文\)。
4. 提交您的 Power BI 視覺效果時，請提供下列項目：
    * 存放庫的連結
    * 登入認證 (包括密碼)
    * 復原碼
    * 我們帳戶 ([pbicvsupport](https://github.com/pbicvsupport) 的唯讀權限

## <a name="certified-power-bi-visual-badges"></a>經認證的 Power BI 視覺效果徽章

一旦 Power BI 視覺效果通過認證，就會取得指定的徽章，表示已通過認證。

### <a name="certified-power-bi-visuals-in-appsource"></a>AppSource 中經認證的 Power BI 視覺效果

* 在線上搜尋 [AppSource 中的 Power BI 視覺效果](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals)時，視覺效果卡片上的小黃色徽章表示其是經認證的 Power BI 視覺效果。

    ![AppSource 經認證的 Power BI 視覺效果](media/power-bi-custom-visuals-certified/certified-visual-yellow-small.png)

* 按一下 AppSource 中的 Power BI 視覺效果卡片之後，名為「PBI 認證」  的黃色徽章會指出此 Power BI 視覺效果已通過認證。

    ![應用程式頁面經認證的 Power BI 視覺效果](media/power-bi-custom-visuals-certified/certified-visual-yellow-big.png)

### <a name="certified-power-bi-visuals-in-the-power-bi-interface"></a>Power BI 介面中經認證的 Power BI 視覺效果

* 從 Power BI (Desktop 或服務) 匯入 Power BI 視覺效果時，藍色徽章表示 Power BI 視覺效果已通過認證。

    ![Power BI 介面經認證的 Power BI 視覺效果](media/power-bi-custom-visuals-certified/certified-visual-blue.png)

* 您可以透過選取 [Power BI 認證]  篩選選項，只顯示經認證的 Power BI 視覺效果。

## <a name="publication-timeline"></a>發行集時間軸

部署至 AppSource 的程序可能略為耗時。 在此程序完成後，您即可從 AppSource 下載 Power BI 視覺效果。

### <a name="when-will-users-be-able-to-download-my-visual"></a>使用者何時能夠下載我的視覺效果？

* 如果您是第一次提交 Power BI 視覺效果，則使用者可在您收到 AppSource 電子郵件後幾小時下載。

* 如果是提交現有 Power BI 視覺效果的更新，則使用者將可在您提交的一個月內下載。

    >[!NOTE]
    > AppSource 中的「版本」  欄位會更新為 AppSource 核准您 Power BI 的日期，大約是在您提交視覺效果後一週。 使用者可下載更新的視覺效果，但更新的功能不會生效。 您的視覺效果新功能約在一個月後才會影響使用者的報表。 

### <a name="when-will-my-power-bi-visual-display-a-certification-badge"></a>我的 Power BI 視覺效果何時會顯示認證徽章？

* 如果您是第一次提交 Power BI 視覺效果，則認證徽章會在您收到 AppSource 核准電子郵件的一天內出現。

* 如果要求現有 Power BI 視覺效果的認證，則認證徽章會在您提交的一個月內出現。

## <a name="next-steps"></a>後續步驟

* 如果您是有興趣建立自己的 Power BI 視覺效果並將其新增至  [Microsoft AppSource](https://appsource.microsoft.com) \(英文\) 的 Web 開發人員，請從 [開發 Power BI 圓形卡片視覺效果](develop-circle-card.md)教學課程開始。

* 如需視覺效果的詳細資訊，請參閱[認證視覺效果的常見問題集](power-bi-custom-visuals-faq.md#certified-power-bi-visuals)。

* [YouTube 上的 Microsoft Power BI 視覺效果播放清單](https://www.youtube.com/playlist?list=PL1N57mwBHtN1vIjfvuBIzZllrmKo-Vz6x)

* [Power BI 中的視覺效果](power-bi-custom-visuals.md)

* [在 Microsoft AppSource 上發佈 Power BI 視覺效果](office-store.md)

* 有其他問題嗎？ [試試 Power BI 社群](https://community.powerbi.com/)