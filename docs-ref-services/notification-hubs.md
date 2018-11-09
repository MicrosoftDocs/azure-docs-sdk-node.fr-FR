---
title: Modules Azure Notification Hubs pour Node.js
description: Références pour les modules Azure Notification Hubs pour Node.js
author: rloutlaw
ms.author: ROutlaw
manager: angrobe
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Notification Hubs
ms.openlocfilehash: 18eae632b41b71bc64b052852b677507da2678e9
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/08/2018
ms.locfileid: "51099028"
---
# <a name="azure-notification-hubs-modules-for-nodejs"></a><span data-ttu-id="29efe-103">Modules Azure Notification Hubs pour Node.js</span><span class="sxs-lookup"><span data-stu-id="29efe-103">Azure Notification Hubs modules for Node.js</span></span>

<span data-ttu-id="29efe-104">Azure Notification Hubs offre un moteur Push facile à utiliser, multi-plateforme et mis à l’échelle.</span><span class="sxs-lookup"><span data-stu-id="29efe-104">Azure Notification Hubs provide an easy-to-use, multi-platform, scaled-out push engine.</span></span> <span data-ttu-id="29efe-105">Avec un appel d’API multi-plateforme unique, vous pouvez aisément envoyer des notifications Push ciblées et personnalisées à n’importe quelle plateforme mobile à partir de n’importe quelle infrastructure cloud ou locale.</span><span class="sxs-lookup"><span data-stu-id="29efe-105">With a single cross-platform API call, you can easily send targeted and personalized push notifications to any mobile platform from any cloud or on-premises backend.</span></span>

<span data-ttu-id="29efe-106">Notification Hubs est parfaitement adapté lors de scénarios d’entreprise et de clients.</span><span class="sxs-lookup"><span data-stu-id="29efe-106">Notification Hubs works great for both enterprise and consumer scenarios.</span></span> <span data-ttu-id="29efe-107">Voici quelques exemples de clients utilisant Notification Hubs pour :</span><span class="sxs-lookup"><span data-stu-id="29efe-107">Here are a few examples customers use Notification Hubs for:</span></span>
- <span data-ttu-id="29efe-108">envoyer des notifications de dernières nouvelles à des millions de personnes avec une faible latence ;</span><span class="sxs-lookup"><span data-stu-id="29efe-108">Send breaking news notifications to millions with low latency.</span></span>
- <span data-ttu-id="29efe-109">envoyer des coupons basés sur la localisation aux segments d’utilisateurs intéressés ;</span><span class="sxs-lookup"><span data-stu-id="29efe-109">Send location-based coupons to interested user segments.</span></span>
- <span data-ttu-id="29efe-110">envoyer des notifications d’événements à des utilisateurs ou des groupes pour des applications de médias/sport/finance/jeux ;</span><span class="sxs-lookup"><span data-stu-id="29efe-110">Send event-related notifications to users or groups for media/sports/finance/gaming applications.</span></span>
- <span data-ttu-id="29efe-111">envoyer des notifications Push de contenu promotionnel vers les applications pour engager et toucher les clients ;</span><span class="sxs-lookup"><span data-stu-id="29efe-111">Push promotional contents to apps to engage and market to customers.</span></span>
- <span data-ttu-id="29efe-112">informer les utilisateurs d’événements d’entreprise tels que des nouveaux messages et des éléments de travail ;</span><span class="sxs-lookup"><span data-stu-id="29efe-112">Notify users of enterprise events like new messages and work items.</span></span>
- <span data-ttu-id="29efe-113">envoyer des codes pour l’authentification MFA.</span><span class="sxs-lookup"><span data-stu-id="29efe-113">Send codes for multi-factor authentication.</span></span>

## <a name="management-package"></a><span data-ttu-id="29efe-114">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="29efe-114">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="29efe-115">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="29efe-115">Install the npm module</span></span>

<span data-ttu-id="29efe-116">Installez le module Azure Notification Hubs</span><span class="sxs-lookup"><span data-stu-id="29efe-116">Install the Azure Notification Hubs module</span></span> 

```bash
npm install azure-arm-notificationhubs
```

### <a name="example"></a><span data-ttu-id="29efe-117">Exemples</span><span class="sxs-lookup"><span data-stu-id="29efe-117">Example</span></span>

<span data-ttu-id="29efe-118">Cet exemple répertorie tous les concentrateurs de notification.</span><span class="sxs-lookup"><span data-stu-id="29efe-118">This example lists all notification hubs.</span></span>

 ```javascript
const msRestAzure = require('ms-rest-azure');
const notificationHubsManagementClient = require('azure-arm-notificationhubs');

const subscriptionId = 'your-subscription-id';
const notificationHubNamespace = 'your-hub-namespace';
const resourceGroup = 'your-resource-group';
let notificationHubsClient;

msRestAzure.interactiveLogin().then(credentials => {
  notificationHubsClient = new notificationHubsManagementClient(credentials, subscriptionId);
  notificationHubsClient.notificationHubs
    .list(resourceGroup, notificationHubNamespace)
    .then(notificationHubs => console.log('Retrieved notification hubs: ', notificationHubs));
});
```

## <a name="samples"></a><span data-ttu-id="29efe-119">Exemples</span><span class="sxs-lookup"><span data-stu-id="29efe-119">Samples</span></span>

* [<span data-ttu-id="29efe-120">App Service Mobile a terminé le démarrage rapide du serveur principal Node.js</span><span class="sxs-lookup"><span data-stu-id="29efe-120">App Service Mobile completed quickstart for Node.js backend</span></span>](https://azure.microsoft.com/resources/samples/app-service-mobile-nodejs-backend-quickstart/)
* [<span data-ttu-id="29efe-121">Envoi de tweet en cas de détection d’une anomalie de vibration par les services Azure IoT sur des données venant d’un Intel Edison exécutant Node.js</span><span class="sxs-lookup"><span data-stu-id="29efe-121">Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js</span></span>](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)

<span data-ttu-id="29efe-122">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="29efe-122">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
