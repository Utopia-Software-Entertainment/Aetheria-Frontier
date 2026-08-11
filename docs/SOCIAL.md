# SOCIAL — Vie sociale et communication

> Aetheria est un monde vivant : le social est un système de jeu. Ce document couvre les groupes, la communication, la modération et les conséquences sociales des actes. Complète `CLANS.md` (clans de joueurs) et `PVP.md` (conflits).

> **Statut** : Validé v0.2 · **Version** : 0.2 · **MAJ** : 2026-08-11 · **Owner** : Social · **Dépend de** : CLANS.md, PVP.md, SERVICE.md

## 1. Principes

1. **La communication est vocale et spatiale** — on parle avec sa voix, dans le monde, avec distance et occlusion.
2. **Les relations sont persistantes** — amis, ennemis, réputation : le monde se souvient.
3. **La modération est invisible** — jamais un message « signalé » affiché ; la sanction arrive en silence.
4. **Le social est un contenu** — LFG, rumeurs, marchés : les joueurs sont les artisans de la vie sociale.
5. **Pas de matchmaking automatique** — aucune file d'attente algorithmique : les groupes se forment **dans le monde** (non-goal assumé, voir §5).

## 2. Groupes

| Taille | Nom | Usage |
|---|---|---|
| 1 | Solitaire | Exploration, discrétion |
| 2–4 | Escouade | Quêtes, donjons courts |
| 5–8 | Groupe | Donjons, événements |
| 9–16 | Compagnie | Raids, sièges |
| 16–32 | Armée | Grands événements, guerres de clans |

- **Pas de trinité obligatoire** : un groupe se compose librement (voir `COMBAT.md`).
- **Partage d'expérience** : égalité + bonus de proximité physique (rester proche rapporte).
- **Distorsion d'ami** : téléportation vers un coéquipier (compétence) — jamais vers un inconnu.

## 3. Communication

### 3.1 Vocale (le canal principal)
- **Voix spatiale** : la voix des autres joueurs suit position, distance, occlusion (un mur étouffe).
- **Chuchotement** : proximité + geste (main près de la bouche).
- **Canaux** : Escouade (global, non spatial), Clan, Marché (annonces), Chuchotement privé.
- **Sécurité** : l'audio est traité localement (pas d'enregistrement serveur permanent) ; la transcription (Whisper) reste locale.

### 3.2 Textuelle
- **Sous-titres vocaux** : affichés comme paroles du monde (diégétiques, voir `UI.md`).
- **Runes de messagerie** : le Mailbird (oiseaux messagers, voir `LORE.md`) — messages écrits lents, prix de livraison.

### 3.3 Non-verbale
- Gestes : salut, refus, hochement (tracking corps).
- Expressions : le ton vocal prime ; pas de menu d'émotes.

## 4. Amis et listes

| Fonction | Détail |
|---|---|
| **Amis** | Invitation par regard + voix ; statut en ligne visible dans le Carnet |
| **Liste noire** | Bloque la voix, la proximité sociale et les invitations |
| **Favoris PNJ** | Marquer un PNJ (le monde le « croise » pour vous : rumeurs) |
| **Rivaux** | Suivre discrètement les actes d'un joueur (primes, chasses) |

## 5. LFG (Recherche de groupe)

- **Sans interface** : les annonces passent par les lieux (places de ville, tavernes) et les rumeurs.
- **Affiches physiques** : des tableaux dans les villes (regard + voix pour s'inscrire).
- **Le bouche-à-oreille est réel** : les PNJ répètent les annonces entendues (voir `NPC.md`).

## 6. Modération

| Sujet | Approche |
|---|---|
| **Harcèlement vocal** | Signalement par commande vocale (« Aetheria, signaler ») + liste noire immédiate |
| **Triche** | Détection automatique (serveur) + sanctions progressives, jamais annoncées |
| **RMT** | Interdit (voir `MONETIZATION.md`) ; sanctions sur les comptes |
| **Abus de PK** | Marquage automatique, primes, chasses (voir `PVP.md`) |
| **Contenu inapproprié** | Filtres vocaux et textuels locaux ; signalement humain |
| **Bans** | Progressifs : avertissement invisible → limitation de canaux → exclusion temporaire → bannissement |

- **Le médiateur PNJ** : dans les villes, un « Ancien » reçoit les conflits (duels de réparation, rédemption) — la justice du monde, pas un tribunal.

## 7. Réputation sociale

- **Karma des actes** : aide, trahison, PK — accumulé et lisible par les PNJ (pas par une jauge).
- **Conséquences** : prix négociés, accès refusés, rumeurs, invitations (voir `NPC.md`, `ECONOMY.md`).
- **Rédemption** : les Saints et les Anciens offrent des voies de réparation (quêtes, rituels).

## 8. Contrat d'implémentation (rappel moteur)

| Besoin | Module moteur |
|---|---|
| Audio spatial multijoueur (VoIP) | `network/` + `audio/` |
| États de groupe/clan autoritatifs | `network/` + `game/` |
| Modération (signalement, sanctions) | `network/` (serveur) |
| Réputation et karma persistants | `network/` (base de données) |
