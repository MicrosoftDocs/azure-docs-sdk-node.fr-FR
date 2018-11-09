---
title: Modules Azure Advisor pour Node.js
description: Références pour les modules Azure Advisor pour Node.js
author: KumudD
ms.author: kumud
manager: jeconnoc
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Advisor
ms.openlocfilehash: 54686220006d27341dbb50a249d0b2f44411b112
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/08/2018
ms.locfileid: "51134408"
---
# <a name="azure-advisor-modules-for-nodejs"></a><span data-ttu-id="6d356-103">Modules Azure Advisor pour Node.js</span><span class="sxs-lookup"><span data-stu-id="6d356-103">Azure Advisor modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="6d356-104">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="6d356-104">Overview</span></span>

<span data-ttu-id="6d356-105">Azure Advisor est un conseiller personnalisé basé dans le cloud qui décrit les meilleures pratiques à suivre pour optimiser vos déploiements Azure.</span><span class="sxs-lookup"><span data-stu-id="6d356-105">Azure Advisor is a personalized cloud consultant that helps you follow best practices to optimize your Azure deployments.</span></span> <span data-ttu-id="6d356-106">Advisor analyse votre télémétrie de configuration et d’utilisation des ressources, puis recommande des solutions qui peuvent vous aider à améliorer la rentabilité, les performances, la haute disponibilité et la sécurité de vos ressources Azure.</span><span class="sxs-lookup"><span data-stu-id="6d356-106">Advisor analyzes your resource configuration and usage telemetry and then recommends solutions that can help you improve the cost effectiveness, performance, high availability, and security of your Azure resources.</span></span>

<span data-ttu-id="6d356-107">Avec Advisor, vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="6d356-107">With Advisor, you can:</span></span>
- <span data-ttu-id="6d356-108">Bénéficier de recommandations en termes de meilleures pratiques proactives, interactives et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="6d356-108">Get proactive, actionable, and personalized best practices recommendations.</span></span>
- <span data-ttu-id="6d356-109">Améliorer les performances, la sécurité et la haute disponibilité de vos ressources en identifiant les possibilités de réduction de vos dépenses Azure globales.</span><span class="sxs-lookup"><span data-stu-id="6d356-109">Improve the performance, security, and high availability of your resources, as you identify opportunities to reduce your overall Azure spend.</span></span>
- <span data-ttu-id="6d356-110">Obtenir des recommandations avec des propositions d’actions intégrées.</span><span class="sxs-lookup"><span data-stu-id="6d356-110">Get recommendations with proposed actions inline.</span></span>

## <a name="management-package"></a><span data-ttu-id="6d356-111">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="6d356-111">Management package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="6d356-112">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="6d356-112">Install the npm module</span></span>

<span data-ttu-id="6d356-113">Installer le module npm Azure Advisor</span><span class="sxs-lookup"><span data-stu-id="6d356-113">Install the Azure Advisor npm module</span></span>

```bash
npm install azure-arm-advisor
```

### <a name="example"></a><span data-ttu-id="6d356-114">Exemples</span><span class="sxs-lookup"><span data-stu-id="6d356-114">Example</span></span>

<span data-ttu-id="6d356-115">Cet exemple affiche la liste des recommandations d’Azure Advisor.</span><span class="sxs-lookup"><span data-stu-id="6d356-115">This example displays the list of recommendations from Azure Advisor.</span></span>

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

## <a name="samples"></a><span data-ttu-id="6d356-116">Exemples</span><span class="sxs-lookup"><span data-stu-id="6d356-116">Samples</span></span>

<span data-ttu-id="6d356-117">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="6d356-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
