---
title: Modules Azure Cognitive Services pour Node.js
description: Références pour les modules Azure Cognitive Services pour Node.js
author: brapel
ms.author: v-brapel
manager: ehansen
ms.date: 07/18/2017
ms.topic: article
ms.prod: azure
ms.technology: azure
ms.devlang: nodejs
ms.service: Cognitive Services
ms.openlocfilehash: fb0319965f7ea9d1bcab25e0e213998052b78ae0
ms.sourcegitcommit: 8c6935b6591175798b8e37ad0e511864fad3478e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50272682"
---
# <a name="javascript-azure-cognitive-services-modules"></a>Modules Azure Cognitive Services pour Javascript

## <a name="vision-modules"></a>Modules de vision

### <a name="computer-vision"></a>Vision par ordinateur 

Retourne des informations sur le contenu visuel d’une image :

- Utilisez le marquage, les descriptions et les modèles propres au domaine pour identifier le contenu et le marquer en toute confiance.
- Appliquez des paramètres relatifs au contenu osé/pour adulte pour activer la restriction automatique du contenu réservé aux adultes.
- Identifiez les types d’image et de jeu de couleurs dans les images.

[Essayez Vision par ordinateur](https://azure.microsoft.com/services/cognitive-services/computer-vision/) gratuitement dans votre navigateur.

Obtenez le module JavaScript avec [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) :

```
npm install azure-cognitiveservices-computervision
```

[Obtenez plus d’informations](/azure/cognitive-services/computer-vision/home) sur l’API Vision par ordinateur et la prise en main avec le [démarrage rapide JavaScript API Vision par ordinateur](/azure/cognitive-services/computer-vision/quickstarts/javascript).

### <a name="content-moderator"></a>Content Moderator

Modération assistée par ordinateur de texte, de vidéo et d’images, à laquelle s’ajoutent des outils de vérification par un opérateur humain.

Obtenez le module JavaScript avec [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) :

```
npm install azure-cognitiveservices-contentmoderator
```

[En savoir plus](/azure/cognitive-services/content-moderator/overview) sur le service Content Moderator.

### <a name="face-api"></a>API Visage

Détectez, identifiez, analysez, organisez et balisez des visages sur des photos. 

[Essayez l’API Visage](https://azure.microsoft.com/services/cognitive-services/face/) dans votre navigateur.

Obtenez le module JavaScript avec [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) :

```
npm install azure-cognitiveservices-face
```

[En savoir plus](/azure/cognitive-services/face/overview) sur l’API Visage et la prise en main avec le [démarrage rapide JavaScript API Visage](/azure/cognitive-services/Face/quickstarts/javascript).

## <a name="search-modules"></a>Modules de recherche

### <a name="web-search"></a>Recherche Web

Récupérez des documents web indexés par l’API Recherche Web Bing et affinez les résultats par type, date et bien plus encore. 

[Essayez l’API Recherche Web](https://azure.microsoft.com/services/cognitive-services/bing-web-search-api/) dans votre navigateur.

Obtenez le module JavaScript avec [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) :

```
npm install azure-cognitiveservices-websearch
```

[En savoir plus](/azure/cognitive-services/bing-web-search/overview) sur l’API Recherche Web Bing et la prise en main avec le [démarrage rapide Node.js API Recherche Web Bing](/azure/cognitive-services/bing-web-search/quickstarts/nodejs).

### <a name="image-search"></a>Recherche d’images

Recherchez des images et obtenez des miniatures, des URL d’images complètes, des métadonnées d’images et bien plus encore dans vos résultats.

[Essayez l’API Recherche d’images Bing](https://azure.microsoft.com/services/cognitive-services/bing-image-search-api/) dans votre navigateur.

Obtenez le module JavaScript avec [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) :

```
npm install azure-cognitiveservices-imagesearch
```

[En savoir plus](/azure/cognitive-services/bing-image-search/overview) sur l’API Recherche Images Bing et la prise en main avec le [démarrage rapide Node.js API Recherche d’images Bing](/azure/cognitive-services/bing-image-search/quickstarts/nodejs).


### <a name="entity-search"></a>Recherche d’entité

Recherchez l’entité la plus pertinente (lieu, personne ou chose) pour un emplacement ou un terme de recherche donné.

[Essayez l’API Recherche d’entités Bing](https://azure.microsoft.com/services/cognitive-services/bing-entity-search-api/) dans votre navigateur.

Obtenez le module JavaScript avec [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) :

```
npm install azure-cognitiveservices-entitysearch
```

[En savoir plus](/azure/cognitive-services/bing-entities-search/search-the-web) sur l’API Recherche d’entités Bing et la prise en main avec le [démarrage rapide Node.js API Recherche d’entités Bing](/azure/cognitive-services/bing-entities-search/quickstarts/nodejs).

### <a name="custom-search"></a>Recherche personnalisée

Générez une recherche personnalisée sur le web qui répond à votre domaine de recherche spécifique.

Obtenez le module JavaScript avec [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) :

```
npm install azure-cognitiveservices-customsearch
```

[En savoir plus](/azure/cognitive-services/bing-custom-search/) sur le service Recherche personnalisée Bing et commencer à interroger votre recherche personnalisée à partir de vos applications avec le [démarrage rapide Node.js API Recherche personnalisée Bing](/azure/cognitive-services/bing-custom-search/call-endpoint-nodejs).

### <a name="video-search"></a>Recherche de vidéos

Recherchez des vidéos sur le web et obtenez des résultats comprenant les métadonnées d’auteur, d’encodage, de longueur et de nombre d’affichages.

[Essayez l’API Recherche de vidéos Bing](https://azure.microsoft.com/services/cognitive-services/bing-video-search-api/) dans votre navigateur.

Obtenez le module JavaScript avec [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) :

```
npm install azure-cognitiveservices-videosearch
```

[En savoir plus](/azure/cognitive-services/bing-video-search/search-the-web) sur le service Recherche de vidéos et la prise en main avec le [démarrage rapide Node.js API Recherche de vidéos Bing](/azure/cognitive-services/bing-video-search/nodejs).


### <a name="news-search"></a>Recherche Actualités

Recherchez sur le web des articles d’actualité et travaillez avec des métadonnées d’articles, d’informations liées, d’images et d’informations de fournisseur.

[Essayez l’API Recherche d’actualités Bing](https://azure.microsoft.com/services/cognitive-services/bing-news-search-api/) dans votre navigateur.

Obtenez le module JavaScript avec [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) :

```
npm install azure-cognitiveservices-newssearch
```

[En savoir plus](/azure/cognitive-services/bing-news-search/search-the-web) sur le service Recherche d’actualités Bing et la prise en main avec le [démarrage rapide Javascript API Recherche d’actualités Bing](/azure/cognitive-services/bing-news-search/nodejs).


## <a name="language-modules"></a>Modules linguistiques

### <a name="text-analytics"></a>Analyse de texte 

L’API Analyse de texte est un service informatique qui fournit un traitement en langage naturel sur le texte brut. L’API comprend trois fonctions principales :

- analyse de sentiments
- Extraction d’expressions clés
- Détection de la langue

[Essayez l’API Analyse de texte](https://azure.microsoft.com/services/cognitive-services/text-analytics/) dans votre navigateur.

Obtenez le module JavaScript avec [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) :

```
npm install azure-cognitiveservices-textanalytics
```

[En savoir plus](/azure/cognitive-services/text-analytics/overview) sur l’API Analyse de texte et la prise en main avec le [démarrage rapide Node.js API Analyse de texte](/azure/cognitive-services/text-analytics/quickstarts/nodejs).


### <a name="spell-check"></a>API Vérification orthographique

Utilisez la vérification orthographique et de grammaire contextuelle avec l’API Vérification orthographique Bing.

[Essayez l’API Vérification orthographique](https://azure.microsoft.com/services/cognitive-services/spell-check/) dans votre navigateur.

Obtenez le module JavaScript avec [npm](https://docs.npmjs.com/getting-started/installing-npm-packages-locally) :

```
npm install azure-cognitiveservices-spellcheck
```

[En savoir plus](/azure/cognitive-services/bing-spell-check/proof-text) sur l’API Vérification orthographique et la prise en main avec le [démarrage rapide Node.js API Vérification orthographique](/azure/cognitive-services/bing-spell-check/quickstarts/nodejs).

## <a name="samples"></a>Exemples

Découvrez d’autres [exemples de code Node.js](https://azure.microsoft.com/resources/samples/?platform=nodejs) à utiliser dans vos applications.
