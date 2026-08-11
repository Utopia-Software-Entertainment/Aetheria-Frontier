# QUESTS — Système de quêtes et Scénarios Uniques EX

> Le système de quêtes d'Aetheria : aucun « panneau de quête » — le monde propose, le joueur choisit. Complète `NPC.md` (PNJ autonomes) et `BOSSES.md` (Entités).

> **Statut** : Brouillon · **Version** : 0.1 · **MAJ** : 2026-08-11 · **Owner** : Narration · **Dépend de** : NPC.md, BOSSES.md

## 1. Principes

1. **Jamais de panneau au-dessus d'une tête** — une quête se propose par le dialogue, la situation, la rumeur.
2. **Le joueur ne sait jamais tout** — objectifs implicites, conditions cachées, aucune « quête marqueur ».
3. **Les quêtes viennent des vies** — un PNJ qui cherche son artisan, un garde qui ferme une porte : chaque quête est une tranche de vie.
4. **Pas de « il n'a rien pour toi »** — tout PNJ a une situation en cours.

## 2. Types de quêtes

| Type | Déclencheur | Exemple |
|---|---|---|
| **Tranche de vie** | Dialogue avec un PNJ autonome | Aider Bilac à forger un prototype |
| **Situationnelle** | Événement du monde | Défendre un village contre une invasion de la Bleue |
| **De faction** | Rang/affiliation | Archives royales : document volé |
| **De guilde** | Clan (voir `CLANS.md`) | Chasse à l'information sur une Entité |
| **Économique** | Artisanat/marché | Récolter des matériaux pour un forgeron |
| **Unique EX** | Conditions secrètes | Voir §4 |

## 3. Génération depuis les PNJ autonomes

- **Source unique** : chaque PNJ a un « fil narratif » (objectif personnel, relations, mémoire).
- **Génération contextuelle** : la quête émerge de l'état du monde (horaire, relations, météo, événements) — pas d'un catalogue statique.
- **Conséquences** : réussir/échouer/trahir modifie le graphe de relations (voir `NPC.md`) — le monde se souvient.
- **Sans journal obligatoire** : le joueur peut « oublier » une quête ; elle continue sans lui (mais il perd l'occasion).

## 4. Scénarios Uniques EX

### 4.1 Définition
Les **Scénarios Uniques EX** sont les seuls chemins pour vaincre les Sept Entités (voir `BOSSES.md`). Ce sont des chaînes de quêtes longues, secrètes et à conditions inconnues.

### 4.2 Caractéristiques
- **Conditions de déclenchement cachées** : objets rares, lieux, PNJ, comportements — jamais documentés, jamais annoncés.
- **Chaîne non linéaire** : plusieurs entrées possibles, plusieurs échecs définitifs.
- **Récompenses de niveau supérieur** : reliques des Divins, accès à des zones, Inventoriaire, armes ascensionnées.
- **Progression de l'histoire mondiale** : chaque achèvement change l'état du monde (nouveau contenu, nouvelles rumeurs).

### 4.3 Exemples (transpositions de travail)
| Scénario | Entité | Concept |
|---|---|---|
| « De l'autre côté du deuil » | Vésémon | Une femme cherche son passé ; le gardien se souvient d'elle |
| « Contemple l'abîme » | Ctharnide | Le monde se retourne : combat tête en bas |
| « La Bête et la Lune » | Lycaon | Approche non-combattante de la bête (piste inconnue) |

### 4.4 Règles de design
1. **Zéro documentation** : pas de walkthrough possible en jeu ; l'information se négocie entre joueurs (marché de l'info).
2. **Échecs définitifs possibles** : une mauvaise décision peut fermer une voie pour le serveur.
3. **Le joueur ne doit jamais savoir qu'il est entré** dans un Scénario EX avant d'en être trop loin.
4. **Chaque Entité a 2+ voies d'approche** — jamais une seule bonne réponse.

## 5. Journal et aide

- **Journal minimal** : notes du joueur (dictées par voix), pas de carte de quête.
- **Rappels contextuels** : un PNJ peut rappeler « tu avais promis… » (mémoire du monde).
- **Pas de marqueurs** : la direction se lit dans le monde (pistes, lueurs, sons).

## 6. Contrat d'implémentation (rappel moteur)

| Besoin | Module moteur |
|---|---|
| Graine/état des scénarios par serveur | `game/` (serveur autoritatif) |
| Déclencheurs d'événements (état, relations, comportements) | `ecs/` + `game/` |
| Génération de dialogues contextuels | `voice/` (Whisper) + `game/` |
| Mémoire longue (relations, décisions) | `network/` (persistance serveur) |
