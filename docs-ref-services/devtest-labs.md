---
title: Modules Azure DevTest Labs pour Node.js
description: "Références pour les modules Azure DevTest Labs pour Node.js"
keywords: Azure, SDK, API, DevTest Labs, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DevTest Labs
ms.openlocfilehash: 933ce8971e02c2898d296112282169b8c7dca1c7
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-devtest-labs-modules-for-nodejs"></a><span data-ttu-id="bd10f-104">Modules Azure DevTest Labs pour Node.js</span><span class="sxs-lookup"><span data-stu-id="bd10f-104">Azure DevTest Labs modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="bd10f-105">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="bd10f-105">Overview</span></span>

<span data-ttu-id="bd10f-106">Azure DevTest Labs est un service permettant aux développeurs et aux testeurs de créer rapidement des environnements dans Azure tout en réduisant le temps perdu et les coûts.</span><span class="sxs-lookup"><span data-stu-id="bd10f-106">Azure DevTest Labs is a service that helps developers and testers quickly create environments in Azure while minimizing waste and controlling cost.</span></span> <span data-ttu-id="bd10f-107">Vous pouvez tester la dernière version de votre application en approvisionnant rapidement des environnements Windows et Linux à l’aide d’artefacts et de modèles réutilisables.</span><span class="sxs-lookup"><span data-stu-id="bd10f-107">You can test the latest version of your application by quickly provisioning Windows and Linux environments using reusable templates and artifacts.</span></span> <span data-ttu-id="bd10f-108">DevTest Labs facilite l’intégration de votre pipeline de déploiement pour approvisionner des environnements à la demande.</span><span class="sxs-lookup"><span data-stu-id="bd10f-108">Easily integrate your deployment pipeline with DevTest Labs to provision on-demand environments.</span></span> <span data-ttu-id="bd10f-109">Faites évoluer votre test de charge de travail en approvisionnant plusieurs agents de test et créez des environnements pré-approvisionnés pour des formations et des démonstrations.</span><span class="sxs-lookup"><span data-stu-id="bd10f-109">Scale up your load testing by provisioning multiple test agents, and create pre-provisioned environments for training and demos.</span></span>

## <a name="management-package"></a><span data-ttu-id="bd10f-110">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="bd10f-110">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="bd10f-111">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="bd10f-111">Install the npm module</span></span>

<span data-ttu-id="bd10f-112">Installer le module npm Azure DevTest Labs</span><span class="sxs-lookup"><span data-stu-id="bd10f-112">Install the Azure DevTest Labs npm module</span></span>

```bash
npm install azure-arm-devtestlabs
```

### <a name="example"></a><span data-ttu-id="bd10f-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="bd10f-113">Example</span></span>

<span data-ttu-id="bd10f-114">Cet exemple obtient et imprime les détails d’un laboratoire.</span><span class="sxs-lookup"><span data-stu-id="bd10f-114">This example gets and prints the details of a lab.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const DevTestLabsClient = require('azure-arm-devtestlabs');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';
const labName = 'your-lab-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new DevTestLabsClient(credentials, subscriptionId);
    return client.labOperations.getResource(resourceGroupName, labName);
  })
  .then(lab => {
    console.log('Details of lab:');
    console.dir(lab, { depth: null, colors: true });
  });


```

## <a name="samples"></a><span data-ttu-id="bd10f-115">Exemples</span><span class="sxs-lookup"><span data-stu-id="bd10f-115">Samples</span></span>

<span data-ttu-id="bd10f-116">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="bd10f-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
