# BESTIARY — La faune d'Aetheria

> Les créatures du monde : familles, comportements, signaux. Chaque bête a un territoire, un langage corporel et une raison d'exister. Complète `WORLD.md` (zones) et `BOSSES.md` (Entités et uniques).

> **Statut** : Validé v0.1 · **Version** : 0.1 · **MAJ** : 2026-08-11 · **Owner** : Combat · **Dépend de** : WORLD.md, BOSSES.md

## 1. Principes

1. **Chaque créature a un comportement** — territoire, prédation, fuite, troupeau : rien ne patrouille sans raison.
2. **Chaque créature se comprend avant de se combattre** — le pattern se lit dans le corps, le son, le regard.
3. **Chaque créature est lisible sans jauge** — force, faiblesse, élément : tout est visible ou audible.
4. **Chaque créature a une place écologique** — elle mange, se reproduit (faiblement), migre.

## 2. Familles

| Famille | Exemples | Comportement | Faiblesse lisible |
|---|---|---|---|
| **Ronciers** | Ronces, jeunes Vorpaux | Territorial, charge en groupe | Lent, charge télégraphiée |
| **Vorpaux** | Lapins Vorpaux (niveau bas → élevé) | Curieux puis agressif | Oreilles : alerte sonore avant l'attaque |
| **Spectres** | Brumes, gémissements | Immatériel, ne court pas | Craint le son (commandes vocales puissantes) |
| **Golems** | Colosse de Bunker, de Cristal | Lent, tank, points vitaux multiples | Noyau visible, frappe après l'impact |
| **Bêtes blindées** | Scarabée Quad, larves blindées | Tourne le dos, charge | Articulations, dessous |
| **Créatures de la Bleue** | Corrompus, moignons | Errant, contaminant, agressif sans raison | La corruption se voit ; la lumière les gêne |
| **Prédateurs ailés** | Aigles toxiques | Piqué, harcèlement | Aile : unique point vital mobile |
| **Profondes** | Serpent du Lac, Trinité | Immersives, champ | Lumière/écho (son) |
| **Draconiques** | Dragon Usurpateur, Jinryong | Roi de territoire | Écailles anciennes : résistances visibles |

## 3. Langage de la menace (télégraphie)

Chaque attaque majeure est **annoncée** par un signal (jamais par un marqueur) :

| Signal | Sens |
|---|---|
| **Posture basse + souffle** | Charge imminente |
| **Oreilles plaquées + couinement** | Alerte avant bond |
| **Grondement grave** | Attaque de zone |
| **Silence soudain** | Attaque « invisible » (la plus dangereuse) |
| **Lueur/teinte** | Attaque élémentaire (feu rouge, eau bleue…) |

- **Règle d'or** : un joueur attentif peut **éviter sans subir** — jamais de dégâts « téléportés ».

## 4. Écologie et territoire

- **Densité** : stabilisée par le serveur (voir `WORLD.md` §3 — respawn de recolonisation).
- **Migrations** : certaines espèces changent de zone (saisons, événements).
- **Relations inter-espèces** : prédateurs chassent proies (les proies fuient les combats à proximité).
- **La Bleue corrompt** : les créatures corrompues attaquent tout, même leur propre espèce.

## 5. Drops et usages

| Source | Usage |
|---|---|
| Peaux, griffes, crocs | Tanneur, tailleur (voir `ECONOMY.md`) |
| Minéraux animaux | Matériaux d'armes (carapaces, os) |
| Essences élémentaires | Alchimie, gravure |
| Matériaux uniques (Entités) | Événements économiques (voir `BOSSES.md`) |
| Reliques de monstres | Quêtes, archéologie (Bibliothèque) |

## 6. Créatures notables (hors Entités)

| Créature | Zone | Particularité |
|---|---|---|
| **Serpent du Lac de Vie** | Ruines de Fer | Gardien d'entraînement de groupe |
| **Gobelin Furax** | Fosse des Brèches | Boss de donjon, charge en meute |
| **Colosse de Cristal** | Grotte Prismatique | Réfléchit la lumière (esquive par vision) |
| **Dragon Usurpateur** | Barrows de Lumière | A pris la place d'un ancien gardien |
| **Colosse de Bunker** | Cinquantia (approches) | Points vitaux multiples, test d'équipe |
| **Jinryong, Dragon Véritable** | Onzécime (secret) | Unique, non-respawnable (voir `BOSSES.md`) |

## 7. Contrat d'implémentation (rappel moteur)

| Besoin | Module moteur |
|---|---|
| IA comportementale (territoire, prédation) | `ecs/` + `game/` (serveur) |
| Animation et télégraphie | `renderer/` (animation) |
| Signaux audio par espèce | `audio/` (FMOD) |
| Écologie (densité, migrations) | `world/` + `game/` |
