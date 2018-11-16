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
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51439103"
---
# <a name="azure-machine-learning-modules-for-nodejs"></a>Modules Azure Machine Learning Studio pour Node.js

L’apprentissage automatique (Machine Learning) utilise des ordinateurs pour exécuter des modèles prédictifs qui apprennent à partir de données existantes afin de prévoir les tendances, résultats et comportements futurs. Ces prévisions ou prédictions générées à partir de l’apprentissage automatique peuvent rendre les applications et les appareils plus intelligents. Lorsque vous faites vos achats en ligne, l’apprentissage automatique permet de recommander d’autres produits que vous êtes susceptible d’aimer, en fonction de ce que vous avez acheté. Lorsque vous utilisez votre carte de crédit, l’apprentissage automatique compare la transaction à une base de données de transactions et aide la banque à détecter des fraudes. Lorsque votre robot aspirateur nettoie une pièce, l’apprentissage automatique l’aide à déterminer si le travail est terminé.

## <a name="management-package"></a>Gestion des packages


### <a name="install-the-npm-module"></a>Installer le module npm

Installer le module npm Azure Machine Learning

```bash
npm install azure-arm-machinelearning
```

### <a name="example"></a>Exemples

Cet exemple répertorie tous les plans d’engagement de Machine Learning.

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

## <a name="samples"></a>Exemples

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
