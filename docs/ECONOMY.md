# ECONOMY — Économie, artisanat, marché

> L'économie d'Aetheria : l'artisanat est un métier social (PNJ et joueurs), chaque objet est unique, l'information est une monnaie. Complète `SYSTEMS.md` (vue d'ensemble) et `CLANS.md` (clans/échange d'info).

> **Statut** : Validé v0.3 · **Version** : 0.3 · **MAJ** : 2026-08-11 · **Owner** : Économie · **Dépend de** : SYSTEMS.md, CLANS.md, LOOT.md

## 1. Principes

1. **Pas de fabrication en série** — deux armes identiques n'existent pas (variations de stats/effets selon l'artisan, les matériaux, la chance).
2. **L'information est une monnaie** — cartes, identités d'Entités, emplacements de scénarios se vendent (Mahni, troc, faveurs).
3. **L'artisanat est social** — un objet rare exige plusieurs métiers et des relations (forgeron PNJ, droits de clan).
4. **La valeur vient de la rareté vraie** — jamais de « skin » d'objets identiques.

## 2. Monnaies

| Monnaie | Source | Usage |
|---|---|---|
| **Mahni** (or) | Drops, quêtes, ventes | Toutes les transactions joueur↔joueur et boutiques |
| **Faveurs** (informelles) | Relations PNJ/joueurs | Accès, droits, informations — non comptables en jeu |

- Une seule monnaie fongible : pas de « monnaie de faction » qui dilue la valeur.

## 3. Artisanat

### 3.1 Métiers
| Métier | Produits | Dépendances |
|---|---|---|
| **Mineur** | Minerais (gris, magma doré…), gemmes | Zones de récolte |
| **Bûcheron** | Bois (qualité par essence) | Zones boisées |
| **Cuiseur / collecteur** | Plantes, essences élémentaires | Saisons, météo |
| **Forgeron** | Armes, armures (voir `SYSTEMS.md`) | Minerais + matrices + droits de priorité |
| **Tanneur / tailleur** | Armures légères, sacs | Peaux de monstres |
| **Enchanteur (graveur)** | Gravures magiques, sorts | Matrices de l'Ère des Divins |
| **Alchimiste** | Potions, coatings | Essences élémentaires |

### 3.2 Raretés et qualité
| Rareté | Signature visuelle/sonore | Exemple |
|---|---|---|
| Commun | Neutre | Lame de fer |
| Rare | Lueur discrète | Dague de marais |
| Épique | Son propre (chant) | Arme gravée |
| Légendaire | Forme unique, nom propre | Arme ascensionnée (Shinka) |
| Relique des Divins | Technologie anachronique | Source d'énergie des Divins |

### 3.3 Matériaux élémentaires
- Feu : minerais de surface. Eau : profondeurs (Trinité). Terre : magma doré. Vent : stratosphère (Aurora Kamuy).
- Chaque matériau confère une propriété (résistance, affinité) et une signature sonore.

## 4. Marché

- **Boutiques PNJ** : catalogues fixes, mais prix négociés par relation (un PNJ fidèle baisse ses prix).
- **Enchères** : place à Cinquantia — objets rares, informations, droits.
- **Troc direct** : joueur↔joueur, sans intermédiaire.
- **Vente d'information** : cartes, pistes, identités — la Bibliothèque (institution des Archives) en fait commerce ; les clans négocient leurs parts entre eux (voir `CLANS.md` §4).
- **Antiquaires** : achètent et revendent les reliques — au prix fort.

## 5. Équilibre et anti-inflation

- **Sink quotidien** : frais de forge, réparations, voyages (mailbird, portails).
- **Taxe de marché** : 5 % aux enchères (sink).
- **Pas d'argent facile** : les drops d'or sont rares ; la richesse vient du travail (artisanat, exploration, négoce).
- **Prix dynamiques légers** : certains PNJ ajustent selon l'offre locale (jamais d'IA d'enchères sur les joueurs).
- **Suivi anti-bot** : détection d'activité non humaine (voir `PVP.md` pour la partie sociale).

## 6. Économie des Entités

- La première victoire sur une Entité produit des **matériaux uniques** (un seul exemplaire au monde) — les prix deviennent des événements.
- Les informations de scénarios EX se négocient entre **clans** ; chaque alliance fixe ses règles de partage (voir `CLANS.md` §4).

## 7. Contrat d'implémentation (rappel moteur)

| Besoin | Module moteur |
|---|---|
| Persistance des objets uniques (entités) | `network/` (serveur, base de données) |
| Serveur autoritatif des transactions | `network/` + `game/` |
| Génération d'objets (statistiques/effets) | `game/` (seed par serveur) |
| Enchères et marché (anti-fraude) | `network/` (serveur) |
