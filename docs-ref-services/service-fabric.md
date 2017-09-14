---
title: Modules Azure Service Fabric pour Node.js
description: "Références pour les modules Azure Service Fabric pour Node.js"
keywords: Azure, SDK, API, Service Fabric, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Fabric
ms.openlocfilehash: d3de9af4e8ca834963cf2ac0275ed02b8021f29f
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-service-fabric-modules-for-nodejs"></a><span data-ttu-id="b1eef-104">Modules Azure Service Fabric pour Node.js</span><span class="sxs-lookup"><span data-stu-id="b1eef-104">Azure Service Fabric modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="b1eef-105">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="b1eef-105">Overview</span></span>

<span data-ttu-id="b1eef-106">Azure Service Fabric est une plateforme de systèmes distribués qui facilite le packaging, le déploiement et la gestion de conteneurs et de microservices évolutifs et fiables.</span><span class="sxs-lookup"><span data-stu-id="b1eef-106">Azure Service Fabric is a distributed systems platform that makes it easy to package, deploy, and manage scalable and reliable microservices and containers.</span></span>

<span data-ttu-id="b1eef-107">En savoir plus sur [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).</span><span class="sxs-lookup"><span data-stu-id="b1eef-107">Learn more about [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="b1eef-108">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="b1eef-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b1eef-109">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="b1eef-109">Install the npm module</span></span>

<span data-ttu-id="b1eef-110">Installer le module npm Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="b1eef-110">Install the Azure Service Fabric npm module</span></span>

```bash
npm install azure-arm-servicefabric
```

### <a name="example"></a><span data-ttu-id="b1eef-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="b1eef-111">Example</span></span>

<span data-ttu-id="b1eef-112">Cet exemple montre la façon dont vous pouvez répertorier les clusters pour un abonnement Azure.</span><span class="sxs-lookup"><span data-stu-id="b1eef-112">This example shows how you can list the clusters for an Azure subscription.</span></span>

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

## <a name="samples"></a><span data-ttu-id="b1eef-113">Exemples</span><span class="sxs-lookup"><span data-stu-id="b1eef-113">Samples</span></span>

<span data-ttu-id="b1eef-114">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="b1eef-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
