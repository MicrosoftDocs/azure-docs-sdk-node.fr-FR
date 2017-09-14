---
title: Modules Azure Machine Learning Studio pour Node.js
description: "Références pour les modules Azure Machine Learning Studio pour Node.js"
keywords: Azure, SDK, API, apprentissage automatique, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Machine Learning
ms.openlocfilehash: 465b569d0eef53208211be2c2ff36d28bb28d107
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-machine-learning-modules-for-nodejs"></a><span data-ttu-id="1ca6b-104">Modules Azure Machine Learning Studio pour Node.js</span><span class="sxs-lookup"><span data-stu-id="1ca6b-104">Azure Machine Learning modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="1ca6b-105">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="1ca6b-105">Overview</span></span>

<span data-ttu-id="1ca6b-106">L’apprentissage automatique (Machine Learning) utilise des ordinateurs pour exécuter des modèles prédictifs qui apprennent à partir de données existantes afin de prévoir les tendances, résultats et comportements futurs.</span><span class="sxs-lookup"><span data-stu-id="1ca6b-106">Machine learning is a technique of data science that helps computers learn from existing data in order to forecast future behaviors, outcomes, and trends.</span></span> <span data-ttu-id="1ca6b-107">Ces prévisions ou prédictions générées à partir de l’apprentissage automatique peuvent rendre les applications et les appareils plus intelligents.</span><span class="sxs-lookup"><span data-stu-id="1ca6b-107">These forecasts or predictions from machine learning can make apps and devices smarter.</span></span> <span data-ttu-id="1ca6b-108">Lorsque vous faites vos achats en ligne, l’apprentissage automatique permet de recommander d’autres produits que vous êtes susceptible d’aimer, en fonction de ce que vous avez acheté.</span><span class="sxs-lookup"><span data-stu-id="1ca6b-108">When you shop online, machine learning helps recommend other products you might like based on what you've purchased.</span></span> <span data-ttu-id="1ca6b-109">Lorsque vous utilisez votre carte de crédit, l’apprentissage automatique compare la transaction à une base de données de transactions et aide la banque à détecter des fraudes.</span><span class="sxs-lookup"><span data-stu-id="1ca6b-109">When your credit card is swiped, machine learning compares the transaction to a database of transactions and helps detect fraud.</span></span> <span data-ttu-id="1ca6b-110">Lorsque votre robot aspirateur nettoie une pièce, l’apprentissage automatique l’aide à déterminer si le travail est terminé.</span><span class="sxs-lookup"><span data-stu-id="1ca6b-110">When your robot vacuum cleaner vacuums a room, machine learning helps it decide whether the job is done.</span></span>

## <a name="management-package"></a><span data-ttu-id="1ca6b-111">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="1ca6b-111">Management Package</span></span>


### <a name="install-the-npm-module"></a><span data-ttu-id="1ca6b-112">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="1ca6b-112">Install the npm module</span></span>

<span data-ttu-id="1ca6b-113">Installer le module npm Azure Machine Learning</span><span class="sxs-lookup"><span data-stu-id="1ca6b-113">Install the Azure Machine Learning npm module</span></span>

```bash
npm install azure-arm-machinelearning
```

### <a name="example"></a><span data-ttu-id="1ca6b-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="1ca6b-114">Example</span></span>

<span data-ttu-id="1ca6b-115">Cet exemple répertorie tous les plans d’engagement de Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="1ca6b-115">This example lists all machine learning committment plans.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const MachineLearningManagement = require('azure-arm-machinelearning');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new MachineLearningManagement.CommitmentPlansManagementClient(
      credentials,
      subscriptionId
    );
    return client.commitmentPlans.list();
  })
  .then(commitmentPlans => {
    console.log('List of commitmentPlans:');
    console.dir(commitmentPlans, { depth: null, colors: true });
  });
```

## <a name="samples"></a><span data-ttu-id="1ca6b-116">Exemples</span><span class="sxs-lookup"><span data-stu-id="1ca6b-116">Samples</span></span>

<span data-ttu-id="1ca6b-117">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="1ca6b-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
