---
title: Modules Azure Traffic Manager pour Node.js
description: Références pour les modules Azure Traffic Manager pour Node.js
author: KumudD
ms.author: kumud
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Traffic Manager
ms.openlocfilehash: 2a32eed460c6076011fdcf31d77200502ef61a3d
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51366453"
---
# <a name="azure-traffic-manager-modules-for-nodejs"></a><span data-ttu-id="79701-103">Modules Azure Traffic Manager pour Node.js</span><span class="sxs-lookup"><span data-stu-id="79701-103">Azure Traffic Manager modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="79701-104">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="79701-104">Overview</span></span>

<span data-ttu-id="79701-105">Microsoft Azure Traffic Manager vous permet de contrôler la répartition du trafic utilisateur pour les points de terminaison de service dans différents centres de données.</span><span class="sxs-lookup"><span data-stu-id="79701-105">Microsoft Azure Traffic Manager allows you to control the distribution of user traffic for service endpoints in different datacenters.</span></span> <span data-ttu-id="79701-106">Les points de terminaison de service pris en charge par Traffic Manager incluent des machines virtuelles Azure, des applications web et des services cloud.</span><span class="sxs-lookup"><span data-stu-id="79701-106">Service endpoints supported by Traffic Manager include Azure VMs, Web Apps, and cloud services.</span></span> <span data-ttu-id="79701-107">Vous pouvez également utiliser Traffic Manager avec des points de terminaison externes non-Azure.</span><span class="sxs-lookup"><span data-stu-id="79701-107">You can also use Traffic Manager with external, non-Azure endpoints.</span></span>

<span data-ttu-id="79701-108">En savoir plus sur [Azure Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span><span class="sxs-lookup"><span data-stu-id="79701-108">Learn more about [Azure Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="79701-109">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="79701-109">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="79701-110">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="79701-110">Install the npm module</span></span>

<span data-ttu-id="79701-111">Installer le module npm Azure Traffic Manager</span><span class="sxs-lookup"><span data-stu-id="79701-111">Install the Azure traffic manager npm module</span></span>

```bash
npm install azure-arm-trafficmanager
```

### <a name="example"></a><span data-ttu-id="79701-112">Exemples</span><span class="sxs-lookup"><span data-stu-id="79701-112">Example</span></span>

<span data-ttu-id="79701-113">Cet exemple répertorie tous les gestionnaires de trafic pour un groupe de ressources donné.</span><span class="sxs-lookup"><span data-stu-id="79701-113">This example lists all Traffic Managers for a given resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const trafficManager = require('azure-arm-trafficmanager');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new trafficManager(credentials, subscriptionId);
  const resourceGroupName = 'resource-group-name';
  client.profiles.listAllInResourceGroup(resourceGroupName).then(profiles => {
    profiles.map(profile => {
      console.log(`found profile : ${profile.name}`);
    });
  });
});
```

## <a name="samples"></a><span data-ttu-id="79701-114">Exemples</span><span class="sxs-lookup"><span data-stu-id="79701-114">Samples</span></span>

<span data-ttu-id="79701-115">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="79701-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
