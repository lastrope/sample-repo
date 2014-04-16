Bon usage de GIT : 15/04/2014
===============================
Repository de test pour exp�rimenter :
http://nvie.com/posts/a-successful-git-branching-model/

- **origin / master** : branche contenant les releases de production. Utilisation de tags pour d�finir les *versions*.
- **origin / develop** : branche contenant les d�veloppements en cours. Sert � int�grer les d�veloppements. *Automatic nightly builds*
- **_developper_ / feature-_name_** : branche contenant une feature en cours de developpement. (habituellement pr�sente uniquement sur les postes de d�veloppeurs)
- *R�gle:* feature **PEUT** �tre cr��e � partir de *develop*
- *R�gle:* feature **DOIT** �tre fusionn�e dans *develop*
- *R�gle:* feature peut avoir n'importe quel nom except� *master*, *develop*, *release-...*, *hotfix-...*
- **origin / release-_targetVersion_** : branche servant � la pr�paration de la prochaine version de production.
- *R�gle:* release **PEUT** �tre cr��e � partir de *develop*
- *R�gle:* release **DOIT** �tre fusionn�e dans *develop* **ET** *master*
- *R�gle:* release **DOIT** �tre nomm�e **release-_targetVersion_**
- *R�gle:* le bon moment pour cr�er *release* est atteint lorsque la branche *develop* contient toutes le features (en cours de finalisation) qui doivent �tre livr�es en production. Le num�ro de version doit �tre fix� � ce moment l�.


***********
## Cr�er un repo sur git hub
Voir https://help.github.com/articles/create-a-repo

### S'identifier  
(--global = valable pour toute la machine. Sans --global, valable pour le repo locale seulement)
> git config --global user.name "yginieys"

> git config --global user.email "yginieys@stepnet.fr"

### Cr�er un repo local
> mkdir sample-repo

> cd sample-repo

> git init

> git add *

> git commit -m 'first commit'

### Pusher dans un repo distant
cr�er un repo "origin" sur le serveur
> git remote add origin https://github.com/yginieys/sample-repo.git  

Envoyer le commit dans la branche master de origin
> git push -u origin master

### Gestion des tags
Voir les tags:
> git tag

Cr�er un tag local:
> git tag -a 0.1.0 -m 'Version 0.1.0'

Partager un tag sur origin:
> git push origin 0.1.0

Partager tous les tags sur origin:
> git push origin --tags

**********
## Branche feature
Cr�er une branche feature :
> git checkout -b myfeature develop

Inclure une feature termin�e dans develop :
> git checkout develop  *(retour � la branche develop)*

> git merge --no-ff myfeature   *(fusion de myfeature dans develop)*

> git branch -d myfeature   *(cloture de myfeature)*

> git push origin develop   *(envoi des changements sur origin)*

**********
## Branche release
Cr�er une branche release :
> git checkout -b release-0.2.0 develop

> Mise au point de la version 0.2.0. Des fichiers sont modifi�s dans la branche release.

> git commit -a -m "Finalization of 0.2.0"    *(Commit des fichiers)*

Terminer une branche release :
> git checkout master    *(switch dans master)*

> git merge --no-ff release-0.2.0    *(fusion de release dans master)*

> git tag -a 0.2.0    *(Tag de la version dans master)*

> git checkout develop    *(switch dans develop)*

> git merge --no-ff release-0.2.0    *(fusion de release dans develop)*

> git branch -d release-1.2   *(cloture de release)*





