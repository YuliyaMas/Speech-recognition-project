# Speech-recognition-project

## Description du projet 
Ce projet a été réalisé dans le cadre d'une étude sur les réseaux de neurones pour la reconnaissance de la parole, et est le fruit d'un travail d'équipe.
L'objectif est d'identifier la langue à partir de phonèmes extraits d'enregistrements audio.
La méthodologie appliquée repose sur l'analyse des phonèmes communs à six langues : l’allemand, l’anglais australien, le néerlandais, le russe, le biélorusse et l’ukrainien, regroupées en deux blocs : 
-	les langues germaniques : l’allemand, l’anglais australien et le néerlandais
-	les langues slaves : le russe, le biélorusse et l’ukrainien

Les langues choisies sont regroupées en fonction de leur similarité, ce qui constitue un défi pour le projet. L'objectif principal était de développer un modèle de neurones profonds capable de distinguer les phonèmes de langues phonologiquement proches (par exemple, le biélorusse et l'ukrainien) en se basant sur les mêmes phonèmes.
Les phonèmes choisis sont [p], [m] et [z] car ils semblent être les mieux représentés dans les corpus respectifs.

## Données 
Les fichiers audio utilisés proviennent de la banque d'enregistrements spontanés réalisés par des locuteurs natifs, disponibles sur le site de Mozilla Common Voice.

## Baseline
Afin de comparer les résultats obtenus grâce à l'algorithme des réseaux de neurones convolutifs (CNN), un modèle baseline a été construit en se basant sur le phonème [a].

## Couches de CNN 
1. Couche de convolution avec 32 filtres, un noyau de taille 3x3 et une fonction d’activation ReLU, dont la dimension d’entrée est [64, 64, 1] car nos images sont en noir et blanc.
2. Couche de MaxPooling2D avec une fenêtre de 2x2, permettant de réduire de moitié la taille des images en conservant les caractéristiques les plus importantes.
3. Couche de convolution avec 64 filtres, un noyau de taille 3x3 et une fonction d’activation ReLU.
4. Couche de MaxPooling2D avec une fenêtre de 2x2, permettant de réduire de moitié la taille des images en conservant les caractéristiques les plus importantes.
5. Couche de Dropout permettant de retirer la moitié des filtres à chaque epoch. Cette couche permet d’éviter le surapprentissage.
6. Couche de flatten pour aplatir la sortie des couches précédentes et renvoyer un vecteur.
7. Couche dense de 128 neurones avec une fonction d’activation ReLU.
8. Couche de dropout permettant de retirer 1/5 des filtres à chaque epoch. Cette couche permet d’éviter le surapprentissage.
9. Couche dense de 6 neurones avec une fonction d’activation softmax. Cette dernière couche nous fournira les probabilités pour chaque élément d’appartenir à l’une des six classes.

## Note 
Dans ce projet, les phonèmes ont été préalablement traités pour obtenir leurs MFCC (Mel Frequency Cepstral Coefficients).
Les MFCC sont en fait une extraction des caractéristiques du signal, développée à partir de la FFT et de la DCT, et basée sur l’échelle de Mel.
Cette technique est très utilisée pour la reconnaissance de locuteurs, grâce à un article du laboratoire de recherche de Jussieu, le LISIF (Laboratoire des Instruments et Systèmes d'Ile-de-France - EA 2385, UPMC).
