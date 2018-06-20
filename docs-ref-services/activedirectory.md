---
title: Modules Azure Active Directory pour Node.js
description: Références pour les modules Azure Active Directory pour Node.js
author: celestedg
ms.author: celested
manager: mtillman
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: active-directory
ms.openlocfilehash: c356801500aa3ef9038fc27634c8a95debf152b3
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34259918"
---
# <a name="azure-active-directory-modules-for-nodejs"></a>Modules Azure Active Directory pour Node.js

## <a name="overview"></a>Vue d'ensemble

> [!IMPORTANT]
> Nous vous recommandons fortement d’utiliser [Microsoft Graph](https://graph.microsoft.io/) au lieu de l’API Azure AD Graph pour accéder aux ressources Azure Active Directory. Nos efforts de développement sont maintenant axés sur Microsoft Graph et aucune autre amélioration n’est prévue pour l’API Azure AD Graph. Il existe un nombre très limité de scénarios pour lesquels l’API Azure AD Graph peut être appropriée. Pour plus d’informations, consultez le billet de blog [Microsoft Graph ou Azure AD Graph](https://dev.office.com/blogs/microsoft-graph-or-azure-ad-graph) dans le centre de développement Office.

La [bibliothèque d’authentification Azure Active Directory (ADAL) pour Node.js](https://www.npmjs.com/package/adal-node) permet aux applications Node.js de s’authentifier auprès d’AAD afin d’accéder des ressources web protégées par AAD.

## <a name="client-package"></a>Package client

### <a name="install-the-npm-modules"></a>Installer les modules npm

Utilisez npm pour installer les modules client ou de gestion de stockage Azure.

```bash
npm install adal-node
```   

### <a name="example"></a>Exemples

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
