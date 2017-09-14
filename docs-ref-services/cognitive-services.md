---
title: Modules Azure Cognitive Services pour Node.js
description: "Références pour les modules Azure Cognitive Services pour Node.js"
keywords: Azure, SDK, API, Cognitive Services, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cognitive Services
ms.openlocfilehash: fba98930fccaf4fa40dd1d0224031276f5fb7f84
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-cognitive-services-modules-for-nodejs"></a>Modules Azure Cognitive Services pour Node.js

## <a name="overview"></a>Vue d'ensemble

Azure Cognitive Services est un ensemble d’API, de SDK et de services qui permettent aux développeurs de créer des applications plus intelligentes, attrayantes et exposées. Microsoft Cognitive Services développe le portefeuille évolutif d’API de Machine Learning de Microsoft et permet aux développeurs d’ajouter facilement des fonctionnalités intelligentes telles que la détection d’émotion et vidéo, la reconnaissance faciale, vocale et de la vision ainsi que la compréhension vocale et du langage, dans leurs applications. Notre objectif est de proposer des expériences informatiques plus personnelles ainsi qu’une productivité assistée par des systèmes qui améliorent leurs capacités à voir, entendre, parler, comprendre et qui commencent même à raisonner.

## <a name="management-package"></a>Gestion des packages

### <a name="install-the-npm-module"></a>Installer le module npm

Installer le module npm Azure Cognitive Services

```bash
npm install azure-arm-cognitiveservices
```

### <a name="example"></a>Exemple

Cet exemple répertorie tous les comptes de service Cognitifs.

```javascript
const msRestAzure = require('ms-rest-azure');
const cognitiveServicesManagementClient = require('azure-arm-cognitiveservices');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const cognitiveServicesClient = new cognitiveServicesManagementClient(
      credentials,
      subscriptionId
    );
    return cognitiveServicesClient.cognitiveServicesAccounts.list();
  })
  .then(cognitiveServicesAccounts => {
    console.log('List of accounts:');
    console.dir(cognitiveServicesAccounts, { depth: null, colors: true });    
  });

```

## <a name="samples"></a>Exemples

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
