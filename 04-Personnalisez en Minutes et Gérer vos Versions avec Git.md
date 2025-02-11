### 04 - Section 4 : Personnalisez en Minutes et Gérer vos Versions avec Git

---

# Partie 1 : Concevoir un Bon Prompt

### **1.1 Préciser la Page à Modifier**  
Indiquez clairement la page ou la section à modifier.  
**Exemple** : La page principale à `http://localhost:3000/`.

### **1.2 Rappeler le Contexte**  
Décrivez brièvement le projet et son objectif.  
**Exemple** : "Ce projet utilise Docusaurus pour fournir une documentation interactive."

### **1.3 Définir les Détails du Style**  
Ajoutez des précisions pour orienter le design :  
- Style moderne avec animations fluides.  
- Palette de couleurs harmonieuse et typographie lisible.  
- Navigation intuitive avec micro-interactions engageantes.

### **1.4 Booster le Prompt**  
Ajoutez un rôle spécifique pour l'IA.  
**Exemple** : "Agis comme un designer professionnel spécialisé en UI/UX avec 30 ans d'expérience."

### **1.5 Exemples de Plans de Formation (Utiliser des Cercles)**  

#### **Plan 1 : Formation Python**  
1. Introduction à Python  
2. Bases du Langage Python  
3. Fonctions et Modules  
4. Gestion des Fichiers  
5. Programmation Orientée Objet (POO)  
6. Projet Final  

---

# Partie 2 : Écriture des Prompts et Validation avec Git

### Prompt 1 : Modifier la Page d'Accueil

```bash
- Page à modifier : Page principale du projet accessible via la route : http://localhost:3000/  
- Contexte : Ce projet est construit avec Docusaurus
- Précisions sur le style : Crée un design époustouflant et moderne avec :  
    - Animations fluides et transitions élégantes pour une navigation immersive.  
    - Style 3D esthétique avec des éléments interactifs visuellement impressionnants.  
    - Dégradés subtils et ombres portées légères pour un rendu visuel sophistiqué.  
    - Typographie soignée et lisible avec des titres accrocheurs et un corps de texte confortable à lire.  
    - Micro-interactions engageantes (effets de survol, clics dynamiques) pour enrichir l’expérience utilisateur.  
    - Palette de couleurs harmonieuse et contemporaine en utilisant des tons modernes et apaisants.  
    - Mise en page aérée et équilibrée, mettant en avant chaque section sans surcharge visuelle.  


- Objectif : Captiver instantanément les visiteurs dès leur arrivée sur la page, les incitant à découvrir davantage le contenu grâce à un visuel attractif et mémorable.  
- Boost du Prompt : Imagine que tu es un designer UI/UX professionnel avec 30 ans d'expérience et que tu travailles sur un projet phare pour une grande entreprise technologique visant à impressionner les investisseurs.  


- Plan de formation avec des cercles ou rectangles interactifs :  

Ajoute une présentation animée du plan de formation suivante : 


#### Formation Python
1. Introduction à Python  
2. Bases du Langage Python  
3. Fonctions et Modules  
4. Gestion des Fichiers  
5. Programmation Orientée Objet (POO)  
6. Projet Final  

```

**Commandes Git** :
```bash
git init
git status
git add .
git commit -m "Prompt 1 - Modification de la page d'accueil"
git status
git log
git log --oneline
```

---

### Prompt 2 : Ajouter des Liens Cliquables vers des Catégories

```markdown
Objectif : Intégrer des liens interactifs redirigeant vers les catégories.  
Prompt :  
- Lien : Chaque lien redirige vers `/docs/{nom-categorie}`.  
- Style : Animation au survol et transition fluide.  
```

**Commandes Git** :
```bash
git status
git add src/pages/index.js
git commit -m "Prompt 2 - Ajout de liens cliquables vers les catégories"
```

---

### Prompt 3 : Créer une Animation pour les Titres

```markdown
Objectif : Ajouter une animation pour une meilleure expérience utilisateur.  
Prompt :  

- Animation : Le titre principal glisse de la gauche vers la droite au chargement de la page.  
```

**Commandes Git** :
```bash
git status
git add src/pages/index.js
git commit -m "Prompt 3 - Le titre principal glisse de la gauche vers la droite au chargement de la page"
git log --oneline
```

---

### Prompt 4 : Ajouter des Catégories

```markdown
Objectif : Automatiser l’ajout des catégories dans `/docs/`.  
Prompt :  

- Catégories à ajouter :  
  1. Bases du Langage Python → `/docs/bases-langage-python`.  
  2. Programmation Orientée Objet → `/docs/poo`.  
```

**Commandes Git** :
```bash
git status
git add .
git commit -m "Prompt 4 - Ajout de 2 premières catégories"
```

---

### Prompt 5 : Tout Casser pour Tester Git
```markdown
Objectif : Créer volontairement une version chaotique pour tester Git.  
Prompt :  

- Modifications :  
  - Supprimer tous les styles CSS.  
  - Remplacer tous les titres par "ERREUR 404".  
  - Ajouter des animations clignotantes et des couleurs rouges.  
```

**Commandes Git** :
```bash
git status
git add .
git commit -m "Prompt 5 - Version chaotique pour tester Git"
```

---

# Partie 3 : Restaurer une Version Précédente avec Git

### **Solution 1 : Forcer la Branche Principale**  
1. Affichez les commits récents :  
   ```bash
   git log --oneline
   ```
2. Revenir à un commit stable :  
   ```bash
   git checkout <commit_id>
   git branch -f main HEAD
   git switch main
   ```

---

### **Solution 2 : Utiliser une Branche Temporaire**  


1. **Ajoutez et committez toutes les modifications actuelles** avant de basculer :  
   ```bash
   git add .
   git commit -m "Sauvegarde avant création de la branche temporaire"
   ```
2. **Vérifiez l’état du dépôt** pour éviter des problèmes de fichiers non suivis ou en conflit :  
   ```bash
   git status
   ```
   
3. **Créer une branche temporaire** :  
   ```bash
   git switch -c sauvegarde-version
   ```
   Si cette commande échoue, utilisez :  
   ```bash
   git checkout -b sauvegarde-version
   ```

4. **Aligner la branche temporaire sur le commit cible** :  
   Identifiez le commit cible à l’aide de :  
   ```bash
   git log --oneline
   ```
   Puis alignez :  
   ```bash
   git reset --hard <commit_id>
   ```

5. **Fusionner proprement avec la branche principale**

   Basculez vers la branche principale :  
   ```bash
   git switch main
   ```
   Fusionnez la branche temporaire :  
   ```bash
   git merge sauvegarde-version
   ```
   Supprimez la branche temporaire une fois la fusion réussie :  
   ```bash
   git branch -d sauvegarde-version
   ```


6. **Autres conseils pour éviter les erreurs**

- **Nettoyez votre dépôt avant chaque manipulation** :  
   Si vous avez des modifications en attente, utilisez :
   ```bash
   git stash
   ```
   pour les sauvegarder temporairement.

- **Testez toujours la fusion dans un environnement isolé** avant d’appliquer à la branche principale.

- **Utilisez des alias Git pour simplifier les commandes longues** :  
   Par exemple, pour voir un journal concis :  
   ```bash
   git config --global alias.lg "log --oneline --graph --decorate"
   ```

7. **Exemple complet du processus**


*Créer et aligner une branche temporaire* :
   ```bash
   git switch -c sauvegarde-version
   git reset --hard <commit_id>
   ```
*Fusionner et nettoyer* :
   ```bash
   git switch main
   git merge sauvegarde-version
   git branch -d sauvegarde-version
   ```





### **Solution 3 : Utiliser la commande git revert**  


   ```bash
   git log --oneline
   git revert <id_du_commit>
   git log --oneline
   ```

---

# Partie 4 : Workflow Git Recommandé

1. **Initialisation** :  
   ```bash
   git init
   git config --global user.name "Votre Nom"
   git config --global user.email "votre.email@example.com"
   git local --global user.name "Votre Nom"
   git local --global user.email "votre.email@example.com"
   echo "Modification" > fichier1.txt
   git add .
   git commit -m "Votre message"
   git log --oneline
   git push origin main
   ```

# 1 -  git checkout <commit_id> (1 branche main)


   ```bash
   git log --oneline
   git checkout <commit_id>
   git branch -f main HEAD
   git switch main
   ```
 
# 2 - git reset --hard <commit_id> (2 branches)


   ```bash
   git add .
   git commit -m "Sauvegarde avant création de la branche temporaire"
   git status
   git switch -c sauvegarde-version
   git checkout -b sauvegarde-version
   git log --oneline
   git reset --hard <commit_id>
   git switch main
   git merge sauvegarde-version
   git branch -d sauvegarde-version
   ```

   ```bash
   git stash
   git config --global alias.lg "log --oneline --graph --decorate"
   ```


# 3 - git revert <id_du_commit> (1 branche)

```bash
git log --oneline
git revert <id_du_commit>
git log --oneline
```

# 4

---

### Bonnes Pratiques

- **Branches Fonctionnelles** : Créez une branche pour chaque fonctionnalité.  
- **Restauration** : Utilisez `git checkout` pour revenir à des versions stables.  
- **Fusion Propre** : Testez toujours vos modifications sur une branche temporaire avant de fusionner avec `main`.  

Ce guide garantit un développement sûr et organisé, même avec des prompts risqués.
