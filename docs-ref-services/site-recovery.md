---
title: Modules Azure Site Recovery pour Node.js
description: "Références pour les modules Azure Site Recovery pour Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Site Recovery
ms.openlocfilehash: a1f3e1c18be68dd7e68f38e353e0c2ba224fbaa1
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-site-recovery-modules-for-nodejs"></a><span data-ttu-id="a8a32-103">Modules Azure Site Recovery pour Node.js</span><span class="sxs-lookup"><span data-stu-id="a8a32-103">Azure Site Recovery modules for Node.js</span></span>

<span data-ttu-id="a8a32-104">La récupération de sites vous permet d’automatiser la réplication de machines virtuelles Azure entre des régions, depuis des machines virtuelles locales et des serveurs physiques vers Azure, et depuis des machines locales vers un centre de données secondaire.</span><span class="sxs-lookup"><span data-stu-id="a8a32-104">Site Recovery allows you to automate replication of Azure VMs between regions, on-premises virtual machines and physical servers to Azure, and on-premises machines to a secondary datacenter.</span></span>

<span data-ttu-id="a8a32-105">En savoir plus sur [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview).</span><span class="sxs-lookup"><span data-stu-id="a8a32-105">Learn more about [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="a8a32-106">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="a8a32-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="a8a32-107">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="a8a32-107">Install the npm module</span></span>

<span data-ttu-id="a8a32-108">Installer le module npm de service Azure Site Recovery</span><span class="sxs-lookup"><span data-stu-id="a8a32-108">Install the Azure Site Recovery service npm module</span></span>

```bash
npm install azure-arm-recoveryservices
```

### <a name="example"></a><span data-ttu-id="a8a32-109">exemples</span><span class="sxs-lookup"><span data-stu-id="a8a32-109">Example</span></span>

<span data-ttu-id="a8a32-110">Cet exemple répertorie le service de récupération de sites pour un groupe de ressources.</span><span class="sxs-lookup"><span data-stu-id="a8a32-110">This example lists the Site Recovery service for a resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="a8a32-111">Exemples</span><span class="sxs-lookup"><span data-stu-id="a8a32-111">Samples</span></span>

<span data-ttu-id="a8a32-112">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="a8a32-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
