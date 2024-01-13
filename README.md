# WeChall
##comment entrer dans le challenge :
- s'enregistrer avec le bouton **s'enregistrer**
- créer son compte ssh en créant un mot de passe ssh sur **(re)set your ssh password**
- on peut alors se connecter via *ssh -p 19198 VotreNomUtilisateur@warchall.net* qui est fournie par le site We Chall
- ouvrir un terminal : un CMD ou aller sur putty
pour mon cas je suis allé sur putty avec VMWare allumé et je me suis d'abord connecté en mode superutilisateur
- se connecter sur le terminal et entrer le mot de passe ssh pour entrer 

##level00:
- après la connexion, on se retrouve tout de suite sur notre répertoire personnel
> jennifer@warchall:~$
- avec **ls** on regarde ce qu'il y a à l'intérieur 
- il y avait un fichier WELCOME.md qui annonce grâce à **cat WELCOME.md** que les solutions se trouvent dans le dossier */home/level ou /home/user/yournick/level*
- donc on fait **cd /home/level** pour accéder au dossier
- à l'intérieur, on entre avec **cd 00_WELCOME** dans le dossier 00_welcome dans laquel se trouve un fichier README.md
- en faisant **cat README.md**, on trouve la solution

##level01:
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

##level02:
- dans /home/level, on entre dans le dossier 02 et dedans en faisant **ls** on tombe sur des dossiers qui ne contiennent pas la solution mais informe qu'on est bien en *level02*
- donc on execute la commande **ls -al**
- on peut par la suite trouver un dossier caché appellé .porb et y entrer par **cd .porb**
- en faisant **ls -al** dans ce dossier, on peut trouver un fichier .solution
- en faisant **cat .solution**, on obtient la solution
