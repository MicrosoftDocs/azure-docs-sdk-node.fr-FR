---
title: Modules Azure Scheduler pour Node.js
description: "Références pour les modules Azure Scheduler pour Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Scheduler
ms.openlocfilehash: 539337abd2fff3830cb022a49aff374e877a08ee
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-scheduler-modules-for-nodejs"></a><span data-ttu-id="9ca07-103">Modules Azure Scheduler pour Node.js</span><span class="sxs-lookup"><span data-stu-id="9ca07-103">Azure Scheduler modules for Node.js</span></span>

<span data-ttu-id="9ca07-104">Azure Scheduler crée, tient à jour et appelle un travail planifié via HTTP, HTTPS, une file d’attente de stockage, ou [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview).</span><span class="sxs-lookup"><span data-stu-id="9ca07-104">Azure Scheduler creates, maintains, and invokes scheduled work via HTTP, HTTPS, a storage queue, or the [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview).</span></span>

<span data-ttu-id="9ca07-105">En savoir plus sur [Azure Scheduler](/azure/scheduler/scheduler-intro).</span><span class="sxs-lookup"><span data-stu-id="9ca07-105">Learn more about [Azure Scheduler](/azure/scheduler/scheduler-intro).</span></span>

## <a name="management-package"></a><span data-ttu-id="9ca07-106">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="9ca07-106">Management package</span></span>

<span data-ttu-id="9ca07-107">Créer, mettre à jour et appeler un travail planifié par différents canaux de communication avec l’API de gestion.</span><span class="sxs-lookup"><span data-stu-id="9ca07-107">Create, maintain, and invoke scheduled work across various communication channels with the management API.</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="9ca07-108">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="9ca07-108">Install the npm module</span></span>

<span data-ttu-id="9ca07-109">Installer le module npm Azure Scheduler</span><span class="sxs-lookup"><span data-stu-id="9ca07-109">Install the Azure Scheduler npm module</span></span>

```bash
npm install azure-arm-scheduler
```

### <a name="example"></a><span data-ttu-id="9ca07-110">exemples</span><span class="sxs-lookup"><span data-stu-id="9ca07-110">Example</span></span>

<span data-ttu-id="9ca07-111">Cet exemple répertorie les planificateurs actuels.</span><span class="sxs-lookup"><span data-stu-id="9ca07-111">This examples lists the current schedulers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="9ca07-112">Exemples</span><span class="sxs-lookup"><span data-stu-id="9ca07-112">Samples</span></span>

<span data-ttu-id="9ca07-113">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="9ca07-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
