PyLingo : Présentation & Architecture Technique

PyLingo est une application web d'apprentissage interactive et ludique (gamifiée) dédiée à l'apprentissage du langage Python. Conçue entièrement en "Single Page Application" (SPA) contenue dans un fichier unique, elle permet d'écrire, d'exécuter et de valider du code Python directement dans le navigateur de l'utilisateur, sans aucune installation logicielle externe.

🛠️ Stack Technique & Dépendances

L'application repose sur un ensemble de bibliothèques modernes chargées via CDN, garantissant la légèreté de l'hébergement et une exécution immédiate côté client (Client-Side) :

Moteur d'exécution Python (Pyodide v0.25.0) : Compilateur Python basé sur WebAssembly (WASM). Il permet d'exécuter du code Python standard complet directement à l'intérieur du bac à sable (sandbox) du navigateur à une vitesse quasi-native.

Éditeur de code (CodeMirror v5.65.13) : Fournit un éditeur de code de niveau professionnel avec coloration syntaxique pour Python, gestion des tabulations et de l'indentation adaptées.

Design & Style (Tailwind CSS) : Framework CSS utilitaire permettant d'avoir une interface entièrement adaptative (responsive), moderne (inspirée de Duolingo) et fluide.

Effets visuels & Sonores (Canvas Confetti & Web Audio API) :

Confetti pour récompenser visuellement les utilisateurs lors de la réussite d'un jalon majeur (milestone).

Web Audio API native pour synthétiser des ondes sonores personnalisées de succès (ondes sinusoïdales), d'erreur (ondes en dents de scie) ou de niveau franchi (ondes triangulaires), éliminant le besoin de fichiers audio lourds.

Ressources visuelles (Phosphor Icons & Google Fonts Nunito) : Fournissent une typographie claire et lisible alliée à un catalogue d'icônes vectorielles cohérent.

📐 Architecture & Fonctionnalités Clés

1. Compilation et Validation dans le Navigateur

Le cœur technique de PyLingo réside dans l'intégration de Pyodide.

Capture de flux (stdout/stderr) : L'application encapsule le code de l'utilisateur en redirigeant le flux de sortie standard (sys.stdout) vers un tampon mémoire (StringIO). Cela permet d'isoler l'affichage de la console locale et de la restituer proprement à l'écran.

Tests unitaires asynchrones : Pour chaque exercice, l'application exécute d'abord le code de l'utilisateur, puis lui injecte un script de test Python spécifique (ex: validation de variables, structures de contrôle, assertions). La réussite de la validation repose sur un mécanisme d'assertions Python (assert) attrapé par le moteur JavaScript.

2. Ingénierie Pédagogique (100 Niveaux / 10 Sections)

Le parcours d'apprentissage est divisé de manière modulaire en 10 sections thématiques de 10 exercices chacune :

Les Bases (Variables, entrées-sorties simples, types)

Mathématiques (Opérations, modulo, priorités)

Conditions IF (Structures logiques, indentations)

Logique AND/OR (Opérateurs booléens, conditions complexes)

Les Listes (Tableaux, indexes, méthodes d'inventaire)

Boucles FOR (Itérations, parcours, filtres)

Boucles WHILE (Boucles conditionnelles, conditions d'arrêt)

Les Fonctions (Arguments, valeurs de retour, scope local)

Dictionnaires (Paires clé-valeur, dictionnaires imbriqués)

Modules & Mini-projets (Importations, random, math, algorithme final du jeu Snake)

3. Sauvegarde et Persistance

L'état de l'application est géré localement en mémoire et synchronisé de deux manières :

Sauvegarde automatique : Utilisation de l'API localStorage du navigateur pour conserver en temps réel la progression de l'utilisateur (niveau atteint, score d'XP).

Import/Export physique : Possibilité de télécharger un fichier JSON de sauvegarde (pylingo_save.json) et de le réimporter sur un autre appareil ou navigateur, assurant la portabilité de l'apprentissage.

4. Expérience Mobile-First & Notifications de Rappel

L'interface est configurée pour réagir comme une application native sur iOS et Android :

Web App capable (PWA) : Présence des balises <meta> requises pour masquer la barre d'adresse du navigateur une fois l'application ajoutée à l'écran d'accueil d'un iPhone (icône dédiée, statut bar translucide).

Rappels d'activité : Utilisation de l'API JavaScript Notification combinée à l'écouteur d'état de visibilité de l'application (visibilitychange). Si l'utilisateur quitte l'application ou met son téléphone en veille, un minuteur planifie un rappel personnalisé l'invitant à reprendre sa leçon.

💾 Analyse du Code Source Principal

L'application est entièrement contenue dans une architecture propre à fichier unique :

index.html
├── HEAD (Métadonnées iOS, CSS Tailwind, CDN CodeMirror/Pyodide/Confetti)
├── CSS Styles (Overlays personnalisés, Drawer d'évaluation, thèmes CodeMirror)
├── HTML Body
│   ├── Écran de chargement initial (Initialisation asynchrone de Pyodide)
│   ├── Vue 1 : Carte de progression (Générée dynamiquement en forme de courbe sinus)
│   └── Vue 2 : Interface de l'exercice (Description, éditeur de code, console de sortie)
└── JavaScript Engine
    ├── Données brutes des 100 exercices (Enoncés, codes de départ, tests d'évaluation)
    ├── Gestionnaires d'événements & Audio (Web Audio API)
    ├── Wrapper d'exécution asynchrone pour Pyodide
    └── Logique de sauvegarde & Notifications push


🚀 Perspectives d'Évolution

Grâce à sa structure propre et à l'isolation de ses modules, PyLingo peut évoluer vers plusieurs fonctionnalités avancées :

Persistance Cloud : Remplacement optionnel de la sauvegarde locale par une base de données Cloud asynchrone pour synchroniser la progression multi-appareil via un compte utilisateur.

Éditeur de niveaux communautaire : Permettre aux enseignants ou aux utilisateurs avancés de concevoir leurs propres exercices en y associant des assertions personnalisées écrites en Python.

Mode Hors-ligne (PWA Complète) : Configuration d'un Service Worker et mise en cache locale des bibliothèques clés (y compris le package WASM de Pyodide) pour exécuter l'application entièrement sans connexion internet.
