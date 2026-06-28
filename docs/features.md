# Fonctionnalités Mantota

Ce document détaille les fonctionnalités principales de Mantota, organisées par module et par rôle utilisateur.

> **Statut** : En cours de documentation. Les placeholders seront remplacés par des spécifications détaillées.

---

## 1. Authentification et gestion des comptes

- Inscription avec vérification d'identité
- Connexion multi-rôles (Admin, Vendor, Influencer)
- Récupération de mot de passe sécurisée
- Gestion du profil utilisateur
- KYC avec upload de documents et validation

## 2. Module Vendor (Annonceur)

- Tableau de bord avec indicateurs clés
- Création et gestion de campagnes publicitaires
- Gestion du catalogue produits (e-commerce)
- Suivi des commandes et des transactions
- Gestion du wallet et des retraits
- Analytics des campagnes et des ventes

## 3. Module Influencer (Créateur de contenu)

- Tableau de bord personnel
- Découverte et postulation aux campagnes
- Génération de liens de tracking (SmartLink)
- Suivi des gains et des commissions
- Gestion des services UGC proposés
- Réception des commandes de contenu
- Parrainage et programme d'ambassadeur

## 4. Module E-commerce

- Boutique par vendeur
- Catalogue produits avec images, prix, stock
- Panier et commande pour les consommateurs
- Paiement Mobile Money multigateway
- Système d'escrow sécurisé
- Suivi des commandes avec token public
- Gestion des litiges et remboursements

## 5. Module Wallet

- Dépôts via Mobile Money
- Retraits avec vérification
- Historique des transactions
- Gestion des commissions et frais
- Sécurité des transactions

## 6. Module Campagnes

- Création de campagnes (CPC, CPM, objectifs personnalisés)
- Matching influenceurs / campagnes
- Validation des livrables
- Suivi des clics, vues, conversions
- Calcul automatique des rémunérations

## 7. Module Studio UGC

- Création de studios de contenu
- Commande de vidéos / photos auprès de créateurs
- Workflow de validation
- Livraison des fichiers
- Paiement automatique après validation

## 8. Module KYC et Sécurité

- Vérification des identités
- Validation des documents
- Scoring de confiance des utilisateurs
- Détection des fraudes
- Gestion des litiges

## 9. Module Notifications

- Notifications par SMS
- Notifications WhatsApp
- Notifications e-mail
- Notifications push (application mobile, roadmap)
- Templates configurables

## 10. Module Admin

- Panel d'administration sécurisé
- Validation des KYC
- Supervision des transactions
- Gestion des commissions et frais
- Modération des contenus
- Statistiques globales de la plateforme

## 11. Roadmap IA (fonctionnalités futures)

- Recommandation de créateurs pour les campagnes
- Prédiction de performance des campagnes
- Modération automatique des contenus
- Assistant IA pour les utilisateurs
- Analyse prédictive des tendances de consommation

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

---

## Prochaines étapes

- [ ] Spécifications détaillées de chaque module
- [ ] Maquettes et parcours utilisateurs
- [ ] Dictionnaire des données
- [ ] Tests d'acceptation par module
