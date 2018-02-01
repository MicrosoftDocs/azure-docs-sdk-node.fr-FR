---
title: Modules Azure DevTest Labs pour Node.js
description: "Références pour les modules Azure DevTest Labs pour Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: DevTest Labs
ms.openlocfilehash: 7754280741c09d47e138518d33628c667944c651
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-devtest-labs-modules-for-nodejs"></a>Modules Azure DevTest Labs pour Node.js

Azure DevTest Labs est un service permettant aux développeurs et aux testeurs de créer rapidement des environnements dans Azure tout en réduisant le temps perdu et les coûts. Vous pouvez tester la dernière version de votre application en approvisionnant rapidement des environnements Windows et Linux à l’aide d’artefacts et de modèles réutilisables. DevTest Labs facilite l’intégration de votre pipeline de déploiement pour approvisionner des environnements à la demande. Faites évoluer votre test de charge de travail en approvisionnant plusieurs agents de test et créez des environnements pré-approvisionnés pour des formations et des démonstrations.

## <a name="management-package"></a>Gestion des packages

### <a name="install-the-npm-module"></a>Installer le module npm

Installer le module npm Azure DevTest Labs

```bash
npm install azure-arm-devtestlabs
```

### <a name="example"></a>exemples

Cet exemple obtient et imprime les détails d’un laboratoire.

```javascript
const msRestAzure = require('ms-rest-azure');
const DevTestLabsClient = require('azure-arm-devtestlabs');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';
const labName = 'your-lab-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new DevTestLabsClient(credentials, subscriptionId);
    return client.labOperations.getResource(resourceGroupName, labName);
  })
  .then(lab => {
    console.log('Details of lab:');
    console.dir(lab, { depth: null, colors: true });
  });


```

## <a name="samples"></a>Exemples

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
