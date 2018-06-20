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
ms.openlocfilehash: fde02006fcf364071fcb866098dba7fcd3b1c07b
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34260302"
---
# <a name="azure-service-bus-modules-for-nodejs"></a><span data-ttu-id="40d9c-103">Modules Azure Service Bus pour Node.js</span><span class="sxs-lookup"><span data-stu-id="40d9c-103">Azure Service Bus Modules for Node.js</span></span>

<span data-ttu-id="40d9c-104">Azure Service Bus est une plateforme cloud de messagerie asynchrone qui vous permet d’envoyer des données entre systèmes découplés.</span><span class="sxs-lookup"><span data-stu-id="40d9c-104">Azure Service Bus is an asynchronous messaging cloud platform that enables you to send data between decoupled systems.</span></span>

<span data-ttu-id="40d9c-105">En savoir plus sur [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview).</span><span class="sxs-lookup"><span data-stu-id="40d9c-105">Learn more about [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="40d9c-106">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="40d9c-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="40d9c-107">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="40d9c-107">Install the npm module</span></span>

<span data-ttu-id="40d9c-108">Utiliser npm pour installer le module Azure Service Bus pour Node.js</span><span class="sxs-lookup"><span data-stu-id="40d9c-108">Use npm to install the Azure Service Bus module for Node.js</span></span>

```bash
npm install azure-arm-sb
```

### <a name="example"></a><span data-ttu-id="40d9c-109">Exemples</span><span class="sxs-lookup"><span data-stu-id="40d9c-109">Example</span></span>

<span data-ttu-id="40d9c-110">Cet exemple crée un client et répertorie ensuite tous les espaces de noms Service Bus associés à un abonnement donné.</span><span class="sxs-lookup"><span data-stu-id="40d9c-110">This example creates a client and then lists all Service Bus namespaces associated with a given subscription.</span></span>

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

## <a name="samples"></a><span data-ttu-id="40d9c-111">Exemples</span><span class="sxs-lookup"><span data-stu-id="40d9c-111">Samples</span></span>

<span data-ttu-id="40d9c-112">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="40d9c-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
