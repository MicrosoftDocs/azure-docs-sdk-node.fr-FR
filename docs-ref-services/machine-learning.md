---
title: Modules Azure Machine Learning Studio pour Node.js
description: Références pour les modules Azure Machine Learning Studio pour Node.js
author: hning86
ms.author: haining
manager: mwinkle
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Machine Learning
ms.openlocfilehash: 7e39084c65a40e47ed61cc01daf994aff447690e
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/08/2018
ms.locfileid: "51071699"
---
# <a name="azure-machine-learning-modules-for-nodejs"></a><span data-ttu-id="cda0d-103">Modules Azure Machine Learning Studio pour Node.js</span><span class="sxs-lookup"><span data-stu-id="cda0d-103">Azure Machine Learning modules for Node.js</span></span>

<span data-ttu-id="cda0d-104">L’apprentissage automatique (Machine Learning) utilise des ordinateurs pour exécuter des modèles prédictifs qui apprennent à partir de données existantes afin de prévoir les tendances, résultats et comportements futurs.</span><span class="sxs-lookup"><span data-stu-id="cda0d-104">Machine learning is a technique of data science that helps computers learn from existing data in order to forecast future behaviors, outcomes, and trends.</span></span> <span data-ttu-id="cda0d-105">Ces prévisions ou prédictions générées à partir de l’apprentissage automatique peuvent rendre les applications et les appareils plus intelligents.</span><span class="sxs-lookup"><span data-stu-id="cda0d-105">These forecasts or predictions from machine learning can make apps and devices smarter.</span></span> <span data-ttu-id="cda0d-106">Lorsque vous faites vos achats en ligne, l’apprentissage automatique permet de recommander d’autres produits que vous êtes susceptible d’aimer, en fonction de ce que vous avez acheté.</span><span class="sxs-lookup"><span data-stu-id="cda0d-106">When you shop online, machine learning helps recommend other products you might like based on what you've purchased.</span></span> <span data-ttu-id="cda0d-107">Lorsque vous utilisez votre carte de crédit, l’apprentissage automatique compare la transaction à une base de données de transactions et aide la banque à détecter des fraudes.</span><span class="sxs-lookup"><span data-stu-id="cda0d-107">When your credit card is swiped, machine learning compares the transaction to a database of transactions and helps detect fraud.</span></span> <span data-ttu-id="cda0d-108">Lorsque votre robot aspirateur nettoie une pièce, l’apprentissage automatique l’aide à déterminer si le travail est terminé.</span><span class="sxs-lookup"><span data-stu-id="cda0d-108">When your robot vacuum cleaner vacuums a room, machine learning helps it decide whether the job is done.</span></span>

## <a name="management-package"></a><span data-ttu-id="cda0d-109">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="cda0d-109">Management Package</span></span>


### <a name="install-the-npm-module"></a><span data-ttu-id="cda0d-110">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="cda0d-110">Install the npm module</span></span>

<span data-ttu-id="cda0d-111">Installer le module npm Azure Machine Learning</span><span class="sxs-lookup"><span data-stu-id="cda0d-111">Install the Azure Machine Learning npm module</span></span>

```bash
npm install azure-arm-machinelearning
```

### <a name="example"></a><span data-ttu-id="cda0d-112">Exemples</span><span class="sxs-lookup"><span data-stu-id="cda0d-112">Example</span></span>

<span data-ttu-id="cda0d-113">Cet exemple répertorie tous les plans d’engagement de Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="cda0d-113">This example lists all machine learning committment plans.</span></span>

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

## <a name="samples"></a><span data-ttu-id="cda0d-114">Exemples</span><span class="sxs-lookup"><span data-stu-id="cda0d-114">Samples</span></span>

<span data-ttu-id="cda0d-115">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="cda0d-115">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
