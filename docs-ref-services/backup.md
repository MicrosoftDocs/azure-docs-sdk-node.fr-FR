---
title: Modules Sauvegarde Azure pour Node.js
description: "Références pour les modules Sauvegarde Azure pour Node.js"
keywords: Azure, SDK, API, sauvegarde, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Backup
ms.openlocfilehash: 3ff9bff16a520bca461198531fd4c02139d2b293
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-backup-modules-for-nodejs"></a><span data-ttu-id="611c6-104">Modules Sauvegarde Azure pour Node.js</span><span class="sxs-lookup"><span data-stu-id="611c6-104">Azure Backup Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="611c6-105">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="611c6-105">Overview</span></span>

<span data-ttu-id="611c6-106">Azure Backup est le service Azure qui vous permet de sauvegarder (ou de protéger) et de restaurer vos données dans le cloud Microsoft.</span><span class="sxs-lookup"><span data-stu-id="611c6-106">Azure Backup is the Azure-based service you can use to back up (or protect) and restore your data in the Microsoft cloud.</span></span> <span data-ttu-id="611c6-107">Azure Backup remplace votre solution de sauvegarde locale ou hors site par une solution basée dans le cloud à la fois fiable, sécurisée et économique.</span><span class="sxs-lookup"><span data-stu-id="611c6-107">Azure Backup replaces your existing on-premises or off-site backup solution with a cloud-based solution that is reliable, secure, and cost-competitive.</span></span> <span data-ttu-id="611c6-108">Azure Backup propose plusieurs composants que vous pouvez télécharger et déployer sur l’ordinateur ou sur le serveur approprié, ou dans le cloud.</span><span class="sxs-lookup"><span data-stu-id="611c6-108">Azure Backup offers multiple components that you download and deploy on the appropriate computer, server, or in the cloud.</span></span> <span data-ttu-id="611c6-109">Vous déployez un composant (ou un agent) en fonction de ce que vous souhaitez protéger.</span><span class="sxs-lookup"><span data-stu-id="611c6-109">The component, or agent, that you deploy depends on what you want to protect.</span></span> <span data-ttu-id="611c6-110">Vous pouvez utiliser tous les composants de Sauvegarde Azure (que vous protégiez des données en local ou dans le cloud) pour sauvegarder des données dans un coffre Recovery Services d’Azure.</span><span class="sxs-lookup"><span data-stu-id="611c6-110">All Azure Backup components (no matter whether you're protecting data on-premises or in the cloud) can be used to back up data to a Recovery Services vault in Azure.</span></span> 

## <a name="management-package"></a><span data-ttu-id="611c6-111">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="611c6-111">Management package</span></span>

### <a name="install-the-modules-with-npm"></a><span data-ttu-id="611c6-112">Installer les modules avec npm</span><span class="sxs-lookup"><span data-stu-id="611c6-112">Install the modules with npm</span></span>

<span data-ttu-id="611c6-113">Utiliser npm pour installer les modules Sauvegarde Azure pour Node.js</span><span class="sxs-lookup"><span data-stu-id="611c6-113">Use npm to install the Azure Backup modules for Node.js</span></span>

```bash
npm install azure-arm-recoveryservicesbackup
```

### <a name="example"></a><span data-ttu-id="611c6-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="611c6-114">Example</span></span>

<span data-ttu-id="611c6-115">Cet exemple répertorie les tâches de récupération pour un coffre et un groupe de ressources donnés.</span><span class="sxs-lookup"><span data-stu-id="611c6-115">This example lists the recovery jobs for a given vault and resource group.</span></span>

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

## <a name="samples"></a><span data-ttu-id="611c6-116">Exemples</span><span class="sxs-lookup"><span data-stu-id="611c6-116">Samples</span></span>

<span data-ttu-id="611c6-117">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="611c6-117">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
