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
# <a name="azure-service-bus-modules-for-nodejs"></a><span data-ttu-id="94472-104">Modules Azure Service Bus pour Node.js</span><span class="sxs-lookup"><span data-stu-id="94472-104">Azure Service Bus Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="94472-105">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="94472-105">Overview</span></span>

<span data-ttu-id="94472-106">Azure Service Bus est une plateforme cloud de messagerie asynchrone qui vous permet d’envoyer des données entre systèmes découplés.</span><span class="sxs-lookup"><span data-stu-id="94472-106">Azure Service Bus is an asynchronous messaging cloud platform that enables you to send data between decoupled systems.</span></span>

<span data-ttu-id="94472-107">En savoir plus sur [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview).</span><span class="sxs-lookup"><span data-stu-id="94472-107">Learn more about [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="94472-108">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="94472-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="94472-109">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="94472-109">Install the npm module</span></span>

<span data-ttu-id="94472-110">Utiliser npm pour installer le module Azure Service Bus pour Node.js</span><span class="sxs-lookup"><span data-stu-id="94472-110">Use npm to install the Azure Service Bus module for Node.js</span></span>

```bash
npm install azure-arm-sb
```

### <a name="example"></a><span data-ttu-id="94472-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="94472-111">Example</span></span>

<span data-ttu-id="94472-112">Cet exemple crée un client et répertorie ensuite tous les espaces de noms Service Bus associés à un abonnement donné.</span><span class="sxs-lookup"><span data-stu-id="94472-112">This example creates a client and then lists all Service Bus namespaces associated with a given subscription.</span></span>

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

## <a name="samples"></a><span data-ttu-id="94472-113">Exemples</span><span class="sxs-lookup"><span data-stu-id="94472-113">Samples</span></span>

<span data-ttu-id="94472-114">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="94472-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
