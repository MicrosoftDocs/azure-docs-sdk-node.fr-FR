---
title: Modules Azure Relay pour Node.js
description: "Références pour les modules Azure Relay pour Node.js"
keywords: Azure, SDK, API, Relay, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Relay
ms.openlocfilehash: 7e958433e0d3cc6b464bb5980d4f161323a18ab2
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-relay-modules-for-nodejs"></a>Modules Azure Relay pour Node.js

## <a name="overview"></a>Vue d'ensemble

Le service Azure Relay crée des applications hybrides en offrant la possibilité d’exposer les services qui résident dans un réseau d’entreprise sur le cloud public en toute sécurité, sans avoir à ouvrir une connexion de pare-feu ni à exiger des modifications intrusives dans une infrastructure de réseau d’entreprise. Azure Relay prend en charge une grande variété de protocoles de transport et normes de services web.

En savoir plus sur [Azure Relay](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it).

## <a name="management-package"></a>Gestion des packages

### <a name="install-the-npm-module"></a>Installer le module npm

Installer le module npm Azure Relay

```bash
npm install azure-arm-relay
```

### <a name="example"></a>Exemple

Cet exemple répertorie les espaces de noms pour un client de relais.

```javascript
const msRestAzure = require('ms-rest-azure');
const RelayManagement = require('azure-arm-relay');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RelayManagement(credentials, subscriptionId);
    return client.namespaces.list();
  })
  .then(namespaces => {
    console.dir(namespaces, { depth: null, colors: true });
  })
  .catch(err => console.log(err));
```

## <a name="samples"></a>Exemples

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
