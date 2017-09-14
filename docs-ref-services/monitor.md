---
title: Modules Azure Monitor pour Node.js
description: "Références pour les modules Azure Monitor pour Node.js"
keywords: Azure, SDK, API, Monitor, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Monitor
ms.openlocfilehash: 8d27d837bddaa5258dde47b769cf601f6f5a861f
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-monitor-modules-for-nodejs"></a>Modules Azure Monitor pour Node.js

## <a name="overview"></a>Vue d'ensemble
Les applications cloud sont complexes, et se composent de nombreux éléments mobiles. L’analyse fournit des données visant à garantir que votre application reste opérationnelle et soit exécutée en toute intégrité. Elle vous permet également de parer à des problèmes potentiels ou de résoudre des problèmes déjà survenus. En outre, vous pouvez utiliser les données d’analyse pour obtenir des informations détaillées sur votre application. Ces connaissances peuvent vous aider à améliorer les performances de l’application ou sa facilité de gestion, ou à automatiser des actions qui exigeraient normalement une intervention manuelle.

## <a name="management-package"></a>Gestion des packages

### <a name="install-npm-module"></a>Installer le module npm

```bash
npm install azure-arm-monitor
```

### <a name="example"></a>Exemple

Cet exemple de code imprime toutes les règles d’alerte associées à un groupe de ressources.

```javascript
const msRestAzure = require('ms-rest-azure');
const monitorManagementClient = require('azure-arm-monitor');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new monitorManagementClient(credentials, subscriptionId);
    client.alertRules.listByResourceGroup(resourceGroupName, rules => {
      console.log('List of rules:');
      console.dir(rules, { depth: null, colors: true });
    })
  });

```

### <a name="samples"></a>Exemples

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
