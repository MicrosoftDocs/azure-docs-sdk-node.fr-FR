---
title: Modules Azure Active Directory pour Node.js
description: "Références pour les modules Azure Active Directory pour Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: active-directory
ms.openlocfilehash: 59ef5321db6e5e7f3ad0e3b63aaa6a107207d3c2
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-active-directory-modules-for-nodejs"></a><span data-ttu-id="e700b-103">Modules Azure Active Directory pour Node.js</span><span class="sxs-lookup"><span data-stu-id="e700b-103">Azure Active Directory modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="e700b-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="e700b-104">Overview</span></span>

<span data-ttu-id="e700b-105">La [bibliothèque d’authentification Azure Active Directory (ADAL) pour Node.js](https://www.npmjs.com/package/adal-node) permet aux applications Node.js de s’authentifier auprès d’AAD afin d’accéder des ressources web protégées par AAD.</span><span class="sxs-lookup"><span data-stu-id="e700b-105">The [Azure Active Directory Authentication Library (ADAL) for Node.js](https://www.npmjs.com/package/adal-node) enables Node.js applications to authenticate to AAD in order to access AAD protected web resources.</span></span>

## <a name="client-package"></a><span data-ttu-id="e700b-106">Package client</span><span class="sxs-lookup"><span data-stu-id="e700b-106">Client package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="e700b-107">Installer les modules npm</span><span class="sxs-lookup"><span data-stu-id="e700b-107">Install the npm modules</span></span>

<span data-ttu-id="e700b-108">Utilisez npm pour installer les modules client ou de gestion de stockage Azure.</span><span class="sxs-lookup"><span data-stu-id="e700b-108">Use npm to install the Azure storage client or management modules.</span></span>

```bash
npm install adal-node
```   

### <a name="example"></a><span data-ttu-id="e700b-109">exemples</span><span class="sxs-lookup"><span data-stu-id="e700b-109">Example</span></span>

<span data-ttu-id="e700b-110">Cet exemple à partir de [l’exemple d’informations d’identification du client](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) illustre l’authentification de serveur à serveur via les informations d’identification du client.</span><span class="sxs-lookup"><span data-stu-id="e700b-110">This example from the [client credentials sample](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) illustrates server-to-server authentication via client credentials.</span></span>

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

## <a name="samples"></a><span data-ttu-id="e700b-111">Exemples</span><span class="sxs-lookup"><span data-stu-id="e700b-111">Samples</span></span>

[!INCLUDE [node-activedirectory-samples](../docs-ref-conceptual/includes/activedirectory-samples.md)]

<span data-ttu-id="e700b-112">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="e700b-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
