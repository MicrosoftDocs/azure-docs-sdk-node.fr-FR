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
ms.sourcegitcommit: a748445fdd0dd7ead43d45fd4ad45009cfc439a6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/08/2018
ms.locfileid: "51134232"
---
# <a name="cognitive-services-speech-sdk-for-javascript"></a><span data-ttu-id="74558-103">Kit de développement logiciel (SDK) Speech Cognitive Services pour JavaScript</span><span class="sxs-lookup"><span data-stu-id="74558-103">Cognitive Services Speech SDK for JavaScript</span></span>

## <a name="overview"></a><span data-ttu-id="74558-104">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="74558-104">Overview</span></span>

<span data-ttu-id="74558-105">Pour simplifier le développement d’applications pourvues d’une reconnaissance vocale, Microsoft fournit le [Kit de développement logiciel (SDK) Speech](https://aka.ms/csspeech) pour une utilisation avec le service de reconnaissance vocale.</span><span class="sxs-lookup"><span data-stu-id="74558-105">To simplify the development of speech-enabled applications, Microsoft provides the Speech SDK for use with the [Speech service](https://aka.ms/csspeech).</span></span>
<span data-ttu-id="74558-106">Le Kit de développement logiciel (SDK) Speech fournit des API de reconnaissance vocale et de traduction vocale native cohérente.</span><span class="sxs-lookup"><span data-stu-id="74558-106">The Speech SDK provides consistent native Speech-to-Text and Speech Translation APIs.</span></span>

> [!NOTE]
> <span data-ttu-id="74558-107">Le Kit de développement logiciel (SDK) Speech Cognitive Services est actuellement disponible uniquement sur les navigateurs.</span><span class="sxs-lookup"><span data-stu-id="74558-107">The Cognitive Services Speech SDK is currently available only for browsers.</span></span>
> <span data-ttu-id="74558-108">Un package NPM suivra peu après.</span><span class="sxs-lookup"><span data-stu-id="74558-108">An NPM package will follow soon.</span></span>

### <a name="install-the-speech-sdk"></a><span data-ttu-id="74558-109">Installer le Kit de développement logiciel (SDK) Speech</span><span class="sxs-lookup"><span data-stu-id="74558-109">Install the Speech SDK</span></span>

<span data-ttu-id="74558-110">Téléchargez le Kit de développement logiciel (SDK) Speech en tant que [package .zip](https://aka.ms/csspeech/jsbrowserpackage) et décompressez-le.</span><span class="sxs-lookup"><span data-stu-id="74558-110">Download the Speech SDK as a [.zip package](https://aka.ms/csspeech/jsbrowserpackage) and unpack it.</span></span>
<span data-ttu-id="74558-111">Cela devrait également décompresser un grand nombre de fichiers, y compris un fichier nommé `microsoft.cognitiveservices.speech.sdk.bundle.js`.</span><span class="sxs-lookup"><span data-stu-id="74558-111">This should result in a number of files being unpacked including a file named `microsoft.cognitiveservices.speech.sdk.bundle.js`.</span></span>
<span data-ttu-id="74558-112">Chargez ce fichier comme une ressource de script dans votre page web pour commencer à utiliser le Kit de développement logiciel (SDK) Speech :</span><span class="sxs-lookup"><span data-stu-id="74558-112">Load this file as a script resource in your web page to start using the Speech SDK:</span></span>

```html
<script src="microsoft.cognitiveservices.speech.sdk.bundle.js"></script>
```

### <a name="example"></a><span data-ttu-id="74558-113">Exemples</span><span class="sxs-lookup"><span data-stu-id="74558-113">Example</span></span> 

<span data-ttu-id="74558-114">Les extraits de code suivants illustrent comment effectuer une reconnaissance vocale simple à partir de votre navigateur :</span><span class="sxs-lookup"><span data-stu-id="74558-114">The following code snippets illustrates how to do simple speech recognition from your browser:</span></span>

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

<span data-ttu-id="74558-115">Découvrez notre [Guide de démarrage rapide pas à pas](/azure/cognitive-services/speech-service/quickstart-js-browser).</span><span class="sxs-lookup"><span data-stu-id="74558-115">Check out our [step-by-step quickstart](/azure/cognitive-services/speech-service/quickstart-js-browser).</span></span>

## <a name="samples"></a><span data-ttu-id="74558-116">Exemples</span><span class="sxs-lookup"><span data-stu-id="74558-116">Samples</span></span>

<span data-ttu-id="74558-117">Explorez d’autres exemples dans notre [Référentiel d’exemples de Kit de développement logiciel (SDK) Speech](https://aka.ms/csspeech/samples).</span><span class="sxs-lookup"><span data-stu-id="74558-117">Explore more samples in our [Speech SDK sample repository](https://aka.ms/csspeech/samples).</span></span>
