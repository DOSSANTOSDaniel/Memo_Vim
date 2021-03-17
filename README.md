# Aide mémoire des commandes VIM

Supprime toutes les lignes d'un fichier --> `:1,$d` ou `:%d` ou "d+G"

Va à la fin de la ligne --> `$`

Va au début de la ligne --> `0`

Supprimer ou couper à partir du curseur vers la fin de la ligne --> `d$`

Supprimer ou couper à partir du curseur vers le début de la ligne --> `d0`

Supprimer un mot --> `dw`

Efface la ligne --> `dd`

Retour arrière --> `u`

Retour arrière pour toutes les modifications d'une lignes --> `U`

Copier couper coller

* dd : couper la ligne
* yy : copier la ligne
* p : coller la ligne

Couper copier coller plusieurs lignes

Exemple avec 5 lignes:

* y4 : copier
* d4 : couper
* p : coller

Même principe pour copier

Faire une copie du fichier ouvert --> `:w /chemin/`

Enregistrer et quitter VIM

Différence entre :wq et :x

:wq la date de modification change toujours même si on a rien modifier.

:x si aucun changement la date de modification n'est pas changé.

Enregistrer et fermer toutes les fenêtres

```
:wqa
:xa
```

Insertion de texte

* o  Sur une nouvelle ligne en dessous de la ligne courante
* O  Sur une nouvelle ligne au-dessus de la ligne courante

Rechercher et remplacer du texte

Exemple remplacer jean par daniel :

* Remplace la première occurrence de la ligne ou se trouve le curseur

`:s/jean/daniel/`

* Remplace toutes les occurrences de la ligne ou se trouve le curseur

`:s/jean/daniel/g`

* Remplace toutes les occurrences sur une plage de lignes

`:<numéro de ligne, début>,<numéro de ligne, fin>s/jean/daniel/g`

Exemple : Remplacer toutes les occurrences de la ligne 5 à la ligne 16

`:5,16s/jean/daniel/g`

Remplace toutes les occurrences dans tout le fichier

`:%s/jean/daniel/g`

Remplace toutes les occurrences dans tout le fichier mais de façon interactive

`:%s/jean/daniel/gc`

Fusionner des fichiers

Insérer un fichier ou le résultat d’une commande externe à partir de la position du curseur

`:r<nom du fichier>`

ou

`:r! <command>`

On peut utiliser l'autocomplétion pour trouver le fichier!

Division de l'écran et ouverture d'un fichier
* `:sp <nom du fichier>` (division horizontalement)
* `:vsp <nom du fichier>` (division verticalement)

Pour passer d'une fenêtre à l'autre (control+w)

Pour enregistrer et fermer une fenêtre (control+wq)

Numéro de la ligne ou se trouve le curseur --> `control+G`

Aller tout en haut d'un fichier --> `gg`

Aller tout en bas d'un fichier --> `shift+g`

Aller à la ligne 520 --> `:520`

Rechercher un mot

`/<mot>`

* pour le résultat suivant : n
* pour le résultat précédent : N

Afficher les numéros de ligne

```
:set nu
:set number
```

Ouvrir plusieurs fichiers en même temps sans avoir à fermer Vim

`:badd <nouveau fichier>`

Afficher les fichiers dans le buffer

`:ls`

Switcher entre les fichiers

`:b<numéro>`

Autre façon de switcher

* Occurrence suivante : (:bn)
* Occurrence précédente : (:bp)

Lancer une commande externe à VIM --> `:!`

Exemple (`:! ps -aux`)

Imprimer des documents directement à partir de VIM

Configuration de lpr sur le système

Trouver le nom de votre imprimante

`lpstat -p -d`
ou
`lpstat -t`

Configurer l'imprimante comme imprimante par défaut

```
lpoptions -d <nom imprimante>

lpstat -p -d <nom imprimante>
```

Vérifier que l'imprimante est bien configurée

`lpq`

Maintenant on peut lancer l'impression

`:hardcopy`

Ou si on veut imprimer un autre fichier

`:hardcopy <nom fichier>`

Ouvrir un explorateur de fichiers

`:e <chemin>`

Ouvrir l'explorateur dans une autre fenêtre

* `:Vex` : découpe verticale

* `:Sex` : découpe horizontale

Éditer le fichier positionné sous le curseur

`gf`

Ouvrir 2 fichiers cote-à-cote

`vim -O file1 file2`

ou

`vim -o file1 file2`

Correcteur d'orthographe et grammaire

Téléchargement des fichiers de langue

```
mkdir -p ~/.vim/spell
cd ~/.vim/spell
wget http://ftp.vim.org/vim/runtime/spell/fr.latin1.spl
wget http://ftp.vim.org/vim/runtime/spell/fr.latin1.sug
wget http://ftp.vim.org/vim/runtime/spell/fr.utf-8.spl
wget http://ftp.vim.org/vim/runtime/spell/fr.utf-8.sug
```

Activation de la correction

`:setlocal spell spelllang=fr`

* ]s      " va au prochain mot mal orthographié
* [s      " va au précédent mot mal orthographié
* zg      " ajoute un mot au dictionnaire
* zG      ajoute un mot au dictionnaire global
* zug     " enlève le mot précédemment mit
* z=      " affiche la liste des mots proposés

Installation de Grammalecte pour la correction grammaticale

_Source : https://github.com/dpelle/vim-Grammalecte_

```
git clone https://github.com/dpelle/vim-Grammalecte.git

cd Grammalecte

cp plugin/* home/daniel/.vim/plugin

cp doc/* home/daniel/.vim/doc

vim -c 'helptags /home/daniel/.vim/doc'

:q!

mkdir /home/daniel/.vimrc

vim /home/daniel/.vimrc

"set nocompatible

filetype plugin on"

mkdir /home/daniel/grammalecte/

wget https://grammalecte.net/grammalecte/zip/Grammalecte-fr-v1.10.0.zip /home/daniel/grammalecte/

unzip /home/daniel/grammalecte/Grammalecte-fr-v1.10.0.zip

rm /home/daniel/grammalecte/Grammalecte-fr-v1.10.0.zip

vim /home/daniel/.vimrc

"set nocompatible

filetype plugin on

let g:grammalecte_cli_py='~/home/daniel/Grammalecte/grammalecte-cli.py'"
```

* :GrammalecteCheck

Permet de vérifier les erreurs de grammaire

Efface un mot après le curseur et se met en mode insertion --> `ce`

Si on ouvre un fichier et qu'on l'édite alors que nous n'avons pas les droits, comment faire ?

`:w !sudo tee %`

Sélectionner tout le texte d'un fichier ouvert puis copier le dans le presse-papiers système

Pour que cela fonctonne il faut avoir le paquet "vim-gtk3" d'installé dans votre système!

`:%y+`

* `%` : sélectionne tout le texte
* `y` : copie le texte
* `+` : colle le texte dans le presse-papiers

Créer un fichier chiffré
`vim -x fichier.txt`

Afficher le résultat d'une commande directement avec vim

1. Ecrire la commande en mode edition

2. Passer en mode normal
`.!$SHELL`
puis valider
