# Roadmap Intelligence Artificielle — Mantota

Ce document présente la vision et les étapes d'intégration de l'intelligence artificielle dans Mantota.

---

## Contexte

Mantota v1.0 est en production sur [mantota.com](https://mantota.com) avec environ 120 utilisateurs actifs. Les fonctionnalités IA sont planifiées pour la **v2.1**, après la migration vers une infrastructure scalable en **v2.0**.

## Vision IA — OD IA

Mantota intégrera **OD IA**, l'intelligence artificielle commerciale souveraine d'OD Systeme, pour transformer le commerce en Afrique de l'Ouest.

L'objectif d'OD IA dans Mantota est de :

- **Automatiser** les tâches répétitives (matching, modération, scoring).
- **Recommander** les meilleurs acteurs pour chaque campagne ou transaction.
- **Prédire** les performances et les tendances du marché.
- **Sécuriser** la plateforme via la détection de fraudes et la vérification automatisée.
- **Accompagner** les utilisateurs avec un assistant IA conversationnel et vocal.
- **Democratiser** le commerce en rendant l'achat et la vente accessibles par la voix, notamment via WhatsApp.

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

## Cas d'usage commerciaux OD IA

### 8. Assistant commercial conversationnel

**Problème** : les vendeurs et influenceurs débutants ne savent pas optimiser leurs campagnes et boutiques.

**Solution** : OD IA répond aux questions, suggère des améliorations, génère des descriptions de produits et des scripts de contenu.

### 9. Commande automatique par IA

**Problème** : le processus d'achat en ligne reste complexe pour certains utilisateurs.

**Solution** : l'utilisateur décrit son besoin à OD IA (texte ou voix). L'IA sélectionne le meilleur produit/vendeur, remplit le panier, calcule la livraison et initie le paiement Mobile Money après confirmation.

### 10. Commerce vocal WhatsApp pour analphabètes

**Problème** : des millions de commerçants et clients en Afrique de l'Ouest ne savent pas lire ou écrire.

**Solution** : OD IA intégrée à WhatsApp permet de vendre et d'acheter par messages vocaux. Exemples :
- *"Je vends des sacs en pagne à 5 000 francs, j'ai 10 pièces"* → OD IA crée la fiche produit.
- *"Je cherche un téléphone pas cher à Cotonou"* → OD IA propose des produits avec photos et prix.
- *"Oui, je prends celui-là"* → OD IA génère le paiement Mobile Money et le suivi de commande.

### 11. Guide marché et commerce local

**Problème** : difficile de savoir quoi acheter et où, surtout dans les marchés physiques.

**Solution** : OD IA oriente l'utilisateur vers les vendeurs Mantota disponibles près de lui, compare les stocks et les prix, et suggère les meilleures options.

### 12. Avis et confiance produit par IA

**Problème** : les utilisateurs craignent les arnaques et les produits de mauvaise qualité.

**Solution** : OD IA analyse les retours, les disputes, les notes et les descriptions pour attribuer un score qualité/prix et alerter sur les risques.

---

## Stack technique envisagée

| Composant | Technologie | Usage |
| :--- | :--- | :--- |
| LLM | Modèles open source / API avec anonymisation | Assistant, recommandation textuelle |
| Vision | OpenAI Vision / CLIP | Modération des images et vidéos |
| ASR / TTS | Whisper / modèles vocaux locaux | Transcription et synthèse vocale |
| OCR | Tesseract / AWS Textract | Extraction KYC |
| ML | Python, scikit-learn, FastAPI | Scoring, prédiction, fraude |
| WhatsApp | WhatsApp Business API | Canal vocal et conversationnel |
| Données | MySQL / PostgreSQL, exports analytics | Entraînement et inférence |
| Infrastructure | Docker, serveur dédié, hébergement régional | Hébergement souverain des services IA |

---

## Phases de déploiement

### Phase 0 — Préparation infrastructure (v2.0)

- Migration vers VPS/cloud
- Mise en place d'un pipeline de collecte et d'export de données
- Définition des métriques et indicateurs de performance

### Phase 1 — Fondations IA (Mois 1-6)

- Collecte structurée des données
- Anonymisation et conformité
- Choix des modèles et APIs

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

### Phase 5 — OD IA commerciale vocale (Mois 24-36)

- Intégration WhatsApp Business API avec OD IA
- Commande automatique par IA (texte + voix)
- Commerce vocal pour analphabètes
- Guide marché local et comparaison produits par IA
- Déploiement progressif par pays selon les langues locales

---

## Éthique et conformité

- Anonymisation des données sensibles avant traitement externe.
- Consentement explicite des utilisateurs pour l'utilisation de leurs données.
- Transparence sur les décisions automatisées.
- Conformité aux réglementations locales de protection des données.
- Validation humaine pour les décisions critiques (KYC, litiges).

---

## Prochaines étapes

- [ ] Finaliser la migration infrastructure v2.0
- [ ] Définir le pipeline de collecte et de traitement des données
- [ ] Choisir les modèles et les APIs
- [ ] Concevoir l'architecture des services IA
- [ ] Mettre en place un environnement de test
- [ ] Rédiger les spécifications par cas d'usage
