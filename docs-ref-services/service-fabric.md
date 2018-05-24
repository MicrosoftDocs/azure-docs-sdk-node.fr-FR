---
title: Modules Azure Service Fabric pour Node.js
description: Références pour les modules Azure Service Fabric pour Node.js
author: rwike77
ms.author: ryanwi
manager: timlt
ms.date: 11/12/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Fabric
ms.openlocfilehash: 12fcc4af4a78cc01370355cba0b4c642f202a30c
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="azure-service-fabric-modules-for-nodejs"></a><span data-ttu-id="e9e5a-103">Modules Azure Service Fabric pour Node.js</span><span class="sxs-lookup"><span data-stu-id="e9e5a-103">Azure Service Fabric modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="e9e5a-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="e9e5a-104">Overview</span></span>

<span data-ttu-id="e9e5a-105">Azure Service Fabric est une plateforme de systèmes distribués qui facilite le packaging, le déploiement et la gestion de conteneurs et de microservices évolutifs et fiables.</span><span class="sxs-lookup"><span data-stu-id="e9e5a-105">Azure Service Fabric is a distributed systems platform that makes it easy to package, deploy, and manage scalable and reliable microservices and containers.</span></span>

<span data-ttu-id="e9e5a-106">En savoir plus sur [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).</span><span class="sxs-lookup"><span data-stu-id="e9e5a-106">Learn more about [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="e9e5a-107">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="e9e5a-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="e9e5a-108">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="e9e5a-108">Install the npm module</span></span>

<span data-ttu-id="e9e5a-109">Installer le module npm Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="e9e5a-109">Install the Azure Service Fabric npm module</span></span>

```bash
npm install azure-arm-servicefabric
```

### <a name="example"></a><span data-ttu-id="e9e5a-110">Exemples</span><span class="sxs-lookup"><span data-stu-id="e9e5a-110">Example</span></span>

<span data-ttu-id="e9e5a-111">Cet exemple montre la façon dont vous pouvez répertorier les clusters pour un abonnement Azure.</span><span class="sxs-lookup"><span data-stu-id="e9e5a-111">This example shows how you can list the clusters for an Azure subscription.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const ServiceFabricManagement = require('azure-arm-servicefabric');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new ServiceFabricManagement(
      credentials,
      subscriptionId
    );
    return client.clusters.list();
  })
  .then(clusters => {
    console.log('List of clusters:');
    console.dir(clusters, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="e9e5a-112">Exemples</span><span class="sxs-lookup"><span data-stu-id="e9e5a-112">Samples</span></span>

<span data-ttu-id="e9e5a-113">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="e9e5a-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
