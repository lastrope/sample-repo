Bon usage de GIT : 15/04/2014
===============================

http://nvie.com/posts/a-successful-git-branching-model/

***********
*** Créer un repo sur git hub
Voir https://help.github.com/articles/create-a-repo

***********
*** S'identifier  (--global = valable pour toute la machine. Sans --global, valable pour le repo locale seulement)
$ git config --global user.name "yginieys"
$ git config --global user.email "yginieys@stepnet.fr"

***********
*** Créer un repo local
$ mkdir sample-repo
$ cd sample-repo
$ git init
$ git add *
$ git commit -m 'first commit'

***********
*** Pusher dans un repo distant
# créer un repo "origin" sur le serveur
$ git remote add origin https://github.com/yginieys/sample-repo.git  
# Envoyer le commit dans la branche master de origin
$ git push -u origin master