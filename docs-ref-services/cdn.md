---
title: Modules Azure CDN pour Node.js
description: "Références pour les modules Azure CDN pour Node.js"
keywords: Azure, SDK, API, CDN, Node.js
author: tomarcher
ms.author: tarcher
manager: douge
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: CDN
ms.openlocfilehash: ae44606510037fa3ba3d5b95196a40f8eeef3afe
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="azure-cdn-modules-for-nodejs"></a><span data-ttu-id="44168-104">Modules Azure CDN pour Node.js</span><span class="sxs-lookup"><span data-stu-id="44168-104">Azure CDN modules for Node.js</span></span>

## <a name="overview"></a><span data-ttu-id="44168-105">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="44168-105">Overview</span></span>

<span data-ttu-id="44168-106">Azure Content Delivery Network (CDN) offre aux développeurs une solution globale pour fournir du contenu de large bande passante hébergé dans Azure ou ailleurs.</span><span class="sxs-lookup"><span data-stu-id="44168-106">The Azure Content Delivery Network (CDN) offers developers a global solution for delivering high-bandwidth content that is hosted in Azure or any other location.</span></span> <span data-ttu-id="44168-107">Le réseau de diffusion de contenu (CDN) vous permet de mettre en cache des objets disponibles publiquement, chargés à partir d’un stockage d’objets blob Azure, d’une application web, d’une machine virtuelle, d’un dossier d’application ou d’un autre emplacement HTTP/HTTPS.</span><span class="sxs-lookup"><span data-stu-id="44168-107">Using the CDN, you can cache publicly available objects loaded from Azure blob storage, a web application, virtual machine, application folder, or other HTTP/HTTPS location.</span></span> <span data-ttu-id="44168-108">Le cache du CDN peut être maintenu dans des emplacements stratégiques afin d’offrir une bande passante maximale pour la distribution de contenu aux utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="44168-108">The CDN cache can be held at strategic locations to provide maximum bandwidth for delivering content to users.</span></span> <span data-ttu-id="44168-109">Le CDN est généralement utilisé pour distribuer du contenu statique tel que des images, des feuilles de style, des documents, des fichiers, des scripts côté client et des pages HTML.</span><span class="sxs-lookup"><span data-stu-id="44168-109">The CDN is typically used for delivering static content such as images, style sheets, documents, files, client-side scripts, and HTML pages.</span></span>

## <a name="management-package"></a><span data-ttu-id="44168-110">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="44168-110">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="44168-111">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="44168-111">Install the npm module</span></span>

<span data-ttu-id="44168-112">Installer le module npm Azure CDN</span><span class="sxs-lookup"><span data-stu-id="44168-112">Install the Azure CDN npm module</span></span>

```bash
npm install azure-arm-cdn
```

### <a name="example"></a><span data-ttu-id="44168-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="44168-113">Example</span></span>

<span data-ttu-id="44168-114">Cet exemple répertorie tous les profils CDN.</span><span class="sxs-lookup"><span data-stu-id="44168-114">This example lists all of the CDN profiles.</span></span>

```javascript
const msRestAzure = require('ms-rest-azure');
const cdnManagementClient = require('azure-arm-cdn');

const subscriptionId = 'your-subscription-id';

msRestAzure.interactiveLogin().then(credentials => {
  const cdnClient = new cdnManagementClient(credentials, subscriptionId);
  cdnClient.profiles
    .list()
    .then(profilesList => console.log('Retrieved profiles list: ', profilesList));
});
```

## <a name="samples"></a><span data-ttu-id="44168-115">Exemples</span><span class="sxs-lookup"><span data-stu-id="44168-115">Samples</span></span>

<span data-ttu-id="44168-116">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="44168-116">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
