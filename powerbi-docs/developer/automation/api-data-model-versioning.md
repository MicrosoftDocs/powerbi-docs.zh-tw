---
title: Power BI 內嵌式分析中，用於取得更佳內嵌 BI 見解的 Power BI 資料模型版本設定
description: OData 服務公開的資料模型。 使用 Power BI 內嵌式分析，以便取得更佳的內嵌 BI 見解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: 0c645774f7af1a8575ca3c755a74fd65b652031a
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887699"
---
# <a name="data-model-versioning"></a>資料模型版本設定

OData 服務 (例如 Power BI 資料模型) 所公開的資料模型會定義 OData 服務與其用戶端之間的合約。 服務只能擴充其模型到不會中斷現有用戶端的程度。 重大變更 (例如移除屬性或變更現有屬性的類型) 需要提供新的服務版本，其位於新模型的不同服務根 URL。  
  
下列資料模型新增視為安全，並且不需要對其進入點進行版本設定的服務。  
  
* 加入可為 null 或具有預設值的屬性；如果與現有的動態屬性同名，其類型 (或基底類型) 必須與現有的動態屬性相同  
* 加入可為 null 或具有以集合為值的導覽屬性；如果與現有的動態導覽屬性同名，其類型 (或基底類型) 必須與現有的動態導覽屬性相同  
* 將新的實體類型加入模型  
* 將新的複雜類型加入模型  
* 加入新的實體集  
* 加入新的單一值  
* 加入動作、函式、動作匯入或函式匯入
* 加入可為 null 的動作參數  
* 加入類型定義或列舉  
* 將任何註釋加入不須經用戶端了解就能正確與服務互動的模型項目  
  
用戶端「應該」為服務對其模型進行這類累加的變更有所準備。 用戶端尤其應該準備好接收屬性與服務先前未定義的衍生類型。  
  
服務「不應該」變更相依於已驗證使用者的資料模型。 如果是使用者或使用者群組相依的資料模型，所有變更都必須是安全變更，如同在此節中比較完整模型與授權受限使用者可見的模型時所定義。  
  
如需 OData 資料模型標準的詳細資訊，請參閱 [OData 4.0 版第 1 部分：Protocol Plus Errata 02](https://docs.oasis-open.org/odata/odata/v4.0/odata-v4.0-part1-protocol.html)。  
  
## <a name="see-also"></a>請參閱
[Power BI REST API 概觀](/rest/api/power-bi/)