# Introduction

## Hash cryptographique
Avant de parler de ce qui va réellement nous intéresser et d’entré dans le vif du sujet, voici une petite introduction portant sur les hash cryptographiques. Qu’est-ce qu’un hash ? Pour faire simple, c’est un système qui va prendre un input de taille quelconque et en ressortir un output unique de taille fixe : quoi ça veut dire ? 

```{figure} figures/
```

Sur le schéma ci-dessus, nous pouvons voir qu’il y a un input « Hello world » qui va passer à travers une fonction de hash, une « hash function » en anglais, et va ressortir sous une forme étrange : un hash.

La principale caractéristique d’un hash c’est qu’il est unilatéral, il fonctionne à sens unique. si je crypte « Hello world » ça va me donner un très grand nombre en hexadécimal. Cependant je ne pourrais pas retrouver « Hello world » même en connaissant la fonction utilisée.

### Titre 2
