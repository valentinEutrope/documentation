## Faciliter et harmoniser les commits 

### Contexte
Le but de ce script est de créer rapidement des commits formatés pour votre projet. Le format rendu sera : 
```
[type] PROJET-xxxx: description 
```
type = feat, fix, build, etc.

PROJET = nom du projet

xxxx = numéro du ticket ou de la tâche traitée

Si le nom de votre branche est sous cette forme par exemple : PROJET-XXXX/description. Le script récupère automatiquement le numéro du ticket pour l'incorporer au commit. 

### Script
Depuis un terminal bash :
- Créer un dossier "bin" à la racine utilisateur : 
```bash 
mkdir ~/bin
```
- Créer un fichier "gc.sh"

```bash 
touch ~/bin/gc.sh
```
- Ajouter le script suivant via un IDE, vim ou nano (vim ~/bin/gc.sh) :  
```bash
#!/usr/bin/env bash

# Liste des types
types=("feat" "fix" "build" "chore" "ci" "docs" "style" "refactor" "test")

projet="PROJET"

echo "Type de commit :"
select type in "${types[@]}"; do
  if [[ -n "$type" ]]; then
    break
  else
    echo "Choix invalide"
  fi
done

# Récupération de la branche courante
branch=$(git branch --show-current)

# Extraction du ticket (ex: SIRIUS-1234)
ticket=$(echo "$branch" | grep -oE '$projet-[0-9]+')

# Si pas trouvé → demander à l'utilisateur
if [[ -z "$ticket" ]]; then
  read -r -p "Numéro de ticket (xxxx) : " input_ticket
  ticket="$projet-$input_ticket"
else
  echo "Ticket détecté : $ticket"
fi

# Description
read -e -r -p "Description : " desc

# Message final
message="[$type] $ticket: $desc"

echo "Commit message: $message"

# Confirmation
read -r -p "Confirmer ? (y/n) " confirm
if [[ "$confirm" != "y" ]]; then
  echo "Annulé"
  exit 0
fi

git commit -m "$message"
```
Vous pouvez adapter la variable "projet" en début de script avec le nom de votre projet.

- Octroyer les droits d'écritures
```bash 
chmod +x ~/bin/gc
```

### Alias

Ouvrer le fichier ~/.bashrc pour ajouter un alias qui appel le script, par exemple : 
```bash 
alias  gc="~/bin/gc.sh"
```
Redémarrer le bash : 
```bash 
source ~/.bashrc
```
Vérifier si votre alias apparaît dans a liste : 
```bash 
$ alias
alias gc='~/bin/gc.sh'
alias gclean='git clean -fd'
alias gp='git pull'
alias gph='git push'
alias gpho='git push origin'
alias gpo='git pull origin'
alias gpod='git pull origin dev'
....
```
-> Vous pouvez désormais utiliser la commande "gc" pour commit après avoir ajouté vos fichiers. 

