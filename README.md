# JSS - Card Collection Manager

## Description du projet
JSS Card Manager est une application web conçue pour les collectionneurs de cartes (Pokémon, Magic, etc.). 
Elle permet de gérer une collection numérique en offrant une interface simple pour ajouter, visualiser et trier ses cartes.

## Fonctionnalités principales
- **Modélisation** : Structure de données claire pour chaque carte (nom, extension, rareté, image).
- **Gestion** : Ajout et suppression de cartes dans la collection.
- **Visualisation** : Affichage sous forme de grille/liste.

## Structure du projet
L'architecture suit les bonnes pratiques modernes :

- `/src/components` : Éléments visuels (formulaire ajout + liste de cartes).
- `/src/models` : Définition de la structure d'une `Card`.
- `/src/services` : Logique de gestion des données.
- `/docs` : Documentation technique détaillée (`api.md`, `setup.md`).
- `/tests` : Test pour garantir la fiabilité du code.

## Installation et Lancement
1. Clonez le projet.
2. Installez les dépendances : `npm install`
3. Lancez le projet : `npm start`
4. Pour lancer les tests : `npm test`