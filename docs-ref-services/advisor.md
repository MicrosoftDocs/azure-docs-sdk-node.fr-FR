---
title: Modules Azure Advisor pour Node.js
description: Références pour les modules Azure Advisor pour Node.js
author: KumudD
ms.author: kumud
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.devlang: nodejs
ms.service: Advisor
ms.openlocfilehash: 952ac4bb67f4c177a06ce0ae3eb0fac7fa8ded54
ms.sourcegitcommit: 34172ad11850839ddd81d02841807e07f3761425
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58052588"
---
# <a name="azure-advisor-modules-for-nodejs"></a><span data-ttu-id="1068d-103">Modules Azure Advisor pour Node.js</span><span class="sxs-lookup"><span data-stu-id="1068d-103">Azure Advisor modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="1068d-104">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="1068d-104">Overview</span></span>

<span data-ttu-id="1068d-105">Azure Advisor est un conseiller personnalisé basé dans le cloud qui décrit les meilleures pratiques à suivre pour optimiser vos déploiements Azure.</span><span class="sxs-lookup"><span data-stu-id="1068d-105">Azure Advisor is a personalized cloud consultant that helps you follow best practices to optimize your Azure deployments.</span></span> <span data-ttu-id="1068d-106">Advisor analyse votre télémétrie de configuration et d’utilisation des ressources, puis recommande des solutions qui peuvent vous aider à améliorer la rentabilité, les performances, la haute disponibilité et la sécurité de vos ressources Azure.</span><span class="sxs-lookup"><span data-stu-id="1068d-106">Advisor analyzes your resource configuration and usage telemetry and then recommends solutions that can help you improve the cost effectiveness, performance, high availability, and security of your Azure resources.</span></span>

<span data-ttu-id="1068d-107">Avec Advisor, vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="1068d-107">With Advisor, you can:</span></span>
- <span data-ttu-id="1068d-108">Bénéficier de recommandations en termes de meilleures pratiques proactives, interactives et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="1068d-108">Get proactive, actionable, and personalized best practices recommendations.</span></span>
- <span data-ttu-id="1068d-109">Améliorer les performances, la sécurité et la haute disponibilité de vos ressources en identifiant les possibilités de réduction de vos dépenses Azure globales.</span><span class="sxs-lookup"><span data-stu-id="1068d-109">Improve the performance, security, and high availability of your resources, as you identify opportunities to reduce your overall Azure spend.</span></span>
- <span data-ttu-id="1068d-110">Obtenir des recommandations avec des propositions d’actions intégrées.</span><span class="sxs-lookup"><span data-stu-id="1068d-110">Get recommendations with proposed actions inline.</span></span>

## <a name="management-package"></a><span data-ttu-id="1068d-111">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="1068d-111">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="1068d-112">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="1068d-112">Install the npm module</span></span>

<span data-ttu-id="1068d-113">Installer le module npm Azure Advisor</span><span class="sxs-lookup"><span data-stu-id="1068d-113">Install the Azure Advisor npm module</span></span>

```bash
npm install azure-arm-advisor
```

### <a name="example"></a><span data-ttu-id="1068d-114">Exemples</span><span class="sxs-lookup"><span data-stu-id="1068d-114">Example</span></span>

<span data-ttu-id="1068d-115">Cet exemple affiche la liste des recommandations d’Azure Advisor.</span><span class="sxs-lookup"><span data-stu-id="1068d-115">This example displays the list of recommendations from Azure Advisor.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const advisorManagement = require('azure-arm-advisor');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new advisorManagement(credentials, subscriptionId);
  client.recommendations.list().then(recommendations => {
    console.log('List of recommendations:');
    console.dir(recommendations, {depth: null, colors: true});
  });
});
```

## <a name="samples"></a><span data-ttu-id="1068d-116">Exemples</span><span class="sxs-lookup"><span data-stu-id="1068d-116">Samples</span></span>

<span data-ttu-id="1068d-117">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="1068d-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
