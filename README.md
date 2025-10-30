# 🔧 GitOps Template Lab

[![GitHub Repo](https://img.shields.io/badge/GitHub-Template-blue)](https://github.com/tonuser/GitOpsTemplateLab)
[![ArgoCD Sync](https://img.shields.io/badge/ArgoCD-Sync-green)](#)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?logo=kubernetes&logoColor=white)
![Helm](https://img.shields.io/badge/Helm-0F1689?logo=helm&logoColor=white)
![Terraform](https://img.shields.io/badge/Terraform-844FBA?logo=terraform&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?logo=grafana&logoColor=white)
![ArgoCD](https://img.shields.io/badge/ArgoCD-FE5D26?logo=argo&logoColor=white)
![Kyverno](https://img.shields.io/badge/Kyverno-007ACC?logo=kyverno&logoColor=white)
![Cosign](https://img.shields.io/badge/Cosign-000000?logo=cosign&logoColor=white)

---

## 👋 Présentation

**GitOps Template Lab** est un projet de référence pour mettre en place un workflow **GitOps sécurisé et observable** sur Kubernetes.

Ce template permet de :

- 📦 Déployer des applications et de l’infrastructure via Git  
- 🔁 Utiliser **ArgoCD** avec le pattern **App of Apps**  
- 🔐 Sécuriser les déploiements avec SealedSecrets, Kyverno et Cosign  
- 📊 Observer les clusters avec Prometheus, Grafana et Loki  
- 🛠️ Industrialiser les déploiements avec Helm, Kustomize et CI/CD  

Ce projet est **reproductible**, facile à cloner et adapté à tous les environnements Kubernetes.

---

## 🗂️ Structure du projet
la structure ici
---

## ⚡ Quick Start

1️⃣ Créer un cluster K3d  
```bash
k3d cluster create gitops-lab --agents 2
kubectl get nodes
```

2️⃣ Installer ArgoCD 
```bash
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

3️⃣ Appliquer les AppProjects
```bash
kubectl apply -f argocd/dev-project.yaml -n argocd
kubectl apply -f argocd/prod-project.yaml -n argocd
```
4️⃣ Déployer l’App of Apps
```bash
kubectl apply -f argocd/app-of-apps.yaml -n argocd
```
## 🔐 Sécurité GitOps

- Utiliser **SealedSecrets** ou **SOPS** pour les credentials  
- Configurer **RBAC ArgoCD** pour limiter les accès  
- Scanner les images avec **Trivy** et les signer avec **Cosign**  
- Appliquer des politiques **Kyverno** pour sécuriser les pods  
- ⚠️ **Ne jamais stocker de secrets en clair dans Git**

---

## 📊 Observabilité

- **Prometheus** : collecte des métriques du cluster et des applications  
- **Grafana** : dashboards préconfigurés pour visualiser les métriques  
- **Loki** : centralisation et agrégation des logs  
- **Alertmanager** : gestion des alertes en temps réel

---

## 🔄 CI/CD

- Build et push des images Docker  
- Scan de sécurité et signature des images  
- Auto-sync des applications via **ArgoCD**

---

## 📌 Contribution

- Fork du projet  
- Créer une branche `feature`  
- Soumettre une **Pull Request (PR)**  
- Respecter la structure GitOps  
- 📖 Voir le **Wiki** pour un guide complet
