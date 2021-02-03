---
title: 取得用戶端密碼的內嵌式分析教學課程
description: 取得內嵌式分析教學課程的用戶端密碼。
services: powerbi
author: KesemSharabi
ms.author: kesharab
ms.topic: include
ms.date: 12/09/2020
ms.custom: include file
ms.openlocfilehash: 875243aa890b80d21a73b20dec291329d256ba21
ms.sourcegitcommit: 2e81649476d5cb97701f779267be59e393460097
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/02/2021
ms.locfileid: "99494576"
---
若要取得用戶端祕密，請遵循下列步驟：

1. 登入 [Microsoft Azure](https://ms.portal.azure.com/#allservices)。

2. 搜尋 **應用程式註冊**，然後選取 [應用程式註冊] 連結。

3. 選取您用來內嵌 Power BI 內容的 Azure AD 應用程式。

4. 在 [管理]  下，選取 [憑證和密碼]  。

5. 在 [用戶端密碼] 底下，選取 [新增用戶端密碼]。

6. 在 [新增用戶端祕密] 快顯視窗中，提供應用程式祕密的描述、選擇應用程式祕密何時到期，然後選取 [新增]。

7. 從 [用戶端祕密] 區段中，複製新建立的應用程式祕密中 [值] 資料行的字串。 用戶端祕密值是您的「用戶端識別碼」。