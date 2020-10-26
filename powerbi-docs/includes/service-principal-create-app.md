---
title: 服務主體建立應用程式
description: 服務主體建立應用程式
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 05/20/2020
ms.custom: include file
ms.openlocfilehash: 80886eab6de6c125d0361b326f5d31d2b3bb35e5
ms.sourcegitcommit: d153cfc0ce559480c53ec48153a7e131b7a31542
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91524506"
---
1. 登入 [Microsoft Azure](https://ms.portal.azure.com/#allservices)。

2. 搜尋 [應用程式註冊]，然後按一下 [應用程式註冊] 連結。

    ![azure 應用程式註冊](media/embedded-service-principal/azure-app-registration.png)

3. 按一下 [新增註冊]。

    ![新增註冊](media/embedded-service-principal/new-registration.png)

4. 填寫必要資訊：
    * **名稱** - 輸入應用程式的名稱
    * **支援的帳戶類型** - 選取支援的帳戶類型
    * (選擇性) **重新導向 URI** - 必要時輸入 URI

5. 按一下 [註冊] 。

6. 註冊之後，您可以從 [概觀] 索引標籤取得「應用程式識別碼」。複製並儲存「應用程式識別碼」以供稍後使用。

    ![螢幕擷取畫面顯示在 [概觀] 索引標籤中取得應用程式識別碼的位置。](media/embedded-service-principal/application-id.png)