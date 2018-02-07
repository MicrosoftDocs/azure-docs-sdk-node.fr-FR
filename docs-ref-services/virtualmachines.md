---
title: Modules Machines virtuelles Azure pour Node.js - Azure
description: "Guide de référence pour les modules Machines virtuelles Azure pour Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: compute
ms.openlocfilehash: 608a915499d7c32c2c8b04464f716fa4fd17243d
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-virtual-machine-modules-for-nodejs"></a><span data-ttu-id="df6ae-103">Modules Machines virtuelles Azure pour Node.js</span><span class="sxs-lookup"><span data-stu-id="df6ae-103">Azure Virtual Machine Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="df6ae-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="df6ae-104">Overview</span></span>

<span data-ttu-id="df6ae-105">Définir, configurer et déployer de nouvelles machines virtuelles Windows et Linux ainsi que des groupe de machines virtuelles identiques à partir de votre code avec les modules de gestion Azure pour Node.js.</span><span class="sxs-lookup"><span data-stu-id="df6ae-105">Define, configure, and deploy new Windows and Linux virtual machines and virtual machine scale sets from your code with the Azure management modules for Node.js.</span></span> <span data-ttu-id="df6ae-106">Les modules vous permettent de démarrer et d’arrêter des machines virtuelles existantes, d’attacher ou de détacher les disques des machines virtuelles arrêtées dans votre abonnement Azure.</span><span class="sxs-lookup"><span data-stu-id="df6ae-106">The modules let you start and stop existing virtual machines and attach or detach disks to stopped VMs in your Azure subscription.</span></span>

## <a name="management-package"></a><span data-ttu-id="df6ae-107">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="df6ae-107">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="df6ae-108">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="df6ae-108">Install the npm module</span></span>

<span data-ttu-id="df6ae-109">Installer le module npm Azure Compute</span><span class="sxs-lookup"><span data-stu-id="df6ae-109">Install the Azure Compute npm module</span></span>

```bash
npm install azure-arm-compute
```   

### <a name="example"></a><span data-ttu-id="df6ae-110">exemples</span><span class="sxs-lookup"><span data-stu-id="df6ae-110">Example</span></span>

<span data-ttu-id="df6ae-111">L’exemple suivant illustre comment se connecter à Azure, créer un client de gestion et dresser la liste de toutes les images de machine virtuelle pour un emplacement, un éditeur, une offre et une référence SKU spécifiés.</span><span class="sxs-lookup"><span data-stu-id="df6ae-111">The following example illustrates how to log in to Azure, create a management client, and list all VM images for the specified location, publisher, offer, and SKU.</span></span>

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

## <a name="samples"></a><span data-ttu-id="df6ae-112">Exemples</span><span class="sxs-lookup"><span data-stu-id="df6ae-112">Samples</span></span>

[!INCLUDE [node-storage-samples](../docs-ref-conceptual/includes/virtualmachines-samples.md)]

<span data-ttu-id="df6ae-113">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="df6ae-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
