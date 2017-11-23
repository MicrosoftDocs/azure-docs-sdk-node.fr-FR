---
title: Modules Azure Relay pour Node.js
description: "Références pour les modules Azure Relay pour Node.js"
keywords: Azure, SDK, API, Relay, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Relay
ms.openlocfilehash: 7e958433e0d3cc6b464bb5980d4f161323a18ab2
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-relay-modules-for-nodejs"></a><span data-ttu-id="b5205-104">Modules Azure Relay pour Node.js</span><span class="sxs-lookup"><span data-stu-id="b5205-104">Azure Relay modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="b5205-105">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="b5205-105">Overview</span></span>

<span data-ttu-id="b5205-106">Le service Azure Relay crée des applications hybrides en offrant la possibilité d’exposer les services qui résident dans un réseau d’entreprise sur le cloud public en toute sécurité, sans avoir à ouvrir une connexion de pare-feu ni à exiger des modifications intrusives dans une infrastructure de réseau d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="b5205-106">The Azure Relay service creates hybrid applications by enabling you to securely expose services that reside within a corporate enterprise network to the public cloud, without having to open a firewall connection, or require intrusive changes to a corporate network infrastructure.</span></span> <span data-ttu-id="b5205-107">Azure Relay prend en charge une grande variété de protocoles de transport et normes de services web.</span><span class="sxs-lookup"><span data-stu-id="b5205-107">Relay supports a variety of different transport protocols and web services standards.</span></span>

<span data-ttu-id="b5205-108">En savoir plus sur [Azure Relay](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it).</span><span class="sxs-lookup"><span data-stu-id="b5205-108">Learn more about [Azure Relay](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it).</span></span>

## <a name="management-package"></a><span data-ttu-id="b5205-109">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="b5205-109">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b5205-110">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="b5205-110">Install the npm module</span></span>

<span data-ttu-id="b5205-111">Installer le module npm Azure Relay</span><span class="sxs-lookup"><span data-stu-id="b5205-111">Install the Azure Relay npm module</span></span>

```bash
npm install azure-arm-relay
```

### <a name="example"></a><span data-ttu-id="b5205-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="b5205-112">Example</span></span>

<span data-ttu-id="b5205-113">Cet exemple répertorie les espaces de noms pour un client de relais.</span><span class="sxs-lookup"><span data-stu-id="b5205-113">This example lists the namespaces for a Relay client.</span></span>

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

## <a name="samples"></a><span data-ttu-id="b5205-114">Exemples</span><span class="sxs-lookup"><span data-stu-id="b5205-114">Samples</span></span>

<span data-ttu-id="b5205-115">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="b5205-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
