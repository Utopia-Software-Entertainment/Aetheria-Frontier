# PVP — Joueur contre joueur

> Le PvP d'Aetheria : toléré, encadré, à conséquences. Les PK sont un contenu, pas un accident. Complète `CLANS.md` (clans de joueurs, guerres de clans).

> **Statut** : Validé v0.3 · **Version** : 0.3 · **MAJ** : 2026-08-11 · **Owner** : Social · **Dépend de** : CLANS.md, DEATH.md, SOCIAL.md

## 1. Philosophie

1. **Le PvP est un choix** — personne ne subit le PvP hors des zones prévues, sauf s'il est PK.
2. **Les PK sont un contenu** — marquage, primes, chasses : le monde réagit aux tueurs.
3. **La réputation est durable** — les actes PvP modifient la perception des PNJ et des joueurs.

## 2. Modes de PvP

| Mode | Zones | Règles |
|---|---|---|
| **Duel** | Partout (consentement mutuel) | Sans perte, sans marque |
| **Arène** | Arènes de Cinquantia | Classements, récompenses |
| **Guerre de clans** | Territoires déclarés | Conquête de zones, conséquences économiques |
| **PK** | Monde ouvert | Non consenti — voir §3 |

## 3. Système PK

### 3.1 Marquage
- **Tuer un autre joueur est possible** hors zones sûres — mais le tueur devient un **PK (Player Killer)** : marqué, visible de tous, poursuivi. Le PvP non consenti est une décision, jamais un accident.
- **Escalade** : toute attaque non consentie inflige une **marque provisoire** (24 h, voir `BALANCE.md`) ; un **meurtre non consenti confirme le statut PK** (crâne près du nom, pertes accrues, primes, cimetière éloigné).
- La marque s'estompe avec le temps et les actes réparateurs (quêtes de rédemption), pas avec l'argent.

### 3.2 Conséquences
- **Pertes accrues** : un PK marqué perd plus à sa mort (équipement non protégé, ressources).
- **Exclusion sociale** : les PNJ marchands surtaxent ou refusent ; les gardes chassent.
- **Primes** : les victimes peuvent offrir une prime — visible par les chasseurs de primes (clan ou mercenaires).
- **Cimetière éloigné** : un PK meurt loin de son point d'attache.

### 3.3 Protection des nouveaux
- **Immunité de début** : aucun PvP subi pendant les 10 premiers niveaux.
- **Zones sûres** : villes, sanctuaires — pas de PK possible (la loi du monde, pas une option).

## 4. Chasse aux PK

- Les **clans** et les primes organisent des **chasses** : pistage, embuscades, coordination (voir `CLANS.md` — les clans de joueurs s'y taillent une réputation).
- Un PK déchu peut revenir par la rédemption (quêtes des Saints, actes publics) — le monde accepte le retour, pas l'oubli.

## 5. Guerres de clans

- **Déclaration** : un clan déclare la guerre à un autre (surenchère sur des droits : enchères, territoire, forge).
- **Déroulé** : batailles planifiées ou sièges ouverts — jamais de spawn camping.
- **Conséquences** : droits perdus, taxes, réputation de clan ; les alliances peuvent intervenir (voir `CLANS.md`).
- **Trêves** : le monde impose des trêves après des sièges longs (fatigue de guerre).

## 6. Équilibre et intégrité

- **Serveur autoritatif** : toute action PvP est validée côté serveur (anti-ping, anti-bot).
- **Pas de one-shot de structure** : les combats PvP suivent les mêmes règles physiques que le PvE (points vitaux, garde, esquive).
- **Recherche d'égalité** : les arènes utilisent des paliers de stats pour éviter l'écart de niveau total.

## 7. Contrat d'implémentation (rappel moteur)

| Besoin | Module moteur |
|---|---|
| Validation serveur des actions PvP | `network/` (autorité) |
| État de marquage, primes, réputation | `game/` (persistance serveur) |
| Zones sûres / zones de guerre | `world/` + `game/` |
| Anti-triche PvP (latence, macros) | `network/` (validation) |
