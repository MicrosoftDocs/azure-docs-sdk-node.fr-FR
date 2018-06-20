---
title: Modules Réseau virtuel Azure pour Node.js
description: Références pour les modules Réseau virtuel Azure pour Node.js
author: jimdial
ms.author: jdial
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Virtual Network
ms.openlocfilehash: 456839dbecb9ddd1ad0d4b3f8aa7570a04c100b1
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34260698"
---
# <a name="azure-virtual-network-modules-for-nodejs"></a><span data-ttu-id="a387e-103">Modules Réseau virtuel Azure pour Node.js</span><span class="sxs-lookup"><span data-stu-id="a387e-103">Azure Virtual Network modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="a387e-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="a387e-104">Overview</span></span>

<span data-ttu-id="a387e-105">Le service Réseau virtuel Azure vous permet de connecter en toute sécurité des ressources Azure entre elles en utilisant des réseaux virtuels.</span><span class="sxs-lookup"><span data-stu-id="a387e-105">The Azure Virtual Network service enables you to securely connect Azure resources to each other with virtual networks (VNets).</span></span> <span data-ttu-id="a387e-106">Un réseau virtuel est une représentation de votre propre réseau dans le cloud.</span><span class="sxs-lookup"><span data-stu-id="a387e-106">A VNet is a representation of your own network in the cloud.</span></span> <span data-ttu-id="a387e-107">Il s’agit d’un isolement logique du cloud Azure dédié à votre abonnement.</span><span class="sxs-lookup"><span data-stu-id="a387e-107">A VNet is a logical isolation of the Azure cloud dedicated to your subscription.</span></span> <span data-ttu-id="a387e-108">Vous pouvez également connecter des réseaux virtuels à votre réseau local.</span><span class="sxs-lookup"><span data-stu-id="a387e-108">You can also connect VNets to your on-premises network.</span></span>

<span data-ttu-id="a387e-109">En savoir plus sur [Réseau virtuel Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).</span><span class="sxs-lookup"><span data-stu-id="a387e-109">Learn more about [Azure Virtual Network](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="a387e-110">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="a387e-110">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="a387e-111">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="a387e-111">Install the npm module</span></span>

<span data-ttu-id="a387e-112">Installer le module npm de réseau virtuel Azure</span><span class="sxs-lookup"><span data-stu-id="a387e-112">Install the Azure Virtual Network npm module</span></span>

```bash
npm install azure-arm-network
```

### <a name="example"></a><span data-ttu-id="a387e-113">Exemples</span><span class="sxs-lookup"><span data-stu-id="a387e-113">Example</span></span>

<span data-ttu-id="a387e-114">Cet exemple obtient et imprime la liste des réseaux virtuels</span><span class="sxs-lookup"><span data-stu-id="a387e-114">This example gets and prints the list of virtual networks</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const NetworkManagementClient = require('azure-arm-network');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new NetworkManagementClient(credentials, subscriptionId);
    return client.virtualNetworks.list(resourceGroup);
  })
  .then(networkList => {
    console.log('List of virtual networks:');
    console.dir(networkList, { depth: null, colors: true });
  });

```

## <a name="samples"></a><span data-ttu-id="a387e-115">Exemples</span><span class="sxs-lookup"><span data-stu-id="a387e-115">Samples</span></span>

<span data-ttu-id="a387e-116">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="a387e-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
