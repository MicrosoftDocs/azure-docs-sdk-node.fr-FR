---
title: Modules Azure HDInsight pour Node.js
description: Références pour les modules Azure HDInsight pour Node.js
author: mumian
ms.author: jgao
manager: cgronlun
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: HDInsight
ms.openlocfilehash: 311933f619ceab5d679c8b0a767d3b52960c5ce1
ms.sourcegitcommit: 75051fec38cc3be4cb7d7cb6fc695c162fc0e91b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34260392"
---
# <a name="azure-hdinsight-modules-for-nodejs"></a><span data-ttu-id="e847c-103">Modules Azure HDInsight pour Node.js</span><span class="sxs-lookup"><span data-stu-id="e847c-103">Azure HDInsight Modules for Node.js</span></span>

<span data-ttu-id="e847c-104">Azure HDInsight est une distribution par cloud des composants Hadoop à partir de Hortonworks Data Platform (HDP).</span><span class="sxs-lookup"><span data-stu-id="e847c-104">Azure HDInsight is a cloud distribution of the Hadoop components from the Hortonworks Data Platform (HDP).</span></span> <span data-ttu-id="e847c-105">Apache Hadoop était l’infrastructure open source d’origine de traitement et d’analyse distribués des jeux de données volumineuses sur des clusters d’ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="e847c-105">Apache Hadoop was the original open-source framework for distributed processing and analysis of big data sets on clusters of computers.</span></span>

<span data-ttu-id="e847c-106">HDInsight rend les technologies Hadoop plus faciles à utiliser, avec :</span><span class="sxs-lookup"><span data-stu-id="e847c-106">HDInsight makes Hadoop technologies easier to use, with:</span></span>
- <span data-ttu-id="e847c-107">Moins de tâches d’installation et de configuration.</span><span class="sxs-lookup"><span data-stu-id="e847c-107">Less setup and configuration.</span></span> <span data-ttu-id="e847c-108">Consultez Approvisionnement de clusters dans HDInsight.</span><span class="sxs-lookup"><span data-stu-id="e847c-108">See Provision Hadoop clusters in HDInsight.</span></span>
- <span data-ttu-id="e847c-109">Haute disponibilité et fiabilité.</span><span class="sxs-lookup"><span data-stu-id="e847c-109">High availability and reliability.</span></span> <span data-ttu-id="e847c-110">Consultez Disponibilité et fiabilité de HDInsight.</span><span class="sxs-lookup"><span data-stu-id="e847c-110">See HDInsight availability and reliability.</span></span>
- <span data-ttu-id="e847c-111">Sécurité et gouvernance grâce à l’intégration avec Active Directory.</span><span class="sxs-lookup"><span data-stu-id="e847c-111">Security and governance through integration with Active Directory.</span></span> <span data-ttu-id="e847c-112">Consultez Clusters joints à un domaine.</span><span class="sxs-lookup"><span data-stu-id="e847c-112">See Domain-joined clusters.</span></span>
- <span data-ttu-id="e847c-113">Mise à l’échelle dynamique sans interrompre les travaux</span><span class="sxs-lookup"><span data-stu-id="e847c-113">Dynamic scaling without interrupting jobs</span></span>
- <span data-ttu-id="e847c-114">Mises à jour de composant et versions actuelles.</span><span class="sxs-lookup"><span data-stu-id="e847c-114">Component updates and current versions.</span></span> <span data-ttu-id="e847c-115">Consultez Composants et versions Hadoop sur HDInsight.</span><span class="sxs-lookup"><span data-stu-id="e847c-115">See Hadoop components and versions on HDInsight.</span></span>
- <span data-ttu-id="e847c-116">Intégration avec d’autres services Azure, notamment Web Apps et SQL Database</span><span class="sxs-lookup"><span data-stu-id="e847c-116">Integration with other Azure services, including Web apps and SQL Database</span></span>

<span data-ttu-id="e847c-117">La pile de technologies Hadoop inclut des logiciels et utilitaires liés, notamment Apache Hive, HBase, Spark, Kafka et bien d’autres encore.</span><span class="sxs-lookup"><span data-stu-id="e847c-117">The Hadoop technology stack includes related software and utilities, including Apache Hive, HBase, Spark, Kafka, and many others.</span></span> 

## <a name="management-package"></a><span data-ttu-id="e847c-118">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="e847c-118">Management package</span></span>

### <a name="install-the-npm-modules"></a><span data-ttu-id="e847c-119">Installer les modules npm</span><span class="sxs-lookup"><span data-stu-id="e847c-119">Install the npm modules</span></span>

<span data-ttu-id="e847c-120">Utiliser npm pour installer les modules Azure HDInsight pour Node.js</span><span class="sxs-lookup"><span data-stu-id="e847c-120">Use npm to install the Azure HDInsight modules for Node.js</span></span>

```bash
npm install azure-arm-hdinsight
```

```bash
azure-arm-hdinsight-jobs
```

### <a name="example"></a><span data-ttu-id="e847c-121">Exemples</span><span class="sxs-lookup"><span data-stu-id="e847c-121">Example</span></span> 

<span data-ttu-id="e847c-122">Cet exemple crée un client HD Insight et répertorie ensuite tous les clusters disponibles.</span><span class="sxs-lookup"><span data-stu-id="e847c-122">This example creates an HD Insight client and then lists all of the available clusters.</span></span> 

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

## <a name="samples"></a><span data-ttu-id="e847c-123">Exemples</span><span class="sxs-lookup"><span data-stu-id="e847c-123">Samples</span></span>

<span data-ttu-id="e847c-124">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="e847c-124">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
