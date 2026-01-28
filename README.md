# Webserv# webserv 🌐

<div align="center">
  <img src="https://img.shields.io/badge/C++-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white" alt="C++" />
  <img src="https://img.shields.io/badge/HTTP-1.1-FF6B6B?style=for-the-badge" alt="HTTP/1.1" />
  <img src="https://img.shields.io/badge/CGI-Supported-4ECDC4?style=for-the-badge" alt="CGI" />
  <img src="https://img.shields.io/badge/Standard-C++98-00599C?style=for-the-badge" alt="C++98" />
</div>

## 📝 Description

**webserv** est une implémentation complète d'un serveur web HTTP/1.1 développée from scratch en C++98. Ce projet démontre une compréhension approfondie des protocoles réseau, de la gestion des sockets et de l'architecture serveur.

## 🎯 Objectifs du Projet

- Implémenter un serveur HTTP/1.1 conforme aux standards
- Maîtriser la programmation réseau avec les sockets
- Gérer les requêtes concurrentes et les connexions multiples
- Comprendre les protocoles de communication web
- Développer une architecture modulaire et robuste

## 🛠️ Technologies Utilisées

- **C++98** - Standard C++ strict pour la compatibilité
- **Sockets** - Communication réseau TCP/IP
- **HTTP/1.1** - Protocole de communication web
- **CGI** - Interface pour scripts dynamiques
- **Multiplexing I/O** - Gestion des connexions simultanées

## 🚀 Installation & Lancement

### Prérequis
```bash
# Compilateur C++ compatible C++98
g++ >= 4.8
make
```

### Compilation et lancement
```bash
# Cloner le repository
git clone https://github.com/alesshardy/Webserv.git
cd Webserv

# Compiler le serveur
make

# Lancer avec fichier de configuration par défaut
./webserv

# Lancer avec fichier de configuration personnalisé
./webserv chemin/vers/config.conf

# Afficher l'aide
./webserv --help
```

### Commandes Make disponibles
```bash
make          # Compilation du projet
make clean    # Suppression des fichiers objets
make fclean   # Nettoyage complet (objets + exécutable)
make re       # Recompilation complète
```

## 📋 Fonctionnalités Principales

### 🌐 Serveur HTTP/1.1 Complet
- **Méthodes HTTP** - GET, POST, DELETE
- **Headers HTTP** - Gestion complète des en-têtes
- **Status Codes** - Codes de réponse standards
- **Keep-Alive** - Connexions persistantes
- **Chunked Transfer** - Transfert par chunks

### 🔧 Configuration Flexible
- **Fichiers de configuration** - Syntaxe type Nginx
- **Virtual Hosts** - Plusieurs sites sur un serveur
- **Routes personnalisées** - Gestion des emplacements
- **Pages d'erreur** - Personnalisation des erreurs HTTP

### 🚀 Performance & Robustesse
- **Multiplexing I/O** - select()/poll() pour les connexions simultanées
- **Gestion mémoire** - Aucune fuite mémoire
- **Signal handling** - Arrêt propre du serveur
- **Logs détaillés** - Système de journalisation complet

### 📜 Support CGI
- **Scripts dynamiques** - Exécution de scripts CGI
- **Variables d'environnement** - Passage des paramètres
- **Timeouts** - Protection contre les scripts qui traînent

## 🏗️ Architecture

```
webserv/
├── srcs/
│   ├── main.cpp              # Point d'entrée
│   ├── Server/               # Logique serveur principal
│   │   ├── Server.cpp
│   │   └── Socket.cpp
│   ├── Request/              # Parsing des requêtes HTTP
│   │   ├── Request.cpp
│   │   ├── RequestBody.cpp
│   │   └── CgiRequest.cpp
│   ├── Response/             # Génération des réponses
│   │   ├── Response.cpp
│   │   └── ErrorPage.cpp
│   ├── Config/               # Gestion configuration
│   │   ├── Config.cpp
│   │   ├── BlocServer.cpp
│   │   └── BlocLocation.cpp
│   ├── Client/               # Gestion des clients
│   ├── Utils/                # Utilitaires
│   └── LogManager/           # Système de logs
├── www/                      # Contenu web par défaut
├── configs/                  # Fichiers de configuration
└── Makefile                 # Build system
```

## ⚙️ Configuration

### Exemple de configuration
```nginx
server {
    listen 8080;
    server_name localhost;
    root ./www;
    index index.html;
    
    location / {
        allow_methods GET POST;
        autoindex on;
    }
    
    location /cgi-bin/ {
        cgi_extension .py .php;
        cgi_path /usr/bin/python3;
    }
    
    error_page 404 /404.html;
}
```

## 🏆 Compétences Acquises

- **Programmation système** - Sockets, processus, signaux
- **Protocoles réseau** - HTTP/1.1, TCP/IP
- **Architecture logicielle** - Design patterns, modularité
- **Gestion mémoire** - Allocation/libération rigoureuse
- **Concurrence** - I/O multiplexing, gestion multi-clients
- **Parsing** - Analyse de protocoles textuels
- **Debugging** - Outils de diagnostic réseau

## 🎯 Défis Techniques Relevés

- **Conformité HTTP/1.1** - Respect strict des RFC
- **Performance** - Gestion de milliers de connexions simultanées
- **Stabilité** - Serveur qui ne crash jamais
- **Parsing robuste** - Gestion des requêtes malformées
- **Memory management** - Zéro fuite mémoire
- **Signal handling** - Arrêt propre en toutes circonstances

## 🧪 Tests

```bash
# Test basique avec curl
curl http://localhost:8080/

# Test de performance avec siege
siege -c 100 -t 30s http://localhost:8080/

# Test CGI
curl http://localhost:8080/cgi-bin/script.py

# Test des méthodes HTTP
curl -X POST -d "data=test" http://localhost:8080/upload
curl -X DELETE http://localhost:8080/file.txt
```

---

*Projet réalisé dans le cadre du cursus 42 Paris - Démonstration de maîtrise de la programmation système et des protocoles réseau*
