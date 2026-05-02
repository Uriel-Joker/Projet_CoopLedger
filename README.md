[README.md](https://github.com/user-attachments/files/27297180/README.md)
# 🌿 CoopLedger

> **La transparence financière des coopératives agricoles togolaises, garantie par la blockchain.**

[![MIABE Hackathon 2026](https://img.shields.io/badge/MIABE%20Hackathon-2026-green?style=flat-square)](https://www.miabehackathon.com)
[![Projet](https://img.shields.io/badge/Projet-T--02-blue?style=flat-square)]()
[![Togo](https://img.shields.io/badge/Pays-🇹🇬%20Togo-orange?style=flat-square)]()
[![ODD](https://img.shields.io/badge/ODD-1%20·%2016%20·%2017-purple?style=flat-square)]()

---

## Description de la solution

CoopLedger est une plateforme web et mobile qui utilise la **technologie blockchain** pour garantir la transparence financière des coopératives agricoles togolaises.

### Le problème

- **60%** des coopératives togolaises tiennent leur comptabilité uniquement sur papier
- **15 à 20%** des fonds collectifs font l'objet de détournements documentés chaque année
- **70%** des membres citent le manque de transparence comme raison principale de méfiance
- Les coopératives transparentes lèvent en moyenne **×3** plus de financements (IFAD, 2022)

### La solution

CoopLedger enregistre chaque transaction financière sur une blockchain **Hyperledger Besu (Proof of Authority)**, rendant toute modification ou suppression techniquement impossible. Chaque membre peut vérifier en temps réel l'état financier de sa coopérative depuis son téléphone.

---

## Technologies utilisées

| Couche                 | Technologie                               | Rôle                                           |
| ---------------------- | ----------------------------------------- | ---------------------------------------------- |
| **Blockchain**         | Hyperledger Besu (PoA)                    | Enregistrement immuable des transactions       |
| **Smart Contracts**    | Solidity (EVM compatible)                 | Automatisation des votes et règles financières |
| **Backend API**        | Node.js + Web3.js                         | Interface entre l'application et la blockchain |
| **Frontend Web**       | HTML5 / CSS3 / JavaScript                 | Tableau de bord responsive                     |
| **Application Mobile** | Interface responsive mobile-first         | Consultation + vote depuis le téléphone        |
| **Stockage**           | IPFS + hash ancré on-chain                | Rapports mensuels permanents                   |
| **Authentification**   | Signatures cryptographiques ECDSA         | Clé privée par membre                          |
| **Polices**            | Google Fonts (DM Serif Display, Epilogue) | Interface professionnelle                      |

---

## Structure du dépôt

```
coopledger/
│
├──  index.html                          # Site vitrine Phase 1
├──  coopledger.css                      # Styles du site vitrine
│
├──  CoopLedger_Dashboard_V2.html        # Tableau de bord web (Phase 2)
├──  CoopLedger_Vote_V2.html            # Module de vote blockchain (Phase 2)
├──  CoopLedger_Mobile_Demo.html         # Application mobile + Démo live (Phase 2)
│
├──  CoopLedger_Gouvernance.docx         # Document de gouvernance (Phase 1)
├──  CoopLedger_Blockchain_Technique.docx # Description technique blockchain (Phase 1)
├──  CoopLedger_Notes_Demo.pdf           # Notes de démonstration Phase 2
│
└──  README.md                           # Ce fichier
```

---

## Instructions d'installation et d'utilisation

### Prérequis

- Un navigateur web moderne (Chrome, Firefox, Edge)
- Connexion internet (pour charger les polices Google Fonts)
- Aucune installation de logiciel requise

### Lancer le prototype en local

**Option 1 — Directement depuis le navigateur :**

1. Télécharge le dépôt en cliquant sur **Code → Download ZIP**
2. Extrais le dossier
3. Ouvre les fichiers HTML dans ton navigateur

**Option 2 — Cloner le dépôt :**

```bash
git clone https://github.com/[votre-username]/coopledger.git
cd coopledger
# Ouvre index.html dans ton navigateur
```

### Ordre de navigation recommandé

```
1. index.html                    → Découvrir le projet (site vitrine)
2. CoopLedger_Dashboard_V2.html  → Tableau de bord complet
3. CoopLedger_Vote_V2.html       → Votes et gouvernance
4. CoopLedger_Mobile_Demo.html   → App mobile + Démo live blockchain
```

---

## Fonctionnalités principales développées

### Phase 1 — Présélection ✅

- [x] Site web vitrine présentant le problème, la solution et la justification blockchain
- [x] Maquettes visuelles : tableau de bord membre, écran de vote, historique des transactions
- [x] Documentation de gouvernance avec données et cas documentés
- [x] Description technique complète de la composante blockchain

### Phase 2 — Demi-finale ✅

- [x] **Tableau de bord web** : solde en temps réel, graphiques interactifs (barres + donut), historique paginé, enregistrement de transactions avec ancrage blockchain simulé
- [x] **Module de vote** : propositions avec barres de progression Pour/Contre, vote signé cryptographiquement, smart contract VoteManager, journal blockchain live, déploiement de nouvelles propositions
- [x] **Application mobile** : 4 écrans (Accueil, Historique, Vote, Profil), navigation tactile, consultation du solde et participation aux votes depuis le téléphone
- [x] **Démonstration live** : simulation complète de la propagation blockchain en 5 étapes (Saisie → Signature → Broadcast → Consensus PoA → Ancrage), propagation visible chez tous les membres en temps réel

---

## Architecture blockchain

```
┌─────────────────────────────────────────────┐
│           Interface Utilisateur              │
│    Web Dashboard  │  Application Mobile      │
└──────────┬──────────────────┬────────────────┘
           │                  │
┌──────────▼──────────────────▼────────────────┐
│              API Node.js + Web3.js           │
└──────────────────────┬───────────────────────┘
                       │
┌──────────────────────▼───────────────────────┐
│         Smart Contracts (Solidity)           │
│  TransactionVault │ VoteManager │ AuditLog   │
└──────────────────────┬───────────────────────┘
                       │
┌──────────────────────▼───────────────────────┐
│      Blockchain Hyperledger Besu (PoA)       │
│  Lomé-01 │ Kara-02 │ Sokodé-03 │ Atakpamé-04 │ Dapaong-05  │
└──────────────────────────────────────────────┘
```

### Flux d'une transaction

1. **Saisie** — Trésorier entre description, montant, catégorie
2. **Signature** — Clé privée ECDSA signe le JSON (tx_id, montant, date, bénéficiaire)
3. **Broadcast** — Transaction diffusée aux 5 nœuds validateurs
4. **Consensus PoA** — 5/5 nœuds valident → bloc confirmé en quelques secondes
5. **Ancrage immuable** — Hash SHA-256 enregistré, visible par tous les membres

---

## Utilisateurs finaux

| Acteur                          | Rôle                                               | Accès                  |
| ------------------------------- | -------------------------------------------------- | ---------------------- |
| **Membres**                     | Consulter solde + historique, participer aux votes | Application mobile     |
| **Trésorier**                   | Enregistrer transactions, signer les opérations    | Tableau de bord web    |
| **Président**                   | Co-valider décisions, soumettre propositions       | Tableau de bord web    |
| **Partenaires (IFAD, banques)** | Consulter rapports de transparence                 | Accès lecture publique |
| **Ministère Agriculture**       | Supervision et audit des coopératives              | Accès rapports agrégés |

---

## Impact attendu

- ✅ Accès aux financements institutionnels jusqu'ici refusés (×3 selon IFAD 2022)
- ✅ Élimination des conditions permettant les détournements (registre immuable)
- ✅ Augmentation des revenus agricoles de +30 à +50% (achats groupés mieux gérés)
- ✅ Confiance restaurée entre membres et dirigeants de coopératives
- ✅ Modèle réplicable à toutes les coopératives agricoles d'Afrique de l'Ouest

---

## ODD ciblés

| ODD        | Objectif               | Lien avec CoopLedger                                                     |
| ---------- | ---------------------- | ------------------------------------------------------------------------ |
| **ODD 1**  | Fin de la pauvreté     | Augmentation des revenus agricoles grâce aux achats groupés transparents |
| **ODD 16** | Institutions efficaces | Gouvernance coopérative transparente, responsable et immuable            |
| **ODD 17** | Partenariats           | Accès facilité aux financements institutionnels (IFAD, BAD, banques)     |

---

## Équipe

**Projet T-02 — CoopLedger**  
MIABE Hackathon 2026 · Darollo Technologies Corporation  
 [www.miabehackathon.com](https://www.miabehackathon.com)

---

_La Blockchain, levier du développement durable africain_ 🌱
