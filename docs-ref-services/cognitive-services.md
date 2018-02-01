---
title: Modules Azure Cognitive Services pour Node.js
description: "Références pour les modules Azure Cognitive Services pour Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cognitive Services
ms.openlocfilehash: df6ea913ca69341fbbb730b75f547ce9c10bd45f
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-cognitive-services-modules-for-nodejs"></a><span data-ttu-id="610f8-103">Modules Azure Cognitive Services pour Node.js</span><span class="sxs-lookup"><span data-stu-id="610f8-103">Azure Cognitive Services modules for Node.js</span></span>

<span data-ttu-id="610f8-104">Azure Cognitive Services est un ensemble d’API, de SDK et de services qui permettent aux développeurs de créer des applications plus intelligentes, attrayantes et exposées.</span><span class="sxs-lookup"><span data-stu-id="610f8-104">Azure Cognitive Services is a set of APIs, SDKs, and services available to developers to make their applications more intelligent, engaging and discoverable.</span></span> <span data-ttu-id="610f8-105">Microsoft Cognitive Services développe le portefeuille évolutif d’API de Machine Learning de Microsoft et permet aux développeurs d’ajouter facilement des fonctionnalités intelligentes telles que la détection d’émotion et vidéo, la reconnaissance faciale, vocale et de la vision ainsi que la compréhension vocale et du langage, dans leurs applications.</span><span class="sxs-lookup"><span data-stu-id="610f8-105">Microsoft Cognitive Services expands on Microsoft’s evolving portfolio of machine learning APIs and enables developers to easily add intelligent features – such as emotion and video detection; facial, speech and vision recognition; and speech and language understanding – into their applications.</span></span> <span data-ttu-id="610f8-106">Notre objectif est de proposer des expériences informatiques plus personnelles ainsi qu’une productivité assistée par des systèmes qui améliorent leurs capacités à voir, entendre, parler, comprendre et qui commencent même à raisonner.</span><span class="sxs-lookup"><span data-stu-id="610f8-106">Our vision is for more personal computing experiences and enhanced productivity aided by systems that increasingly can see, hear, speak, understand and even begin to reason.</span></span>

## <a name="management-package"></a><span data-ttu-id="610f8-107">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="610f8-107">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="610f8-108">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="610f8-108">Install the npm module</span></span>

<span data-ttu-id="610f8-109">Installer le module npm Azure Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="610f8-109">Install the Azure Cognitive Services npm module</span></span>

```bash
npm install azure-arm-cognitiveservices
```

### <a name="example"></a><span data-ttu-id="610f8-110">exemples</span><span class="sxs-lookup"><span data-stu-id="610f8-110">Example</span></span>

<span data-ttu-id="610f8-111">Cet exemple répertorie tous les comptes de service Cognitifs.</span><span class="sxs-lookup"><span data-stu-id="610f8-111">This example lists all cognitive service accounts.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const cognitiveServicesManagementClient = require('azure-arm-cognitiveservices');

const subscriptionId = 'your-subscription-id';

msRestAzure
  .interactiveLogin()
  .then(credentials => {
    const cognitiveServicesClient = new cognitiveServicesManagementClient(
      credentials,
      subscriptionId
    );
    return cognitiveServicesClient.cognitiveServicesAccounts.list();
  })
  .then(cognitiveServicesAccounts => {
    console.log('List of accounts:');
    console.dir(cognitiveServicesAccounts, { depth: null, colors: true });    
  });

```

## <a name="samples"></a><span data-ttu-id="610f8-112">Exemples</span><span class="sxs-lookup"><span data-stu-id="610f8-112">Samples</span></span>

<span data-ttu-id="610f8-113">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="610f8-113">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
