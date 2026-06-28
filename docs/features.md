# Fonctionnalités Mantota

Ce document détaille les fonctionnalités de Mantota v1.0, déployées en production sur [mantota.com](https://mantota.com), ainsi que les fonctionnalités en développement pour la v2.0.

---

## 1. Authentification et gestion des comptes

- Inscription multi-rôles (Admin, Vendor, Influencer).
- Connexion sécurisée avec sessions chiffrées (lifetime 120 min).
- Récupération de mot de passe par e-mail.
- Gestion du profil utilisateur.
- KYC avec upload de documents et validation manuelle + robot.
- Guards séparés pour chaque rôle.

## 2. Module Vendor (Annonceur)

- Tableau de bord avec indicateurs clés.
- Création et gestion de campagnes publicitaires CPC.
- Fixation du budget et du prix par clic (min. 25 FCFA).
- Ciblage par pays, niche et tier d'influenceur.
- Gestion du catalogue produits (e-commerce).
- Suivi des commandes et des transactions.
- Gestion du wallet et des retraits.
- Analytics des campagnes et des ventes en temps réel.
- Anti-fraude : détection de bots, filtrage IP, géo-vérification.

## 3. Module Influencer (Créateur de contenu)

- Tableau de bord personnel.
- Découverte et postulation aux campagnes.
- Génération de liens de tracking (SmartLink) avec expiration 48h.
- Suivi des gains, commissions et solde séquestre.
- Gestion des services UGC proposés.
- Réception des commandes de contenu.
- Programme de parrainage (500 FCFA par filleul).
- Classement par tier : Bronze, Argent, Or.

## 4. Module E-commerce

- Boutique par vendeur.
- Catalogue produits avec images, prix, stock, galerie.
- Panier et commande pour les consommateurs.
- Paiement Mobile Money multigateway (FedaPay, PayDunya, FeexPay, Moneroo).
- Système d'escrow sécurisé.
- Suivi des commandes avec token public.
- Gestion des litiges et remboursements.

## 5. Module Wallet

- Dépôts via Mobile Money.
- Retraits avec vérification (min. 1 000 FCFA).
- Historique des transactions.
- Gestion des commissions et frais.
- Sécurité des transactions et audit logs.

## 6. Module Campagnes

- Création de campagnes CPC.
- Matching influenceurs / campagnes.
- Validation des livrables.
- Suivi des clics, vues, conversions.
- Calcul automatique des rémunérations.
- SmartLinks trackés et expirables.

## 7. Module Studio UGC

- Création de studios de contenu.
- Commande de vidéos / photos auprès de créateurs VIP.
- Workflow de validation.
- Livraison des fichiers.
- Paiement automatique après validation.
- Commission plateforme de 15%.

## 8. Module Feed Social (v1.0)

- Publication de posts par les vendors et influenceurs.
- Likes et commentaires (guest-first).
- Sessions live externes.
- Scoring du feed basé sur l'engagement.

## 9. Module KYC et Sécurité

- Vérification des identités.
- Validation des documents.
- Scoring de confiance des utilisateurs.
- Détection des fraudes.
- Gestion des litiges.
- Whitelist IP, audit logs, rate limiting.
- Score de sécurité global : 8/10.

## 10. Module Notifications

- Notifications par SMS.
- Notifications WhatsApp.
- Notifications e-mail.
- Notifications push WebSocket (via Laravel Reverb).
- Templates configurables par rôle.

## 11. Module Admin

- Panel d'administration sécurisé (URL secrète).
- Validation des KYC.
- Supervision des transactions.
- Gestion des commissions et frais (20+ paramètres).
- Modération des contenus.
- Ghost Mode pour le support client.
- Statistiques globales de la plateforme.

## 12. Modules Ambassador et Parrainage

- Programme d'ambassadeurs.
- Système de parrainage avec récompense.
- Suivi des conversions par filleul.

## 13. Roadmap IA (v2.0)

- Recommandation de créateurs pour les campagnes.
- Prédiction de performance des campagnes.
- Modération automatique des contenus.
- Vérification automatique des documents KYC.
- Assistant IA pour les utilisateurs.
- Détection de fraudes et anomalies.
- Analyse prédictive des tendances de consommation.

---

## Matrice rôles / fonctionnalités

| Fonctionnalité | Admin | Vendor | Influencer | Consommateur |
| :--- | :--- | :--- | :--- | :--- |
| Gestion des campagnes | :x: | :white_check_mark: | :white_check_mark: (postuler) | :x: |
| Gestion des produits | :x: | :white_check_mark: | :x: | :x: |
| Passer commande | :x: | :x: | :x: | :white_check_mark: |
| Wallet | :x: | :white_check_mark: | :white_check_mark: | :x: |
| KYC | :white_check_mark: (validation) | :white_check_mark: | :white_check_mark: | :x: |
| Analytics | :white_check_mark: | :white_check_mark: | :white_check_mark: | :x: |
| Feed / Publications | :x: | :white_check_mark: | :white_check_mark: | :white_check_mark: (lecture) |
| Admin panel | :white_check_mark: | :x: | :x: | :x: |

---

## Prochaines étapes

- [ ] Spécifications détaillées de l'API publique v2.0
- [ ] Maquettes des nouveaux écrans v2.0
- [ ] Dictionnaire de données complet
- [ ] Tests d'acceptation par rôle
- [ ] Architecture de migration v1.0 → v2.0
