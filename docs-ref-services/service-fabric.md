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

### <a name="example"></a>Exemples

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
