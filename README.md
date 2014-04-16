Bon usage de GIT : 15/04/2014
===============================
Repository de test pour expérimenter :
http://nvie.com/posts/a-successful-git-branching-model/

- **origin / master** : branche contenant les releases de production. Utilisation de tags pour définir les *versions*.
- **origin / develop** : branche contenant les développements en cours. Sert à intégrer les développements. *Automatic nightly builds*
- **_developper_ / feature-_name_** : branche contenant une feature en cours de developpement. (habituellement présente uniquement sur les postes de développeurs)
- *Rêgle:* feature **PEUT** être créée à partir de *develop*
- *Rêgle:* feature **DOIT** être fusionnée dans *develop*
- *Rêgle:* feature peut avoir n'importe quel nom excepté *master*, *develop*, *release-...*, *hotfix-...*
- **origin / release-_targetVersion_** : branche servant à la préparation de la prochaine version de production.
- *Rêgle:* release **PEUT** être créée à partir de *develop*
- *Rêgle:* release **DOIT** être fusionnée dans *develop* **ET** *master*
- *Rêgle:* release **DOIT** être nommée **release-_targetVersion_**
- *Rêgle:* le bon moment pour créer *release* est atteint lorsque la branche *develop* contient toutes le features (en cours de finalisation) qui doivent être livrées en production. Le numéro de version doit être fixé à ce moment là.
- **origin / hotfix-_targetVersion_** : branche servant à correction d'un bug majeur en production. La branche develop est instable et ne peut être utilisée pour la correction.
- *Rêgle:* hotfix **DOIT** être créée à partir de *master*
- *Rêgle:* hotfix **DOIT** être fusionnée dans *master* **ET** *develop* **OU** *release* si elle existe.

***********
## Créer un repo sur git hub
Voir https://help.github.com/articles/create-a-repo

### S'identifier  
(--global = valable pour toute la machine. Sans --global, valable pour le repo locale seulement)
> git config --global user.name "yginieys"

> git config --global user.email "yginieys@stepnet.fr"

### Créer un repo local
> mkdir sample-repo

> cd sample-repo

> git init

> git add *

> git commit -m 'first commit'

### Pusher dans un repo distant
créer un repo "origin" sur le serveur
> git remote add origin https://github.com/yginieys/sample-repo.git  

Envoyer le commit dans la branche master de origin
> git push -u origin master

### Gestion des tags
Voir les tags:
> git tag

Créer un tag local:
> git tag -a 0.1.0 -m 'Version 0.1.0'

Partager un tag sur origin:
> git push origin 0.1.0

Partager tous les tags sur origin:
> git push origin --tags

**********
## Branche feature
Créer une branche feature :
> git checkout -b myfeature develop

Inclure une feature terminée dans develop :
> git checkout develop  *(retour à la branche develop)*

> git merge --no-ff myfeature   *(fusion de myfeature dans develop)*

> git branch -d myfeature   *(cloture de myfeature)*

> git push origin develop   *(envoi des changements sur origin)*

**********
## Branche release
Créer une branche release :
> git checkout -b release-0.2.0 develop

> Mise au point de la version 0.2.0. Des fichiers sont modifiés dans la branche release.

> git commit -a -m "Finalization of 0.2.0"    *(Commit des fichiers)*

Terminer une branche release :
> git checkout master    *(switch dans master)*

> git merge --no-ff release-0.2.0    *(fusion de release dans master)*

> git tag -a 0.2.0    *(Tag de la version dans master)*

> git checkout develop    *(switch dans develop)*

> git merge --no-ff release-0.2.0    *(fusion de release dans develop)*

> git branch -d release-0.2.0   *(cloture de release)*

**********
## Branche hotfix
Créer une branche hotfix :
> git checkout -b hotfix-0.2.1 master

> Correction du bug dans hotfix

> git commit -a -m "Correctif 0.2.1"   *(commit du correctif dans hotfix)*

> git checkout master   *(retour dans master)*

> git merge --no-ff hotfix-0.2.1   *(Fusion de hotfix dans master)*

> git tag -a 0.2.1   *(Tag de la version dans master)*

> git checkout develop   *(retour dans develop **OU** release si elle existe)*

> git merge --no-ff hotfix-0.2.1    *(Fusion de hotfix dans develop **OU** release si elle existe)*

> git branch -d hotfix-0.2.1    *(cloture de hotfix)*

