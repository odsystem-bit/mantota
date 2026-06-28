# API Mantota

Ce document décrit l'API publique de Mantota. Il est en cours de rédaction et sera enrichi au fur et à mesure du développement.

> **Statut** : Version préliminaire. Les endpoints, formats et authentification sont susceptibles d'évoluer.

---

## Introduction

L'API Mantota permet aux développeurs et partenaires d'intégrer la plateforme dans leurs propres outils. Elle repose sur une architecture RESTful avec authentification par tokens.

---

## Authentification

> **À compléter** : méthode d'authentification (OAuth 2.0, API Key, Sanctum, etc.).

```http
Authorization: Bearer {token}
```

---

## En-têtes communs

```http
Content-Type: application/json
Accept: application/json
Authorization: Bearer {token}
```

---

## Versionnement

L'API est versionnée dans l'URL :

```
https://api.mantota.com/v1/
```

---

## Endpoints

### Authentification

| Méthode | Endpoint | Description |
| :--- | :--- | :--- |
| POST | `/v1/auth/register` | Créer un compte |
| POST | `/v1/auth/login` | Se connecter |
| POST | `/v1/auth/logout` | Se déconnecter |
| GET | `/v1/auth/me` | Profil connecté |

### Campagnes

| Méthode | Endpoint | Description |
| :--- | :--- | :--- |
| GET | `/v1/campaigns` | Lister les campagnes |
| GET | `/v1/campaigns/{id}` | Détails d'une campagne |
| POST | `/v1/campaigns` | Créer une campagne |
| PUT | `/v1/campaigns/{id}` | Mettre à jour une campagne |
| DELETE | `/v1/campaigns/{id}` | Supprimer une campagne |
| POST | `/v1/campaigns/{id}/apply` | Postuler à une campagne |

### Produits

| Méthode | Endpoint | Description |
| :--- | :--- | :--- |
| GET | `/v1/products` | Lister les produits |
| GET | `/v1/products/{id}` | Détails d'un produit |
| POST | `/v1/products` | Créer un produit |
| PUT | `/v1/products/{id}` | Mettre à jour un produit |
| DELETE | `/v1/products/{id}` | Supprimer un produit |

### Commandes

| Méthode | Endpoint | Description |
| :--- | :--- | :--- |
| GET | `/v1/orders` | Lister les commandes |
| GET | `/v1/orders/{id}` | Détails d'une commande |
| POST | `/v1/orders` | Passer une commande |
| GET | `/v1/orders/track/{token}` | Suivre une commande publiquement |

### Wallet

| Méthode | Endpoint | Description |
| :--- | :--- | :--- |
| GET | `/v1/wallet` | Solde du wallet |
| GET | `/v1/wallet/transactions` | Historique des transactions |
| POST | `/v1/wallet/deposit` | Déposer des fonds |
| POST | `/v1/wallet/withdraw` | Retirer des fonds |

### Influencers

| Méthode | Endpoint | Description |
| :--- | :--- | :--- |
| GET | `/v1/creators` | Lister les créateurs |
| GET | `/v1/creators/{slug}` | Profil public d'un créateur |
| GET | `/v1/creators/{id}/services` | Services UGC proposés |

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

> **À compléter** : format de pagination des réponses listes.

---

## Exemple de requête

```bash
curl -X GET https://api.mantota.com/v1/campaigns \
  -H "Authorization: Bearer {token}" \
  -H "Accept: application/json"
```

---

## Exemple de réponse

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

> **À compléter** : rate limits et quotas par type de compte.

---

## Prochaines étapes

- [ ] Définir les schémas complets de requête et réponse
- [ ] Rédiger les spécifications d'authentification
- [ ] Documenter les webhooks
- [ ] Publier une collection Postman
- [ ] Mettre en place une documentation interactive (Swagger / Scribe)
