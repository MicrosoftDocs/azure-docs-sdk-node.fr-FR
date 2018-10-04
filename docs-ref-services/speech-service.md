---
title: Kit de développement logiciel (SDK) Speech Cognitive Services pour JavaScript
description: Référence pour le Kit de développement logiciel (SDK) Speech Cognitive Services pour JavaScript
author: mahilleb-msft
ms.author: mahilleb
manager: wolfma
ms.date: 09/24/2018
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: cognitive-services
ms.component: speech-service
ms.openlocfilehash: 69167faa5b2677fc15561ed33beccf7925efbe39
ms.sourcegitcommit: 8f2555cd23e454ff79e27bd3ed0a6f65b08c1c9e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48458647"
---
# <a name="cognitive-services-speech-sdk-for-javascript"></a>Kit de développement logiciel (SDK) Speech Cognitive Services pour JavaScript

## <a name="overview"></a>Vue d’ensemble

Pour simplifier le développement d’applications pourvues d’une reconnaissance vocale, Microsoft fournit le [Kit de développement logiciel (SDK) Speech](https://aka.ms/csspeech) pour une utilisation avec le service de reconnaissance vocale.
Le Kit de développement logiciel (SDK) Speech fournit des API de reconnaissance vocale et de traduction vocale native cohérente.

> [!NOTE]
> Le Kit de développement logiciel (SDK) Speech Cognitive Services est actuellement disponible uniquement sur les navigateurs.
> Un package NPM suivra peu après.

### <a name="install-the-speech-sdk"></a>Installer le Kit de développement logiciel (SDK) Speech

Téléchargez le Kit de développement logiciel (SDK) Speech en tant que [package .zip](https://aka.ms/csspeech/jsbrowserpackage) et décompressez-le.
Cela devrait également décompresser un grand nombre de fichiers, y compris un fichier nommé `microsoft.cognitiveservices.speech.sdk.bundle.js`.
Chargez ce fichier comme une ressource de script dans votre page web pour commencer à utiliser le Kit de développement logiciel (SDK) Speech :

```html
<script src="microsoft.cognitiveservices.speech.sdk.bundle.js"></script>
```

### <a name="example"></a>Exemples 

Les extraits de code suivants illustrent comment effectuer une reconnaissance vocale simple à partir de votre navigateur :

```javascript 
var SpeechSDK = window.SpeechSDK;
var speechConfig = SpeechSDK.SpeechConfig.fromSubscription("your-subscription-key", "your-service-region");
speechConfig.language = "en-US";
var audioConfig = SpeechSDK.AudioConfig.fromDefaultMicrophoneInput();
recognizer = new SpeechSDK.SpeechRecognizer(speechConfig, audioConfig);

recognizer.recognizeOnceAsync(
  function (result) {
    alert("Recognition result:" + JSON.stringify(result));
    recognizer.close();
  },
  function (err) {
    alert("An error occurred:" + JSON.stringify(err));
    recognizer.close();
  }
);
``` 

Découvrez notre [Guide de démarrage rapide pas à pas](/azure/cognitive-services/speech-service/quickstart-js-browser).

## <a name="samples"></a>Exemples

Explorez d’autres exemples dans notre [Référentiel d’exemples de Kit de développement logiciel (SDK) Speech](https://aka.ms/csspeech/samples).
