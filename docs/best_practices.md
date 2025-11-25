# Guide des Bonnes Pratiques et Débogage

Ce document recense les conventions de code adoptées pour le projet `jss-card-manager` ainsi que les erreurs courantes et leurs solutions.

## 1. Règles de Nommage (Naming Conventions)

Pour assurer la lisibilité et la maintenabilité du code, nous suivons ces règles strictes :

### Fichiers et Dossiers
*   **Composants (React)** : `PascalCase`.  
    *   *Exemple :* `CardItem.js`, `AddCardForm.js`.
    *   *Pourquoi ?* Pour les distinguer visuellement des fichiers de logique pure.
*   **Services et Utilitaires** : `camelCase`.  
    *   *Exemple :* `cardService.js`, `helpers.js`.
*   **Dossiers** : `kebab-case` ou `camelCase` (minuscule au début).
    *   *Exemple :* `components/`, `services/`.

### Variables et Fonctions
*   **Variables** : `camelCase`. Doivent être explicites et en anglais.
    *   *Bon :* `cardList`, `userScore`.
    *   *Mauvais :* `c`, `liste`, `variable1`.
*   **Fonctions** : `camelCase`. Doivent commencer par un verbe d'action.
    *   *Exemple :* `getCardById()`, `addCardToCollection()`, `calculateTotalValue()`.
*   **Constantes** : `UPPER_SNAKE_CASE`. Pour les valeurs fixes.
    *   *Exemple :* `MAX_CARDS_PER_PAGE = 20`.

### Commentaires
*   Utiliser des **JSDoc** pour les fonctions complexes (décrire les paramètres et le retour).
*   Commenter le *pourquoi* d'une logique complexe, pas le *comment* (le code doit être assez clair).

---

## 2. Gestion des Erreurs et Débogage

Voici 3 erreurs courantes qu'un développeur peut rencontrer sur ce projet, comment les détecter et les corriger.

### Erreur 1 : Mauvais chemin d'import (Module not found)
*   **Le problème :** Tenter d'importer un fichier qui n'existe pas à l'endroit indiqué.
    *   *Code fautif :* `import Card from './models/Card';` (alors que le fichier est dans `../models/Card`).
*   **Détection :**
    *   **Terminal :** Erreur critique `Module not found: Error: Can't resolve...`.
    *   **IDE :** Soulignement rouge sur la ligne d'import.
*   **Correction :** Vérifier l'arborescence. Utiliser l'autocomplétion de l'IDE (VS Code) pour générer le chemin automatiquement.

### Erreur 2 : Type de donnée incorrect (Type Mismatch)
*   **Le problème :** Passer une chaîne de caractères ("10") au lieu d'un nombre (10) pour un calcul (ex: prix ou points de vie).
    *   *Conséquence :* `10 + "20"` donne `"1020"` au lieu de `30`.
*   **Détection :**
    *   **Runtime :** Comportement bizarre dans l'application (affichage incorrect).
    *   **Console du navigateur :** Pas forcément d'erreur rouge, mais des résultats inattendus (`NaN`).
*   **Correction :**
    *   Utiliser `parseInt()` ou `Number()` pour convertir les entrées utilisateur.
    *   Vérifier les types avec `typeof variable` dans un `console.log`.

### Erreur 3 : Faute de frappe ou variable non définie (ReferenceError)
*   **Le problème :** Utiliser une variable `cardName` alors qu'elle a été déclarée comme `cardTitle`.
*   **Détection :**
    *   **Console du navigateur :** Erreur rouge explicite : `Uncaught ReferenceError: cardName is not defined`.
    *   **IDE :** La variable apparaît souvent en gris (non utilisée) ou soulignée si l'IDE est bien configuré.
*   **Correction :**
    *   Bien relire les noms de variables.
    *   Utiliser le copier-coller pour éviter les typos.
    *   Installer un "Linter" (comme ESLint) qui prévient avant même de lancer le code.
