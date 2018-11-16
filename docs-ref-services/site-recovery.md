---
title: Modules Azure Site Recovery pour Node.js
description: Références pour les modules Azure Site Recovery pour Node.js
author: rayne-wiselman
ms.author: raynew
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Site Recovery
ms.openlocfilehash: f8cddf806b921d5445cd0757b64aeb0dc5df03cf
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51373953"
---
# <a name="azure-site-recovery-modules-for-nodejs"></a><span data-ttu-id="be414-103">Modules Azure Site Recovery pour Node.js</span><span class="sxs-lookup"><span data-stu-id="be414-103">Azure Site Recovery modules for Node.js</span></span>

<span data-ttu-id="be414-104">La récupération de sites vous permet d’automatiser la réplication de machines virtuelles Azure entre des régions, depuis des machines virtuelles locales et des serveurs physiques vers Azure, et depuis des machines locales vers un centre de données secondaire.</span><span class="sxs-lookup"><span data-stu-id="be414-104">Site Recovery allows you to automate replication of Azure VMs between regions, on-premises virtual machines and physical servers to Azure, and on-premises machines to a secondary datacenter.</span></span>

<span data-ttu-id="be414-105">En savoir plus sur [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview).</span><span class="sxs-lookup"><span data-stu-id="be414-105">Learn more about [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview).</span></span>

## <a name="management-package"></a><span data-ttu-id="be414-106">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="be414-106">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="be414-107">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="be414-107">Install the npm module</span></span>

<span data-ttu-id="be414-108">Installer le module npm de service Azure Site Recovery</span><span class="sxs-lookup"><span data-stu-id="be414-108">Install the Azure Site Recovery service npm module</span></span>

```bash
npm install azure-arm-recoveryservices
```

### <a name="example"></a><span data-ttu-id="be414-109">Exemples</span><span class="sxs-lookup"><span data-stu-id="be414-109">Example</span></span>

<span data-ttu-id="be414-110">Cet exemple répertorie le service de récupération de sites pour un groupe de ressources.</span><span class="sxs-lookup"><span data-stu-id="be414-110">This example lists the Site Recovery service for a resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="be414-111">Exemples</span><span class="sxs-lookup"><span data-stu-id="be414-111">Samples</span></span>

<span data-ttu-id="be414-112">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="be414-112">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
