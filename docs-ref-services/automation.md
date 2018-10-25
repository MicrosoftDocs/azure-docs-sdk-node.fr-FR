---
title: Modules Azure Automation pour Node.js
description: Références pour les modules Azure Automation pour Node.js
author: eamonoreilly
ms.author: eamono
manager: nirb
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Automation
ms.openlocfilehash: f364bb09c97c1262f640a4b48514c6abaee5f14a
ms.sourcegitcommit: 7cea63cdde5fcfb19271bf7a93b1eb0dabdddb31
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "49779250"
---
# <a name="azure-automation-modules-for-nodejs"></a>Modules Azure Automation pour Node.js

## <a name="overview"></a>Vue d’ensemble

Azure Automation permet aux utilisateurs d’automatiser les tâches répétitives, manuelles, de longue durée et susceptibles de générer des erreurs, qui sont communément exécutées dans un environnement cloud et d’entreprise. Automation fait gagner du temps, accroît la fiabilité des tâches d’administration récurrentes et planifie même leur exécution automatique à intervalles réguliers. Vous pouvez automatiser les processus à l'aide de Runbooks ou automatiser la gestion de configuration avec la Configuration de l'état souhaité (DSC, Desired State Configuration).

## <a name="management-package"></a>Gestion des packages

### <a name="install-the-modules-with-npm"></a>Installer les modules avec npm

Utiliser npm pour installer les modules Azure Automation pour Node.js

```bash
npm install azure-arm-automation
```

### <a name="example"></a>Exemples

Cet exemple répertorie les comptes Automation.

```javascript
const msRestAzure = require('ms-rest-azure');
const AutomationManagement = require('azure-arm-automation');

const subcriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new AutomationManagement(credentials, subcriptionId);
    return client.automationAccounts.listByResourceGroup(resourceGroup);
  })
  .then(automationAccounts =>
    console.dir(automationAccounts, { depth: null, colors: true })
  )
  .catch(err => console.log(err));
```

## <a name="samples"></a>Exemples

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
