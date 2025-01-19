# Architecture de déploiement Kubernetes avec Kafka (KRaft), Laravel, Redis et WebSockets

Ce projet utilise Kubernetes pour déployer une stack microservices avec les composants suivants :
- **Kafka avec KRaft** : Gestion des messages en temps réel, sans Zookeeper.
- **Laravel** : Backend avec API REST et WebSockets.
- **Nginx Ingress** : Gestion des accès HTTP.
- **Redis** : Caching pour améliorer les performances.
- **WebSockets** avec **Laravel Reverb** : Communication en temps réel avec le frontend.

Cette architecture permet une gestion moderne des messages et des données en temps réel tout en maintenant une communication fluide entre le frontend et le backend.

---

## Prérequis

Avant de commencer, assurez-vous que vous avez les éléments suivants installés :
- **Kubernetes** (Version minimale recommandée : 1.20)
- **Helm** (Version minimale recommandée : 3.x)
- **Docker** (pour la création d'images si nécessaire)
- **kubectl** pour l'interaction avec Kubernetes
- **PHP 8.3+** (pour Laravel)

---

## Architecture

### Composants principaux :
1. **Frontend (React.js)** : Application client qui communique via WebSockets pour obtenir des mises à jour en temps réel.
2. **Backend (Laravel)** : API REST pour la gestion des données et des services WebSocket via Laravel Reverb.
3. **Kafka (avec KRaft)** : Kafka en mode KRaft pour la gestion des événements en arrière-plan. Kafka ne nécessite pas Zookeeper dans cette configuration.
4. **Redis** : Cache des données clients pour réduire les appels aux services externes.
5. **Nginx Ingress** : Serveur proxy inversé pour exposer les services via `frontend.test.com` et `api.test.com`.

---

## Déploiement dans Kubernetes

### 1. Cloner le dépôt

Clonez ce dépôt pour récupérer tous les fichiers nécessaires au déploiement.

```bash
git clone <URL DU DEPOT>
cd <REPERTOIRE DU DEPOT>
