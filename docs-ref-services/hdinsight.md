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
# <a name="azure-hdinsight-modules-for-nodejs"></a>Modules Azure HDInsight pour Node.js

Azure HDInsight est une distribution par cloud des composants Hadoop à partir de Hortonworks Data Platform (HDP). Apache Hadoop était l’infrastructure open source d’origine de traitement et d’analyse distribués des jeux de données volumineuses sur des clusters d’ordinateurs.

HDInsight rend les technologies Hadoop plus faciles à utiliser, avec :
- Moins de tâches d’installation et de configuration. Consultez Approvisionnement de clusters dans HDInsight.
- Haute disponibilité et fiabilité. Consultez Disponibilité et fiabilité de HDInsight.
- Sécurité et gouvernance grâce à l’intégration avec Active Directory. Consultez Clusters joints à un domaine.
- Mise à l’échelle dynamique sans interrompre les travaux
- Mises à jour de composant et versions actuelles. Consultez Composants et versions Hadoop sur HDInsight.
- Intégration avec d’autres services Azure, notamment Web Apps et SQL Database

La pile de technologies Hadoop inclut des logiciels et utilitaires liés, notamment Apache Hive, HBase, Spark, Kafka et bien d’autres encore. 

## <a name="management-package"></a>Gestion des packages

### <a name="install-the-npm-modules"></a>Installer les modules npm

Utiliser npm pour installer les modules Azure HDInsight pour Node.js

```bash
npm install azure-arm-hdinsight
```

```bash
azure-arm-hdinsight-jobs
```

### <a name="example"></a>Exemples 

Cet exemple crée un client HD Insight et répertorie ensuite tous les clusters disponibles. 

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

## <a name="samples"></a>Exemples

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
