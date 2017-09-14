---
title: Modules Azure Service Bus pour Node.js
description: "Références pour les modules Azure Service Bus pour Node.js"
keywords: Azure, SDK, API, Service Bus, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Bus
ms.openlocfilehash: 4d1bbe917512d2ad5383081bef2c28a33541f28c
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-service-bus-modules-for-nodejs"></a>Modules Azure Service Bus pour Node.js

## <a name="overview"></a>Vue d'ensemble

Azure Service Bus est une plateforme cloud de messagerie asynchrone qui vous permet d’envoyer des données entre systèmes découplés.

En savoir plus sur [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview).

## <a name="management-package"></a>Gestion des packages

### <a name="install-the-npm-module"></a>Installer le module npm

Utiliser npm pour installer le module Azure Service Bus pour Node.js

```bash
npm install azure-arm-sb
```

### <a name="example"></a>Exemple

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
