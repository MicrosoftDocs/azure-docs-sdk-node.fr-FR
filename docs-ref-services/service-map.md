---
title: Modules Azure Service Map pour Node.js
description: "Références pour les modules Azure Service Map pour Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Map
ms.openlocfilehash: 3f858e52f7a97ff77959825a1be993ef52f96e57
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-service-map-modules-for-nodejs"></a>Modules Azure Service Map pour Node.js

La solution Service Map détecte automatiquement les composants d’application sur les systèmes Windows et Linux, et mappe la communication entre les services. Elle affiche les connexions entre serveurs, processus et ports au sein de toute architecture TCP connectée, sans nécessiter de configuration autre que l’installation d’un agent.

En savoir plus sur [Azure Service Map](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-service-map).

## <a name="management-package"></a>Gestion des packages

### <a name="install-the-npm-module"></a>Installer le module npm

Installer le module npm Azure Service Map

```bash
npm install azure-arm-servicemap
```

### <a name="example"></a>exemples

Cet exemple répertorie tous les mappages de service pour le groupe de ressources et l’espace de travail spécifiés.

```javascript
const msRestAzure = require('ms-rest-azure');
const serviceMapManagement = require('azure-arm-servicemap');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const workspace = 'your-workspace';
let serviceMapClient;

msRestAzure.interactiveLogin().then(credentials => {
  serviceMapClient = new serviceMapManagement(credentials, subscriptionId);
  serviceMapClient.machineGroups
    .listByWorkspace(resourceGroup, workspace)
    .then(machineGroups => console.log('Retrieved machine groups: ', machineGroups));
});
```

## <a name="samples"></a>Exemples

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
