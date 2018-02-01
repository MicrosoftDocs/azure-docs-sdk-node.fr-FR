---
title: Modules Azure Service Bus pour Node.js
description: "Références pour les modules Azure Service Bus pour Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Bus
ms.openlocfilehash: 792e51acf2577649432b26e4b840bc1d40b7abaf
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-service-bus-modules-for-nodejs"></a>Modules Azure Service Bus pour Node.js

Azure Service Bus est une plateforme cloud de messagerie asynchrone qui vous permet d’envoyer des données entre systèmes découplés.

En savoir plus sur [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview).

## <a name="management-package"></a>Gestion des packages

### <a name="install-the-npm-module"></a>Installer le module npm

Utiliser npm pour installer le module Azure Service Bus pour Node.js

```bash
npm install azure-arm-sb
```

### <a name="example"></a>exemples

Cet exemple crée un client et répertorie ensuite tous les espaces de noms Service Bus associés à un abonnement donné.

```javascript
const msRestAzure = require('ms-rest-azure');
const ServicebusManagement = require('azure-arm-sb');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = new ServicebusManagement(credentials, subscriptionId);
    client.namespaces.listBySubscription().then(namespaces => {
        namespaces.map(ns => {
            console.log(`found ns : ${ns.name}`);
        });
    });
});
```

## <a name="samples"></a>Exemples

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
