# BOSSES — Les Sept Entités et monstres uniques

> Inspiration mécanique : les « Sept Colosses » de *Shangri-La Frontier* (© Katarina / Kodansha). Contenu original.

## Règles des Entités

- **Unicité absolue** : chaque Entité n'existe qu'une seule fois par serveur. **Aucun respawn.**
- **Invincibilité par défaut** : hors de leur **Scénario Unique EX**, elles encaissent les coups sans jamais mourir — leur barre ne descend pas.
- **Scénarios Uniques EX** : déclenchés par des conditions inconnues (objet rare, PNJ, lieu, comportement). Récompenses de niveau supérieur, progression de l'histoire mondiale.
- **Contre-mesures divines** : le système triche pour elles (métadonnées de combat, exigences de niveau, immunités) — c'est le système anti-exploit le plus strict du jeu.
- **Malédictions** : se confronter à une Entité et survivre peut marquer le joueur d'une **Marque** permanente.

## Les Sept Entités

| # | Entité | État | Scénario EX |
|---|--------|------|-------------|
| 1 | **Lycaon, le Tueur de Nuits** | Vivante | Inconnu (approches : « La Bête et la Lune ») |
| 2 | **Vésémon, le Gardien des Tombes** | **Détruite** — 1re Entité vaincue | « De l'autre côté du deuil » |
| 3 | **Ctharnide de l'Abîme** | Réinitialisable (répétable) | « Contemple l'abîme, le monde à l'envers » |
| 4 | **Siegwurm, le Maître des Cieux** | Vivante | Inconnu |
| 5 | **Orchestre de l'Écho Funèbre** | Vivante | Inconnu |
| 6 | **Goldhuneenay, l'Inépuisable** | Vivante | Inconnu |
| 7 | **La Septième** | Inconnue | Inconnu |

### Détail par Entité

**1. Lycaon, le Tueur de Nuits** — Loup colossal des plaines lunaires.
- Toute la population de joueurs a déjà échoué contre lui.
- Marque : **Marque de Lycaon** — impossible d'équiper armure de jambes et de torse ; immunité aux sorts ; interdiction de combattre des monstres plus faibles ; les PNJ traitent le marqué différemment. Permanente, levée par une Sainte ou par la mort de Lycaon.
- Particularité : peut créer des **doubles d'ombre** ; un faux Lycaon vaincu déclenche un Scénario Unique bonus.

**2. Vésémon, le Gardien des Tombes** — Gardien des morts, armure robotique de l'Ère des Divins.
- **Verrou de niveau** : pendant le combat, le niveau de tous les joueurs est figé à **50** — les stats supérieures sont neutralisées.
- Scénario « De l'autre côté du deuil » : quête d'une femme perdue (voir lore des Divins) ; première Entité jamais vaincue, par un groupe de trois Éclaireurs.
- Récompenses majeures : accès à un **Inventaire** (dimension séparée remplie d'armes des Divins), réputation mondiale.

**3. Ctharnide de l'Abîme** — Entité marine, gardienne du sceau de la Grande Bleue.
- Réinitialisable : elle réapparaît après sa mort — mais chaque victoire fait évoluer l'histoire mondiale.
- Scénario « Contemple l'abîme » : le combat se déroule dans un monde renversé (océan au-dessus).

**4–6. Siegwurm, Orchestre, Goldhuneenay** — Entités vivantes, scénarios jamais déclenchés à ce jour. Leurs faiblesses restent théoriques.

**7. La Septième** — Même les factions de chercheurs n'en connaissent ni le nom ni la forme. Certains joueurs la croient déjà vaincue, d'autres pensent qu'elle n'existe pas encore.

## Autres monstres uniques

- **Jinryong, le Dragon Véritable** — dragon authentique de l'Ère des Divins, sommet de la hiérarchie des dragons. Unique, non-respawnable, supérieur aux boss de zone.
- **Aurora Kamuy** — créature des vents stratosphériques ; son habitat fournit le matériau « vent » (voir `SYSTEMS.md`).
- **La Trinité** — créature des profondeurs marines ; habitat des matériaux « eau ».
- **Dragon Usurpateur** — boss de zone ayant pris la place d'un ancien gardien.
- **Serpent du Lac de Vie** — gardien des Ruines de Fer, niveau élevé, utilisé pour l'entraînement de groupe.
- **Colosse du Bunker** — golem antique aux points vitaux multiples.

## Design rules pour Aetheria

1. Une Entité = un événement mondial, jamais une routine de farm.
2. Les mécaniques doivent exploiter la spécificité du jeu (inertie, voix, eye-tracking) — ex. Vésémon exige des esquives précises, pas des inputs boutons.
3. La mort contre une Entité doit laisser une trace (Marque, PNJ modifié, réputation).
4. Le secret de déclenchement est un contenu à part entière : jamais documenté en jeu.
