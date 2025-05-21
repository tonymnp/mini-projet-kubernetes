# Mini-projet Kubernetes — Déploiement de WordPress via Manifests

## Objectif 

Ce projet consiste à déployer WordPress et MySQL sur un cluster Kubernetes en utilisant uniquement des manifests YAML (sans Helm), dans le but de comprendre et maîtriser les composants essentiels d’un déploiement K8s manuel.


## 📂 Arborescence du projet
```
k8s-wordpress/
├── mysql-deployment.yaml
├── mysql-service.yaml
├── wordpress-deployment.yaml
├── wordpress-service.yaml
└── README.md
```
## ✅ Lancement

```
kubectl apply -f mysql-pv.yaml
kubectl apply -f mysql-pvc.yaml
kubectl apply -f mysql-deployment.yaml
kubectl apply -f mysql-svc.yaml
kubectl apply -f wp-deployment.yaml
kubectl apply -f wp-svc.yaml
```

Vérifier que les pods tournent :
```
kubectl get pods
kubectl get svc
kubectl get pv,pvc
```
## Accéder à l'interface Wordpress

```
sur minikube :
minikube service wp-svc
```
## Nettoyage

```
kubectl delete -f wp-svc.yaml
kubectl delete -f wp-deployment.yaml
kubectl delete -f mysql-svc.yaml
kubectl delete -f mysql-deployment.yaml
kubectl delete -f mysql-pvc.yaml
kubectl delete -f mysql-pv.yaml
```

## 🎓 Compétences développées
Déploiement manuel sur Kubernetes

Écriture et structuration de fichiers YAML

Gestion de volumes, variables d’environnement et services réseau

Compréhension des dépendances entre services dans un cluster K8s

## Stack technique
Kubernetes (manifests YAML)

WordPress

MySQL

Services : ClusterIP, NodePort

Volumes persistants (hostPath ou PVC selon contexte)

🔧 Étapes de déploiement
MySQL

mysql-deployment.yaml : création d’un Deployment avec 1 seul pod

mysql-service.yaml : exposition en interne via ClusterIP

WordPress

wordpress-deployment.yaml : création du pod avec les bonnes variables d’environnement (DB info)

wordpress-service.yaml : exposition en externe via NodePort

Stockage

Volume monté sur le pod WordPress (/data) pour stocker les données de manière persistante

Réseau

Les services permettent la communication entre les pods et l’accès depuis l’extérieur



