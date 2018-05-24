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
ms.openlocfilehash: 07b6369ef69343cc47cd38484ebb87d050264775
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="azure-advisor-modules-for-nodejs"></a>Modules Azure Advisor pour Node.js

## <a name="overview"></a>Vue d'ensemble

Azure Advisor est un conseiller personnalisé basé dans le cloud qui décrit les meilleures pratiques à suivre pour optimiser vos déploiements Azure. Advisor analyse votre télémétrie de configuration et d’utilisation des ressources, puis recommande des solutions qui peuvent vous aider à améliorer la rentabilité, les performances, la haute disponibilité et la sécurité de vos ressources Azure.

Avec Advisor, vous pouvez :
- Bénéficier de recommandations en termes de meilleures pratiques proactives, interactives et personnalisées.
- Améliorer les performances, la sécurité et la haute disponibilité de vos ressources en identifiant les possibilités de réduction de vos dépenses Azure globales.
- Obtenir des recommandations avec des propositions d’actions intégrées.

## <a name="management-package"></a>Gestion des packages

### <a name="install-the-npm-module"></a>Installer le module npm

Installer le module npm Azure Advisor

```bash
npm install azure-arm-advisor
```

### <a name="example"></a>Exemples

Cet exemple affiche la liste des recommandations d’Azure Advisor.

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

## <a name="samples"></a>Exemples

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
