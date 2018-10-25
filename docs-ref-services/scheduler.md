---
title: Modules Azure Scheduler pour Node.js
description: Références pour les modules Azure Scheduler pour Node.js
author: rloutlaw
ms.author: ROutlaw
manager: angrobe
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Scheduler
ms.openlocfilehash: 9a842919fddb3d6448d5a4e951dc58dd0d3211e0
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "49747474"
---
# <a name="azure-scheduler-modules-for-nodejs"></a><span data-ttu-id="7c974-103">Modules Azure Scheduler pour Node.js</span><span class="sxs-lookup"><span data-stu-id="7c974-103">Azure Scheduler modules for Node.js</span></span>

<span data-ttu-id="7c974-104">Azure Scheduler crée, tient à jour et appelle un travail planifié via HTTP, HTTPS, une file d’attente de stockage, ou [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview).</span><span class="sxs-lookup"><span data-stu-id="7c974-104">Azure Scheduler creates, maintains, and invokes scheduled work via HTTP, HTTPS, a storage queue, or the [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview).</span></span>

<span data-ttu-id="7c974-105">En savoir plus sur [Azure Scheduler](/azure/scheduler/scheduler-intro).</span><span class="sxs-lookup"><span data-stu-id="7c974-105">Learn more about [Azure Scheduler](/azure/scheduler/scheduler-intro).</span></span>

## <a name="management-package"></a><span data-ttu-id="7c974-106">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="7c974-106">Management package</span></span>

<span data-ttu-id="7c974-107">Créer, mettre à jour et appeler un travail planifié par différents canaux de communication avec l’API de gestion.</span><span class="sxs-lookup"><span data-stu-id="7c974-107">Create, maintain, and invoke scheduled work across various communication channels with the management API.</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="7c974-108">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="7c974-108">Install the npm module</span></span>

<span data-ttu-id="7c974-109">Installer le module npm Azure Scheduler</span><span class="sxs-lookup"><span data-stu-id="7c974-109">Install the Azure Scheduler npm module</span></span>

```bash
npm install azure-arm-scheduler
```

### <a name="example"></a><span data-ttu-id="7c974-110">Exemples</span><span class="sxs-lookup"><span data-stu-id="7c974-110">Example</span></span>

<span data-ttu-id="7c974-111">Cet exemple répertorie les planificateurs actuels.</span><span class="sxs-lookup"><span data-stu-id="7c974-111">This examples lists the current schedulers.</span></span>

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

## <a name="samples"></a><span data-ttu-id="7c974-112">Exemples</span><span class="sxs-lookup"><span data-stu-id="7c974-112">Samples</span></span>

<span data-ttu-id="7c974-113">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="7c974-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
