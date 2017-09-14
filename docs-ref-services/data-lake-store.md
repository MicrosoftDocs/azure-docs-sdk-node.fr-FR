---
title: Modules Azure Data Lake Store pour Node.js
description: "Références pour les modules Azure Data Lake Store pour Node.js"
keywords: Azure, SDK, API, Data Lake Store, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Store
ms.openlocfilehash: 5885bf8f073e4f4f1ac2be88b8691b092e8a21d3
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-data-lake-store-modules-for-nodejs"></a>Modules Azure Data Lake Store pour Node.js

## <a name="overview"></a>Vue d'ensemble
Azure Data Lake Store est un référentiel d'entreprise à très grande échelle pour les charges de travail d'analyse du Big Data. Azure Data Lake vous permet de capturer les données de toute taille, de tout type et à toute vitesse d'ingestion dans un emplacement unique en vue d'une analyse opérationnelle et exploratoire.

## <a name="management-package"></a>Gestion des packages

### <a name="install-the-npm-module"></a>Installer le module npm

Utiliser npm pour installer les modules Azure Data Lake Store pour Node.js

```bash
npm install azure-arm-datalake-store
```

### <a name="example"></a>Exemple

Cet exemple répertorie tous les comptes Data Lake Store d’un abonnement Azure donné

```javascript
const msRestAzure = require('ms-rest-azure');
const adlsManagement = require('azure-arm-datalake-store');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const accountClient = new adlsManagement.DataLakeStoreAccountClient(
    credentials,
    subscriptionId
  );
  accountClient.account.list().then(result => {
    console.log(result);
  });
});
```

## <a name="samples"></a>Exemples

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
