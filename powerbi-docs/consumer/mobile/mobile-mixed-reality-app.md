---
title: 適用於 HoloLens 的 Power BI (第 1 代)
description: 您可以透過 Power BI for Mixed Reality 應用程式 (預覽) 來檢視您的儀表板和報表，沉浸在虛擬世界或您的環境內容中。
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 09/22/2020
ms.openlocfilehash: c832217363f726e3eff469238fe9b3f29025837c
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415350"
---
# <a name="power-bi-for-hololens-1st-gen"></a>適用於 HoloLens 的 Power BI (第 1 代)
您可以在沉浸於虛擬世界的同時，透過適用於 HoloLens 的 Power BI 應用程式來檢視您的儀表板和報表，或將這些項目放在您環境內容中的特定位置。 

從 Microsoft Store [下載 Power BI for Mixed Reality](https://www.microsoft.com/p/power-bi-mobile/9nblgggzlxn1?activetab=pivot%3aoverviewtab)應用程式：在 Microsoft Store 中，該項目稱作「Power BI 行動版」。 您可在虛擬世界中與儀表板和報表互動，然後選取您要放置的項目。 

## <a name="two-views-windows-classic-and-holographic"></a>兩個檢視：Windows 傳統和全像

Power BI for Mixed Reality 是以 Power BI Windows 行動裝置應用程式為基礎，其中包含混合實境特有的其他功能。 當您啟動 Power BI for Mixed Reality 時，您會進入 Power BI 的這個「傳統」Windows 檢視。 在此檢視中，您可以在有權存取的儀表板與報表之間巡覽。 當您找到想要的項目時，您可以從傳統 Windows 檢視切換至全像體驗。 


## <a name="windows-classic-view-basics"></a>Windows 傳統檢視基本概念

如果您還不熟悉混合實境體驗，本節會很適合您。 與混合實境應用程式互動不同於與電腦 (或甚至是與平板電腦或手機) 互動。 在 Windows 傳統檢視中，混合實境應用程式會回應取代傳統滑鼠和鍵盤 (或手機點選) 的一組手勢和語音命令。 

**空中點選**

空中點選是您需要了解以與幾乎所有混合實境應用程式互動的最基本手勢。 您會舉起手並以拇指和食指點選，類似於按一下滑鼠或手機點選。  

![混合實境空中點選手勢](./media/mobile-mixed-reality-app/power-bi-hololens-airtap.png)

在 Power BI 中，您可以在使用按一下滑鼠之任何地方的 Windows 傳統型應用程式中使用空中點選。 您可以空中點選來開啟工作區中的儀表板或報表，或空中點選視覺效果的一部分來篩選或交叉醒目提示其他視覺效果，以及執行其他工作。

![在 Power BI 中手動空中點選](./media/mobile-mixed-reality-app/power-bi-hololens-airtap-hand.png) 

深入了解[混合實境中的 Microsoft 手勢](https://developer.microsoft.com/windows/mixed-reality/gestures)。

**釘選項目** 

空中點選 **釘選** 圖示![釘選圖示](./media/mobile-mixed-reality-app/power-bi-hololens-pin.png)，將儀表板或報表從 Windows 傳統檢視釘選到全像檢視。 您可以將一些項目釘選到全像檢視。 

**切換至全像檢視**

在 Windows 傳統檢視中釘選項目之後，您可以空中點選 **全螢幕** 圖示![全螢幕圖示](./media/mobile-mixed-reality-app/power-bi-hololens-fullscreen.png)切換至全像檢視。 


## <a name="holographic-view-basics"></a>全像檢視基本概念

現在您已進入全像檢視，所有釘選的成品都會在您的停駐列中。 您可以將這些釘選項目放在實體空間中的特定位置，例如放在項目描述的設備項目旁。 在全像檢視中，語音命令會補充手勢。 以下是一些常見的語音命令。

**"Follow me"** 

選擇一個 Power BI 成品，讓它停留在您的主要視野，並跟著您的視線直到您將它放在某處。

**"Dock"** 

使用 "dock" 命令可將成品放在您的 Power BI 停駐列，讓其在您的主要視野外也會跟著您，以方便存取。

**"Place here"**

此命令可將儀表板或報表放在塗鴉牆或物件上，或停留在空間中。

![將儀表板放在空間中](./media/mobile-mixed-reality-app/power-bi-hololens-place-visuals.png)

**"Go home"**

說 "go home" 可返回 Power BI 傳統 Windows 檢視。 

**"Remove"**

使用此命令可從全像檢視中移除成品。

**"Remove all"** 

使用此命令可從全像檢視中移除所有成品。


## <a name="scan-a-report-qr-code-in-holographic-view"></a>在全像檢視中掃描報表的 QR 代碼

您可以在全像檢視中掃描報表的 QR 代碼，就像是[使用適用於 iPhone 和 Android 的 Power BI 行動裝置應用程式掃描 QR 代碼](mobile-apps-qr-code.md)一樣。

- 在全像檢視中，注視 QR 代碼。 Power BI 會開啟與該 QR 代碼建立關聯的報表。

## <a name="limitations-and-considerations"></a>限制與考量

以下是全像檢視的一些限制和考量。

- 您看不到 Windows 傳統檢視中可能已設定的交叉篩選或醒目提示。
- 已釘選儀表板和報表的檢視是私人的。 我們目前不支援共用體驗。
- 當資料變更時，儀表板和報表會每隔 45 秒重新整理一次。


## <a name="next-steps"></a>後續步驟

- [使用 Power BI 行動裝置應用程式取得實際資料](mobile-apps-data-in-real-world-context.md)

 



