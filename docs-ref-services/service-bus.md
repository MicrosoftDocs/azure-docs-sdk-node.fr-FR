---
title: Modules Azure Service Bus pour Node.js
description: Références pour les modules Azure Service Bus pour Node.js
author: sethmanheim
ms.author: sethm
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Service Bus
ms.openlocfilehash: 76d7c615cbe64fa38f9c28ea8dfc6d1c854bb0c9
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51380349"
---
# <a name="azure-service-bus-modules-for-nodejs"></a><span data-ttu-id="7985d-103">Modules Azure Service Bus pour Node.js</span><span class="sxs-lookup"><span data-stu-id="7985d-103">Azure Service Bus Modules for Node.js</span></span>

<span data-ttu-id="7985d-104">Azure Service Bus est une plateforme cloud de messagerie asynchrone qui vous permet d’envoyer des données entre systèmes découplés.</span><span class="sxs-lookup"><span data-stu-id="7985d-104">Azure Service Bus is an asynchronous messaging cloud platform that enables you to send data between decoupled systems.</span></span>

<span data-ttu-id="7985d-105">En savoir plus sur [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview).</span><span class="sxs-lookup"><span data-stu-id="7985d-105">Learn more about [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="7985d-106">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="7985d-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="7985d-107">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="7985d-107">Install the npm module</span></span>

<span data-ttu-id="7985d-108">Utiliser npm pour installer le module Azure Service Bus pour Node.js</span><span class="sxs-lookup"><span data-stu-id="7985d-108">Use npm to install the Azure Service Bus module for Node.js</span></span>

```bash
npm install azure-arm-sb
```

### <a name="example"></a><span data-ttu-id="7985d-109">Exemples</span><span class="sxs-lookup"><span data-stu-id="7985d-109">Example</span></span>

<span data-ttu-id="7985d-110">Cet exemple crée un client et répertorie ensuite tous les espaces de noms Service Bus associés à un abonnement donné.</span><span class="sxs-lookup"><span data-stu-id="7985d-110">This example creates a client and then lists all Service Bus namespaces associated with a given subscription.</span></span>

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

## <a name="samples"></a><span data-ttu-id="7985d-111">Exemples</span><span class="sxs-lookup"><span data-stu-id="7985d-111">Samples</span></span>

<span data-ttu-id="7985d-112">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="7985d-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
