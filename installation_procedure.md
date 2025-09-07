# Procédure d'Installation Complète pour un Environnement de Data Science

Ce guide détaille les étapes pour configurer un environnement de développement pour la data science sur macOS en utilisant Homebrew, Mamba et Jupyter.

## 1. Prérequis : Homebrew

Homebrew est un gestionnaire de paquets pour macOS. Si vous ne l'avez pas déjà, ouvrez votre terminal et exécutez la commande suivante :

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Suivez les instructions à l'écran pour finaliser l'installation.

## 2. Installation de Mambaforge

Au lieu d'installer Conda puis Mamba, il est plus simple et recommandé d'installer **Mambaforge**. Ce paquet inclut une installation minimale de Conda avec Mamba pré-installé et configuré pour utiliser par défaut le canal `conda-forge`, qui est riche en paquets pour la data science.

```bash
brew install mambaforge
```

## 3. Initialisation du Shell

Une fois Mambaforge installé, vous devez initialiser votre shell pour que les commandes `mamba` et `conda` soient disponibles. Comme vous utilisez `zsh`, exécutez :

```bash
mamba shell init --shell zsh
```

**IMPORTANT :** Après avoir exécuté cette commande, **fermez et rouvrez votre terminal** pour que les changements prennent effet.

## 4. Création et Activation d'un Environnement

Il est recommandé de créer des environnements séparés pour chaque projet afin d'isoler les dépendances. Créons un environnement nommé `ds_env` avec Python.

```bash
# Créer un nouvel environnement avec python 3.10
mamba create -n ds_env python=3.10 -c conda-forge

# Activer l'environnement
mamba activate ds_env
```

Le nom de votre environnement (`ds_env`) devrait maintenant apparaître au début de votre prompt, indiquant qu'il est actif.

## 5. Installation de Jupyter et des Extensions

Maintenant que l'environnement est actif, nous pouvons installer JupyterLab (l'interface moderne) et les extensions que nous avons mentionnées.

### a. Installation de JupyterLab

```bash
mamba install jupyterlab -c conda-forge
```

### b. Installation des extensions

```bash
# Collection d'extensions pour l'interface Jupyter Notebook classique
mamba install -c conda-forge jupyter_contrib_nbextensions

# Pour créer des présentations à partir de notebooks
mamba install -c conda-forge rise

# Pour les widgets interactifs
mamba install -c conda-forge ipywidgets

# Intégration de Git dans JupyterLab
mamba install -c conda-forge jupyterlab-git

# Fonctionnalités d'IDE (autocomplétion avancée, etc.) pour JupyterLab
mamba install -c conda-forge jupyter-lsp jupyterlab-lsp python-lsp-server
```

## 6. Lancer JupyterLab

Une fois l'installation terminée, vous pouvez lancer JupyterLab. Assurez-vous que votre environnement `ds_env` est toujours actif.

```bash
jupyter lab
```

Cette commande ouvrira une nouvelle page dans votre navigateur web avec l'interface de JupyterLab, prête à l'emploi.

