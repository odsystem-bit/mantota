# Architecture Mantota

Ce document présente l'architecture générale de la plateforme Mantota. Il est destiné aux investisseurs, incubateurs et développeurs souhaitant comprendre les fondations techniques du projet.

> **Statut** : En cours de documentation. Certaines sections contiennent des placeholders qui seront complétés au fur et à mesure du développement.

---

## Vue d'ensemble

Mantota est une plateforme web monolithique modulaire construite autour d'une architecture **API-first** avec une interface frontend moderne et réactive.

```
┌─────────────────────────────────────────────────────────────┐
│                        Utilisateurs                         │
│  Admin    Vendor    Influencer    Consommateur    Visiteur  │
└──────────────────────┬────────────────────────────────────────┘
                       │
┌──────────────────────▼────────────────────────────────────────┐
│                     Frontend (Vue 3)                          │
│  Inertia.js · TailwindCSS · Vite · Ziggy                      │
└──────────────────────┬────────────────────────────────────────┘
                       │ HTTPS / API REST
┌──────────────────────▼────────────────────────────────────────┐
│                      Backend (Laravel)                          │
│  Auth · KYC · Wallet · Campagnes · E-commerce · UGC · IA    │
└──────────────────────┬────────────────────────────────────────┘
                       │
        ┌──────────────┼──────────────┬──────────────┐
        │              │              │              │
┌───────▼──────┐ ┌────▼─────┐ ┌──────▼──────┐ ┌──────▼──────┐
│   MySQL      │ │  Redis   │ │ File Storage│ │  Gateways   │
│  (données)   │ │ (cache)  │ │  (uploads)  │ │  (paiement) │
└──────────────┘ └──────────┘ └─────────────┘ └─────────────┘
```

---

## Couches applicatives

### 1. Présentation (Frontend)

- **Framework** : Vue 3 (Composition API)
- **Routage** : Inertia.js + Ziggy (routes Laravel)
- **Styling** : TailwindCSS v3
- **Build** : Vite 7
- **Composants** : bibliothèque interne avec shell commun `AppShell.vue`
- **Communication temps réel** : Laravel Echo + Reverb (WebSockets)

### 2. Logique métier (Backend)

- **Framework** : Laravel 12
- **Langage** : PHP 8.3+
- **Structure** : modules métier (Campagnes, E-commerce, Wallet, UGC, KYC, etc.)
- **Authentification** : guards séparés pour Admin, Vendor, Influencer
- **API** : RESTful, avec documentation progressive dans [`api.md`](api.md)

### 3. Données

- **Base de données principale** : MySQL
- **Cache** : Redis (sessions, files d'attente, cache applicatif)
- **Stockage** : stockage local et cloud (Cloudinary pour les médias)
- **Files d'attente** : Laravel Queues pour les tâches asynchrones

### 4. Paiements

- Intégration des gateways locales : Feexpay, Moneroo, etc.
- Support du Mobile Money (MTN, Moov, Wave)
- Système d'escrow pour les transactions e-commerce
- Gestion des commissions, frais de retrait et dépôts

### 5. Notifications

- SMS, WhatsApp, e-mail, push
- Files d'attente pour la fiabilité
- Templates personnalisables par rôle

---

## Modèle de sécurité

- Authentification multi-facteur (roadmap)
- Rôles et permissions granulaires (Spatie Laravel Permission)
- KYC avec vérification humaine et automatique
- Protection CSRF, XSS, SQL injection
- Sécurisation des fichiers et médias
- Journalisation des actions sensibles

---

## Scalabilité

Mantota est conçu pour évoluer :

- Architecture modulaire facilitant la migration vers des services séparés
- Caching par Redis
- Files d'attente pour décharger le serveur principal
- Base de données relationnelle optimisée pour les requêtes métier
- Hébergement initial sur Hostinger mutualisé, évolutif vers VPS ou cloud

---

## Environnements

| Environnement | Usage | Statut |
| :--- | :--- | :--- |
| Local | Développement | Actif |
| Staging | Tests et recettes | À venir |
| Production | Déploiement public | À venir |

---

## Dépendances externes

- Passerelles de paiement (Feexpay, Moneroo)
- Services de notification (Twilio, WhatsApp Business API)
- Stockage cloud (Cloudinary)
- Outils d'analyse (Google Analytics, outils internes)

---

## Prochaines étapes documentaires

- [ ] Schéma détaillé de la base de données
- [ ] Diagrammes de séquence des flux critiques
- [ ] Spécification des endpoints API
- [ ] Matrice des rôles et permissions
- [ ] Plan de déploiement et de monitoring
