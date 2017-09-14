---
title: "Développement Node.js avec Visual Studio Code et Azure"
description: "Didacticiel complet décrivant la procédure à suivre pour créer, dockeriser et déployer une application Node.js dans Azure"
services: multiple
author: tomarcher
manager: douge
ms.service: azure-nodejs
ms.tgt_pltfrm: na
ms.devlang: nodejs
ms.topic: article
ms.date: 06/25/2017
ms.author: joncart
ms.openlocfilehash: 1b43502394b7224c5791ee870999cdb958a0969d
ms.sourcegitcommit: 9974b43899e98df10253738dab5b09b484ac1bf5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2017
---
# <a name="nodejs-development-with-visual-studio-code-and-azure"></a>Développement Node.js avec Visual Studio Code et Azure

Ce didacticiel explique comment « conteneuriser » une application Node.js existante (avec Docker) et comment la déployer dans Azure à l’aide de Visual Studio Code.

Il utilise une simple application de tâches créée et publiée par [Scotch.io](https://scotch.io/tutorials/creating-a-single-page-todo-app-with-node-and-angular). Cette application MEAN ne comporte qu’une seule page et, par conséquent, utilise MongoDB comme base de données, Node/Express comme API REST/serveur web et Angular.js 1.x comme interface utilisateur frontale. 

## <a name="prerequisites"></a>Composants requis

Pour suivre la démonstration, vous devez avoir installé les logiciels suivants :

- [Visual Studio Code](https://code.visualstudio.com/)
- [Docker](https://www.docker.com/products/docker)
- [Compte DockerHub](https://hub.docker.com/)
- [Azure CLI 2.0](https://docs.microsoft.com/cli/azure/install-az-cli2)
- [Compte Azure](https://azure.microsoft.com/free/)
- [Yarn](https://yarnpkg.com/en/docs/install)
- [Chrome](https://www.google.com/chrome/browser/desktop/) : utilisé pour le débogage du code frontal de l’application de démonstration.
- MongoDB : étant donné que l’application de démonstration utilise MongoDB, vous devez disposer d’une instance MongoDB exécutée en local qui écoute sur le port `27017` standard. La façon la plus simple d’effectuer cette opération consiste à exécuter les deux commandes suivantes après l’installation de Docker : `docker pull mongo`, puis `docker run -it -p 27017:27017 mongo`.

## <a name="project-setup"></a>Configuration du projet

Pour commencer, téléchargez l’exemple de projet en procédant comme suit :

1. Ouvrez Visual Studio Code.

1. Appuyez sur **&lt;F1>** pour afficher la palette de commandes.

1. À l’invite de la palette de commandes, entrez `gitcl`, sélectionnez la commande **Git: Clone**, puis appuyez sur **&lt;Entrée>**.

    ![commande gitcl dans l’invite de la palette de commandes de Visual Studio Code](./media/node-howto-e2e/git-clone.png)

1. Lorsque vous êtes invité à saisir **l’URL du référentiel**, entrez `https://github.com/scotch-io/node-todo`, puis appuyez sur **&lt;Entrée>**.

1. Sélectionnez (ou créez) le répertoire local dans lequel vous souhaitez cloner le projet.

    ![Explorateur Visual Studio Code](./media/node-howto-e2e/explorer.png)

## <a name="integrated-terminal"></a>Terminal intégré

Dans la mesure où il s’agit d’un projet Node.js, la première chose à faire est de s’assurer que toutes les dépendances du projet sont installées à partir de npm.  

1. Appuyez sur **&lt;Ctrl>`** pour afficher le terminal intégré de Visual Studio Code. 

1. Tapez `yarn`, puis appuyez sur **&lt;Entrée>**.  

    ![Exécution de la commande yarn dans Visual Studio Code](./media/node-howto-e2e/terminal.png)

## <a name="integrated-git-version-control"></a>Contrôle de version Git intégré

Un fichier `yarn.lock` est créé une fois les dépendances de l’application installées via Yarn. Ce fichier offre un moyen prévisible de réacquérir précisément les mêmes dépendances, sans la moindre surprise dans les builds CI (intégration continue), les déploiements de production ou d’autres ordinateurs de développement.

Les étapes suivantes expliquent comment vérifier le fichier `yarn.lock` dans le contrôle de code source :

1. Dans Visual Studio Code, basculez vers l’onglet Git intégré (l’onglet avec le logo Git).

1. Dans la zone **Message**, entrez un message de validation, puis appuyez sur **&lt;Ctrl>&lt;Entrée>**. 

    ![Ajout du fichier yarn.lock à Git](./media/node-howto-e2e/git.png)

## <a name="project-and-code-navigation"></a>Navigation dans le projet et le code

Pour nous orienter dans la base de code, voyons ensemble quelques exemples de fonctionnalités de navigation offertes par Visual Studio Code.

1. Appuyez sur **&lt;Ctrl> P**.

1. Entrez `.js` pour afficher tous les fichiers JSON/JavaScript du projet, ainsi que le répertoire parent de chaque fichier. 

    ![Affichage de tous les fichiers .js*](./media/node-howto-e2e/git-output.png)

1. Sélectionnez `server.js`, à savoir le script de démarrage de l’application. 

1. Pointez votre souris sur la variable **database** (importée sur la ligne 6) pour en déterminer le type. Cette fonction qui permet d’inspecter rapidement les variables/modules/types au sein d’un fichier est extrêmement utile lors du développement de vos projets. 

    ![Détection du type](./media/node-howto-e2e/hover-help.png)

1. En cliquant dans l’étendue d’une variable (**database**, par exemple), vous pouvez visualiser toutes les références à cette variable dans le même fichier. Pour afficher toutes les références à une variable dans le projet, cliquez avec le bouton droit sur la variable puis, dans le menu contextuel, sélectionnez **Rechercher toutes les références**.

    ![Rechercher les références à une variable](./media/node-howto-e2e/word-hilight.png)

1. Outre la possibilité de pointer le curseur de la souris sur une variable pour en découvrir le type, vous pouvez également inspecter la définition d’une variable, même si elle se trouve dans un autre fichier. Pour voir cette fonctionnalité en action, cliquez avec le bouton droit sur **database.localUrl** (ligne 12) et, dans le menu contextuel, sélectionnez **Aperçu de la définition**. 

    ![Aperçu de la définition d’une variable](./media/node-howto-e2e/code-peek.png)

## <a name="modifying-the-code-and-using-autocompletion"></a>Modification du code et utilisation de la saisie semi-automatique

La chaîne de connexion MongoDB est codée en dur dans la déclaration de **database.localUrl**. Dans cette section, vous allez modifier le code pour récupérer la chaîne de connexion à partir d’une variable d’environnement et en savoir plus sur la fonctionnalité de saisie semi-automatique de Visual Studio Code.  

1. Ouvrez le fichier `server.js`.

1. Remplacez le code suivant : 

    ```javascript
    mongoose.connect(database.localUrl);
    ```

    par ce code :

    ```javascript
    mongoose.connect(process.env.MONGODB_URL || database.localUrl);
    ```

Notez que si vous saisissez le code manuellement (au lieu d’effectuer un copier-coller), lorsque vous tapez le point après `process`, Visual Studio Code affiche les membres disponibles de l’API globale **process** de Node.js.

![La saisie semi-automatique affiche automatiquement les membres d’une API](./media/node-howto-e2e/process-env.png)

La saisie semi-automatique fonctionne grâce à l’utilisation en arrière-plan de TypeScript (même pour JavaScript), qui permet d’obtenir des informations de type qui peuvent ensuite être utilisées pour informer la liste de saisie semi-automatique au fil de la saisie. Visual Studio Code est en mesure de détecter qu’il s’agit d’un projet Node.js et donc de télécharger automatiquement le fichier de typages TypeScript pour [Node.js à partir de NPM](https://www.npmjs.com/package/@types/node). Le fichier de typages vous permet d’obtenir une saisie semi-automatique pour les autres fonctions globales Node.js, telles que **Buffer** et **setTimeout**, ainsi que pour tous les modules intégrés comme **fs** et **http**.

Outre les API Node.js intégrées, cette acquisition automatique des typages fonctionne également pour plus de 2 000 modules tiers, tels que React, Underscore et Express. Par exemple, pour empêcher Mongoose de bloquer l’exemple d’application en cas de problème de connexion à l’instance de base de données MongoDB configurée, insérez la ligne de code suivante à la ligne 13 :

```javascript
mongoose.connection.on("error", () => { console.log("DB connection error"); });
```

Comme avec le code précédent, vous remarquerez que vous obtenez une saisie semi-automatique sans la moindre intervention de votre part.

![La saisie semi-automatique affiche automatiquement les membres d’une API](./media/node-howto-e2e/mongoose.png)

Vous pouvez voir les modules qui prennent en charge cette fonctionnalité de saisie semi-automatique en parcourant le projet [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped), qui est la source communautaire de toutes les définitions de type TypeScript.

## <a name="running-the-app"></a>Exécution de l'application

Maintenant que vous avez un peu exploré le code, le moment est venu d’exécuter l’application. Pour exécuter l’application à partir de Visual Studio Code, appuyez sur **&lt;F5>**. Lors de l’exécution du code via **&lt;F5>** (mode de débogage), Visual Studio Code lance l’application et ouvre la fenêtre **Console de débogage** qui affiche le pointeur stdout de l’application.

![Analyse du stdout d’une application via la console de débogage](./media/node-howto-e2e/console.png)

En outre, la **Console de débogage** est attachée à la nouvelle application en cours d’exécution, ce qui vous permet d’entrer des expressions JavaScript qui seront évaluées dans l’application. Elle inclut également la saisie semi-automatique. Pour voir ceci en action, tapez `process.env` dans la console :

![Saisie du code dans la console de débogage](./media/node-howto-e2e/console-code.png)

Vous avez pu exécuter l’application en appuyant sur **&lt;F5>** car le fichier actuellement ouvert est un fichier JavaScript (`server.js`). Par conséquent, Visual Studio Code suppose que le projet est une application Node.js. Si vous fermez tous les fichiers JavaScript dans Visual Studio Code et si vous appuyez ensuite sur **&lt;F5>**, Visual Studio Code vous interrogera sur l’environnement :

![Spécification de l’environnement runtime](./media/node-howto-e2e/select-env.png)

Ouvrez un navigateur et accédez à `http://localhost:8080` pour voir l’application en cours d’exécution. Tapez un message dans la zone de texte et ajoutez/supprimez quelques tâches pour avoir une idée du fonctionnement de l’application.

![Application de tâches en cours d’exécution](./media/node-howto-e2e/todo.png)

## <a name="debugging"></a>Débogage

En plus de la possibilité d’exécuter l’application et d’interagir avec elle via la console intégrée, Visual Studio Code vous permet de définir des points d’arrêt directement dans votre code. Par exemple, appuyez sur **&lt;Ctrl>P** pour afficher le sélecteur de fichiers. Une fois que le sélecteur de fichier s’affiche, tapez `route`, puis sélectionnez le fichier `route.js`.

Définissez un point d’arrêt sur la ligne 28, qui représente l’itinéraire Express qui est appelé lorsque l’application tente d’ajouter une entrée de tâche. Pour définir un point d’arrêt, cliquez simplement sur la zone à gauche du numéro de ligne dans l’éditeur, comme indiqué dans l’illustration suivante.

![Définition d’un point d’arrêt dans Visual Studio Code](./media/node-howto-e2e/breakpoint.png)

> [!NOTE]
> En plus des points d’arrêt standard, Visual Studio Code prend en charge des points d’arrêt conditionnels qui vous permettent de personnaliser le moment où l’application doit suspendre son exécution. Pour définir un point d’arrêt conditionnel, cliquez sur la zone à gauche de la ligne sur laquelle vous souhaitez interrompre l’exécution, sélectionnez **Ajouter un point d’arrêt conditionnel...** et spécifiez soit une expression JavaScript (par exemple, `foo = "bar"`) soit le nombre d’exécutions qui définit la condition sous laquelle vous voulez interrompre l’exécution.
> 
> 

Une fois le point d’arrêt défini, retournez à l’application en cours d’exécution et ajoutez une entrée de tâche. L’ajout d’une entrée de tâche provoque immédiatement la suspension de l’exécution de l’application sur la ligne 28 où vous avez défini le point d’arrêt :

![Interruption de l’exécution sur un point d’arrêt par Visual Studio Code](./media/node-howto-e2e/debugger.png)

Une fois l’application suspendue, vous pouvez pointer votre souris sur les expressions du code pour afficher leur valeur actuelle, inspecter les variables locales/espions et la pile des appels, et utiliser la barre d’outils de débogage pour naviguer dans l’exécution du code. Appuyez sur **&lt;F5>** pour reprendre l’exécution de l’application.

## <a name="full-stack-debugging"></a>Débogage de la pile complète

Comme mentionné précédemment dans la rubrique, l’application de tâches est une application MEAN, ce qui signifie que ses codes frontaux et principaux sont écrits à l’aide de JavaScript. Ainsi, pendant que vous déboguez le code (Node/Express) principal, vous devrez peut-être à un moment donné déboguer le code (Angular) frontal. À cette fin, Visual Studio Code dispose d’un énorme écosystème d’extensions, notamment un débogage de Chrome intégré.

Basculez vers l’onglet **Extensions** et tapez `chrome` dans la zone de recherche :

![Extension de débogage de Chrome pour Visual Studio Code](./media/node-howto-e2e/chrome.png)

Sélectionnez l’extension nommée **Debugger for Chrome** (Débogueur pour Chrome), puis sélectionnez **Installer**. Après avoir installé l’extension de débogage de Chrome, sélectionnez **Recharger** pour fermer et rouvrir Visual Studio Code afin d’activer l’extension. 

![Rechargement de Visual Studio Code après l’installation de l’extension de débogage de Chrome](./media/node-howto-e2e/chrome-extension-reload-vscode.png)

Si vous avez pu exécuter et déboguer le code Node.js sans la moindre configuration spécifique à Visual Studio Code, pour déboguer une application web frontale, vous devez générer un fichier `launch.json` qui indique à Visual Studio Code comment exécuter l’application. 

Pour générer le fichier `launch.json`, basculez vers l’onglet **Déboguer**, cliquez sur l’icône d’engrenage (au-dessus de laquelle doit figurer un point rouge), puis sélectionnez l’environnement **node.js**.

![Option de Visual Studio Code permettant de configurer le fichier launch.json](./media/node-howto-e2e/debug-gear.png)

Une fois créé, le fichier `launch.json` ressemble à ce qui suit et indique à Visual Studio Code comment le lancer et/ou l’attacher à l’application aux fins de débogage. 

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "node",
            "request": "launch",
            "name": "Launch Program",
            "program": "${workspaceRoot}/server.js"
        },
        {
            "type": "node",
            "request": "attach",
            "name": "Attach to Port",
            "address": "localhost",
            "port": 5858
        }
    ]
}
```

Notez que Visual Studio Code a été en mesure de détecter que le script de démarrage de l’application est `server.js`. 

Ouvrez le fichier `launch.json`, cliquez sur **Ajouter une configuration** (en bas à droite), puis sélectionnez **Chrome: launch with userDataDir** (Chrome : lancement avec userDataDir).

![Ajout d’une configuration Chrome à Visual Studio Code](./media/node-howto-e2e/add-chrome-config.png)

L’ajout d’une nouvelle configuration de série de tests pour Chrome vous permet de déboguer le code JavaScript frontal. 

Vous pouvez pointer la souris sur n’importe quel paramètre spécifié pour afficher une documentation sur l’action du paramètre. Notez également que Visual Studio Code détecte automatiquement l’URL de l’application. Mettez à jour la propriété **webRoot** sur `${workspaceRoot}/public` afin que le débogueur de Chrome sache où trouver les ressources frontales de l’application :

```json
{
   "type": "chrome",
   "request": "launch",
   "name": "Launch Chrome",
   "url": "http://localhost:8080",
   "webRoot": "${workspaceRoot}/public",
   "userDataDir": "${workspaceRoot}/.vscode/chrome"
}
```

Pour pouvoir lancer/déboguer simultanément les ressources frontales et principales, vous devez créer une configuration de série de test *composée* qui indique à Visual Studio Code l’ensemble de configurations à exécuter en parallèle. 

Ajoutez l’extrait de code suivant en tant que propriété de niveau supérieur dans le fichier `launch.json` (comme parent de la propriété **configurations** existante).

```json
"compounds": [
   {
      "name": "Full-Stack",
      "configurations": ["Launch Program", "Launch Chrome"]
   }
]
```

Les valeurs de chaîne spécifiées dans le tableau **compounds.configurations** renvoient au **nom** des entrées individuelles dans la liste des **configurations**. Si vous avez modifié ces noms, vous devrez apporter les modifications appropriées au tableau. Pour voir comment cela fonctionne, basculez vers l’onglet de débogage, définissez la configuration sélectionnée sur **Full-Stack** (le nom de la configuration composée), puis appuyez sur **&lt;F5>** pour l’exécuter.

![Exécution d’une configuration dans Visual Studio Code](./media/node-howto-e2e/full-stack-profile.png)

L’exécution de la configuration lance l’application Node.js (comme indiqué dans la sortie de la console de débogage) et Chrome (configuré pour accéder à l’application Node.js à l’adresse `http://localhost:8080`).

Appuyez sur **&lt;Ctrl> P**, puis entrez (ou sélectionnez) `todos.js`, qui correspond au Angular principal pour le code frontal de l’application. 

Définissez un point d’arrêt sur la ligne 11, qui correspond au point d’entrée pour une nouvelle entrée de tâche en cours de création.

Retournez à l’application en cours d’exécution et ajoutez une nouvelle entrée de tâche. Vous remarquerez que Visual Studio Code a interrompu l’exécution dans le code Angular.

![Débogage du code frontal dans Visual Studio Code](./media/node-howto-e2e/chrome-pause.png)

Tout comme le débogage Node.js, vous pouvez pointez votre souris sur des expressions, afficher les variables locales/espions, évaluer les expressions dans la console, etc. 

Deux points intéressants sont à prendre en considération :

1. Le volet **Pile des appels** affiche deux piles différentes : **Node** et **Chrome**, en indiquant celle qui est actuellement suspendue.

1. Vous pouvez basculer entre le code frontal et principal. Pour tester cela, appuyez sur **&lt;F5>** pour exécuter et atteindre le point d’arrêt défini précédemment dans l’itinéraire Express.

Avec cette configuration, vous pouvez maintenant déboguer efficacement le code JavaScript frontal, principal ou de la pile complète directement dans Visual Studio Code. 

En outre, le concept de débogueur composé ne se résume pas à deux processus cibles, de même qu’il ne limite pas à JavaScript. Par conséquent, si vous travaillez sur une application de microservice (qui est potentiellement polyglotte), vous pouvez utiliser exactement le même workflow (une fois que vous avez installé les extensions appropriées pour la langage ou l’infrastructure).

## <a name="dockerizing-the-app"></a>Dockerisation de l’application

Cette section se concentre sur l’expérience offerte par Visual Studio Code pour un développement avec [Docker](https://www.docker.com/). Les développeurs Node.js utilisent Docker pour fournir des déploiements d’applications portables pour les environnements de développement, d’intégration continue (CI) et de production. Docker présente une courbe d’apprentissage difficile pour certains, c’est pourquoi Visual Studio Code fournit une extension qui tente de simplifier l’utilisation de Docker dans vos applications.

Revenez à l’onglet **Extensions**, recherchez `docker`, puis sélectionnez l’extension **Docker**. 

Installez l’extension Docker, puis rechargez Visual Studio Code.

![Installation de l’extension Docker pour Visual Studio Code](./media/node-howto-e2e/docker-search.png)

L’extension Docker pour Visual Studio Code inclut une commande qui permet de générer un *Dockerfile* et le fichier `docker-compose.yml` pour un projet existant. 

Pour afficher les commandes Docker disponibles, affichez la palette de commandes via **&lt;F1>**, puis tapez `docker`.

![Commandes prises en charge par l’extension Docker pour Visual Studio ](./media/node-howto-e2e/docker-commands.png)

Sélectionnez **Docker: Add docker files to workspace** (Docker : ajouter des fichiers Docker à l’espace de travail), sélectionnez **Node.js** en tant que plateforme d’application, puis indiquez que l’application expose le port `8080`. 

La commande Docker génère un `Dockerfile` complet et des fichiers de composition Docker que vous pouvez commencer à utiliser immédiatement.

![Fichier Dockerfile généré](./media/node-howto-e2e/docker-file.png)

L’extension Docker prend également en charge la saisie semi-automatique pour vos fichiers `Dockerfiles` et `docker-compose.yml`. 

Pour voir comment cela fonctionne, ouvrez le `Dockerfile` et remplacez la ligne 2 :

```docker
FROM node:latest
```

Par :

```docker
FROM mhart
```

En plaçant votre curseur après le `t` dans `mhart`, appuyez sur **&lt;Ctrl>&lt;Espace>** pour afficher tous les référentiels d’images que `mhart` a publiés sur DockerHub.

![Saisie semi-automatique de l’extension Docker](./media/node-howto-e2e/docker-completion.png)

Sélectionnez `mhart/alpine-node` pour obtenir toutes les informations nécessaires pour cette application. 

Les images de plus petite taille sont généralement préférables dans la mesure où il est dans votre intérêt d’accélérer autant que possible vos builds et vos déploiements d’applications, de manière à assurer une distribution et une mise à l’échelle plus rapides.

Maintenant que vous avez généré le `Dockerfile`, vous devez créer l’image réelle de Docker. Une fois encore, vous pouvez utiliser une commande installée par l’extension Docker dans Visual Studio Code. Appuyez sur **&lt;F1>**, entrez `dockerb` dans la palette de commandes, puis sélectionnez la commande **Docker: Build Image** (Docker : générer l’image). Choisissez le `/Dockerfile` que vous venez de générer et de modifier. Spécifiez une balise qui inclut votre nom d’utilisateur DockerHub (par exemple, `lostintangent/node`). Appuyez sur **&lt;ENTRÉE>** pour lancer la fenêtre du terminal intégré qui affiche la sortie de votre image Docker en cours de génération.

![État de génération de l’image Docker](./media/node-howto-e2e/docker-build.png)

Notez que la commande a automatisé le processus d’exécution de `docker build`, ce qui illustre une fois de plus la prise en charge d’une fonction d’amélioration de la productivité que vous pouvez choisir d’utiliser, à moins que vous ne préfériez utiliser directement l’interface CLI Docker. 

À ce stade, pour faciliter l’acquisition de cette image pour les déploiements, vous devez simplement transmettre l’image à DockerHub. Pour ce faire, assurez-vous que vous êtes déjà authentifié auprès de DockerHub en exécutant la commande `docker login` à partir de l’interface CLI et en saisissant vos informations d’identification de compte. Puis, dans Visual Studio Code, vous pouvez afficher la palette de commandes, saisir `dockerpush`, puis sélectionner la commande `Docker: Push`. Sélectionnez la balise d’image que vous venez de créer (par exemple, `lostintangent/node`) et appuyez sur **&lt;Entrée>**. La commande automatise l’appel de `docker push` et affiche la sortie dans le terminal intégré.

## <a name="deploying-the-app"></a>Déploiement de l’application

Maintenant que vous avez dockerisé l’application et que vous l’avez transmise à DockerHub, vous devez la déployer dans le cloud pour la rendre visible à tous. Pour ce faire, vous pouvez utiliser Azure App Service, autrement dit l’offre PaaS d’Azure. App Service possède deux fonctions intéressantes pour les développeurs Node.js :

- La prise en charge des machines virtuelles Linux, ce qui réduit les incompatibilités pour les applications créées à l’aide de modules Node natifs ou d’autres outils qui ne prennent peut-être pas en charge Windows et/ou peuvent avoir un comportement différent.
- La prise en charge des déploiements Docker, qui vous permet de spécifier le nom de votre image Docker tout en autorisant App Service à extraire, déployer et mettre à l’échelle l’image automatiquement.

Pour commencer, ouvrez le terminal Visual Studio. Vous allez utiliser la nouvelle interface Azure CLI 2.0 pour gérer votre compte Azure et approvisionner l’infrastructure nécessaire à l’exécution de l’application de tâches. Une fois que vous êtes connecté à votre compte à partir de l’interface CLI à l’aide de la commande `az login` (comme mentionné dans la section Composants requis), procédez comme suit pour approvisionner l’instance App Service et déployer le conteneur d’applications de tâches :

1. Créez un groupe de ressources, que vous pouvez considérer comme un *espace de noms* ou un *répertoire* destiné à simplifier l’organisation des ressources Azure. L’option `-n` est utilisée pour spécifier le nom du groupe et peut prendre la valeur de votre choix.

    ```shell
    az group create -n nina-demo -l westus
    ```

    > [!NOTE]
    > L’option `-l` indique l’emplacement du groupe de ressources. En version préliminaire, la prise en charge d’App Service sur Linux est disponible uniquement dans certaines régions. Par conséquent, si vous ne vous trouvez pas dans l’ouest des États-Unis et que vous souhaitez vérifier les autres régions disponibles, exécutez `az appservice list-locations --linux-workers-enabled` à partir de l’interface CLI pour afficher les options de votre centre de données.

2. Définissez le groupe de ressources que vous venez de créer en tant que groupe de ressources par défaut afin que vous puissiez continuer à utiliser l’interface CLI sans avoir à spécifier explicitement le groupe de ressources à chaque appel de la CLI :

   ```shell
   az configure -d group=nina-demo
   ```
   
3. Créez le *plan* App Service qui gère la création et la mise à l’échelle des machines virtuelles sous-jacentes sur lesquelles votre application est déployée. Une fois encore, vous pouvez spécifier n’importe quelle valeur pour l’option `n`.

    ```shell
    az appservice plan create -n nina-demo-plan --is-linux
    ```

    > [!NOTE]
    > L’option --is-linux indique que vous souhaitez des machines virtuelles basées sur Linux. Sans cette option, l’interface CLI approvisionnera par défaut des machines virtuelles basées sur Windows.

4. Créez l’application web App Service, qui représente l’application de tâche réelle qui s’exécutera dans le plan et dans le groupe de ressources que vous venez de créer. Vous pouvez considérer une application web comme synonyme d’un processus ou d’un conteneur et assimiler le plan à l’hôte de la machine virtuelle ou du conteneur sur lequel elle s’exécute. En outre, dans le cadre de la création de l’application web, vous devez la configurer pour utiliser l’image Docker que vous avez publiée sur DockerHub :

    ```shell
    az webapp create -n nina-demo-app -p nina-demo-plan -i lostintangent/node
    ``` 

    > [!NOTE]
    > Si vous préférez un déploiement Git plutôt que d’utiliser un conteneur personnalisé, consultez l’article [Créer une application web Node.js dans Azure](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-nodejs#configure-to-use-nodejs).

5. Définissez l’application web en tant qu’instance web par défaut :

    ```shell
    az configure -d web=nina-demo-app
    ```

6. Lancez l’application pour afficher le conteneur déployé qui est disponible sur une URL `*.azurewebsites.net` :

    ```shell
    az webapp browse
    ```

    ![Application de tâches en cours d’exécution dans le navigateur](./media/node-howto-e2e/browse-app.png)

    > [!NOTE]
    > Le premier chargement de l’application peut prendre quelques minutes étant donné qu’App Service doit extraire l’image Docker de DockerHub puis la démarrer.

À ce stade, vous venez de déployer et d’exécuter l’application de tâches. 

Vous avez maintenant déployé l’application de tâches. L’icône qui tourne indique cependant que l’application ne peut pas se connecter à la base de données. Cela est dû au fait que vous avez utilisé une instance locale de MongoDB pendant le développement, qui n’est évidemment pas accessible à partir des centres de données Azure. Étant donné que vous avez modifié l’application pour accepter la chaîne de connexion via une variable d’environnement, il vous suffit de démarrer un serveur MongoDB et de reconfigurer l’instance App Service pour faire référence à la variable d’environnement. Ce point est illustré dans la section suivante.

## <a name="provisioning-a-mongodb-server"></a>Approvisionnement d’un serveur MongoDB

Bien que vous puissiez configurer un serveur MongoDB ou un ensemble de réplicas et gérer cette infrastructure vous-même, Azure fournit une solution appelée [Cosmos DB](https://azure.microsoft.com/services/documentdb/). Cosmos DB est une base de données NoSQL performante, entièrement gérée et géoréplicable, qui fournit une couche de compatibilité MongoDB. Cela signifie que vous pouvez y faire pointer une application MEAN existante (ou n’importe quel client/outil MongoDB comme [Studio 3P](https://studio3t.com/)) sans avoir à modifier quoi que ce soit, à l’exception de la chaîne de connexion. Les étapes suivantes montrent comment procéder :

1. À partir du terminal Visual Studio Code, exécutez la commande suivante pour créer une instance compatible MongoDB du service Cosmos DB. Remplacez l’espace réservé **<NAME>** par une valeur globale unique (Cosmos DB utilise ce nom pour générer l’URL du serveur de base de données) :

   ```shell
   COSMOSDB_NAME=<NAME>
   az cosmosdb create -n $COSMOSDB_NAME --kind MongoDB
   ```

2. Récupérez la chaîne de connexion MongoDB pour cette instance :

   ```shell
   MONGODB_URL=$(az cosmosdb list-connection-strings -n $COSMOSDB_NAME -otsv --query "connectionStrings[0].connectionString")
   ```

3. Mettez à jour la variable d’environnement **MONGODB_URL** de votre application web afin qu’elle se connecte à l’instance Cosmos DB nouvellement provisionnée au lieu d’essayer de se connecter à un serveur MongoDB qui s’exécute en local (et qui n’existe pas !) :

    ```shell
    az webapp config appsettings set --settings MONGODB_URL=$MONGODB_URL
    ```

4. Retournez dans votre navigateur et actualisez la page. Essayez d’ajouter et de supprimer un élément de tâche pour voir si maintenant l’application fonctionne sans avoir à modifier quoi que ce soit ! Définissez la variable d’environnement sur l’instance Cosmos DB créée, qui émule entièrement une base de données MongoDB.

    ![Application de démonstration après connexion à une base de données](./media/node-howto-e2e/finished-demo.png)

Lorsque cela est nécessaire, vous pouvez revenir à l’instance Cosmos DB et augmenter (ou diminuer) le débit réservé dont a besoin MongoDB, puis tirer parti du trafic ajouté sans avoir à gérer d’infrastructure manuellement.

En outre, Cosmos DB indexe automatiquement chaque document et chaque propriété à votre place. De cette façon, vous n’avez pas besoin de profiler les requêtes lentes ou d’affiner manuellement vos index. Il vous suffit d’approvisionner et de mettre à l’échelle au besoin, et laisser Cosmos DB gérer le reste.

## <a name="hosting-a-private-docker-registry"></a>Hébergement d’un registre Docker privé

DockerHub offre une expérience exceptionnelle pour la distribution de vos images de conteneur, mais certains scénarios impliquent d’héberger votre propre registre Docker privé, par exemple pour bénéficier d’avantages sur le plan de la sécurité, de la gouvernance ou des performances. Azure intègre à cet effet [l’Azure Container Registry](https://azure.microsoft.com/services/container-registry/) (ACR), qui vous permet de lancer votre propre registre Docker dont le stockage de sauvegarde se trouve dans le même centre de données que celui de votre application web (ce qui rend les récupérations plus rapides). L’ACR vous assure également un contrôle total sur le contenu et les contrôles d’accès, notamment sur les personnes autorisées à envoyer ou extraire des images. 

La commande suivante permet d’approvisionner un registre personnalisé. Remplacez l’espace réservé **<NAME>** par une valeur globale unique, puisque l’ACR utilise la valeur spécifiée pour générer l’URL du serveur de connexion du registre.

```shell
ACR_NAME=<NAME>
az acr create -n $ACR_NAME -l westus --admin-enabled
```

> [!NOTE]
> Bien que l’exemple de cette rubrique utilise le **compte d’administrateur** pour simplifier les choses, cela n’est pas recommandé pour les registres de production. 

Les commandes `az acr create` affichent l’URL du serveur de connexion (via la colonne `LOGIN SERVER`) que vous utilisez pour vous connecter à l’aide de l’interface CLI Docker (par exemple, `ninademo.azurecr.io`). En outre, la commande génère des informations d’identification d’administrateur que vous pouvez utiliser pour vous authentifier. Pour récupérer ces informations d’identification, exécutez la commande suivante et notez le nom d’utilisateur et le mot de passe qui s’affichent :

```shell
az acr credential show -n $ACR_NAME
```

À l’aide des informations d’identification obtenues à l’étape précédente et de votre serveur de connexion individuel, vous pouvez vous connecter au registre en utilisant le workflow standard de la CLI Docker.

```shell
docker login <LOGIN_SERVER> -u <USERNAME> -p <PASSWORD>
```

Vous pouvez désormais marquer votre conteneur Docker pour indiquer qu’il est associé à votre registre privé à l’aide de la commande suivante (en remplaçant `lostintangent/node` par le nom que vous avez attribué à l’image du conteneur).

```shell
docker tag lostintangent/node <LOGIN_SERVER>/lostintangent/node
```

Pour finir, il ne vous reste plus qu’à envoyer l’image ainsi marquée à votre registre Docker privé.

```shell
docker push <LOGIN_SERVER>/lostintangent/node
```

Votre conteneur est maintenant stocké dans votre propre registre privé, avec l’avantage d’avoir pu utiliser l’interface CLI Docker de la même façon qu’avec DockerHub. Pour indiquer à l’application web App Service une extraction depuis votre registre privé, il vous suffit d’exécuter la commande suivante :

```shell
az appservice web config container set \
    -r <LOGIN_SERVER> \
    -c <LOGIN_SERVER>/lostintangent/node \
    -u <USERNAME> \
    -p <PASSWORD> 
```

> [!NOTE]
> Assurez-vous d’ajouter le préfixe `https://` au début de l’option `-r`. N’ajoutez pas en revanche le préfixe au nom de l’image de conteneur.

Si vous actualisez l’application dans votre navigateur, tout doit normalement apparaître et fonctionner de la même manière. Et pourtant, votre application est exécutée cette fois via votre registre Docker privé. Une fois votre application mise à jour, marquez les modifications et envoyez-les comme indiqué ci-dessus, puis mettez à jour la balise dans la configuration de votre conteneur App Service.

## <a name="configuring-a-custom-domain-name"></a>Configuration d’un nom de domaine personnalisé

Si l’URL `*.azurewebsites.net` est très utile pour les tests, il peut arriver un moment où vous voudrez ajouter un nom de domaine personnalisé à votre application web. Une fois que vous disposez d’un nom de domaine issu d’un bureau d’enregistrement, il vous suffit d’y ajouter un enregistrement `A` qui pointe sur l’adresse IP externe de votre application web (qui est en fait un équilibreur de charge). Vous pouvez récupérer cette adresse IP en exécutant la commande suivante :

```shell
az webapp config hostname get-external-ip
```

Pour ajouter un enregistrement `A`, vous devez également ajouter un enregistrement `TXT` à votre domaine qui pointe vers le domaine `*.azurewebsites.net` que vous utilisiez jusqu’ici. L’association des enregistrements `A` et `TXT` permet à Azure de vérifier que vous êtes le propriétaire du domaine.

Une fois ces enregistrements créés (et une fois que les modifications DNS ont été propagées), enregistrez le domaine personnalisé auprès d’Azure afin qu’il sache recevoir correctement le trafic entrant. 

```shell
az webapp config hostname add --hostname <DOMAIN>
```

> [!NOTE]
> La commande ne fonctionnera pas tant que les modifications DNS n’auront pas été propagées.

Ouvrez un navigateur et accédez à votre domaine personnalisé : vous constaterez qu’il correspond désormais à votre application déployée sur Azure.

## <a name="scaling-up-and-out"></a>Montée en puissance et augmentation de la taille des instances

Dans certains cas, votre application web peut devenir populaire au point que ses ressources allouées (processeur et mémoire RAM) ne suffisent plus à gérer l’augmentation du trafic et des exigences opérationnelles. Le plan App Service que vous avez créé précédemment (**B1**) est fourni avec 1 cœur de processeur et 1,75 Go de RAM, qui peuvent s’épuiser assez rapidement. Le plan **B2** prévoit deux fois plus de RAM et de processeur. Aussi, si vous remarquez que votre application commence à manquer de l’un ou l’autre, vous pouvez augmenter la puissance de la machine virtuelle sous-jacente en exécutant la commande suivante :

```shell
az appservice plan update -n nina-demo-plan --sku B2
```

> [!NOTE]
> Pour accéder aux détails tarifaires et aux spécifications des plans Azure App, consultez l’article [Tarification App Service](https://azure.microsoft.com/pricing/details/app-service/)

Après quelques instants, votre application web est migrée vers le matériel demandé et vous pouvez commencer à tirer parti des ressources associées. Outre la montée en puissance, vous pouvez également effectuer une descente en puissance en exécutant la même commande que ci-dessus, en spécifiant une option `--sku` qui fournit moins de ressources à un prix inférieur. 

Au-delà de la montée en puissance des spécifications de la machine virtuelle, tant que votre application web est sans état, vous avez également la possibilité *d’augmenter la taille des instances* en ajoutant davantage d’instances de machines virtuelles sous-jacentes. Puisque le plan App Service créé précédemment ne comportait qu’une seule machine virtuelle (un *rôle de travail*), tout le trafic entrant est finalement soumis aux limites des ressources disponibles de cette instance. Si vous souhaitez ajouter une deuxième instance de machine virtuelle, vous pouvez exécuter la même commande que précédemment, cette fois non pas en augmentant la puissance de la référence SKU, mais en augmentant le nombre d’instances de machines virtuelles de travail.

```shell
az appservice plan update -n nina-demo-plan --number-of-workers 2
```

Lorsque vous augmentez la taille des instances de cette manière pour une application web, la charge du trafic entrant sera équilibrée en toute transparence entre toutes les instances, ce qui vous permet d’augmenter immédiatement votre capacité sans la moindre modification de code et sans avoir à vous préoccuper de l’infrastructure nécessaire. 

Les applications web sans état sont considérées comme une meilleure pratique, car elles permettent une mise à l’échelle (montée en puissance, descente en puissance, augmentation de la taille des instances) totalement déterministe puisque aucune machine virtuelle ou instance de l’application ne contient l’état nécessaire à son fonctionnement. 

> [!NOTE]
> Bien que le didacticiel de cette rubrique illustre l’exécution d’une simple application web dans le cadre d’un plan App Service, vous pouvez créer et déployer plusieurs applications web dans le même plan, de manière à approvisionner un seul plan et à être facturé en conséquence. 

## <a name="clean-up"></a>Nettoyage

Pour vous éviter de payer pour les ressources Azure que vous n’utilisez pas, exécutez la commande suivante à partir de votre terminal Visual Studio Code pour supprimer toutes les ressources approvisionnées au cours de ce didacticiel.

```shell
az group delete
```

> [!NOTE]
> Le processus de nettoyage peut prendre plusieurs minutes. 

Une fois que vous avez terminé, la commande `az group delete` vous permet de quitter votre compte Azure dans l’état où il se trouvait avant le début de ce didacticiel. Les groupes de ressources présentent notamment l’avantage de pouvoir organiser, déployer et supprimer des ressources Azure en bloc. Il est donc recommandé de regrouper les ressources qui auront vraisemblablement la même durée de vie.