---
title: Modules Azure Data Lake Analytics pour Node.js
description: Références pour les modules Azure Data Lake Analytics pour Node.js
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Data Lake Analytics
ms.openlocfilehash: 28dae604ae9977eb33470757e207ac12a592c676
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2018
ms.locfileid: "28116964"
---
# <a name="azure-data-lake-analytics-modules-for-nodejs"></a>Modules Azure Data Lake Analytics pour Node.js

Azure Data Lake Analytics est un service de travaux d’analyse à la demande, qui simplifie l’analyse du Big Data. Vous pouvez vous concentrer sur l’écriture, l’exécution et la gestion des travaux, plutôt que sur le fonctionnement de l’infrastructure distribuée. Au lieu de déployer, de configurer et d’optimiser le matériel, vous écrivez des requêtes pour transformer vos données et en extraire des informations pertinentes. Le service d’analyse peut traiter les travaux instantanément, quelle qu’en soit l’échelle, en définissant le compteur sur la puissance requise. Vous payez les travaux uniquement lorsque ceux-ci sont exécutés, ce qui rend le service économique. Le service d’analyse prend en charge Azure Active Directory, ce qui vous permet de gérer les accès et les rôles et de bénéficier d’une intégration à votre système d’identité local. Il inclut également U-SQL, un langage qui associe les avantages de SQL avec la puissance d'expression du code utilisateur. Le runtime distribué et évolutif d’U-SQL vous permet d’analyser efficacement les données situées dans le magasin et sur les serveurs SQL Server dans Azure, Azure SQL Database et Azure SQL Data Warehouse.

### <a name="management-package"></a>Gestion des packages

### <a name="install-the-npm-module"></a>Installer le module npm

Utiliser npm pour installer les modules Azure Data Lake Analytics pour Node.js

```bash
npm install azure-arm-datalake-analytics
```

### <a name="example"></a>exemples

Cet exemple répertorie tous les comptes Analytics pour un abonnement donné.

```javascript
const msRestAzure = require('ms-rest-azure');
const adlsManagement = require('azure-arm-datalake-analytics');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const accountClient = new adlsManagement.DataLakeAnalyticsAccountClient(
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
