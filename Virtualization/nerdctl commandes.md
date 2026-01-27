# NERDCTL

Créer un docker-compose.yml et composer votre stack
Vous pouvez alors exécuter un compose comme avec docker

Pour avoir toutes les commandes exécuter :
```
nerdctl compose
```

 1. Lancer un docker compose file
```
nerdctl compose up
```
 2. Arrêter les conteneurs
```
nerdctl compose down
```
 3. Build les conteneurs
```
nerdctl compose build
```
Utiliser sans cache pour le forcer à exécuter de nouveau le dockerfile
```
nerdctl compose build --no-cache
```
 4. Lister les conteneurs 
```
nerdctl compose ps
```
 5. Build sans cache et lancer les conteneurs en une seule commande
```
nerdctl compose up --build --no-cache
```

 5. Forcer la suppression des images

Exemple avec l'image formio :
```
nerdctl rmi -f $(nerdctl images | grep formio | awk '{print $3}')
``` 
*Attention: supprime totalement tout ce qui à pu être fait dans les volumes.*

 6. Naviguer dans le serveur
 
Exemple avec formio : 
```
nerdctl run --rm -it formio/formio-server sh
```


