# Développement d'une borne de charge véhicule électrique

## Description

Ce projet met en œuvre le développement logiciel pour la gestion d’une borne de recharge dédiée aux véhicules électriques. Il s’articule autour de plusieurs modules C++ permettant la gestion des clients, le contrôle des éléments physiques de la borne (charge, trappe, voyants, minuterie), ainsi que l’interface avec une mémoire partagée simulant le matériel embarqué.

## Modules principaux

- **Base_client**  
  Gère la base des clients autorisés via des numéros de carte. Fournit une fonction d'authentification (`authentifier`) des clients par lecture d’un fichier texte, et permet aux utilisateurs autorisés d'accéder aux services de la borne.

- **Charge**  
  Responsable du contrôle du processus de charge. Elle permet de lire la tension, de modifier la valeur du PWM (modulation de largeur d’impulsion), et de manipuler le contacteur AC (ouverture/fermeture).

- **Timer**  
  Implémente la gestion du temps d’utilisation de la borne, avec des méthodes pour initialiser le minuteur et lire le temps écoulé depuis le début de la charge.

- **Trappe**  
  Gère l’état d’ouverture/fermeture de la trappe permettant l’accès à la prise de charge, en interfaçant les voyants associés pour signaler l’état.

## Fichiers sources principaux

- [`Base_client.cpp`](src/Base_client.cpp) / [`Base_client.h`](src/Base_client.h) : gestion et authentification des clients par lecture fichier.
- [`Charge.cpp`](src/Charge.cpp) / [`Charge.h`](src/Charge.h) : interface et contrôle du processus de charge (tension, PWM, contacteur AC).
- [`Timer.cpp`](src/Timer.cpp) / [`Timer.h`](src/Timer.h) : gestion du timer de séance de charge.
- [`Trappe.cpp`](src/Trappe.cpp) / [`Trappe.h`](src/Trappe.h) : ouverture/fermeture de la trappe et gestion des voyants.

## Compilation

Un `Makefile` est fourni dans le dossier `src/` pour faciliter la compilation du projet.

```sh
cd src
make
```

## Utilisation

L’exécutable principal contrôle toute la logique décrite ci-dessus, avec une simulation des interactions matérielles via mémoire partagée et I/O virtuelles.  
Pour ajouter un client, insérer son numéro dans le fichier `Base_client.txt`.

## Auteurs

- Youssef ELBATTAH
- SAPIN-CAPEL

## Structure générale

Chaque classe correspond à un "composant" physique de la borne (carte client, charge, trappe, minuterie, voyants) pour une gestion modulaire et claire du système.
