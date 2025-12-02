# 📌 MSPR-Bloc-3-Sujet-Produire_et_maintenir_une_solution_I.A
📌 README – Projet ObRail Europe (MSPR – Industrialisation & Mise en Production)
🎯 Objectif du projet

Ce projet s’inscrit dans la certification professionnelle
RNCP36581 – Développeur en Intelligence Artificielle et Data Science
et constitue l’industrialisation du prototype réalisé dans la MSPR précédente.

L’objectif est de mettre en production une application complète, composée d’un :

Backend FastAPI

Frontend React

Base de données PostgreSQL

Monitoring (Grafana, Prometheus)

Pipeline CI/CD GitHub Actions

Conteneurisation complète avec Docker Compose

La solution doit être reproductible, testée, supervisée, sécurisée et conforme RGPD.

🧰 Technologies utilisées
🔙 Backend – Python

Frameworks & bibliothèques :

FastAPI — Création de l’API REST

SQLAlchemy — ORM & connexion PostgreSQL

Pydantic — Modèles & validation

requests — Appels externes éventuels

pandas — Manipulation des données

pytest — Tests unitaires & d’intégration

uvicorn — Serveur ASGI

Endpoints principaux :

Endpoint	Description
/trajets	Liste des trajets ferroviaires, filtres & pagination
/trajets/{id}	Détails d’un trajet
/stats/volumes	Statistiques jour/nuit, volumes par opérateur
/health	État du service (monitoring CI/CD)
🎨 Frontend – JavaScript / TypeScript

Framework utilisé :

React (TypeScript)

Vite — Build/dev server rapide

Axios — Appels API

Tailwind CSS — Style moderne, responsive, conforme RGAA

Cypress — Tests End-to-End

Jest (optionnel) — Tests unitaires de composants

Pages livrées :

Page Trajets (liste + filtres)

Page Statistiques (volumes, répartition jour/nuit, opérateurs)

Page Monitoring (latence API, erreurs, disponibilité)

Page Documentation (optionnel)

🗄 Base de données

PostgreSQL (base principale)

Schémas fournis par la MSPR précédente (TPRE512)

Connexion via SQLAlchemy + psycopg2

🐳 Conteneurisation & Orchestration

Docker

Docker Compose pour orchestrer :

Service	Port	Description
backend	8000	API FastAPI
frontend	3000	Interface React
postgres	5432	Base de données
grafana	4000	Monitoring
prometheus	9090	Scraping métriques

L’ensemble doit être démarré via :

docker-compose up --build

⚙️ CI/CD – GitHub Actions

Le pipeline CI/CD inclut :

CI — Intégration Continue

Installation des dépendances backend & frontend

Lancement des tests automatiques

Pytest (backend)

Cypress (frontend)

Build des images Docker

Analyse de qualité optionnelle (linting, mypy…)

CD — Livraison Continue

Publication des images Docker dans le GitHub Container Registry

Déploiement automatique sur environnement de test

📊 Supervision & Observabilité

L’application inclura :

Prometheus

métriques backend

latence

disponibilité

taux d’erreurs

Grafana

dashboard attractif

suivi du service API

graphique temps réel

logs (si Loki ajouté)

Métriques suivies :

Temps de réponse API

Nombre de requêtes

% erreurs 5xx / 4xx

Santé /health

Charge PostgreSQL

🧪 Tests automatisés
Backend – Pytest

Tests unitaires (services, modèles, validation)

Tests d’intégration (FastAPI + PostgreSQL mock)

Tests sur endpoints

Frontend – Cypress

Navigation (UI)

Filtres & affichage trajets

Graphiques & stats

Page monitoring

Les tests tournent automatiquement dans la CI/CD.

🧱 Architecture (aperçu rapide)
Diagramme C2 – Conteneurs (Mermaid)
flowchart LR
    subgraph Frontend["Container Frontend (React + TS)"]
        ReactApp["⚛️ React SPA"]
    end

    subgraph Backend["Container Backend (FastAPI)"]
        FastAPI["🧩 API REST FastAPI"]
    end

    subgraph DB["Container PostgreSQL"]
        Postgres["🗄 Base de données PostgreSQL"]
    end

    subgraph Monitoring["Monitoring (Grafana + Prometheus)"]
        Prometheus["📈 Prometheus"]
        Grafana["📊 Grafana"]
    end

    ReactApp -->|"Appels API REST"| FastAPI
    FastAPI -->|"Requêtes SQL"| Postgres
    Prometheus --> FastAPI
    Prometheus --> Postgres
    Grafana --> Prometheus

▶️ Démarrage du projet
1) Cloner le dépôt
git clone https://github.com/…/obrail-mspr.git
cd obrail-mspr

2) Lancer en local via Docker Compose
docker-compose up --build

3) Accéder aux services
Service	URL
Frontend	http://localhost:3000

Backend API	http://localhost:8000

Documentation Swagger	http://localhost:8000/docs

Grafana	http://localhost:4000

Prometheus	http://localhost:9090
👥 Répartition du travail (équipe)
1️⃣ Backend Lead

FastAPI, SQLAlchemy, tests Pytest, documentation OpenAPI

2️⃣ Frontend Lead

React, Axios, pages, UI/UX, tests Cypress, accessibilité RGAA

3️⃣ DevOps / CI/CD

Dockerfiles, docker-compose, GitHub Actions, registry

4️⃣ Monitoring Lead

Grafana, Prometheus, métriques, intégration logs

5️⃣ Documentation / Rapport / Soutenance

Architecture, RGPD, sécurité, pipeline CI/CD, slides

📄 Livrables

Application complète via Docker Compose

Backend + frontend + base + monitoring

Pipeline GitHub Actions fonctionnel

Tests automatisés

Dashboard Grafana

Rapport technique complet

Support de soutenance
