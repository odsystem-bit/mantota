# API Mantota

Ce document décrit les API de Mantota v1.0 (internes) et la roadmap de l'API publique v2.0.

---

## Introduction

Mantota v1.0 expose une API REST interne utilisée par le frontend Inertia.js/Vue 3. L'API publique v2.0 permettra aux développeurs et partenaires d'intégrer la plateforme dans leurs propres outils.

---

## Authentification v1.0

Les utilisateurs du frontend sont authentifiés via des **sessions Laravel** sécurisées. Chaque rôle (Admin, Vendor, Influencer) dispose d'un guard dédié.

## Authentification v2.0 (publique)

L'API publique utilisera **Laravel Sanctum** avec des tokens Bearer.

```http
Authorization: Bearer {token}
```

---

## En-têtes communs v2.0

```http
Content-Type: application/json
Accept: application/json
Authorization: Bearer {token}
```

---

## Versionnement v2.0

L'API publique sera versionnée dans l'URL :

```
https://api.mantota.com/v1/
```

---

## Endpoints v1.0 (internes)

### Authentification

| Méthode | Endpoint | Description |
| :--- | :--- | :--- |
| POST | `/api/auth/login` | Se connecter |
| POST | `/api/auth/register` | Créer un compte |
| GET | `/api/auth/me` | Profil connecté |
| PUT | `/api/auth/profile` | Mettre à jour le profil |
| POST | `/api/auth/logout` | Se déconnecter |

### Campagnes

| Méthode | Endpoint | Description |
| :--- | :--- | :--- |
| GET | `/api/campaigns` | Lister les campagnes disponibles |
| GET | `/api/campaigns/{campaign}` | Détails d'une campagne |
| POST | `/api/campaigns/{campaign}/promote` | Générer un SmartLink |

### Feed

| Méthode | Endpoint | Description |
| :--- | :--- | :--- |
| GET | `/api/feed` | Récupérer le feed social |
| POST | `/api/feed/{post}/view` | Enregistrer une vue |
| POST | `/api/feed/{post}/like` | Liker un post (guest-first) |
| GET | `/api/feed/{post}/comments` | Lister les commentaires |
| POST | `/api/feed/{post}/comments` | Commenter un post |

### Wallet

| Méthode | Endpoint | Description |
| :--- | :--- | :--- |
| GET | `/api/wallet` | Solde et résumé |
| GET | `/api/wallet/transactions` | Historique des transactions |
| POST | `/api/wallet/withdraw` | Demander un retrait |
| POST | `/api/wallet/deposit` | Effectuer un dépôt |

### Commandes

| Méthode | Endpoint | Description |
| :--- | :--- | :--- |
| GET | `/api/orders` | Lister les commandes |
| GET | `/api/orders/{order}` | Détails d'une commande |
| POST | `/api/orders/guest` | Commander en tant qu'invité |
| GET | `/api/orders/track/{token}` | Suivre une commande publiquement |

### KYC

| Méthode | Endpoint | Description |
| :--- | :--- | :--- |
| GET | `/api/kyc` | Statut KYC |
| POST | `/api/kyc` | Soumettre les documents KYC |

### Notifications

| Méthode | Endpoint | Description |
| :--- | :--- | :--- |
| GET | `/api/notifications` | Lister les notifications |
| POST | `/api/notifications/{id}/read` | Marquer comme lue |
| POST | `/api/notifications/read-all` | Tout marquer comme lu |

### Produits et Créateurs

| Méthode | Endpoint | Description |
| :--- | :--- | :--- |
| GET | `/api/products` | Lister les produits |
| GET | `/api/products/{product}` | Détails d'un produit |
| GET | `/api/creators/{slug}` | Profil public d'un créateur |

---

## Endpoints v2.0 (publique — roadmap)

| Méthode | Endpoint | Description |
| :--- | :--- | :--- |
| GET | `/v1/campaigns` | Lister les campagnes publiques |
| GET | `/v1/campaigns/{id}` | Détails d'une campagne |
| POST | `/v1/campaigns/{id}/apply` | Postuler à une campagne |
| GET | `/v1/products` | Lister les produits |
| GET | `/v1/products/{id}` | Détails d'un produit |
| POST | `/v1/orders` | Créer une commande |
| GET | `/v1/orders/track/{token}` | Suivre une commande |
| GET | `/v1/wallet` | Solde et transactions |
| POST | `/v1/wallet/deposit` | Déposer des fonds |
| POST | `/v1/wallet/withdraw` | Retirer des fonds |
| GET | `/v1/creators` | Lister les créateurs |
| GET | `/v1/creators/{slug}` | Profil public d'un créateur |

---

## Codes de réponse

| Code | Signification |
| :--- | :--- |
| 200 | Succès |
| 201 | Ressource créée |
| 400 | Requête invalide |
| 401 | Non authentifié |
| 403 | Non autorisé |
| 404 | Ressource non trouvée |
| 422 | Erreur de validation |
| 500 | Erreur serveur |

---

## Pagination

> Les réponses listes v2.0 supporteront la pagination standard Laravel avec `data` et `meta`.

---

## Exemple de requête v2.0

```bash
curl -X GET https://api.mantota.com/v1/campaigns \
  -H "Authorization: Bearer {token}" \
  -H "Accept: application/json"
```

---

## Exemple de réponse v2.0

```json
{
  "data": [
    {
      "id": 1,
      "title": "Campagne été 2026",
      "budget": 500000,
      "currency": "XOF",
      "status": "active",
      "created_at": "2026-06-28T10:00:00Z"
    }
  ],
  "meta": {
    "current_page": 1,
    "last_page": 5,
    "total": 48
  }
}
```

---

## Limites d'utilisation

> Les rate limits et quotas par type de compte seront définis dans la v2.0.

---

## Prochaines étapes

- [ ] Documenter les schémas complets de requête et réponse v1.0
- [ ] Rédiger les spécifications d'authentification Sanctum v2.0
- [ ] Documenter les webhooks et signatures des paiements
- [ ] Publier une collection Postman publique
- [ ] Définir la rate limiting et les plans d'API
- [ ] Mettre en place une documentation interactive (Swagger / Scribe)
