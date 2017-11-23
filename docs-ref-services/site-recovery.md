---
title: Modules Azure Site Recovery pour Node.js
description: "Références pour les modules Azure Site Recovery pour Node.js"
keywords: "Azure, SDK, API, Récupération de sites, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Site Recovery
ms.openlocfilehash: 3537503118a6fbe181c8cc4b26da545a4bdbd764
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-site-recovery-modules-for-nodejs"></a><span data-ttu-id="659e2-104">Modules Azure Site Recovery pour Node.js</span><span class="sxs-lookup"><span data-stu-id="659e2-104">Azure Site Recovery modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="659e2-105">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="659e2-105">Overview</span></span>

<span data-ttu-id="659e2-106">La récupération de sites vous permet d’automatiser la réplication de machines virtuelles Azure entre des régions, depuis des machines virtuelles locales et des serveurs physiques vers Azure, et depuis des machines locales vers un centre de données secondaire.</span><span class="sxs-lookup"><span data-stu-id="659e2-106">Site Recovery allows you to automate replication of Azure VMs between regions, on-premises virtual machines and physical servers to Azure, and on-premises machines to a secondary datacenter.</span></span>

<span data-ttu-id="659e2-107">En savoir plus sur [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview).</span><span class="sxs-lookup"><span data-stu-id="659e2-107">Learn more about [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="659e2-108">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="659e2-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="659e2-109">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="659e2-109">Install the npm module</span></span>

<span data-ttu-id="659e2-110">Installer le module npm de service Azure Site Recovery</span><span class="sxs-lookup"><span data-stu-id="659e2-110">Install the Azure Site Recovery service npm module</span></span>

```bash
npm install azure-arm-recoveryservices
```

### <a name="example"></a><span data-ttu-id="659e2-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="659e2-111">Example</span></span>

<span data-ttu-id="659e2-112">Cet exemple répertorie le service de récupération de sites pour un groupe de ressources.</span><span class="sxs-lookup"><span data-stu-id="659e2-112">This example lists the Site Recovery service for a resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const RecoveryServicesManagement = require('azure-arm-recoveryservices');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RecoveryServicesManagement(credentials, subscriptionId);
    return client.vaults.listByResourceGroup(resourceGroupName);
  })
  .then(vaults => {
    console.log('List of vaults:');
    console.dir(vaults, { depth: null, colors: true });
  });
  
```

## <a name="samples"></a><span data-ttu-id="659e2-113">Exemples</span><span class="sxs-lookup"><span data-stu-id="659e2-113">Samples</span></span>

<span data-ttu-id="659e2-114">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="659e2-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
