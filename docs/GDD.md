# GDD — Game Design Document

> Document maître du jeu **Aetheria-Frontier**. Tous les autres docs de `docs/` détaillent les sections ici résumées.

> **Statut** : Validé v0.2 · **Version** : 0.2 · **MAJ** : 2026-08-11 · **Owner** : Design · **Dépend de** : tous les docs

## 0. Historique de révision

| Version | Date | Changement |
|---|---|---|
| 0.1 | 2026-07-XX | Création (vision, pillars, architecture des docs) |
| 0.2 | 2026-08-11 | Core loop, audience, priorités P0/P1, 12e Terre (Septième), ref CONTENT.md |

## 1. Vision

**Aetheria-Frontier** est un VRMMO techno-fantastique en monde ouvert : les joueurs explorent un continent de **12 Terres** (dont une effacée des cartes, la Septième) façonné par une civilisation disparue (l'Ère des Divins), combattent des créatures uniques quasi invincibles, et vivent dans un monde dont les habitants — PNJ comme joueurs — mènent leur propre vie.

La spécificité d'Aetheria : **aucune manette**. Les commandes passent par le regard, la voix, le cerveau et les micro-mouvements. Le joueur est dans le monde, pas derrière un écran.

## 2. Pillars (piliers de design)

1. **Un monde qui vit sans toi** — PNJ autonomes, horloges, événements ; l'histoire continue hors connexion.
2. **Pas de héros** — création de personnage libre (origine + voie), aucun protagoniste imposé.
3. **Les Sept Entités** — contenu signature : uniques, non-respawnables, vaincues uniquement via des Scénarios Uniques EX cachés.
4. **Physique stylisée** — simulation réaliste (moteur) traduite en règles de jeu (inertie = puissance, points vitaux, critiques parfaits).
5. **Zéro HUD, zéro manette** — l'information et les commandes vivent dans le monde : regard, voix, EEG/EMG, micro-sticks.
6. **Le mystère est un contenu** — les réponses ouvrent des questions ; rien n'est jamais entièrement documenté en jeu.

## 3. Promesses (player promises)

- Je peux créer **mon** personnage et jouer ma propre histoire.
- Les PNJ ont **leurs** vies, pas des quêtes à me vendre.
- Je peux mourir contre une Entité et **garder une trace** (Marque, réputation).
- Je joue **allongé**, **sans manette**, avec mon corps et ma voix.
- Les boss les plus célèbres du jeu **ne se farm pas** : ils se comprennent.

## 4. Non-goals

- Pas de personnage principal scénarisé.
- Pas de HUD conventionnel (jauges, minimap, icônes).
- Pas de fabrication en série : chaque équipement est unique.
- Pas de pay-to-win (voir `MONETIZATION.md`).
- Pas de contenu documenté pour les Scénarios Uniques EX.

## 5. Core loop (boucle de jeu)

**Boucle longue** : Explorer → Comprendre → Affronter → Survivre (ou être Marqué) → Apprendre → Retenter.

**Boucle courte (combat)** : Lire le monde (regard + oreilles) → Engager (regard + voix) → Frapper juste (inertie + points vitaux + timing) → Récolter (drops, connaissances) → Repartir.

**Boucle sociale** : Rencontrer (voix spatiale) → S'allier (groupe, guilde) → Coopérer (donjons, raids) → Partager l'information (marché de l'info, voir `ECONOMY.md`).

## 6. Audience cible

| Segment | Profil | Accès |
|---|---|---|
| **Cœur** | Joueurs VR 18–40, amateurs d'immersion, MMORPG et action | PCVR, PSVR2 |
| **Casual immersif** | Joueurs allongés, sessions 30–90 min | Mode allongé, courbes douces |
| **Hardcore** | Chasseurs de défis, guildes, chasse aux Entités | Contenu 16–32 joueurs, Scénarios EX |
| **Spectateurs** | Diffuseurs et communautés d'événements | Événements mondiaux = spectacle (voir `SERVICE.md`) |

Non-cible : le jeu est **VR-first** — l'adaptation souris/clavier n'est pas prévue.

## 7. Priorités P0/P1

| Priorité | Feature | Doc |
|---|---|---|
| **P0** | Commandes sans manette (calibration, regard, voix, allongé) | `CONTROLS.md`, `ONBOARDING.md` |
| **P0** | Combat physique (inertie, points vitaux, critique) | `COMBAT.md`, `SYSTEMS.md` |
| **P0** | Monde ouvert 12 Terres + donjons | `WORLD.md`, `LEVELDESIGN.md`, `CONTENT.md` |
| **P0** | PNJ autonomes (horloge, relations, dialogue) | `NPC.md` |
| **P1** | Les Sept Entités + Scénarios EX (cible lancement : 2, à valider) | `BOSSES.md`, `BOSSCONCEPTS.md`, `QUESTS.md` |
| **P1** | Guildes + économie (enchères, artisanat, objets uniques) | `CLANS.md`, `ECONOMY.md`, `LOOT.md` |
| **P1** | Événements mondiaux + machine à états | `NARRATIVE.md`, `SERVERWORLD.md` |
| **P1** | Accessibilité consolidée + profils | `ACCESSIBILITY.md` |

## 8. Cible technique (rappel)

- Moteur custom **synapse-engine** (C++23, Vulkan, OpenXR, EnTT, Jolt, FMOD, LibLSL, Whisper.cpp).
- VR full-dive sur matériel commercial : ASUS ROG + PSVR2 en entrée de gamme ; Somnium VR1 + OpenBCI en progression.
- Réseau : 500 CCU cible v0, shards + Nakama, server meshing à terme.
- Mode **allongé (recumbent)** : le monde pivote à 90°.

## 9. Architecture des documents

| Doc | Sujet |
|---|---|
| `LORE.md` | Le monde, l'Ère des Divins, les 12 Terres, la Grande Bleue, la société |
| `BOSSES.md` | Les Sept Entités + monstres uniques, règles de design |
| `CLANS.md` | Guildes, alliance des quatre, économie de l'information |
| `SYSTEMS.md` | Création de personnage, équipement, forge, économie (vue d'ensemble) |
| `NPC.md` | PNJ autonomes : vie propre, relations, anti-« effet IA » |
| `GDD.md` | Ce document |
| `CONTROLS.md` | Mapping des commandes (regard, voix, EEG/EMG, micro-sticks, allongé) |
| `COMBAT.md` | Combat détaillé, voies, magie, contrat physique, raids |
| `WORLD.md` | Zones, donjons, boss de zone, respawn, événements |
| `QUESTS.md` | Système de quêtes, Scénarios Uniques EX |
| `AUDIO.md` | Design audio (spatial, voix, zéro-HUD) |
| `ECONOMY.md` | Artisanat, récolte, enchères, équilibre |
| `PVP.md` | PK, duels, guerres de guilde |
| `ONBOARDING.md` | Calibration multi-capteurs, zone tutoriel, apprentissage sans HUD |
| `UI.md` | Interface diégétique : sac, carte, carnet, menus vocaux, zéro-HUD |
| `DEATH.md` | Mort, respawn, pénalités, résurrection |
| `SOCIAL.md` | Groupes, communication vocale spatiale, modération |
| `BESTIARY.md` | Faune : familles, comportements, télégraphie, drops |
| `NARRATIVE.md` | Histoire du monde : machine à états, arcs, événements |
| `ART.md` | Direction artistique : contraste médiéval/Divins, lisibilité VR |
| `ACCESSIBILITY.md` | Référence accessibilité consolidée (vision, audition, voix, corps) |
| `BALANCE.md` | Bible d'équilibrage : courbes, temps, économie, tolérances |
| `MONETIZATION.md` | Modèle économique, lignes rouges |
| `GLOSSARY.md` | Index des termes |
| `_TEMPLATE.md` | Modèle de document (bloc méta, structure, statuts) |
| `CONTENT.md` | Inventaire de contenu chiffré (villes, PNJ, armes, boss, quêtes) |
| `SERVERWORLD.md` | Structure serveur/monde : shards, population, événements globaux |
| `LOOT.md` | Récompenses : tables de loot, raretés, anti-farm |
| `ACHIEVEMENTS.md` | Titres, Marques, méta-progression « légende » |
| `TESTING.md` | Playtest design, métriques, jalons QA |
| `SERVICE.md` | Service : GMs, modération, support, communauté |
| `BOSSCONCEPTS.md` | Concepts de combat détaillés par Entité |
| `LEVELDESIGN.md` | Méthodologie de construction des zones |

## 10. Roadmap produit

1. **Vertical slice moteur** : Core → ECS → Vulkan → OpenXR → Jolt (dans synapse-engine).
2. **Prototype combat** : inertie + points vitaux + commandes vocales (boucle la plus courte).
3. **Prototype PNJ** : horloge mondiale + graphe de relations + dialogue contextuel.
4. **Zones de départ** : Priméa, Secondil, Fosse des Brèches.
5. **Première Entité jouable** : scénario EX complet de bout en bout.
6. **Contenu d'échelle** : 12 Terres, guildes, économie complète, événements.

## 11. Décisions à trancher (ouvert)

- Noms définitifs Aetheria (remplacer les transpositions : Lycaon, Vésémon…).
- Approche technique des PNJ : règles locales vs modèle de langage vs hybride.
- Simulation hors-champ : périmètre exact du monde « vivant sans joueur ».
- Équilibrage des courbes (Kai, VIT, multiplicateurs).
- **Septième** : nature de son effacement, entrée secrète, contenu 65–75+.
- **Scope de lancement** : nombre d'Entités, d'armes, de PNJ, de quêtes (cibles dans `CONTENT.md`).
