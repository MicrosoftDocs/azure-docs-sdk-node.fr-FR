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
# <a name="azure-service-fabric-modules-for-nodejs"></a>Modules Azure Service Fabric pour Node.js

## <a name="overview"></a>Vue d'ensemble

Azure Service Fabric est une plateforme de systèmes distribués qui facilite le packaging, le déploiement et la gestion de conteneurs et de microservices évolutifs et fiables.

En savoir plus sur [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview).

## <a name="management-package"></a>Gestion des packages

### <a name="install-the-npm-module"></a>Installer le module npm

Installer le module npm Azure Service Fabric

```bash
npm install azure-arm-servicefabric
```

### <a name="example"></a>Exemple

Cet exemple montre la façon dont vous pouvez répertorier les clusters pour un abonnement Azure.

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

## <a name="samples"></a>Exemples

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
