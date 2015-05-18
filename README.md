# trigset
Jeu de Tetris sur HP 28 S

Ce jeu de mains de 1,5 K0 se joue seul. Il est inspiré du célèbre TETRIS russe. Pour jouer, on retourne le clavier de gauche sous la machine et on tourne celle-ci d’un quart de tour dans le sens inverse des aiguille d'une montre. Pour diriger la pièce qui tombe, on utilise INS pour aller à gauche et SHIFT (la touche rouge) pour aller à droite. Pour faire tourner la pièce sur elle-même, on utilise STO. Pour accélérer la chute de pièce, on utilise ‘. L‘activation ou la désactivation des effets sonores dépend du flag 51, comme en
utilisation normale de la machine.

Apres avoir sélectionné le programme TRGST, c’est parti !!! Le but du jeu est de placer les pieces qui tombent du creux d’une colonne, afin de constituer des lignes faisant toute la largeur de l’écran, sans trou. Toute ligne constituée disparait, faisant redescendre le tas de pieces posées précédemment d’un cran. Bien sûr le tas de pièces ne doit pas atteindre le haut de la colonne. La prochaine pièce : tomber est indiquée en haut
: gauche de l’écran. Cette pièce étant une piece à part entière, attention de ne pas "coincer" votre pièce en la serrant trop à gauche dés le depart. Le niveau et le nombre de ligne restant à compléter sont affiches en permanence. Qui arrivera, au mépris d’une vitesse de jeu croissante ainsi que d’obstacles apparaissant dans l‘écran (à partir du niveau 3), à finir le niveau 10 ?…

Pour ne pas faire d’erreurs fatales (risques de Memory Lost) en entrant ce programme, bien suivre étapes successives. Si vous avez deja rentre les programmes ASSR et CHKR lors de la saisie d'un autre jeu, passer à l’étape V

## Création du Programme ASSL

Rentrez ce programme SANS ERREUR:
```
<< -> C << HEX "" 1 C SIZE FOR X "#" C X 1 + DUP SUB C X X SUB + + STR—> B—>R CHR + 2 STEP 2 #8253h SYSEVAL #4F3Dh SYSEVAL >> >>
```
Stocker-le dans ASSL.

## Création du programme CHKL

Rentre: ce programme SANS ERREUR:
```
<< —> C << HEX 64 STWS #0h ! C SIZE FOR X "#" C X DUP SUB + STR-> X I + NEXT >> >>
```
Stocker-le dans CHKL.

## Création du programme ASSR
Rentrez la chaine suivante **Sans espace ni saut de ligne**
```
"
76C20 OC8E1 1E3C0 69C20 F6000 8F180 50147 068F7 2F40A F2306 EE474 81E81 E68F9 38200 7D507 13606 13516 914A3
103EA 31909 EA703 07EA1 59016 1170C D5CD8 DDEDD 109F2 0
"
```
Dupliquez la chaîne et verifiez-la avec CHKL. Si le resultat est different de #E016h, elle a été mal rentrée. Recpmmencez cette étape. Sinon, éxecutez ASSL et stockez le résultat (les 3 System Object) dans ASSR. Ensuite, purger ASSL.

## Création du programme CHKR
Rentrez la chaine suivante **Sans espace ni saut de ligne**
```
"
76C20 07971 CD570 EEE80 01670 69C20 4B000 8F180 50143 13117 4AF0A F3101 10214 3174D 2305E A8101 0014B 3103B
6A319 09EA8 0307B 6AAE6 AE711 1E410 1AF13 1F3A7 5A775 50A78 A6E50 F112A 70102 17111 11188 A6BA8 F8B05 0174E
71431 33179 11A15 57131 14216 4808C 09F20
"
```
Dupliquez la chaîne et verifiez-la avec CHKL. Si le resultat est différent de #1DOFBh, elle a été mal rentrée,
recommencez cette étape.Sinon, éxecutez ASSL et stockez le résultat (le #0h DUP + SWAP System Object} dans
CHKR. Ensuite purger CHKL.

## Création du programme **Trgst**
Rentrez les chaînes suivantes **sans espace ni saut de ligne**. Après chacune des saisies de chaine, il faut
dupliquer la derniére chaine saisie et la vérifier avec CHKR. Si le résultat n‘est pas celui indiqué, il faut
retaper la chaînes. A la fin, vaus devriez normalement vous retrouver avec 12 chaines dans la pile.
```
"
76C20 4B211 9C211 D78E0 73D20 10C47 3D201 0E40D 9E04B 211DD 0AOE4 A2033 000A2 A2A2A 2A2A2 A2024 52594 74355
44502 A2A2A 2A2A2 A2A2A 5832E 4A203 90004 45534 84543 5E454 02020 20202 02022 383F2 0383F 29313 A0255 47494
35024 53413 02020 20202 02020 20202 63239 393A0 C4953 45454 02D49 4C494 45149 42554 02023 547D2 34952 5ED21
16A5A 08031 1A37A 04B21 14B21 1535E 04467 0E57A 0E4A2 01200 00202 0202E 49465 54145 50202 02027 3D201 0E4EA
970EE E803A BB19C 211A3 7A073 D2010 E43F2 11670 90CF9 E073D 2010C 471AE 0022A 069C2 0C400 08F18 050AF 2BFE1
B048F F15C7 37100 00008 AFA31 E3
"
```
CHKR: #88B89h
```
"
16715 87A6E 55F8F 8B050 14216 4808C 3C0A0 23311 67090 79CB0 CD570 2E3E0 76C20 73D20 10E4E D211A 4B800 9F208
F3E07 6C209 C2117 3D201 0E4ED 21167 090D6 5E03C 0A0D1 31167 09079 CB03C 0A017 31167 09079 CB069 C20B3 0008F
18050 75F4D 51747 CE40A 7D567 8E68F 8B050 179E7 E7142 16480 8CF06 E009F 20974 E0535 E0A26 7073D 2010C 4
"
```
CHKR: #32C35h
