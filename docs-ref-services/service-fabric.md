---
title: Modules Azure Service Fabric pour Node.js
description: "Références pour les modules Azure Service Fabric pour Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 11/12/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Fabric
ms.openlocfilehash: c855e0003a4b6f4a4d75f37b4c8480721fe0a942
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-service-fabric-modules-for-nodejs"></a><span data-ttu-id="a07d8-103">Modules Azure Service Fabric pour Node.js</span><span class="sxs-lookup"><span data-stu-id="a07d8-103">Azure Service Fabric modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="a07d8-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="a07d8-104">Overview</span></span>

<span data-ttu-id="a07d8-105">Azure Service Fabric est une plateforme de systèmes distribués qui facilite le packaging, le déploiement et la gestion de conteneurs et de microservices évolutifs et fiables.</span><span class="sxs-lookup"><span data-stu-id="a07d8-105">Azure Service Fabric is a distributed systems platform that makes it easy to package, deploy, and manage scalable and reliable microservices and containers.</span></span>

<span data-ttu-id="a07d8-106">En savoir plus sur [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).</span><span class="sxs-lookup"><span data-stu-id="a07d8-106">Learn more about [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="a07d8-107">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="a07d8-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="a07d8-108">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="a07d8-108">Install the npm module</span></span>

<span data-ttu-id="a07d8-109">Installer le module npm Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="a07d8-109">Install the Azure Service Fabric npm module</span></span>

```bash
npm install azure-arm-servicefabric
```

### <a name="example"></a><span data-ttu-id="a07d8-110">exemples</span><span class="sxs-lookup"><span data-stu-id="a07d8-110">Example</span></span>

<span data-ttu-id="a07d8-111">Cet exemple montre la façon dont vous pouvez répertorier les clusters pour un abonnement Azure.</span><span class="sxs-lookup"><span data-stu-id="a07d8-111">This example shows how you can list the clusters for an Azure subscription.</span></span>

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

## <a name="samples"></a><span data-ttu-id="a07d8-112">Exemples</span><span class="sxs-lookup"><span data-stu-id="a07d8-112">Samples</span></span>

<span data-ttu-id="a07d8-113">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="a07d8-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
