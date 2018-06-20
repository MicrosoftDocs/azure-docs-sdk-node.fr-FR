---
title: Développement Node.js avec Visual Studio Code et Azure
description: Didacticiel complet décrivant la procédure à suivre pour créer, dockeriser et déployer une application Node.js dans Azure
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
ms.locfileid: "20908139"
---
# <a name="nodejs-development-with-visual-studio-code-and-azure"></a><span data-ttu-id="3d887-103">Développement Node.js avec Visual Studio Code et Azure</span><span class="sxs-lookup"><span data-stu-id="3d887-103">Node.js development with Visual Studio Code and Azure</span></span>

<span data-ttu-id="3d887-104">Ce didacticiel explique comment « conteneuriser » une application Node.js existante (avec Docker) et comment la déployer dans Azure à l’aide de Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="3d887-104">This tutorial illustrates taking an existing Node.js app, "containerizing" it (with Docker), and then deploying the app to Azure using Visual Studio Code.</span></span>

<span data-ttu-id="3d887-105">Il utilise une simple application de tâches créée et publiée par [Scotch.io](https://scotch.io/tutorials/creating-a-single-page-todo-app-with-node-and-angular).</span><span class="sxs-lookup"><span data-stu-id="3d887-105">The tutorial makes use of a simple todo app created by and published by [Scotch.io](https://scotch.io/tutorials/creating-a-single-page-todo-app-with-node-and-angular).</span></span> <span data-ttu-id="3d887-106">Cette application MEAN ne comporte qu’une seule page et, par conséquent, utilise MongoDB comme base de données, Node/Express comme API REST/serveur web et Angular.js 1.x comme interface utilisateur frontale.</span><span class="sxs-lookup"><span data-stu-id="3d887-106">It is a single-page MEAN app, and therefore, uses MongoDB as its database, Node/Express for the REST API/web server, and Angular.js 1.x for the front-end UI.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="3d887-107">Composants requis</span><span class="sxs-lookup"><span data-stu-id="3d887-107">Prerequisites</span></span>

<span data-ttu-id="3d887-108">Pour suivre la démonstration, vous devez avoir installé les logiciels suivants :</span><span class="sxs-lookup"><span data-stu-id="3d887-108">In order to follow along with the demo, you'll need to have the following software installed:</span></span>

- [<span data-ttu-id="3d887-109">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="3d887-109">Visual Studio Code</span></span>](https://code.visualstudio.com/)
- [<span data-ttu-id="3d887-110">Docker</span><span class="sxs-lookup"><span data-stu-id="3d887-110">Docker</span></span>](https://www.docker.com/products/docker)
- [<span data-ttu-id="3d887-111">Compte DockerHub</span><span class="sxs-lookup"><span data-stu-id="3d887-111">DockerHub account</span></span>](https://hub.docker.com/)
- [<span data-ttu-id="3d887-112">Azure CLI 2.0</span><span class="sxs-lookup"><span data-stu-id="3d887-112">Azure CLI 2.0</span></span>](https://docs.microsoft.com/cli/azure/install-az-cli2)
- [<span data-ttu-id="3d887-113">Compte Azure</span><span class="sxs-lookup"><span data-stu-id="3d887-113">Azure account</span></span>](https://azure.microsoft.com/free/)
- [<span data-ttu-id="3d887-114">Yarn</span><span class="sxs-lookup"><span data-stu-id="3d887-114">Yarn</span></span>](https://yarnpkg.com/en/docs/install)
- <span data-ttu-id="3d887-115">[Chrome](https://www.google.com/chrome/browser/desktop/) : utilisé pour le débogage du code frontal de l’application de démonstration.</span><span class="sxs-lookup"><span data-stu-id="3d887-115">[Chrome](https://www.google.com/chrome/browser/desktop/) - Used for debugging the demo app's front-end.</span></span>
- <span data-ttu-id="3d887-116">MongoDB : étant donné que l’application de démonstration utilise MongoDB, vous devez disposer d’une instance MongoDB exécutée en local qui écoute sur le port `27017` standard.</span><span class="sxs-lookup"><span data-stu-id="3d887-116">MongoDB - Since the demo app uses MongoDB, you need to have a locally running MongoDB instance that is listening on the standard `27017` port.</span></span> <span data-ttu-id="3d887-117">La façon la plus simple d’effectuer cette opération consiste à exécuter les deux commandes suivantes après l’installation de Docker : `docker pull mongo`, puis `docker run -it -p 27017:27017 mongo`.</span><span class="sxs-lookup"><span data-stu-id="3d887-117">The simplest way to achieve this is by running the following two commands after Docker is installed: `docker pull mongo` followed by `docker run -it -p 27017:27017 mongo`.</span></span>

## <a name="project-setup"></a><span data-ttu-id="3d887-118">Configuration du projet</span><span class="sxs-lookup"><span data-stu-id="3d887-118">Project setup</span></span>

<span data-ttu-id="3d887-119">Pour commencer, téléchargez l’exemple de projet en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="3d887-119">To get started, download the sample project using the following steps:</span></span>

1. <span data-ttu-id="3d887-120">Ouvrez Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="3d887-120">Open Visual Studio Code.</span></span>

1. <span data-ttu-id="3d887-121">Appuyez sur **&lt;F1>** pour afficher la palette de commandes.</span><span class="sxs-lookup"><span data-stu-id="3d887-121">Press **&lt;F1>** to display the command palette.</span></span>

1. <span data-ttu-id="3d887-122">À l’invite de la palette de commandes, entrez `gitcl`, sélectionnez la commande **Git: Clone**, puis appuyez sur **&lt;Entrée>**.</span><span class="sxs-lookup"><span data-stu-id="3d887-122">At the command palette prompt, enter `gitcl`, select the **Git: Clone** command, and press **&lt;Enter>**.</span></span>

    ![commande gitcl dans l’invite de la palette de commandes de Visual Studio Code](./media/node-howto-e2e/git-clone.png)

1. <span data-ttu-id="3d887-124">Lorsque vous êtes invité à saisir **l’URL du référentiel**, entrez `https://github.com/scotch-io/node-todo`, puis appuyez sur **&lt;Entrée>**.</span><span class="sxs-lookup"><span data-stu-id="3d887-124">When prompted for the **Repository URL**, enter `https://github.com/scotch-io/node-todo`, then press **&lt;Enter>**.</span></span>

1. <span data-ttu-id="3d887-125">Sélectionnez (ou créez) le répertoire local dans lequel vous souhaitez cloner le projet.</span><span class="sxs-lookup"><span data-stu-id="3d887-125">Select (or create) the local directory into which you want to clone the project.</span></span>

    ![Explorateur Visual Studio Code](./media/node-howto-e2e/explorer.png)

## <a name="integrated-terminal"></a><span data-ttu-id="3d887-127">Terminal intégré</span><span class="sxs-lookup"><span data-stu-id="3d887-127">Integrated terminal</span></span>

<span data-ttu-id="3d887-128">Dans la mesure où il s’agit d’un projet Node.js, la première chose à faire est de s’assurer que toutes les dépendances du projet sont installées à partir de npm.</span><span class="sxs-lookup"><span data-stu-id="3d887-128">Since this is a Node.js project, the first thing you need to do is ensure that all of the project's dependencies are installed from npm.</span></span>  

1. <span data-ttu-id="3d887-129">Appuyez sur **&lt;Ctrl>\`** pour afficher le terminal intégré de Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="3d887-129">Press **&lt;Ctrl>\`** to display the Visual Studio Code integrated terminal.</span></span> 

1. <span data-ttu-id="3d887-130">Tapez `yarn`, puis appuyez sur **&lt;Entrée>**.</span><span class="sxs-lookup"><span data-stu-id="3d887-130">Enter `yarn`, and press **&lt;Enter>**.</span></span>  

    ![Exécution de la commande yarn dans Visual Studio Code](./media/node-howto-e2e/terminal.png)

## <a name="integrated-git-version-control"></a><span data-ttu-id="3d887-132">Contrôle de version Git intégré</span><span class="sxs-lookup"><span data-stu-id="3d887-132">Integrated Git version control</span></span>

<span data-ttu-id="3d887-133">Un fichier `yarn.lock` est créé une fois les dépendances de l’application installées via Yarn. Ce fichier offre un moyen prévisible de réacquérir précisément les mêmes dépendances, sans la moindre surprise dans les builds CI (intégration continue), les déploiements de production ou d’autres ordinateurs de développement.</span><span class="sxs-lookup"><span data-stu-id="3d887-133">After installing the app's dependencies via Yarn, a `yarn.lock` file is created that provides a predictable way to reacquire the exact same dependencies in the future, without any surprises in either CI (continuous integration) builds, production deployments, or other developer machines.</span></span>

<span data-ttu-id="3d887-134">Les étapes suivantes expliquent comment vérifier le fichier `yarn.lock` dans le contrôle de code source :</span><span class="sxs-lookup"><span data-stu-id="3d887-134">The following steps illustrate how to check the `yarn.lock` file into source control:</span></span>

1. <span data-ttu-id="3d887-135">Dans Visual Studio Code, basculez vers l’onglet Git intégré (l’onglet avec le logo Git).</span><span class="sxs-lookup"><span data-stu-id="3d887-135">Within Visual Studio Code, switch to the integrated Git tab (the tab with the Git logo).</span></span>

1. <span data-ttu-id="3d887-136">Dans la zone **Message**, entrez un message de validation, puis appuyez sur **&lt;Ctrl>&lt;Entrée>**.</span><span class="sxs-lookup"><span data-stu-id="3d887-136">In the **Message** box, enter a commit message, and press **&lt;Ctrl>&lt;Enter>**.</span></span> 

    ![Ajout du fichier yarn.lock à Git](./media/node-howto-e2e/git.png)

## <a name="project-and-code-navigation"></a><span data-ttu-id="3d887-138">Navigation dans le projet et le code</span><span class="sxs-lookup"><span data-stu-id="3d887-138">Project and code navigation</span></span>

<span data-ttu-id="3d887-139">Pour nous orienter dans la base de code, voyons ensemble quelques exemples de fonctionnalités de navigation offertes par Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="3d887-139">In order to orient ourselves within the codebase, let's play around with some examples of some of the navigation capabilities that Visual Studio Code provides.</span></span>

1. <span data-ttu-id="3d887-140">Appuyez sur **&lt;Ctrl> P**.</span><span class="sxs-lookup"><span data-stu-id="3d887-140">Press **&lt;Ctrl>P**.</span></span>

1. <span data-ttu-id="3d887-141">Entrez `.js` pour afficher tous les fichiers JSON/JavaScript du projet, ainsi que le répertoire parent de chaque fichier.</span><span class="sxs-lookup"><span data-stu-id="3d887-141">Enter `.js` to display all the JavaScript/JSON files in the project along with each file's parent directory</span></span> 

    ![Affichage de tous les fichiers .js\*](./media/node-howto-e2e/git-output.png)

1. <span data-ttu-id="3d887-143">Sélectionnez `server.js`, à savoir le script de démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="3d887-143">Select `server.js`, which is the startup script for the app.</span></span> 

1. <span data-ttu-id="3d887-144">Pointez votre souris sur la variable **database** (importée sur la ligne 6) pour en déterminer le type.</span><span class="sxs-lookup"><span data-stu-id="3d887-144">Hover your mouse over the **database** variable (imported on line 6) to see its type.</span></span> <span data-ttu-id="3d887-145">Cette fonction qui permet d’inspecter rapidement les variables/modules/types au sein d’un fichier est extrêmement utile lors du développement de vos projets.</span><span class="sxs-lookup"><span data-stu-id="3d887-145">This ability to quickly inspect variables/modules/types within a file is very useful during the development of your projects.</span></span> 

    ![Détection du type](./media/node-howto-e2e/hover-help.png)

1. <span data-ttu-id="3d887-147">En cliquant dans l’étendue d’une variable (**database**, par exemple), vous pouvez visualiser toutes les références à cette variable dans le même fichier.</span><span class="sxs-lookup"><span data-stu-id="3d887-147">Clicking your mouse within the span of a variable - such as **database** - allows you to see all references to that variable within the same file.</span></span> <span data-ttu-id="3d887-148">Pour afficher toutes les références à une variable dans le projet, cliquez avec le bouton droit sur la variable puis, dans le menu contextuel, sélectionnez **Rechercher toutes les références**.</span><span class="sxs-lookup"><span data-stu-id="3d887-148">To view all references to a variable within the project, right-click the variable, and from the context menu, and select **Find All References**.</span></span>

    ![Rechercher les références à une variable](./media/node-howto-e2e/word-hilight.png)

1. <span data-ttu-id="3d887-150">Outre la possibilité de pointer le curseur de la souris sur une variable pour en découvrir le type, vous pouvez également inspecter la définition d’une variable, même si elle se trouve dans un autre fichier.</span><span class="sxs-lookup"><span data-stu-id="3d887-150">In addition to being to hover your mouse over a variable to discover its type, you can also inspect the definition of a variable, even if it's in another file.</span></span> <span data-ttu-id="3d887-151">Pour voir cette fonctionnalité en action, cliquez avec le bouton droit sur **database.localUrl** (ligne 12) et, dans le menu contextuel, sélectionnez **Aperçu de la définition**.</span><span class="sxs-lookup"><span data-stu-id="3d887-151">To see this in action, right-click **database.localUrl** (line 12), and, from the context menu, select **Peek Definition**.</span></span> 

    ![Aperçu de la définition d’une variable](./media/node-howto-e2e/code-peek.png)

## <a name="modifying-the-code-and-using-autocompletion"></a><span data-ttu-id="3d887-153">Modification du code et utilisation de la saisie semi-automatique</span><span class="sxs-lookup"><span data-stu-id="3d887-153">Modifying the code and using autocompletion</span></span>

<span data-ttu-id="3d887-154">La chaîne de connexion MongoDB est codée en dur dans la déclaration de **database.localUrl**.</span><span class="sxs-lookup"><span data-stu-id="3d887-154">The MongoDB connection string is hard-coded in declaration of the **database.localUrl**.</span></span> <span data-ttu-id="3d887-155">Dans cette section, vous allez modifier le code pour récupérer la chaîne de connexion à partir d’une variable d’environnement et en savoir plus sur la fonctionnalité de saisie semi-automatique de Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="3d887-155">In this section, you'll modify the code to retrieve the connection string from an environment variable, and learn about Visual Studio Code's autocompetion feature.</span></span>  

1. <span data-ttu-id="3d887-156">Ouvrez le fichier `server.js`.</span><span class="sxs-lookup"><span data-stu-id="3d887-156">Open the `server.js` file</span></span>

1. <span data-ttu-id="3d887-157">Remplacez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="3d887-157">Replace the following code:</span></span> 

    ```javascript
    mongoose.connect(database.localUrl);
    ```

    <span data-ttu-id="3d887-158">par ce code :</span><span class="sxs-lookup"><span data-stu-id="3d887-158">with this code:</span></span>

    ```javascript
    mongoose.connect(process.env.MONGODB_URL || database.localUrl);
    ```

<span data-ttu-id="3d887-159">Notez que si vous saisissez le code manuellement (au lieu d’effectuer un copier-coller), lorsque vous tapez le point après `process`, Visual Studio Code affiche les membres disponibles de l’API globale **process** de Node.js.</span><span class="sxs-lookup"><span data-stu-id="3d887-159">Note that if you type the code in manually (instead of copy and paste), when you type the period after `process`, Visual Studio Code displays the available members of the Node.js **process** global API.</span></span>

![La saisie semi-automatique affiche automatiquement les membres d’une API](./media/node-howto-e2e/process-env.png)

<span data-ttu-id="3d887-161">La saisie semi-automatique fonctionne grâce à l’utilisation en arrière-plan de TypeScript (même pour JavaScript), qui permet d’obtenir des informations de type qui peuvent ensuite être utilisées pour informer la liste de saisie semi-automatique au fil de la saisie.</span><span class="sxs-lookup"><span data-stu-id="3d887-161">Autocompetion works because Visual Studio Code uses TypeScript behind the scenes - even for JavaScript - to provide type information that can then be used to inform the completion list as you type.</span></span> <span data-ttu-id="3d887-162">Visual Studio Code est en mesure de détecter qu’il s’agit d’un projet Node.js et donc de télécharger automatiquement le fichier de typages TypeScript pour [Node.js à partir de NPM](https://www.npmjs.com/package/@types/node).</span><span class="sxs-lookup"><span data-stu-id="3d887-162">Visual Studio Code is able to detect that this is a Node.js project, and as a result, automatically downloaded the TypeScript typings file for [Node.js from NPM](https://www.npmjs.com/package/@types/node).</span></span> <span data-ttu-id="3d887-163">Le fichier de typages vous permet d’obtenir une saisie semi-automatique pour les autres fonctions globales Node.js, telles que **Buffer** et **setTimeout**, ainsi que pour tous les modules intégrés comme **fs** et **http**.</span><span class="sxs-lookup"><span data-stu-id="3d887-163">The typings file allows you to get autocompletion for other Node.js globals - such as **Buffer** and **setTimeout** - as well as all of the built-in modules such as **fs** and **http**.</span></span>

<span data-ttu-id="3d887-164">Outre les API Node.js intégrées, cette acquisition automatique des typages fonctionne également pour plus de 2 000 modules tiers, tels que React, Underscore et Express.</span><span class="sxs-lookup"><span data-stu-id="3d887-164">In addition to the built-in Node.js APIs, this auto-acquisition of typings also works for over 2,000 3rd party modules, such as React, Underscore and Express.</span></span> <span data-ttu-id="3d887-165">Par exemple, pour empêcher Mongoose de bloquer l’exemple d’application en cas de problème de connexion à l’instance de base de données MongoDB configurée, insérez la ligne de code suivante à la ligne 13 :</span><span class="sxs-lookup"><span data-stu-id="3d887-165">For example, in order to disable Mongoose from crashing the sample app if it can't connect to the configured MongoDB database instance, insert the following line of code at  line 13:</span></span>

```javascript
mongoose.connection.on("error", () => { console.log("DB connection error"); });
```

<span data-ttu-id="3d887-166">Comme avec le code précédent, vous remarquerez que vous obtenez une saisie semi-automatique sans la moindre intervention de votre part.</span><span class="sxs-lookup"><span data-stu-id="3d887-166">As with the previous code, you'll notice that you get autocompletion without any work on your part.</span></span>

![La saisie semi-automatique affiche automatiquement les membres d’une API](./media/node-howto-e2e/mongoose.png)

<span data-ttu-id="3d887-168">Vous pouvez voir les modules qui prennent en charge cette fonctionnalité de saisie semi-automatique en parcourant le projet [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped), qui est la source communautaire de toutes les définitions de type TypeScript.</span><span class="sxs-lookup"><span data-stu-id="3d887-168">You can see which modules support this auto-complete capability by browsing the [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped) project, which is the community-driven source of all TypeScript type definitions.</span></span>

## <a name="running-the-app"></a><span data-ttu-id="3d887-169">Exécution de l'application</span><span class="sxs-lookup"><span data-stu-id="3d887-169">Running the app</span></span>

<span data-ttu-id="3d887-170">Maintenant que vous avez un peu exploré le code, le moment est venu d’exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="3d887-170">Once you've explored the code a bit, it's time to run the app.</span></span> <span data-ttu-id="3d887-171">Pour exécuter l’application à partir de Visual Studio Code, appuyez sur **&lt;F5>**.</span><span class="sxs-lookup"><span data-stu-id="3d887-171">To run the app from Visual Studio Code, press **&lt;F5>**.</span></span> <span data-ttu-id="3d887-172">Lors de l’exécution du code via **&lt;F5>** (mode de débogage), Visual Studio Code lance l’application et ouvre la fenêtre **Console de débogage** qui affiche le pointeur stdout de l’application.</span><span class="sxs-lookup"><span data-stu-id="3d887-172">When running the code via **&lt;F5>** (debug mode), Visual Studio Code launches the app and displays the **Debug Console** window that displays stdout for the app.</span></span>

![Analyse du stdout d’une application via la console de débogage](./media/node-howto-e2e/console.png)

<span data-ttu-id="3d887-174">En outre, la **Console de débogage** est attachée à la nouvelle application en cours d’exécution, ce qui vous permet d’entrer des expressions JavaScript qui seront évaluées dans l’application. Elle inclut également la saisie semi-automatique.</span><span class="sxs-lookup"><span data-stu-id="3d887-174">Additionally, the **Debug Console** is attached to the newly running app so you can type JavaScript expressions, which will be evaluated in the app, and also includes auto-completion.</span></span> <span data-ttu-id="3d887-175">Pour voir ceci en action, tapez `process.env` dans la console :</span><span class="sxs-lookup"><span data-stu-id="3d887-175">To see this in action, type `process.env` in the console:</span></span>

![Saisie du code dans la console de débogage](./media/node-howto-e2e/console-code.png)

<span data-ttu-id="3d887-177">Vous avez pu exécuter l’application en appuyant sur **&lt;F5>** car le fichier actuellement ouvert est un fichier JavaScript (`server.js`).</span><span class="sxs-lookup"><span data-stu-id="3d887-177">You were able to press **&lt;F5>** to run the app because the currently open file is a JavaScript file (`server.js`).</span></span> <span data-ttu-id="3d887-178">Par conséquent, Visual Studio Code suppose que le projet est une application Node.js.</span><span class="sxs-lookup"><span data-stu-id="3d887-178">As a result, Visual Studio Code assumes that the project is a Node.js app.</span></span> <span data-ttu-id="3d887-179">Si vous fermez tous les fichiers JavaScript dans Visual Studio Code et si vous appuyez ensuite sur **&lt;F5>**, Visual Studio Code vous interrogera sur l’environnement :</span><span class="sxs-lookup"><span data-stu-id="3d887-179">If you close all JavaScript files in Visual Studio Code, and then press **&lt;F5>**, Visual Studio Code will query you as the environment:</span></span>

![Spécification de l’environnement runtime](./media/node-howto-e2e/select-env.png)

<span data-ttu-id="3d887-181">Ouvrez un navigateur et accédez à `http://localhost:8080` pour voir l’application en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="3d887-181">Open a browser, and navigate to `http://localhost:8080` to see the running app.</span></span> <span data-ttu-id="3d887-182">Tapez un message dans la zone de texte et ajoutez/supprimez quelques tâches pour avoir une idée du fonctionnement de l’application.</span><span class="sxs-lookup"><span data-stu-id="3d887-182">Type a message into the textbox and add/remove a few todos to get a feel for how the app works.</span></span>

![Application de tâches en cours d’exécution](./media/node-howto-e2e/todo.png)

## <a name="debugging"></a><span data-ttu-id="3d887-184">Débogage</span><span class="sxs-lookup"><span data-stu-id="3d887-184">Debugging</span></span>

<span data-ttu-id="3d887-185">En plus de la possibilité d’exécuter l’application et d’interagir avec elle via la console intégrée, Visual Studio Code vous permet de définir des points d’arrêt directement dans votre code.</span><span class="sxs-lookup"><span data-stu-id="3d887-185">In addition to being able to run the app and interact with it via the integrated console, Visual Studio Code provides the ability to set breakpoints directly within your code.</span></span> <span data-ttu-id="3d887-186">Par exemple, appuyez sur **&lt;Ctrl>P** pour afficher le sélecteur de fichiers.</span><span class="sxs-lookup"><span data-stu-id="3d887-186">For example, press **&lt;Ctrl>P** to display the file picker.</span></span> <span data-ttu-id="3d887-187">Une fois que le sélecteur de fichier s’affiche, tapez `route`, puis sélectionnez le fichier `route.js`.</span><span class="sxs-lookup"><span data-stu-id="3d887-187">Once the file picker displays, type `route`, and select the `route.js` file.</span></span>

<span data-ttu-id="3d887-188">Définissez un point d’arrêt sur la ligne 28, qui représente l’itinéraire Express qui est appelé lorsque l’application tente d’ajouter une entrée de tâche.</span><span class="sxs-lookup"><span data-stu-id="3d887-188">Set a breakpoint on line 28, which represents the Express route that is called when the app tries to add a todo entry.</span></span> <span data-ttu-id="3d887-189">Pour définir un point d’arrêt, cliquez simplement sur la zone à gauche du numéro de ligne dans l’éditeur, comme indiqué dans l’illustration suivante.</span><span class="sxs-lookup"><span data-stu-id="3d887-189">To set a breakpoint, simply click the area to the left of the line number within the editor as shown in the following figure.</span></span>

![Définition d’un point d’arrêt dans Visual Studio Code](./media/node-howto-e2e/breakpoint.png)

> [!NOTE]
> <span data-ttu-id="3d887-191">En plus des points d’arrêt standard, Visual Studio Code prend en charge des points d’arrêt conditionnels qui vous permettent de personnaliser le moment où l’application doit suspendre son exécution.</span><span class="sxs-lookup"><span data-stu-id="3d887-191">In addition to standard breakpoints, Visual Studio Code supports conditional breakpoints that allow you to customize when the app should suspend execution.</span></span> <span data-ttu-id="3d887-192">Pour définir un point d’arrêt conditionnel, cliquez sur la zone à gauche de la ligne sur laquelle vous souhaitez interrompre l’exécution, sélectionnez **Ajouter un point d’arrêt conditionnel...** et spécifiez soit une expression JavaScript (par exemple, `foo = "bar"`) soit le nombre d’exécutions qui définit la condition sous laquelle vous voulez interrompre l’exécution.</span><span class="sxs-lookup"><span data-stu-id="3d887-192">To set a conditional breakpoint, right-click the area to the left of the line on which you wish to pause execution, select **Add Conditional Breakpoint...**, and specify either a JavaScript expression (e.g. `foo = "bar"`) or execution count that defines the condition under which you want to pause execution.</span></span>
> 
> 

<span data-ttu-id="3d887-193">Une fois le point d’arrêt défini, retournez à l’application en cours d’exécution et ajoutez une entrée de tâche.</span><span class="sxs-lookup"><span data-stu-id="3d887-193">Once the breakpoint has been set, return to the running app and add a todo entry.</span></span> <span data-ttu-id="3d887-194">L’ajout d’une entrée de tâche provoque immédiatement la suspension de l’exécution de l’application sur la ligne 28 où vous avez défini le point d’arrêt :</span><span class="sxs-lookup"><span data-stu-id="3d887-194">Adding a todo entry immediately causes the app to suspend execution on line 28 where you set the breakpoint:</span></span>

![Interruption de l’exécution sur un point d’arrêt par Visual Studio Code](./media/node-howto-e2e/debugger.png)

<span data-ttu-id="3d887-196">Une fois l’application suspendue, vous pouvez pointer votre souris sur les expressions du code pour afficher leur valeur actuelle, inspecter les variables locales/espions et la pile des appels, et utiliser la barre d’outils de débogage pour naviguer dans l’exécution du code.</span><span class="sxs-lookup"><span data-stu-id="3d887-196">Once the application has been paused, you can hover your mouse over the code's expressions to view their current value, inspect the locals/watches and call stack, and use the debug toolbar to step through the code execution.</span></span> <span data-ttu-id="3d887-197">Appuyez sur **&lt;F5>** pour reprendre l’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="3d887-197">Press **&lt;F5>** to resume execution of the app.</span></span>

## <a name="full-stack-debugging"></a><span data-ttu-id="3d887-198">Débogage de la pile complète</span><span class="sxs-lookup"><span data-stu-id="3d887-198">Full-stack debugging</span></span>

<span data-ttu-id="3d887-199">Comme mentionné précédemment dans la rubrique, l’application de tâches est une application MEAN, ce qui signifie que ses codes frontaux et principaux sont écrits à l’aide de JavaScript.</span><span class="sxs-lookup"><span data-stu-id="3d887-199">As mentioned earlier in the topic, the TODO app is a MEAN app - meaning that its front-end and back-end are both written using JavaScript.</span></span> <span data-ttu-id="3d887-200">Ainsi, pendant que vous déboguez le code (Node/Express) principal, vous devrez peut-être à un moment donné déboguer le code (Angular) frontal.</span><span class="sxs-lookup"><span data-stu-id="3d887-200">So, while you're currently debugging the back-end (Node/Express) code, at some point, you may need to debug the front-end (Angular) code.</span></span> <span data-ttu-id="3d887-201">À cette fin, Visual Studio Code dispose d’un énorme écosystème d’extensions, notamment un débogage de Chrome intégré.</span><span class="sxs-lookup"><span data-stu-id="3d887-201">For that purpose, Visual Studio Code has a huge ecosystem of extensions, including integrated Chrome debugging.</span></span>

<span data-ttu-id="3d887-202">Basculez vers l’onglet **Extensions** et tapez `chrome` dans la zone de recherche :</span><span class="sxs-lookup"><span data-stu-id="3d887-202">Switch to the **Extensions** tab, and type `chrome` into the search box:</span></span>

![Extension de débogage de Chrome pour Visual Studio Code](./media/node-howto-e2e/chrome.png)

<span data-ttu-id="3d887-204">Sélectionnez l’extension nommée **Debugger for Chrome** (Débogueur pour Chrome), puis sélectionnez **Installer**.</span><span class="sxs-lookup"><span data-stu-id="3d887-204">Select the extension named **Debugger for Chrome**, and select **Install**.</span></span> <span data-ttu-id="3d887-205">Après avoir installé l’extension de débogage de Chrome, sélectionnez **Recharger** pour fermer et rouvrir Visual Studio Code afin d’activer l’extension.</span><span class="sxs-lookup"><span data-stu-id="3d887-205">After installing the Chrome debugging extension, select **Reload** to close and reopen Visual Studio Code in order to activate the extension.</span></span> 

![Rechargement de Visual Studio Code après l’installation de l’extension de débogage de Chrome](./media/node-howto-e2e/chrome-extension-reload-vscode.png)

<span data-ttu-id="3d887-207">Si vous avez pu exécuter et déboguer le code Node.js sans la moindre configuration spécifique à Visual Studio Code, pour déboguer une application web frontale, vous devez générer un fichier `launch.json` qui indique à Visual Studio Code comment exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="3d887-207">While you were able to run and debug the Node.js code without any Visual Stdio Code-specific configuration, in order to debug a front-end web app, you need to generate a `launch.json` file that instructs Visual Studio Code how to run the app.</span></span> 

<span data-ttu-id="3d887-208">Pour générer le fichier `launch.json`, basculez vers l’onglet **Déboguer**, cliquez sur l’icône d’engrenage (au-dessus de laquelle doit figurer un point rouge), puis sélectionnez l’environnement **node.js**.</span><span class="sxs-lookup"><span data-stu-id="3d887-208">To generate the `launch.json` file, switch to the **Debug** tab, click the gear icon (which should have a little red dot on top of it), and select the **node.js** environment.</span></span>

![Option de Visual Studio Code permettant de configurer le fichier launch.json](./media/node-howto-e2e/debug-gear.png)

<span data-ttu-id="3d887-210">Une fois créé, le fichier `launch.json` ressemble à ce qui suit et indique à Visual Studio Code comment le lancer et/ou l’attacher à l’application aux fins de débogage.</span><span class="sxs-lookup"><span data-stu-id="3d887-210">Once created, the `launch.json` file looks similar to the following, and tells Visual Studio Code how to launch and/or attach to the app in order to debug it.</span></span> 

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

<span data-ttu-id="3d887-211">Notez que Visual Studio Code a été en mesure de détecter que le script de démarrage de l’application est `server.js`.</span><span class="sxs-lookup"><span data-stu-id="3d887-211">Note that Visual Studio Code was able to detect that the app's startup script is `server.js`.</span></span> 

<span data-ttu-id="3d887-212">Ouvrez le fichier `launch.json`, cliquez sur **Ajouter une configuration** (en bas à droite), puis sélectionnez **Chrome: launch with userDataDir** (Chrome : lancement avec userDataDir).</span><span class="sxs-lookup"><span data-stu-id="3d887-212">With the `launch.json` file open, select **Add Configuration** (bottom right), and select **Chrome: Launch with userDataDir**.</span></span>

![Ajout d’une configuration Chrome à Visual Studio Code](./media/node-howto-e2e/add-chrome-config.png)

<span data-ttu-id="3d887-214">L’ajout d’une nouvelle configuration de série de tests pour Chrome vous permet de déboguer le code JavaScript frontal.</span><span class="sxs-lookup"><span data-stu-id="3d887-214">Adding a new run configuration for Chrome allows you to debug the front-end JavaScript code.</span></span> 

<span data-ttu-id="3d887-215">Vous pouvez pointer la souris sur n’importe quel paramètre spécifié pour afficher une documentation sur l’action du paramètre.</span><span class="sxs-lookup"><span data-stu-id="3d887-215">You can hover your mouse over any of the settings that are specified to view documentation about what the setting does.</span></span> <span data-ttu-id="3d887-216">Notez également que Visual Studio Code détecte automatiquement l’URL de l’application.</span><span class="sxs-lookup"><span data-stu-id="3d887-216">Additionally, notice that Visual Studio Code automatically detects the URL of the app.</span></span> <span data-ttu-id="3d887-217">Mettez à jour la propriété **webRoot** sur `${workspaceRoot}/public` afin que le débogueur de Chrome sache où trouver les ressources frontales de l’application :</span><span class="sxs-lookup"><span data-stu-id="3d887-217">Update the **webRoot** property to `${workspaceRoot}/public` so that the Chrome debugger will know where to find the app's front-end assets:</span></span>

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

<span data-ttu-id="3d887-218">Pour pouvoir lancer/déboguer simultanément les ressources frontales et principales, vous devez créer une configuration de série de test *composée* qui indique à Visual Studio Code l’ensemble de configurations à exécuter en parallèle.</span><span class="sxs-lookup"><span data-stu-id="3d887-218">In order to launch/debug both the front and back-end at the same time, you need to create a *compound* run configuration that tells Visual Studio Code which set of configurations to run in parallel.</span></span> 

<span data-ttu-id="3d887-219">Ajoutez l’extrait de code suivant en tant que propriété de niveau supérieur dans le fichier `launch.json` (comme parent de la propriété **configurations** existante).</span><span class="sxs-lookup"><span data-stu-id="3d887-219">Add the following snippet as a top-level property within the `launch.json` file (as a sibling of the existing **configurations** property).</span></span>

```json
"compounds": [
   {
      "name": "Full-Stack",
      "configurations": ["Launch Program", "Launch Chrome"]
   }
]
```

<span data-ttu-id="3d887-220">Les valeurs de chaîne spécifiées dans le tableau **compounds.configurations** renvoient au **nom** des entrées individuelles dans la liste des **configurations**.</span><span class="sxs-lookup"><span data-stu-id="3d887-220">The string values specified in the **compounds.configurations** array refer to the **name** of individual entries in the list of **configurations**.</span></span> <span data-ttu-id="3d887-221">Si vous avez modifié ces noms, vous devrez apporter les modifications appropriées au tableau.</span><span class="sxs-lookup"><span data-stu-id="3d887-221">If you've modfied those names, you'll need to make the appropriate changes in the array.</span></span> <span data-ttu-id="3d887-222">Pour voir comment cela fonctionne, basculez vers l’onglet de débogage, définissez la configuration sélectionnée sur **Full-Stack** (le nom de la configuration composée), puis appuyez sur **&lt;F5>** pour l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="3d887-222">To see this in action, switch to the debug tab, and change the selected configuration to **Full-Stack** (the name of the compound configuration), and press **&lt;F5>** to run it.</span></span>

![Exécution d’une configuration dans Visual Studio Code](./media/node-howto-e2e/full-stack-profile.png)

<span data-ttu-id="3d887-224">L’exécution de la configuration lance l’application Node.js (comme indiqué dans la sortie de la console de débogage) et Chrome (configuré pour accéder à l’application Node.js à l’adresse `http://localhost:8080`).</span><span class="sxs-lookup"><span data-stu-id="3d887-224">Running the configuration launches the Node.js app (as can be seen in the debug console output) and Chrome (configured to navigate to the Node.js app at `http://localhost:8080`).</span></span>

<span data-ttu-id="3d887-225">Appuyez sur **&lt;Ctrl> P**, puis entrez (ou sélectionnez) `todos.js`, qui correspond au Angular principal pour le code frontal de l’application.</span><span class="sxs-lookup"><span data-stu-id="3d887-225">Press **&lt;Ctrl>P**, and enter (or select) `todos.js`, which is the main Angular controller for the app's front-end.</span></span> 

<span data-ttu-id="3d887-226">Définissez un point d’arrêt sur la ligne 11, qui correspond au point d’entrée pour une nouvelle entrée de tâche en cours de création.</span><span class="sxs-lookup"><span data-stu-id="3d887-226">Set a breakpoint on line 11, which is the entry-point for a new todo entry being created.</span></span>

<span data-ttu-id="3d887-227">Retournez à l’application en cours d’exécution et ajoutez une nouvelle entrée de tâche. Vous remarquerez que Visual Studio Code a interrompu l’exécution dans le code Angular.</span><span class="sxs-lookup"><span data-stu-id="3d887-227">Return to the running app, add a new todo entry, and notice that Visual Studio Code has now suspended execution within the Angular code.</span></span>

![Débogage du code frontal dans Visual Studio Code](./media/node-howto-e2e/chrome-pause.png)

<span data-ttu-id="3d887-229">Tout comme le débogage Node.js, vous pouvez pointez votre souris sur des expressions, afficher les variables locales/espions, évaluer les expressions dans la console, etc.</span><span class="sxs-lookup"><span data-stu-id="3d887-229">Like Node.js debugging, you can hover your mouse over expressions, view locals/watches, evaluate expressions in the console, and so on.</span></span> 

<span data-ttu-id="3d887-230">Deux points intéressants sont à prendre en considération :</span><span class="sxs-lookup"><span data-stu-id="3d887-230">There are two cools things to note:</span></span>

1. <span data-ttu-id="3d887-231">Le volet **Pile des appels** affiche deux piles différentes : **Node** et **Chrome**, en indiquant celle qui est actuellement suspendue.</span><span class="sxs-lookup"><span data-stu-id="3d887-231">The **Call Stack** pane displays two different stacks: **Node** and **Chrome**, and indicates which one is currently paused.</span></span>

1. <span data-ttu-id="3d887-232">Vous pouvez basculer entre le code frontal et principal.</span><span class="sxs-lookup"><span data-stu-id="3d887-232">You can step between front and back-end code.</span></span> <span data-ttu-id="3d887-233">Pour tester cela, appuyez sur **&lt;F5>** pour exécuter et atteindre le point d’arrêt défini précédemment dans l’itinéraire Express.</span><span class="sxs-lookup"><span data-stu-id="3d887-233">To test this, press **&lt;F5>**, which will run and hit the breakpoint previously set in the Express route.</span></span>

<span data-ttu-id="3d887-234">Avec cette configuration, vous pouvez maintenant déboguer efficacement le code JavaScript frontal, principal ou de la pile complète directement dans Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="3d887-234">With this setup, you can now efficiently debug front, back, or full-stack JavaScript code directly within Visual Studio Code.</span></span> 

<span data-ttu-id="3d887-235">En outre, le concept de débogueur composé ne se résume pas à deux processus cibles, de même qu’il ne limite pas à JavaScript.</span><span class="sxs-lookup"><span data-stu-id="3d887-235">In addition, the compound debugger concept is not limited to just two target processes, and also isn't just limited to JavaScript.</span></span> <span data-ttu-id="3d887-236">Par conséquent, si vous travaillez sur une application de microservice (qui est potentiellement polyglotte), vous pouvez utiliser exactement le même workflow (une fois que vous avez installé les extensions appropriées pour la langage ou l’infrastructure).</span><span class="sxs-lookup"><span data-stu-id="3d887-236">Therefore, if work on a microservice app (that is potentially polyglot), you can use the exact same workflow (once you've installed the appropriate extensions for the language/framework).</span></span>

## <a name="dockerizing-the-app"></a><span data-ttu-id="3d887-237">Dockerisation de l’application</span><span class="sxs-lookup"><span data-stu-id="3d887-237">Dockerizing the app</span></span>

<span data-ttu-id="3d887-238">Cette section se concentre sur l’expérience offerte par Visual Studio Code pour un développement avec [Docker](https://www.docker.com/).</span><span class="sxs-lookup"><span data-stu-id="3d887-238">This section focuses on the experience that Visual Studio Code provides for developing with [Docker](https://www.docker.com/).</span></span> <span data-ttu-id="3d887-239">Les développeurs Node.js utilisent Docker pour fournir des déploiements d’applications portables pour les environnements de développement, d’intégration continue (CI) et de production.</span><span class="sxs-lookup"><span data-stu-id="3d887-239">Node.js developers use Docker to provide portable app deployments for both development, CI (continuous integration), and production environments.</span></span> <span data-ttu-id="3d887-240">Docker présente une courbe d’apprentissage difficile pour certains, c’est pourquoi Visual Studio Code fournit une extension qui tente de simplifier l’utilisation de Docker dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="3d887-240">As Docker presents a steep-learning curve to some, Visual Studio Code provides an extension that tries to help simplify some using Docker in your apps.</span></span>

<span data-ttu-id="3d887-241">Revenez à l’onglet **Extensions**, recherchez `docker`, puis sélectionnez l’extension **Docker**.</span><span class="sxs-lookup"><span data-stu-id="3d887-241">Switch back to the **Extensions** tab, search for `docker`, and select the **Docker** extension.</span></span> 

<span data-ttu-id="3d887-242">Installez l’extension Docker, puis rechargez Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="3d887-242">Install the Docker extension, and then reload Visual Studio Code.</span></span>

![Installation de l’extension Docker pour Visual Studio Code](./media/node-howto-e2e/docker-search.png)

<span data-ttu-id="3d887-244">L’extension Docker pour Visual Studio Code inclut une commande qui permet de générer un *Dockerfile* et le fichier `docker-compose.yml` pour un projet existant.</span><span class="sxs-lookup"><span data-stu-id="3d887-244">The Docker extension for Visual Studio Code includes a command for generating a *Dockerfile* and the `docker-compose.yml` file for an existing project.</span></span> 

<span data-ttu-id="3d887-245">Pour afficher les commandes Docker disponibles, affichez la palette de commandes via **&lt;F1>**, puis tapez `docker`.</span><span class="sxs-lookup"><span data-stu-id="3d887-245">To see the available Docker commands, display the command palette - via **&lt;F1>** - and type `docker`.</span></span>

![<span data-ttu-id="3d887-246">Commandes prises en charge par l’extension Docker pour Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3d887-246">Commands supported by the Docker extension for Visual Studio</span></span> ](./media/node-howto-e2e/docker-commands.png)

<span data-ttu-id="3d887-247">Sélectionnez **Docker: Add docker files to workspace** (Docker : ajouter des fichiers Docker à l’espace de travail), sélectionnez **Node.js** en tant que plateforme d’application, puis indiquez que l’application expose le port `8080`.</span><span class="sxs-lookup"><span data-stu-id="3d887-247">Select **Docker: Add docker files to workspace**, select **Node.js** as the app platform, and specify that the app exposes port `8080`.</span></span> 

<span data-ttu-id="3d887-248">La commande Docker génère un `Dockerfile` complet et des fichiers de composition Docker que vous pouvez commencer à utiliser immédiatement.</span><span class="sxs-lookup"><span data-stu-id="3d887-248">The Docker command generates a complete `Dockerfile` and Docker-compose files that you can begin using immediately.</span></span>

![Fichier Dockerfile généré](./media/node-howto-e2e/docker-file.png)

<span data-ttu-id="3d887-250">L’extension Docker prend également en charge la saisie semi-automatique pour vos fichiers `Dockerfiles` et `docker-compose.yml`.</span><span class="sxs-lookup"><span data-stu-id="3d887-250">The Docker extension also provides auto-completion for your `Dockerfiles` and `docker-compose.yml` files.</span></span> 

<span data-ttu-id="3d887-251">Pour voir comment cela fonctionne, ouvrez le `Dockerfile` et remplacez la ligne 2 :</span><span class="sxs-lookup"><span data-stu-id="3d887-251">To see this in action, open the `Dockerfile` and change line 2 from:</span></span>

```docker
FROM node:latest
```

<span data-ttu-id="3d887-252">Par :</span><span class="sxs-lookup"><span data-stu-id="3d887-252">To:</span></span>

```docker
FROM mhart
```

<span data-ttu-id="3d887-253">En plaçant votre curseur après le `t` dans `mhart`, appuyez sur **&lt;Ctrl>&lt;Espace>** pour afficher tous les référentiels d’images que `mhart` a publiés sur DockerHub.</span><span class="sxs-lookup"><span data-stu-id="3d887-253">With your cursor positioned after the `t` in `mhart`, press **&lt;Ctrl>&lt;Space>** to view all the image repositories that `mhart` has published on DockerHub.</span></span>

![Saisie semi-automatique de l’extension Docker](./media/node-howto-e2e/docker-completion.png)

<span data-ttu-id="3d887-255">Sélectionnez `mhart/alpine-node` pour obtenir toutes les informations nécessaires pour cette application.</span><span class="sxs-lookup"><span data-stu-id="3d887-255">Select `mhart/alpine-node`, which provides everything that this app needs.</span></span> 

<span data-ttu-id="3d887-256">Les images de plus petite taille sont généralement préférables dans la mesure où il est dans votre intérêt d’accélérer autant que possible vos builds et vos déploiements d’applications, de manière à assurer une distribution et une mise à l’échelle plus rapides.</span><span class="sxs-lookup"><span data-stu-id="3d887-256">Smaller images are typically better since you want your app builds and deployments to be as fast as possible, which makes distribution and scaling quicker.</span></span>

<span data-ttu-id="3d887-257">Maintenant que vous avez généré le `Dockerfile`, vous devez créer l’image réelle de Docker.</span><span class="sxs-lookup"><span data-stu-id="3d887-257">Now, that you have generated the `Dockerfile`, you need to build the actual Docker image.</span></span> <span data-ttu-id="3d887-258">Une fois encore, vous pouvez utiliser une commande installée par l’extension Docker dans Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="3d887-258">Once again, you can use a command that the Docker extension installed in Visual Studio Code.</span></span> <span data-ttu-id="3d887-259">Appuyez sur **&lt;F1>**, entrez `dockerb` dans la palette de commandes, puis sélectionnez la commande **Docker: Build Image** (Docker : générer l’image).</span><span class="sxs-lookup"><span data-stu-id="3d887-259">Press **&lt;F1>**, enter `dockerb` at the command palette, and select the **Docker: Build Image** command.</span></span> <span data-ttu-id="3d887-260">Choisissez le `/Dockerfile` que vous venez de générer et de modifier.</span><span class="sxs-lookup"><span data-stu-id="3d887-260">Choose the `/Dockerfile` that you just generated and modified.</span></span> <span data-ttu-id="3d887-261">Spécifiez une balise qui inclut votre nom d’utilisateur DockerHub (par exemple, `lostintangent/node`).</span><span class="sxs-lookup"><span data-stu-id="3d887-261">Specify a tag that includes your DockerHub username (e.g. `lostintangent/node`).</span></span> <span data-ttu-id="3d887-262">Appuyez sur **&lt;ENTRÉE>** pour lancer la fenêtre du terminal intégré qui affiche la sortie de votre image Docker en cours de génération.</span><span class="sxs-lookup"><span data-stu-id="3d887-262">Press **&lt;ENTER>** to launch the integrated terminal window that displays the output of your Docker image being built.</span></span>

![État de génération de l’image Docker](./media/node-howto-e2e/docker-build.png)

<span data-ttu-id="3d887-264">Notez que la commande a automatisé le processus d’exécution de `docker build`, ce qui illustre une fois de plus la prise en charge d’une fonction d’amélioration de la productivité que vous pouvez choisir d’utiliser, à moins que vous ne préfériez utiliser directement l’interface CLI Docker.</span><span class="sxs-lookup"><span data-stu-id="3d887-264">Notice that the command automated the process of running `docker build` for you, which is another example of a productivity enhancer that you can either choose to use, or you can just use the Docker CLI directly.</span></span> 

<span data-ttu-id="3d887-265">À ce stade, pour faciliter l’acquisition de cette image pour les déploiements, vous devez simplement transmettre l’image à DockerHub.</span><span class="sxs-lookup"><span data-stu-id="3d887-265">At this point, to make this image easily acquirable for deployments, you need only push the image to DockerHub.</span></span> <span data-ttu-id="3d887-266">Pour ce faire, assurez-vous que vous êtes déjà authentifié auprès de DockerHub en exécutant la commande `docker login` à partir de l’interface CLI et en saisissant vos informations d’identification de compte.</span><span class="sxs-lookup"><span data-stu-id="3d887-266">To do this, make sure you have already autheticated with DockerHub by running `docker login` from the CLI and entering your account credentials.</span></span> <span data-ttu-id="3d887-267">Puis, dans Visual Studio Code, vous pouvez afficher la palette de commandes, saisir `dockerpush`, puis sélectionner la commande `Docker: Push`.</span><span class="sxs-lookup"><span data-stu-id="3d887-267">Then, in Visual Studio Code, you can bring up the command palette, enter `dockerpush`, and select the `Docker: Push` command.</span></span> <span data-ttu-id="3d887-268">Sélectionnez la balise d’image que vous venez de créer (par exemple, `lostintangent/node`) et appuyez sur **&lt;Entrée>**.</span><span class="sxs-lookup"><span data-stu-id="3d887-268">Select the image tag that you just built (e.g. `lostintangent/node`) and press **&lt;Enter>**.</span></span> <span data-ttu-id="3d887-269">La commande automatise l’appel de `docker push` et affiche la sortie dans le terminal intégré.</span><span class="sxs-lookup"><span data-stu-id="3d887-269">The command automates the calling of `docker push` and displays the output in the integrated terminal.</span></span>

## <a name="deploying-the-app"></a><span data-ttu-id="3d887-270">Déploiement de l’application</span><span class="sxs-lookup"><span data-stu-id="3d887-270">Deploying the app</span></span>

<span data-ttu-id="3d887-271">Maintenant que vous avez dockerisé l’application et que vous l’avez transmise à DockerHub, vous devez la déployer dans le cloud pour la rendre visible à tous.</span><span class="sxs-lookup"><span data-stu-id="3d887-271">Now that you the app Dockerized and pushed to DockerHub, you need to deploy it to the cloud so the world can see it.</span></span> <span data-ttu-id="3d887-272">Pour ce faire, vous pouvez utiliser Azure App Service, autrement dit l’offre PaaS d’Azure.</span><span class="sxs-lookup"><span data-stu-id="3d887-272">For this, you can use Azure App Service, which is Azure's PaaS offering.</span></span> <span data-ttu-id="3d887-273">App Service possède deux fonctions intéressantes pour les développeurs Node.js :</span><span class="sxs-lookup"><span data-stu-id="3d887-273">App Service has two capabilities that are relevant to Node.js developers:</span></span>

- <span data-ttu-id="3d887-274">La prise en charge des machines virtuelles Linux, ce qui réduit les incompatibilités pour les applications créées à l’aide de modules Node natifs ou d’autres outils qui ne prennent peut-être pas en charge Windows et/ou peuvent avoir un comportement différent.</span><span class="sxs-lookup"><span data-stu-id="3d887-274">Support for Linux-based VMs, which reduces incompatibilities for apps which are built using native Node modules, or other tools which might not support Windows and/or may behave differently.</span></span>
- <span data-ttu-id="3d887-275">La prise en charge des déploiements Docker, qui vous permet de spécifier le nom de votre image Docker tout en autorisant App Service à extraire, déployer et mettre à l’échelle l’image automatiquement.</span><span class="sxs-lookup"><span data-stu-id="3d887-275">Support for Docker-based deployments, which allows you to specify the name of your Docker image, and allow App Service to pull, deploy, and scale the image automatically.</span></span>

<span data-ttu-id="3d887-276">Pour commencer, ouvrez le terminal Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3d887-276">To get started, open up the Visual Studio terminal.</span></span> <span data-ttu-id="3d887-277">Vous allez utiliser la nouvelle interface Azure CLI 2.0 pour gérer votre compte Azure et approvisionner l’infrastructure nécessaire à l’exécution de l’application de tâches.</span><span class="sxs-lookup"><span data-stu-id="3d887-277">You'll use the new Azure CLI 2.0 to manage your Azure account and provision the necessary infrastructure to run the todo app.</span></span> <span data-ttu-id="3d887-278">Une fois que vous êtes connecté à votre compte à partir de l’interface CLI à l’aide de la commande `az login` (comme mentionné dans la section Composants requis), procédez comme suit pour approvisionner l’instance App Service et déployer le conteneur d’applications de tâches :</span><span class="sxs-lookup"><span data-stu-id="3d887-278">Once you've logged into your account from the CLI using the `az login` command (as mentioned in the pre-reqs), perform the following steps to provision the App Service instance and deploy the todo app container:</span></span>

1. <span data-ttu-id="3d887-279">Créez un groupe de ressources, que vous pouvez considérer comme un *espace de noms* ou un *répertoire* destiné à simplifier l’organisation des ressources Azure.</span><span class="sxs-lookup"><span data-stu-id="3d887-279">Create a resource group, which you can think of as a *namespace* or *directory* for helping to organize Azure resources.</span></span> <span data-ttu-id="3d887-280">L’option `-n` est utilisée pour spécifier le nom du groupe et peut prendre la valeur de votre choix.</span><span class="sxs-lookup"><span data-stu-id="3d887-280">The `-n` option is used to specify the name of the group and can be anything you want.</span></span>

    ```shell
    az group create -n nina-demo -l westus
    ```

    > [!NOTE]
    > <span data-ttu-id="3d887-281">L’option `-l` indique l’emplacement du groupe de ressources.</span><span class="sxs-lookup"><span data-stu-id="3d887-281">The `-l` option indicates the location of the resource group.</span></span> <span data-ttu-id="3d887-282">En version préliminaire, la prise en charge d’App Service sur Linux est disponible uniquement dans certaines régions.</span><span class="sxs-lookup"><span data-stu-id="3d887-282">While in preview, the App Service on Linux support is available only in select regions.</span></span> <span data-ttu-id="3d887-283">Par conséquent, si vous ne vous trouvez pas dans l’ouest des États-Unis et que vous souhaitez vérifier les autres régions disponibles, exécutez `az appservice list-locations --linux-workers-enabled` à partir de l’interface CLI pour afficher les options de votre centre de données.</span><span class="sxs-lookup"><span data-stu-id="3d887-283">Therefore, if you aren't located in the Western US, and you want to check which other regions are available, run `az appservice list-locations --linux-workers-enabled` from the CLI to view your datacenter options.</span></span>

2. <span data-ttu-id="3d887-284">Définissez le groupe de ressources que vous venez de créer en tant que groupe de ressources par défaut afin que vous puissiez continuer à utiliser l’interface CLI sans avoir à spécifier explicitement le groupe de ressources à chaque appel de la CLI :</span><span class="sxs-lookup"><span data-stu-id="3d887-284">Set the newly created resource group as the default resource group so that you can continue to use the CLI without needing to explicitly specify the resource group with each CLI call:</span></span>

   ```shell
   az configure -d group=nina-demo
   ```
   
3. <span data-ttu-id="3d887-285">Créez le *plan* App Service qui gère la création et la mise à l’échelle des machines virtuelles sous-jacentes sur lesquelles votre application est déployée.</span><span class="sxs-lookup"><span data-stu-id="3d887-285">Create the App Service *plan*, which manages the creation and scaling of the underlying virtual machines to which your app is deployed.</span></span> <span data-ttu-id="3d887-286">Une fois encore, vous pouvez spécifier n’importe quelle valeur pour l’option `n`.</span><span class="sxs-lookup"><span data-stu-id="3d887-286">Once again, specify any value that you'd like for the `n` option.</span></span>

    ```shell
    az appservice plan create -n nina-demo-plan --is-linux
    ```

    > [!NOTE]
    > <span data-ttu-id="3d887-287">L’option --is-linux indique que vous souhaitez des machines virtuelles basées sur Linux.</span><span class="sxs-lookup"><span data-stu-id="3d887-287">The --is-linux option is indicates that you want Linux-based virtual machines.</span></span> <span data-ttu-id="3d887-288">Sans cette option, l’interface CLI approvisionnera par défaut des machines virtuelles basées sur Windows.</span><span class="sxs-lookup"><span data-stu-id="3d887-288">Without it, the CLI defaults to provisioning Windows-based virtual machines.</span></span>

4. <span data-ttu-id="3d887-289">Créez l’application web App Service, qui représente l’application de tâche réelle qui s’exécutera dans le plan et dans le groupe de ressources que vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="3d887-289">Create the App Service web app, which represents the actual todo app that will be running within the plan and resource group just created.</span></span> <span data-ttu-id="3d887-290">Vous pouvez considérer une application web comme synonyme d’un processus ou d’un conteneur et assimiler le plan à l’hôte de la machine virtuelle ou du conteneur sur lequel elle s’exécute.</span><span class="sxs-lookup"><span data-stu-id="3d887-290">You can think of a web app as being synonymous with a process or container, and the plan as being the virtual machine/container host that they're running on.</span></span> <span data-ttu-id="3d887-291">En outre, dans le cadre de la création de l’application web, vous devez la configurer pour utiliser l’image Docker que vous avez publiée sur DockerHub :</span><span class="sxs-lookup"><span data-stu-id="3d887-291">Additionally, as part of creating the web app, you'll need to configure it to use the Docker image you published to DockerHub:</span></span>

    ```shell
    az webapp create -n nina-demo-app -p nina-demo-plan -i lostintangent/node
    ``` 

    > [!NOTE]
    > <span data-ttu-id="3d887-292">Si vous préférez un déploiement Git plutôt que d’utiliser un conteneur personnalisé, consultez l’article [Créer une application web Node.js dans Azure](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-nodejs#configure-to-use-nodejs).</span><span class="sxs-lookup"><span data-stu-id="3d887-292">If instead of using a custom container, you'd prefer a Git deployment, refer to the article, [Create a Node.js web app in Azure](https://docs.microsoft.com/azure/app-service-web/app-service-web-get-started-nodejs#configure-to-use-nodejs).</span></span>

5. <span data-ttu-id="3d887-293">Définissez l’application web en tant qu’instance web par défaut :</span><span class="sxs-lookup"><span data-stu-id="3d887-293">Set the web app as the default web instance:</span></span>

    ```shell
    az configure -d web=nina-demo-app
    ```

6. <span data-ttu-id="3d887-294">Lancez l’application pour afficher le conteneur déployé qui est disponible sur une URL `*.azurewebsites.net` :</span><span class="sxs-lookup"><span data-stu-id="3d887-294">Launch the app to view the deployed container, which will be available at an `*.azurewebsites.net` URL:</span></span>

    ```shell
    az webapp browse
    ```

    ![Application de tâches en cours d’exécution dans le navigateur](./media/node-howto-e2e/browse-app.png)

    > [!NOTE]
    > <span data-ttu-id="3d887-296">Le premier chargement de l’application peut prendre quelques minutes étant donné qu’App Service doit extraire l’image Docker de DockerHub puis la démarrer.</span><span class="sxs-lookup"><span data-stu-id="3d887-296">It may take few minutes to load app the first time as App Service has to pull the Docker image from DockerHub and then start it.</span></span>

<span data-ttu-id="3d887-297">À ce stade, vous venez de déployer et d’exécuter l’application de tâches.</span><span class="sxs-lookup"><span data-stu-id="3d887-297">At this point, you've just deployed and run the todo app.</span></span> 

<span data-ttu-id="3d887-298">Vous avez maintenant déployé l’application de tâches.</span><span class="sxs-lookup"><span data-stu-id="3d887-298">You have now deployed the todo app.</span></span> <span data-ttu-id="3d887-299">L’icône qui tourne indique cependant que l’application ne peut pas se connecter à la base de données.</span><span class="sxs-lookup"><span data-stu-id="3d887-299">However, the spinning icon indicates that the app can't connect to the database.</span></span> <span data-ttu-id="3d887-300">Cela est dû au fait que vous avez utilisé une instance locale de MongoDB pendant le développement, qui n’est évidemment pas accessible à partir des centres de données Azure.</span><span class="sxs-lookup"><span data-stu-id="3d887-300">This is due to the fact that you were using a local instance of MongoDB during development, which obviously isn't reachable from within the Azure datacenters.</span></span> <span data-ttu-id="3d887-301">Étant donné que vous avez modifié l’application pour accepter la chaîne de connexion via une variable d’environnement, il vous suffit de démarrer un serveur MongoDB et de reconfigurer l’instance App Service pour faire référence à la variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="3d887-301">Since you modified the app to accept the connection string via an environment variable, you need only to start a MongoDB server and re-configure the App Service instance to reference the environment variable.</span></span> <span data-ttu-id="3d887-302">Ce point est illustré dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="3d887-302">This is illustrated in the next section.</span></span>

## <a name="provisioning-a-mongodb-server"></a><span data-ttu-id="3d887-303">Approvisionnement d’un serveur MongoDB</span><span class="sxs-lookup"><span data-stu-id="3d887-303">Provisioning a MongoDB server</span></span>

<span data-ttu-id="3d887-304">Bien que vous puissiez configurer un serveur MongoDB ou un ensemble de réplicas et gérer cette infrastructure vous-même, Azure fournit une solution appelée [Cosmos DB](https://azure.microsoft.com/services/documentdb/).</span><span class="sxs-lookup"><span data-stu-id="3d887-304">While you could configure a MongoDB server, or replica set, and manage that infrastructure yourself, Azure provides a solution called [Cosmos DB](https://azure.microsoft.com/services/documentdb/).</span></span> <span data-ttu-id="3d887-305">Cosmos DB est une base de données NoSQL performante, entièrement gérée et géoréplicable, qui fournit une couche de compatibilité MongoDB.</span><span class="sxs-lookup"><span data-stu-id="3d887-305">Cosmos DB is a fully-managed, geo-replicable, high-performance, NoSQL database that provides a MongoDB-compatibility layer.</span></span> <span data-ttu-id="3d887-306">Cela signifie que vous pouvez y faire pointer une application MEAN existante (ou n’importe quel client/outil MongoDB comme [Studio 3P](https://studio3t.com/)) sans avoir à modifier quoi que ce soit, à l’exception de la chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="3d887-306">This means that you can point an existing MEAN app at it (or any MongoDB client/tool such as [Studio 3T](https://studio3t.com/)) without needing to change anything but the connection string.</span></span> <span data-ttu-id="3d887-307">Les étapes suivantes montrent comment procéder :</span><span class="sxs-lookup"><span data-stu-id="3d887-307">The following steps illustrate how this is done:</span></span>

1. <span data-ttu-id="3d887-308">À partir du terminal Visual Studio Code, exécutez la commande suivante pour créer une instance compatible MongoDB du service Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="3d887-308">From the Visual Studio Code terminal, run the following command to create a MongoDB-compatible instance of the Cosmos DB service.</span></span> <span data-ttu-id="3d887-309">Remplacez l’espace réservé **<NAME>** par une valeur globale unique (Cosmos DB utilise ce nom pour générer l’URL du serveur de base de données) :</span><span class="sxs-lookup"><span data-stu-id="3d887-309">Replace the **<NAME>** placeholder with a globally unique value (Cosmos DB uses this name to generate the database's server URL):</span></span>

   ```shell
   COSMOSDB_NAME=<NAME>
   az cosmosdb create -n $COSMOSDB_NAME --kind MongoDB
   ```

2. <span data-ttu-id="3d887-310">Récupérez la chaîne de connexion MongoDB pour cette instance :</span><span class="sxs-lookup"><span data-stu-id="3d887-310">Retrieve the MongoDB connection string for this instance:</span></span>

   ```shell
   MONGODB_URL=$(az cosmosdb list-connection-strings -n $COSMOSDB_NAME -otsv --query "connectionStrings[0].connectionString")
   ```

3. <span data-ttu-id="3d887-311">Mettez à jour la variable d’environnement **MONGODB_URL** de votre application web afin qu’elle se connecte à l’instance Cosmos DB nouvellement provisionnée au lieu d’essayer de se connecter à un serveur MongoDB qui s’exécute en local (et qui n’existe pas !) :</span><span class="sxs-lookup"><span data-stu-id="3d887-311">Update your web app's **MONGODB_URL** environment variable so that it connects to the newly provisioned Cosmos DB instance instead of attempting to connect to a locally running MongoDB server (that doesn't exist!):</span></span>

    ```shell
    az webapp config appsettings set --settings MONGODB_URL=$MONGODB_URL
    ```

4. <span data-ttu-id="3d887-312">Retournez dans votre navigateur et actualisez la page.</span><span class="sxs-lookup"><span data-stu-id="3d887-312">Return to your browser and refresh it.</span></span> <span data-ttu-id="3d887-313">Essayez d’ajouter et de supprimer un élément de tâche pour voir si maintenant l’application fonctionne sans avoir à modifier quoi que ce soit !</span><span class="sxs-lookup"><span data-stu-id="3d887-313">Try adding and removing a todo item to prove that the app now works without needing to change anything!</span></span> <span data-ttu-id="3d887-314">Définissez la variable d’environnement sur l’instance Cosmos DB créée, qui émule entièrement une base de données MongoDB.</span><span class="sxs-lookup"><span data-stu-id="3d887-314">Set the environment variable to the created Cosmos DB instance, which is fully emulating a MongoDB database.</span></span>

    ![Application de démonstration après connexion à une base de données](./media/node-howto-e2e/finished-demo.png)

<span data-ttu-id="3d887-316">Lorsque cela est nécessaire, vous pouvez revenir à l’instance Cosmos DB et augmenter (ou diminuer) le débit réservé dont a besoin MongoDB, puis tirer parti du trafic ajouté sans avoir à gérer d’infrastructure manuellement.</span><span class="sxs-lookup"><span data-stu-id="3d887-316">When needed, you can switch back to the Cosmos DB instance and scale up (or down) the reserved throughput that the MongoDB instance needs, and benefit from the added traffic without needing to manage any infrastructure manually.</span></span>

<span data-ttu-id="3d887-317">En outre, Cosmos DB indexe automatiquement chaque document et chaque propriété à votre place.</span><span class="sxs-lookup"><span data-stu-id="3d887-317">Additionally, Cosmos DB automatically indexes every single document and property for you.</span></span> <span data-ttu-id="3d887-318">De cette façon, vous n’avez pas besoin de profiler les requêtes lentes ou d’affiner manuellement vos index.</span><span class="sxs-lookup"><span data-stu-id="3d887-318">That way, you don't need to profile slow queries or manually fine-tune your indexes.</span></span> <span data-ttu-id="3d887-319">Il vous suffit d’approvisionner et de mettre à l’échelle au besoin, et laisser Cosmos DB gérer le reste.</span><span class="sxs-lookup"><span data-stu-id="3d887-319">Just provision and scale as needed, and let Cosmos DB handle the rest.</span></span>

## <a name="hosting-a-private-docker-registry"></a><span data-ttu-id="3d887-320">Hébergement d’un registre Docker privé</span><span class="sxs-lookup"><span data-stu-id="3d887-320">Hosting a private Docker registry</span></span>

<span data-ttu-id="3d887-321">DockerHub offre une expérience exceptionnelle pour la distribution de vos images de conteneur, mais certains scénarios impliquent d’héberger votre propre registre Docker privé, par exemple pour bénéficier d’avantages sur le plan de la sécurité, de la gouvernance ou des performances.</span><span class="sxs-lookup"><span data-stu-id="3d887-321">DockerHub provides an amazing experience for distributing your container images, but there may be scenarios where you'd prefer to host your own private Docker registry - such as for security/governance or performance benefits.</span></span> <span data-ttu-id="3d887-322">Azure intègre à cet effet [l’Azure Container Registry](https://azure.microsoft.com/services/container-registry/) (ACR), qui vous permet de lancer votre propre registre Docker dont le stockage de sauvegarde se trouve dans le même centre de données que celui de votre application web (ce qui rend les récupérations plus rapides).</span><span class="sxs-lookup"><span data-stu-id="3d887-322">For this purpose, Azure provides the [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) (ACR) that allows you to spin up your own Docker registry whose backing storage is located in the same data center as your web app (which makes pulls quicker).</span></span> <span data-ttu-id="3d887-323">L’ACR vous assure également un contrôle total sur le contenu et les contrôles d’accès, notamment sur les personnes autorisées à envoyer ou extraire des images.</span><span class="sxs-lookup"><span data-stu-id="3d887-323">The ACR also provides you with full control over the contents and access controls - such as who can push or pull images.</span></span> 

<span data-ttu-id="3d887-324">La commande suivante permet d’approvisionner un registre personnalisé.</span><span class="sxs-lookup"><span data-stu-id="3d887-324">Provisioning a custom registry can be accomplished by running the following command.</span></span> <span data-ttu-id="3d887-325">Remplacez l’espace réservé **<NAME>** par une valeur globale unique, puisque l’ACR utilise la valeur spécifiée pour générer l’URL du serveur de connexion du registre.</span><span class="sxs-lookup"><span data-stu-id="3d887-325">(Replace the **<NAME>** placeholder with a globally unique value as ACR uses specified value to generate the registry's login server URL.</span></span>

```shell
ACR_NAME=<NAME>
az acr create -n $ACR_NAME -l westus --admin-enabled
```

> [!NOTE]
> <span data-ttu-id="3d887-326">Bien que l’exemple de cette rubrique utilise le **compte d’administrateur** pour simplifier les choses, cela n’est pas recommandé pour les registres de production.</span><span class="sxs-lookup"><span data-stu-id="3d887-326">While this topic's example uses the **admin account** to keep things simple, it is not recommended for production registries.</span></span> 

<span data-ttu-id="3d887-327">Les commandes `az acr create` affichent l’URL du serveur de connexion (via la colonne `LOGIN SERVER`) que vous utilisez pour vous connecter à l’aide de l’interface CLI Docker (par exemple, `ninademo.azurecr.io`).</span><span class="sxs-lookup"><span data-stu-id="3d887-327">The `az acr create` commands displays the login server URL (via the `LOGIN SERVER` column) that you use to log in using the Docker CLI (e.g. `ninademo.azurecr.io`).</span></span> <span data-ttu-id="3d887-328">En outre, la commande génère des informations d’identification d’administrateur que vous pouvez utiliser pour vous authentifier.</span><span class="sxs-lookup"><span data-stu-id="3d887-328">Additionally, the command generates admin credentials that you can use in order to authenticate against it.</span></span> <span data-ttu-id="3d887-329">Pour récupérer ces informations d’identification, exécutez la commande suivante et notez le nom d’utilisateur et le mot de passe qui s’affichent :</span><span class="sxs-lookup"><span data-stu-id="3d887-329">To retrieve those credentials, run the following command and note the displayed username and password:</span></span>

```shell
az acr credential show -n $ACR_NAME
```

<span data-ttu-id="3d887-330">À l’aide des informations d’identification obtenues à l’étape précédente et de votre serveur de connexion individuel, vous pouvez vous connecter au registre en utilisant le workflow standard de la CLI Docker.</span><span class="sxs-lookup"><span data-stu-id="3d887-330">Using the credentials from the previous step, and your individual login server, you can log in to the registry using the standard Docker CLI workflow.</span></span>

```shell
docker login <LOGIN_SERVER> -u <USERNAME> -p <PASSWORD>
```

<span data-ttu-id="3d887-331">Vous pouvez désormais marquer votre conteneur Docker pour indiquer qu’il est associé à votre registre privé à l’aide de la commande suivante (en remplaçant `lostintangent/node` par le nom que vous avez attribué à l’image du conteneur).</span><span class="sxs-lookup"><span data-stu-id="3d887-331">You can now tag your Docker container to indicate that it's associated with your private registry using the following command (replacing `lostintangent/node` with the name you gave the container image.</span></span>

```shell
docker tag lostintangent/node <LOGIN_SERVER>/lostintangent/node
```

<span data-ttu-id="3d887-332">Pour finir, il ne vous reste plus qu’à envoyer l’image ainsi marquée à votre registre Docker privé.</span><span class="sxs-lookup"><span data-stu-id="3d887-332">Finally, push the tagged image to your private Docker registry.</span></span>

```shell
docker push <LOGIN_SERVER>/lostintangent/node
```

<span data-ttu-id="3d887-333">Votre conteneur est maintenant stocké dans votre propre registre privé, avec l’avantage d’avoir pu utiliser l’interface CLI Docker de la même façon qu’avec DockerHub.</span><span class="sxs-lookup"><span data-stu-id="3d887-333">Your container is now stored in your own private registry, and the Docker CLI was happy to allow you to continue working in the same way as you did when using DockerHub.</span></span> <span data-ttu-id="3d887-334">Pour indiquer à l’application web App Service une extraction depuis votre registre privé, il vous suffit d’exécuter la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="3d887-334">In order to instruct the App Service web app to pull from your private registry, you need only run the following command:</span></span>

```shell
az appservice web config container set \
    -r <LOGIN_SERVER> \
    -c <LOGIN_SERVER>/lostintangent/node \
    -u <USERNAME> \
    -p <PASSWORD> 
```

> [!NOTE]
> <span data-ttu-id="3d887-335">Assurez-vous d’ajouter le préfixe `https://` au début de l’option `-r`.</span><span class="sxs-lookup"><span data-stu-id="3d887-335">Make sure to add the `https://` prefix to the beginning of the `-r` option.</span></span> <span data-ttu-id="3d887-336">N’ajoutez pas en revanche le préfixe au nom de l’image de conteneur.</span><span class="sxs-lookup"><span data-stu-id="3d887-336">However, don't add the prefix to the container image name.</span></span>

<span data-ttu-id="3d887-337">Si vous actualisez l’application dans votre navigateur, tout doit normalement apparaître et fonctionner de la même manière.</span><span class="sxs-lookup"><span data-stu-id="3d887-337">If you refresh the app in your browser, everything should look and work the same.</span></span> <span data-ttu-id="3d887-338">Et pourtant, votre application est exécutée cette fois via votre registre Docker privé.</span><span class="sxs-lookup"><span data-stu-id="3d887-338">However, it's now running your app via your private Docker registry.</span></span> <span data-ttu-id="3d887-339">Une fois votre application mise à jour, marquez les modifications et envoyez-les comme indiqué ci-dessus, puis mettez à jour la balise dans la configuration de votre conteneur App Service.</span><span class="sxs-lookup"><span data-stu-id="3d887-339">Once you update your app, tag and push the changes as done above, and update the tag in your App Service container configuration.</span></span>

## <a name="configuring-a-custom-domain-name"></a><span data-ttu-id="3d887-340">Configuration d’un nom de domaine personnalisé</span><span class="sxs-lookup"><span data-stu-id="3d887-340">Configuring a custom domain name</span></span>

<span data-ttu-id="3d887-341">Si l’URL `*.azurewebsites.net` est très utile pour les tests, il peut arriver un moment où vous voudrez ajouter un nom de domaine personnalisé à votre application web.</span><span class="sxs-lookup"><span data-stu-id="3d887-341">While the `*.azurewebsites.net` URL is great for testing, at some point you may want to add a custom domain name to your web app.</span></span> <span data-ttu-id="3d887-342">Une fois que vous disposez d’un nom de domaine issu d’un bureau d’enregistrement, il vous suffit d’y ajouter un enregistrement `A` qui pointe sur l’adresse IP externe de votre application web (qui est en fait un équilibreur de charge).</span><span class="sxs-lookup"><span data-stu-id="3d887-342">Once you have a domain name from a registrar, you need only add an `A` record to it  that points at your web app's external IP (which is actually a load balancer).</span></span> <span data-ttu-id="3d887-343">Vous pouvez récupérer cette adresse IP en exécutant la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="3d887-343">You can retrieve this IP by running the following command:</span></span>

```shell
az webapp config hostname get-external-ip
```

<span data-ttu-id="3d887-344">Pour ajouter un enregistrement `A`, vous devez également ajouter un enregistrement `TXT` à votre domaine qui pointe vers le domaine `*.azurewebsites.net` que vous utilisiez jusqu’ici.</span><span class="sxs-lookup"><span data-stu-id="3d887-344">In addition to add an `A` record, you also need to add a `TXT` record to your domain that points at the `*.azurewebsites.net` domain you've been using thus far.</span></span> <span data-ttu-id="3d887-345">L’association des enregistrements `A` et `TXT` permet à Azure de vérifier que vous êtes le propriétaire du domaine.</span><span class="sxs-lookup"><span data-stu-id="3d887-345">The combination of the `A` and `TXT` records allows Azure to verify that you own the domain.</span></span>

<span data-ttu-id="3d887-346">Une fois ces enregistrements créés (et une fois que les modifications DNS ont été propagées), enregistrez le domaine personnalisé auprès d’Azure afin qu’il sache recevoir correctement le trafic entrant.</span><span class="sxs-lookup"><span data-stu-id="3d887-346">Once those records are created - and the DNS changes have propagated - register the custom domain with Azure so that it knows to expect the incoming traffic correctly.</span></span> 

```shell
az webapp config hostname add --hostname <DOMAIN>
```

> [!NOTE]
> <span data-ttu-id="3d887-347">La commande ne fonctionnera pas tant que les modifications DNS n’auront pas été propagées.</span><span class="sxs-lookup"><span data-stu-id="3d887-347">The command will not work until the DNS changes have propagated.</span></span>

<span data-ttu-id="3d887-348">Ouvrez un navigateur et accédez à votre domaine personnalisé : vous constaterez qu’il correspond désormais à votre application déployée sur Azure.</span><span class="sxs-lookup"><span data-stu-id="3d887-348">Open a browser and navigate to your custom domain to see that it now resolves to your deployed app on Azure.</span></span>

## <a name="scaling-up-and-out"></a><span data-ttu-id="3d887-349">Montée en puissance et augmentation de la taille des instances</span><span class="sxs-lookup"><span data-stu-id="3d887-349">Scaling up and out</span></span>

<span data-ttu-id="3d887-350">Dans certains cas, votre application web peut devenir populaire au point que ses ressources allouées (processeur et mémoire RAM) ne suffisent plus à gérer l’augmentation du trafic et des exigences opérationnelles.</span><span class="sxs-lookup"><span data-stu-id="3d887-350">At some point, your web app may become popular enough that its allocated resources (CPU and RAM) aren't sufficient for handling the increase in traffic and operational demands.</span></span> <span data-ttu-id="3d887-351">Le plan App Service que vous avez créé précédemment (**B1**) est fourni avec 1 cœur de processeur et 1,75 Go de RAM, qui peuvent s’épuiser assez rapidement.</span><span class="sxs-lookup"><span data-stu-id="3d887-351">The App Service Plan that you created earlier (**B1**) comes with 1 CPU core and 1.75 GB of RAM, which can get maxed out fairly quickly.</span></span> <span data-ttu-id="3d887-352">Le plan **B2** prévoit deux fois plus de RAM et de processeur. Aussi, si vous remarquez que votre application commence à manquer de l’un ou l’autre, vous pouvez augmenter la puissance de la machine virtuelle sous-jacente en exécutant la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="3d887-352">The **B2** plan come swith twice as much RAM and CPU, so if you notice that your app is beginning to run out of either, you can scale up the underlying virtual machine by running the following command:</span></span>

```shell
az appservice plan update -n nina-demo-plan --sku B2
```

> [!NOTE]
> <span data-ttu-id="3d887-353">Pour accéder aux détails tarifaires et aux spécifications des plans Azure App, consultez l’article [Tarification App Service](https://azure.microsoft.com/pricing/details/app-service/)</span><span class="sxs-lookup"><span data-stu-id="3d887-353">For Azure App Plan pricing details and specs, see the article, [App Service Pricing](https://azure.microsoft.com/pricing/details/app-service/)</span></span>

<span data-ttu-id="3d887-354">Après quelques instants, votre application web est migrée vers le matériel demandé et vous pouvez commencer à tirer parti des ressources associées.</span><span class="sxs-lookup"><span data-stu-id="3d887-354">After just a few moments, your web app will be migrated to the requested hardware, and can begin taking advantage of the associated resources.</span></span> <span data-ttu-id="3d887-355">Outre la montée en puissance, vous pouvez également effectuer une descente en puissance en exécutant la même commande que ci-dessus, en spécifiant une option `--sku` qui fournit moins de ressources à un prix inférieur.</span><span class="sxs-lookup"><span data-stu-id="3d887-355">In addition to scaling up, you can also scale down by running the same command as above, specifying a `--sku` option that provides less resources at a lower price.</span></span> 

<span data-ttu-id="3d887-356">Au-delà de la montée en puissance des spécifications de la machine virtuelle, tant que votre application web est sans état, vous avez également la possibilité *d’augmenter la taille des instances* en ajoutant davantage d’instances de machines virtuelles sous-jacentes.</span><span class="sxs-lookup"><span data-stu-id="3d887-356">In addition to scaling up the virtual machine specs, as long as your web app is stateless, you also have the option to *scale out* by adding more underlying virtual machine instances.</span></span> <span data-ttu-id="3d887-357">Puisque le plan App Service créé précédemment ne comportait qu’une seule machine virtuelle (un *rôle de travail*), tout le trafic entrant est finalement soumis aux limites des ressources disponibles de cette instance.</span><span class="sxs-lookup"><span data-stu-id="3d887-357">The App Service Plan you created earlier included only a single virtual machine (a *worker*), and therefore, all incoming traffic is ultimately bound by the limits of the available resources of that one instance.</span></span> <span data-ttu-id="3d887-358">Si vous souhaitez ajouter une deuxième instance de machine virtuelle, vous pouvez exécuter la même commande que précédemment, cette fois non pas en augmentant la puissance de la référence SKU, mais en augmentant le nombre d’instances de machines virtuelles de travail.</span><span class="sxs-lookup"><span data-stu-id="3d887-358">If you want to add a second virtual machine instance, you could run the same command you ran earlier, but instead of scaling up the SKU, you scale out the number of worker virtual machines.</span></span>

```shell
az appservice plan update -n nina-demo-plan --number-of-workers 2
```

<span data-ttu-id="3d887-359">Lorsque vous augmentez la taille des instances de cette manière pour une application web, la charge du trafic entrant sera équilibrée en toute transparence entre toutes les instances, ce qui vous permet d’augmenter immédiatement votre capacité sans la moindre modification de code et sans avoir à vous préoccuper de l’infrastructure nécessaire.</span><span class="sxs-lookup"><span data-stu-id="3d887-359">When you scale out a web app like this, incoming traffic will be transparently load balanced between all instances, which allows you to immediately increase your capacity without any code changes or worrying about the needed infrastructure.</span></span> 

<span data-ttu-id="3d887-360">Les applications web sans état sont considérées comme une meilleure pratique, car elles permettent une mise à l’échelle (montée en puissance, descente en puissance, augmentation de la taille des instances) totalement déterministe puisque aucune machine virtuelle ou instance de l’application ne contient l’état nécessaire à son fonctionnement.</span><span class="sxs-lookup"><span data-stu-id="3d887-360">Stateless web apps are considered a best practice as they make the ability to scale them (up, down, out) entirely deterministic as no single virtual machine or app instance includes state that is neccessary in order to function.</span></span> 

> [!NOTE]
> <span data-ttu-id="3d887-361">Bien que le didacticiel de cette rubrique illustre l’exécution d’une simple application web dans le cadre d’un plan App Service, vous pouvez créer et déployer plusieurs applications web dans le même plan, de manière à approvisionner un seul plan et à être facturé en conséquence.</span><span class="sxs-lookup"><span data-stu-id="3d887-361">While this topic's tutorial illustrates running a single web app as part of an App Service Plan, you can create and deploy multiple web apps into the same plan, allowing you to provision and pay for a single plan.</span></span> 

## <a name="clean-up"></a><span data-ttu-id="3d887-362">Nettoyage</span><span class="sxs-lookup"><span data-stu-id="3d887-362">Clean-up</span></span>

<span data-ttu-id="3d887-363">Pour vous éviter de payer pour les ressources Azure que vous n’utilisez pas, exécutez la commande suivante à partir de votre terminal Visual Studio Code pour supprimer toutes les ressources approvisionnées au cours de ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="3d887-363">To ensure that you don't get charged for any Azure resources you aren't using, run the following command from your Visual Studio Code terminal to delete all of the resources provisioned during this tutorial.</span></span>

```shell
az group delete
```

> [!NOTE]
> <span data-ttu-id="3d887-364">Le processus de nettoyage peut prendre plusieurs minutes.</span><span class="sxs-lookup"><span data-stu-id="3d887-364">The clean-up process can take several minutes to complete.</span></span> 

<span data-ttu-id="3d887-365">Une fois que vous avez terminé, la commande `az group delete` vous permet de quitter votre compte Azure dans l’état où il se trouvait avant le début de ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="3d887-365">Once finished, the `az group delete` command leaves your Azure account in the same state it was before you started the tutorial.</span></span> <span data-ttu-id="3d887-366">Les groupes de ressources présentent notamment l’avantage de pouvoir organiser, déployer et supprimer des ressources Azure en bloc.</span><span class="sxs-lookup"><span data-stu-id="3d887-366">The ability to organize, deploy, and delete Azure resources as a single unit is one of the primary benefits of resource groups.</span></span> <span data-ttu-id="3d887-367">Il est donc recommandé de regrouper les ressources qui auront vraisemblablement la même durée de vie.</span><span class="sxs-lookup"><span data-stu-id="3d887-367">Therefore, as a recommended practice,  you should group your resources together that you anticipate having the same lifespan.</span></span>