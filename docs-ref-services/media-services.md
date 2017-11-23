---
title: Modules Azure Media Services pour Node.js
description: "Références pour les modules Azure Media Services pour Node.js"
keywords: Azure, SDK, API, Media Services, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Media Services
ms.openlocfilehash: 9b304ceb0c2d0580534ae1bee5a44d01fd4d8b33
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-media-services-modules-for-nodejs"></a><span data-ttu-id="26efe-104">Modules Azure Media Services pour Node.js</span><span class="sxs-lookup"><span data-stu-id="26efe-104">Azure Media Services modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="26efe-105">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="26efe-105">Overview</span></span>

<span data-ttu-id="26efe-106">Azure Media Services est une plateforme extensible basée sur le cloud qui permet aux développeurs de créer des applications évolutives de gestion et de diffusion de médias.</span><span class="sxs-lookup"><span data-stu-id="26efe-106">Azure Media Services is an extensible cloud-based platform that enables developers to build scalable media management and delivery applications.</span></span> <span data-ttu-id="26efe-107">Media Services est basé sur les API REST qui permettent de télécharger, stocker, encoder et empaqueter en toute sécurité du contenu vidéo ou audio destiné à être diffusé à la demande ou en direct sur différents clients (par exemple, téléviseurs, PC et appareils mobiles).</span><span class="sxs-lookup"><span data-stu-id="26efe-107">Media Services is based on REST APIs that enable you to securely upload, store, encode, and package video or audio content for both on-demand and live streaming delivery to various clients (for example, TV, PC, and mobile devices).</span></span>

<span data-ttu-id="26efe-108">Avec Azure Media Services, vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="26efe-108">With Azure Media Services, you can:</span></span>
- <span data-ttu-id="26efe-109">Créer des flux de travail de bout en bout en utilisant uniquement Media Services.</span><span class="sxs-lookup"><span data-stu-id="26efe-109">Build end-to-end workflows using entirely Media Services.</span></span> 
- <span data-ttu-id="26efe-110">Utiliser des composants tiers pour certaines parties de votre flux de travail.</span><span class="sxs-lookup"><span data-stu-id="26efe-110">Use third-party components for some parts of your workflow.</span></span> <span data-ttu-id="26efe-111">(par exemple, en encodant avec un encodeur tiers).</span><span class="sxs-lookup"><span data-stu-id="26efe-111">For example, encode using a third-party encoder.</span></span> <span data-ttu-id="26efe-112">Le contenu est ensuite téléchargé, protégé, empaqueté et remis à l'aide de Media Services.</span><span class="sxs-lookup"><span data-stu-id="26efe-112">Then, upload, protect, package, deliver using Media Services.</span></span>
- <span data-ttu-id="26efe-113">Diffuser votre contenu en direct ou de le distribuer à la demande.</span><span class="sxs-lookup"><span data-stu-id="26efe-113">Stream your content live or deliver content on-demand.</span></span> <span data-ttu-id="26efe-114">La rubrique contient également des liens vers d’autres rubriques pertinentes.</span><span class="sxs-lookup"><span data-stu-id="26efe-114">The topic also links to other relevant topics.</span></span>

## <a name="management-package"></a><span data-ttu-id="26efe-115">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="26efe-115">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="26efe-116">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="26efe-116">Install the npm module</span></span>

<span data-ttu-id="26efe-117">Installer le module npm Azure Media Services</span><span class="sxs-lookup"><span data-stu-id="26efe-117">Install the Azure media services npm module</span></span>

```bash
npm install azure-arm-mediaservices
```

### <a name="example"></a><span data-ttu-id="26efe-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="26efe-118">Example</span></span>

<span data-ttu-id="26efe-119">Cet exemple répertorie tous les media services pour un groupe de ressources donné.</span><span class="sxs-lookup"><span data-stu-id="26efe-119">This example lists all media services for a resource group.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const mediaServicesManagement = require('azure-arm-mediaservices');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
let mediaServicesClient;

msRestAzure.interactiveLogin().then(credentials => {
  mediaServicesClient = new mediaServicesManagement(credentials, subscriptionId);
  mediaServicesClient.mediaServiceOperations
    .listByResourceGroup(resourceGroup)
    .then(mediaServices => console.log('Retrieved media services: ', mediaServices));
});
```

## <a name="samples"></a><span data-ttu-id="26efe-120">Exemples</span><span class="sxs-lookup"><span data-stu-id="26efe-120">Samples</span></span>

<span data-ttu-id="26efe-121">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="26efe-121">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
