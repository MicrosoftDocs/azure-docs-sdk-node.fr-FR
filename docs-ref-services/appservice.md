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
# <a name="azure-app-service-modules-for-nodejs"></a><span data-ttu-id="2c3ad-103">Modules Azure App Service pour Node.js</span><span class="sxs-lookup"><span data-stu-id="2c3ad-103">Azure App Service modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="2c3ad-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="2c3ad-104">Overview</span></span>

<span data-ttu-id="2c3ad-105">Azure App Service est une offre PaaS (platform-as-a-service) de Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="2c3ad-105">Azure App Service is a platform-as-a-service (PaaS) offering of Microsoft Azure.</span></span> <span data-ttu-id="2c3ad-106">Créez des applications web et mobiles adaptées à toutes les plateformes et appareils.</span><span class="sxs-lookup"><span data-stu-id="2c3ad-106">Create web and mobile apps for any platform or device.</span></span> <span data-ttu-id="2c3ad-107">Intégrez vos applications avec des solutions SaaS, connectez-vous à des applications locales et automatisez vos processus d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="2c3ad-107">Integrate your apps with SaaS solutions, connect with on-premises applications, and automate your business processes.</span></span> <span data-ttu-id="2c3ad-108">Azure exécute vos applications sur des machines virtuelles entièrement gérées, avec les ressources de machines virtuelles partagées ou les machines virtuelles dédiées de votre choix.</span><span class="sxs-lookup"><span data-stu-id="2c3ad-108">Azure runs your apps on fully managed virtual machines (VMs), with your choice of shared VM resources or dedicated VMs.</span></span>

<span data-ttu-id="2c3ad-109">App Service inclut les fonctionnalités web et mobiles que nous avons précédemment fournies séparément en tant que sites web Azure et services mobiles Azure.</span><span class="sxs-lookup"><span data-stu-id="2c3ad-109">App Service includes the web and mobile capabilities that we previously delivered separately as Azure Websites and Azure Mobile Services.</span></span> <span data-ttu-id="2c3ad-110">Il inclut également de nouvelles fonctionnalités d’automatisation des processus d’entreprise et d’hébergement d’API cloud.</span><span class="sxs-lookup"><span data-stu-id="2c3ad-110">It also includes new capabilities for automating business processes and hosting cloud APIs.</span></span> <span data-ttu-id="2c3ad-111">En tant que service intégré unique, App Service vous permet d’assembler différents éléments (sites web, serveurs principaux d’application mobile, API RESTful et processus d’entreprise) au sein d’une solution unique.</span><span class="sxs-lookup"><span data-stu-id="2c3ad-111">As a single integrated service, App Service lets you compose various components -- websites, mobile app back ends, RESTful APIs, and business processes -- into a single solution.</span></span>

## <a name="management-package"></a><span data-ttu-id="2c3ad-112">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="2c3ad-112">Management Package</span></span>

### <a name="install-the-npm-package"></a><span data-ttu-id="2c3ad-113">Installer le package npm</span><span class="sxs-lookup"><span data-stu-id="2c3ad-113">Install the npm package</span></span>

<span data-ttu-id="2c3ad-114">Installer le module Azure App Service pour Node.js</span><span class="sxs-lookup"><span data-stu-id="2c3ad-114">Install the Azure App Service module for Node.js</span></span>

```bash
npm install azure-arm-website
```

### <a name="example"></a><span data-ttu-id="2c3ad-115">exemples</span><span class="sxs-lookup"><span data-stu-id="2c3ad-115">Example</span></span>

<span data-ttu-id="2c3ad-116">Cet exemple crée un site web sur Azure à l’aide de Node.js.</span><span class="sxs-lookup"><span data-stu-id="2c3ad-116">This example creates a website on Azure using Node.js.</span></span>

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

## <a name="samples"></a><span data-ttu-id="2c3ad-117">Exemples</span><span class="sxs-lookup"><span data-stu-id="2c3ad-117">Samples</span></span>

[!INCLUDE [node-appservice-samples](../docs-ref-conceptual/includes/appservice-samples.md)]

<span data-ttu-id="2c3ad-118">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="2c3ad-118">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
