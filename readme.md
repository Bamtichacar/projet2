modif branch-a 
modif branch-b 


Exercice GIT base manip 

1/ crÃ©er un dossier de projet

Créer dans c:xampp:htdocs 

2/ crÃ©er 3 dossiers (html/css/js)

Idem

3/ crÃ©er les fichiers index.html, index.js et styles.css dans leurs dossiers respectifs

Dans vscode nvx file taper html.index , selectionner et on enregistre dans fichier de xampp htdocs le projet etc

4/ mettre a jour l'ensemble dans le dossier remote

Ouvrir mettre notre fichier dans vscode en open folder, créer folder puis open folder puis le bouton de gauche (celui de partage) et publish sur git

5/ crÃ©er une branche "dev"

Sur vscode en haut à côté de run les ... - terminal- nouveau terminal
Créer la branche dev : git checkout -b dev
puis bouton à gauche publish branch



6/ lister les branches

git branch
Liste les branches locales existantes. L'option -r permet de lister les branches distantes et l'option -a montre les branches locales et distantes.

 


7/ se positionner sur la branche dev

git switch branche
Échange les branches en mettant à jour l'ESPACE_DE_TRAVAIL et l'INDEX pour charger la BRANCHE spécifiée en positionnant la TÊTE dessus.

 



8/ modifier le fichier css 

Par exemple j'ai mis un fond bleu au h1 créé au préalable dans html



9/ mettre la modif a jour sur la branche dev

Dans le symbole partager appuyer commit et ok
attention de bien etre sur la branche dev
rajouter un commentaire pour la modif
ICI JAI NOTE MODIFICATION CSS POUR H1
puis le V pour valider

10/ revenir sur la branche master et ouvrir le fichier css (voit-on la modif ?)

NON (ps : la branche master c'est main)


11/ fusionner la branche dev sur la branche master

git merge commit ou branche
Fusionne les modifications du COMMIT ou de la BRANCHE dans la branche courante. Utilisez --no-commit pour ignorer les modifications n'ayant pas encore fait l'objet d'un commit.
=> se placer dans main et faire git merge dev

 

 


12/ verifier la modif css

Ok elles apparaissent


13/ retourner sur la branche dev et ajouter un fichier readme.md

pour changer de branche appuyer ici la ou il y a main

 

new file readme.md et enregistrer dans projet



14/ faire un commit de ce fichier 

LE COMMENTAIRE QUE J AI MIS 
CREATION FICHIER readme.md



15/ visualiser les differences avec la commande adÃ©quate

AVANT SYNCHRONOSATION :
git diff
Affiche les différences entre l'ESPACE_DE_TRAVAIL et l'INDEX.
espace de travail est dev
index est main
=> git diff dev main

 

On dirait que vous regardez une sortie diff d’un système de contrôle de version (comme Git) indiquant la suppression d’un fichier. Plus précisément, le fichier readme.md a été supprimé. Voici une ventilation de la sortie de diff :

 'diff --git a/readme.md b/readme.md' : Cette ligne montre la comparaison entre deux versions du fichier 'readme.md', avec 'a/' représentant la version précédente et 'b/' représentant la nouvelle version.
  
 'mode fichier supprimé 100644' : cela indique que le mode du fichier supprimé était '100644', ce qui est un mode de fichier typique pour un fichier normal avec des autorisations de lecture et d’écriture pour le propriétaire, et des autorisations de lecture pour le groupe et autres.

 'index e69de29.. 00000000' : La ligne 'index' indique la modification de la valeur d’index du fichier. 'e69de29' est le hachage SHA-1 d’un fichier vide, indiquant que le fichier était précédemment vide ou nouvellement créé, et '0000000' indique que le fichier n’existe plus dans le dernier commit.

Si c’était votre intention, alors tout va bien. Si vous n’aviez pas l’intention de supprimer le fichier, vous pouvez le récupérer à l’aide de commandes de contrôle de version, généralement en extrayant le fichier d’un commit précédent. Vous souhaitez obtenir de l’aide sur la façon de le faire ?


APRES SYNCHRONISATION

 

IDEM

TERMINAL EN ENTIER
 


100644'est une façon un peu cryptique de montrer les permissions des fichiers, le nombre 100644 signifie qu’il s’agit d’un fichier normal

 

ok c est bon il fallait attendre qq secondes apres la synchronisation




16/ crÃ©er deux nouvelles branches branch-a et branch-b


 
 



17/  dans chaque fichier readme de chaque branche, ajoutez une ligne spÃ©cifique (modif branch-a et branch-b par ex)


 


ctrl S

puis commit

 

yes
 

save 
 
synchroniser






18/ comparez les deux branches avec la fonction adÃ©quate 

git diff branch-a branch-b

 

L’extrait de code fourni montre une différence entre deux versions d’un fichier nommé readme.md.

Voici une ventilation :

La ligne commençant par - indique le contenu dans l’ancienne version (à partir de la branche-a) : modif branche-a
La ligne commençant par + indique le contenu dans la nouvelle version (à partir de la branche-b) : modif branche-b
Le message  No saut de ligne à la fin du fichier indique que le fichier ne se termine pas par un saut de ligne dans l’ancienne version.
En résumé, la modification apportée à readme.md était simplement une modification du texte de « modif branch-a » à « modif branch-b ».



19/ mergez la branche a sur master 

aller sur main
git merge branch-a

 




20/ mergez la branche b sur master 

git merge branch-b

 

 



21/ essayez de resoudre le conflit ... 

git status pour voirs tous les conflits et les éléments non mergés :

 


Avec le banedeau en haut de vs code, j'ai cliqué sur l'icone à droite : Resolve in merge editor pour ouvrir le correcteur, et j'ai sélectionné de garder les 2 en indiquant lequel apparaitrait en 1er et lequel en second

résultat :

 

et sur github :

DANS main :

 

 

 

DANS branch-a

 


DANS branch-b

 

DANS dev :

 





EXPLICATIONS / DOCUMENTATION

https://youtu.be/QmKdodJU-js?feature=shared 

Aujourd’hui, je vais vous montrer comment résoudre les conflits de fusion dans VS Code.
Dans cet exemple, il y a du texte sur le README du maître qui dit : « Ceci est du texte sur le maître ».
Sur ma branche locale, cependant, et je suis sur master, je suis allé de l’avant et j’ai validé un texte ici
qui dit : « Ceci est un texte sur ma branche locale. »
Et j’ai déjà fait un commit, comme vous pouvez le voir ici, dans cette notation en bas à gauche
Ici, une flèche pointant vers le haut avec le chiffre 1.
Donc, ce que je veux faire maintenant, c’est fusionner cette version de GitHub dans ma version locale de ce dépôt.
Donc, je tape simplement « git merge master » et il dit « Déjà à jour ».
parce que je n’ai pas tiré.
Je vais donc faire « git pull » et, comme vous pouvez le voir, il se remplit d’un conflit de fusion.
Donc, ce qu’il a juste essayé de faire, c’est de fusionner la version GitHub de ce README dans ma branche locale.
Comme vous pouvez le voir, il y a quelques conflits de fusion ici.
Accepter le changement actuel est ce bloc vert ici, donc ce serait : "C’est un peu
sur ma branche locale.
Accepter la modification entrante serait « Ceci est du texte sur master » -- celui que nous voyons sur
GitHub.
Je veux garder ma branche locale à jour avec master donc je ferais Accepter les appels entrants
Changement dans cette situation.
Mais bien sûr, vous pouvez explorer ces autres options en fonction de la situation dans laquelle vous vous trouvez
dans.
Peut-être que votre code est en avance sur master et que vous souhaitez l’enregistrer.
Je vais donc faire Accepter les modifications entrantes.
Et la fusion des fichiers en conflit affichera ce C violet dans l’onglet git.
Vous devez enregistrer le fichier.
Je suis juste en train de faire commande + S et ce petit point a disparu parce que je viens d’enregistrer ce fichier.
Après cela, il me suffit de le mettre en scène et d’utiliser commande + entrée sur Mac pour effectuer un autre commit.
Et puis après cela, je peux pousser mes modifications sur GitHub.
Et c’est tout !
C’est ainsi que vous résolvez les conflits de fusion dans git en utilisant vs code.
VS Code rend cela très facile et j’espère que vous utiliserez ce tutoriel dans votre flux de travail quotidien.
N’oubliez pas d’aimer cette vidéo et de vous abonner pour plus de tutoriels courts.
J’aime vraiment les faire et j’ai hâte d’en faire plus.
Alors merci ! pour regarder.
N’oubliez pas de consulter mes autres tutoriels git si vous êtes intéressé.

ou https://www.ionos.fr/digitalguide/sites-internet/developpement-web/git-merge-et-branch/#:~:text=Apr%C3%A8s%20avoir%20scind%C3%A9%20une%20Git%20Branch%20pour%20tester%20des%20modifications,

 

Résolution de conflits pour Git Merge
En tentant de merger des branches Git, vous risquez d’être confronté à un conflit très commun. En effet, si exactement la même partie du fichier a été modifiée dans les deux branches, Git n’est pas en mesure de déterminer quelle version doit être utilisée. Dans ce cas, le processus est stoppé avant la fin du Git Merge. Vous pouvez alors résoudre le conflit à la main après avoir reçu le message suivant :

CONFLICT (content): Merge conflict in fichier> /fichier>
Automatic merge failed; fix conflicts and then commit the result.
Bien connue grâce à la très pratique Git Cheat Sheet avec PDF à télécharger, la commande Git Status permet d’afficher exactement quels fichiers doivent être modifiés. Ils sont alors affichés clairement comme "unmerged" (non fusionnés). Modifiez les fichiers en conséquence puis exécutez-les avec Git Add et lancez au bout du compte un nouveau Git Commit. Vous avez maintenant la possibilité d’effectuer de merger les branches Git concernées. Vous pouvez ensuite supprimer les Git Branches dont vous n’avez plus besoin.

Git Cheat Sheet avec PDF à télécharger :
https://www.ionos.fr/digitalguide/sites-internet/developpement-web/git-cheat-sheet/ 


ou alors 
https://www.delftstack.com/fr/howto/git/resolve-merge-conflicts-in-git/#:~:text=R%C3%A9soudre%20les%20conflits%20survenant%20lors%20de%20la%20fusion%20de%20deux

ou encore 


https://git-scm.com/docs/git-merge/fr#:~:text=;%20git%20merge%20--abort%20peut%20%C3%AAtre%20utilis%C3%A9%20pour%20cela.%20R%C3%A9soudre

COMMENT LES CONFLITS SONT PRÉSENTÉS
Lors d’une fusion, les fichiers de l’arbre de travail sont mis à jour pour refléter le résultat de la fusion. Parmi les modifications apportées à la version de l’ancêtre commun, celles qui ne se chevauchent pas (c’est-à-dire que vous avez modifié une zone du fichier alors que l’autre côté a laissé cette zone intacte, ou vice versa) sont incorporées directement dans le résultat final. Cependant, lorsque les deux côtés ont apporté des modifications à la même zone, Git ne peut pas choisir au hasard un côté par rapport à l’autre, et vous demande de résoudre le problème en laissant ce que les deux côtés ont fait à cette zone.

Par défaut, Git utilise le même style que celui utilisé par le programme "merge" de la suite RCS pour présenter une telle section conflictuelle, comme ceci :

Voici des lignes qui sont soit inchangées par rapport à l'ancêtre
commun, ou résolues proprement car un seul côté a changé.
 <<<<<<< yours?: exemple.txt
La résolution des conflits est difficile?;
allons faire du shopping.
 =======
Git facilite la résolution des conflits.
 .>>>>>> theirs?: exemple.txt
Et voici une autre ligne qui est résolue proprement ou non modifiée.
La zone où une paire de modifications contradictoires s’est produite est marquée par les marqueurs <<<<<<<, ========, et >>>>>>>>>>`. La partie qui précède le ======= est généralement votre côté, et la partie qui suit est généralement leur côté.

Le format par défaut ne montre pas ce que l’original a dit dans la zone de conflit. Vous ne pouvez pas savoir combien de lignes sont supprimées et remplacées par la remarque de Barbie à votre côté. La seule chose que vous pouvez dire, c’est que votre côté veut dire que c’est difficile et que vous préférez faire du shopping, alors que l’autre côté veut prétendre que c’est facile.

Un autre style peut être utilisé en réglant la variable de configuration "merge.conflictStyle" sur "diff3". Dans le style "diff3", le conflit ci-dessus peut ressembler à ceci :

Voici les lignes qui sont soit inchangées par rapport à l'ancêtre
commun, ou proprement résolu parce qu'un seul côté a changé.
 .<<<<<<<< yours:exemple.txt
La résolution des conflits est difficile ;
Allons faire du shopping.
. |||||||
La résolution des conflits est difficile.
. =======
Git facilite la résolution des conflits.
 .>>>>>>> theirs:exemple.txt
Et voici une autre ligne qui est proprement résolue ou non modifiée.
En plus des marqueurs <<<<<<<<, =======, et >>>>>>>>>>>, il utilise un autre marqueur `|||||||| qui est suivi par le texte original. Vous pouvez voir que l’original ne faisait qu’énoncer un fait, et que votre camp a simplement cédé à cette déclaration et a abandonné, tandis que l’autre camp a essayé d’avoir une attitude plus positive. Vous pouvez parfois aboutir à une meilleure résolution en regardant l’original.

COMMENT RÉSOUDRE LES CONFLITS
Après avoir vu un conflit, vous pouvez faire deux choses?:

Décider de ne pas fusionner. Les seuls nettoyages dont vous avez besoin sont de réinitialiser le fichier index au commit HEAD à inverser 2. et pour nettoyer les modification d’arbre de travail effectuées par 2. et 3. ?; git merge --abort peut être utilisé pour cela.

Résoudre les conflits. Git marquera les conflits dans l’arbre de travail. Modifier les fichiers en forme et les «git add» à l’index. Utiliser git commit ou git merge --continue pour sceller l’affaire. Cette dernière commande vérifie s’il y a une fusion (interrompue) en cours avant d’appeler git commit.

Vous pouvez résoudre le conflit à l’aide d’un certain nombre d’outils :

Utiliser un mergetool. git mergetool pour lancer un outil de fusion graphique qui vous permettra de travailler sur la fusion.

Regarder les différences.  git diff` affichera une différence à trois points, en mettant en évidence les modifications apportées par les versions HEAD et MERGE_HEAD.

Regarder les différences de chaque branche. git log --merge -p chemin> montrera les différences d’abord pour la version HEAD et ensuite pour la version MERGE_HEAD.

Regarder les originaux. git show :1:nom-de-fichier montre l’ancêtre commun, git show :2:nom-de-fichier montre la version HEAD, et git show :3:nom-de-fichier montre la version MERGE_HEAD.















