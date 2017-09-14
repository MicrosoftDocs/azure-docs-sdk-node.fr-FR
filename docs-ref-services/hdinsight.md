---
title: Modules Azure HDInsight pour Node.js
description: "Références pour les modules Azure HDInsight pour Node.js"
keywords: Azure, SDK, API, HDInsight, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: HDInsight
ms.openlocfilehash: 1df988e98def42dcf33e90b4c3debece8cbe85e3
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-hdinsight-modules-for-nodejs"></a><span data-ttu-id="665f1-104">Modules Azure HDInsight pour Node.js</span><span class="sxs-lookup"><span data-stu-id="665f1-104">Azure HDInsight Modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="665f1-105">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="665f1-105">Overview</span></span>

<span data-ttu-id="665f1-106">Azure HDInsight est une distribution par cloud des composants Hadoop à partir de Hortonworks Data Platform (HDP).</span><span class="sxs-lookup"><span data-stu-id="665f1-106">Azure HDInsight is a cloud distribution of the Hadoop components from the Hortonworks Data Platform (HDP).</span></span> <span data-ttu-id="665f1-107">Apache Hadoop était l’infrastructure open source d’origine de traitement et d’analyse distribués des jeux de données volumineuses sur des clusters d’ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="665f1-107">Apache Hadoop was the original open-source framework for distributed processing and analysis of big data sets on clusters of computers.</span></span>

<span data-ttu-id="665f1-108">HDInsight rend les technologies Hadoop plus faciles à utiliser, avec :</span><span class="sxs-lookup"><span data-stu-id="665f1-108">HDInsight makes Hadoop technologies easier to use, with:</span></span>
- <span data-ttu-id="665f1-109">Moins de tâches d’installation et de configuration.</span><span class="sxs-lookup"><span data-stu-id="665f1-109">Less setup and configuration.</span></span> <span data-ttu-id="665f1-110">Consultez Approvisionnement de clusters dans HDInsight.</span><span class="sxs-lookup"><span data-stu-id="665f1-110">See Provision Hadoop clusters in HDInsight.</span></span>
- <span data-ttu-id="665f1-111">Haute disponibilité et fiabilité.</span><span class="sxs-lookup"><span data-stu-id="665f1-111">High availability and reliability.</span></span> <span data-ttu-id="665f1-112">Consultez Disponibilité et fiabilité de HDInsight.</span><span class="sxs-lookup"><span data-stu-id="665f1-112">See HDInsight availability and reliability.</span></span>
- <span data-ttu-id="665f1-113">Sécurité et gouvernance grâce à l’intégration avec Active Directory.</span><span class="sxs-lookup"><span data-stu-id="665f1-113">Security and governance through integration with Active Directory.</span></span> <span data-ttu-id="665f1-114">Consultez Clusters joints à un domaine.</span><span class="sxs-lookup"><span data-stu-id="665f1-114">See Domain-joined clusters.</span></span>
- <span data-ttu-id="665f1-115">Mise à l’échelle dynamique sans interrompre les travaux</span><span class="sxs-lookup"><span data-stu-id="665f1-115">Dynamic scaling without interrupting jobs</span></span>
- <span data-ttu-id="665f1-116">Mises à jour de composant et versions actuelles.</span><span class="sxs-lookup"><span data-stu-id="665f1-116">Component updates and current versions.</span></span> <span data-ttu-id="665f1-117">Consultez Composants et versions Hadoop sur HDInsight.</span><span class="sxs-lookup"><span data-stu-id="665f1-117">See Hadoop components and versions on HDInsight.</span></span>
- <span data-ttu-id="665f1-118">Intégration avec d’autres services Azure, notamment Web Apps et SQL Database</span><span class="sxs-lookup"><span data-stu-id="665f1-118">Integration with other Azure services, including Web apps and SQL Database</span></span>

<span data-ttu-id="665f1-119">La pile de technologies Hadoop inclut des logiciels et utilitaires liés, notamment Apache Hive, HBase, Spark, Kafka et bien d’autres encore.</span><span class="sxs-lookup"><span data-stu-id="665f1-119">The Hadoop technology stack includes related software and utilities, including Apache Hive, HBase, Spark, Kafka, and many others.</span></span> 

## <a name="management-package"></a><span data-ttu-id="665f1-120">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="665f1-120">Management package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="665f1-121">Installer les modules npm</span><span class="sxs-lookup"><span data-stu-id="665f1-121">Install the npm modules</span></span>

<span data-ttu-id="665f1-122">Utiliser npm pour installer les modules Azure HDInsight pour Node.js</span><span class="sxs-lookup"><span data-stu-id="665f1-122">Use npm to install the Azure HDInsight modules for Node.js</span></span>

```bash
npm install azure-arm-hdinsight
```

```bash
azure-arm-hdinsight-jobs
```

### <a name="example"></a><span data-ttu-id="665f1-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="665f1-123">Example</span></span> 

<span data-ttu-id="665f1-124">Cet exemple crée un client HD Insight et répertorie ensuite tous les clusters disponibles.</span><span class="sxs-lookup"><span data-stu-id="665f1-124">This example creates an HD Insight client and then lists all of the available clusters.</span></span> 

```javascript
const msRestAzure = require('ms-rest-azure');
const HDInsightManagementClient = require('azure-arm-hdinsight');

const subscriptionId = 'my-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
    const client = HDInsightManagementClient.createHDInsightManagementClient(
        credentials
    );

    credentials.subscriptionId = subscriptionId;

    client.clusters.list((err, result) => {
        console.log(result);
    });
});
```

## <a name="samples"></a><span data-ttu-id="665f1-125">Exemples</span><span class="sxs-lookup"><span data-stu-id="665f1-125">Samples</span></span>

<span data-ttu-id="665f1-126">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="665f1-126">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
