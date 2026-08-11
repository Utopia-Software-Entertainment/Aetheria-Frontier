# TESTING — Playtest design et QA

> Comment on prouve qu'Aetheria fonctionne — avant, pendant et après les playtests. Ce document définit les sessions, les métriques et les jalons de qualité. Complète `BALANCE.md` §8 (réglages) et `ACCESSIBILITY.md` §5 (personas).

> **Statut** : Validé v0.1 · **Version** : 0.1 · **MAJ** : 2026-08-11 · **Owner** : Équilibrage · **Dépend de** : BALANCE.md, ACCESSIBILITY.md, ONBOARDING.md

## 1. Principes

1. **Une métrique par promesse** — chaque pillar a un indicateur mesurable.
2. **Tester le fun avant la technique** — les playtests commencent dès le prototype combat.
3. **Toujours un pass accessibilité** — chaque session inclut les personas (voir §4).
4. **Les données sont anonymisées** — télémétrie serveur, jamais de données personnelles.

## 2. Types de sessions

| Session | Contenu | Participants | Cadence |
|---|---|---|---|
| **Prototype** | Une mécanique (combat, PNJ, voix) | 4–8 internes | Hebdo |
| **Playtest de zone** | Une Terre, donjons | 8–16 recrutés | Bimensuel |
| **Playtest d'événement** | Événements mondiaux, Entité | 16–32 + spectateurs | Mensuel |
| **Stress test** | Serveur, shards, 500 CCU simulés | Interne + outillage | À chaque jalon réseau |
| **Test accessibilité** | Personas (voir §4) | 5–10 profilés | À chaque pass majeur |
| **Bêta fermée → ouverte** | Monde complet | Communauté | Après jalons P0/P1 |

## 3. Métriques par promesse

| Promesse | Métrique | Cible |
|---|---|---|
| Sans manette | Taux de réussite de la calibration (voir `ONBOARDING.md`) | > 90 % au 2e essai |
| Combat physique | % de critiques parfaits tentés/réussis | 30–50 % des tentatives |
| Monde vivant | % de joueurs qui ont vu un événement PNJ spontané | > 80 % en 10 h |
| Zéro HUD | Temps pour trouver une info sans interface | < 30 s |
| Entités | % de serveurs ayant déclenché un scénario EX | > 10 % (voir `BALANCE.md` §8) |
| Confort VR | Abandons pour inconfort | < 5 % des sessions |
| Économie | Inflation des objets rares | < 5 %/mois |

## 4. Personas de test (accessibilité)

1. **Photo-sensible** — réduction des lueurs, flashs.
2. **Malentendant** — sous-titres complets, indices alternatifs.
3. **Dysarthrie** — tolérance vocale élargie.
4. **Moteur limité** — seuils EMG, amplitude réduite, mode assis.
5. **Novice VR** — courbe d'apprentissage, confort.

Chaque persona dispose d'un **parcours de test standard** (calibration → tutoriel → combat → dialogue).

## 5. Jalons QA

| Jalon | Critère de sortie |
|---|---|
| **Prototype combat** | 30 min de jeu sans blocage ; critique parfait reproductible |
| **Prototype PNJ** | 5 PNJ autonomes cohérents sur 1 h sans joueur |
| **Vertical slice** | Priméa jouable de bout en bout (calibration → première quête) |
| **Alpha (P0)** | 12 Terres navigables, 300 quêtes, 2 Entités (cible) |
| **Bêta fermée** | 500 CCU/stress test OK, zéro corruption de sauvegarde |
| **Bêta ouverte** | 1 mois, inflation maîtrisée, incidents SEV1 < 1/semaine |

## 6. Collecte de données

- **Télémétrie serveur** : durées de combat, taux de morts, densité, événements (anonymisée).
- **Replays** : captures de session (opt-in) pour analyse des moments de friction.
- **Observateurs** : playtests avec observateurs qui notent les « blocages silencieux » (le joueur ne sait pas quoi faire).
- **Entretiens courts** (5 min post-session) : 3 questions — ce que tu as aimé / détesté / voulu faire sans savoir comment.

## 7. Contrat d'implémentation (rappel moteur)

| Besoin | Module moteur |
|---|---|
| Télémétrie anonymisée | `network/` (stats serveur) |
| Replays de sessions | `network/` + `renderer/` |
| Outillage de stress test | `network/` |
| Journalisation des métriques de design | `game/` |
