---
title: Modules Azure DevTest Labs pour Node.js
description: Références pour les modules Azure DevTest Labs pour Node.js
author: craigcaseyMSFT
ms.author: v-craic
manager: v-laurab
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DevTest Labs
ms.openlocfilehash: 5bd010d26ca11f9909191f25128b9bdb89811fd5
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="azure-devtest-labs-modules-for-nodejs"></a><span data-ttu-id="b8691-103">Modules Azure DevTest Labs pour Node.js</span><span class="sxs-lookup"><span data-stu-id="b8691-103">Azure DevTest Labs modules for Node.js</span></span>

<span data-ttu-id="b8691-104">Azure DevTest Labs est un service permettant aux développeurs et aux testeurs de créer rapidement des environnements dans Azure tout en réduisant le temps perdu et les coûts.</span><span class="sxs-lookup"><span data-stu-id="b8691-104">Azure DevTest Labs is a service that helps developers and testers quickly create environments in Azure while minimizing waste and controlling cost.</span></span> <span data-ttu-id="b8691-105">Vous pouvez tester la dernière version de votre application en approvisionnant rapidement des environnements Windows et Linux à l’aide d’artefacts et de modèles réutilisables.</span><span class="sxs-lookup"><span data-stu-id="b8691-105">You can test the latest version of your application by quickly provisioning Windows and Linux environments using reusable templates and artifacts.</span></span> <span data-ttu-id="b8691-106">DevTest Labs facilite l’intégration de votre pipeline de déploiement pour approvisionner des environnements à la demande.</span><span class="sxs-lookup"><span data-stu-id="b8691-106">Easily integrate your deployment pipeline with DevTest Labs to provision on-demand environments.</span></span> <span data-ttu-id="b8691-107">Faites évoluer votre test de charge de travail en approvisionnant plusieurs agents de test et créez des environnements pré-approvisionnés pour des formations et des démonstrations.</span><span class="sxs-lookup"><span data-stu-id="b8691-107">Scale up your load testing by provisioning multiple test agents, and create pre-provisioned environments for training and demos.</span></span>

## <a name="management-package"></a><span data-ttu-id="b8691-108">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="b8691-108">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="b8691-109">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="b8691-109">Install the npm module</span></span>

<span data-ttu-id="b8691-110">Installer le module npm Azure DevTest Labs</span><span class="sxs-lookup"><span data-stu-id="b8691-110">Install the Azure DevTest Labs npm module</span></span>

```bash
npm install azure-arm-devtestlabs
```

### <a name="example"></a><span data-ttu-id="b8691-111">Exemples</span><span class="sxs-lookup"><span data-stu-id="b8691-111">Example</span></span>

<span data-ttu-id="b8691-112">Cet exemple obtient et imprime les détails d’un laboratoire.</span><span class="sxs-lookup"><span data-stu-id="b8691-112">This example gets and prints the details of a lab.</span></span>

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

## <a name="samples"></a><span data-ttu-id="b8691-113">Exemples</span><span class="sxs-lookup"><span data-stu-id="b8691-113">Samples</span></span>

<span data-ttu-id="b8691-114">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="b8691-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
