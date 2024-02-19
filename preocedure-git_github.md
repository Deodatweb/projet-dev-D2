---

Author: Alain ORLUK  
Formation : Développeur Web & Web mobile - Client CEF
Lieu: E-learning
Date : 06/02/2024  

---
# **COMMENT BIEN PRATIQUER GIT**

1. Créer le nouveau dépôt sur le compte GitHub. Pour l'exemple, nous l'appellerons **projet-dev**
Une fois le dépôt créé, GitHub vous fournit notamment un script sous la forme de cette liste de commandes :

    ```bash
    echo "# projet-dev" >> README.md
    git init
    git add README.md
    git commit -m "first commit"
    git branch -M main
    git remote add origin git@github.com:pseudoDeVotreCompteGithub/projet-dev.git
    git push -u origin main
    ```

2. Il faut alors vous rendre dans votre explorateur et créer un dossier pour le projet. Nommez ce dossier **projet-dev**, du même nom donc que le dépôt GitHub, ce sera plus pratique.

3. Une fois ceci fait, ouvrez ce dossier dans Visual Studio Code.

4. Ouvrez une session de  Terminal dans Visual Studio Code (raccourci **Ctrl + ù** sur Windows ou **Cmd + `**sur Mac).

5. Copiez/collez la première ligne puis exécutez la commande en appuyant sur **ENTRÉE**.  
Cette commande sert à créer un fichier README.md dans le dossier de votre projet.  
En effet il n'est pas possible de configurer le versioning Git d'un projet vide.

6. La commande `git init` sert à initialiser le versioning dans le dossier courant.  
Cette commande créé donc un dossier **.git** (caché par défaut) qui contiendra tout ce qui a trait au versioning du projet.
Avant de poursuivre, vous pouvez taper la commande `git status`.  
Vous y verrez apparaitre une mention du fichier README.md affichée en rouge.  
Cela signifie que l'outil Git est bien initialisé mais que les fichiers du projet n'ont pas encore été ajoutés dans son système.

7. la commande `git add README.md` permet justement d'ajouter le fichier README.md au "système" Git.  
Par la suite vous pourrez utiliser la commande `git add .` qui ajoute à la volée TOUS les éléments qui ne sont pas inclus dans le système Git.  
Une fois cette commande validée, vous pourrez confirmer la prise en compte du contenu en relançant la commande `git status`.  
La mention du fichier READM.md est désormais affichée en vert, signe que Git a intégré le fichier à son système.

8. La commande `git commit -m "first commit"`, pour schématiser, prend une photo instantanée de l'état du projet, c'est à dire de tout ce que contiennent tous les dossiers et fichiers à l'intérieur du dossier **projet-dev** (vous verrez ultérieurement que l'on peut d'ailleurs exclure certains dossiers et types de fichier du système Git).  
Cette "photo", que l'on appelle donc un **commit**, sera porteur d'un identifiant unique, d'une date, d'un titre et contiendra aussi une "image" de tout le contenu. Ici le titre sera le texte renseigné entre les guillemets, ici **first commit**.  
Une fois la commande validée, je vous invite à relancer la commande `git status`. Elle génèrera ce message :

    ```bash
    On branch master
    nothing to commit, working tree clean
    ```

    Ce qui m'amène à expliquer la commande suivante.  

    NB : Il se peut que lors de l'exécution de la commande `git commit -m "first commit`, Git vous renvoie une erreur et vous invite à y remédier en configurant les paramètres globaux :

    ```bash
    git config --global user.name "John Doe"
    git config --global user.email johndoe@example.com
    ```

    Dans ce cas il vous suffira d'exécuter chacune des commandes l'une après l'autre en renseignant votre **nom** et votre propre **adresse email**.

9. La commande suivante permet de renommer la **branche principale** déclarée dans le système Git.  
Une branche est un espace de travail indépendant des autres branches au sein d'un projet.  
Par exemple, si depuis la branche principale **main**, je créé une autre branche **dev-html** et que je bascule dedans (nous verrons plus loin comment faire cela, ne le faites pas encore), cette nouvelle branche contiendra tout ce que contenait la branche **main** au moment où je l'ai créée.  
Dès cet instant, si j'ajoute du contenu dans le projet, ce contenu n'existera que pour la branche **dev-html**. La branche **main** ne sera pas affectée par ces changements.  
Je vous ai dit que la commande qui suivait permettait de renommer la branche principale.  
Pourquoi doit-on faire cela ? Parce que lorsque vous créez un dépôt sur GitHub, celui-ci contiendra une branche principale nommée **main** par défaut.  
Or lorsque vous initialisez Git via la commande `git init`, Git créé une branche principale qu'il nomme **master**.  
Pour que les 2 branches, celle du dépôt GitHub et celle du système Git local (sur votre PC) soient identiques, on renomme la branche locale. C'est ce que permet de faire la commande `git branch -M main`.  
D'ailleurs si exécutez la commande puis que vous rappelez ensuite la commande `git status`, vous verrez ceci s'afficher :

    ```bash
    On branch main
    nothing to commit, working tree clean
    ```

    La branche a bien été renommée en **main**.

10. La commande suivante peut présenter 2 formes différentes selon la méthode d'identification GitHub que vous avez configuré dans votre compte.  
`git remote add origin git@github.com:pseudoDeVotreCompteGithub/projet-dev.git`  ou `git remote add origin https://github.com/pseudoDeVotreCompteGithub/projet-dev.git`.  
Les 2 commandez ont le même effet. Utilisez donc celle qui vous est proposée par défaut.  
Cette commande permet de lier le système Git au dépôt GitHub que vous avez créé initialement.  

11. La dernière commande permet de "pousser" (`push`) le contenu de la branche locale actuelle dans la même branche du dépôt GitHub.  

Une fois que la commande est terminée, vous devriez voir s'afficher quelque chose de cet ordre (pas 100% identique) après l'exécution de la commande :

```bash
Enumerating objects: 74, done.
Counting objects: 100% (74/74), done.
Delta compression using up to 8 threads
Compressing objects: 100% (71/71), done.
Writing objects: 100% (74/74), 3.29 MiB | 1.47 MiB/s, done.
Total 74 (delta 2), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (2/2), done.
To https://github.com/pseudoDeVotreCompteGithub/projet-dev.git
 * [new branch]      main -> main
branch 'main' set up to track 'origin/main'.
```

Cela indique que tout s'est bien déroulé.  
Maintenant retournez sur le dépôt GitHub et rechargez la page.  
La page des scripts des commandes ne s'affiche plus et à la place est affiché le contenu de la branche **main** du dépôt, c'est à dire un fichier nommé README.md.  

Tout est prêt pour pouvoir travailler en mode "versioning" à présent.  

Comment coder le projet à présent ?  

En commençant par créer une branche de travail. En effet et c'est très important de bien le retenir, **ON NE CODE JAMAIS DANS LA BRANCHE `main`**.  
Vous allez donc commencer à coder la structure HTML de votre application.  
Avant de créer, une nouvelle branche, voyons si nous sommes bien dans la branche **main**.  
Retournez donc dans le terminal de Visual Studio Code et exécutez la commande `git branch`.  
Ceci s'affiche :

```bash
* main 
```

Avec **main** affiché en vert. Cela signifie que vous êtes actuellement dans cette branche.  
Créons donc une autre branche.  

Créez une nouvelle branche que vous appellerez par exemple **dev-html** (nommez-les  toujours sans espaces ni majuscules ou accents).  
Pour ce faire, exécutez la commande :

```bash
git branch dev-html
```

La branche est crée. Il suffit pour cela de relancer la commande `git branch`.  
Ceci s'affiche :

```bash
  dev-html
* main
```

La branche est bien créée. Profitez-en pour vous rendre sur le dépôt GitHub et créer une **issue** qui portera le même nom que votre branche (par simple souci de cohérence,).  
Avant de commencer à coder le HTML, il faut d'abord "basculer" dans la branche **dev-html**.  

Pour ce faire, exécutez la commande `git checkout dev-html`.  
Ceci s'affichera :

```bash
Switched to branch 'dev-html'
```

Cela confirme que vous avez basculé dans la branche **dev-html**.  
Vous pouvez modifier le projet et ajouter le fichier  `index.html` (nommez **TOUJOURS** le fichier principal de votre site ainsi).  
Puis vous allez commencer à coder la structure de la page.  

Régulièrement il vous faudra ajouter les modifications au système Git.  
Par exemple lorsque vous aurez codé la structure du `<header>`, vous pourrez enregistrer cela dans Git en exécutant dans le terminal la commande `git add .`  
Puis vous prendrez une photo de l'état du code en ajoutant un commit via `git commit -m "structure du header"`.
Vous pourrez poursuivre votre travail en codant alors l'élément `<main>`, en ajoutant des commit intermédiaires si nécessaires puis lorsque l'élément `<main>` sera terminé, enregistrer avec `git add .` puis `git commit -m "structure du main"`.  

Puis en fin de journée, vous n'avez pas encore terminé de coder tout le HTML mais décidez de vous arrêter de travailler et reprendrez demain.  
Avant de couper votre ordinateur, vous allez devoir synchroniser le dépôt GitHub avec le projet puisque vous avez ajouté du contenu en local sur le projet.  

Pour ce faire vous allez devoir "pousser" le contenu de la branche **dev-html** dans le dépôt.  
En théorie pour faire cela il suffit d'exécuter la commande `git push`.  
Cependant si vous tentez d'exécuter cette commande, un message d'erreur s'affichera :

```bash
fatal: The current branch dev-html has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin dev-html

To have this happen automatically for branches without a tracking
upstream, see 'push.autoSetupRemote' in 'git help config'.
```

Pourquoi cette erreur ? Ici Git vous dit que la branche que vous voulez pousser n'existe pas sur le dépôt ("*The current branch dev-html has no upstream branch*").  
En effet vous avez créé la branche dev-html sur votre PC mais pas sur le dépôt "distant" (GitHub).  
Heureusement Git est bien fait et vous indique quelle commande il faut utiliser pour remédier à ce problème :

```bash
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin dev-html
```

Exécutez donc la commande `git push --set-upstream origin dev-html`.

Pour vérifier que tout s'est bien déroulé, rendez-vous sur le dépôt GitHub et rechargez la page.  
Vous devriez à présent y trouver 2 branches sur le dépôt, **main** et **dev-html**, chacune avec un contenu différent.  

Admettons maintenant que vous ayez poussé la branche **dev-html** et que vous ayez terminé de coder toute la structure HTML.  

Avant de poursuivre le développement de votre application et de passer le cas échant aux CSS, il va falloir intégrer le code de la branche **dev-html** dans la branche **main**.  
Pour cela il va falloir fusionner **dev-html** dans **main** grâce à une **pull request**.  

Vous verrez que GitHub est intelligent et vous le propose via un bouton vert intitulé **Compare & pull request**.  
Ce bouton n'apparaitra sur le dépôt qu'à la condition que celui-ci contienne 2 branches dont le contenu est différent.  
Cliquez sur le bouton, suivez la procédure et si aucun conflit n'a été détecté (dans le cas contraire, bon courage mais c'est une autre histoire:grin: ), la procédure devrait se terminer par un encadré sur la page qui stipulera :  
"**Pull request successfully merged and closed**".  

Le contenu de la branche **dev-html** a bien été fusionné dans la branche **main**, qui contient à présent ce qu'elle contenait avant la fusion ***PLUS*** ce que la branche **dev-html** contenait.  

La branche **main** est donc maintenant à jour et vous pouvez supprimer la branche **dev-html** sur le dépôt GitHub ET sur votre PC.  
PS : Profitez-en aussi pour clôturer l'issue dédiée sur le dépôt GitHub.  

Pour la supprimer sur le projet sur votre ordinateur, voici comment procéder :

1. Sortez de la branche en basculant sur **main** via la commande `git checkout main`.

2. Supprimez la branche **dev-html** via la commande `git branch -D dev-html`.
Une confirmation s'affichera :

    ```bash
    Deleted branch dev-html (was …)
    ```

3. Vérifiez qu'il ne reste que la branche main via la commande `git branch`.

Vous voilà prêt pour recréer une autre branche pour commencer à travailer sur les CSS.  

**NON, NON, NON, PAS ENCORE !!!**

En effet si la branche **main** de votre dépôt GitHub contient bien tout le code de l'ancienne branche **dev-html**, la branche **main** sur votre ordinateur est toujours dans le même état qu'à l'origine lorsque vous avez initialisé Git.  
Avant de créer une nouvelle branche de travail, il faut d'abord récupérer la version actuelle de **main** sur le dépôt GitHub.  
Pour ce faire il faut exécuter la commande `git pull` ("tirer") qui permet de prendre le contenu de la branche du dépôt GitHub et de la rapatrier dans votre ordinateur sur le projet.  

Vous pouvez maintenant depuis la branche **main** *À JOUR* créer une autre branche, par exemple **dev-css**, basculer dedans et commencer à coder les CSS.  

Avec ce gros tutorial, vous devriez mieux vous en sortir et j'espère mieux comprendre le fonctionnement du versioning.  
