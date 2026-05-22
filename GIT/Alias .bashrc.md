## Ajouter des alias git dans sa console

### Accéder au .bashrc
Dans un environnement Linux (WSL) :
```bash
vim ~/.bashrc
# OR
nano ~/.bashrc
```

Vous pouvez ajouter une section GIT et y mettre les alias suivants : 
```
### GIT 

alias gs="git status"
alias gc="git commit -m"
alias gp="git pull"
alias gpo="git pull origin"
alias gpod="git pull origin dev"
alias gph="git push"
alias gpho="git push origin"
alias gclean="git clean -fd" # with force & not tracked folder option.
alias greset="git reset --hard" # add for example origin/develop to reset hard from develop version. Careful to hard option, it delete all your local modifications.
``` 

### Restart le bashrc :

```bash
source ~/.bashrc
```
OR
```bash
. ~/.bashrc
```

