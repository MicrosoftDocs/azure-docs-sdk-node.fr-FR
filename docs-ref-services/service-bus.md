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
# <a name="azure-service-bus-modules-for-nodejs"></a><span data-ttu-id="b3a31-103">Modules Azure Service Bus pour Node.js</span><span class="sxs-lookup"><span data-stu-id="b3a31-103">Azure Service Bus Modules for Node.js</span></span>

<span data-ttu-id="b3a31-104">Azure Service Bus est une plateforme cloud de messagerie asynchrone qui vous permet d’envoyer des données entre systèmes découplés.</span><span class="sxs-lookup"><span data-stu-id="b3a31-104">Azure Service Bus is an asynchronous messaging cloud platform that enables you to send data between decoupled systems.</span></span>

<span data-ttu-id="b3a31-105">En savoir plus sur [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview).</span><span class="sxs-lookup"><span data-stu-id="b3a31-105">Learn more about [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="b3a31-106">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="b3a31-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b3a31-107">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="b3a31-107">Install the npm module</span></span>

<span data-ttu-id="b3a31-108">Utiliser npm pour installer le module Azure Service Bus pour Node.js</span><span class="sxs-lookup"><span data-stu-id="b3a31-108">Use npm to install the Azure Service Bus module for Node.js</span></span>

```bash
npm install azure-arm-sb
```

### <a name="example"></a><span data-ttu-id="b3a31-109">exemples</span><span class="sxs-lookup"><span data-stu-id="b3a31-109">Example</span></span>

<span data-ttu-id="b3a31-110">Cet exemple crée un client et répertorie ensuite tous les espaces de noms Service Bus associés à un abonnement donné.</span><span class="sxs-lookup"><span data-stu-id="b3a31-110">This example creates a client and then lists all Service Bus namespaces associated with a given subscription.</span></span>

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

## <a name="samples"></a><span data-ttu-id="b3a31-111">Exemples</span><span class="sxs-lookup"><span data-stu-id="b3a31-111">Samples</span></span>

<span data-ttu-id="b3a31-112">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="b3a31-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
