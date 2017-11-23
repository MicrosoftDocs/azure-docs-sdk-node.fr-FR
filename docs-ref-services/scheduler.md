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
# <a name="azure-scheduler-modules-for-nodejs"></a><span data-ttu-id="edf78-104">Modules Azure Scheduler pour Node.js</span><span class="sxs-lookup"><span data-stu-id="edf78-104">Azure Scheduler modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="edf78-105">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="edf78-105">Overview</span></span>

<span data-ttu-id="edf78-106">Azure Scheduler crée, tient à jour et appelle un travail planifié via HTTP, HTTPS, une file d’attente de stockage, ou [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview).</span><span class="sxs-lookup"><span data-stu-id="edf78-106">Azure Scheduler creates, maintains, and invokes scheduled work via HTTP, HTTPS, a storage queue, or the [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview).</span></span>

<span data-ttu-id="edf78-107">En savoir plus sur [Azure Scheduler](/azure/scheduler/scheduler-intro).</span><span class="sxs-lookup"><span data-stu-id="edf78-107">Learn more about [Azure Scheduler](/azure/scheduler/scheduler-intro).</span></span>

## <a name="management-package"></a><span data-ttu-id="edf78-108">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="edf78-108">Management package</span></span>

<span data-ttu-id="edf78-109">Créer, mettre à jour et appeler un travail planifié par différents canaux de communication avec l’API de gestion.</span><span class="sxs-lookup"><span data-stu-id="edf78-109">Create, maintain, and invoke scheduled work across various communication channels with the management API.</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="edf78-110">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="edf78-110">Install the npm module</span></span>

<span data-ttu-id="edf78-111">Installer le module npm Azure Scheduler</span><span class="sxs-lookup"><span data-stu-id="edf78-111">Install the Azure Scheduler npm module</span></span>

```bash
npm install azure-arm-scheduler
```

### <a name="example"></a><span data-ttu-id="edf78-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="edf78-112">Example</span></span>

<span data-ttu-id="edf78-113">Cet exemple répertorie les planificateurs actuels.</span><span class="sxs-lookup"><span data-stu-id="edf78-113">This examples lists the current schedulers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="edf78-114">Exemples</span><span class="sxs-lookup"><span data-stu-id="edf78-114">Samples</span></span>

<span data-ttu-id="edf78-115">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="edf78-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
