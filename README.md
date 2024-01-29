# WeChall
##comment entrer dans le challenge :
- s'enregistrer avec le bouton **s'enregistrer**
- créer son compte ssh en créant un mot de passe ssh sur **(re)set your ssh password**
- on peut alors se connecter via *ssh -p 19198 VotreNomUtilisateur@warchall.net* qui est fournie par le site We Chall
- ouvrir un terminal : un CMD ou aller sur putty
pour mon cas je suis allé sur putty avec VMWare allumé et je me suis d'abord connecté en mode superutilisateur
- se connecter sur le terminal et entrer le mot de passe ssh pour entrer 

##Training: Warchall - The Beginning

###level00:
- après la connexion, on se retrouve tout de suite sur notre répertoire personnel
> jennifer@warchall:~$
- avec **ls** on regarde ce qu'il y a à l'intérieur 
- il y avait un fichier WELCOME.md qui annonce grâce à **cat WELCOME.md** que les solutions se trouvent dans le dossier */home/level ou /home/user/yournick/level*
- donc on fait **cd /home/level** pour accéder au dossier
- à l'intérieur, on entre avec **cd 00_WELCOME** dans le dossier 00_welcome dans laquel se trouve un fichier README.md
- en faisant **cat README.md**, on trouve la solution

###level01:
- dans /home/level, on entre dans le dossier 01_choice_tree avec **cd 01_choice_tree** 
- avec **ls** on peut y voir un fichier README.md mais la solution n'y était pas
- toujours à l'intérieur, il y avait aussi 3 dossiers et on entre dans le dossier blue, **cd blue** et puis on fait **ls**
- dans ce dossier il y avait un autre dossier hats et on peut y entrer avec **cd hats**
- dans ce dossier hats avec **ls**, il y avait un dossier solution et on y entre avec **cd solution**
- trois dossiers : black, grey et white s'affichait dans solution puis on entre dans grey avec **cd grey** car :
> DEEP IN YOUR HEART YOU SHOULD BECOME A **GRAY**HAT 
ALWAYS KEEP A JOKER.
- puis, à l'interieur avec un autre **ls** il y avait un dossier patience et on fait **cd patience**
- après on peut trouver le fichier SOLUTION.txt avec **ls**
- en faisant **cat SOLUTION.txt**, on obtient la solution

###level02:
- dans /home/level, on entre dans le dossier 02 et dedans en faisant **ls** on tombe sur des dossiers qui ne contiennent pas la solution mais informe qu'on est bien en *level02*
- donc on execute la commande **ls -al**
- on peut par la suite trouver un dossier caché appellé .porb et y entrer par **cd .porb**
- en faisant **ls -al** dans ce dossier, on peut trouver un fichier .solution
- en faisant **cat .solution**, on obtient la solution

###level03:
- en entrant dans le dossier /home/level/03 et en faisant **ls** dedans il n'y a rien 
- mais avec **ls -al**, on peut voir un dossier et un fichier .bash_history
- en faisant **cat .bash_history**, on accède au solution

###level04:
- en entrant dans le dossier /home/level/04_kwisatz$, on peut voir par **ls** un fichier README.nfo 
- à l'interieur de ce fichier, il y a une indication qui dit d'*aller dans notre ~ qui veut dire notre répertoire personnel*
- on execute alors **cd /home/user/TonNomUtilisateur**, pour moi c'était **cd /home/user/jennifer** pour accéder au répertoire personnel
- dedans on entre dans le dossier level
- puis à l'interieur on entre dans 04_kwisatz 
- en tapant sur **ls** on peut voir deux fichiers dont l'un README.txt nous conseillant d'*aller dans le fichier README2.md un fichier pour le moment inaccessible*
- en tapant **ls -al** on voit que on n'a aucun droit sur ce fichier 
- donc on utilise **chmod +r README2.md** pour au moins _lire le contenu du fichier README2.md_
- en revenant sur la commande **ls -al**, on peut constater que *le droit de lire le fichier a changé*
- puis avec **cat README2.md** on accède au solution

###level05:
- en entrant dans /home/level/05_privacy, on peut voir un fichier README.md
- en faisant **cat README.md**, on accède à la solution

##Warchall: Live LFI
- en cliquant sur Live LFI, on accède à un page web
- puis en entrant sur le code source de cette page on peut voir qu'il a deux liens assez similaires 
- et en cliquant sur l'un d'eux, on se retrouve dans la même page mais avec un URL différent et la langue de la page est : en anglais si on a un **URL=en**, en allemand si on a un **URL=de**
- d'après les precédentes challenges qu'on a vu, la solution est souvent stockée dans un fichier README ou solution
- si on essaie de changer **en** ou **de** en **solution.php** pour accéder à la solution, la solution n'y est pas encore 
-  on utilise donc un wrapper de php pour pouvoir lire l'intégralité du fichier solution.php en utilisant le codage en base64
>wrapper PHP : php://filter/convert.base64-encode/resource=solution.php
- on change le **en** ou **de** dans l'URL en ce wrapper PHP 
- une suite de caractères en sous forme d'ASCII s'affichent et on le copie
- on va dans un autre site qui permet de décoder un base64 et on cole dessus la suite de caractères
- on tape sur le bouton *decode* 
- le contenu intégral du fichier **solution.php** s'affiche et on peut trouver dedans à l'intérieur de **' '** la solution.

##Warchall: Live RFI
- En cliquant sur Live RFI, on accède à un page web
- puis en entrant sur le code source de cette page on peut voir qu'il a deux liens avec 2href
- si on clique sur le premier lien, on se retrouve dans la page précedente en anglais et si on clique sur le deuxieme lien, on se retrouve sur une page similaire mais en allemand. Tous deux avec des URL différents à partir du caractère **=** dans l'URL
- si on change en **solution.php** les caractères après **=**, on accède à une page mais la solution n'y est pas 
-  on utilise donc un wrapper de php pour pouvoir lire l'intégralité du fichier solution.php en utilisant le codage en base64
>wrapper PHP : php://filter/convert.base64-encode/resource=solution.php
- on remplace par ce wrapper PHP le contenu de l'URL après **=** 
- une suite de caractères en sous forme d'ASCII s'affichent et on le copie
- on va dans un autre site qui permet de décoder un base64 et on cole dessus la suite de caractères
- on tape sur le bouton *decode* 
- le contenu intégral du fichier **solution.php** s'affiche et on peut trouver dedans tout en bas en **'  '** la solution.

##Choose your Path
- après avoir analyser la fonction donnée sur le fichier charp.c, il retourne le nombre moyen de caractère par ligne d'un fichier donné
- cependant avec **ls -al** on peut voir que ce fichier ne peut pas être executé par d'autres utilisateurs
- contrairement à cela un autre fichier charp peut 
- on peut donc envisager une méthode similaire à l'injection pour avoir la solution avec :
>./charp "solution.txt | cat solution.txt > ~/solution10.txt"
- puis on affiche le contenu du fichier **solution10.txt** avec **cat /home/user/jennifer/solution10.txt** ou simplement avec **cat ~/solution10.txt**
- la solution ou notre flag se trouve dedans

##Choose your path2
- après avoir examiné la fonction dans le code source
- on peut créer un lien symbolique dans notre répertoire personnel avec :
> ln -s /bin/sh ~/wc
- puis on modifie la variable d'environnement afin d'inclure uniquement le répertoire personnel où se trouve notre lien symbolique **wc** avec :
> PATH=~ ./charp2 "/bin/cat solution.txt 1>&2" 
- la solution s'affiche