---
title: 建立 Power BI 視覺效果的 SSL 憑證
description: 了解如何使用 Windows、Mac 或 Linux 中的 Power BI Visual Tools，或以手動方式產生 SSL 憑證。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: reference
ms.date: 05/08/2020
ms.openlocfilehash: f6f458d2fe82668074d7cfb046cb5a72afa35c38
ms.sourcegitcommit: 50b21718a167c2b131313b4135c8034c6f027597
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/14/2020
ms.locfileid: "92048778"
---
# <a name="create-an-ssl-certificate"></a>建立 SSL 憑證

此文章說明如何產生並安裝 Power BI 視覺效果的安全通訊端層 (SSL) 憑證。

針對 Windows、macOS X 與 Linux 程序，您必須已安裝 Power BI Visual Tools **.pbiviz** 套件。 如需詳細資訊，請參閱[設定環境以開發 Power BI 視覺效果](./environment-setup.md)。 

## <a name="create-a-certificate-on-windows"></a>在 Windows 上建立憑證

若要在 Windows 8 與更新版本上使用 PowerShell `New-SelfSignedCertificate` Cmdlet 來產生憑證，請執行下列命令：

```powershell
pbiviz --install-cert
```

針對 Windows 7，`pbiviz` 工具要求必須能從命令列存取 OpenSSL 公用程式。 若要安裝 OpenSSL，請移至 [OpenSSL](https://www.openssl.org) \(英文\) 或 [OpenSSL 二進位檔](https://wiki.openssl.org/index.php/Binaries) \(英文\)。

如需安裝憑證的詳細資訊與指示，請參閱[建立並安裝適用於 Windows 的憑證](./environment-setup.md#create-and-install-a-certificate)。

## <a name="create-a-certificate-on-macos-x"></a>在 macOS X 上建立憑證

macOS X 作業系統通常會提供 OpenSSL 公用程式。

您也可以透過執行下列其中一個命令來安裝 OpenSSL 公用程式：

- 從 *Brew* 套件管理員：
  
  ```cmd
  brew install openssl
  brew link openssl --force
  ```

- 使用 *MacPorts*：
  
  ```cmd
  sudo port install openssl
  ```

安安裝 OpenSSL 公用程式之後，請執行下列命令以產生新憑證：

```cmd
pbiviz --install-cert
```

如需詳細資訊與指示，請參閱[建立並安裝憑證](./environment-setup.md#create-and-install-a-certificate)中的 [OSX] 索引標籤。

## <a name="create-a-certificate-on-linux"></a>在 Linux 上建立憑證

Linux 作業系統通常會提供 OpenSSL 公用程式。

開始之前，請執行下列命令，確定已安裝 `openssl` 與 `certutil`：

```sh
which openssl
which certutil
```

如果未安裝 `openssl` 與 `certutil`，請安裝 `openssl` 與 `libnss3` 公用程式。

### <a name="create-the-ssl-configuration-file"></a>建立 SSL 設定檔

建立名為 */tmp/openssl.cnf* 且包含下列文字的檔案：

```
authorityKeyIdentifier=keyid,issuer
basicConstraints=CA:FALSE
keyUsage = digitalSignature, nonRepudiation, keyEncipherment, dataEncipherment
subjectAltName = @alt_names

[ alt_names ]
DNS.1=localhost
```

### <a name="generate-root-certificate-authority"></a>產生根憑證授權單位

若要產生用來簽署本機憑證的根憑證授權單位 (CA)，請執行下列命令：

```sh
touch $HOME/.rnd
openssl req -x509 -nodes -new -sha256 -days 1024 -newkey rsa:2048 -keyout /tmp/local-root-ca.key -out /tmp/local-root-ca.pem -subj "/C=US/CN=Local Root CA/O=Local Root CA"
openssl x509 -outform pem -in /tmp/local-root-ca.pem -out /tmp/local-root-ca.crt
```

### <a name="generate-a-certificate-for-localhost"></a>產生 localhost 的憑證 

若要使用產生的 CA 與 *openssl.cnf* 來產生 `localhost` 的憑證，請執行下列命令：

```sh
PBIVIZ=`which pbiviz`
PBIVIZ=`dirname $PBIVIZ`
PBIVIZ="$PBIVIZ/../lib/node_modules/powerbi-visuals-tools/certs"
# Make sure that $PBIVIZ contains the correct certificate directory path. ls $PBIVIZ should list 'blank' file.
openssl req -new -nodes -newkey rsa:2048 -keyout $PBIVIZ/PowerBIVisualTest_private.key -out $PBIVIZ/PowerBIVisualTest.csr -subj "/C=US/O=PowerBI Visuals/CN=localhost"
openssl x509 -req -sha256 -days 1024 -in $PBIVIZ/PowerBIVisualTest.csr -CA /tmp/local-root-ca.pem -CAkey /tmp/local-root-ca.key -CAcreateserial -extfile /tmp/openssl.cnf -out $PBIVIZ/PowerBIVisualTest_public.crt
```

### <a name="add-root-certificates"></a>新增根憑證

若要將根憑證新增至 Chrome 瀏覽器的資料庫，請執行：

```sh
certutil -A -n "Local Root CA" -t "CT,C,C" -i /tmp/local-root-ca.pem -d sql:$HOME/.pki/nssdb
```

若要將根憑證新增至 Chrome 瀏覽器的資料庫，請執行：

```sh
for certDB in $(find $HOME/.mozilla* -name "cert*.db")
do
certDir=$(dirname ${certDB});
certutil -A -n "Local Root CA" -t "CT,C,C" -i /tmp/local-root-ca.pem -d sql:${certDir}
done
```

若要新增全系統的根憑證，請執行：

```sh
sudo cp /tmp/local-root-ca.pem /usr/local/share/ca-certificates/
sudo update-ca-certificates
```

### <a name="remove-root-certificates"></a>移除根憑證

若要移除根憑證，請執行：

```sh
sudo rm /usr/local/share/ca-certificates/local-root-ca.pem
sudo update-ca-certificates --fresh
```

## <a name="generate-a-certificate-manually"></a>手動產生憑證

您也可以使用 OpenSSL 手動產生 SSL 憑證。 您可以指定任何工具來產生憑證。

如果已安裝 OpenSSL 公用程式，請透過執行下列命令來產生新憑證：

```cmd
openssl req -x509 -newkey rsa:4096 -keyout PowerBIVisualTest_private.key -out PowerBIVisualTest_public.crt -days 365
```

您通常可透過執行下列其中一個命令來找到 `PowerBI-visuals-tools` Web 伺服器憑證：

- 針對工具的全域執行個體：
  
  ```cmd
  %appdata%\npm\node_modules\PowerBI-visuals-tools\certs
  ```

- 針對工具的本機執行個體：
  
  ```cmd
  <Power BI visual project root>\node_modules\PowerBI-visuals-tools\certs
  ```

### <a name="pem-format"></a>PEM 格式

如果您使用隱私增強郵件 (PEM) 憑證格式，請將憑證檔案儲存為 *PowerBIVisualTest_public.crt*，然後將私密金鑰儲存為 *PowerBIVisualTest_private.key*。

### <a name="pfx-format"></a>PFX 格式

如果您使用個人資訊交換 (PFX) 憑證格式，請將憑證檔案儲存為 *PowerBIVisualTest_public.pfx*。

如果您的 PFX 憑證檔案需要複雜密碼：

1. 在設定檔中，請指定：
   
   ```cmd
   \PowerBI-visuals-tools\config.json
   ```
   
1. 在 `server` 區段中，透過取代 \<YOUR PASSPHRASE> 預留位置來指定複雜密碼：

    ```cmd
    "server":{
        "root":"webRoot",
        "assetsRoute":"/assets",
        "privateKey":"certs/PowerBIVisualTest_private.key",
        "certificate":"certs/PowerBIVisualTest_public.crt",
        "pfx":"certs/PowerBIVisualTest_public.pfx",
        "port":"8080",
        "passphrase":"<YOUR PASSPHRASE>"
    }
    ```

## <a name="next-steps"></a>後續步驟
- [開發 Power BI 圓形卡片視覺效果](develop-circle-card.md)
- [Power BI 視覺效果範例](samples.md)
- [將 Power BI 視覺效果發佈到 AppSource](office-store.md)