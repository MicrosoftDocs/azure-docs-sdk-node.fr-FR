---
title: Bibliothèques Azure Event Grid pour Node.js
description: Référence pour les bibliothèques Azure Event Grid pour Node.js
author: rloutlaw
ms.author: routlaw
manager: angerobe
ms.date: 05/03/2018
ms.topic: reference
ms.prod: ''
ms.technology: ''
ms.devlang: nodejs
ms.service: event-grid
ms.custom: devcenter
ms.openlocfilehash: bddf4efc1eda186aee92d30af24125823c7a8f7b
ms.sourcegitcommit: da60ea91d4215d738b1e0df82066f0fc337ad85a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2018
ms.locfileid: "47347134"
---
# <a name="azure-event-grid-libraries-for-nodejs"></a>Bibliothèques Azure Event Grid pour Node.js

Créez des applications pilotées par des événements, qui écoutent et réagissent aux événements venant des services Azure et de sources personnalisées à l’aide d’une gestion simple des événements basés sur HTTP avec Azure Event Grid.

[En savoir plus](/azure/event-grid/overview) sur Azure Event Grid et la prise en main avec le [didacticiel des événements de stockage d’objets Blob Azure](/azure/storage/blobs/storage-blob-event-quickstart). 

## <a name="publish-sdk"></a>Kit de développement logiciel de publication

Créez des événements, authentifiez-vous et faites des publications dans des rubriques à l’aide du kit de développement logiciel de publication de Azure Event Grid.

### <a name="installation"></a>Installation

Ajoutez le module à votre projet avec npm :

```bash
npm install azure-eventgrid
```

### <a name="example-code"></a>Exemple de code

Le segment de code suivant publie un événement fictif dans une rubrique Event Grid. Vous pouvez récupérer les clés d’accès de point de terminaison et de la rubrique à partir du portail Azure ou via Azure CLI :

```azurecli-interactive
endpoint=$(az eventgrid topic show --name <topic_name> -g gridResourceGroup --query "endpoint" --output tsv)
key=$(az eventgrid topic key list --name <topic_name> -g gridResourceGroup --query "key1" --output tsv)
```

```javascript
var EventGridClient = require("azure-eventgrid");
var msRestAzure = require('ms-rest-azure');
var uuid = require('uuid').v4;

let topicCreds = new msRestAzure.TopicCredentials('your-topic-key');
let EGClient = new EventGridClient(topicCreds, 'your-subscription-id');
let topicHostName = 'your-topic-endpoint';
let events = [
   {
   id: uuid(),
   subject: 'TestSubject',
   dataVersion: '1.0',
   eventType: 'Microsoft.MockPublisher.TestEvent',
   data: {
        field1: 'value1',
        filed2: 'value2'
        }
    }
];
return EGClient.publishEvents(topicHostName, events).then((result) => {
   return Promise.resolve(console.log('Published events successfully.'));
 }).catch((err) => {
  console.log('An error ocurred');
  console.dir(err, {depth: null, colors: true});
});
```

Cet exemple montre comment gérer un événement depuis le stockage Azure :

```javascript
var http = require('http');

module.exports = function (context, req) {
    context.log('JavaScript HTTP trigger function begun');
    var validationEventType = "Microsoft.EventGrid.SubscriptionValidationEvent";
    var storageBlobCreatedEvent = "Microsoft.Storage.BlobCreated";

    for (var events in req.body) {
        var body = req.body[events];
        // Deserialize the event data into the appropriate type based on event type  
        if (body.data && body.eventType == validationEventType) {
            context.log("Got SubscriptionValidation event data, validation code: " + body.data.validationCode + " topic: " + body.topic);

            // Do any additional validation (as required) and then return back the below response
            var code = body.data.validationCode;
            context.res = { status: 200, body: { "ValidationResponse": code } };
        }

        else if (body.data && body.eventType == storageBlobCreatedEvent) {
            var blobCreatedEventData = body.data;
            context.log("Relaying received blob created event payload:" + JSON.stringify(blobCreatedEventData));
        }
    }
    context.done();
};
```

> [!div class="nextstepaction"]
> [Explorer les API clientes](/javascript/api/overview/azure/eventgrid/client)

## <a name="management-sdk"></a>Kit de développement logiciel (SDK) de gestion

Créez, mettez à jour et supprimez des instances, des rubriques et des abonnements Event Grid avec le kit de développement logiciel de gestion.

### <a name="installation"></a>Installation

```
npm install azure-arm-eventgrid
```

### <a name="example-code"></a>Exemple de code

Le code suivant crée une rubrique Event Grid `topic1` et retourne les clés d’accès associées à la rubrique nouvellement créée.

```javascript
var msRestAzure = require('ms-rest-azure');
var EventGridManagementClient = require("azure-arm-eventgrid");

msRestAzure.interactiveLogin(function(err, credentials) {
    // Created the management client
    let EGMClient = new EventGridManagementClient(credentials, 'your-subscription-id');
    let topicResponse;
    // created an enventgrid topic
    return EGMClient.topics.createOrUpdate('resourceGroup', 'topic1', { location: 'westus' }).then((topicResponse) => {
        return Promise.resolve(console.log('Created topic ', topicResponse));
    }).then(() => {
        // listed the access keys
        return EGMClient.topics.listSharedAccessKeys('resourceGroup', 'topic1')}
)};
```

> [!div class="nextstepaction"]
> [Explorer les API de gestion](/javascript/api/overview/azure/eventgrid/management)

## <a name="learn-more"></a>En savoir plus

- [Recevoir des événements avec le kit de développement logiciel Event Grid](/azure/event-grid/receive-events)
