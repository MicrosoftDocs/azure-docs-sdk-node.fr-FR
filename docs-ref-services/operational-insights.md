---
title: Modules Azure Operational Insights pour Node.js
description: "Références pour les modules Azure Operational Insights pour Node.js"
keywords: Azure, SDK, API, Operational Insights, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Operational Insights
ms.openlocfilehash: e7f7ee30509125a131346039c1245eb9fa6cb6b1
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-operational-insights-modules-for-nodejs"></a>Modules Azure Operational Insights pour Node.js

## <a name="overview"></a>Vue d'ensemble

## <a name="management-package"></a>Gestion des packages

### <a name="install-the-npm-module"></a>Installer le module npm

Utiliser npm pour installer le module Azure Operational Insights pour Node.js

```bash
npm install azure-arm-operationalinsights
```

### <a name="example"></a>Exemple 

Cet exemple crée un client, le connecte à Operational Insights et récupère une liste d’espaces de travail par un groupe de ressources spécifié.

```javascript
const msRestAzure = require('ms-rest-azure');
const OperationalInsightsManagement = require('azure-arm-operationalinsights');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = new OperationalInsightsManagement(
        credentials,
        subscriptionId
    );
    return client.workspaces.listByResourceGroup('resource-group-name');
})
.then(workspaces => {
    console.log(workspaces);
});
``` 

## <a name="samples"></a>Exemples

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
