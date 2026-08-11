# CONTENT — Inventaire de contenu chiffré

> Le « combien » d'Aetheria : villes, PNJ, armes, boss, quêtes. **Toutes les valeurs sont des cibles à valider en production** — elles définissent le scope de lancement, pas un catalogue figé. Complète `WORLD.md` (zones) et `BALANCE.md` (valeurs).

> **Statut** : Brouillon · **Version** : 0.1 · **MAJ** : 2026-08-11 · **Owner** : Design · **Dépend de** : WORLD.md, LORE.md, BOSSES.md, SYSTEMS.md

## 1. Vue d'ensemble (cibles lancement)

| Item | Cible | Détail |
|---|---|---|
| Terres | **12** | 11 nommées + **Septième** (effacée des cartes, 65–75+) |
| Villes principales | **11** | Une par Terre nommée |
| Villages | **~30** | 2–4 par Terre |
| Zones secrètes | **3** | Rabituza, Ruluath, Inventoriaire |
| Donjons de progression | **5** | Voir `WORLD.md` §2 |
| Donjons d'événement/guilde | **~12** | 1 par Terre environ |
| Boss de zone | **~11** | 1 par Terre (rotation) |
| Monstres uniques | **6** | Voir `BOSSES.md` |
| Les Sept Entités | **7** | 2 jouables au lancement (cible), 5 en contenu post-lancement |
| Scénarios Uniques EX | **7** (+14+ voies) | Un par Entité, conditions secrètes |
| PNJ nommés | **~600** | ~50 par ville principale |
| Armes uniques | **~120** | Voir §5 |
| Quêtes au lancement | **~300** | Tranches de vie, situationnelles, factions, guildes |
| Événements simultanés | **2–4** | Un par shard |

## 2. Contenu par Terre

| Terre | Niveaux | Ville principale | Villages | Donjons | Boss de zone |
|---|---|---|---|---|---|
| **Priméa** | 1–10 | Priméa-Ville | 3 | Ruines de Fer de la Divinité | Gardien des Premières Forges |
| **Secondil** | 10–20 | Secondil | 3 | Fosse des Brèches | Gobelin Furax (donjon) |
| **Terrae Trois** | 15–25 | Terrae Trois | 3 | Grotte de la Forêt Prismatique | Colosse de Cristal (donjon) |
| **Quatrelle** | 20–30 | Quatrelle | 3 | Barrows de Lumière | Dragon Usurpateur (donjon) |
| **Cinquepont** | 25–35 | Cinquepont | 4 | — | Serpent du Lac de Vie (donjon) |
| **Sixvallon** | 30–40 | Sixvallon | 3 | — | Seigneur des Vallées |
| **Huitbrume** | 40–50 | Huitbrume | 2 | — | Roi des Brumes |
| **Neuville** | 45–55 | Neuville | 2 | — | Gardien Déchu |
| **Dixverne** | 50–60 | Dixverne | 3 | Fond des Abysses | Ver des Sables Dorés |
| **Onzécime** | 55–65 | Onzécime | 2 | — | Colosse du Bunker (donjon) |
| **Cinquantia** | 60–70 | Cinquantia | 1 | — | Champion de l'Arène |
| **Septième** | 65–75+ | — (inconnue) | 0 | À définir | La Gardienne Effacée |

> Note : les boss de zone ont un nom provisoire « en attente de lore définitif » — un seul par Terre, respawn hebdomadaire, rotation d'emplacement (voir `WORLD.md` §3).

## 3. PNJ (population)

- **~50 PNJ nommés par ville principale** → ~550 + figures mondiales (~50 : membres de guildes canoniques, l'Alliance des Quatre, figures d'histoire) ≈ **600 au lancement**.
- **PNJ non nommés** (foule, gardes, passants) : ~3× les nommés par zone, sans quête, purement atmosphériques.
- **Budget de simulation** : horloge + graphe de relations pour tous les nommés ; comportement simplifié pour la foule (voir `NPC.md`).
- Figures nommées déjà définies : Bilac (forgeron), l'ancien roi forgeron, la femme aux vêtements d'une autre époque, la gardienne du sceau, le chef de la Bibliothèque, la Tueuse de Loup Noir, les trois fondateurs des Loups Voyageurs.

## 4. Boss (total au lancement)

| Catégorie | Nombre |
|---|---|
| Entités (2 jouables, 7 au total en service) | 7 |
| Monstres uniques (non-respawnables) | 6 |
| Boss de donjon de progression | 5 |
| Boss de zone (rotation) | ~11 |
| **Total combats « boss » au lancement** | **~24 jouables** |

## 5. Armes (catalogue cible)

| Famille | Variantes | Détail |
|---|---|---|
| Impériales (5 familles × 3 tiers) | ~15 | Épée (STR), coutelas (DEX), rapière (AGI), dague (TEC), falchion (VIT) |
| Exotiques | ~10 | Vocales, gravées, Divins, artisanales uniques |
| Reliques des Divins | ~5 | Uniques mondiaux, sources d'énergie |
| Armes d'événement/uniques nommées | ~90 | Cibles de quêtes, drops uniques, récompenses EX |
| **Total armes uniques au lancement** | **~120** | Dont ~30 « signatures » nommées |

- Chaque arme unique = variation de stats/effets + usure + nom propre (jamais deux identiques, voir `ECONOMY.md`).

## 6. Scénarios et mystères

| Item | Nombre | Statut de documentation |
|---|---|---|
| Scénarios EX | 7 (2+ voies chacun) | **Jamais documentés** (voir `QUESTS.md` §4.4) |
| Scénario bonus | 1 | Faux Lycaon (voir `BOSSES.md`) |
| Zones cachées | 3 | Accès par conditions secrètes |
| Mystères majeurs (arcs narratifs) | 5 | Origine des Divins, la Grande Bleue, Septième, La Septième, la flotte stellaire |

## 7. Quêtes (répartition cible)

| Type | Lancement | Note |
|---|---|---|
| Tranches de vie | ~120 | Générées par les PNJ autonomes |
| Situationnelles (événements) | ~80 | Réutilisables, liées aux événements mondiaux |
| De faction | ~40 | Archives, Forge Magique, Saints, guildes canoniques |
| De guilde | ~40 | Contenu clan (voir `CLANS.md`) |
| Économiques (artisanat) | ~20 | Chaînes matériaux → objets |
| **Total** | **~300** | + contenu post-lancement saisonnier |

## 8. Scope de lancement vs post-lancement

| Contenu | Lancement (cible) | Post-lancement |
|---|---|---|
| Entités jouables | 2 (Lycaon, Vésémon) | +1 par saison (cible) |
| Terres | 12 (Septième en accès secret progressif) | Nouveaux pans, extensions |
| Armes | ~120 | Ajouts par événements et arcs |
| PNJ nommés | ~600 | ~50 par saison |
| Événements | Tous les types | Saisonniers (voir `NARRATIVE.md`) |

## 9. Contrat d'implémentation (rappel moteur)

| Besoin | Module moteur |
|---|---|
| Données de contenu data-driven (tables par Terre) | `game/` (fichiers de données) |
| Génération d'objets uniques (seed par serveur) | `game/` |
| Population PNJ nommés (horloge, graphe) | `game/` (serveur) |
| Streaming par chunk (villes, villages) | `world/` + `renderer/` |
