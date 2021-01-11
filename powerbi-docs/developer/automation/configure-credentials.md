---
title: 以程式設計方式為 Power BI 內嵌式分析設定認證，以便取得更佳的內嵌 BI 見解
description: 將 Power BI 自動化時，如何以程式設計方式設定認證。 使用 Power BI 內嵌式分析，以便取得更佳的內嵌 BI 見解。
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: how-to
ms.date: 06/23/2020
ms.openlocfilehash: c87ca689d804c909ca3a6ca9544ac1a4568c8b86
ms.sourcegitcommit: eeaf607e7c1d89ef7312421731e1729ddce5a5cc
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2021
ms.locfileid: "97887630"
---
# <a name="configure-credentials-programmatically-for-power-bi"></a>以程式設計的方式為 Power BI 設定認證

請遵循此文章中的步驟，來以程式設計的方式為 Power BI 設定認證。

>[!NOTE]
>* 呼叫的使用者必須是資料集擁有者，或閘道管理員。您也可以使用[服務主體](../embedded/embed-service-principal.md)。 例如，服務主體可以是資料集擁有者。
>* 雲端資料來源及其對應的認證會在使用者層級進行管理。

## <a name="update-credentials-flow-for-data-sources"></a>為資料來源更新認證流程

1. 呼叫 [Get Datasources](/rest/api/power-bi/datasets/getdatasourcesingroup) 來找到資料集的資料來源。 各資料來源的回應本文中會有類型、連線詳細資料、閘道與資料來源識別碼。

    ```csharp
    // Select a datasource
    var datasources = pbiClient.Datasets.GetDatasources(datasetId).Value;
    var datasource = datasources.First();
    ```

2. 依照認證類型，根據[更新資料來源範例](/rest/api/power-bi/gateways/updatedatasource)來建置認證字串。

    # <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

    ```csharp
    var credentials =  new BasicCredentials(username: "username", password :"*****");
    ```

    # <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

     ```csharp
    var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
    ```

    ---

    >[!NOTE]
    >如果使用的是雲端資料來源，請不要遵循本節中的後續步驟。 透過呼叫[更新資料來源](/rest/api/power-bi/gateways/updatedatasource) (英文)，使用在步驟 1 取得的閘道識別碼和資料來源識別碼來設定認證。 

3. 呼叫 [Get Gateway](/rest/api/power-bi/gateways/getgateways)來擷取閘道公開金鑰。

    ```csharp
    var gateway = pbiClient.Gateways.GetGatewayById(datasource.GatewayId);
    ```

4. 加密認證。

    # <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

    ```csharp
    var credentialsEncryptor = new AsymmetricKeyEncryptor(gateway.publicKey);
    ```

    # <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

    以步驟 2 中的閘道公開金鑰加密認證字串。 不同閘道版本可能有不同的公開金鑰大小。 請參閱 SDK 程式碼中的下列範例 (可在 [PowerBI-CSharp GitHub 存放庫](https://github.com/microsoft/PowerBI-CSharp/tree/master/sdk/PowerBI.Api/Extensions) \(英文\) 中找到)：
    * [AsymmetricKeyEncryptor.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AsymmetricKeyEncryptor.cs)
    * [Asymmetric1024KeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/Asymmetric1024KeyEncryptionHelper.cs)
    * [AsymmetricHigherKeyEncryptionHelper.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AsymmetricHigherKeyEncryptionHelper.cs)
    * [AuthenticatedEncryption.cs](https://github.com/microsoft/PowerBI-CSharp/blob/master/sdk/PowerBI.Api/Extensions/AuthenticatedEncryption.cs) 

    ---  

5. 使用加密的認證來建置認證詳細資料。

    # <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

    使用 AssymetricKeyEncryptor 類別搭配在 **步驟 3** 中擷取的公開金鑰。

    ```csharp
    var credentialDetails = new CredentialDetails(
            credentials,
            PrivacyLevel.Private,
            EncryptedConnection.Encrypted,
            credentialsEncryptor);
    ```


    # <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

    ```csharp
    var credentialDetails = new CredentialDetails(
            credentials,
            CredentialTypeEnum.Basic,
            EncryptedConnectionEnum.Encrypted,
            EncryptionAlgorithmEnum.None,
            PrivacyLevelEnum.Private);
    ```

    ---

6. 呼叫 [Update Datasource](/rest/api/power-bi/gateways/updatedatasource)來設定認證。

    ```csharp
    pbiClient.Gateways.UpdateDatasource(gatewayId, datasourceId, credentialDetails);
    ```

## <a name="configure-a-new-data-source-for-a-data-gateway"></a>為資料閘道設定新的資料來源

1. 在您的電腦上安裝[內部部署資料閘道](https://powerbi.microsoft.com/gateway/)。

2. 呼叫 [Get Gateway](/rest/api/power-bi/gateways/getgateways)來擷取閘道識別碼和公開金鑰。

    ```csharp
    // Select a gateway
    var gateways = pbiClient.Gateways.GetGateways().Value;
    var gateway = gateways.First();
    ```

3. 使用 **步驟 2** 中擷取的閘道公開金鑰，以 [為資料來源更新認證流程](#update-credentials-flow-for-data-sources)中所述的相同方式建置認證詳細資料。

4. 建置要求本文。

    ```csharp
    var request = new PublishDatasourceToGatewayRequest(
            dataSourceType: "SQL",
            connectionDetails: "{\"server\":\"myServer\",\"database\":\"myDatabase\"}",
            credentialDetails: credentialDetails,
            dataSourceName: "my sql datasource");
    ```

5. 呼叫 [Create Datasource](/rest/api/power-bi/gateways/createdatasource) API。

    ```csharp
    pbiClient.Gateways.CreateDatasource(gateway.Id, request);
    ```

## <a name="credential-types"></a>認證類型

當您在 **企業內部部署閘道** 下使用 [Power BI Rest API](/rest/api/power-bi/) 呼叫 [建立資料來源](/rest/api/power-bi/gateways/createdatasource)或 [更新資料來源](/rest/api/power-bi/gateways/updatedatasource)時，需要使用閘道的公用金鑰來加密認證值。

>[!NOTE]
>.NET SDK v3 也可以執行下面所列的 .NET SDK v2 範例。

### <a name="windows-and-basic-credentials"></a>Windows 與基本認證

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
// Windows credentials
var credentials = new WindowsCredentials(username: "john", password: "*****");

// Or

// Basic credentials
var credentials = new BasicCredentials(username: "john", password: "*****");

var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"username\", \"value\":\"john\"},{\"name\":\"password\", \"value\":\"*****\"}]}";
```

---

### <a name="key-credentials"></a>金鑰認證

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
var credentials = new KeyCredentials("TestKey");
var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"key\", \"value\":\"ec....LA=\"}]}";
```

---

**OAuth2 認證**

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
var credentials = new OAuth2Credentials("TestToken");
var credentialsEncryptor = new AsymmetricKeyEncryptor(publicKey);
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.Encrypted, credentialsEncryptor);
```

# <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":[{\"name\":\"accessToken\", \"value\":\"eyJ0....fwtQ\"}]}";
```

---

**匿名認證**

# <a name="net-sdk-v3"></a>[.NET SDK v3](#tab/sdk3)

```csharp
var credentials = new AnonymousCredentials();
var credentialDetails = new CredentialDetails(credentials, PrivacyLevel.Private, EncryptedConnection.NotEncrypted);
```

# <a name="net-sdk-v2"></a>[.NET SDK v2](#tab/sdk2)

```csharp
var credentials = "{\"credentialData\":\"\"}";
```

---

## <a name="troubleshooting"></a>疑難排解

### <a name="no-gateway-and-data-source-id-found-when-calling-get-data-sources"></a>呼叫 get data sources 時未找到任何閘道和資料來源識別碼

這項問題代表資料集未繫結至閘道。 建立新的資料集時，系統會針對每個雲端連線，在使用者的雲端閘道上自動建立沒有認證的資料來源。 這個閘道會用來儲存雲端連線的認證。

在您建立資料集後，會自動建立資料集與合適閘道的繫結，其中包括所有連線的相符資料來源。 如果沒有該種閘道或有多個合適的閘道，則自動繫結會失敗。

如果您使用內部部署資料集，請建立缺少的內部部署資料來源，並使用[繫結至閘道](/rest/api/power-bi/datasets/bindtogateway) \(英文\) 手動將資料集繫結至閘道。

若要探索可繫結的閘道，請使用[探索閘道](/rest/api/power-bi/datasets/discovergateways) \(英文\)。
