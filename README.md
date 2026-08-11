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

Statuts : ✅ Validé · 📝 Brouillon

| Doc | Statut | Contenu |
|---|---|---|
| [docs/GDD.md](docs/GDD.md) | ✅ | Document maître : vision, pillars, core loop, audience, priorités, architecture de la doc |
| [docs/LORE.md](docs/LORE.md) | 📝 | Le monde : Ère des Divins, 12 Terres (dont la Septième), la Grande Bleue, société |
| [docs/BOSSES.md](docs/BOSSES.md) | 📝 | Les Sept Entités + monstres uniques, règles de design |
| [docs/BOSSCONCEPTS.md](docs/BOSSCONCEPTS.md) | 📝 | Concepts de combat détaillés par Entité (phases, canaux, environnement) |
| [docs/BOSSDOSSIERS.md](docs/BOSSDOSSIERS.md) | 📝 | Dossiers complets de tous les boss : forces, faiblesses, compétences, IA |
| [docs/CLANS.md](docs/CLANS.md) | 📝 | Guildes, PK, alliance des quatre, économie de l'info |
| [docs/SYSTEMS.md](docs/SYSTEMS.md) | 📝 | Création de personnage, équipement, forge, économie (vue d'ensemble) |
| [docs/NPC.md](docs/NPC.md) | 📝 | PNJ autonomes : vies propres, routines, interactions sans « effet IA » |
| [docs/CONTROLS.md](docs/CONTROLS.md) | 📝 | Commandes sans manette : regard, voix, EEG/EMG, micro-sticks, mode allongé |
| [docs/COMBAT.md](docs/COMBAT.md) | 📝 | Combat détaillé : voies, magie gravée, contrat physique, raids |
| [docs/WORLD.md](docs/WORLD.md) | 📝 | Zones, donjons, boss de zone, respawn, événements |
| [docs/LEVELDESIGN.md](docs/LEVELDESIGN.md) | 📝 | Méthodologie de construction des zones (lecture, VR, budget) |
| [docs/QUESTS.md](docs/QUESTS.md) | 📝 | Système de quêtes, Scénarios Uniques EX |
| [docs/AUDIO.md](docs/AUDIO.md) | 📝 | Design audio : spatialisation, voix PNJ, zéro-HUD |
| [docs/ECONOMY.md](docs/ECONOMY.md) | 📝 | Artisanat, récolte, enchères, équilibre monétaire |
| [docs/LOOT.md](docs/LOOT.md) | 📝 | Récompenses : tables de loot, raretés, anti-farm |
| [docs/PVP.md](docs/PVP.md) | 📝 | PK, duels, guerres de guilde |
| [docs/MONETIZATION.md](docs/MONETIZATION.md) | 📝 | Modèle économique, lignes rouges (anti-p2w) |
| [docs/ONBOARDING.md](docs/ONBOARDING.md) | 📝 | Calibration, zone tutoriel, apprentissage sans HUD |
| [docs/UI.md](docs/UI.md) | 📝 | Interface diégétique : sac, carte, carnet, menus vocaux |
| [docs/DEATH.md](docs/DEATH.md) | 📝 | Mort, respawn, pénalités, résurrection |
| [docs/SOCIAL.md](docs/SOCIAL.md) | 📝 | Groupes, communication vocale spatiale, modération, LFG (non-goal matchmaking) |
| [docs/SERVICE.md](docs/SERVICE.md) | 📝 | Service : GMs, modération, support, événements communautaires |
| [docs/BESTIARY.md](docs/BESTIARY.md) | 📝 | Faune : familles, comportements, télégraphie, drops |
| [docs/NARRATIVE.md](docs/NARRATIVE.md) | 📝 | Histoire du monde : machine à états, arcs, événements |
| [docs/SERVERWORLD.md](docs/SERVERWORLD.md) | 📝 | Structure serveur : shards, 500 CCU, population feel, cross-shard |
| [docs/ART.md](docs/ART.md) | 📝 | Direction artistique : contraste médiéval/Divins, lisibilité VR |
| [docs/ACCESSIBILITY.md](docs/ACCESSIBILITY.md) | 📝 | Référence accessibilité consolidée (vision, audition, voix, corps) |
| [docs/BALANCE.md](docs/BALANCE.md) | 📝 | Bible d'équilibrage : courbes, temps, économie, tolérances techniques |
| [docs/ACHIEVEMENTS.md](docs/ACHIEVEMENTS.md) | 📝 | Titres, Marques, méta-progression « légende » |
| [docs/TESTING.md](docs/TESTING.md) | 📝 | Playtest design, métriques par promesse, jalons QA |
| [docs/CONTENT.md](docs/CONTENT.md) | 📝 | Inventaire de contenu chiffré : villes, PNJ, armes, boss, quêtes |
| [docs/GLOSSARY.md](docs/GLOSSARY.md) | 📝 | Index des termes du lore et des systèmes |
| [docs/_TEMPLATE.md](docs/_TEMPLATE.md) | 📝 | Modèle de document (bloc méta, structure, règles de rédaction) |

> Note : ce repo documente le **jeu** (lore, design). Le moteur est développé dans le repo voisin `synapse-engine`.

## Roadmap (jeu)

- [ ] Valider le lore et les noms définitifs (transpositions → noms Aetheria)
- [ ] Valider le modèle de monétisation avec le studio
- [ ] Vertical slice moteur (Core → ECS → renderer Vulkan → OpenXR → Jolt)
- [ ] Prototype combat : inertie + points vitaux + commandes vocales
- [ ] Prototype PNJ : horloge mondiale + graphe de relations + dialogue contextuel
- [ ] Zones de départ : Priméa, Secondil, fosse des Brèches
- [ ] Première Entité jouable (scénario EX complet)
