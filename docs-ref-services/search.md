---
title: Modules Recherche Azure pour Node.js
description: "Références pour les modules Recherche Azure pour Node.js"
keywords: Azure, SDK, API, recherche, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Search
ms.openlocfilehash: dc9d4c5128c99a9518bd059e191bb11e4de4b78f
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-search-modules-for-nodejs"></a><span data-ttu-id="9ba1b-104">Modules Recherche Azure pour Node.js</span><span class="sxs-lookup"><span data-stu-id="9ba1b-104">Azure Search modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="9ba1b-105">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="9ba1b-105">Overview</span></span>

<span data-ttu-id="9ba1b-106">Le service Recherche Azure est une solution cloud de recherche sous forme de service qui délègue la gestion du serveur et de l’infrastructure à Microsoft pour vous laisser un service prêt à l’emploi que vous renseignez avec vos données pour ensuite ajouter une recherche à votre application.</span><span class="sxs-lookup"><span data-stu-id="9ba1b-106">Azure Search is a cloud search-as-a-service solution that delegates server and infrastructure management to Microsoft, leaving you with a ready-to-use service that you can populate with your data and then use to add search to your application.</span></span>

<span data-ttu-id="9ba1b-107">En savoir plus sur [Recherche Azure](https://docs.microsoft.com/azure/search/search-what-is-azure-search).</span><span class="sxs-lookup"><span data-stu-id="9ba1b-107">Learn more about [Azure Search](https://docs.microsoft.com/azure/search/search-what-is-azure-search).</span></span>

## <a name="management-package"></a><span data-ttu-id="9ba1b-108">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="9ba1b-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="9ba1b-109">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="9ba1b-109">Install the npm module</span></span>

<span data-ttu-id="9ba1b-110">Installer le module npm Recherche Azure</span><span class="sxs-lookup"><span data-stu-id="9ba1b-110">Install the Azure Search npm module</span></span>

```bash
npm install azure-arm-search
```

### <a name="example"></a><span data-ttu-id="9ba1b-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="9ba1b-111">Example</span></span>

<span data-ttu-id="9ba1b-112">Cet exemple crée un nouveau service de recherche dans Azure, et dresse la liste des ressources dans son groupe de ressources.</span><span class="sxs-lookup"><span data-stu-id="9ba1b-112">This example creates a new Search service in Azure, and lists the resources in its resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const SearchManagement = require('azure-arm-search');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'yourResourceGroup';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new SearchManagement(credentials, subscriptionId);
    return client.services.listByResourceGroup(resourceGroup);
  })
  .then(services => console.dir(services, { depth: null, colors: true }))
  .catch(err => {
    console.log('An error ocurred');
    console.dir(err, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="9ba1b-113">Exemples</span><span class="sxs-lookup"><span data-stu-id="9ba1b-113">Samples</span></span>

<span data-ttu-id="9ba1b-114">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="9ba1b-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
