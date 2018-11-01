---
title: Modules Azure Commerce pour Node.js
description: Références pour les modules Azure Commerce pour Node.js
author: rloutlaw
ms.author: ROutlaw
manager: angrobew
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Commerce
ms.openlocfilehash: 87a0e8d689d8d782a705a4525fdbe9b681403c07
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50378527"
---
# <a name="azure-commerce-modules-for-nodejs"></a>Modules Azure Commerce pour Node.js

## <a name="overview"></a>Vue d’ensemble

Utilisez les API Azure Commerce pour extraire les données d’utilisation et de ressources dans vos outils d’analyse de données préférés. Les API d’utilisation des ressources Azure et RateCard peuvent vous aider à prévoir vos coûts avec précision et à les gérer. Les API sont implémentées en tant que fournisseur de ressources et font partie intégrante de la famille d’API exposées par Azure Resource Manager.

## <a name="management-package"></a>Gestion des packages

### <a name="install-the-npm-module"></a>Installer le module npm

Installer le module npm Azure Commerce

```bash
npm install azure-arm-commerce
```

### <a name="example"></a>Exemples

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
