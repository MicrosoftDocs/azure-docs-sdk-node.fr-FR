---
title: Modules Azure Commerce pour Node.js
description: "Références pour les modules Azure Commerce pour Node.js"
keywords: Azure, SDK, API, Commerce, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Commerce
ms.openlocfilehash: b337e070ee7da0b852d8cad1d4e163d7f8130857
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-commerce-modules-for-nodejs"></a>Modules Azure Commerce pour Node.js

## <a name="overview"></a>Vue d'ensemble

Utilisez les API Azure Commerce pour extraire les données d’utilisation et de ressources dans vos outils d’analyse de données préférés. Les API d’utilisation des ressources Azure et RateCard peuvent vous aider à prévoir vos coûts avec précision et à les gérer. Les API sont implémentées en tant que fournisseur de ressources et font partie intégrante de la famille d’API exposées par Azure Resource Manager.

## <a name="management-package"></a>Gestion des packages

### <a name="install-the-npm-module"></a>Installer le module npm

Installer le module npm Azure Commerce

```bash
npm install azure-arm-commerce
```

### <a name="example"></a>Exemple

Cet exemple récupère vos données de consommation Azure estimées pour le mois dernier.

```javascript
const msRestAzure = require('ms-rest-azure');
const CommerceManagement = require('azure-arm-commerce');

const endDate = new Date();
endDate.setUTCHours(0, 0, 0, 0);
const startDate = new Date();
startDate.setMonth(startDate.getMonth() - 1);
startDate.setUTCHours(0, 0, 0, 0);

const subscriptionId = 'your-subscription-id';
const usageOptions = {
  showDetails: true,
  granularity: 'Daily'
};

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new CommerceManagement(credentials, subscriptionId);
    return client.usageAggregates.list(startDate, endDate, usageOptions);
  })
  .then(usage => {
    console.dir(usage, { depth: null, colors: true });
  });
```

## <a name="samples"></a>Exemples

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
