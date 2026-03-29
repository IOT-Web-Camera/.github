# Sodium Vision

Sodium Vision est une plateforme permettant la collecte, la gestion et la redistribution de flux vidéo en temps réel. Le système facilite également la communication bidirectionnelle entre les clients et les appareils émetteurs (caméras).

---

## Objectifs

- Centraliser les flux vidéo provenant de différentes sources
- Permettre leur diffusion en ligne de manière fiable
- Assurer la communication entre les utilisateurs et les équipements
- Offrir une gestion sécurisée des accès et des ressources

---

## Architecture

Le projet repose sur une architecture distribuée composée de plusieurs services indépendants, chacun isolé dans un conteneur Docker.

### 1. Web (Backend Laravel)
- Repository : https://github.com/IOT-Web-Camera/Web
- Stack :
  - PHP / Laravel 13
  - Laravel Breeze
  - Laravel Sanctum
- Rôle :
  - Gestion des utilisateurs
  - Exposition d’une API REST sécurisée
  - Interface d’administration

---

### 2. Client (Bridge Python)
- Repository : https://github.com/IOT-Web-Camera/Client
- Stack :
  - Python 3
- Rôle :
  - Communication avec les caméras
  - Envoi des flux vers le serveur de streaming
  - Réception et exécution des commandes
  - Synchronisation avec l’API

---

### 3. Infrastructure Docker
- Repository : https://github.com/IOT-Web-Camera/Docker
- Rôle :
  - Orchestration des services
  - Gestion des conteneurs :
    - Backend Laravel
    - Bridge Python
    - MediaMTX (serveur de streaming)
    - ( Base de données : NOT IMPLEMENTED )
  - Configuration des réseaux et volumes

---

### 4. Serveur de streaming
- Outil : MediaMTX
- Rôle :
  - Réception des flux vidéo (RTSP, RTMP, etc.)
  - Redistribution (HLS, WebRTC, etc.)

---

### 5. Base de données
- Stockage de :
  - Comptes utilisateurs
  - Caméras
  - Données associées
  - Relations utilisateurs ↔ caméras

---

## Fonctionnalités

- Authentification sécurisée des utilisateurs
- Gestion des caméras
- Diffusion de flux vidéo en temps réel
- Communication bidirectionnelle client ↔ appareil
- API REST pour intégration externe
- Déploiement simplifié via Docker

---

## Technologies utilisées

- PHP / Laravel 13
- Laravel Breeze
- Laravel Sanctum
- Python 3
- MediaMTX
- Docker / Docker Compose
- MySQL ou PostgreSQL

---

## Installation (via Docker)

### Prérequis

- Docker
- Docker Compose

### Étapes

1. Cloner le repository principal (infrastructure)
```bash
git clone https://github.com/IOT-Web-Camera/Docker
# Pour la partie Web
git clone https://github.com/IOT-Web-Camera/Web       
cd Docker
# Pour lancer le service
docker-compose up -d --build
```
## Badges

[![MIT License](https://img.shields.io/badge/License-MIT-green.svg)](https://choosealicense.com/licenses/mit/)

