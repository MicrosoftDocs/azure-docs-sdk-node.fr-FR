---
title: Modules Sauvegarde Azure pour Node.js
description: Références pour les modules Sauvegarde Azure pour Node.js
author: markgalioto
ms.author: markgal
manager: carmonm
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Backup
ms.openlocfilehash: bf3e66ac8341cebd28dee20b6370ed3e5fbfbfa0
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50378087"
---
# <a name="azure-backup-modules-for-nodejs"></a>Modules Sauvegarde Azure pour Node.js

## <a name="overview"></a>Vue d’ensemble

Azure Backup est le service Azure qui vous permet de sauvegarder (ou de protéger) et de restaurer vos données dans le cloud Microsoft. Azure Backup remplace votre solution de sauvegarde locale ou hors site par une solution basée dans le cloud à la fois fiable, sécurisée et économique. Azure Backup propose plusieurs composants que vous pouvez télécharger et déployer sur l’ordinateur ou sur le serveur approprié, ou dans le cloud. Vous déployez un composant (ou un agent) en fonction de ce que vous souhaitez protéger. Vous pouvez utiliser tous les composants de Sauvegarde Azure (que vous protégiez des données en local ou dans le cloud) pour sauvegarder des données dans un coffre Recovery Services d’Azure. 

## <a name="management-package"></a>Gestion des packages

### <a name="install-the-modules-with-npm"></a>Installer les modules avec npm

Utiliser npm pour installer les modules Sauvegarde Azure pour Node.js

```bash
npm install azure-arm-recoveryservicesbackup
```

### <a name="example"></a>Exemples

Cet exemple répertorie les tâches de récupération pour un coffre et un groupe de ressources donnés.

```javascript
const msRestAzure = require('ms-rest-azure');
const RecoveryServicesBackupManagement = require('azure-arm-recoveryservicesbackup');

const subcriptionId = 'your-subscription-id';
const vault = 'your-recovery-service-vault';
const resourceGroupName = 'your-resource-group';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const client = new RecoveryServicesBackupManagement(
      credentials,
      subcriptionId
    );
    return client.jobs.list(vault, resourceGroupName);
  })
  .then(jobs => console.dir(jobs, { depth: null, colors: true }))
  .catch(err => console.log(err));
```

## <a name="samples"></a>Exemples

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
