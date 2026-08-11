# COMBAT — Combat, voies, magie, contrat physique

> Détaille le combat d'Aetheria. Complète `SYSTEMS.md` (vue d'ensemble) et `CONTROLS.md` (canaux d'entrée).

> **Statut** : Validé v0.2 · **Version** : 0.2 · **MAJ** : 2026-08-11 · **Owner** : Combat · **Dépend de** : SYSTEMS.md, CONTROLS.md, BESTIARY.md

## 1. Le contrat physique (moteur ↔ jeu)

La question « physique réaliste = moteur ? » se règle ici. Le **moteur** (synapse-engine, Jolt) fournit la simulation réaliste ; le **jeu** (ce repo) définit comment elle devient du gameplay.

### 1.1 Ce que le moteur doit fournir (boîte à outils)
- Corps rigides avec masses, inerties, frottements et matériaux (bois, fer, roche, chair, gel).
- Contact et collisions à fréquence élevée (fixe 120 Hz conseillée), à bande étroite (sweep).
- Impulsions et forces appliquées au monde à partir des mouvements du joueur (tracking).
- Contraintes (articulations, cordes, portes), destruction d'objets (splitting), détection de troncature.
- Raycasts/pénétration pour les armes : l'impact est un événement physique, pas un jet de dé.
- Data de matériaux : densité, dureté, son d'impact, réaction de recul.

### 1.2 Ce que le jeu définit par-dessus (règles de design)
- **Inertie = puissance** : la vitesse et l'amplitude du mouvement réel → multiplicateur de dégâts (courbe non linéaire : plafonner pour éviter les lésions réelles).
- **Seuils de mouvement** : en dessous d'une vélocité minimale, pas de dégâts (poussette ≠ frappe).
- **Points vitaux** : zones déclarées par créature (yeux, gorge, articulations, noyau) ; toucher une zone = critique.
- **Critique parfait** : point vital + timing (fenêtre 120 ms) + élan suffisant → dégâts maximaux + effet spécial.
- **Exceptions stylisées** : les Entités ont leurs propres lois physiques (immunités, verrous de niveau, gravité inversée de Ctharnide) — le moteur les exécute, le design les définit.

### 1.3 Règle d'or
La simulation réaliste doit **servir la lisibilité** : le joueur doit comprendre pourquoi un coup frappe fort ou rate, sans jamais voir une jauge. La physique est un langage, pas un gadget.

## 2. Les voies (classes)

| Voie | Canal | Rôle | Armes | Spécificité |
|---|---|---|---|---|
| **Chevalier** | Regard | Tank, protection | Épée longue, bouclier | Garde directionnelle (le bouclier suit le regard) |
| **Voleur → Ninja** | Regard | Furtif, critique | Lames, shurikens | Critiques sur points vitaux, déplacement |
| **Faucon des Brèches** | Regard | DPS distance | Arc, arbalète, lames de jet | Visée au regard ; « respiration » (pause = précision) |
| **Sentinelle** | Regard + allongé | Défense de zone | Pavois, armes de jet | Contrôle de zone au regard ; pensée pour le mode allongé |
| **Orateur gravé** | Voix + TEC | Support, contrôle | Cristaux, gravures sonores | Sorts par paroles ; le silence est une vulnérabilité |
| **Artilleur vocal** | Voix + VIT | DPS distance | Cristaux armés vocaux | Tirs sur commande vocale ; recharge par rythme de parole |
| **Invocateur des Vestiges** | Voix + TEC | Invocation | Reliques, grimoires | Unités des Divins invoquées par mots-clés |
| **Mercenaire** | Inertie | DPS polyvalent | Double arme (couteaux, épées) | Enchaînements à élan, style libre |
| **Marteau du Crépuscule** | Inertie | DPS lourd | Marteaux, masses | Frappes amplifiées par amplitude réelle ; compatible allongé |
| **Moine (Poing de l'Esprit)** | EEG | DPS corps-à-corps | Mains nues | Ki : concentrer l'EEG (flux) en puissance |
| **Archonte du Flux** | EEG | Contrôle, support | Orbes, sceptres | Focus long : buffs mentaux, régénération, debuffs de zone |
| **Éclaireur des Terres** | Mixte (TEC + allongé) | Mobilité, exploration | Dague, cordes, corne | Compagnon faune, pistage, survie |

- Évolution : chaque voie a une branche avancée débloquée par des **actes**, pas par le niveau seul (Voleur → Ninja, Orateur → Chantre des Échos, Éclaireur → Piste-Faune, Artilleur → Bombardier du Ciel…) — les autres branches se définissent avec chaque voie.

## 3. Actions de combat

- **Frappe légère / lourde** : amplitude + vélocité (canal corps).
- **Garde** : bouclier/croisement d'armes dirigé par le regard.
- **Esquive** : déplacement réel hors trajectoire ; fenêtre d'invulnérabilité courte.
- **Saut / roulade** : micro-stick + geste.
- **Saisie / port d'objet** : contraction EMG soutenue.
- **Sort / compétence vocale** : commande vocale → invocation (avec focus EEG requis pour les sorts forts).
- **Déplacement magique** : skills utilitaires (ex. « Distorsion d'ami » : téléportation vers un coéquipier).

## 4. Magie et éléments

### 4.1 Magie gravée
- Les sorts sont **gravés dans des supports** (lames, cristaux, grimoires) — la magie vient de l'objet, pas du lanceur.
- Une arme gravée lance son sort elle-même ; le joueur la déclenche par la voix.
- **Temps d'incantation** = temps de concentration (focus EEG maintenu).

### 4.2 Les quatre éléments
| Élément | Matériau | Habitat source | Effet signature |
|---|---|---|---|
| **Feu** | Minerais de surface | Terres chaudes | Dégâts sur la durée |
| **Eau** | Eau des profondeurs | Habitat de la Trinité | Contrôle, champs |
| **Terre** | Magma doré | Profondeurs volcaniques | Défense, poids |
| **Vent** | Vent stratosphérique | Habitat d'Aurora Kamuy | Vitesse, coups multiples |

- Affinités : les créatures ont des résistances/faiblesses élémentaires — jamais invisibles (teinte, texture, comportement).

## 5. Combat de groupe et raids

- **Groupe** : jusqu'à 8 joueurs — rôles souples, pas de trinité obligatoire.
- **Raids** : 16–32 joueurs contre les grands défis (Entités, donjons d'élite).
- **La coopération est physique** : un garde peut couvrir un allié (bouclier placé devant un corps en mouvement) ; les esquives ouvrent des fenêtres pour les critiques d'un coéquipier.
- **Raids d'Entité** : voir `BOSSES.md` — chaque Entité exige un scénario EX, pas seulement du DPS.

## 6. Antispam et lisibilité

- Les enchaînements « par cœur » se dégradent (dégâts réduits) ; la variation est récompensée.
- Pas de chiffres flottants par défaut : les impacts se **voient** (réactions physiques) et **s'entendent** (voir `AUDIO.md`).
- Mode « entrainement » : traces visuelles temporaires des fenêtres de timing (désactivées en combat réel).

## 7. Contrat d'implémentation (rappel moteur)

| Besoin | Module moteur |
|---|---|
| Simulation corps rigides réaliste | `physics/` (Jolt) |
| Détection d'élan depuis le tracking | `vr/` + `input/` |
| Raycasts d'armes, impacts, destruction | `physics/` + `renderer/` (débris) |
| Zones de points vitaux (géométrie) | `ecs/` + `physics/` |
| Sorts, buffs, effets | `ecs/` + `game/` (serveur autoritatif) |
