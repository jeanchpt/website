---
layout: "../../layouts/BlogPost.astro"
title: "MacOS Docker"
description: "Installer MacOS sur une machine Docker"
pubDate: "22 Dec. 2022"
#updatedDate: "22 Dec. 2022"
heroImage: "/heroes/docker.png"
---

# MacOS sur Docker

>  Ce guide d'installation est basé sur le travail de : [sickcodes](https://github.com/sickcodes/Docker-OSX) et de [Chris Titus Tech](https://christitus.com)

## Installation de Docker

L'installation de docker dépend du système d'exploitation. Les informations ci-dessous ne sont donc pas toujours valables. Se référer au site officiel de docker et à sa documentation. 

Cependant, sous **Archlinux** voilà comment il est possible de procéder :

```sh
yay -S docker
sudo usermod -aG docker $USER
```

Après cela on procède à un redémarage et on vérifie que l'utilisateur a bien été ajouté au groupe docker avec la commande :

```sh
groups
```

Si la sortie de cette commande contient le groupe **docker**, tout est bon vous pouvez passer à la suite. 

## Installation de MacOS

Pour installer MacOS Monterey on utilise la commande suivante :

```sh
docker run -it \
    --device /dev/kvm \
    -p 50922:10022 \
    -v /tmp/.X11-unix:/tmp/.X11-unix \
    -e "DISPLAY=${DISPLAY:-:0.0}" \
    -e GENERATE_UNIQUE=true \
    -e MASTER_PLIST_URL='https://raw.githubusercontent.com/sickcodes/osx-serial-generator/master/config-custom.plist' \
    sickcodes/docker-osx:monterey

# docker build -t docker-osx --build-arg SHORTNAME=monterey
```

Il est tout à fait possible d'installer un autre système en se référant à [cette documentation](https://github.com/sickcodes/Docker-OSX).

Une fois que le système se lance, on efface le disque virtuel de 270 Go et on procède à la réinstallation de MacOS. L'installation se poursuit avec une succession de redémarrages mais une fois terminée, on lance le système et on finalise en suivant les étapes.

## Démarrage de MacOS

Pour lancer notre système fraichement créé, on trouve son nom avec la commande :

```sh
docker ps -a
```

Puis on le lance avec :

```sh
docker start nom-du-système
```