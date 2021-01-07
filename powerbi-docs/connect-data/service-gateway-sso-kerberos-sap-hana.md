---
title: 將 Kerberos 用於 SAP HANA 的單一登入 (SSO)
description: 設定您的 SAP HANA 伺服器，以從 Power BI 服務啟用 SSO
author: arthiriyer
ms.author: arthii
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: how-to
ms.date: 12/16/2020
LocalizationGroup: Gateways
ms.openlocfilehash: 3f50b174e8293d75a0077e1799cb64ff4fdcd696
ms.sourcegitcommit: 5c09d121d3205e65fb33a2eca0e60bc30e777773
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/18/2020
ms.locfileid: "97675112"
---
# <a name="use-kerberos-for-single-sign-on-sso-to-sap-hana"></a>將 Kerberos 用於 SAP HANA 的單一登入 (SSO)

> [!IMPORTANT]
> 由於 [SAP 已不再支援 OpenSSL](https://help.sap.com/viewer/b3ee5778bc2e4a089d3299b82ec762a7/2.0.05/en-US/de15ffb1bb5710148386ffdfd857482a.html)，因此 Microsoft 也已停止其支援。 現有的連線將會繼續運作，但從 2021 年 2 月開始，您將無法建立新的連線。 往後，請改為使用 CommonCryptoLib。

本文描述如何設定您的 SAP HANA 資料來源，以從 Power BI 服務啟用 SSO。

> [!NOTE]
> 在您嘗試重新整理使用 Kerberos SSO 的 SAP HANA 架構報表之前，請先完成本文中的步驟，以及[設定 Kerberos SSO](service-gateway-sso-kerberos.md) 中的步驟。

## <a name="enable-sso-for-sap-hana"></a>啟用 SAP HANA 的 SSO

若要啟用 SAP HANA 的 SSO，請遵循下列步驟：

1. 請確定 SAP HANA 伺服器執行的是所需最低版本，這取決於 SAP HANA 伺服器的平台層級：
   - [HANA 2 SPS 01 Rev 012.03](https://launchpad.support.sap.com/#/notes/2557386)
   - [HANA 2 SPS 02 Rev 22](https://launchpad.support.sap.com/#/notes/2547324)
   - [HANA 1 SP 12 Rev 122.13](https://launchpad.support.sap.com/#/notes/2528439)

2. 在閘道電腦上安裝最新的 SAP HANA ODBC 驅動程式。 最低版本為 2017 年 8 月的 HANA ODBC 2.00.020.00 版。

3. 請確定已針對 Kerberos 架構 SSO 設定 SAP HANA 伺服器。 如需使用 Kerberos 為 SAP HANA 設定 SSO 的詳細資訊，請參閱 "SAP HANA Security Guide" 中的 "[Single Sign-on Using Kerberos](https://help.sap.com/viewer/b3ee5778bc2e4a089d3299b82ec762a7/2.0.03/1885fad82df943c2a1974f5da0eed66d.html)"。 另請參閱該頁面中的連結，尤其是 SAP Note 1837331 – 如何使用 HANA DBSSO Kerberos/Active Directory。

我們也建議您遵循這些額外步驟，這可稍微提升效能：

1. 在閘道安裝目錄中尋找並開啟這個設定檔：Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config。

2. 尋找 `FullDomainResolutionEnabled` 屬性，並將其值變更為 `True`。

    ```xml
    <setting name=" FullDomainResolutionEnabled " serializeAs="String">
          <value>True</value>
    </setting>
    ```

現在，請[執行 Power BI 報表](service-gateway-sso-kerberos.md#run-a-power-bi-report)。

## <a name="next-steps"></a>後續步驟

如需內部部署資料閘道和 DirectQuery 的詳細資訊，請參閱下列資源：

* [什麼是內部部署的資料閘道？](/data-integration/gateway/service-gateway-onprem)
* [Power BI 中的 DirectQuery](desktop-directquery-about.md)
* [DirectQuery 支援的資料來源](power-bi-data-sources.md)
* [DirectQuery 和 SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery 和 SAP HANA](desktop-directquery-sap-hana.md)
