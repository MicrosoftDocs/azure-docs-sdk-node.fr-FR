---
title: Modules Azure Notification Hubs pour Node.js
description: "Références pour les modules Azure Notification Hubs pour Node.js"
author: craigshoemaker
ms.author: cshoe
manager: routlaw
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Notification Hubs
ms.openlocfilehash: c353bdc0fff7784881b5cd4f1d3b4dda5268f1ea
ms.sourcegitcommit: 78001187db408d21909e949c8a592f76626c2c3b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2018
---
# <a name="azure-notification-hubs-modules-for-nodejs"></a>Modules Azure Notification Hubs pour Node.js

Azure Notification Hubs offre un moteur Push facile à utiliser, multi-plateforme et mis à l’échelle. Avec un appel d’API multi-plateforme unique, vous pouvez aisément envoyer des notifications Push ciblées et personnalisées à n’importe quelle plateforme mobile à partir de n’importe quelle infrastructure cloud ou locale.

Notification Hubs est parfaitement adapté lors de scénarios d’entreprise et de clients. Voici quelques exemples de clients utilisant Notification Hubs pour :
- envoyer des notifications de dernières nouvelles à des millions de personnes avec une faible latence ;
- envoyer des coupons basés sur la localisation aux segments d’utilisateurs intéressés ;
- envoyer des notifications d’événements à des utilisateurs ou des groupes pour des applications de médias/sport/finance/jeux ;
- envoyer des notifications Push de contenu promotionnel vers les applications pour engager et toucher les clients ;
- informer les utilisateurs d’événements d’entreprise tels que des nouveaux messages et des éléments de travail ;
- envoyer des codes pour l’authentification MFA.

## <a name="management-package"></a>Gestion des packages

### <a name="install-the-npm-module"></a>Installer le module npm

Installez le module Azure Notification Hubs 

```bash
npm install azure-arm-notificationhubs
```

### <a name="example"></a>exemples

Cet exemple répertorie tous les concentrateurs de notification.

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

## <a name="samples"></a>Exemples

* [App Service Mobile a terminé le démarrage rapide du serveur principal Node.js](https://azure.microsoft.com/resources/samples/app-service-mobile-nodejs-backend-quickstart/)
* [Envoi de tweet en cas de détection d’une anomalie de vibration par les services Azure IoT sur des données venant d’un Intel Edison exécutant Node.js](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
