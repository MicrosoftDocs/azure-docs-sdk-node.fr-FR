---
title: Modules Azure Analysis Services pour Node.js
description: "Références pour les modules Azure Analysis Services pour Node.js"
keywords: Azure, SDK, API, Analysis Services, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Analysis Services
ms.openlocfilehash: ff38883eed2de5d95fb5bd5fd951c6b9564a4b35
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-analysis-services-modules-for-nodejs"></a>Modules Azure Analysis Services pour Node.js

## <a name="overview"></a>Vue d'ensemble
Ce package fournit un module Node.js qui facilite la gestion de Microsoft Azure Analysis Services.

## <a name="management-package"></a>Gestion des packages

### <a name="install-the-npm-module"></a>Installer le module npm

Installer le module npm Azure Analysis Services

```bash
npm install azure-arm-analysisservices
```

### <a name="example"></a>Exemple

Cet exemple répertorie tous les serveurs Analysis Services disponibles.

```javascript
const msRestAzure = require('ms-rest-azure');
const analysisServicesManagement = require('azure-arm-analysisservices');

const subscriptionId = 'your-subscription-id';
let analysisServicesClient;

msRestAzure.interactiveLogin().then(credentials => {
  analysisServicesClient = new analysisServicesManagement(credentials, subscriptionId);

  analysisServicesClient.servers
    .list()
    .then(servers => console.log('Retrieved analysis services servers: ', servers));
});
```

## <a name="samples"></a>Exemples

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
