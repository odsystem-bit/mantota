# Architecture Mantota

Ce document présente l'architecture de la plateforme Mantota, de la version 1.0 en production à la version 2.0 en développement.

---

## Vue d'ensemble

### Version 1.0 (production)

Mantota v1.0 est une plateforme web monolithique modulaire construite avec Laravel 12 et Vue 3, déployée en production sur hébergement mutualisé Hostinger.

```
┌─────────────────────────────────────────────────────────────┐
│  Admin · Vendor · Influencer · Consommateur · Visiteur      │
└──────────────────────┬────────────────────────────────────────┘
                       │
┌──────────────────────▼────────────────────────────────────────┐
│  Frontend (Vue 3 + Inertia.js + TailwindCSS v3 + Vite 7)    │
│  AppShell · Bottom nav TikTok-style · Sidebar desktop         │
└──────────────────────┬────────────────────────────────────────┘
                       │ HTTPS / API REST
┌──────────────────────▼────────────────────────────────────────┐
│  Backend (Laravel 12 · PHP 8.3+)                              │
│  Auth · KYC · Wallet · Campagnes · E-commerce · UGC · Feed  │
└──────────────────────┬────────────────────────────────────────┘
                       │
        ┌──────────────┼──────────────┬──────────────┐
        │              │              │              │
┌───────▼──────┐ ┌──────▼─────┐ ┌──────▼──────┐ ┌──────▼──────┐
│   MySQL      │ │  Redis     │ │  Cloudinary │ │  Gateways   │
│  (données)   │ │ (cache/    │ │  (médias)   │ │  (Mobile   │
│              │ │  sessions) │ │             │ │  Money)     │
└──────────────┘ └────────────┘ └─────────────┘ └─────────────┘
```

### Version 2.0 (cible)

La v2.0 vise à migrer vers une infrastructure plus scalable (VPS/cloud) avec :

- Load balancer + 3-5 serveurs applicatifs
- MySQL dédié ou PostgreSQL avec réplication
- Redis cluster pour cache et sessions
- CDN pour les assets
- Monitoring Prometheus / Grafana
- CI/CD automatisé

---

## Couches applicatives

### 1. Présentation (Frontend)

- **Framework** : Vue 3 (Composition API)
- **Routage** : Inertia.js + Ziggy (routes Laravel)
- **Styling** : TailwindCSS v3
- **Build** : Vite 7
- **UX** : shell commun `AppShell.vue`, bottom nav TikTok-style (mobile), sidebar desktop
- **Temps réel** : Laravel Echo + Reverb (WebSockets) pour notifications et feed

### 2. Logique métier (Backend)

- **Framework** : Laravel 12
- **Langage** : PHP 8.3+ (PHP 8.5 en local)
- **Structure** : modules métier (Campagnes, E-commerce, Wallet, UGC, KYC, Feed, Ambassador, Parrainage)
- **Authentification** : guards séparés pour Admin, Vendor, Influencer
- **API** : RESTful avec Sanctum, documentation progressive dans [`api.md`](api.md)

### 3. Données

- **Base de données principale** : MySQL 5.7
- **Cache** : Redis (sessions, files d'attente, cache applicatif)
- **Stockage** : Cloudinary pour les médias, stockage local pour les documents KYC
- **Files d'attente** : Laravel Queues (driver DB en production actuellement)

### 4. Paiements

- **Gateways** : FedaPay, PayDunya, FeexPay, Moneroo
- **Mobile Money** : MTN, Moov, Wave, Orange Money
- **Escrow** : fonds bloqués jusqu'à confirmation de livraison
- **Commissions** : 5% campagnes, 20% retraits, 1.5% dépôts, 15% UGC

### 5. Notifications

- SMS, WhatsApp, e-mail, push WebSocket
- Files d'attente pour la fiabilité
- Templates personnalisables par rôle

---

## Modèle de sécurité

### Forces actuelles (v1.0)

- **Authentification multi-garde** : sessions séparées pour web, admin, vendor, influencer.
- **Sessions chiffrées** : stockées en base avec lifetime de 120 minutes.
- **Protection CSRF** : activée partout sauf webhooks signés (HMAC-SHA256).
- **En-têtes de sécurité** : X-Frame-Options, HSTS, CSP, X-Content-Type-Options.
- **Validation rigoureuse** : types MIME, tailles max, dates, uploads sécurisés.
- **Rate limiting** : throttling sur auth (5/1min), vérifications (6/1min), actions sensibles.
- **Middleware personnalisés** : blocage IP, permissions admin, vérification bannissement.
- **Stockage fichiers** : documents KYC stockés localement (non publics).
- **Logs sécurisés** : aucune donnée sensible (mots de passe, cartes) dans les logs.
- **Escrow** : fonds bloqués jusqu'à confirmation de livraison.
- **Score global** : 8/10.

### Améliorations en cours (v2.0)

- Authentification multi-facteur (2FA) pour admins et comptes sensibles.
- Renforcement CSP (suppression `unsafe-inline`, ajout de nonces).
- WAF externe et monitoring des tentatives de connexion.
- Audit logs immuables.
- API publique sécurisée avec Sanctum.

---

## Scalabilité

### v1.0 (production actuelle)

- Hébergement mutualisé Hostinger.
- MySQL 5.7, Redis pour cache/sessions.
- Optimisé pour la charge actuelle (~120 utilisateurs actifs).
- Limites identifiées : driver de queue DB, SQLite non utilisé, mono-instance.

### v2.0 (cible)

- Migration vers VPS/cloud (Contabo, AWS, DigitalOcean).
- MySQL dédié ou PostgreSQL avec réplication.
- Redis cluster pour cache et sessions.
- Load balancer + 3-5 serveurs applicatifs.
- CDN pour les assets.
- Monitoring Prometheus / Grafana.
- CI/CD automatisé.

### Niveaux de scalabilité

| Niveau | Utilisateurs simultanés | Infrastructure | Coût indicatif |
| :--- | :--- | :--- | :--- |
| Niveau 1 | 500 | VPS 4-8 CPU, 8-16 GB RAM, Redis local | 15 000-30 000 FCFA/mois |
| Niveau 2 | 200-500 | MySQL dédié + Redis externe + CDN | 5 000-15 000 FCFA/mois |
| Niveau 3 | 2000+ | Load balancer + 3-5 serveurs, RDS, Redis cluster | 50 000-150 000 FCFA/mois |

---

## Environnements

| Environnement | Usage | Statut |
| :--- | :--- | :--- |
| Local | Développement v2.0 | Actif |
| Production v1.0 | [mantota.com](https://mantota.com) | Actif |
| Staging v2.0 | Tests et recettes | À venir |
| Production v2.0 | Plateforme scalable | À venir |

---

## Dépendances externes

- Passerelles de paiement : FedaPay, PayDunya, FeexPay, Moneroo.
- Services de notification : WhatsApp Business API, SMS, e-mail.
- Stockage cloud : Cloudinary.
- Outils d'analyse : Google Analytics, outils internes.

---

## Prochaines étapes documentaires

- [ ] Schéma détaillé de la base de données v1.0
- [ ] Diagrammes de séquence des flux critiques (paiement, escrow, KYC)
- [ ] Spécification complète de l'API publique v2.0
- [ ] Matrice des rôles et permissions
- [ ] Plan de migration v1.0 → v2.0 (zero downtime)
- [ ] Plan de déploiement cloud et de monitoring
