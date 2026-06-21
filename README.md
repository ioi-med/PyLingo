# PyLingo 🐍

PyLingo est une application web interactive et ludique pour apprendre les bases de la programmation en **Python**. Conçu avec une approche inspirée de célèbres applications d'apprentissage de langues, PyLingo vous propose un chemin d'apprentissage progressif avec des leçons interactives, un éditeur de code complet et un moteur d'exécution Python directement intégré dans votre navigateur !

## 🚀 Fonctionnalités Principales

*   **100 Niveaux Progressifs** : Parcourez une carte d'apprentissage (Map) allant des bases (`print()`, variables) jusqu'aux concepts plus complexes.
*   **Exécution de Python dans le navigateur** : Grâce à [Pyodide](https://pyodide.org/), le code Python que vous écrivez est compilé et exécuté instantanément dans votre navigateur, sans nécessiter de serveur ou d'installation complexe !
*   **Éditeur de Code Avancé** : Intégration de [CodeMirror](https://codemirror.net/) avec le thème Dracula pour une expérience de codage confortable et stylée.
*   **Système de Progression et de Vies** : Gagnez de l'XP à chaque leçon réussie. Mais attention, vous perdez des cœurs si vous vous trompez !
*   **Sauvegarde Locale** : Votre progression, vos XP et vos leçons terminées sont automatiquement sauvegardés dans le navigateur via `localStorage`. Vous pouvez également télécharger et importer vos sauvegardes au format JSON.
*   **Design "App" Fluide** : Utilisation de Tailwind CSS pour un rendu esthétique et responsive qui donne l'impression d'utiliser une véritable application native.
*   **PyLingo Pro** : Un système d'abonnement (simulé) pour débloquer des vies illimitées et accéder à toutes les fonctionnalités sans interruption.

## 🛠️ Technologies Utilisées

*   **HTML5 / CSS3** : Structure et style de base.
*   **JavaScript (Vanilla)** : Logique complète de l'application (pas de framework lourd).
*   **Tailwind CSS** (via CDN) : Pour un design rapide, moderne et esthétique.
*   **Pyodide** : Le cœur de l'application, permettant d'exécuter du vrai Python (CPython) compilé en WebAssembly dans le navigateur.
*   **CodeMirror** : L'éditeur de texte enrichi pour la coloration syntaxique.
*   **Canvas Confetti** : Pour célébrer vos victoires et les paliers atteints !
*   **Phosphor Icons** : Pour une iconographie élégante et moderne.

## 📥 Installation & Utilisation

PyLingo est une application **100% Client-Side** (Front-end). Aucune base de données ou serveur backend n'est nécessaire.

1. Clonez ce dépôt ou téléchargez les fichiers.
2. Ouvrez simplement le fichier `index.html` dans n'importe quel navigateur web moderne (Chrome, Firefox, Safari, Edge).
3. Et c'est tout ! Commencez à coder en Python immédiatement.

*(Note : Lors du premier chargement de la page, Pyodide télécharge le moteur Python en arrière-plan. Cela peut prendre quelques secondes en fonction de votre connexion).*

## 👨‍💻 Créé par

Codé avec passion par **Mohamed Mehdi Tannoubi**.
