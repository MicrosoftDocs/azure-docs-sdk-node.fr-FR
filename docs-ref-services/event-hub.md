---
title: Modules Azure Event Hub pour Node.js
description: Références pour les modules Azure Event Hub pour Node.js
author: sethmanheim
ms.author: sethm
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Event Hub
ms.openlocfilehash: cf50d0e69e336dac9addc85625599fbbefd1902e
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2018
ms.locfileid: "52127544"
---
# <a name="azure-event-hub-modules-for-nodejs"></a><span data-ttu-id="d5be9-103">Modules Azure Event Hub pour Node.js</span><span class="sxs-lookup"><span data-stu-id="d5be9-103">Azure Event Hub modules for Node.js</span></span>

<span data-ttu-id="d5be9-104">Azure Event Hubs est une plateforme de diffusion de données hautement évolutive et de service d’ingestion d’événement capable de recevoir et de traiter des millions d’événements par seconde.</span><span class="sxs-lookup"><span data-stu-id="d5be9-104">Azure Event Hubs is a highly scalable data streaming platform and event ingestion service capable of receiving and processing millions of events per second.</span></span> <span data-ttu-id="d5be9-105">Les concentrateurs d’événements peuvent traiter et stocker des événements, des données ou la télémétrie produits par des logiciels et appareils distribués.</span><span class="sxs-lookup"><span data-stu-id="d5be9-105">Event Hubs can process and store events, data, or telemetry produced by distributed software and devices.</span></span> <span data-ttu-id="d5be9-106">Les données envoyées à un concentrateur d’événements peuvent être transformées et stockées à l’aide d’adaptateurs de traitement par lot/stockage ou d’un fournisseur d’analyse en temps réel.</span><span class="sxs-lookup"><span data-stu-id="d5be9-106">Data sent to an event hub can be transformed and stored using any real-time analytics provider or batching/storage adapters.</span></span> <span data-ttu-id="d5be9-107">Grâce à leur capacité à fournir des fonctionnalités publication-abonnement avec une faible latence et à grande échelle, Event Hubs constitue la « base » des données volumineuses (Big Data).</span><span class="sxs-lookup"><span data-stu-id="d5be9-107">With the ability to provide publish-subscribe capabilities with low latency and at massive scale, Event Hubs serves as the "on ramp" for Big Data.</span></span>

## <a name="management-package"></a><span data-ttu-id="d5be9-108">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="d5be9-108">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="d5be9-109">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="d5be9-109">Install the npm module</span></span> 

<span data-ttu-id="d5be9-110">Utiliser npm pour installer les modules Azure Event Hub pour Node.js</span><span class="sxs-lookup"><span data-stu-id="d5be9-110">Use npm to install the Azure Event Hub modules for Node.js</span></span>

```bash
npm install azure-arm-eventhub
```

### <a name="example"></a><span data-ttu-id="d5be9-111">Exemples</span><span class="sxs-lookup"><span data-stu-id="d5be9-111">Example</span></span>

<span data-ttu-id="d5be9-112">Cet exemple récupère des informations sur un concentrateur d’événements existant.</span><span class="sxs-lookup"><span data-stu-id="d5be9-112">This example retrieves information about an existing event hub.</span></span>

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

## <a name="samples"></a><span data-ttu-id="d5be9-113">Exemples</span><span class="sxs-lookup"><span data-stu-id="d5be9-113">Samples</span></span>

<span data-ttu-id="d5be9-114">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="d5be9-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
