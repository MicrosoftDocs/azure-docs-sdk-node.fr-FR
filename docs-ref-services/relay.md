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
ms.openlocfilehash: 1f9b4263b8ffae78fcf9f35b8ef0160095059693
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34260782"
---
# <a name="azure-relay-modules-for-nodejs"></a><span data-ttu-id="5e874-103">Modules Azure Relay pour Node.js</span><span class="sxs-lookup"><span data-stu-id="5e874-103">Azure Relay modules for Node.js</span></span>

<span data-ttu-id="5e874-104">Le service Azure Relay crée des applications hybrides en offrant la possibilité d’exposer les services qui résident dans un réseau d’entreprise sur le cloud public en toute sécurité, sans avoir à ouvrir une connexion de pare-feu ni à exiger des modifications intrusives dans une infrastructure de réseau d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="5e874-104">The Azure Relay service creates hybrid applications by enabling you to securely expose services that reside within a corporate enterprise network to the public cloud, without having to open a firewall connection, or require intrusive changes to a corporate network infrastructure.</span></span> <span data-ttu-id="5e874-105">Azure Relay prend en charge une grande variété de protocoles de transport et normes de services web.</span><span class="sxs-lookup"><span data-stu-id="5e874-105">Relay supports a variety of different transport protocols and web services standards.</span></span>

<span data-ttu-id="5e874-106">En savoir plus sur [Azure Relay](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it).</span><span class="sxs-lookup"><span data-stu-id="5e874-106">Learn more about [Azure Relay](https://docs.microsoft.com/azure/service-bus-relay/relay-what-is-it).</span></span>

## <a name="management-package"></a><span data-ttu-id="5e874-107">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="5e874-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="5e874-108">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="5e874-108">Install the npm module</span></span>

<span data-ttu-id="5e874-109">Installer le module npm Azure Relay</span><span class="sxs-lookup"><span data-stu-id="5e874-109">Install the Azure Relay npm module</span></span>

```bash
npm install azure-arm-relay
```

### <a name="example"></a><span data-ttu-id="5e874-110">Exemples</span><span class="sxs-lookup"><span data-stu-id="5e874-110">Example</span></span>

<span data-ttu-id="5e874-111">Cet exemple répertorie les espaces de noms pour un client de relais.</span><span class="sxs-lookup"><span data-stu-id="5e874-111">This example lists the namespaces for a Relay client.</span></span>

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

## <a name="samples"></a><span data-ttu-id="5e874-112">Exemples</span><span class="sxs-lookup"><span data-stu-id="5e874-112">Samples</span></span>

<span data-ttu-id="5e874-113">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="5e874-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
