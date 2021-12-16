# Introduction

## Hash cryptographique
Avant de parler de ce qui va réellement nous intéresser et d’entré dans le vif du sujet, voici une petite introduction portant sur les hash cryptographiques. Qu’est-ce qu’un hash ? Pour faire simple, c’est un système qui va prendre un input de taille quelconque et en ressortir un output unique de taille fixe : quoi ça veut dire ? 

```{figure} figures/hash1.png
```

Sur le schéma ci-dessus, nous pouvons voir qu’il y a un input « Hello world » qui va passer à travers une fonction de hash, une « hash function » en anglais, et va ressortir sous une forme étrange : un hash.

La principale caractéristique d’un hash c’est qu’il est unilatéral, il fonctionne à sens unique. si je crypte « Hello world » ça va me donner un très grand nombre en hexadécimal. Cependant je ne pourrais pas retrouver « Hello world » même en connaissant la fonction utilisée.

Vous avez surement remarqué sur le schéma ci-dessus que pour hasher l’input il nous faut une fonction de hashing. Il en existe plein, mais celle qui va nous intéresser, c’est sha256. Vous l’avez peut-être compris, mais cette fonction retournera toujours un nombre de 256 bits comme ceci :


```{figure} figures/hash2.png
```
Cependant, s’il y un nombre limité de bits, cela veut dire qu’il y a un nombre limité de possibilité, mais la probabilité que cela arrive est de l’ordre de l’impossible. De ce fait chaque input à un output unique et indifférenciable. On pourrait penser que si deux inputs se ressemble, alors leur output respectif seront similaire. Qu’en penser vous ? 

Répondez d’abord puis tester votre théorie. Pour faire ceci, utilisé le module hashlib puis créer une fonction créant des hash (comme dit précédemment nous utiliserons sha256). Vous trouverez ci-dessous la solution

```{code-block} python

import hashlib

def do_sha256(string):
    hash = (hashlib.sha256(string.encode())).hexdigest()
    return(hash)
```
## La blockchain en bref
Une blockchain est, comme son nom l’indique, une chaine de Bloc. Vous avez surement déjà entendu parler de blockchain, c’est même probable puisqu’il s’agit de la technologie derrière le Bitcoin et les autres cryptomonnaies. Pour faire simple, la blockchain permet de stocker des données, une fois que celle-ci sont dans le système il devient extrêmement compliqué de les modifier. Le principe de base, c’est que l’on va avoir des blocs reliés contenants des donnés quelconque, cela dépend du type de blockchain. 

Regardons à présent le contenu d’un bloc. Comme dit précédemment ces blocs vont contenir des don-nées mais pas seulement. Un bloc possède également un numéro, ainsi que la date et l’heure de créa-tion du bloc. Pour l’instant rien ne relie les blocs, c’est pour cela que l’on va utiliser les hash, vu précé-demment. Il y a donc également le hash du bloc ainsi que le hash du bloc précèdent. De cette manière, si quelqu’un de mal intentionné venait à modifier des données, cela invaliderait tous les blocs suivants.

```{figure} figures/block1.png
```
Si quelqu’un change une data du bloc n+1 , cela va changer le hash du bloc n+1, par conséquent le hash n+1 ne correspondra pas au previous hash du bloc n+2. Il faudrait donc recalculer toute la blockchain. Il subsiste cependant un problème, c’est que les ordinateurs serait capable de le faire puisqu’ils ont une vitesse de calcul très grande, mais ce problème sera abordé plus tard en détail.
La plupart des blockchains utilisées en cryptomonnaies fonctionne en « Peer to Peer », c’est-à-dire qu’il n’y a pas d’autorité central, tout se passe d’égal à égal. Imaginons que l’on ait plusieurs personnes, ces personnes vont collaborer et auront toutes une copie de la blockchain. Si une des copies vient à être corrompu les autres pourront l’identifier et rejeter cette version. 
