Bon usage de GIT : 15/04/2014
===============================
Repository de test pour exp�rimenter :
http://nvie.com/posts/a-successful-git-branching-model/

- **origin/master** : branche contenant les releases de production. Utilisation de tags pour d�finir les *versions*.
- **origin/develop** : branche contenant les d�veloppements en cours. Sert � int�grer les d�veloppements. *Automatic nightly builds*
- **_developper_/feature-_name_** : branche contenant une feature en cours de developpement. (habituellement pr�sente uniquement sur les postes de d�veloppeurs)
- Feature **PEUT** �tre cr��e � partir de *develop*
- Feature **DOIT** �tre fusionner dans *develop*

***********
## Cr�er un repo sur git hub
Voir https://help.github.com/articles/create-a-repo

***********
## S'identifier  
(--global = valable pour toute la machine. Sans --global, valable pour le repo locale seulement)
> git config --global user.name "yginieys"

> git config --global user.email "yginieys@stepnet.fr"

***********
## Cr�er un repo local
> mkdir sample-repo

> cd sample-repo

> git init

> git add *

> git commit -m 'first commit'

***********
## Pusher dans un repo distant
cr�er un repo "origin" sur le serveur
> git remote add origin https://github.com/yginieys/sample-repo.git  

Envoyer le commit dans la branche master de origin
> git push -u origin master

