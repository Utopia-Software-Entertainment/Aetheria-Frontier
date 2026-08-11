# NARRATIVE — L'histoire du monde

> Aetheria n'a pas de « quête principale » au sens classique : il a une **histoire du monde** qui avance avec ou sans les joueurs, et que les joueurs font bouger à coups d'événements. Complète `LORE.md` (le passé) et `QUESTS.md` (les quêtes).

> **Statut** : Validé v0.2 · **Version** : 0.2 · **MAJ** : 2026-08-11 · **Owner** : Narration · **Dépend de** : LORE.md, QUESTS.md, WORLD.md

## 1. Principes

1. **Le monde raconte sans texte imposé** — pas de cinématiques de 5 minutes : des faits, des rumeurs, des traces.
2. **L'histoire avance toujours** — des événements se produisent hors connexion (résumés à la connexion).
3. **Les joueurs sont les acteurs** — vaincre une Entité est un acte narratif mondial, pas une quête personnelle.
4. **Le mystère central ne se résout pas vite** — l'Ère des Divins se comprend en années de contenu.

## 2. L'arc central : l'Ère des Divins

- **Question de fond** : pourquoi la flotte stellaire est-elle tombée ? Que sont devenus les Divins ?
- **Pistes distribuées** : ruines, reliques, PNJ anciens (l'ancien roi forgeron, la femme aux vêtements d'une autre époque — voir `NPC.md`).
- **Réponses en strates** : chaque couche de réponse ouvre deux nouvelles questions (voir `LORE.md` §Principes de ton).
- **Chronologie mondiale** : un état du monde serveur qui évolue (système d'« âges »).

## 3. La machine à états du monde

| État | Déclencheur | Effet |
|---|---|---|
| **Paix fragile** | Départ | Monde stable, mystères dormants |
| **Première brèche** | Première victoire sur une Entité (Vésémon) | Rumeurs mondiales, nouvelles quêtes, respect des PNJ |
| **Sceau affaibli** | Victoire sur Ctharnide (répétable) | La Bleue gagne du terrain, événements de corruption |
| **Réveil** | Première approche sérieuse de Lycaon | Les clans se mobilisent, l'information devient cruciale |
| **Âge des Éclaireurs** | 2+ Entités vaincues | Le monde s'ouvre : zones secrètes, technologie des Divins accessible |
| **La Septième** | Conditions inconnues | État final — le mystère reste ouvert |

- **Jamais de retour en arrière** : un état atteint ne se défait pas (sauf événements catastrophiques prévus).

## 4. Raconter sans texte imposé

| Moyen | Exemple |
|---|---|
| **Rumeurs PNJ** | « Ils disent que le forgeron est parti vers le nord… » |
| **Traces physiques** | Champ de bataille gelé, arbre foudroyé, porte scellée |
| **Changements de monde** | La faune migre, les prix changent, les gardes changent de garde |
| **Objets narratifs** | Lettres, journaux, gravures sur les armes ascensionnées |
| **Événements** | Brèches de la Bleue, tournois, mariages de PNJ, funérailles |
| **Le silence** | Une ville « trop calme » est un récit en soi |

## 5. Les acteurs du récit

- **PNJ à vie propre** : ils portent l'histoire (voyages, secrets, relations) — voir `NPC.md`.
- **Clans** : les alliances et trahisons écrivent des chapitres (voir `CLANS.md`).
- **Joueurs** : les victoires, les chutes, les trahisons deviennent des **rumeurs** que les PNJ répètent.
- **Le serveur** : horloge mondiale + états = le « narrateur » invisible.

## 6. Événements scénarisés (arcs)

| Arc | Durée | Contenu |
|---|---|---|
| **L'héritage des Divins** | Continu | Ruines, reliques, compréhension du passé |
| **La Bleue remonte** | Saison | Corruption croissante, défenses, sacrifice possible |
| **La chasse aux Entités** | Événements liés aux victoires | Récompenses mondiales, nouvelles voies |
| **La guerre des clans** | Jusqu'à résolution | Conflits déclarés, conséquences économiques |
| **Les éclipses** | Ponctuel (calendrier du monde) | Événements célestes qui ouvrent des scénarios EX |

## 7. Règles de design narratif

1. **Jamais de monologue de PNJ > 30 secondes** — l'action ou la rumeur prime.
2. **Chaque victoire majeure change le monde visiblement** — pas de fanfare : un fait.
3. **Les échecs sont narratifs aussi** — une Entité vaincue par une autre voie ferme des pistes pour tous.
4. **Le joueur ne sait jamais si l'histoire « le concerne »** — le monde ne se met pas en pause pour lui.

## 8. Contrat d'implémentation (rappel moteur)

| Besoin | Module moteur |
|---|---|
| Machine à états mondiaux (serveur) | `game/` (autorité) |
| Horloge mondiale + chronologie | `game/` + `world/` |
| Rumeurs générées (PNJ → dialogue) | `game/` + `voice/` |
| Persistance des états d'arc | `network/` (base de données) |
