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
---
# <a name="azure-active-directory-modules-for-nodejs"></a><span data-ttu-id="e9474-103">Modules Azure Active Directory pour Node.js</span><span class="sxs-lookup"><span data-stu-id="e9474-103">Azure Active Directory modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="e9474-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="e9474-104">Overview</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e9474-105">Nous vous recommandons fortement d’utiliser [Microsoft Graph](https://graph.microsoft.io/) au lieu de l’API Azure AD Graph pour accéder aux ressources Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="e9474-105">We strongly recommend that you use [Microsoft Graph](https://graph.microsoft.io/) instead of Azure AD Graph API to access Azure Active Directory resources.</span></span> <span data-ttu-id="e9474-106">Nos efforts de développement sont maintenant axés sur Microsoft Graph et aucune autre amélioration n’est prévue pour l’API Azure AD Graph.</span><span class="sxs-lookup"><span data-stu-id="e9474-106">Our development efforts are now concentrated on Microsoft Graph and no further enhancements are planned for Azure AD Graph API.</span></span> <span data-ttu-id="e9474-107">Il existe un nombre très limité de scénarios pour lesquels l’API Azure AD Graph peut être appropriée. Pour plus d’informations, consultez le billet de blog [Microsoft Graph ou Azure AD Graph](https://dev.office.com/blogs/microsoft-graph-or-azure-ad-graph) dans le centre de développement Office.</span><span class="sxs-lookup"><span data-stu-id="e9474-107">There are a very limited number of scenarios for which Azure AD Graph API might still be appropriate; for more information, see the [Microsoft Graph or the Azure AD Graph](https://dev.office.com/blogs/microsoft-graph-or-azure-ad-graph) blog post in the Office Dev Center.</span></span>

<span data-ttu-id="e9474-108">La [bibliothèque d’authentification Azure Active Directory (ADAL) pour Node.js](https://www.npmjs.com/package/adal-node) permet aux applications Node.js de s’authentifier auprès d’AAD afin d’accéder des ressources web protégées par AAD.</span><span class="sxs-lookup"><span data-stu-id="e9474-108">The [Azure Active Directory Authentication Library (ADAL) for Node.js](https://www.npmjs.com/package/adal-node) enables Node.js applications to authenticate to AAD in order to access AAD protected web resources.</span></span>

## <a name="client-package"></a><span data-ttu-id="e9474-109">Package client</span><span class="sxs-lookup"><span data-stu-id="e9474-109">Client package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="e9474-110">Installer les modules npm</span><span class="sxs-lookup"><span data-stu-id="e9474-110">Install the npm modules</span></span>

<span data-ttu-id="e9474-111">Utilisez npm pour installer les modules client ou de gestion de stockage Azure.</span><span class="sxs-lookup"><span data-stu-id="e9474-111">Use npm to install the Azure storage client or management modules.</span></span>

```bash
npm install adal-node
```   

### <a name="example"></a><span data-ttu-id="e9474-112">Exemples</span><span class="sxs-lookup"><span data-stu-id="e9474-112">Example</span></span>

<span data-ttu-id="e9474-113">Cet exemple à partir de [l’exemple d’informations d’identification du client](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) illustre l’authentification de serveur à serveur via les informations d’identification du client.</span><span class="sxs-lookup"><span data-stu-id="e9474-113">This example from the [client credentials sample](https://github.com/MSOpenTech/azure-activedirectory-library-for-nodejs/blob/master/sample/client-credentials-sample.js) illustrates server-to-server authentication via client credentials.</span></span>

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

## <a name="samples"></a><span data-ttu-id="e9474-114">Exemples</span><span class="sxs-lookup"><span data-stu-id="e9474-114">Samples</span></span>

[!INCLUDE [node-activedirectory-samples](../docs-ref-conceptual/includes/activedirectory-samples.md)]

<span data-ttu-id="e9474-115">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="e9474-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
