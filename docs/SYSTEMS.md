# SYSTEMS — Systèmes de jeu

> Inspiration mécanique : les systèmes de *Shangri-La Frontier* (© Katarina / Kodansha), adaptés à nos contraintes : **aucun héros imposé — chaque joueur crée son personnage**, commandes 100 % sans manette (eye-tracking, voix, EEG/EMG, micro-sticks), physique stylisée, mode allongé.

> **Statut** : Brouillon · **Version** : 0.1 · **MAJ** : 2026-08-11 · **Owner** : Systèmes · **Dépend de** : GDD.md, CONTROLS.md

## Principes fondateurs

1. **Pas de héros, que des Éclaireurs** : l'histoire n'impose aucun personnage principal. Chaque joueur crée son personnage (origine + voie) et forge sa propre légende.
2. **Le monde respecte la physique** : l'inertie du corps influence la puissance des frappes — un coup lancé avec élan fait plus de dégâts qu'un coup statique.
3. **Zéro HUD de confort** : l'information est dans le monde (vibration, son, vision périphérique, voix interne).
4. **Le jeu récompense la justesse** : les coups critiques ne sont pas aléatoires — ils exigent de toucher les points vitaux ou d'atteindre le « timing idéal ».

## Création de personnage

Le joueur choisit son **origine** (identité sociale) et sa **voie** (métier de combat). Aucune combinaison n'est imposée par l'histoire ; les PNJ réagissent différemment selon l'origine et la réputation.

### Origines (inspirées des conventions VRMMO, transposées)
- **Vagabond** — sans attaches, bonus de chance, maîtrise lente des zones nouvelles.
- **Sang Guidant** — lignée ancienne, accès privilégié à certains secrets.
- **Héros de l'Ombre** — méritocratie de terrain, réputation acquise par les actes.
- **Enfant des Bêtes** — affinité faune, interactions animales modifiées.
- **Tout-le-monde** — départ neutre, aucun préjugé des PNJ.
- **Escrimeur** — formation militaire, bonus voies de combat.
- **Optimiste** — résilience morale, buffs légers en groupe.
- **Bluffeur** — apparence supérieure à la réalité, interactions sociales trompeuses.

### Voies
- **Chevalier** — défense, tanking, protection de groupe.
- **Mercenaire** — DPS polyvalent, armes doubles.
- **Moine (Poing de l'Esprit)** — combat à mains nues, ki, esquives.
- **Voleur → Ninja** — furtivité, coups critiques, déplacement supérieur.

Chaque origine change la façon dont les PNJ traitent le joueur (voir `NPC.md`) — sans jamais l'expliquer en jeu.

## Combat

### Lois physiques stylisées
- **Inertie = puissance** : vitesse et amplitude du mouvement réel → multiplicateur de dégâts.
- **Points vitaux** : chaque créature a des zones de faiblesse (yeux, gorge, articulation, noyau) ; les toucher déclenche des critiques.
- **Critique parfait** : frappe idéale (point vital + bon timing + élan suffisant) → dégâts maximaux.
- **Pas de spam** : les enchaînements appris « par cœur » se dégradent ; la variation est récompensée.

### Contre-mesures anti-triche « niveau divin »
- Détection d'inputs impossibles, de macros, de regards non-naturels.
- Les Entités disposent de règles spéciales (immunités, verrous de niveau) qui court-circuitent les builds optimisés.

## Équipement

### Modèle « multiplicateur × effet »
- **Pas de statistiques explicites** : chaque arme a un **multiplicateur** (ex. couteau ×2) et un **effet**.
- Dégâts = (stat de base × multiplicateur) × modificateurs (critique, buffs, debuffs, élément).
- **Armures** : apportent surtout de la VIT (vitalité) et des effets combinés.

### Forge et améliorations
- **Renforcement (Kai)** : jusqu'à 15 niveaux ; coûteux après le niveau 10.
- **Ascension (Shinka)** : transformation d'une arme en sa **forme véritable** — nécessite un **Forgeron Divin** et des matériaux rares.
- **Sets d'armure** : certains ensembles complets débloquent des fusions (ex. ensemble « Plumes Iriales » → fusion « Oiseau Vermillon »).
- **Matériaux élémentaires** :
  - Feu : minerais de surface.
  - Eau : profondeurs marines (habitat de la Trinité).
  - Terre : magma doré.
  - Vent : stratosphère (habitat d'Aurora Kamuy).
- **Armes impériales** : familles d'armes qui boostent une stat selon la variante (épée→STR, coutelas→DEX, rapière→AGI, dague→TEC, falchion→VIT).

### Armes exotiques (alignées sur nos contrôles)
- **Armes à commande vocale** : ex. un cristal armé qui tire des projectiles sur commande vocale (« Tirez », « Grandir ») — exige une VIT élevée (400+). Naturel avec notre pipeline Whisper.
- **Armes magiques gravées** : des sorts sont gravés dans la lame (grilles magiques) — l'arme lance elle-même le sort.
- **Armes d'Ère des Divins** : nécessitent une **source d'énergie** ; inutilisables sans un artisan ancien.

## Économie

- **Monnaie** : Mahni. **Pas de fabrication en série** : deux armes identiques n'existent pas — chaque pièce est unique (variations de stats/effets).
- **PNJ forgerons** : chacun a un style et un sens du nommage propre ; leur allégeance se gagne.
- **Marché** : boutiques, enchères, troc direct, vente d'information.
- **PK** : marque de crâne, pertes accrues, primes.

## Progression

- **Niveau** : augmente les stats de base (STR, DEX, AGI, TEC, VIT).
- **Statuts** : sources de VIT par équipement (ceintures, anneaux) — certains équipements exigent un seuil de VIT.
- **Malédictions permanentes** : les Marques (ex. Marque de Lycaon) modifient durablement les capacités — levées uniquement par des moyens rares (Saints, victoire sur l'Entité).
- **Compétences de déplacement** : skills utilitaires (ex. « Distorsion d'ami » — téléportation vers un coéquipier).

## Adaptation aux contraintes Aetheria

| Contrainte | Impact système |
|---|---|
| Création libre (pas de héros) | Personnages joueurs avec origine + voie ; aucune histoire imposée ; les PNJ réagissent à l'identité du personnage |
| Eye-tracking | Ciblage, points vitaux, sélection d'ennemis par regard |
| Voix (Whisper) | Commandes vocales (armes, sorts, menus) |
| EEG/EMG (OpenBCI) | « état de flux » : concentration → focus critique ; relâchement → détente, régénération |
| Mode allongé (90°) | Rotation du monde à 90° ; combats « plats » adaptés au regard horizontal |
| Physique stylisée | Inertie et élan du corps réel transmis au combat virtuel |
