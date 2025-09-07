# Procédure d'authentification Git avec SSH

Ce document détaille la procédure complète pour configurer l'authentification SSH pour interagir avec des dépôts Git sur GitHub.

## 1. Générer une nouvelle clé SSH

Si vous n'avez pas déjà une clé SSH, vous devez en générer une.

Ouvrez votre terminal et exécutez la commande suivante, en remplaçant "your_email@example.com" par votre adresse e-mail GitHub.

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

Lorsqu'on vous demande "Enter a file in which to save the key," vous pouvez appuyer sur Entrée pour accepter l'emplacement par défaut (`~/.ssh/id_ed25519`).

Il est fortement recommandé de définir une passphrase pour votre clé SSH.

## 2. Ajouter votre clé SSH à l'agent ssh

Pour que votre système utilise la clé, vous devez l'ajouter à l'agent SSH.

Démarrez l'agent SSH en arrière-plan :

```bash
eval "$(ssh-agent -s)"
```

Modifiez votre fichier `~/.ssh/config` pour qu'il charge automatiquement les clés dans l'agent et stocke les passphrases dans votre trousseau.

Créez le fichier s'il n'existe pas :
```bash
touch ~/.ssh/config
```

Ouvrez le fichier `~/.ssh/config` et ajoutez le contenu suivant :

```
Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_ed25519
```

Ajoutez votre clé privée SSH à l'agent. Si vous avez créé votre clé avec un nom différent, remplacez `id_ed25519` par le nom de votre fichier de clé privée.

```bash
ssh-add --apple-use-keychain ~/.ssh/id_ed25519
```

## 3. Ajouter la clé publique SSH à votre compte GitHub

Vous devez maintenant ajouter la partie publique de votre clé à votre compte GitHub.

Copiez le contenu de votre fichier de clé publique dans votre presse-papiers.

```bash
pbcopy < ~/.ssh/id_ed25519.pub
```

Ensuite, suivez ces étapes sur GitHub :

1.  Allez dans les **Settings** de votre compte GitHub.
2.  Dans la section "Access", cliquez sur **SSH and GPG keys**.
3.  Cliquez sur **New SSH key** ou **Add SSH key**.
4.  Dans le champ "Title", donnez un nom descriptif à votre clé (par exemple, "MacBook Pro").
5.  Collez votre clé publique (copiée à l'étape précédente) dans le champ "Key".
6.  Cliquez sur **Add SSH key**.

## 4. Tester votre connexion SSH

Pour vérifier que tout est configuré correctement, testez votre connexion à GitHub.

```bash
ssh -T git@github.com
```

Vous devriez voir un message comme celui-ci :
> Hi `username`! You've successfully authenticated, but GitHub does not provide shell access.

Cela confirme que votre configuration SSH est fonctionnelle.

## 5. Configurer votre dépôt pour utiliser SSH

Si votre dépôt est actuellement configuré pour utiliser HTTPS, vous devrez changer l'URL du remote pour utiliser SSH.

Vérifiez l'URL actuelle de votre remote :
```bash
git remote -v
```

Si l'URL commence par `https://`, changez-la avec la commande suivante, en remplaçant `username` et `repo` par vos informations :
```bash
git remote set-url origin git@github.com:username/repo.git
```

Maintenant, toutes vos opérations `git push`, `git pull`, etc., utiliseront votre clé SSH pour l'authentification.

