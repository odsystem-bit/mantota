# Roadmap Intelligence Artificielle — Mantota

Ce document présente la vision et les étapes d'intégration de l'intelligence artificielle dans Mantota.

> **Statut** : Document de planification. Les fonctionnalités IA seront déployées progressivement à partir de la Phase 5 du produit.

---

## Vision IA

L'objectif de Mantota est d'utiliser l'intelligence artificielle pour :

- **Automatiser** les tâches répétitives (matching, modération, scoring).
- **Recommander** les meilleurs acteurs pour chaque campagne ou transaction.
- **Prédire** les performances et les tendances du marché.
- **Sécuriser** la plateforme via la détection de fraudes et la vérification automatisée.
- **Accompagner** les utilisateurs avec un assistant IA.

---

## Cas d'usage IA

### 1. Matching influenceur / campagne

**Problème** : les vendors perdent du temps à choisir les bons créateurs.

**Solution** : un algorithme de recommandation qui suggère les influenceurs les plus pertinents en fonction de :
- La niche et l'audience
- Les performances passées
- Le budget et les objectifs de la campagne
- La localisation géographique

### 2. Scoring et prédiction de campagnes

**Problème** : difficile d'estimer le ROI d'une campagne avant son lancement.

**Solution** : un modèle prédictif qui estime :
- Le nombre de clics, vues et conversions attendus
- Le ROI estimé
- Le prix optimal par influenceur

### 3. Modération automatique des contenus

**Problème** : vérifier manuellement les livrables des influenceurs est coûteux.

**Solution** : un modèle de vision / NLP qui analyse :
- La conformité au brief
- La qualité du contenu
- La détection de contenus inappropriés

### 4. Vérification automatique des documents KYC

**Problème** : la validation KYC manuelle est lente.

**Solution** : un pipeline OCR + classification qui :
- Extrait les informations des documents
- Vérifie la cohérence
- Détecte les falsifications potentielles

### 5. Assistant IA pour les utilisateurs

**Problème** : les utilisateurs ont besoin d'aide pour optimiser leurs campagnes et boutiques.

**Solution** : un assistant conversationnel intégré qui répond aux questions et propose des recommandations.

### 6. Détection de fraudes et anomalies

**Problème** : les transactions et les clics peuvent être frauduleux.

**Solution** : un système d'analyse comportementale qui détecte :
- Les clics suspects
- Les transactions anormales
- Les comportements de bot

### 7. Analyse prédictive des tendances

**Problème** : anticiper les tendances de consommation locales.

**Solution** : un modèle d'analyse des données de la plateforme et des réseaux sociaux pour identifier les produits et créateurs émergents.

---

## Stack technique envisagée

| Composant | Technologie | Usage |
| :--- | :--- | :--- |
| LLM | OpenAI API / modèles open source | Assistant, recommandation textuelle |
| Vision | OpenAI Vision / CLIP | Modération des images et vidéos |
| OCR | Tesseract / AWS Textract | Extraction KYC |
| ML | Python, scikit-learn, FastAPI | Scoring, prédiction, fraude |
| Données | MySQL, exports analytics | Entraînement et inférence |
| Infrastructure | Docker, serveur dédié | Hébergement des services IA |

---

## Phases de déploiement

### Phase 1 — Fondations (Mois 1-6)

- Collecte structurée des données
- Mise en place d'un pipeline d'export
- Définition des indicateurs de performance

### Phase 2 — Recommandation et scoring (Mois 6-12)

- Moteur de recommandation d'influenceurs
- Scoring des campagnes
- Tableau de bord prédictif

### Phase 3 — Modération et KYC (Mois 12-18)

- Modération automatique des livrables
- Vérification automatique des documents KYC
- Réduction du temps de validation

### Phase 4 — Assistant et prédictions avancées (Mois 18-24)

- Assistant IA pour vendors et influencers
- Prédiction des tendances de marché
- Détection avancée de fraudes

---

## Éthique et conformité

- Anonymisation des données sensibles avant traitement externe.
- Consentement explicite des utilisateurs pour l'utilisation de leurs données.
- Transparence sur les décisions automatisées.
- Conformité aux réglementations locales de protection des données.
- Validation humaine pour les décisions critiques (KYC, litiges).

---

## Prochaines étapes

- [ ] Définir les jeux de données nécessaires
- [ ] Choisir les modèles et les APIs
- [ ] Concevoir l'architecture des services IA
- [ ] Mettre en place un environnement de test
- [ ] Rédiger les spécifications par cas d'usage
