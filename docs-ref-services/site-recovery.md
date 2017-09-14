---
title: Modules Azure Site Recovery pour Node.js
description: "Références pour les modules Azure Site Recovery pour Node.js"
keywords: "Azure, SDK, API, Récupération de sites, Node.js"
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Site Recovery
ms.openlocfilehash: 3537503118a6fbe181c8cc4b26da545a4bdbd764
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-site-recovery-modules-for-nodejs"></a>Modules Azure Site Recovery pour Node.js

## <a name="overview"></a>Vue d'ensemble

La récupération de sites vous permet d’automatiser la réplication de machines virtuelles Azure entre des régions, depuis des machines virtuelles locales et des serveurs physiques vers Azure, et depuis des machines locales vers un centre de données secondaire.

En savoir plus sur [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview).

## <a name="management-package"></a>Gestion des packages

### <a name="install-the-npm-module"></a>Installer le module npm

Installer le module npm de service Azure Site Recovery

```bash
npm install azure-arm-recoveryservices
```

### <a name="example"></a>Exemple

Cet exemple répertorie le service de récupération de sites pour un groupe de ressources.

```javascript
const msRestAzure = require('ms-rest-azure');
const RecoveryServicesManagement = require('azure-arm-recoveryservices');

const subscriptionId = 'your-subscription-id';
const resourceGroupName = 'your-resource-group-name';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RecoveryServicesManagement(credentials, subscriptionId);
    return client.vaults.listByResourceGroup(resourceGroupName);
  })
  .then(vaults => {
    console.log('List of vaults:');
    console.dir(vaults, { depth: null, colors: true });
  });
  
```

## <a name="samples"></a>Exemples

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
