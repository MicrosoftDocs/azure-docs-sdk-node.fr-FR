---
title: Modules Machines virtuelles Azure pour Node.js
description: "Références pour les modules Machines virtuelles Azure pour Node.js"
keywords: "Azure, nœud, SDK, API, machine virtuelle, mv, Node.js, Javascript"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: compute
ms.openlocfilehash: 816714f5c286ee82f61502978c5d811e9f283432
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-virtual-machine-modules-for-nodejs"></a><span data-ttu-id="0300f-104">Modules Machines virtuelles Azure pour Node.js</span><span class="sxs-lookup"><span data-stu-id="0300f-104">Azure Virtual Machine Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="0300f-105">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="0300f-105">Overview</span></span>

<span data-ttu-id="0300f-106">Définir, configurer et déployer de nouvelles machines virtuelles Windows et Linux ainsi que des groupe de machines virtuelles identiques à partir de votre code avec les modules de gestion Azure pour Node.js.</span><span class="sxs-lookup"><span data-stu-id="0300f-106">Define, configure, and deploy new Windows and Linux virtual machines and virtual machine scale sets from your code with the Azure management modules for Node.js.</span></span> <span data-ttu-id="0300f-107">Les modules vous permettent de démarrer et d’arrêter des machines virtuelles existantes, d’attacher ou de détacher les disques des machines virtuelles arrêtées dans votre abonnement Azure.</span><span class="sxs-lookup"><span data-stu-id="0300f-107">The modules let you start and stop existing virtual machines and attach or detach disks to stopped VMs in your Azure subscription.</span></span>

## <a name="management-package"></a><span data-ttu-id="0300f-108">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="0300f-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="0300f-109">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="0300f-109">Install the npm module</span></span>

<span data-ttu-id="0300f-110">Installer le module npm Azure Compute</span><span class="sxs-lookup"><span data-stu-id="0300f-110">Install the Azure Compute npm module</span></span>

```bash
npm install azure-arm-compute
```   

### <a name="example"></a><span data-ttu-id="0300f-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="0300f-111">Example</span></span>

<span data-ttu-id="0300f-112">L’exemple suivant illustre comment se connecter à Azure, créer un client de gestion et dresser la liste de toutes les images de machine virtuelle pour un emplacement, un éditeur, une offre et une référence SKU spécifiés.</span><span class="sxs-lookup"><span data-stu-id="0300f-112">The following example illustrates how to log in to Azure, create a management client, and list all VM images for the specified location, publisher, offer, and SKU.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const computeManagementClient = require('azure-arm-compute');

const subscriptionId = 'my-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new computeManagementClient(credentials, subscriptionId);

  client.virtualMachineImages
    .list(
        'westus',                   // location
        'MicrosoftWindowsServer',   // publisher name
        'WindowsServer',            // offer
        '2012-R2-Datacenter'        // sku
    )
    .then(result => console.log(result));
});
```

## <a name="samples"></a><span data-ttu-id="0300f-113">Exemples</span><span class="sxs-lookup"><span data-stu-id="0300f-113">Samples</span></span>

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/virtualmachines-samples.md)]

<span data-ttu-id="0300f-114">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="0300f-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
