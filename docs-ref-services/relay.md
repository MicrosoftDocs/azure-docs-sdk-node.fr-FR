---
title: Modules Azure Relay pour Node.js
description: "Références pour les modules Azure Relay pour Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Relay
ms.openlocfilehash: 632e17f9169353ad9348b3b098b4a3e8d873238a
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-relay-modules-for-nodejs"></a>Modules Azure Relay pour Node.js

Le service Azure Relay crée des applications hybrides en offrant la possibilité d’exposer les services qui résident dans un réseau d’entreprise sur le cloud public en toute sécurité, sans avoir à ouvrir une connexion de pare-feu ni à exiger des modifications intrusives dans une infrastructure de réseau d’entreprise. Azure Relay prend en charge une grande variété de protocoles de transport et normes de services web.

En savoir plus sur [Azure Relay](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it).

## <a name="management-package"></a>Gestion des packages

### <a name="install-the-npm-module"></a>Installer le module npm

Installer le module npm Azure Relay

```bash
npm install azure-arm-relay
```

### <a name="example"></a>exemples

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
