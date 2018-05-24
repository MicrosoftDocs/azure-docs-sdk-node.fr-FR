---
title: Modules Machines virtuelles Azure pour Node.js - Azure
description: Guide de référence pour les modules Machines virtuelles Azure pour Node.js
author: iainfoulds
ms.author: iainfou
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: compute
ms.openlocfilehash: 891b441d25369db0f0a67d791d527e6644415434
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="azure-virtual-machine-modules-for-nodejs"></a><span data-ttu-id="f235a-103">Modules Machines virtuelles Azure pour Node.js</span><span class="sxs-lookup"><span data-stu-id="f235a-103">Azure Virtual Machine Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="f235a-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="f235a-104">Overview</span></span>

<span data-ttu-id="f235a-105">Définir, configurer et déployer de nouvelles machines virtuelles Windows et Linux ainsi que des groupe de machines virtuelles identiques à partir de votre code avec les modules de gestion Azure pour Node.js.</span><span class="sxs-lookup"><span data-stu-id="f235a-105">Define, configure, and deploy new Windows and Linux virtual machines and virtual machine scale sets from your code with the Azure management modules for Node.js.</span></span> <span data-ttu-id="f235a-106">Les modules vous permettent de démarrer et d’arrêter des machines virtuelles existantes, d’attacher ou de détacher les disques des machines virtuelles arrêtées dans votre abonnement Azure.</span><span class="sxs-lookup"><span data-stu-id="f235a-106">The modules let you start and stop existing virtual machines and attach or detach disks to stopped VMs in your Azure subscription.</span></span>

## <a name="management-package"></a><span data-ttu-id="f235a-107">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="f235a-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="f235a-108">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="f235a-108">Install the npm module</span></span>

<span data-ttu-id="f235a-109">Installer le module npm Azure Compute</span><span class="sxs-lookup"><span data-stu-id="f235a-109">Install the Azure Compute npm module</span></span>

```bash
npm install azure-arm-compute
```   

### <a name="example"></a><span data-ttu-id="f235a-110">Exemples</span><span class="sxs-lookup"><span data-stu-id="f235a-110">Example</span></span>

<span data-ttu-id="f235a-111">L’exemple suivant illustre comment se connecter à Azure, créer un client de gestion et dresser la liste de toutes les images de machine virtuelle pour un emplacement, un éditeur, une offre et une référence SKU spécifiés.</span><span class="sxs-lookup"><span data-stu-id="f235a-111">The following example illustrates how to log in to Azure, create a management client, and list all VM images for the specified location, publisher, offer, and SKU.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const computeManagementClient = require('azure-arm-compute');

const subscriptionId = 'my-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new computeManagementClient(credentials, subscriptionId);

  client.virtualMachineImages
    .list(
        'westus',                   // location
        'Canonical',   // publisher name
        'UbuntuServer',            // offer
        '16.04-LTS'        // sku
    )
    .then(result => console.log(result));
});
```

## <a name="samples"></a><span data-ttu-id="f235a-112">Exemples</span><span class="sxs-lookup"><span data-stu-id="f235a-112">Samples</span></span>

[!INCLUDE [node-virtualmachines-samples](../docs-ref-conceptual/includes/virtualmachines-samples.md)]

<span data-ttu-id="f235a-113">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="f235a-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
