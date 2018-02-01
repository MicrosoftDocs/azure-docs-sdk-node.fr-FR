---
title: Modules Azure Event Hub pour Node.js
description: "Références pour les modules Azure Event Hub pour Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Event Hub
ms.openlocfilehash: 043c34e5b352a786ebead986d05b18c8216d0c93
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-event-hub-modules-for-nodejs"></a>Modules Azure Event Hub pour Node.js

Azure Event Hubs est une plateforme de diffusion de données hautement évolutive et de service d’ingestion d’événement capable de recevoir et de traiter des millions d’événements par seconde. Les concentrateurs d’événements peuvent traiter et stocker des événements, des données ou la télémétrie produits par des logiciels et appareils distribués. Les données envoyées à un concentrateur d’événements peuvent être transformées et stockées à l’aide d’adaptateurs de traitement par lot/stockage ou d’un fournisseur d’analyse en temps réel. Grâce à leur capacité à fournir des fonctionnalités publication-abonnement avec une faible latence et à grande échelle, Event Hubs constitue la « base » des données volumineuses (Big Data).

## <a name="management-package"></a>Gestion des packages

### <a name="install-the-npm-module"></a>Installer le module npm 

Utiliser npm pour installer les modules Azure Event Hub pour Node.js

```bash
npm install azure-arm-eventhub
```

### <a name="example"></a>exemples

Cet exemple récupère des informations sur un concentrateur d’événements existant.

```javascript
const msRestAzure = require('ms-rest-azure');
const EventHubManagement = require('azure-arm-eventhub');

const resourceGroupName = 'testRG';
const namespaceName = 'testNS';
const eventHubName = 'testEH';
const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new EventHubManagement(credentials, subscriptionId);
    return client.eventHubs.get(resourceGroupName, namespaceName, eventHubName);
  })
  .then(zones => console.dir(zones, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a>Exemples

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
