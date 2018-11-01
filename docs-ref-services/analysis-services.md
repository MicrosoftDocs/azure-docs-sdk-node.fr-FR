---
title: Modules Azure Analysis Services pour Node.js
description: Références pour les modules Azure Analysis Services pour Node.js
author: Minewiskan
ms.author: owend
manager: kfile
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Analysis Services
ms.openlocfilehash: 5214cd2f171074ba330bc639643dfba490540856
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50339977"
---
# <a name="azure-analysis-services-modules-for-nodejs"></a>Modules Azure Analysis Services pour Node.js

## <a name="overview"></a>Vue d’ensemble
Ce package fournit un module Node.js qui facilite la gestion de Microsoft Azure Analysis Services.

## <a name="management-package"></a>Gestion des packages

### <a name="install-the-npm-module"></a>Installer le module npm

Installer le module npm Azure Analysis Services

```bash
npm install azure-arm-analysisservices
```

### <a name="example"></a>Exemples

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
