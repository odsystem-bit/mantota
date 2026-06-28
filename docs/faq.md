# FAQ Mantota

## Général

### Qu'est-ce que Mantota ?

Mantota est le premier réseau publicitaire 100% performance en Afrique francophone. Elle connecte les vendeurs (annonceurs), les créateurs de contenu (influenceurs) et les consommateurs dans un écosystème sécurisé, transparent et adapté aux paiements Mobile Money.

### Quel problème Mantota résout-il ?

Mantota résout le manque de plateforme locale adaptée aux réalités africaines : paiement Mobile Money, ciblage géographique, escrow, anti-fraude et modèle de performance (CPC/CPA).

### Qui peut utiliser Mantota ?

- **Vendors** : PME et e-commerçants qui veulent promouvoir ou vendre des produits.
- **Influencers** : créateurs de contenu qui veulent monétiser leur audience.
- **Consommateurs** : acheteurs qui veulent acheter des produits locaux en toute confiance.
- **Admins** : équipe de modération et de support de la plateforme.

### Mantota est-il déjà en ligne ?

Oui, la version 1.0 est en production sur [mantota.com](https://mantota.com) avec environ **120 utilisateurs actifs**. La version 2.0 est en développement.

---

## Pour les annonceurs (Vendors)

### Comment créer une campagne ?

Rendez-vous sur votre dashboard Vendor, cliquez sur "Nouvelle campagne", définissez le budget, le prix par clic (minimum 25 FCFA), les pays et niches cibles, puis publiez.

### Comment payer les influenceurs ?

Les paiements sont automatiques via le wallet intégré. Les influenceurs gagnent des commissions sur les clics valides et les conversions.

### Quels sont les frais de commission ?

- **Commission sur campagnes** : 5% sur le budget.
- **Commission plateforme** : 20% sur les retraits.
- **Markup sur dépôts** : 1.5%.
- **Commission UGC** : 15% sur les commandes de contenu.
- **Commission e-commerce** : variable selon les ventes.

---

## Pour les influenceurs

### Comment postuler à une campagne ?

Depuis votre dashboard Influencer, consultez les campagnes disponibles, filtrez par niche et tier, puis cliquez sur "Postuler".

### Comment suis-je rémunéré ?

Les gains sont crédités sur votre wallet Mantota. Vous pouvez demander un retrait vers votre compte Mobile Money (minimum 1 000 FCFA, commission 20%).

### Qu'est-ce que le Studio UGC ?

Le Studio UGC permet aux influenceurs VIP de proposer des services de création de contenu (vidéos humaines, vidéos pub IA) à la demande des annonceurs.

### Qu'est-ce qu'un SmartLink ?

Un SmartLink est un lien de promotion unique généré pour chaque influenceur. Il est tracké et expire après 48 heures.

---

## E-commerce

### Comment fonctionne l'escrow ?

Lors d'un achat, l'argent est conservé par Mantota jusqu'à la confirmation de la livraison par l'acheteur. Le vendeur est ensuite payé.

### Quels modes de paiement sont acceptés ?

Mantota intègre les paiements Mobile Money (MTN, Moov, Wave, Orange Money) via des gateways locales : FedaPay, PayDunya, FeexPay, Moneroo.

### Comment suivre ma commande ?

Chaque commande dispose d'un token de suivi unique. Vous pouvez le partager avec vos clients pour un suivi public via `/api/orders/track/{token}`.

---

## Sécurité et KYC

### Pourquoi dois-je vérifier mon identité ?

La vérification KYC garantit la confiance entre les utilisateurs et sécurise les transactions financières. La validation combine un robot et une vérification manuelle.

### Mes données sont-elles sécurisées ?

Oui, Mantota applique les bonnes pratiques de sécurité : sessions chiffrées, protection CSRF, rate limiting, whitelist IP, audit logs et stockage local des documents KYC. Le score de sécurité global est de **8/10**.

---

## Intelligence artificielle

### Quel rôle l'IA joue-t-elle dans Mantota ?

L'IA est planifiée pour la v2.1 : recommandation de créateurs, prédiction des performances, modération automatique, vérification KYC, assistant IA et détection de fraudes.

### L'IA remplace-t-elle les humains ?

Non. L'IA aide à automatiser certaines tâches, mais les décisions critiques (validation KYC, litiges) restent supervisées par l'équipe Mantota.

---

## Support et contact

### Comment contacter l'équipe ?

Vous pouvez nous contacter via les coordonnées disponibles dans le [`README.md`](../README.md).

### Où trouver la documentation technique ?

La documentation est disponible dans le dossier [`docs/`](./).

---

## Questions non listées ?

Ouvrez une issue sur GitHub ou contactez-nous directement. Nous enrichirons cette FAQ au fur et à mesure des retours.
