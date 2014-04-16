Bon usage de GIT : 15/04/2014
===============================
Repository de test pour expérimenter :
http://nvie.com/posts/a-successful-git-branching-model/

- **origin/master** : branche contenant les releases de production. Utilisation de tags pour définir les *versions*.
- **origin/develop** : branche contenant les développements en cours. Sert à intégrer les développements. *Automatic nightly builds*
- **_developper_/feature-_name_** : branche contenant une feature en cours de developpement. (habituellement présente uniquement sur les postes de développeurs)
- *Rêgle:* feature **PEUT** être créée à partir de *develop*
- *Rêgle:* feature **DOIT** être fusionnée dans *develop*
- *Rêgle:* feature peut avoir n'importe quel nom excepté *master*, *develop*, *release-...*, *hotfix-...*

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

Créer un tag:
> git tag -a 0.1.0 -m 'Version 0.1.0'

**********
## Branche feature
Créer une branche feature :
> git checkout -b myfeature develop

