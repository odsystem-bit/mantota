<div align="center">
  <img src="assets/banner.svg" alt="Mantota Banner" width="100%" />
</div>

<div align="center">
  <img src="assets/logo/logo-placeholder.svg" alt="Mantota Logo" width="120" height="120" />
  <h1>Mantota</h1>
  <p><strong>Plateforme de marketing d'influence et d'e-commerce intelligent pour l'Afrique de l'Ouest</strong></p>
  <p>
    <img src="https://img.shields.io/badge/Status-En%20production%20%28v1.0%29%20%2F%20v2.0%20en%20dev-2A8A1A?style=flat-square" alt="Status" />
    <img src="https://img.shields.io/badge/Version-1.0.0-1D3C6E?style=flat-square" alt="Version" />
    <img src="https://img.shields.io/badge/License-MIT-F5A800?style=flat-square" alt="License" />
    <img src="https://img.shields.io/badge/Afrique%20de%20l'Ouest-FCFA-1D3C6E?style=flat-square" alt="Marché" />
  </p>
</div>

---

## Table des matières

- [Présentation](#présentation)
- [Le problème](#le-problème)
- [La solution](#la-solution)
- [Fonctionnalités principales](#fonctionnalités-principales)
- [Architecture générale](#architecture-générale)
- [Technologies utilisées](#technologies-utilisées)
- [Feuille de route](#feuille-de-route)
- [Captures d'écran](#captures-décran)
- [Démo](#démo)
- [Liens officiels](#liens-officiels)
- [Contact](#contact)

---

## Présentation

**Mantota** est le premier réseau publicitaire 100% performance en Afrique francophone, connectant vendeurs (annonceurs) et créateurs de contenu (influenceurs) via un modèle basé sur le **Coût Par Clic (CPC)** et la **Commission Par Vente (CPA)**.

La **version 1.0 est en production** sur [mantota.com](https://mantota.com) avec environ **120 utilisateurs actifs**. La **version 2.0** est en développement pour renforcer la scalabilité, l'IA et l'expérience utilisateur.

Mantota combine :
- Une **marketplace** de campagnes publicitaires CPC entre annonceurs et influenceurs.
- Un **module e-commerce** avec escrow et paiement Mobile Money.
- Des **studios UGC** pour la production de contenu sponsorisé.
- Un **système KYC** et de scoring pour la confiance entre acteurs.
- Un **wallet intégré** avec dépôts, retraits et commissions.
- Une **roadmap IA** pour le matching, le scoring et la modération automatique.

---

## Le problème

En Afrique de l'Ouest, les marques et les PME peinent à :
- Identifier et collaborer avec des créateurs de contenu pertinents localement.
- Sécuriser les paiements et les livraisons dans l'e-commerce.
- Mesurer le retour sur investissement de leurs campagnes d'influence.
- Accéder à des outils numériques adaptés aux réalités locales (Mobile Money, FCFA, faible bancarisation).

Les créateurs de contenu, quant à eux, manquent d'une plateforme structurée pour monétiser leur audience, recevoir des commandes et gérer leur activité professionnellement.

---

## La solution

Mantota propose un **écosystème unifié** qui répond à ces défis :

- **Pour les Vendors (annonceurs)** : créer des campagnes CPC, fixer le budget, choisir les pays et niches, suivre les performances en temps réel et vendre des produits via une boutique intégrée.
- **Pour les Influencers (créateurs)** : postuler à des campagnes, générer des SmartLinks trackés, gérer un wallet, proposer des services UGC et bénéficier d'un programme de parrainage.
- **Pour les consommateurs** : acheter des produits locaux en toute confiance avec un système de paiement sécurisé et un suivi de commandes.
- **Pour l'administration** : un panneau de contrôle sécurisé pour valider les KYC, superviser les transactions et garantir le bon fonctionnement de la plateforme.

---

## Fonctionnalités principales

### Pour les Vendors
- **Campagnes CPC** : création, budget, prix par clic (min. 25 FCFA), ciblage par pays/niche/tier.
- **Marketplace e-commerce** : boutique, catalogue, stock, galerie d'images, livraison.
- **Tableau de bord en temps réel** : clics payés, clics totaux, conversions, budget restant.
- **Anti-fraude** : détection de bots, filtrage IP dupliquées, géo-vérification.
- **Escrow** : fonds bloqués jusqu'à confirmation de livraison.

### Pour les Influencers
- **SmartLinks** : liens trackés uniques avec expiration 48h.
- **Dashboard personnalisé** : campagnes filtrées par niche et tier (Bronze, Argent, Or).
- **Wallet** : solde disponible, solde en attente, solde séquestre.
- **Mantota Studios (VIP)** : vente de services UGC (vidéos humaines, vidéos pub IA).
- **Retraits** : via Mobile Money (FedaPay, PayDunya, FeexPay).
- **Parrainage** : 500 FCFA par filleul inscrit.

### Pour l'Administration
- **Dashboard KPI** : utilisateurs, dépôts, retraits, profits en temps réel.
- **Modération KYC** : vérification d'identité avec robot + validation manuelle.
- **Ghost Mode** : impersonation sécurisée pour le support.
- **Paramètres configurables** : 20+ paramètres (commissions, seuils, frais).
- **Sécurité** : whitelist IP, audit logs, rate limiting.

Pour plus de détails, consulter :
- [`docs/architecture.md`](docs/architecture.md)
- [`docs/features.md`](docs/features.md)
- [`docs/business-model.md`](docs/business-model.md)
- [`docs/ai-roadmap.md`](docs/ai-roadmap.md)
- [`docs/api.md`](docs/api.md)
- [`docs/faq.md`](docs/faq.md)

---

## Architecture générale

Mantota repose sur une architecture monolithique modulaire, moderne et évolutive :

- **Backend** : Laravel 12, API REST, base de données MySQL, Redis (cache/sessions/queues), WebSockets via Laravel Reverb.
- **Frontend** : Vue 3 avec Inertia.js, TailwindCSS v3, Vite 7, Ziggy.
- **Paiements** : intégration multi-gateway (FedaPay, PayDunya, FeexPay, Moneroo) avec Mobile Money.
- **Médias** : Cloudinary pour le stockage des images et vidéos.
- **Infrastructure** : hébergement mutualisé Hostinger en production, migration vers VPS/cloud prévue pour la v2.0.

Pour plus de détails, consulter [`docs/architecture.md`](docs/architecture.md).

---

## Technologies utilisées

### Backend
![Laravel](https://img.shields.io/badge/Laravel-FF2D20?style=for-the-badge&logo=laravel&logoColor=white)
![PHP](https://img.shields.io/badge/PHP-777BB4?style=for-the-badge&logo=php&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white)

### Frontend
![Vue.js](https://img.shields.io/badge/Vue.js-4FC08D?style=for-the-badge&logo=vue.js&logoColor=white)
![Inertia.js](https://img.shields.io/badge/Inertia.js-8A6FDF?style=for-the-badge&logo=inertia&logoColor=white)
![TailwindCSS](https://img.shields.io/badge/TailwindCSS-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=for-the-badge&logo=vite&logoColor=white)

### DevOps & Outils
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![Cloudinary](https://img.shields.io/badge/Cloudinary-3448C5?style=for-the-badge&logo=cloudinary&logoColor=white)

---

## Feuille de route

| Phase | Objectif | Statut |
| :--- | :--- | :--- |
| **v1.0** | Fondation, authentification, KYC, wallet, campagnes CPC, e-commerce, UGC | ✅ En production |
| **v1.x** | Stabilisation, optimisations, 120+ utilisateurs actifs | ✅ En cours |
| **v2.0** | Scalabilité, migration VPS/cloud, refonte UX, API publique | En développement |
| **v2.1** | Intelligence artificielle : matching, scoring, modération, assistant | À venir |
| **v2.2** | Expansion régionale (CI, Sénégal, Togo, Cameroun) | À venir |

Consulter [`ROADMAP.md`](ROADMAP.md) et [`docs/ai-roadmap.md`](docs/ai-roadmap.md) pour le détail.

---

## Captures d'écran

> Les captures d'écran seront ajoutées progressivement dans le dossier [`assets/screenshots/`](assets/screenshots/).

<div align="center">
   <p><em>Dashboard Mantota — placeholder</em></p>
  <img src="assets/screenshots/Capture d'écran 2026-06-09 211130.png" alt="Dashboard placeholder" width="80%" />
    <img src="assets/screenshots/Capture d'écran 2026-06-09 211245.png" alt="Dashboard placeholder" width="80%" />
     <img src="assets/screenshots/Capture d'écran 2026-06-09 215808.png" alt="Dashboard placeholder" width="80%" />
      <img src="assets/screenshots/Capture d'écran 2026-06-09 211546.png" alt="Dashboard placeholder" width="80%" />
       <img src="assets/screenshots/Capture d'écran 2026-06-09 211702.png" alt="Dashboard placeholder" width="80%" />
        <img src="assets/screenshots/Capture d'écran 2026-06-09 215833.png" alt="Dashboard placeholder" width="80%" />
         <img src="assets/screenshots/Capture d'écran 2026-06-09 215846.png" alt="Dashboard placeholder" width="80%" />
          <img src="assets/screenshots/Capture d'écran 2026-06-09 215931.png" alt="Dashboard placeholder" width="80%" />
           <img src="assets/screenshots/Capture d'écran 2026-06-09 211521.png" alt="Dashboard placeholder" width="80%" />
            <img src="assets/screenshots/Capture d'écran 2026-06-09 211216.png" alt="Dashboard placeholder" width="80%" />

   <p><em>Prochaine mise a jour</em></p>
  <img src="assets/screenshots/Capture d'écran 2026-06-10 205317.png" alt="Dashboard placeholder" width="80%" />
</div>

---

## Démo

- **Site en production** : [mantota.com](https://mantota.com)
- **Démo et maquettes** : disponibles prochainement dans le dossier [`demo/`](demo/).

---

## Liens officiels

- **Site web** : [mantota.com](https://mantota.com)
- **Documentation** : [`docs/`](docs/)
- **Portfolio** : [stanislas-nouemou](https://github.com/odsystem-bit/stanislas-nouemou)
- **GitHub** : [mantota](https://github.com/odsystem-bit/mantota)

---

## Contact

Pour toute question, partenariat ou opportunité d'investissement :

- **Email** : [contact@mantota.com](mailto:contact@mantota.com)
- **LinkedIn** : [À compléter](https://linkedin.com/in/)
- **GitHub** : [@odsystem-bit](https://github.com/odsystem-bit)

---

<div align="center">
  <sub>Mantota — Construire l'avenir du digital en Afrique de l'Ouest.</sub>
</div>
