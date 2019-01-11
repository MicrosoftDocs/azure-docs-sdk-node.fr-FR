---
title: Kit de développement logiciel (SDK) Speech Cognitive Services pour JavaScript
description: Référence pour le Kit de développement logiciel (SDK) Speech Cognitive Services pour JavaScript
author: mahilleb-msft
ms.author: mahilleb
manager: wolfma
ms.date: 12/18/2018
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: cognitive-services
ms.component: speech-service
ms.openlocfilehash: 43a6921d4ec782287cc041ecaabab4567b0fe677
ms.sourcegitcommit: 74417c10aee8987c3e0343728efac75823c902d9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2019
ms.locfileid: "54185986"
---
# <a name="cognitive-services-speech-sdk-for-javascript"></a>Kit de développement logiciel (SDK) Speech Cognitive Services pour JavaScript

## <a name="overview"></a>Vue d’ensemble

Pour simplifier le développement d’applications pourvues d’une reconnaissance vocale, Microsoft fournit le [Kit de développement logiciel (SDK) Speech](https://aka.ms/csspeech) pour une utilisation avec le service de reconnaissance vocale.
Le Kit de développement logiciel (SDK) Speech fournit des API de reconnaissance vocale et de traduction vocale native cohérente.

### <a name="install-the-npm-module"></a>Installer le module npm

Installer le module npm du SDK Speech de Cognitive Services

```bash
npm install microsoft-cognitiveservices-speech-sdk
```

### <a name="example"></a>Exemples 

Les extraits de code suivants illustrent comment effectuer une reconnaissance vocale simple à partir d’un fichier :

```javascript 
// Pull in the required packages.
var sdk = require("microsoft-cognitiveservices-speech-sdk");
var fs = require("fs");

// Replace with your own subscription key, service region (e.g., "westus"), and
// the name of the file you want to run through the speech recognizer.
var subscriptionKey = "YourSubscriptionKey";
var serviceRegion = "YourServiceRegion"; // e.g., "westus"
var filename = "YourAudioFile.wav"; // 16000 Hz, Mono

// Create the push stream we need for the speech sdk.
var pushStream = sdk.AudioInputStream.createPushStream();

// Open the file and push it to the push stream.
fs.createReadStream(filename).on('data', function(arrayBuffer) {
  pushStream.write(arrayBuffer.buffer);
}).on('end', function() {
  pushStream.close();
});

// We are done with the setup
console.log("Now recognizing from: " + filename);

// Create the audio-config pointing to our stream and
// the speech config specifying the language.
var audioConfig = sdk.AudioConfig.fromStreamInput(pushStream);
var speechConfig = sdk.SpeechConfig.fromSubscription(subscriptionKey, serviceRegion);

// Setting the recognition language to English.
speechConfig.speechRecognitionLanguage = "en-US";

// Create the speech recognizer.
var recognizer = new sdk.SpeechRecognizer(speechConfig, audioConfig);

// Start the recognizer and wait for a result.
recognizer.recognizeOnceAsync(
  function (result) {
    console.log(result);

    recognizer.close();
    recognizer = undefined;
  },
  function (err) {
    console.trace("err - " + err);

    recognizer.close();
    recognizer = undefined;
  });
``` 

Découvrez notre [Guide de démarrage rapide pas à pas](/azure/cognitive-services/speech-service/quickstart-js-node).

## <a name="samples"></a>Exemples

* [Démarrage rapide pas à pas pour Node.js](/azure/cognitive-services/speech-service/quickstart-js-node).
* [Démarrage rapide pas à pas pour le navigateur](/azure/cognitive-services/speech-service/quickstart-js-browser).
* Retrouvez d’autres exemples dans notre [dépôt d’exemples du SDK Speech](https://aka.ms/csspeech/samples).
