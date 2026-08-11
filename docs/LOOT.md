# LOOT — Récompenses et tables de loot

> Ce que le monde donne, pourquoi, et ce qu'il **refuse** de donner. Aetheria ne récompense pas le farm : il récompense la compréhension. Complète `BESTIARY.md` (drops par créature) et `ECONOMY.md` (valeur des objets).

> **Statut** : Brouillon · **Version** : 0.1 · **MAJ** : 2026-08-11 · **Owner** : Équilibrage · **Dépend de** : BESTIARY.md, ECONOMY.md, BALANCE.md

## 1. Principes

1. **Pas de farm** — tuer 500 fois la même créature ne rapporte jamais mieux que la première fois.
2. **La première fois compte** — premier kill, première découverte, première compréhension.
3. **Les matériaux, pas les objets** — les créatures donnent des matériaux ; les objets viennent du travail (artisanat, voir `ECONOMY.md`).
4. **Le savoir est le meilleur loot** — les informations (pistes, identités, scénarios) valent plus que tout objet.
5. **Zéro loot box** — jamais d'aléatoire monétisé (voir `MONETIZATION.md`).

## 2. Ce que l'on obtient en tuant

| Source | Obtention | Réserve |
|---|---|---|
| Créatures communes | Matériaux (peaux, os, essences), Mahni rare | Diminue après 1er kill (loi anti-farm) |
| Créatures rares | Matériaux rares + **un objet unique possible** | Drop unique à la 1re fois seulement |
| Boss de zone | Matériaux épiques + gages (titres) | Rotation, voir `WORLD.md` |
| Monstres uniques | Matériaux légendaires + objets nommés | Un seul exemplaire au monde |
| Entités | Matériaux d'Ère des Divins + accès | Voir `BOSSES.md` §économie |

- **Loi anti-farm** : la 2e victoire sur une même créature rapporte ~10 % du matériel de la 1re, puis ~1 % — le monde « épuise » la ressource (et se recolonise, voir `WORLD.md` §3).
- **Boss de zone** : chaque victoire rapporte moins de matériel, mais les **gages** (preuves de victoire) restent vendables.

## 3. Tables de loot (principe)

```
Loot = f(créature, première fois ?, qualité du kill, état du monde)
```

| Facteur | Effet |
|---|---|
| Créature | Table par famille (voir `BESTIARY.md`) |
| Première fois | ×10 matériel, drop unique possible |
| Qualité du kill | Critique parfait → matériaux supérieurs (signature du joueur) |
| État du monde | Migrations, événements → matériaux saisonniers |

- Les tables sont **data-driven** (serveur) et **jamais publiées** : l'information se découvre par l'expérience ou s'achète (voir `ECONOMY.md`).

## 4. Raretés et signatures

| Rareté | Fréquence | Signature (voir `ART.md`, `AUDIO.md`) |
|---|---|---|
| Commun | ~60 % | Neutre |
| Rare | ~30 % | Lueur discrète |
| Épique | ~9 % | Son propre (chant) |
| Légendaire | ~1 % | Forme unique, nom propre |
| Relique des Divins | Uniques | Anachronique, lumière interne |

## 5. Répartition en groupe

- **Attribution libre** (le groupe se met d'accord — pas de master looter automatique).
- **Butin visible** : les objets au sol se voient et se lisent à voix haute (regard + voix, voir `UI.md`).
- **Pas de roll popup** : la négociation est une interaction sociale (voir `SOCIAL.md`).

## 6. Loot des événements

| Événement | Récompense |
|---|---|
| Invasions de la Bleue | Matériaux de corruption (rares, à usage spécifique) |
| Migrations de faune | Matériaux saisonniers |
| Victoire d'Entité | Matériaux uniques mondiaux + Marques + accès |

## 7. Contrat d'implémentation (rappel moteur)

| Besoin | Module moteur |
|---|---|
| Tables data-driven, anti-farm (serveur) | `game/` |
| Génération d'objets uniques (seed) | `game/` |
| Attribution visible (lecture, regard) | `renderer/` + `voice/` |
| Matériaux d'événements (saisons) | `game/` (événements) |
