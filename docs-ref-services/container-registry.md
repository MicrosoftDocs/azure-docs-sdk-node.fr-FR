---
title: Modules Azure Container Registry pour Node.js
description: "Références pour les modules Azure Container Registry pour Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Container Registry
ms.openlocfilehash: dda0e9bbfaa8a3e060f3b8f820d5bab315662629
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-container-registry-modules-for-nodejs"></a><span data-ttu-id="9a6be-103">Modules Azure Container Registry pour Node.js</span><span class="sxs-lookup"><span data-stu-id="9a6be-103">Azure Container Registry modules for Node.js</span></span>

<span data-ttu-id="9a6be-104">Azure Container Registry est un service de registre Docker géré basé sur le Registre open source Docker 2.0.</span><span class="sxs-lookup"><span data-stu-id="9a6be-104">Azure Container Registry is a managed Docker registry service based on the open-source Docker Registry 2.0.</span></span> <span data-ttu-id="9a6be-105">Créez et gérez des registres de conteneur Azure pour stocker et gérer vos images de conteneur Docker privées.</span><span class="sxs-lookup"><span data-stu-id="9a6be-105">Create and maintain Azure container registries to store and manage your private Docker container images.</span></span> <span data-ttu-id="9a6be-106">Utilisez des registres de conteneur dans Azure avec vos pipelines de développement et de déploiement existants, et exploitez l’expertise de la communauté de Docker.</span><span class="sxs-lookup"><span data-stu-id="9a6be-106">Use container registries in Azure with your existing container development and deployment pipelines, and draw on the body of Docker community expertise.</span></span>

## <a name="management-package"></a><span data-ttu-id="9a6be-107">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="9a6be-107">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="9a6be-108">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="9a6be-108">Install the npm module</span></span>

<span data-ttu-id="9a6be-109">Installer le module npm Azure Container Registry</span><span class="sxs-lookup"><span data-stu-id="9a6be-109">Install the Azure container registry npm module</span></span>

```bash
npm install azure-arm-containerregistry
```

### <a name="example"></a><span data-ttu-id="9a6be-110">exemples</span><span class="sxs-lookup"><span data-stu-id="9a6be-110">Example</span></span>

<span data-ttu-id="9a6be-111">Cet exemple obtient une liste des conteneurs disponibles.</span><span class="sxs-lookup"><span data-stu-id="9a6be-111">This example gets a list of the available containers.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const ContainerRegistryManagement = require('azure-arm-containerregistry');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const manager = new ContainerRegistryManagement(
      credentials,
      subscriptionId
    );
    return manager.registries.list();
  })
  .then(registries => {
    console.log('List of registries:');
    console.dir(registries, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="9a6be-112">Exemples</span><span class="sxs-lookup"><span data-stu-id="9a6be-112">Samples</span></span>

<span data-ttu-id="9a6be-113">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="9a6be-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
