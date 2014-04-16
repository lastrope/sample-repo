Bon usage de GIT : 15/04/2014
===============================
Repository de test pour exp�rimenter :
http://nvie.com/posts/a-successful-git-branching-model/

- **origin/master** : branche contenant les releases de production. Utilisation de tags pour d�finir les *versions*.
- **origin/develop** : branche contenant les d�veloppements en cours. Sert � int�grer les d�veloppements. *Automatic nightly builds*
- **_developper_/feature-_name_** : branche contenant une feature en cours de developpement. (habituellement pr�sente uniquement sur les postes de d�veloppeurs)
- *R�gle:* feature **PEUT** �tre cr��e � partir de *develop*
- *R�gle:* feature **DOIT** �tre fusionn�e dans *develop*
- *R�gle:* feature peut avoir n'importe quel nom except� *master*, *develop*, *release-...*, *hotfix-...*

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

Cr�er un tag:
> git tag -a 0.1.0 -m 'Version 0.1.0'

**********
## Branche feature
Cr�er une branche feature :
> git checkout -b myfeature develop

