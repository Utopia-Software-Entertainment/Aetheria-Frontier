# CLANS — Clans de joueurs : création, structure, alliances, guerre

> Le système de clans d'Aetheria. **Les clans sont créés par les joueurs — aucun clan n'existe au lancement.** « Clan » et « guilde » sont synonymes dans le monde (les PNJ emploient les deux). Complète `SOCIAL.md` (groupes, communication), `PVP.md` (conflits) et `ECONOMY.md` (information comme monnaie).

> **Statut** : Validé v0.2 · **Version** : 0.2 · **MAJ** : 2026-08-11 · **Owner** : Social · **Dépend de** : SOCIAL.md, PVP.md, ECONOMY.md, SERVERWORLD.md

## 0. Principe fondateur

1. **Les clans sont des créations de joueurs** : aucun clan n'est pré-établi par le monde, aucun clan de PNJ, aucun clan canonique. Le monde part **vierge** au lancement — les organisations émergent des joueurs, et seulement d'eux.
2. **Les institutions ne sont pas des clans** : la Forge Magique, les Saints, les Archives royales sont des factions PNJ. On peut y adhérer (rangs, faveurs), jamais les « diriger » comme un clan.
3. **Les clans légendaires du passé étaient des clans de joueurs** : les vainqueurs de Vésémon (trois Éclaireurs), les grandes chasses aux Entités — tout cela fut accompli par des joueurs. Ces clans n'existent plus que dans les archives et les souvenirs (voir `NARRATIVE.md`).
4. **Aucun clan ne peut vaincre une Entité seul** : la compétition d'information est aussi importante que la compétition de combat — c'est ce qui pousse aux alliances.

## 1. Création

| Champ | Règle (valeurs à valider en playtest) |
|---|---|
| **Condition** | Niveau 10+ ; payer le **sceau de clan** (50 000 Mahni, cible) ; être seul (pas de clan actif) |
| **Nom** | Unique (vérifié), diégétique, visible — les noms « hors monde » sont refusés par les PNJ greffiers |
| **Emblème** | Gravure de clan (modifiable, coûteuse), affichée : bannière, sceau sur les maisons, marque sur les objets |
| **Fondateurs** | 1 à 5 joueurs présents à la création ; le fondateur devient **chef** |
| **Limite par joueur** | Un seul clan à la fois ; changer de clan = quitter l'ancien (délai de grâce, voir trahison §6) |
| **Limite par shard** | Cap de clans actifs par shard (voir `SERVERWORLD.md`) — la rareté des noms est un contenu |

- La création se fait auprès d'un **greffier de clan** (PNJ institutionnel présent dans les capitales) — un rituel public, jamais un menu.
- Un joueur sans clan est un **indépendant** : aucun désavantage mécanique, mais pas d'accès au contenu de clan (maison, donjons, droits).

## 2. Structure et rôles

- **Chef** (fondateur ou élu) : pleins pouvoirs (recrutement, trésor, alliances, guerre, dissolution).
- **Officiers** : délégués par le chef — recrutement, trésor partiel, déclarations mineures.
- **Rangs personnalisables** : chaque clan nomme ses rangs (cœur, lame, éclaireur…) — le titre s'affiche près du nom, diégétique (voir `ACHIEVEMENTS.md`).
- **Effectifs** : de 5 (clan d'amis) à 100+ (armée) ; les raids d'Entité (16–32, `COMBAT.md`) exigent soit un clan de taille suffisante, soit une **alliance** — c'est voulu.
- **Départ / exclusion** : l'exclusion d'un membre est un acte public (le greffier en garde trace) ; les PNJ réagissent (voir `NPC.md` — loyautés qui peuvent diverger du clan).

## 3. Vie de clan

- **Maison de clan** : siège dans une ville (achat, agrandissement) ; sert de point de rassemblement, de stockage partagé et de **rituel de mort** (voir `DEATH.md`) pour les membres.
- **Trésor** : contributions, taxes sur les ventes de clan, butin de donjons de clan.
- **Droits de priorité** : un clan peut obtenir des droits chez certains forgerons PNJ (voir `ECONOMY.md`, `NPC.md`) — négociés, jamais achetés d'office.
- **Quêtes de clan** (~40 au lancement, voir `CONTENT.md`) : chasses à l'information sur les Entités, expéditions, entraînements.
- **Donjons de clan** (~12, voir `WORLD.md`) : instances réservées, défis d'équipe.
- **Tournois de clan** (trimestriels, `SERVICE.md`) : arènes de Cinquantia.

## 4. Alliances

- **Pacte d'alliance** : contrat signé entre chefs (au greffier) — non-agression, défense mutuelle, partage d'information, accès aux droits réciproques.
- **Confédération** : alliance élargie avec un nom commun (ex. la chasse à une Entité) ; les membres restent des clans distincts.
- **Règle d'or des alliances de chasse** : toute découverte sur une Entité est partagée avant la fin de la journée de jeu — héritée des clans vainqueurs de Vésémon.
- **Alliances économiques** : accès croisés aux forges, aux zones, aux enchères — l'information se négocie comme monnaie (`ECONOMY.md`).
- **Durée** : pacte à durée définie (1 saison de jeu), renouvelable — jamais éternel.

## 5. Guerre entre clans

- **Déclaration** : surenchère sur des droits (enchères, territoire, forges) ou acte d'hostilité déclaré (voir `PVP.md`).
- **Territoires** : les clans peuvent revendiquer des zones (voir `PVP.md` — conquête, conséquences économiques) ; jamais de zones de départ ni de sanctuaires.
- **Conséquences** : droits perdus, taxes, réputation — la guerre de clan est un **événement mondial** (voir `NARRATIVE.md`), pas un mode anonyme.
- **Médiation** : les institutions PNJ peuvent servir de médiateurs (trêves, arbitrages) — leurs faveurs se gagnent.
- **La guerre ne suspend pas le PK** : les règles de `PVP.md` s'appliquent ; tuer dans le cadre d'une guerre n'ajoute pas la marque de crâne, mais les conséquences économiques restent.

## 6. Réputation, trahison, mémoire

- **Réputation de clan** : les PNJ réagissent au clan (méfiance, respect, refus de service) — voir `NPC.md`.
- **Trahison** : rompre un pacte, voler le trésor, quitter pendant une guerre — conséquences de réputation (le monde se souvient, `ACHIEVEMENTS.md`), primes possibles.
- **Dissolution** : le chef peut dissoudre le clan (l'héritage part aux institutions) ; les clans abandonnés (chef absent 90 jours, cible) passent sous tutelle PNJ puis se dissolvent.
- **Mémoire du monde** : victoires d'Entités, guerres, trahisons restent dans les archives — les clans futurs peuvent les étudier (contenu narratif, `NARRATIVE.md`).

## 7. Design rules

1. **La connaissance est un actif** : les clans vendent, échangent ou refusent l'information (livres, cartes, enregistrements de combat).
2. **La guerre de clans est un contenu** : déclarée, encadrée, à conséquences — jamais du chaos anonyme.
3. **Les alliances se négocient** : pacte, trahison et rééquilibrage font partie du récit mondial.
4. **Les PK sont un contenu** : marque de crâne, primes, chasses à l'homme organisées (voir `PVP.md`).
5. **Le clan ne protège pas des conséquences individuelles** : une Marque, une prime ou une réputation personnelle restent personnelles.
6. **Aucun clan pré-établi** : chaque organisation naît d'un joueur — le monde réagit, il n'impose rien.
7. **Un clan se lit comme un personnage** : nom, emblème, actes — tout est diégétique, rien n'est un panneau de menu.

## 8. Contrat d'implémentation (rappel moteur)

| Besoin | Module moteur |
|---|---|
| États de clan autoritatifs (membres, rangs, alliances, guerres) | `game/` (serveur) |
| Maison de clan (achat, agrandissement, rituel de mort) | `world/` + `renderer/` |
| Donjons de clan (instances réservées) | `world/` + `network/` |
| Réputation de clan (réactions PNJ, mémoire) | `game/` + `ecs/` (graphe de relations) |
| Événements de clan (guerres, tournois, médiation) | `game/` (événements mondiaux) |
