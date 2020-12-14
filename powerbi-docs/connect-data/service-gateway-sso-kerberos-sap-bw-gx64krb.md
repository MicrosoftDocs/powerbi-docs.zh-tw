---
title: 使用 gx64krb5 將 Kerberos 用於 SAP BW 的單一登入 (SSO)
description: 設定您的 SAP BW 伺服器，以使用 gx64krb5 從 Power BI 服務啟用 SSO
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: how-to
ms.date: 12/04/2020
LocalizationGroup: Gateways
ms.openlocfilehash: c48abec54e62625a7e32bb33f773995cdb8a3c47
ms.sourcegitcommit: 513c4b884a58e1da2680579339c24c46091bbfb2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96613892"
---
# <a name="use-kerberos-for-single-sign-on-sso-to-sap-bw-using-gx64krb5"></a>使用 gx64krb5 將 Kerberos 用於 SAP BW 的單一登入 (SSO)

本文描述如何設定您的 SAP BW 資料來源，以使用 gx64krb5 從 Power BI 服務啟用 SSO。

> [!IMPORTANT]
> 針對 Power BI 中的內部部署資料閘道，SAP 已不再支援 gx64krb5。 因此，Microsoft 也已停止在此案例中使用 gx64krb5 的支援。 現有的連線將會繼續運作，但從 2021 年 2 月開始，您將無法為此案例建立新的連線。 請改用 CommonCryptoLib。 

> [!NOTE]
> 除了[設定 Kerberos SSO](service-gateway-sso-kerberos.md) 中的步驟之外，您還可以完成本文中的步驟，以在 Power BI 服務中針對 SAP BW 應用程式伺服器型報表啟用 SSO 型重新整理。 不過，Microsoft 建議使用 CommonCryptoLib (而不是 gx64krb5) 作為您的 SNC 程式庫。 SAP 不再支援 gx64krb5，因此相較於 CommonCryptoLib，針對閘道進行設定所需的步驟會複雜許多。 如需如何使用 CommonCryptoLib 設定 SSO 的資訊，請參閱[使用 CommonCryptoLib 針對 SSO 設定 SAP BW](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md)。 您可使用 CommonCryptoLib「或」gx64krb5 作為 SNC 程式庫，但請勿同時使用。 請勿同時完成這兩個程式庫的設定步驟。

本指南是完整的；如果您已經完成一些所述的步驟，則可予以略過。 例如，您可能已經使用 gx64krb5 為 SSO 設定了您的 SAP BW 伺服器。

## <a name="set-up-gx64krb5-on-the-gateway-machine-and-the-sap-bw-server"></a>在閘道電腦和 SAP BW 伺服器上設定 gx64krb5

> [!NOTE]
> SAP 已不再支援 gx64krb5.dll 程式庫。 如需詳細資訊，請參閱 [SAP Note 352295](https://launchpad.support.sap.com/#/notes/352295) (SAP 附註 352295)。 請注意，gx64krb5.dll 不允許從資料閘道到 SAP BW 訊息伺服器的 SSO 連線；其只能連線到 SAP BW 應用程式伺服器。 如果您使用 [CommonCryptoLib](service-gateway-sso-kerberos-sap-bw-commoncryptolib.md) 作為 SNC 程式庫，則不會有這個限制。 雖然其他 SNC 程式庫也可能適用於 BW SSO，但 Microsoft 並未正式支援這些程式庫。

用戶端和伺服器都必須使用 gx64krb5 程式庫才能透過閘道完成 SSO 連線。 亦即，用戶端和伺服器都必須使用相同的 SNC 程式庫。

1. 從 [SAP Note 2115486](https://launchpad.support.sap.com/) 下載 gx64krb5.dll (需要 SAP S 使用者)。 請確認您具備 1.0.11.x 以上的版本。 此外，如果您想要先在 SAP GUI 中測試 SSO 連線，再嘗試透過閘道的 SSO 連線，則建議下載 gsskrb5.dll (32 位元版本的程式庫)。 需要 32 位元版本才能使用 SAP GUI 進行測試，因為 SAP GUI 只有 32 位元版本。

1. 將 gx64krb5.dll 放在閘道電腦上可由閘道服務使用者存取的位置。 如果您想要使用 SAP GUI 來測試 SSO 連線，請同時在電腦上放置 gsskrb5.dll 的複本，並將 **SNC_LIB** 環境變數設定為指向該位置。 閘道服務使用者和服務使用者將模擬的 Active Directory (AD) 使用者都需要 gx64krb5.dll 複本讀取和執行權限。 我們建議將 .dll 的權限授與 [已驗證的使用者] 群組。 基於測試目的，也可以將這些權限明確授與給閘道服務使用者和您用來測試的 Active Directory 使用者。

1. 如果您的 BW 伺服器尚未設定好使用 gx64krb5 進行 SSO，請將此 .dll 的另一個複本放在 SAP BW 伺服器電腦上 SAP BW 伺服器可存取位置中。 

    如需設定 gx64krb5.dll 以與 SAP BW 伺服器搭配使用的詳細資訊，請參閱 [SAP 文件](https://launchpad.support.sap.com/#/notes/2115486) (需要 SAP S 使用者)。

1. 在用戶端和伺服器電腦上，設定 **SNC_LIB** 和 **SNC_LIB_64** 環境變數： 
    - 如果您使用 gsskrb5.dll，請將 **SNC_LIB** 變數設定為其絕對路徑。 
    - 如果您使用 gx64krb5.dll，請將 **SNC_LIB_64** 變數設定為其絕對路徑。

## <a name="configure-an-sap-bw-service-user-and-enable-snc-communication-on-the-bw-server"></a>設定 SAP BW 服務使用者，並在 BW 伺服器上啟用 SNC 通訊

如果您尚未設定 SAP BW 伺服器以使用 gx64krb5 進行 SNC 通訊 (例如 SSO)，請完成本節。

> [!NOTE]
> 本節假設您已經建立 BW 的服務使用者，並將適當的 SPN 繫結到該使用者 (亦即，以 *SAP/* 開頭的名稱)。

1. 授與服務使用者對 SAP BW 應用程式伺服器的存取權：

    1. 在 SAP BW 伺服器電腦上，將服務使用者新增至本機系統管理員群組。 開啟 [電腦管理] 程式，然後找出您伺服器的本機系統管理員群組。 

        ![[電腦管理] 程式](media/service-gateway-sso-kerberos/computer-management.png)

    1. 按兩下本機系統管理員群組，然後選取 [新增] 將您的服務使用者新增至該群組。 

    1. 選取 [檢查名稱] 來確保已正確輸入名稱，然後選取 [確定]。

1. 將 SAP BW 伺服器服務使用者設定為在 SAP BW 伺服器電腦上啟動 SAP BW 伺服器服務的使用者：

    1. 開啟 [執行]，然後輸入 **Services.msc**。 

    1. 尋找對應到 SAP BW 應用程式伺服器執行個體的服務、以滑鼠右鍵按一下，然後選取 [屬性]。

        ![服務的螢幕擷取畫面，其中已醒目提示 [屬性]](media/service-gateway-sso-kerberos/server-properties.png)

    1. 切換至 [登入] 索引標籤，然後將使用者變更為您的 SAP BW 服務使用者。 

    1. 輸入使用者的密碼，然後選取 [確定]。

1. 在 SAP 登入中登入您的伺服器，並使用 RZ10 交易來設定下列設定檔參數：

    1. 將 **snc/identity/as** 設定檔參數設定為 p:&lt;您剛剛建立的 SAP BW 服務使用者&gt;。 例如，*p:BWServiceUser\@MYDOMAIN.COM*。 請注意，*p:* 會在服務使用者的 UPN 前面，而不是像使用 CommonCryptoLib 作為 SNC 程式庫時，在 UPN 前面的 *p:CN=* 。

    1. 將 **snc/gssapi\_lib** 設定檔參數設為 &lt;BW 伺服器上的 gx64krb5.dll 路徑&gt;。 將程式庫放在 SAP BW 應用程式伺服器可以存取的位置。

    1. 設定下列其他設定檔參數，並根據您的需要來變更值。 最後五個選項可讓用戶端無須設定 SNC 即可使用 SAP 登入連線至 SAP BW 伺服器。

        | **設定** | **值** |
        | --- | --- |
        | snc/data\_protection/max | 3 |
        | snc/data\_protection/min | 1 |
        | snc/data\_protection/use | 9 |
        | snc/accept\_insecure\_cpic | 1 |
        | snc/accept\_insecure\_gui | 1 |
        | snc/accept\_insecure\_r3int\_rfc | 1 |
        | snc/accept\_insecure\_rfc | 1 |
        | snc/permit\_insecure\_start | 1 |

    1. 將 **snc/enable** 屬性設定為 1。

1. 設定這些設定檔參數之後，請在伺服器電腦上開啟 SAP 管理主控台並重新啟動 SAP BW 執行個體。 

   如果伺服器無法啟動，請確認設定檔參數已正確設定。 如需設定檔參數設定的詳細資訊，請參閱 [SAP documentation](https://help.sap.com/saphelp_nw70ehp1/helpdata/en/e6/56f466e99a11d1a5b00000e835363f/frameset.htm) (SAP 文件)。 您也可以參閱本文中的[疑難排解](#troubleshooting)一節。

## <a name="map-an-sap-bw-user-to-an-active-directory-user"></a>將 SAP BW 使用者對應至 Active Directory 使用者

如果您還沒這麼做，請將 Active Directory 使用者對應至 SAP BW 應用程式伺服器使用者，並在 SAP 登入中測試 SSO 連線。

1. 使用 SAP 登入來登入您的 SAP BW 伺服器。 執行交易 SU01。

1. 針對 [使用者]，輸入您要為其啟用 SSO 連線的 SAP BW 使用者。 選取 SAP 登入視窗左上角附近的 **編輯** 圖示 (畫筆圖示)。

    ![SAP BW [使用者維護] 畫面](media/service-gateway-sso-kerberos/user-maintenance.png)

1. 選取 [SNC] 索引標籤。在 SNC 名稱輸入方塊中，輸入 p:&lt;您的 Active Directory 使用者&gt;@&lt;您的網域&gt;。 針對 SNC 名稱，Active Directory 使用者 UPN 前面必須加上 *p:* 。 請注意，UPN 會區分大小寫。

   您指定的 Active Directory 使用者，應屬於要為其啟用 SAP BW 應用程式伺服器 SSO 存取權的人員或組織。 例如，如果您希望為使用者 testuser\@TESTDOMAIN.COM 啟用 SSO 存取權，請輸入 *p:testuser\@TESTDOMAIN.COM*。

    ![SAP BW [維護使用者] 畫面](media/service-gateway-sso-kerberos/maintain-users.png)

1. 選取畫面左上角附近的 **儲存** 圖示 (磁碟片影像)。

## <a name="test-sign-in-via-sso"></a>測試透過 SSO 登入

請驗證您是否可以使用 SAP 登入，透過 SSO 來以已啟用 SSO 存取權的 Active Directory 使用者身分登入伺服器：

1. 以您剛已啟用 SSO 存取權的 Active Directory 使用者身分，登入網域中已安裝 SAP 登入的電腦。 啟動 SAP 登入，並建立新的連線。

1. 將您稍早下載的 gsskrb5.dll 檔案，複製到您所登入電腦上的位置。 將 **SNC_LIB** 環境變數設定為這個位置的絕對路徑。

1. 啟動 SAP 登入，並建立新的連線。

1. 在 [Create New System Entry] \(建立新的系統項目\) 畫面中，選取 [User Specified System] \(使用者指定的系統\)，然後選取 [下一步]。

    ![[Create New System Entry] \(建立新的系統項目\) 畫面](media/service-gateway-sso-kerberos/new-system-entry.png)

1. 在下一個畫面填入適當的詳細資料，包括應用程式伺服器、執行個體數目以及系統識別碼。 然後選取 [完成]。

1. 以滑鼠右鍵按一下新的連線、選取 [屬性]，然後選取 [網路] 索引標籤。 

1. 在 [SNC Name] \(SNC 名稱\) 方塊中，輸入 p:&lt;SAP BW 服務使用者的 UPN&gt;。 例如，*p:BWServiceUser\@MYDOMAIN.COM*。 選取 [確定]。

    ![[System Entry Properties] \(系統項目屬性\) 畫面](media/service-gateway-sso-kerberos/system-entry-properties.png)

1. 按兩下您剛才建立的連線，以嘗試與 SAP BW 伺服器建立 SSO 連線。 

   如果連線成功，請繼續下一節。 如果未成功，請檢閱此文件中先前的步驟，確定這些步驟已正確完成，或檢閱[疑難排解](#troubleshooting)一節。 如果您在此內容中無法透過 SSO 連線至 SAP BW 伺服器，則無法在閘道內容中使用 SSO 連線至 SAP BW 伺服器。

## <a name="add-registry-entries-to-the-gateway-machine"></a>新增登錄項目至閘道電腦

將所需登錄項目新增至閘道安裝所在電腦的登錄中，同時安裝至 Power BI Desktop 所要連線的電腦上。 若要新增這些登錄項目，請執行下列命令：

- ```REG ADD HKLM\SOFTWARE\Wow6432Node\SAP\gsskrb5 /v ForceIniCredOK /t REG_DWORD /d 1 /f```

- ```REG ADD HKLM\SOFTWARE\SAP\gsskrb5 /v ForceIniCredOK /t REG_DWORD /d 1 /f```

## <a name="add-a-new-sap-bw-application-server-data-source-to-the-power-bi-service-or-edit-an-existing-one"></a>將新的 SAP BW 應用程式伺服器資料來源新增至 Power BI 服務，或編輯現有的資料來源

1. 在資料來源設定視窗中，輸入 SAP BW 應用程式伺服器的 [主機名稱]、[系統編號] 和 [用戶端識別碼]，如同您用來從 Power BI Desktop 登入 SAP BW 伺服器的資訊。

1. 在 [SNC 合作夥伴名稱] 欄位中，輸入 p:&lt;您對應至 SAP BW 服務使用者的 SPN&gt;。 例如，如果 SPN 是 SAP/BWServiceUser\@MYDOMAIN.COM，則您應該在 [SNC 合作夥伴名稱] 欄位中輸入 p:SAP/BWServiceUser\@MYDOMAIN.COM。

1. 針對 SNC 程式庫，選取 **SNC\_LIB** 或 **SNC\_LIB\_64**。 請確定閘道機器上的 **SNC\_LIB\_64** 指向 gx64krb5.dll。 或者，您可以選取 [自訂] 選項，並提供閘道電腦上的 gx64krb5.dll 絕對路徑。

1. 選取 [Use SSO via Kerberos for DirectQuery queries] \(透過 Kerberos 使用 SSO 進行 DirectQuery 查詢)，然後選取 [套用]。 如果測試連線不成功，請確認已正確完成先前的安裝和設定步驟。

1. [執行 Power BI 報表](service-gateway-sso-kerberos.md#run-a-power-bi-report)

## <a name="troubleshooting"></a>疑難排解

### <a name="troubleshoot-gx64krb5-configuration"></a>針對 gx64krb5 設定進行疑難排解

如果您遇到下列任何問題，請遵循下列步驟針對 gx64krb5 安裝和 SSO 連線進行疑難排解：

* 完成 gx64krb5 設定步驟時遇到錯誤。 例如，變更設定檔參數之後，SAP BW 伺服器無法啟動。 檢視伺服器記錄檔 (伺服器電腦上的 …work\dev\_w0) 來針對這些錯誤進行疑難排解。 

* 因為登入失敗，所以無法啟動 SAP BW 服務。 設定 SAP BW *start-as* 使用者時，可能提供了錯誤的密碼。 以 Active Directory 環境中電腦上 SAP BW 服務使用者身分登入來驗證密碼。

* 您收到導致伺服器無法啟動的基礎資料來源認證 (例如 SQL Server) 相關錯誤，請驗證已授與服務使用者對 SAP BW 資料庫的存取權。

* 您收到下列訊息：(GSS-API) 指定的目標不明或無法連線。 這個錯誤通常表示指定了錯誤的 SNC 名稱。 在用戶端應用程式中，在服務使用者的 UPN 前面，請務必只使用 *p:* ，而不要使用 *p:CN=* 。

* 您收到下列訊息：(GSS-API) 提供的名稱無效。 確認 *p:* 是伺服器 SNC 身分識別設定檔參數的值。

* 您收到下列訊息：(SNC 錯誤) 找不到指定的模組。 這個錯誤通常是因為將 gx64krb5.dll 放在需要提高權限 (../管理員權限) 才能存取的位置而導致的。

### <a name="troubleshoot-gateway-connectivity-issues"></a>針對閘道連線問題進行疑難排解

1. 檢查閘道記錄。 開啟閘道設定應用程式，然後選取 [診斷]、[匯出記錄]。 最新錯誤會在您檢查的任何記錄檔結尾。

    ![[內部部署的資料閘道] 應用程式，其中已醒目提示診斷](media/service-gateway-sso-kerberos/gateway-diagnostics.png)

1. 開啟 SAP BW 追蹤，並檢閱產生的記錄檔。 有許多不同類型的 SAP BW 追蹤可供使用 (例如 CPIC 追蹤)：

   a. 若要啟用 CPIC 追蹤，請設定兩個環境變數：**CPIC\_TRACE** 和 **CPIC\_TRACE\_DIR**.

      第一個變數會設定追蹤層級，第二個變數則會設定追蹤檔案目錄。 此目錄必須是 [已驗證的使用者] 群組成員可以寫入的位置。 
 
    b. 將 **CPIC\_TRACE** 設為 *3*，並將 **CPIC\_TRACE\_DIR** 設為您想要寫入追蹤檔案的任何目錄。 例如：

      ![CPIC 追蹤](media/service-gateway-sso-kerberos/cpic-tracing.png)

    c. 重現問題，並確定 **CPIC\_TRACE\_DIR** 包含追蹤檔案。 
    
    d. 檢查追蹤檔案的內容，以判斷執行問題。 例如，您可能會發現 gx64krb5.dll 未正確載入，或 Active Directory 使用者與您預期起始 SSO 連線嘗試的使用者不同。

## <a name="next-steps"></a>後續步驟

如需內部部署資料閘道和 DirectQuery 的詳細資訊，請參閱下列資源：

* [什麼是內部部署的資料閘道？](/data-integration/gateway/service-gateway-onprem)
* [Power BI 中的 DirectQuery](desktop-directquery-about.md)
* [DirectQuery 支援的資料來源](power-bi-data-sources.md)
* [DirectQuery 和 SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery 和 SAP HANA](desktop-directquery-sap-hana.md)
