# Aide mémoire des commandes sur VIM

Supprime toutes les lignes d'un fichier :
:1,$d 

Va à la fin de la ligne 
$

Va au début de la ligne
0

Efface la ligne à partir du curseur
d$

Efface la ligne
dd

Retour arrière
u

Retour arrière pour toutes les modifications
U

Copier couper coller
dd : couper la ligne
yy : copier la ligne
p : coller la ligne

Couper copier coller plusieurs lignes
exemple avec 5 lignes:
y4 : copier
d4 : couper
p : coller

Supprimer ou couper à partir du curseur vers le début de la ligne
d0
Supprimer ou couper à partir du curseur vers la fin de la ligne
d$
Même principe pour copier

Enregistrer et quitter vim
différence entre :wq et :x
:wq la date de modification change toujours même si on a rien modifier
:x si aucun changement la date de modification n'est pas changé

Enregistrer et ferme toutes les fenetres
:wqa 
:xa

Insertion de texte
o  Sur une nouvelle ligne en dessous de la ligne courante
O  Sur une nouvelle ligne au-dessus de la ligne courante



Rechercher et remplacer du texte
Exemple remplacer jean par daniel :
Remplace la première occurence de la ligne ou se trouve le curseur (:s/jean/daniel/)
Remplace toutes les occurences de la ligne ou se trouve le curseur (:s/jean/daniel/g)
Remplace toutes les occurences sur une plage de lignes (:<numéro de ligne, début>,<numéro de ligne, fin>s/jean/daniel/g)
Exemple : Remplacer toutes les occurences de la ligne 5 à la ligne 16 (:5,16s/jean/daniel/g)
Remplacer toutes les occurences dans tout le fichier
:%s/jean/daniel/g

Fusionner des fichiers
Incerer un fichier à partir de la position du curseur
:r<nom du fichier>
On peut utiliser l'autocompletion pour trouver le fichier

Splite l'écran et ouvre un autre fichier
:sp <nom du fichier> (Split horizontalement)
:vsp <nom du fichier> (Split verticalement)
Pour passer d'une fenetre à l'autre (control+w)
Pour fermer une fenetre (control +wq)

Numéro de ligne ou nous sommes
control G

Aller tout en haut du fichier
gg

Aller en bas du fichier
shift g

Aller à la ligne 520
:520

Rechercher un mot
/mot
pour le résultat suivant : n
pour le résultat précédent : N

Afficher les numeros de ligne
:set nu
:set number

Ouvrir plusieurs fichiers en même temps sans avoir à fermer Vim
:badd <nouveau fichier>
Afficher les fichiers dans le buffeur
:ls
Switcher entre les fichiers
:b<numéro>
Autre facon de switcher
Ocurence suivante : (:bn)
Occurence précédente : (:bp)

Lancer une commande externe à vim
:!
Exemple (:! ps -aux)

Imprimer des documents directement à partir de vim
1 Configuration de lpr sur le système
Trouver le nom de votre imprimante
lpstat -p -d
ou
lpstat -t

configurer l'imprimante comme imprimante par defaut
lpoptions -d <nom imprimante>
lpstat -p -d <nom imprimante>

Vérifier que l'imprimante est bien configurée
lpq

Dans vim
:hardcopy

ou si on veut imprimer un autre fichier 
:hardcopy <nom fichier>


