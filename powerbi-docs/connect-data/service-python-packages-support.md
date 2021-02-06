---
title: 了解支援哪些 Python 套件
description: Power BI 中支援與不支援的 Python 套件
author: otarb
ms.author: otarb
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: conceptual
ms.date: 06/26/2020
LocalizationGroup: Connect to data
ms.openlocfilehash: d3a30098b793ccb75cbae6c271ab1685b3176a10
ms.sourcegitcommit: f17acb16018752c234db6bff1f51f5130be12c58
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/06/2021
ms.locfileid: "99616942"
---
# <a name="create-visuals-by-using-python-packages-in-the-power-bi-service"></a>在 Power BI 服務中使用 Python 套件建立視覺效果
您可以使用功能強大的 [Python 程式設計語言](https://www.python.org/) \(英文\)，在 Power BI 服務中建立視覺效果。 Power BI 服務支援眾多 Python 套件，而且一直都可支援更多套件。

後續小節將提供一個按照字母順序的表格，指出 Power BI 支援哪些 Python 套件。 

## <a name="request-support-for-a-new-python-package"></a>要求支援新的 Python 套件
您可以在下節 (標題為 **支援的套件**) 中找到 **Power BI 服務** 支援的 Python 套件。 如果您想要求支援該清單中找不到的 Python 套件，請將您的要求提交至 [Power BI Ideas](https://ideas.powerbi.com) \(英文\)。

## <a name="requirements-and-limitations-of-python-packages"></a>Python 套件的需求和限制
有少數 Python 套件的需求和限制：

* 目前的 Python 執行階段：Python 3.7.7。
* Power BI 服務大部分支援具有 GPL-2、GPL-3、MIT+ 等這類免費和開放原始碼軟體授權的 Python 套件。
* Power BI 服務支援 PyPI 中發佈的套件。 此服務不支援私人或自訂 Python 套件。 我們鼓勵使用者先製作其可在 PyPI 上使用的私人套件，然後再要求可在 Power BI 服務中使用該套件。
* 針對 **Power BI Desktop** 中的 Python 視覺效果，您可以安裝任何套件，包括自訂的 Python 套件。
* 基於安全性和隱私權考量，不支援服務中透過全球資訊網提供用戶端-伺服器查詢的 Python 套件。 會封鎖這類嘗試的網路功能。
* 包含新 Python 套件的核准程序具有樹狀結構的相依性；無法支援需要在服務中安裝的一些相依性。

## <a name="python-packages-that-are-supported-in-power-bi"></a>Power BI 中支援的 Python 套件
下表顯示 Power BI 服務中 **支援** 的 R 套件。


|        套件        |   版本   |                                   連結                                   |
|-----------------------|-------------|--------------------------------------------------------------------------|
|matplotlib|3.2.1|https://pypi.org/project/matplotlib|
|numpy|1.18.4|https://pypi.org/project/numpy|
|pandas|1.0.1|https://pypi.org/project/pandas|
|scikit-learn|0.23.0|https://pypi.org/project/scikit-learn|
|scipy|1.4.1|https://pypi.org/project/scipy|
|以 seaborn|0.10.1|https://pypi.org/project/seaborn|
|statsmodels|0.11.1|https://pypi.org/project/statsmodels|
|xgboost|1.1.0|https://pypi.org/project/xgboost|

## <a name="next-steps"></a>後續步驟
如需 Power BI 中 Python 的詳細資訊，請查看下列文章：

* [使用 Python 建立 Power BI 視覺效果](desktop-python-visuals.md)
* [在 Power BI Desktop 中執行 Python 指令碼](desktop-python-scripts.md)
* [在查詢編輯器中使用 Python](desktop-python-in-query-editor.md)
