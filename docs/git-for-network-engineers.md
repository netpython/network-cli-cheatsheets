# Git pour ingénieurs réseau

Un flux simple et sûr pour versionner scripts, documentation, playbooks et configurations **anonymisées**.

> Ne commite jamais de mots de passe, jetons API, clés privées, fichiers `.env`, sauvegardes de configurations de production ou exports contenant des données sensibles.

## Le cycle quotidien

```bash
git status
git pull --ff-only
git switch -c docs/ajout-reference-bgp
# modifier ou créer les fichiers
git add docs/bgp.md
git diff --staged
git commit -m "docs: add BGP troubleshooting reference"
git push -u origin docs/ajout-reference-bgp
```

Ouvre ensuite une Pull Request vers `main`. Une branche par sujet rend la revue et le retour arrière beaucoup plus simples.

## Avant une modification réseau

1. Crée une branche nommée selon le changement : `feat/ospf-audit`, `fix/vlan-parser` ou `docs/fortigate-vpn`.
2. Ajoute des exemples fictifs : plages `192.0.2.0/24`, `198.51.100.0/24` et `203.0.113.0/24`.
3. Vérifie le format et lance les tests disponibles.
4. Relis le diff avant le commit : `git diff --staged`.
5. Dans le message, explique l'intention, pas seulement le fichier modifié.

## Sauver un travail local

```bash
git status
git add -A
git commit -m "wip: save local progress"
# ou, sans commit
git stash push -m "draft ospf lab"
git stash list
git stash pop
```

Un commit `wip:` est acceptable sur une branche personnelle ; nettoie-le avant de fusionner dans `main` si le dépôt suit un historique soigné.

## Corriger sans réécrire l'historique partagé

```bash
git revert <commit-sha>
git push
```

Utilise `revert` pour annuler un commit déjà partagé. Évite `git push --force` sur `main` : cela peut faire perdre le travail d'autres contributeurs.

## Voir précisément ce qui change

```bash
git log --oneline --graph --decorate -15
git show <commit-sha>
git diff main...HEAD
git blame README.md
```

## Ignorer les données à risque

Ajoute au minimum dans `.gitignore` :

```gitignore
.env
*.key
*.pem
secrets/
artifacts/
backups/
out/
*.xlsx
*.pcap
```

Adapte la liste au dépôt : un fichier d'exemple sûr peut rester versionné sous un nom comme `.env.example` ou `inventory.example.yml`.
