---
title: "Modules Réseau virtuel Azure pour Node.js"
description: "Références pour les modules Réseau virtuel Azure pour Node.js"
keywords: "Azure, SDK, API, réseau virtuel, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Virtual Network
ms.openlocfilehash: a17615a832c6dddeb7fef0a8a327dbf86ae281a7
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-virtual-network-modules-for-nodejs"></a>Modules Réseau virtuel Azure pour Node.js

## <a name="overview"></a>Vue d'ensemble

Le service Réseau virtuel Azure vous permet de connecter en toute sécurité des ressources Azure entre elles en utilisant des réseaux virtuels. Un réseau virtuel est une représentation de votre propre réseau dans le cloud. Il s’agit d’un isolement logique du cloud Azure dédié à votre abonnement. Vous pouvez également connecter des réseaux virtuels à votre réseau local.

En savoir plus sur [Réseau virtuel Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).

## <a name="management-package"></a>Gestion des packages

### <a name="install-the-npm-module"></a>Installer le module npm

Installer le module npm de réseau virtuel Azure

```bash
npm install azure-arm-network
```

### <a name="example"></a>Exemple

Cet exemple obtient et imprime la liste des réseaux virtuels

```javascript
const msRestAzure = require('ms-rest-azure');
const NetworkManagementClient = require('azure-arm-network');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new NetworkManagementClient(credentials, subscriptionId);
    return client.virtualNetworks.list(resourceGroup);
  })
  .then(networkList => {
    console.log('List of virtual networks:');
    console.dir(networkList, { depth: null, colors: true });
  });

```

## <a name="samples"></a>Exemples

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
