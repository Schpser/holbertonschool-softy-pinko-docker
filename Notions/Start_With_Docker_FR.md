# 🐳 Guide Docker - Démarrer avec Docker

---

## 📦 1. Fondamentaux de Docker

**Docker** est une plateforme qui permet de packager et d'exécuter des applications dans des environnements isolés nommés **conteneurs**.

### 🔑 Concepts Clés

| Concept | Description | Emoji |
|---------|-------------|-------|
| **Conteneurs** | Instances d'exécution d'une image Docker. Ils sont légers, isolent le logiciel de son environnement et garantissent un fonctionnement uniforme quel que soit l'hôte (développement, test ou production). | 📦 |
| **Images** | Package autonome et exécutable qui inclut tout le nécessaire pour faire fonctionner une application : le code, le runtime, les outils système, les bibliothèques et les paramètres. | 💿 |
| **Docker Hub** | Service de registre permettant de trouver et de partager des images de conteneurs avec une équipe ou la communauté. | 🌐 |
| **Docker Desktop** | Interface conviviale disponible sur Mac, Linux et Windows pour gérer les conteneurs et simplifier le processus de construction et de partage. | 🖥️ |

```
┌─────────────────────────────────────────────┐
│         🐳 Docker Architecture              │
├─────────────────────────────────────────────┤
│                                             │
│  📝 Dockerfile  ──build──> 💿 Image        │
│                              │              │
│                              │              │
│                             run             │
│                              │              │
│                              ▼              │
│                          📦 Container       │
│                                             │
└─────────────────────────────────────────────┘
```

---

## 💻 2. Guide des Commandes CLI Docker

Le pilotage de Docker s'effectue principalement via l'**interface en ligne de commande (CLI)**. Voici les commandes essentielles classées par catégorie :

### 🖼️ Gestion des Images

| Commande | Description | Exemple |
|----------|-------------|---------|
| `docker build` | 🔨 Construction d'une image | `docker build -t mon-app .` |
| | 🔄 Avec reconstruction totale | `docker build --no-cache -t mon-app .` |
| `docker images` | 📋 Lister les images locales | `docker images` |
| `docker rmi` | 🗑️ Supprimer une image | `docker rmi mon-app` |
| `docker image prune` | 🧹 Retirer les images inutilisées | `docker image prune` |

### 📦 Gestion des Conteneurs

#### ▶️ Exécution et Contrôle

```bash
# Créer et lancer un conteneur
docker run --name mon-conteneur mon-image

# Publier des ports
docker run -p 8080:80 mon-image

# Lancer en arrière-plan (détaché)
docker run -d --name mon-conteneur mon-image
```

| Commande | Description | Emoji |
|----------|-------------|-------|
| `docker start` | ▶️ Démarrer un conteneur arrêté | ▶️ |
| `docker stop` | ⏸️ Arrêter un conteneur actif | ⏸️ |
| `docker rm` | 🗑️ Supprimer un conteneur arrêté | 🗑️ |
| `docker restart` | 🔄 Redémarrer un conteneur | 🔄 |

#### 👀 Surveillance et Inspection

| Commande | Description | Emoji |
|----------|-------------|-------|
| `docker ps` | 📊 Lister les conteneurs actifs | ✅ |
| `docker ps --all` | 📋 Lister tous les conteneurs | 📋 |
| `docker container stats` | 📈 Statistiques des ressources | 📈 |
| `docker logs -f` | 📜 Suivre les logs en temps réel | 📜 |
| `docker inspect` | 🔍 Détails techniques d'un conteneur | 🔍 |
| `docker exec -it <nom> sh` | 💻 Ouvrir un terminal interactif | 💻 |

> **💡 Astuce :** Utilisez `docker exec -it <conteneur> /bin/bash` pour accéder à un shell bash si disponible.

### 🌐 Interaction avec le Registre (Docker Hub)

```bash
# 🔐 Connexion au hub
docker login -u mon-utilisateur

# ⬆️ Envoyer une image
docker push mon-utilisateur/mon-image:tag

# ⬇️ Récupérer une image
docker pull mon-utilisateur/mon-image:tag

# 🔍 Rechercher une image
docker search nginx
```

---

## 🔄 3. Proxy vs Reverse Proxy

Les serveurs mandataires (proxys) jouent différents rôles selon leur position dans la communication réseau :

### ➡️ Forward Proxy (Proxy "Avant")

**Position :** Entre un groupe de machines clients et Internet

```
👤 Client  ──>  [🛡️ Forward Proxy]  ──>  🌍 Internet  ──>  🖥️ Serveur
```

| Aspect | Description |
|--------|-------------|
| **🎯 Rôle** | Agit au nom des clients pour intercepter leurs requêtes vers les serveurs web |
| **✅ Avantages** | • 🔒 Protège l'identité des clients (cache l'adresse IP)<br>• 🌐 Permet de contourner des restrictions de navigation<br>• 🚫 Peut bloquer l'accès à certains contenus (filtre scolaire/entreprise) |

### ⬅️ Reverse Proxy (Proxy Inverse)

**Position :** Entre Internet et les serveurs web

```
👤 Client  ──>  🌍 Internet  ──>  [🛡️ Reverse Proxy]  ──>  🖥️ Serveur(s)
```

| Aspect | Description |
|--------|-------------|
| **🎯 Rôle** | Intercepte les requêtes des clients pour les rediriger vers les serveurs appropriés |
| **✨ Avantages clés** | • 🔐 **Sécurité** : Cache l'IP réelle des serveurs, protection contre les attaques DDoS<br>• ⚖️ **Load Balancing** : Distribue le trafic sur plusieurs serveurs<br>• 💾 **Mise en cache** : Stocke le contenu statique pour réponses rapides<br>• 🔑 **Chiffrement SSL** : Gère les certificats SSL |
| **📌 Exemples** | Cloudflare, Nginx, Apache (première couche de reverse proxy) |

---

### 💡 Analogie pour comprendre la différence

> **Forward Proxy 👨‍⚖️**  
> Imaginez un **avocat** qui parle au tribunal au nom d'un client pour protéger son anonymat.
> 
> **Reverse Proxy 💁**  
> Comme la **réceptionniste d'un grand hôtel** : les clients ne parlent pas directement aux cuisiniers ou aux agents d'entretien ; ils s'adressent à la réceptionniste qui redirige leurs demandes vers la bonne équipe tout en protégeant l'accès aux coulisses de l'établissement.

---

## 📚 Ressources Supplémentaires

- 📖 [Documentation officielle Docker](https://docs.docker.com/)
- 🎓 [Docker Hub](https://hub.docker.com/)
- 💬 [Forum communautaire Docker](https://forums.docker.com/)

---

## 🛠️ 4. Commandes Docker - Référence Rapide

### 📥 INSTALLATION

Docker Desktop est disponible pour Mac, Linux et Windows

- 🖥️ [Installation Docker Desktop](https://docs.docker.com/desktop)
- 📂 [Projets d'exemple Docker](https://github.com/docker/awesome-compose)
- 📖 [Documentation complète](https://docs.docker.com)

---

### ⚙️ COMMANDES GÉNÉRALES

| Commande | Description | Emoji |
|----------|-------------|-------|
| `docker -d` | 🚀 Démarrer le daemon Docker | 🚀 |
| `docker --help` | ❓ Obtenir de l'aide (fonctionne aussi avec `--help` sur les sous-commandes) | ❓ |
| `docker info` | 📊 Afficher les informations système | 📊 |

---

### 🖼️ GESTION DES IMAGES

| Commande | Description |
|----------|-------------|
| `docker build -t <image_name> .` | 🔨 Construire une image depuis un Dockerfile |
| `docker build -t <image_name> . --no-cache` | 🔄 Construire sans utiliser le cache |
| `docker images` | 📋 Lister les images locales |
| `docker rmi <image_name>` | 🗑️ Supprimer une image |
| `docker image prune` | 🧹 Supprimer toutes les images inutilisées |

---

### 📦 GESTION DES CONTENEURS

#### Création et Exécution

| Commande | Description |
|----------|-------------|
| `docker run --name <container_name> <image_name>` | ▶️ Créer et exécuter un conteneur avec un nom personnalisé |
| `docker run -p <host_port>:<container_port> <image_name>` | 🔌 Exécuter et publier les ports du conteneur vers l'hôte |
| `docker run -d <image_name>` | 🌙 Exécuter un conteneur en arrière-plan |

#### Contrôle

| Commande | Description |
|----------|-------------|
| `docker start\|stop <container_name>` | ▶️⏸️ Démarrer ou arrêter un conteneur existant (ou `<container-id>`) |
| `docker rm <container_name>` | 🗑️ Supprimer un conteneur arrêté |

#### Surveillance et Débogage

| Commande | Description |
|----------|-------------|
| `docker exec -it <container_name> sh` | 💻 Ouvrir un shell dans un conteneur en cours d'exécution |
| `docker logs -f <container_name>` | 📜 Récupérer et suivre les logs d'un conteneur |
| `docker inspect <container_name>` | 🔍 Inspecter un conteneur en cours d'exécution (ou `<container_id>`) |
| `docker ps` | 📊 Lister les conteneurs actuellement en cours d'exécution |
| `docker ps --all` | 📋 Lister tous les conteneurs (actifs et arrêtés) |
| `docker container stats` | 📈 Voir les statistiques d'utilisation des ressources |

---

### 🌐 DOCKER HUB

Docker Hub est un service fourni par Docker pour trouver et partager des images de conteneurs avec votre équipe.

🔗 **En savoir plus :** [https://hub.docker.com](https://hub.docker.com)

| Commande | Description |
|----------|-------------|
| `docker login -u <username>` | 🔐 Se connecter à Docker Hub |
| `docker push <username>/<image_name>` | ⬆️ Publier une image sur Docker Hub |
| `docker search <image_name>` | 🔍 Rechercher une image sur le Hub |
| `docker pull <image_name>` | ⬇️ Télécharger une image depuis Docker Hub |

---

**Bonne pratique Docker ! 🚀**