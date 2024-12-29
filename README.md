# Cahier des Charges : Projet de Jeu de Baccalauréat

## Introduction
Le projet consiste à développer un jeu de baccalauréat en ligne utilisant le framework Symfony. Le jeu devra permettre à plusieurs joueurs de participer, de gérer leurs tours, de saisir des réponses, de calculer des scores, et de continuer ou redémarrer une partie tout en conservant ou réinitialisant les scores.

---

## Objectifs
- Créer une plateforme conviviale pour jouer au baccalauréat en ligne.
- Gérer dynamiquement les parties, les joueurs, les tours, et les scores.
- Permettre une expérience utilisateur fluide avec des interfaces modernes (Bootstrap).

---

## Fonctionnalités Détaillées

### 1. Gestion des joueurs
- Ajout d'un joueur (nom unique).
- Affichage de la liste des joueurs inscrits à une partie.
- Attribution d'un ordre de jeu pour chaque joueur.

### 2. Gestion des parties
- Création d'une nouvelle partie avec :
  - Saisie des catégories (ex : prénom, pays, animal, etc.).
  - Configuration du nombre maximal de joueurs.
- Liste des parties existantes (avec leurs états : en cours, terminées).

### 3. Tour de jeu
- Génération aléatoire d'une lettre pour chaque tour.
- Gestion des tours :
  - Passage au joueur suivant automatiquement.
  - Saisie des réponses par catégorie pour chaque joueur.

### 4. Système de scores
- Calcul des scores basé sur les réponses :
  - 10 points pour une réponse unique.
  - 5 points si plusieurs joueurs ont la même réponse.
  - 0 point pour une réponse incorrecte ou manquante.
- Affichage du classement des joueurs.

### 5. Gestion des parties
- Continuer une partie existante.
- Redémarrer une partie avec ou sans réinitialisation des scores.
- Clôturer une partie et afficher le résultat final.

### 6. Interfaces utilisateur
- Page d'accueil avec :
  - Liste des parties disponibles.
  - Boutons pour créer une partie ou rejoindre une partie existante.
- Interface de jeu :
  - Affichage des catégories, de la lettre actuelle, et des réponses.
  - Gestion des saisies pour les réponses.
  - Affichage en temps réel des scores.

### 7. Administration
- Interface pour supprimer ou modifier des parties.
- Gestion des joueurs inscrits.

---

## Modélisation de la base de données

### Tables principales

#### 1. `game` (Partie)
- **id** (PK) : Identifiant unique.
- **name** : Nom de la partie.
- **status** : Statut (en cours, terminée).
- **categories** : Liste des catégories (JSON).
- **max_players** : Nombre maximal de joueurs.
- **created_at** : Date de création.
- **updated_at** : Date de mise à jour.

#### 2. `player` (Joueur)
- **id** (PK) : Identifiant unique.
- **name** : Nom du joueur.
- **game_id** (FK) : Référence à la partie.
- **order** : Ordre de jeu.
- **score** : Score total du joueur.

#### 3. `round` (Tour)
- **id** (PK) : Identifiant unique.
- **game_id** (FK) : Référence à la partie.
- **letter** : Lettre aléatoire.
- **current_player_id** (FK) : Joueur en cours de jeu.
- **status** : Statut du tour (en cours, terminé).

#### 4. `answer` (Réponse)
- **id** (PK) : Identifiant unique.
- **round_id** (FK) : Référence au tour.
- **player_id** (FK) : Référence au joueur.
- **category** : Catégorie de la réponse.
- **value** : Valeur de la réponse.
- **points** : Points attribués.

---

## Déroulement du jeu

### Étape 1 : Création de la partie
1. Un utilisateur crée une nouvelle partie en définissant :
   - Un nom de partie.
   - Les catégories de jeu.
   - Le nombre maximal de joueurs.
2. La partie est initialisée avec un statut "en cours".

### Étape 2 : Inscription des joueurs
1. Chaque joueur saisit son nom pour rejoindre la partie.
2. L'ordre de jeu est défini automatiquement.

### Étape 3 : Début de la partie
1. La première lettre aléatoire est générée.
2. Le premier joueur saisit ses réponses pour chaque catégorie.
3. Une fois les réponses validées, le tour passe au joueur suivant.

### Étape 4 : Calcul des scores
1. Les scores sont calculés à la fin de chaque tour selon les règles :
   - Réponse unique : 10 points.
   - Réponse partagée : 5 points.
   - Réponse incorrecte ou manquante : 0 point.
2. Le classement est mis à jour en temps réel.

### Étape 5 : Fin de la partie
1. La partie se termine après un nombre prédéfini de tours ou à la demande des joueurs.
2. Les scores finaux sont affichés, et un gagnant est déclaré.
3. Les joueurs peuvent choisir de redémarrer la partie (avec ou sans réinitialisation des scores).

---

## Stack Technique
- **Backend** : Symfony (PHP 8+).
- **Frontend** : Bootstrap 5 pour les interfaces utilisateur.
- **Base de données** : MySQL.
- **Autres outils** : Composer, Doctrine ORM, et Twig.

---

## Livrables
- Code source du projet.
- Documentation technique (installation, configuration, et développement).
- Interface utilisateur fonctionnelle et responsive.

---

## Contraintes
- Respecter le modèle MVC de Symfony.
- Implémentation des tests unitaires pour les principales fonctionnalités.
- Optimisation des requêtes SQL pour de meilleures performances.

---

## Délais
Le projet devra être livré en **8 semaines**. Voici les étapes principales :
1. **Semaine 1-2** : Modélisation de la base de données et configuration initiale de Symfony.
2. **Semaine 3-4** : Développement des fonctionnalités principales (gestion des joueurs, parties, et tours).
3. **Semaine 5-6** : Implémentation du système de scores et des interfaces utilisateur.
4. **Semaine 7** : Tests et corrections.
5. **Semaine 8** : Finalisation et livraison.

---

## Conclusion
Ce cahier des charges décrit en détail le déroulement et les besoins pour le développement du jeu de baccalauréat. Une communication régulière avec les parties prenantes sera essentielle pour garantir le succès du projet.


