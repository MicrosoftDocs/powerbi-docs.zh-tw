---
title: 教學課程：連線到 SQL Server 中的內部部署資料
description: 了解如何使用 SQL Server 作為閘道資料來源，包括如何重新整理資料。
author: arthiriyer
ms.author: arthii
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: tutorial
ms.date: 07/15/2019
LocalizationGroup: Gateways
ms.openlocfilehash: ba518991145b727e141e1441f30ea73819bddb31
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410267"
---
# <a name="refresh-data-from-an-on-premises-sql-server-database"></a>從內部部署 SQL Server 資料庫重新整理資料

在本教學課程中，您會探索如何從您區域網路中的內部部署關聯式資料庫重新整理 Power BI 資料集。 具體而言，本教學課程會使用範例 SQL Database 資料庫，而 Power BI 必須透過內部部署資料閘道才能存取該資料庫。

在本教學課程中，您完成下列步驟：

> [!div class="checklist"]
> * 建立和發佈 Power BI Desktop (.pbx) 檔案，從內部部署 SQL Server 資料庫匯入資料。
> * 在 Power BI 中針對透過資料閘道的 SQL Server 連線能力設定資料來源及資料集設定。
> * 設定重新整理排程，確保您的 Power BI 資料集擁有最近的資料。
> * 執行您資料集的隨選重新整理。
> * 檢閱重新整理歷程記錄，分析過去重新整理循環的結果。
> * 刪除在本教學課程中建立的成品來清除資源。

## <a name="prerequisites"></a>必要條件

- 若您尚未擁有 Power BI，請在開始前先註冊[免費 Power BI 試用版](https://app.powerbi.com/signupredirect?pbi_source=web)。
- 在本機電腦上[安裝 Power BI Desktop](https://powerbi.microsoft.com/desktop/)。
- 在本機電腦上[安裝 SQL Server](/sql/database-engine/install-windows/install-sql-server)，然後[從備份還原範例資料庫](https://github.com/Microsoft/sql-server-samples/releases/download/adventureworks/AdventureWorksDW2017.bak)。 如需 AdventureWorks 的詳細資訊，請參閱 [AdventureWorks 安裝及設定](/sql/samples/adventureworks-install-configure)。
- 在相同的本機電腦上[安裝內部部署資料閘道](service-gateway-onprem.md)作為 SQL Server (在生產環境中，其通常是另一部電腦)。

> [!NOTE]
> 若您不是閘道管理員，且不想要自行安裝閘道，請連絡您組織中的閘道管理員。 他們可以建立將您資料集連線到 SQL Server 資料庫時所需的資料來源定義。

## <a name="create-and-publish-a-power-bi-desktop-file"></a>建立及發佈 Power BI Desktop 檔案

請使用下列程序，利用 AdventureWorksDW 範例資料庫建立基本的 Power BI 報表。 將報表發佈到 Power BI 服務，讓您在 Power BI 中取得資料集，並在接下來的步驟中進行設定及重新整理。

1. 在 Power BI Desktop 的 [首頁]  索引標籤上，選取 [取得資料]  \> [SQL Server]  。

2. 在 [SQL Server 資料庫]  對話方塊中，輸入 [伺服器]  及 [資料庫 (選擇性)]  名稱、確認 [資料連線能力模式]  為 [匯入]  ，然後選取 [確定]  。

    ![SQL Server 資料庫](./media/service-gateway-sql-tutorial/sql-server-database.png)

    我們不會在此教學課程中使用 [進階選項]  ，但請注意，您可以指定 SQL 陳述式並設定其他選項，例如，使用 [SQL Server 容錯移轉](/sql/database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server)。

    ![SQL Server 進階選項](media/service-gateway-sql-tutorial/sql-server-advanced-options.png)

3. 驗證您的 [認證]  ，然後選取 [連線]  。

    > [!NOTE]
    > 若您無法進行驗證，請確認您已選取正確的驗證方法，並使用具備資料庫存取權限的帳戶。 在測試環境中，您可以使用具備明確使用者名稱及密碼的資料庫驗證。 在生產環境中，您通常會使用 Windows 驗證。 請參閱[針對重新整理案例進行疑難排解](refresh-troubleshooting-refresh-scenarios.md)及連絡您的資料庫管理員，以取得其他協助。

1. 若出現 [加密支援]  對話方塊，請選取 [確定]  。

2. 在 [導覽]  對話方塊中，選取 **DimProduct** 資料表，然後選取 [載入]  。

    ![資料來源導覽](./media/service-gateway-sql-tutorial/data-source-navigator.png)

3. 在 Power BI Desktop [報表]  檢視的 [視覺效果]  窗格中，選取 [堆疊直條圖]  。

    ![堆疊直條圖](./media/service-gateway-sql-tutorial/stacked-column-chart.png)

4. 選取報表畫布中的直條圖後，在 [欄位]  窗格中，選取 [EnglishProductName]  和 [ListPrice]  欄位。

    ![欄位窗格](./media/service-gateway-sql-tutorial/fields-pane.png)

5. 將 [EndDate]  拖曳到 [報表層級篩選]  上，然後在 [基本篩選]  下方，只選取 [(空白)]  的核取方塊。

    ![報表層級篩選](./media/service-gateway-sql-tutorial/report-level-filters.png)

    圖表現在看起來應該類似如下。

    ![完成後的直條圖](./media/service-gateway-sql-tutorial/finished-column-chart.png)

    請注意，其中列出了定價最高的五項 **Road-250** 產品。 當您稍後在本教學課程中更新資料並重新整理報表時，這會有所變更。

6. 使用名稱 "AdventureWorksProducts.pbix" 來儲存報表。

7. 在 [首頁]  索引標籤上，選取 [發佈]  \> [我的工作區]  \> [選取]  。 如果系統要求您登入 Power BI 服務，請執行這項操作。

8. 在 [成功]  畫面上，選取 [在 Power BI 中開啟 'AdventureWorksProducts.pbix']  。

    [發佈至 Power BI](./media/service-gateway-sql-tutorial/publish-to-power-bi.png)

## <a name="connect-a-dataset-to-a-sql-server-database"></a>將資料集連線到 SQL Server 資料庫

在 Power BI Desktop 中，您可以直接連線到您的內部部署 SQL Server 資料庫，但 Power BI 服務需要資料閘道作為雲端和您內部部署網路之間的橋樑。 請遵循這些步驟來將您的內部部署 SQL Server 資料庫作為資料來源新增到閘道，然後將您的資料集連線到此資料來源。

1. 登入 Power BI。 選取右上角的設定齒輪圖示，然後選取 [設定]  。

    ![Power BI 設定](./media/service-gateway-sql-tutorial/power-bi-settings.png)

2. 在 [資料集]  索引標籤上，選取 **AdventureWorksProducts** 資料集，讓您可以透過資料閘道連線到內部部署 SQL Server 資料庫。

3. 展開 [閘道連線]  並驗證其中至少列出了一個閘道。 若您沒有閘道，請參閱本教學課程稍早的[必要條件](#prerequisites)一節，以取得安裝及設定閘道的產品文件連結。

    ![閘道連線](./media/service-gateway-sql-tutorial/gateway-connection.png)

4. 在 [動作]  下方，展開切換按鈕來檢視資料來源，並選取 [新增至閘道]  連結。

    ![將資料來源新增至閘道](./media/service-gateway-sql-tutorial/add-data-source-gateway.png)

    > [!NOTE]
    > 若您不是閘道管理員，且不想要自行安裝閘道，請連絡您組織中的閘道管理員。 他們可以建立將您資料集連線到 SQL Server 資料庫時所需的資料來源定義。

5. 在 [閘道]  管理頁面上，於 [資料來源設定]  索引標籤上，輸入並驗證下列資訊，然後選取 [新增]  。

    | 選項 | 值 |
    | --- | --- |
    | 資料來源名稱 | AdventureWorksProducts |
    | 資料來源類型 | SQL Server |
    | 伺服器 | 您的 SQL Server 執行個體名稱，例如 SQLServer01 (必須與您在 Power BI Desktop 中所指定的內容相同)。 |
    | 資料庫 | 您的 SQL Server 資料庫名稱，例如 AdventureWorksDW (必須與您在 Power BI Desktop 中所指定的內容相同)。 |
    | 驗證方法 | Windows 或 Basic (通常是 Windows)。 |
    | 使用者名稱 | 您用來連線到 SQL Server 的使用者帳戶。 |
    | 密碼 | 您用來連線到 SQL Server 的帳戶密碼。 |

    ![資料來源設定](./media/service-gateway-sql-tutorial/data-source-settings.png)

6. 在 [資料集]  索引標籤上，再次展開 [閘道連線]  區段。 選取您設定的資料閘道 (該閘道的 [狀態]  會顯示其正在您安裝它的電腦上執行)，然後選取 [套用]  。

    ![更新閘道連線](./media/service-gateway-sql-tutorial/update-gateway-connection.png)

## <a name="configure-a-refresh-schedule"></a>設定重新整理排程

現在您已將 Power BI 中的資料集透過資料閘道連線到 SQL Server 資料庫內部部署，請遵循這些步驟來設定重新整理排程。 以排程作為基礎重新整理您的資料集，可協助確保您的報表和儀表板皆具備最新資料。

1. 在瀏覽窗格中，開啟 [我的工作區]  \> [資料集]  。 選取 **AdventureWorksProducts** 資料集的省略符號 (**. . .**)，然後選取 [排程重新整理]。

    > [!NOTE]
    > 確認您選取的是 **AdventureWorksProducts** 資料集的省略符號，而非具備相同名稱報表的省略符號。 **AdventureWorksProducts** 報表的操作功能表不包含 [排程重新整理]  選項。

2. 在 [已排程的重新整理]  區段中，於 [將您的資料維持在最新狀態]  下方，將重新整理設為 [開啟]  。

3. 選取適當的 [重新整理頻率]  (例如 [每天]  )，然後在 [時間]  下方，選取 [新增其他時間]  來指定所需的重新整理時間 (此範例為早上和晚上的 6:30)。

    ![設定排程的重新整理](./media/service-gateway-sql-tutorial/configure-scheduled-refresh.png)

    > [!NOTE]
    > 若您的資料集位共用容量上，您可以設定最多每天 8 個時段；若是在 Power BI Premium 中，則可以設定 48 個時段。

4. 將 [傳送重新整理失敗通知電子郵件給我]  核取方塊保持在啟用狀態，然後選取 [套用]  。

## <a name="perform-an-on-demand-refresh"></a>執行隨選重新整理

現在您已設定了重新整理排程，Power BI 即會在下一個排程的時間重新整理您的資料集 (於 15 分鐘的邊際內)。 如果您想要更快重新整理資料 (例如測試閘道和資料來源設定)，請使用導覽窗格中資料集功能表裡的 [立即重新整理]  選項來執行隨選重新整理。 隨選重新整理不會影響下次排程重新整理時間，但會計入每日重新整理限制，如前一節所述。

為了說明，請透過使用 SQL Server Management Studio (SSMS) 更新 AdventureWorksDW 資料庫中的 DimProduct 資料表，來模擬範例資料的變更。

```sql

UPDATE [AdventureWorksDW].[dbo].[DimProduct]
SET ListPrice = 5000
WHERE EnglishProductName ='Road-250 Red, 58'

```

現在請遵循這些步驟，讓更新後的資料可以透過閘道連線流入資料集，並流入 Power BI 中的報表。

1. 在 Power BI 服務的導覽窗格中，選取並展開 [我的工作區]  。

2. 在 [資料集]  下方，針對 **AdventureWorksProducts** 資料集，選取省略符號 ( **. . .** )，然後選取 [立即重新整理]  。

    ![立即重新重理](./media/service-gateway-sql-tutorial/refresh-now.png)

    請注意右上角，Power BI 正在準備執行所要求的重新整理。

3. 選取 [我的工作區 \> 報表 \> AdventureWorksProducts]。 查看更新資料流經的方式，且現在定價最高的產品為 **Road-250 Red, 58**。

    ![更新直條圖](./media/service-gateway-sql-tutorial/updated-column-chart.png)

## <a name="review-the-refresh-history"></a>檢閱重新整理歷程記錄

定期在重新整理歷程記錄中檢查過去重新整理循環的結果是個好做法。 資料庫認證可能已過期，或是所選取的閘道可能已在排程重新整理時離線。 請遵循這些步驟來檢查重新整理歷程記錄並檢查問題。

1. 在 Power BI 使用者介面的右上角，選取設定齒輪圖示，然後選取 [設定]  。

2. 切換到 [資料集]  ，然後選取您要檢查的資料集，例如 **AdventureWorksProducts**。

3. 選取 [重新整理歷程記錄]  連結來開啟 [重新整理歷程記錄]  對話方塊。

    ![重新整理歷程記錄連結](./media/service-gateway-sql-tutorial/refresh-history-link.png)

4. 在 [已排程] 索引標籤上，注意過去的已排程及隨選重新整理，以及它們的 [開始] 和 [結束] 時間，以及 [已完成] 的 [狀態]，其指出 Power BI 是否已成功執行重新整理。 針對失敗的重新整理，您可以查看錯誤訊息並檢查錯誤詳細資料。

    ![重新整理歷程記錄詳細資料](./media/service-gateway-sql-tutorial/refresh-history-details.png)

    > [!NOTE]
    > OneDrive 索引標籤只針對連線到 Power BI Desktop 檔案、Excel 活頁簿，或是 OneDrive 或 SharePoint Online 上 CSV 檔案的資料集才有用途，如 [Power BI 中的資料重新整理](refresh-data.md)中所詳細描述。

## <a name="clean-up-resources"></a>清除資源

若您不想要繼續使用範例資料，請在 SQL Server Management Studio (SSMS) 中卸除資料庫。 若您不想要使用 SQL Server 資料來源，請從您的資料閘道移除資料來源。 若您只是為了完成本教學課程而安裝它，也請考慮移除資料閘道。 您也應該刪除在您上傳 AdventureWorksProducts.pbix 檔案時 Power BI 建立的 AdventureWorksProducts 資料集和 AdventureWorksProducts 報表。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已探索如何從內部部署 SQL Server 資料庫將資料匯入 Power BI 資料集，以及如何根據排程和隨選來重新整理此資料集，以將 Power BI 中使用此資料集的報表和儀表板維持在更新狀態。 現在您可以深入了解管理 Power BI 中的資料閘道和資料來源。 檢閱＜Power BI 中的資料重新整理＞概念文章也是一個不錯的做法。

- [管理內部部署資料閘道](/data-integration/gateway/service-gateway-manage)
- [管理您的資料來源 - 匯入/排程重新整理](service-gateway-enterprise-manage-scheduled-refresh.md)
- [Power BI 的資料重新整理](refresh-data.md)
