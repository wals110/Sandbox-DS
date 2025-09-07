# Installation et Fonctionnalités des Extensions Jupyter

## Procédure d'installation

Pour l'instant, la seule étape réalisée est l'initialisation de l'environnement Mamba.

```bash
eval "$(mamba shell hook --shell zsh)"
mamba activate ds_env
```

## Extensions Jupyter Populaires

Voici une description de quelques extensions Jupyter utiles pour la data science.

### 1. Jupyter Notebook nbextensions

**Installation :**
```bash
mamba install -c conda-forge jupyter_contrib_nbextensions
```

**Fonctionnalités :**
Cette extension est une collection de nombreuses petites améliorations pour l'interface classique de Jupyter Notebook. Parmi les plus populaires, on trouve :
*   **Hinterland :** Autocomplétion du code dans les cellules.
*   **Codefolding :** Permet de plier/déplier des blocs de code.
*   **Table of Contents (2) :** Génère une table des matières cliquable à partir des titres de votre notebook.
*   **Spellchecker :** Un correcteur orthographique pour les cellules de type Markdown.
*   **Autopep8 :** Reformate automatiquement votre code pour suivre le style du guide PEP 8.

### 2. RISE

**Installation :**
```bash
mamba install -c conda-forge rise
```

**Fonctionnalités :**
RISE (Reveal.js - Jupyter/IPython Slideshow Extension) vous permet de transformer vos notebooks Jupyter en présentations interactives de type diaporama, directement depuis le notebook, sans avoir à exporter votre travail. C'est idéal pour présenter vos analyses et vos résultats.

### 3. Jupyter Widgets

**Installation :**
```bash
mamba install -c conda-forge ipywidgets
```

**Fonctionnalités :**
Les Jupyter Widgets permettent de créer des contrôles interactifs dans vos notebooks. Vous pouvez ajouter des sliders, des boutons, des menus déroulants, des zones de texte, et bien plus encore. Ces widgets peuvent être liés à votre code Python, ce qui vous permet de créer des visualisations et des tableaux de bord dynamiques.

### 4. JupyterLab Git

**Installation :**
```bash
mamba install -c conda-forge jupyterlab-git
```

**Fonctionnalités :**
Si vous utilisez JupyterLab (l'interface de nouvelle génération pour Jupyter), cette extension est indispensable. Elle ajoute un onglet Git à l'interface de JupyterLab, vous permettant de :
*   Visualiser les changements dans vos fichiers.
*   Faire des "commits", "push" et "pull" directement depuis l'interface graphique.
*   Gérer les branches de votre dépôt Git.

### 5. JupyterLab LSP (Language Server Protocol)

**Installation :**
```bash
mamba install -c conda-forge jupyter-lsp jupyterlab-lsp python-lsp-server
```

**Fonctionnalités :**
Cette extension apporte des fonctionnalités d'IDE (Environnement de Développement Intégré) avancées à JupyterLab. Grâce à la communication avec un "Language Server", vous bénéficiez de :
*   Autocomplétion intelligente et contextuelle.
*   Navigation dans le code (aller à la définition, trouver les références).
*   Détection d'erreurs en temps réel (linting).
*   Documentation contextuelle au survol de la souris.

