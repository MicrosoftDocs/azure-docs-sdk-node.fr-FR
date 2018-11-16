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
ms.sourcegitcommit: b1e29342a19524f43ed70f4bc961dcfdacffb14a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51410413"
---
# <a name="azure-iot-hub-modules-for-nodejs"></a><span data-ttu-id="d091f-103">Modules Azure IoT Hub pour Node.js</span><span class="sxs-lookup"><span data-stu-id="d091f-103">Azure IoT Hub modules for Node.js</span></span>

<span data-ttu-id="d091f-104">Azure IoT Hub est un service entièrement géré qui permet des communications bidirectionnelles fiables et sécurisées entre des millions d’appareils IoT et un serveur principal de solution.</span><span class="sxs-lookup"><span data-stu-id="d091f-104">Azure IoT Hub is a fully managed service that enables reliable and secure bidirectional communications between millions of IoT devices and a solution back end.</span></span> <span data-ttu-id="d091f-105">Azure IoT Hub :</span><span class="sxs-lookup"><span data-stu-id="d091f-105">Azure IoT Hub:</span></span>
- <span data-ttu-id="d091f-106">Fournit plusieurs options de communication appareil vers cloud et cloud vers appareil, y compris la messagerie unidirectionnelle, le transfert de fichiers et les méthodes de demande-réponse.</span><span class="sxs-lookup"><span data-stu-id="d091f-106">Provides multiple device-to-cloud and cloud-to-device communication options, including one-way messaging, file transfer, and request-reply methods.</span></span>
- <span data-ttu-id="d091f-107">Intègre une fonctionnalité de routage des messages déclaratifs vers d’autres services Azure.</span><span class="sxs-lookup"><span data-stu-id="d091f-107">Provides built-in declarative message routing to other Azure services.</span></span>
- <span data-ttu-id="d091f-108">Fournit un stockage utilisable dans une requête pour les métadonnées d’appareil et les informations d’état synchronisées.</span><span class="sxs-lookup"><span data-stu-id="d091f-108">Provides a queryable store for device metadata and synchronized state information.</span></span>
- <span data-ttu-id="d091f-109">Assure la sécurité des communications et le contrôle d’accès grâce aux clés de sécurité par appareil ou aux certificats X.509.</span><span class="sxs-lookup"><span data-stu-id="d091f-109">Enables secure communications and access control using per-device security keys or X.509 certificates.</span></span>
- <span data-ttu-id="d091f-110">Fournit une surveillance complète de la connectivité des appareils et des événements de gestion de l’identité des appareils.</span><span class="sxs-lookup"><span data-stu-id="d091f-110">Provides extensive monitoring for device connectivity and device identity management events.</span></span>
- <span data-ttu-id="d091f-111">Inclut des bibliothèques d’appareils pour les langages et les plateformes les plus courants.</span><span class="sxs-lookup"><span data-stu-id="d091f-111">Includes device libraries for the most popular languages and platforms.</span></span>

<span data-ttu-id="d091f-112">Utiliser npm pour installer les modules Azure IoT Hub pour Node.js</span><span class="sxs-lookup"><span data-stu-id="d091f-112">Use npm to install the Azure IoT Hub modules for Node.js</span></span>

## <a name="management-package"></a><span data-ttu-id="d091f-113">Gestion des packages</span><span class="sxs-lookup"><span data-stu-id="d091f-113">Management Package</span></span>

### <a name="install-the-npm-module"></a><span data-ttu-id="d091f-114">Installer le module npm</span><span class="sxs-lookup"><span data-stu-id="d091f-114">Install the npm module</span></span>

<span data-ttu-id="d091f-115">Installer le module npm Azure IoT Hub</span><span class="sxs-lookup"><span data-stu-id="d091f-115">Install the Azure IoT Hub npm module</span></span>

```bash
npm install azure-arm-iothub
```

### <a name="example"></a><span data-ttu-id="d091f-116">Exemples</span><span class="sxs-lookup"><span data-stu-id="d091f-116">Example</span></span>

<span data-ttu-id="d091f-117">Cet exemple crée et nomme un IoT hub.</span><span class="sxs-lookup"><span data-stu-id="d091f-117">This example creates and names an IoT hub.</span></span>

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

<span data-ttu-id="d091f-118">Cet exemple obtient l’IoT hub existant, par nom.</span><span class="sxs-lookup"><span data-stu-id="d091f-118">This example gets the existing IoT hub, by name.</span></span>

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

## <a name="samples"></a><span data-ttu-id="d091f-119">Exemples</span><span class="sxs-lookup"><span data-stu-id="d091f-119">Samples</span></span>

- [<span data-ttu-id="d091f-120">Prendre en main le kit de démarrage Azure IoT pour Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="d091f-120">Get started with the Raspberry Pi Azure IoT Starter Kit</span></span>](https://azure.microsoft.com/resources/samples/iot-remote-monitoring-node-raspberrypi-getstartedkit/)
- [<span data-ttu-id="d091f-121">Envoi de tweet en cas de détection d’une anomalie de vibration par les services Azure IoT sur des données venant d’un Intel Edison exécutant Node.js</span><span class="sxs-lookup"><span data-stu-id="d091f-121">Tweet vibration anomalies detected by Azure IoT services on data from an Intel Edison running Node.js</span></span>](https://azure.microsoft.com/resources/samples/iot-hub-nodejs-intel-edison-vibration-anomaly-detection/)

<span data-ttu-id="d091f-122">Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="d091f-122">Explore more [sample Node.js code](https://azure.microsoft.com/resources/samples/?platform=nodejs) you can use in your apps.</span></span>
