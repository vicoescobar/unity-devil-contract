# 📜 Devil's Contract — The Last Run

> **Un jeu d'horreur et d'évasion à la première personne développé sous Unity 6.**  
> *Projet réalisé dans le cadre du cursus EPITA.*

---

## 🎮 Pitch du Jeu

### Prologue : Le Crash Fatidique
Votre périple débute dans un monde ordinaire, jusqu'à ce qu'un avion hors de contrôle vous fonce dessus. Le crash est inévitable : le choc résonne, l'écran s'assombrit... **Vous êtes mort.**

### Acte I : Le Pacte aux Enfers
Vous reprenez conscience dans les profondeurs ténébreuses du monde souterrain. Face à vous, une créature imposante et menaçante vous attend : **le Diable en personne**.  
Il vous soumet une offre que nul mortel ne saurait refuser : signer un contrat d'esclavage éternel. Pour vous laisser le temps de signer, le Diable s'éloigne temporairement, vous laissant seul devant la porte de sortie scellée.

### Acte II : La Traque & L'Évasion
Hors de question d'abandonner votre âme !  
Pendant que le Diable rôde, votre unique espoir est de trouver **2 clés mystiques** dissimulées aléatoirement dans les méandres du cimetière infernal.  
Mais prenez garde :
- Dès que le Diable croise votre regard, il se lance à vos trousses en hurlant et en ricanant de façon sadique.
- Sa vitesse augmente au fil du temps.
- S'il vous attrape, un terrible *jumpscare* scelle votre destin et vous renvoie au menu principal.

### Épilogue : L'Ascension vers le Paradis
Si vous parvenez à réunir les clés et à franchir la porte des Enfers, vous atteignez les cieux baignés de lumière au-dessus des nuages. Une voix céleste reconnaît la part de lumière qui subsiste en vous : vous êtes invité à gravir l'escalier divin et à vous élever vers le Paradis pour y trouver la paix éternelle.

---

## ✨ Fonctionnalités & Mécaniques de Jeu

- **Vue FPS & Déplacements fluides** : Contrôle de la caméra à la souris/manette, course dynamique, marche discrète (`Shift`) et sauts.
- **IA Ennemie avancée (Le Diable)** :
  - Navigation dynamique via le système **Unity NavMesh**.
  - Détection du joueur par lancer de rayon (**Raycast / Line of Sight** prenant en compte les obstacles).
  - Gestion des états : Patrouille entre points stratégiques ➔ Poursuite acharnée ➔ Accélération progressive et sprints périodiques.
  - Émotes procédurales (cris d'effroi et rires diaboliques) et bruitages de pas spatialisés.
  - Séquence de capture punitive avec **Jumpscare** sonore et visuel.
- **Génération & Exploration** :
  - Apparition aléatoire des clés sur la carte (`KeySpawner`).
  - Système d'inventaire interactif (`Inventory`) avec affichage tête haute (**HUD**) dynamique (`KeySlotsUI`).
- **Système de Dialogues & Scénarisation** :
  - Effet machine à écrire (**Typewriter**) avec contrôle au clavier (`Espace`) et option pour passer (`P`).
  - Cadrages de caméra cinématiques pour les scènes d'introduction et de dénouement.
- **Ambiance & Rendu Sonore** :
  - Éclairage dynamique, torches oscillantes vacillantes (`TorchFlicker`).
  - Environnement sonore immersif (ambiance industrielle lugubre, battements, explosions, musique céleste orchestrale de fin).

---

## 🕹️ Commandes & Contrôles

| Action | Clavier / Souris | Manette (Gamepad) |
|---|---|---|
| **Se déplacer** | <kbd>Z</kbd> <kbd>Q</kbd> <kbd>S</kbd> <kbd>D</kbd> ou <kbd>W</kbd> <kbd>A</kbd> <kbd>S</kbd> <kbd>D</kbd> | Stick Gauche |
| **Orienter la caméra** | Souris | Stick Droit |
| **Marcher discrètement** | <kbd>Shift Gauche</kbd> | Gâchette Gauche (<kbd>LT</kbd>) |
| **Sauter** | <kbd>Espace</kbd> | Bouton Sud (<kbd>A</kbd> / <kbd>✕</kbd>) |
| **Ramasser une clé** | <kbd>E</kbd> | Bouton Ouest (<kbd>X</kbd> / <kbd>□</kbd>) |
| **Ouvrir la porte de sortie** | <kbd>F</kbd> | - |
| **Avancer dans les dialogues** | <kbd>Espace</kbd> | Bouton Sud (<kbd>A</kbd> / <kbd>✕</kbd>) |
| **Passer le dialogue (Skip)** | <kbd>P</kbd> | - |
| **Mode Triche (Développeur)** | <kbd>Shift</kbd> + <kbd>K</kbd> (remplit l'inventaire de clés) | - |

---

## 🛠️ Technologies & Outils

| Composant | Technologie utilisée |
|---|---|
| **Moteur de jeu** | **Unity 6** (`6000.3.7f1`) |
| **Pipeline de rendu** | **URP (Universal Render Pipeline)** `17.3.0` |
| **Langage de script** | **C#** (.NET / Mono) |
| **Gestion des entrées** | **Unity New Input System** (`com.unity.inputsystem` 1.18.0) |
| **Intelligence Artificielle** | **Unity AI Navigation** (`com.unity.ai.navigation` 2.0.9) — NavMesh & NavMeshAgent |
| **Interface Utilisateur** | **TextMesh Pro & UGUI** (Menus animés, HUD des clés, sous-titres) |
| **Environnements & Assets 3D** | *Inferno World Free* (ithappy), *Polygon Series* (Synty Studios), *Cemetery Pack*, *TrueClouds* (rendu volumétrique) |
| **Audio & Effets** | Fx sonores spatialisés, bruits de pas synchronisés, *Sci-Industrial Ambience*, musique de fin (*Wars Of Faith* par Ivan Torrent) |
| **Gestion de versions** | Git & GitHub |

---

## 🗺️ Déroulement des Scènes (Build Architecture)

Le jeu s'articule autour de 4 scènes principales ordonnées dans les *Build Settings* :

1. `Assets/Scenes/startScene.unity` *(Scène 0)* :  
   Prologue jouable où un avion poursuit le joueur jusqu'au crash mortel.
2. `Assets/Scenes/playMenuScene.unity` *(Scène 1)* :  
   Menu principal (Jouer / Quitter) avec boutons animés et gestion du curseur.
3. `Assets/Scenes/DesignScene.unity` *(Scène 2)* :  
   La scène centrale de gameplay (confrontation avec le Diable, recherche des clés, fuite dans les catacombes).
4. `Assets/Scenes/EndingScene.unity` *(Scène 3)* :  
   Épilogue céleste (dialogue paradisiaque, escalier divin, lévitation et générique de fin).

---

## 🚀 Installation & Exécution

### Prérequis
- **Unity Hub**
- **Unity Editor 6000.3.7f1** (ou version compatible Unity 6) avec le module correspondant à votre OS (Windows / macOS / Linux).

### Lancer le projet dans l'Éditeur
1. Clonez ce dépôt :
   ```bash
   git clone https://github.com/Fyorix/unity-devil-contract.git
   ```
2. Ouvrez **Unity Hub** et cliquez sur **Add** (Ajouter).
3. Sélectionnez le sous-dossier `The last run`.
4. Assurez-vous d'utiliser la version **6000.3.7f1**.
5. Dans l'arborescence du projet, ouvrez la scène d'introduction `Assets/Scenes/startScene.unity` ou le menu `Assets/Scenes/playMenuScene.unity`.
6. Appuyez sur le bouton **Play** (▶) dans Unity.

### Créer un Exécutable (Build)
1. Dans Unity, allez dans **File > Build Profiles** (ou **Build Settings**).
2. Vérifiez que les 4 scènes sont bien cochées :
   - `Assets/Scenes/startScene.unity`
   - `Assets/Scenes/playMenuScene.unity`
   - `Assets/Scenes/DesignScene.unity`
   - `Assets/Scenes/EndingScene.unity`
3. Sélectionnez votre plateforme cible (Windows x86_64 recommandée) puis cliquez sur **Build**.

---

## 👥 Équipe de Développement (EPITA)

Projet conçu et réalisé par :
- **Victor Agahi**
- **Damien Lugagne-Delpon**
- **Clément Pasteau** (*Fyorix*)
