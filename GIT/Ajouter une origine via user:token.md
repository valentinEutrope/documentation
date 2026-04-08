## Ajouter une origine via user:token

-  `git remote remove origin`
-   Vérifier que vous n’avez plus de remote : `git remote -v`
-   `git remote add origin https://[github-user]:[token]@github.com/[repo].git`
-   Tester le fonctionnement : `git fetch --all`

