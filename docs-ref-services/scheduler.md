---
title: Modules Azure Scheduler pour Node.js
description: "Références pour les modules Azure Scheduler pour Node.js"
keywords: Azure, SDK, API, Scheduler, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Scheduler
ms.openlocfilehash: 3070612721dc434b8c3d7c3200f0666755fd4ce8
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-scheduler-modules-for-nodejs"></a>Modules Azure Scheduler pour Node.js

## <a name="overview"></a>Vue d'ensemble

Azure Scheduler crée, tient à jour et appelle un travail planifié via HTTP, HTTPS, une file d’attente de stockage, ou [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview).

En savoir plus sur [Azure Scheduler](/azure/scheduler/scheduler-intro).

## <a name="management-package"></a>Gestion des packages

Créer, mettre à jour et appeler un travail planifié par différents canaux de communication avec l’API de gestion.

### <a name="install-the-npm-module"></a>Installer le module npm

Installer le module npm Azure Scheduler

```bash
npm install azure-arm-scheduler
```

### <a name="example"></a>Exemple

Cet exemple répertorie les planificateurs actuels.

```javascript
const msRestAzure = require('ms-rest-azure')
const SchedulerManagement = require('azure-arm-scheduler')

msRestAzure.interactiveLogin().then(credentials => {
    // Create a scheduler from the login credentials
    let client = new SchedulerManagement(credentials, 'your-subscription-id')
    // Get the full list of current jobs for the subscription
    return client.jobCollections.listBySubscription()
}).then(currentJobs => {
    console.log("Current jobs:")
    console.dir(currentJobs, {depth:null, colors:true})
}).catch(error => {
    console.log("An error occurred:")
    console.dir(error, {depth:null, colors:true})
})
```

## <a name="samples"></a>Exemples

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
