# Aetheria-Frontier

A high-performance techno-fantasy VRMMO where players explore a massive world, uncover ancient secrets, and engage in fast-paced combat controlled entirely by neural inputs, eye-tracking, and voice commands.

## Pillars

- **Monde ouvert massif** : 12 Terres, ruines de l'Ère des Divins, mystères jamais entièrement résolus.
- **Les Sept Entités** : boss uniques non-respawnables, invincibles hors de leur Scénario Unique EX.
- **Physique stylisée** : inertie, points vitaux, critiques parfaits — le corps du joueur est le contrôleur.
- **Pas de héros** : chaque joueur crée son personnage (origine + voie) ; aucun protagoniste imposé.
- **PNJ vivants** : chaque PNJ a sa propre vie, ses routines et ses relations — sans effet « IA ».
- **100 % sans manette** : eye-tracking, voix (Whisper), EEG/EMG (OpenBCI), micro-sticks. Jouable allongé.

## Documentation

| Doc | Contenu |
|---|---|---|
| [docs/GDD.md](docs/GDD.md) | Document maître : vision, pillars, promesses, architecture de la doc |
| [docs/LORE.md](docs/LORE.md) | Le monde : Ère des Divins, 12 Terres, la Grande Bleue, société |
| [docs/BOSSES.md](docs/BOSSES.md) | Les Sept Entités + monstres uniques, règles de design |
| [docs/CLANS.md](docs/CLANS.md) | Guildes, PK, alliance des quatre, économie de l'info |
| [docs/SYSTEMS.md](docs/SYSTEMS.md) | Création de personnage, équipement, forge, économie (vue d'ensemble) |
| [docs/NPC.md](docs/NPC.md) | PNJ autonomes : vies propres, routines, interactions sans « effet IA » |
| [docs/CONTROLS.md](docs/CONTROLS.md) | Commandes sans manette : regard, voix, EEG/EMG, micro-sticks, mode allongé |
| [docs/COMBAT.md](docs/COMBAT.md) | Combat détaillé : voies, magie gravée, contrat physique, raids |
| [docs/WORLD.md](docs/WORLD.md) | Zones, donjons, boss de zone, respawn, événements |
| [docs/QUESTS.md](docs/QUESTS.md) | Système de quêtes, Scénarios Uniques EX |
| [docs/AUDIO.md](docs/AUDIO.md) | Design audio : spatialisation, voix PNJ, zéro-HUD |
| [docs/ECONOMY.md](docs/ECONOMY.md) | Artisanat, récolte, enchères, équilibre monétaire |
| [docs/PVP.md](docs/PVP.md) | PK, duels, guerres de guilde |
| [docs/MONETIZATION.md](docs/MONETIZATION.md) | Modèle économique, lignes rouges (anti-p2w) |
| [docs/ONBOARDING.md](docs/ONBOARDING.md) | Calibration, zone tutoriel, apprentissage sans HUD |
| [docs/UI.md](docs/UI.md) | Interface diégétique : sac, carte, carnet, menus vocaux |
| [docs/DEATH.md](docs/DEATH.md) | Mort, respawn, pénalités, résurrection |
| [docs/SOCIAL.md](docs/SOCIAL.md) | Groupes, communication vocale spatiale, modération |
| [docs/BESTIARY.md](docs/BESTIARY.md) | Faune : familles, comportements, télégraphie, drops |
| [docs/NARRATIVE.md](docs/NARRATIVE.md) | Histoire du monde : machine à états, arcs, événements |
| [docs/ART.md](docs/ART.md) | Direction artistique : contraste médiéval/Divins, lisibilité VR |
| [docs/ACCESSIBILITY.md](docs/ACCESSIBILITY.md) | Référence accessibilité consolidée (vision, audition, voix, corps) |
| [docs/BALANCE.md](docs/BALANCE.md) | Bible d'équilibrage : courbes, temps, économie, tolérances techniques |
| [docs/GLOSSARY.md](docs/GLOSSARY.md) | Index des termes du lore et des systèmes |

> Note : ce repo documente le **jeu** (lore, design). Le moteur est développé dans le repo voisin `synapse-engine`.

## Roadmap (jeu)

- [ ] Valider le lore et les noms définitifs (transpositions → noms Aetheria)
- [ ] Valider le modèle de monétisation avec le studio
- [ ] Vertical slice moteur (Core → ECS → renderer Vulkan → OpenXR → Jolt)
- [ ] Prototype combat : inertie + points vitaux + commandes vocales
- [ ] Prototype PNJ : horloge mondiale + graphe de relations + dialogue contextuel
- [ ] Zones de départ : Priméa, Secondil, fosse des Brèches
- [ ] Première Entité jouable (scénario EX complet)
