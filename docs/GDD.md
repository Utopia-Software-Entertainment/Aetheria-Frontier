# GDD — Game Design Document

> Document maître du jeu **Aetheria-Frontier**. Tous les autres docs de `docs/` détaillent les sections ici résumées.

## 1. Vision

**Aetheria-Frontier** est un VRMMO techno-fantastique en monde ouvert : les joueurs explorent un continent façonné par une civilisation disparue (l'Ère des Divins), combattent des créatures uniques quasi invincibles, et vivent dans un monde dont les habitants — PNJ comme joueurs — mènent leur propre vie.

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

## 5. Cible technique (rappel)

- Moteur custom **synapse-engine** (C++23, Vulkan, OpenXR, EnTT, Jolt, FMOD, LibLSL, Whisper.cpp).
- VR full-dive sur matériel commercial : ASUS ROG + PSVR2 en entrée de gamme ; Somnium VR1 + OpenBCI en progression.
- Réseau : 500 CCU cible v0, shards + Nakama, server meshing à terme.
- Mode **allongé (recumbent)** : le monde pivote à 90°.

## 6. Architecture des documents

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

## 7. Roadmap produit

1. **Vertical slice moteur** : Core → ECS → Vulkan → OpenXR → Jolt (dans synapse-engine).
2. **Prototype combat** : inertie + points vitaux + commandes vocales (boucle la plus courte).
3. **Prototype PNJ** : horloge mondiale + graphe de relations + dialogue contextuel.
4. **Zones de départ** : Priméa, Secondil, Fosse des Brèches.
5. **Première Entité jouable** : scénario EX complet de bout en bout.
6. **Contenu d'échelle** : 12 Terres, guildes, économie complète, événements.

## 8. Décisions à trancher (ouvert)

- Noms définitifs Aetheria (remplacer les transpositions : Lycaon, Vésémon…).
- Approche technique des PNJ : règles locales vs modèle de langage vs hybride.
- Simulation hors-champ : périmètre exact du monde « vivant sans joueur ».
- Équilibrage des courbes (Kai, VIT, multiplicateurs).
