---
title: Modules Azure IoT Hub pour Node.js
description: Références pour les modules Azure IoT Hub pour Node.js
author: dominicbetts
ms.author: dobett
manager: timlt
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: IoT Hub
ms.openlocfilehash: 1f83e016023722f149384ac015726e9257a9f3af
ms.sourcegitcommit: efa2d98deffe8a0d41a8d63f9f07aa720862e6ab
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2018
ms.locfileid: "52151324"
---
# <a name="azure-iot-hub-modules-for-nodejs"></a>Modules Azure IoT Hub pour Node.js

Azure IoT Hub est un service entièrement géré qui permet des communications bidirectionnelles fiables et sécurisées entre des millions d’appareils IoT et un serveur principal de solution. Azure IoT Hub :
- Fournit plusieurs options de communication appareil vers cloud et cloud vers appareil, y compris la messagerie unidirectionnelle, le transfert de fichiers et les méthodes de demande-réponse.
- Intègre une fonctionnalité de routage des messages déclaratifs vers d’autres services Azure.
- Fournit un stockage utilisable dans une requête pour les métadonnées d’appareil et les informations d’état synchronisées.
- Assure la sécurité des communications et le contrôle d’accès grâce aux clés de sécurité par appareil ou aux certificats X.509.
- Fournit une surveillance complète de la connectivité des appareils et des événements de gestion de l’identité des appareils.
- Inclut des bibliothèques d’appareils pour les langages et les plateformes les plus courants.

Utiliser npm pour installer les modules Azure IoT Hub pour Node.js

## <a name="management-package"></a>Gestion des packages

### <a name="install-the-npm-module"></a>Installer le module npm

Installer le module npm Azure IoT Hub

```bash
npm install azure-arm-iothub
```

### <a name="example"></a>Exemples

Cet exemple crée et nomme un IoT hub.

```javascript
const msRestAzure = require('ms-rest-azure');
const IoTHubClient = require('azure-arm-iothub');

const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const hubName = 'your-hub';
const location = 'East US';

// Describe the IoT hub you want to create
const hubDescription = {
  name: hubName,
  location: location,
  subscriptionid: subscriptionId,
  resourcegroup: resourceGroup,
  sku: { name: 'S1', capacity: 2 },
  properties: {
    enableFileUploadNotifications: false,
    ipFilterRules: [{ filterName: 'ipfilterrule', action: 'accept', ipMask: '0.0.0.0/0' }],
    operationsMonitoringProperties: {
      events: {
        C2DCommands: 'Error',
        DeviceTelemetry: 'Error',
        DeviceIdentityOperations: 'Error',
        Connections: 'Error, Information'
      }
    },
    features: 'None'
  }
};

msRestAzure.interactiveLogin().then(credentials => {
  const client = new IoTHubClient(credentials, subscriptionId);

  client.iotHubResource
    .createOrUpdate(resourceGroup, hubName, hubDescription)
    .then(hubDescriptionResult => console.log(hubDescriptionResult))
    .catch(err => console.error(err));
});
```

Cet exemple obtient l’IoT hub existant, par nom.

```javascript
const subscriptionId = 'your-subscription-id';
const resourceGroup = 'your-resource-group';
const hubName = 'your-hub';

msRestAzure.interactiveLogin().then(credentials => {
  const client = new IoTHubClient(credentials, subscriptionId);

  client.iotHubResource
    .get(resourceGroup, hubName)
    .then(hubDescriptionResult => console.log(hubDescriptionResult))
    .catch(err => console.error(err));
});
```

## <a name="samples"></a>Exemples

- [Prendre en main le kit de démarrage Azure IoT pour Raspberry Pi](https://azure.microsoft.com/resources/samples/iot-remote-monitoring-node-raspberrypi-getstartedkit/)
- [Envoi de tweet en cas de détection d’une anomalie de vibration par les services Azure IoT sur des données venant d’un Intel Edison exécutant Node.js](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
