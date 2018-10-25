---
title: Modules Azure Relay pour Node.js
description: Références pour les modules Azure Relay pour Node.js
author: sethmanheim
ms.author: sethm
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Relay
ms.openlocfilehash: e0bb24ac422d71bd8c957e94cceffd57bf121e48
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "49671124"
---
# <a name="azure-relay-modules-for-nodejs"></a><span data-ttu-id="da6a8-103">Modules Azure Relay pour Node.js</span><span class="sxs-lookup"><span data-stu-id="da6a8-103">Azure Relay modules for Node.js</span></span>

<span data-ttu-id="da6a8-104">Le service Azure Relay crée des applications hybrides en offrant la possibilité d’exposer les services qui résident dans un réseau d’entreprise sur le cloud public en toute sécurité, sans avoir à ouvrir une connexion de pare-feu ni à exiger des modifications intrusives dans une infrastructure de réseau d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="da6a8-104">The Azure Relay service creates hybrid applications by enabling you to securely expose services that reside within a corporate enterprise network to the public cloud, without having to open a firewall connection, or require intrusive changes to a corporate network infrastructure.</span></span> <span data-ttu-id="da6a8-105">Azure Relay prend en charge une grande variété de protocoles de transport et normes de services web.</span><span class="sxs-lookup"><span data-stu-id="da6a8-105">Relay supports a variety of different transport protocols and web services standards.</span></span>

<span data-ttu-id="da6a8-106">En savoir plus sur [Azure Relay](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it).</span><span class="sxs-lookup"><span data-stu-id="da6a8-106">Learn more about [Azure Relay](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it).</span></span>

## <a name="management-package"></a><span data-ttu-id="da6a8-107">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="da6a8-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="da6a8-108">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="da6a8-108">Install the npm module</span></span>

<span data-ttu-id="da6a8-109">Installer le module npm Azure Relay</span><span class="sxs-lookup"><span data-stu-id="da6a8-109">Install the Azure Relay npm module</span></span>

```bash
npm install azure-arm-relay
```

### <a name="example"></a><span data-ttu-id="da6a8-110">Exemples</span><span class="sxs-lookup"><span data-stu-id="da6a8-110">Example</span></span>

<span data-ttu-id="da6a8-111">Cet exemple répertorie les espaces de noms pour un client de relais.</span><span class="sxs-lookup"><span data-stu-id="da6a8-111">This example lists the namespaces for a Relay client.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const RelayManagement = require('azure-arm-relay');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RelayManagement(credentials, subscriptionId);
    return client.namespaces.list();
  })
  .then(namespaces => {
    console.dir(namespaces, { depth: null, colors: true });
  })
  .catch(err => console.log(err));
```

## <a name="samples"></a><span data-ttu-id="da6a8-112">Exemples</span><span class="sxs-lookup"><span data-stu-id="da6a8-112">Samples</span></span>

<span data-ttu-id="da6a8-113">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="da6a8-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
