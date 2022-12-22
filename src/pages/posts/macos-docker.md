---
layout: "../../layouts/BlogPost.astro"
title: "MacOS Docker"
description: "Installer MacOS sur une machine Docker"
pubDate: "22 Dec. 2022"
#updatedDate: "22 Dec. 2022"
heroImage: "/heroes/macos-docker.jpg"
---

# Tunnel IPv6 sur IPv4

> Il s'agit du projet final de l'UE Réseaux du M1 Informatique AMU. Il s'agit d'un programme permettant l'interconnexion de deux réseaux IPv6 par le biais d'un réseau IPv4. Projet en cours de développement, la version la plus à jour se trouve donc sur la branche dev.

```
Structure du projet
├── doc
│   ├── configs           # résultats des configurations au format .txt (ip a et ip r)
│   ├── images           # images et captures d'écrans
│   ├── wireshark        # captures wireshark
│   └── rapport.pdf      # rapport du projet
├── partage              # dossier partagé entre les VMs
│   └── tunnel64         # répertoire contenant l'application
│       ├── inc          # fichiers d'en-têtes
│       ├── src          # fichiers sources
│       ├── scripts      # scripts de configuration
│       └── Makefile      # pour compiler le projet
│       
├── VM1
│   ├── Vagrantfile       # fichier propre à vagrant
│   ├── config.yml        # fichier de configuration ansible
│   └── tunnel64.conf    # fichier de configuration du tunnel
├── VM2
├── VM3
├── VM1-6
└── VM3-6     
```

## Compilation

Pour récupérer le code source du projet :

```sh
git clone https://github.com/JeanChpt/tunnel64.git
```

Et enfin pour compiler :

```sh
cd partage/tunnel64
make
```

> Concernant la compilation, celle-ci est effectuée automatiquement par le fichier de configuration avec ansible. Il n'est donc pas nécessaire de compiler à la main.

Pour nettoyer les répertoires de compilation, utiliser la commande :

```sh
make veryclean
```

## Exécution

Dans le répertoire du projet se trouve un répertoire pour chaque VM. Ici seulement deux VMs nous intéresseront pour le tunnel. Il s'agit de VM1 et de VM3. Pour lancer VM1 et démarrer le tunnel vers VM3, faire depuis le répertoire de VM1 :

```sh
vagrant up
cd /mnt/partage/tunnel64
./bin/tunnel64
```

Pour lancer VM3  et démarrer le tunnel vers VM1, faire depuis le répertoire de VM3 :

```sh
vagrant up
cd /mnt/partage/tunnel64
./bin/tunnel64
```

> Attention, le tunnel lis sa configuration dans le fichier `tunnel64.conf` situé dans le répertoire `/vagrant` sur VM1 et VM3. Les fichiers sont préconfigurés pour ce projet, cependant il est possible de les modifier en respectant la structure ci-dessous :

```
# Nom de l'inteface virtuelle TUN
tun=tun0
# Adresse locale (entrée du tunnel)
inport=123
# Adresse distante (sortie du tunnel)
outip=172.16.2.163
outport=123
```

## Explications

Pour avoir plus d'informations sur le projet, le rapport PDF est disponible dans le répertoire docs avec les captures de tests Wireshark.