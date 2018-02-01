---
title: Modules Azure App Service pour Node.js
description: "Références pour les modules Azure App Service pour Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: appservice
ms.openlocfilehash: b722344f056a52785aef6d853a797231dcafc699
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-app-service-modules-for-nodejs"></a>Modules Azure App Service pour Node.js

## <a name="overview"></a>Vue d'ensemble

Azure App Service est une offre PaaS (platform-as-a-service) de Microsoft Azure. Créez des applications web et mobiles adaptées à toutes les plateformes et appareils. Intégrez vos applications avec des solutions SaaS, connectez-vous à des applications locales et automatisez vos processus d’entreprise. Azure exécute vos applications sur des machines virtuelles entièrement gérées, avec les ressources de machines virtuelles partagées ou les machines virtuelles dédiées de votre choix.

App Service inclut les fonctionnalités web et mobiles que nous avons précédemment fournies séparément en tant que sites web Azure et services mobiles Azure. Il inclut également de nouvelles fonctionnalités d’automatisation des processus d’entreprise et d’hébergement d’API cloud. En tant que service intégré unique, App Service vous permet d’assembler différents éléments (sites web, serveurs principaux d’application mobile, API RESTful et processus d’entreprise) au sein d’une solution unique.

## <a name="management-package"></a>Gestion des packages

### <a name="install-the-npm-package"></a>Installer le package npm

Installer le module Azure App Service pour Node.js

```bash
npm install azure-arm-website
```

### <a name="example"></a>exemples

Cet exemple crée un site web sur Azure à l’aide de Node.js.

```javascript
const msRestAzure = require('ms-rest-azure');
const webSiteManagementClient = require('azure-arm-website');

const subscriptionId = 'your-subscription-id';
const website = 'website001';
const resourceGroup = 'your-resource-group';
const hostingPlan = 'testHostingPlan';
let webSiteClient;

msRestAzure.interactiveLogin().then(credentials => {
  webSiteClient = new webSiteManagementClient(credentials, subscriptionId);
  createWebSite(website).then(website => console.log('Web Site created successfully', website));
});

function createWebSite(webSiteName) {
  const parameters = { location: 'westus', serverFarmId: hostingPlan };
  console.log(`Creating web site:  ${webSiteName}`);
  return webSiteClient.webApps.createOrUpdate(resourceGroup, webSiteName, parameters, null);
}
```

## <a name="samples"></a>Exemples

[!INCLUDE [node-appservice-samples](../docs-ref-conceptual/includes/appservice-samples.md)]

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
