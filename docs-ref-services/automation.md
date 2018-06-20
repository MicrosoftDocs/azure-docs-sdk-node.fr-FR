---
title: Modules Azure Automation pour Node.js
description: Références pour les modules Azure Automation pour Node.js
author: eamonoreilly
ms.author: eamono
manager: nirb
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Automation
ms.openlocfilehash: 5efe0c0633313bcf489b05b8a54f71bba9a00da5
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34264710"
---
# <a name="azure-automation-modules-for-nodejs"></a><span data-ttu-id="75b99-103">Modules Azure Automation pour Node.js</span><span class="sxs-lookup"><span data-stu-id="75b99-103">Azure Automation Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="75b99-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="75b99-104">Overview</span></span>

<span data-ttu-id="75b99-105">Azure Automation permet aux utilisateurs d’automatiser les tâches répétitives, manuelles, de longue durée et susceptibles de générer des erreurs, qui sont communément exécutées dans un environnement cloud et d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="75b99-105">Azure Automation provides a way for users to automate the manual, long-running, error-prone, and frequently repeated tasks that are commonly performed in a cloud and enterprise environment.</span></span> <span data-ttu-id="75b99-106">Automation fait gagner du temps, accroît la fiabilité des tâches d’administration récurrentes et planifie même leur exécution automatique à intervalles réguliers.</span><span class="sxs-lookup"><span data-stu-id="75b99-106">Automation saves time and increases the reliability of regular administrative tasks and even schedules them to be automatically performed at regular intervals.</span></span> <span data-ttu-id="75b99-107">Vous pouvez automatiser les processus à l'aide de Runbooks ou automatiser la gestion de configuration avec la Configuration de l'état souhaité (DSC, Desired State Configuration).</span><span class="sxs-lookup"><span data-stu-id="75b99-107">You can automate processes using runbooks or automate configuration management using Desired State Configuration.</span></span>

## <a name="management-package"></a><span data-ttu-id="75b99-108">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="75b99-108">Management package</span></span>

### <a name="install-the-modules-with-npm"></a><span data-ttu-id="75b99-109">Installer les modules avec npm</span><span class="sxs-lookup"><span data-stu-id="75b99-109">Install the modules with npm</span></span>

<span data-ttu-id="75b99-110">Utiliser npm pour installer les modules Azure Automation pour Node.js</span><span class="sxs-lookup"><span data-stu-id="75b99-110">Use npm to install the Azure Automation modules for Node.js</span></span>

```bash
npm install azure-arm-automation
```

### <a name="example"></a><span data-ttu-id="75b99-111">Exemples</span><span class="sxs-lookup"><span data-stu-id="75b99-111">Example</span></span>

<span data-ttu-id="75b99-112">Cet exemple répertorie les comptes Automation.</span><span class="sxs-lookup"><span data-stu-id="75b99-112">This example lists the automation accounts.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const AutomationManagement = require('azure-arm-automation');

const subcriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new AutomationManagement(credentials, subcriptionId);
    return client.automationAccounts.listByResourceGroup(resourceGroup);
  })
  .then(automationAccounts =>
    console.dir(automationAccounts, { depth: null, colors: true })
  )
  .catch(err => console.log(err));

```

## <a name="samples"></a><span data-ttu-id="75b99-113">Exemples</span><span class="sxs-lookup"><span data-stu-id="75b99-113">Samples</span></span>

<span data-ttu-id="75b99-114">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="75b99-114">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
