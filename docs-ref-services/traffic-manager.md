---
title: Modules Azure Traffic Manager pour Node.js
description: "Références pour les modules Azure Traffic Manager pour Node.js"
keywords: Azure, SDK, API, Traffic Manager, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Traffic Manager
ms.openlocfilehash: a74818b9a92bc6ec781b6d47921a7ef43e90cd31
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-traffic-manager-modules-for-nodejs"></a>Modules Azure Traffic Manager pour Node.js

## <a name="overview"></a>Vue d'ensemble

Microsoft Azure Traffic Manager vous permet de contrôler la répartition du trafic utilisateur pour les points de terminaison de service dans différents centres de données. Les points de terminaison de service pris en charge par Traffic Manager incluent des machines virtuelles Azure, des applications web et des services cloud. Vous pouvez également utiliser Traffic Manager avec des points de terminaison externes non-Azure.

En savoir plus sur [Azure Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).

## <a name="management-package"></a>Gestion des packages

### <a name="install-the-npm-module"></a>Installer le module npm

Installer le module npm Azure Traffic Manager

```bash
npm install azure-arm-trafficmanager
```

### <a name="example"></a>Exemple

Cet exemple répertorie tous les gestionnaires de trafic pour un groupe de ressources donné.

```javascript
const msRestAzure = require('ms-rest-azure');
const trafficManager = require('azure-arm-trafficmanager');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new trafficManager(credentials, subscriptionId);
  const resourceGroupName = 'resource-group-name';
  client.profiles.listAllInResourceGroup(resourceGroupName).then(profiles => {
    profiles.map(profile => {
      console.log(`found profile : ${profile.name}`);
    });
  });
});
```

## <a name="samples"></a>Exemples

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
