---
title: Modules Azure Active Directory pour Node.js
description: "Références pour les modules Azure Active Directory pour Node.js"
keywords: "Azure, nœud, SDK, API, stockage, Node.js, Javascript"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: active-directory
ms.openlocfilehash: d0084faa78986bd5518526c6eb84b9c13fdb10bf
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-active-directory-modules-for-nodejs"></a>Modules Azure Active Directory pour Node.js

## <a name="overview"></a>Vue d'ensemble

La [bibliothèque d’authentification Azure Active Directory (ADAL) pour Node.js](https://www.npmjs.com/package/adal-node) permet aux applications Node.js de s’authentifier auprès d’AAD afin d’accéder des ressources web protégées par AAD.

## <a name="client-package"></a>Package client

### <a name="install-the-npm-modules"></a>Installer les modules npm

Utilisez npm pour installer les modules client ou de gestion de stockage Azure.

```bash
npm install adal-node
```   

### <a name="example"></a>Exemple

Cet exemple à partir de [l’exemple d’informations d’identification du client](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) illustre l’authentification de serveur à serveur via les informations d’identification du client.

```javascript
const adal = require('adal-node').AuthenticationContext;

const authorityHostUrl = 'https://login.windows.net';
const tenant = 'your-tenant-id';
const authorityUrl = authorityHostUrl + '/' + tenant;
const clientId = 'your-client-id';
const clientSecret = 'your-client-secret';
const resource = 'your-app-id-uri';

const context = new adal(authorityUrl);

context.acquireTokenWithClientCredentials(
  resource,
  clientId,
  clientSecret,
  (err, tokenResponse) => {
    if (err) {
      console.log(`Token generation failed due to ${err}`);
    } else {
      console.dir(tokenResponse, { depth: null, colors: true });
    }
  }
);
```

## <a name="samples"></a>Exemples

[!INCLUDE [node-activedirectory-samples](../docs-ref-conceptual/includes/activedirectory-samples.md)]

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
