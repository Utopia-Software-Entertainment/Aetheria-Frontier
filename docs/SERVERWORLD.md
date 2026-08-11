# SERVERWORLD — Structure serveur et monde

> Comment le monde est découpé, peuplé et orchestré côté service. C'est du **game design de la population** : combien de joueurs se croisent, où, et comment le monde le « sent ». Complète `GDD.md` §8 (cible technique) et `WORLD.md` (événements).

> **Statut** : Validé v0.2 · **Version** : 0.2 · **MAJ** : 2026-08-11 · **Owner** : Design · **Dépend de** : GDD.md, WORLD.md, NARRATIVE.md, SOCIAL.md

## 1. Principes

1. **Le monde doit se sentir habité, pas plein** — la densité ressentie prime sur le chiffre de CCU.
2. **Un shard = un monde continu** — pas de salle d'attente, pas de « canal » visible.
3. **Les événements globaux sont le liant** — un shard se vit comme une seule histoire.
4. **Cross-shard : non au lancement** — la séparation est assumée et expliquée en lore (voir §5).

## 2. Architecture (cible v0)

| Paramètre | Valeur | Note |
|---|---|---|
| CCU par shard | **500** | Cible v0 (voir `BALANCE.md` §7) |
| Shards au lancement | 2–4 | Par région linguistique |
| Monde | Continu par shard | 12 Terres dans un seul monde |
| Instances | Donjons uniquement | Zones ouvertes jamais instanciées |
| Server meshing | **À terme** | Hors scope v0 |

## 3. Densité et population feel

| Situation | Densité cible |
|---|---|
| Ville principale (pointe) | 100–150 joueurs visibles |
| Route entre villes | 5–15 joueurs |
| Zone de farm / chasse | 20–40 joueurs |
| Zone sauvage (Sixvallon, Huitbrume) | 0–10 joueurs |
| Village | 10–30 joueurs |

- **Règles d'équilibre de population** :
  - Un joueur croise rarement > 40 personnes à la fois (perception VR).
  - Les zones trop pleines poussent des incitations vers d'autres Terres (rumeurs, événements locaux).
  - Les zones trop vides attirent des événements (migrations de faune, invasions de la Bleue).
- **PNJ comme régulateur** : les rumeurs (voir `NARRATIVE.md`) orientent les joueurs là où le monde a besoin de présence.

## 4. Événements globaux (orchestration)

| Type | Portée | Orchestration |
|---|---|---|
| Rumeurs | Shard entier | Diffusion par PNJ, journaux de ville |
| Événements locaux | 1 Terre | Programme hebdomadaire, déclencheur par densité |
| Événements de clan | Shard | Inscription, arènes, tours |
| Victoire sur une Entité | Shard entier | Machine à états (`NARRATIVE.md`), impact durable |
| Catastrophes | Shard entier | Réponse à la densité (vide → brèche ; plein → invasion) |

- **Un événement ne se déclenche jamais devant zéro joueur** : il attend, rôde, puis éclate.
- **Les événements sont visibles de loin** (signatures audio/visuelles, voir `AUDIO.md`, `ART.md`).

## 5. Cross-shard : la décision

- **v0 : aucun cross-shard** — joueurs, clans, économie sont liés à un shard.
- **Explication lore** : chaque shard est une **« instance du monde »** — les cartographes parlent de mondes parallèles (justification diégétique).
- **Migration** : possible par transfert de personnage **à sens unique** (payant en temps réel, jamais en argent réel — voir `MONETIZATION.md`), sans objets d'économie portables.
- **À terme** : server meshing pour les grandes batailles (Entités) — les clans multi-shards se coordonnent déjà par le discours (voir `SOCIAL.md`).

## 6. Instances vs zones ouvertes

| Contenu | Type | Raison |
|---|---|---|
| Donjons de progression | Instance (≤ 8) | Réutilisabilité, progression garantie |
| Donjons d'événement | Instance (≤ 16) | Timing, scénario |
| Zones de quêtes de faction | Ouvertes | Le monde vit, les conflits se croisent |
| Sièges / raids d'Entité | Ouvertes (≤ 32) | Événement mondial, spectateurs autorisés |
| Zones secrètes | Ouvertes, faible population | Rareté de l'accès |

## 7. Contrat d'implémentation (rappel moteur)

| Besoin | Module moteur |
|---|---|
| Shards + 500 CCU (cible) | `network/` |
| Zones partagées (streaming, occupation) | `network/` + `world/` |
| Instances (donjons) | `network/` + `game/` |
| Orchestrateur d'événements (densité, horaires) | `game/` (serveur) |
| Machine à états du monde | `game/` (serveur, voir `NARRATIVE.md`) |
