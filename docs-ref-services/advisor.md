---
title: Modules Azure Advisor pour Node.js
description: "Références pour les modules Azure Advisor pour Node.js"
keywords: Azure, SDK, API, Advisor, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Advisor
ms.openlocfilehash: 9d0b22cd5f164cb0b1bb79a2cda1aceba0187ba5
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
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

### <a name="example"></a>Exemple

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
