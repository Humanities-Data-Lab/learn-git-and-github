# Apprendre Git et GitHub — Document de l’atelier (Français)

**Contrôle de version dès le début — Essentiel pour les humanités numériques**

Ce document résume les notions et commandes importantes à retenir pendant l’atelier.

---

## 1. Contrôle de version

- **Définition :** Une façon de sauvegarder et de suivre l’évolution de vos fichiers dans le temps. Un seul projet, un historique de chaque modification : qui a changé quoi, et quand. Vous pouvez revenir à n’importe quelle version antérieure.
- **Pourquoi c’est important :** Sans contrôle de version, il est facile de perdre du travail, d’écraser les changements d’un collègue ou d’oublier ce qu’on a modifié. Avec lui, vous avez un historique clair et pouvez collaborer en toute sécurité.
- **Pour les humanités numériques :** Les éditions, corpus, jeux de données et sites web impliquent souvent des équipes, des itérations sur des années, et le besoin de citer ou reproduire un état précis du projet. Beaucoup de financeurs et d’éditeurs attendent ou recommandent le contrôle de version pour la transparence et la reproductibilité.

---

## 2. Bases de Git

### Qu’est-ce que Git ?

- Outil gratuit et open source pour le contrôle de version sur votre ordinateur.
- Fonctionne en **local** : tout l’historique est dans un dossier caché (un **dépôt**) à l’intérieur du projet.
- Pas besoin d’internet pour faire des commits—seulement pour partager ou sauvegarder (ex. avec GitHub).

### Commandes essentielles

| Commande | Rôle |
|----------|------|
| `git init` | Transformer le dossier actuel en dépôt Git |
| `git add <fichier>` ou `git add .` | Mettre des fichiers en stage pour le prochain commit |
| `git commit -m "Votre message"` | Créer une photo du projet avec un message court |
| `git status` | Voir les fichiers modifiés, en stage et non suivis |
| `git log` | Voir l’historique des commits |
| `git log --oneline` | Vue compacte de l’historique (une ligne par commit) |

### Workflow

1. Créer ou modifier des fichiers.
2. `git add` les fichiers à inclure.
3. `git commit -m "Message clair et court"`.
4. Utiliser `git status` souvent pour éviter de committer les mauvais fichiers.

### .gitignore

- Fichier qui liste des **motifs** (un par ligne). Git ignore les fichiers correspondants : ils n’apparaissent pas comme non suivis et ne sont pas ajoutés avec `git add .`.
- À utiliser pour : secrets, clés API, fichiers de build, config locale, caches, sauvegardes d’éditeur.
- Créer avec : `edit .gitignore` (dans le tutoriel) ou n’importe quel éditeur. Commiter `.gitignore` pour partager les règles.

### Corriger les erreurs

| Commande | Rôle |
|----------|------|
| `git restore --staged <fichier>` | Retirer un fichier du stage (l’enlever du prochain commit) |
| `git restore <fichier>` | Annuler les changements non commités dans ce fichier (à utiliser avec précaution) |
| `git commit --amend -m "Nouveau message"` | Remplacer le message du dernier commit (ou y intégrer des changements en stage) |
| `git reset --soft HEAD~1` | Annuler le dernier commit en gardant les changements en stage |

---

## 3. Branches

- **Branche :** Ligne de développement séparée. Vous pouvez tester des changements ou travailler sur des fonctionnalités sans toucher à la ligne principale.
- **Pourquoi :** Essentiel pour expérimenter, travailler sur des fonctionnalités à part et collaborer. En HN, une branche peut servir pour une variante d’édition ou une mise à jour de jeu de données.

### Commandes

| Commande | Rôle |
|----------|------|
| `git branch` | Lister les branches (* = courante) |
| `git checkout -b <nom>` | Créer et passer sur une nouvelle branche |
| `git checkout <nom>` | Passer sur une branche existante |
| `git merge <branche>` | Fusionner cette branche dans la branche courante |
| `git merge --squash <branche>` | Apporter les changements de l’autre branche en un seul ensemble en stage ; vous commitez une fois (pas de commit de merge) |
| `git rebase <branche>` | Déplacer vos commits pour qu’ils reposent sur l’autre branche (historique linéaire) |
| `git branch -d <nom>` | Supprimer une branche fusionnée (pour garder la liste lisible) |

### Conflits de fusion

- Quand deux branches modifient la **même partie** du même fichier, Git ne peut pas fusionner automatiquement.
- Le fichier est marqué avec des marqueurs de conflit : `<<<<<<<`, `=======`, `>>>>>>>`.
- **Résoudre :** Ouvrir le fichier, choisir le contenu final (garder une version, combiner ou modifier), supprimer les marqueurs et la version non voulue, puis `git add` le fichier et `git commit`.

---

## 4. GitHub

- **Définition :** Site qui héberge des dépôts Git dans le cloud. Sauvegarde, historique visible en ligne et outils pour collaborer : les autres peuvent cloner, proposer des changements (pull requests), et vous pouvez gérer les issues et la documentation.
- **Lien avec Git :** Git est local ; GitHub est distant. Ensemble ils permettent de sauvegarder, partager et collaborer.

### Créer un dépôt sur GitHub

- Sur GitHub : **New repository** → choisir un nom (ex. `mon-projet-hn`) → vous obtenez une URL pour connecter votre dépôt local.

### Distant, push et pull

| Commande | Rôle |
|----------|------|
| `git remote add origin <URL>` | Lier votre dépôt local au distant (ex. GitHub) |
| `git push -u origin main` | Premier push : envoyer les commits et définir l’upstream |
| `git push` | Envoyer vos commits vers le distant |
| `git pull` | Récupérer et fusionner les changements depuis le distant |
| `git clone <URL>` | Télécharger une copie complète d’un dépôt (crée un nouveau dossier) |

**Conseil :** Faire `git pull` avant `git push` pour éviter les rejets quand d’autres ont poussé.

---

## 5. Collaboration et bonnes pratiques

- Utiliser des **branches** pour des lignes de travail séparées ; utiliser les **pull requests** sur GitHub pour proposer et faire revue des changements avant de fusionner.
- **Committer souvent** avec des messages clairs et courts.
- **Pousser régulièrement** pour sauvegarder le travail.
- Ajouter un **README** (ex. `README.md`) pour expliquer le projet et comment l’utiliser ou contribuer.
- Ajouter une **licence** pour que les autres sachent comment réutiliser vos données et votre code.
- **Une branche par fonctionnalité ou correctif**, puis fusionner quand c’est prêt.

---

## 6. Aide-mémoire des commandes

### Configuration
```bash
git config user.name "Votre nom"
git config user.email "votre@email.com"
git init
```

### Workflow de base
```bash
git status
git add <fichier>   # ou git add .
git commit -m "message"
git log
```

### Branches
```bash
git branch
git checkout -b <branche>
git checkout <branche>
git merge <branche>
git merge --squash <branche>
git rebase <branche>
git branch -d <branche>
```

### Distant (GitHub)
```bash
git remote add origin <URL>
git push -u origin main
git push
git pull
git clone <URL>
```

### Utile
```bash
git log --oneline
git remote -v
git restore --staged <fichier>
git restore <fichier>
git commit --amend -m "Nouveau message"
```

---

## 7. Termes clés (glossaire)

- **Dépôt (repository / repo) :** Dossier géré par Git ; contient les fichiers du projet et tout l’historique des commits.
- **Commit :** Photo du projet à un instant donné, avec un message et un identifiant unique.
- **Stage / staged :** Marquer des fichiers comme prêts pour le prochain commit avec `git add`.
- **Remote / origin :** Version du dépôt hébergée ailleurs (ex. GitHub) ; `origin` est le nom par défaut.
- **Push :** Envoyer les commits locaux vers un distant. **Pull :** Récupérer et fusionner depuis le distant. **Clone :** Télécharger une copie complète d’un dépôt.
- **Branche :** Ligne de développement séparée. **Merge :** Fusionner une autre branche dans la branche courante.
- **Conflit de fusion :** Même partie du même fichier modifiée dans deux branches ; on résout en éditant le fichier et en supprimant les marqueurs.
- **Untracked :** Fichier que Git ne suit pas encore. **.gitignore :** Fichier listant les motifs que Git doit ignorer.

---

## 8. Prochaines étapes (sur votre ordinateur)

1. **Installer Git :** https://git-scm.com/ (ou votre gestionnaire de paquets).
2. **Créer un compte GitHub :** https://github.com
3. **Configurer l’authentification** pour pouvoir pousser et tirer :
   - **Clés SSH** (recommandé), ou
   - **Jeton d’accès personnel** en HTTPS  
   Voir la doc GitHub : « Connecting to GitHub with SSH » et « Managing your personal access tokens ».

Une fois Git installé et l’authentification configurée, vous pourrez cloner des dépôts, pousser votre travail et ouvrir des pull requests en ligne de commande ou avec une interface graphique.

---

*Document pour l’atelier Apprendre Git et GitHub. Tutoriel : [https://humanities-data-lab.github.io/learn-git-and-github/](https://humanities-data-lab.github.io/learn-git-and-github/)*
