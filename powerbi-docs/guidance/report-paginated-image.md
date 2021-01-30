---
title: 編頁報表的影像使用指導
description: 在 Power BI 編頁報表中使用影像的指導。
author: peter-myers
ms.author: kfollis
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 02/16/2020
ms.openlocfilehash: f83894561f8592d5e679a08773459f14a9d6fa1c
ms.sourcegitcommit: fb529c4532fbbdfde7ce28e2b4b35f990e8f21d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2021
ms.locfileid: "99087744"
---
# <a name="image-use-guidance-for-paginated-reports"></a>編頁報表的影像使用指導

本文適用於設計 Power BI [分頁報表](../paginated-reports/paginated-reports-report-builder-power-bi.md)的報表作者。 本指導提供使用影像時的建議。 通常，報表配置中的影像可以顯示公司標誌或圖片等圖形。

影像可以儲存在三個不同位置：

- 報表內 (內嵌)
- 網頁伺服器上
- 資料庫中，並由資料集擷取

這些影像接著可以應用在您報表配置中的各種案例內：

- 獨立標誌或圖片
- 與資料列建立關聯的圖片
- 特定報表項目的背景：
  - 報表主體
  - 文字方塊
  - 矩形
  - Tablix 資料區域 (資料表、矩陣或清單)

## <a name="suggestions"></a>建議

請考慮下列建議，以傳遞專業的報表配置、簡化維護，並最佳化報表效能：

- **盡可能地使用最小的大小**：我們建議您準備大小較小，看起來仍然銳利且清晰的影像。 這完全取決於品質與大小之間的平衡。 請考慮使用圖形編輯器 (例如 Microsoft 小畫家) 來減少影像的檔案大小。
- **避免內嵌影像**：首先，內嵌影像可能會使報表檔案大小膨脹，降低報表的轉譯速度。 其次，若您需要更新許多報表影像 (例如若公司更改了其標誌)，內嵌影像很快地就會使維護變得相當困難。
- **使用網頁伺服器儲存空間**：將影像儲存在網頁伺服器上是個不錯的選項，特別是從公司網站上取得的公司標誌。 但是，請在報表使用者從您網路的外部存取報表時特別注意。 在這種情況下，請確保影像可以透過網際網路存取。

    當影像與您的資料相關時 (例如您銷售人員的圖片)，請命名影像檔案，讓報表運算式可以動態產生影像 URL 路徑。 例如，您可以使用每一位銷售人員的員工編號來命名銷售人員圖片。 若報表資料集會擷取員工編號，您便可以撰寫運算式來產生完整的影像 URL 路徑。
- **使用資料庫儲存體**：關聯式資料庫儲存影像資料時，從資料庫資料表直接取得影像資料便相當合理，特別是在影像不大時。
- **適當的背景影像**：若決定使用背景影像，請注意不要讓報表使用者從您的報表資料分心。 

    此外，也請務必使用「浮水印樣式的影像」  。 一般而言，浮水印樣式的影像具有透明背景 (或擁有與報表所使用背景色彩相同的背景色彩)。 這些影像也會使用較暗的色彩。 常見的浮水印樣式影像包含公司標誌，或是敏感性標籤 (例如「草稿」或「機密」)。

## <a name="next-steps"></a>後續步驟

如需本文的詳細資訊，請參閱下列資源：

- [什麼是 Power BI Premium 中的編頁報表？](../paginated-reports/paginated-reports-report-builder-power-bi.md)
- 有問題嗎？ [嘗試在 Power BI 社群提問](https://community.powerbi.com/)
- 有任何建議嗎？ [貢獻想法來改善 Power BI](https://ideas.powerbi.com/)
