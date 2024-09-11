# git_cmd
A little repo for the trouble I have for the complex git command.

# Squash de Commits Git

Ce guide explique comment squash (fusionner) plusieurs commits en un seul dans Git, tout en préservant certains commits récents.

## Prérequis

- Git installé sur votre système
- Accès en écriture au dépôt distant

## Étapes

1. **Checkout de la branche**

  `git checkout branch`


2. **Lancer le rebase interactif**

  `git rebase -i 892f40a^`
  
3. **Modifier la liste des commits**
Dans l'éditeur qui s'ouvre, modifiez la liste comme suit :
- Laissez `pick` pour le premier commit (892f40a) et les 5 derniers commits
- Changez les autres en `squash`

4. **Éditer le message de commit**
- Sauvegardez et fermez l'éditeur
- Dans le nouvel éditeur, rédigez un message résumant tous les changements squashés

5. **Vérifier le résultat**

  `git log`

  
6. **Pousser les changements**

  `git push --force origin branch`


## Avertissements

- Cette opération modifie l'historique Git
- L'utilisation de `--force` écrase l'historique distant
- Résolvez manuellement les conflits éventuels

## En cas de problème

  Pour annuler le rebase : `git rebase --abort`
  
## Résultat

Après ces étapes, les commits entre 892f40a et 8eb56b9 (inclus) seront fusionnés en un seul, tandis que les 5 derniers commits resteront inchangés.

## recuperer un commit avec reflog

# Récupération de Commits Perdus avec Git Reflog

Ce guide explique comment utiliser `git reflog` pour récupérer des commits perdus dans Git.

## Prérequis

- Git installé sur votre système
- Un dépôt Git avec des commits perdus à récupérer

## Étapes de Récupération

1. **Afficher le Reflog**

  `git reflog`

Cette commande affiche l'historique des opérations Git, y compris les commits perdus.

2. **Identifier le Commit Perdu**
- Examinez la sortie du reflog
- Recherchez le hash du commit perdu et l'action qui a causé sa perte (ex: reset, suppression de branche)

3. **Créer une Nouvelle Branche**

  `git branch <nom-de-branche> <hash-du-commit>`

Remplacez `<nom-de-branche>` par un nom approprié et `<hash-du-commit>` par le hash identifié.

4. **Vérifier la Récupération**

  `git log`

Vérifiez que la nouvelle branche contient bien le commit récupéré.

## Exemple

```bash
git reflog
# Identifiez le hash du commit perdu, par exemple abc123

git branch recuperation abc123

git log recuperation

# Vérifiez que le commit est présent dans la nouvelle branche
