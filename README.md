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
- en faisant **cat README.md**, on trouve la solution à l'intérieur de deux côtes