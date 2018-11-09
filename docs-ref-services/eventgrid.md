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
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/08/2018
ms.locfileid: "51173121"
---
# <a name="azure-event-grid-libraries-for-nodejs"></a><span data-ttu-id="55a7c-103">Bibliothèques Azure Event Grid pour Node.js</span><span class="sxs-lookup"><span data-stu-id="55a7c-103">Azure Event Grid libraries for Node.js</span></span>

<span data-ttu-id="55a7c-104">Créez des applications pilotées par des événements, qui écoutent et réagissent aux événements venant des services Azure et de sources personnalisées à l’aide d’une gestion simple des événements basés sur HTTP avec Azure Event Grid.</span><span class="sxs-lookup"><span data-stu-id="55a7c-104">Build event-driven applications that listen and react to events from Azure services and custom sources using simple HTTP-based event handling with Azure Event Grid.</span></span>

<span data-ttu-id="55a7c-105">[En savoir plus](/azure/event-grid/overview) sur Azure Event Grid et la prise en main avec le [didacticiel des événements de stockage d’objets Blob Azure](/azure/storage/blobs/storage-blob-event-quickstart).</span><span class="sxs-lookup"><span data-stu-id="55a7c-105">[Learn more](/azure/event-grid/overview) about Azure Event Grid and get started with the [Azure Blob storage event tutorial](/azure/storage/blobs/storage-blob-event-quickstart).</span></span> 

## <a name="publish-sdk"></a><span data-ttu-id="55a7c-106">Kit de développement logiciel de publication</span><span class="sxs-lookup"><span data-stu-id="55a7c-106">Publish SDK</span></span>

<span data-ttu-id="55a7c-107">Créez des événements, authentifiez-vous et faites des publications dans des rubriques à l’aide du kit de développement logiciel de publication de Azure Event Grid.</span><span class="sxs-lookup"><span data-stu-id="55a7c-107">Create events, authenticate, and post to topics using the Azure Event Grid publish SDK.</span></span>

### <a name="installation"></a><span data-ttu-id="55a7c-108">Installation</span><span class="sxs-lookup"><span data-stu-id="55a7c-108">Installation</span></span>

<span data-ttu-id="55a7c-109">Ajoutez le module à votre projet avec npm :</span><span class="sxs-lookup"><span data-stu-id="55a7c-109">Add the module to your project with npm:</span></span>

```bash
npm install azure-eventgrid
```

### <a name="example-code"></a><span data-ttu-id="55a7c-110">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="55a7c-110">Example code</span></span>

<span data-ttu-id="55a7c-111">Le segment de code suivant publie un événement fictif dans une rubrique Event Grid.</span><span class="sxs-lookup"><span data-stu-id="55a7c-111">The following code segment publishes a mock event to a Event Grid topic.</span></span> <span data-ttu-id="55a7c-112">Vous pouvez récupérer les clés d’accès de point de terminaison et de la rubrique à partir du portail Azure ou via Azure CLI :</span><span class="sxs-lookup"><span data-stu-id="55a7c-112">You can retrieve the endpoint and topic access keys from the Azure Portal or through the Azure CLI:</span></span>

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

<span data-ttu-id="55a7c-113">Cet exemple montre comment gérer un événement depuis le stockage Azure :</span><span class="sxs-lookup"><span data-stu-id="55a7c-113">This sample shows how to handle an event from Azure Storage:</span></span>

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
> [<span data-ttu-id="55a7c-114">Explorer les API clientes</span><span class="sxs-lookup"><span data-stu-id="55a7c-114">Explore the client APIs</span></span>](/javascript/api/overview/azure/eventgrid/client)

## <a name="management-sdk"></a><span data-ttu-id="55a7c-115">Kit de développement logiciel (SDK) de gestion</span><span class="sxs-lookup"><span data-stu-id="55a7c-115">Management SDK</span></span>

<span data-ttu-id="55a7c-116">Créez, mettez à jour et supprimez des instances, des rubriques et des abonnements Event Grid avec le kit de développement logiciel de gestion.</span><span class="sxs-lookup"><span data-stu-id="55a7c-116">Create, update, or delete Event Grid instances, topics, and subscriptions with the management SDK.</span></span>

### <a name="installation"></a><span data-ttu-id="55a7c-117">Installation</span><span class="sxs-lookup"><span data-stu-id="55a7c-117">Installation</span></span>

```
npm install azure-arm-eventgrid
```

### <a name="example-code"></a><span data-ttu-id="55a7c-118">Exemple de code</span><span class="sxs-lookup"><span data-stu-id="55a7c-118">Example code</span></span>

<span data-ttu-id="55a7c-119">Le code suivant crée une rubrique Event Grid `topic1` et retourne les clés d’accès associées à la rubrique nouvellement créée.</span><span class="sxs-lookup"><span data-stu-id="55a7c-119">The following code creates an Event Grid topic `topic1` and returns the access keys associated with the newly created topic.</span></span>

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
> [<span data-ttu-id="55a7c-120">Explorer les API de gestion</span><span class="sxs-lookup"><span data-stu-id="55a7c-120">Explore the management APIs</span></span>](/javascript/api/overview/azure/eventgrid/management)

## <a name="learn-more"></a><span data-ttu-id="55a7c-121">En savoir plus</span><span class="sxs-lookup"><span data-stu-id="55a7c-121">Learn more</span></span>

- [<span data-ttu-id="55a7c-122">Recevoir des événements avec le kit de développement logiciel Event Grid</span><span class="sxs-lookup"><span data-stu-id="55a7c-122">Receive events using the Event Grid SDK</span></span>](/azure/event-grid/receive-events)
