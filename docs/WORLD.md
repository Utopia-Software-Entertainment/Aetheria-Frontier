# WORLD — Zones, donjons, respawn, événements

> Le contenu PvE du monde. Complète `LORE.md` (narration) et `BOSSES.md` (Entités).

> **Statut** : Validé v0.2 · **Version** : 0.2 · **MAJ** : 2026-08-11 · **Owner** : Design · **Dépend de** : LORE.md, BOSSES.md, LEVELDESIGN.md

## 1. Les 12 Terres (détail)

| Terre | Biome | Niveaux | Points d'intérêt |
|---|---|---|---|
| **Priméa** | Prairies, forêts claires | 1–10 | Ville de départ, forges simples |
| **Secondil** | Marais sombres | 10–20 | Fosse des Brèches, forgerons, ateliers |
| **Terrae Trois** | Carrefour commercial | 15–25 | Portes vers l'intérieur, foires |
| **Quatrelle** | Collines, fermes | 20–30 | Quêtes de faction |
| **Cinquepont** | Rivières, lacs | 25–35 | Villages lacustres, pêche |
| **Sixvallon** | Vallées profondes | 30–40 | Faune dangereuse, camps |
| **Huitbrume** | Brumes éternelles | 40–50 | Spectres, leçon de mort |
| **Neuville** | Ancienne capitale déchue | 45–55 | Ruines urbaines, secrets des Divins |
| **Dixverne** | Déserts, mines | 50–60 | Minerais, chantiers |
| **Onzécime** | Forêts ancestrales | 55–65 | Gardiens anciens |
| **Cinquantia** | Ville-frontière riche | 60–70 | Élite, enchères, raids |
| **Septième** | Terre effacée des cartes | 65–75+ | Entrée secrète (à définir) |
| Zones secrètes (hors Terres) | ? | ? | Rabituza, Ruluath, Inventoriaire (accès spéciaux) |

## 2. Donjons

### 2.1 Donjons de progression (5)
1. **Ruines de Fer de la Divinité** — chantier antique ; unités d'opération magique ; Serpent du Lac de Vie en gardien (entraînement de groupe).
2. **Fosse des Brèches** — marais ; minerais gris ; boss : Gobelin Furax.
3. **Grotte de la Forêt Prismatique** — cristaux ; effets de lumière ; boss : Colosse de Cristal.
4. **Barrows de Lumière** — terres sans lumière ; boss de zone : Dragon Usurpateur.
5. **Fond des Abysses** — accès lié au sceau de la Grande Bleue (voir Ctharnide).

### 2.2 Règles de donjon
- **Instances** pour les donjons de progression (jusqu'à 8 joueurs).
- **Zones ouvertes** pour les grands territoires (faction, événements).
- **Chaque donjon a une clé de compréhension** : mécanique unique (lumière, son, gravité, regard) plutôt que du DPS statique.

## 3. Règles de respawn

| Type | Respawn | Note |
|---|---|---|
| **Monstres communs** | Oui (minutes) | Le monde garde une densité stable |
| **Monstres rares** | Oui (jours/semaines) | Annoncé par les PNJ/rumeurs |
| **Boss de zone** | Oui (semaines) | Rotation d'emplacement |
| **Monstres uniques** | **Non** | Jamais (voir `BOSSES.md`) |
| **Les Sept Entités** | **Non** (sauf Ctharnide, réinitialisable) | Événement mondial |

- **Respawn cohérent** : une créature tuée ne réapparaît jamais au même endroit instantanément ; le monde « se recolonise » (logique de territoire).

## 4. Cycle du monde

- **Jour/nuit** : 4 h réelles par cycle ; la nuit change la faune (prédateurs nocturnes, spectres) et les PNJ (boutiques fermées, gardes).
- **Météo** : pluie (visibilité, foudre), brume (repères), tempêtes (navires, vols).
- **Saisons** : lentes (mois) ; impact sur l'artisanat (matériaux saisonniers).

## 5. Événements mondiaux

| Type | Fréquence | Exemple |
|---|---|---|
| **Rumeurs** | Quotidien | « Un forgeron a quitté la ville » (PNJ) |
| **Événements locaux** | Hebdomadaire | Invasion de la Grande Bleue sur une terre |
| **Événements de clan** | Mensuel | Tournois, chasses à primes |
| **Événements d'histoire** | Rare | Conséquences d'une victoire sur une Entité (Ctharnide → évolution du monde) |
| **Catastrophes** | Imprévisible | Brèches du sceau, migrations de la faune |

## 6. Exploration et découverte

- **Cartes partielles** : la carte se dessine en explorant ; les cartes se vendent.
- **Points d'intérêt secrets** : découverts par le regard (lueurs, sons), jamais marqués.
- **Reliques des Divins** : coffres, ateliers, sources d'énergie — objets de quêtes et de factions.
- **Les zones secrètes** (Rabituza, Ruluath, Inventoriaire) : accès par conditions non documentées (invitations, Marques, scénarios).

## 7. Contrat d'implémentation (rappel moteur)

| Besoin | Module moteur |
|---|---|
| Streaming de zones (chargement par chunks) | `renderer/` + `world/` |
| Streaming réseau des zones partagées | `network/` |
| Simulation du cycle (jour/nuit/météo) | `world/` (serveur) |
| Événements mondiaux | `game/` (serveur) |
