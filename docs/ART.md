# ART — Direction artistique

> L'identité visuelle d'Aetheria : un contraste **médiéval ↔ techno des Divins**, une lisibilité sans HUD, et des contraintes de performance VR strictes. Ce document oriente les assets et le style.

## 1. Principes

1. **Le contraste est la signature** — le monde « actuel » est médiéval-organiciste ; l'Ère des Divins est lisse, lumineuse, anachronique.
2. **La lisibilité prime** — chaque créature, objet, PNJ se distingue en un coup d'œil (et un coup d'oreille).
3. **Le style sert la performance** — la direction artistique s'écrit avec les contraintes VR (voir §6).
4. **Le vide est un espace** — les Terres respirent ; la densité se gagne, elle ne se pose pas.

## 2. Les deux registres

| Registre | Monde actuel | Ère des Divins |
|---|---|---|
| **Palette** | Terres, bois, ocres, bruns, verts sourds | Blancs, ors pâles, cyan froid, métal brillant |
| **Matériaux** | Bois usé, fer forgé, pierre brute | Alliages lisses, cristaux, lumières internes |
| **Formes** | Organiques, irrégulières, utilitaires | Géométriques, symétriques, « fonctionnelles » |
| **Son** | Résonances sourdes | Harmoniques claires, chants |
| **Rôle** | Le présent | Le mystère (et la menace) |

- **Règle d'or** : un objet de l'Ère des Divins se reconnaît **de loin** par sa lumière et sa géométrie.

## 3. Palette par Terre

| Terre | Dominante | Accent |
|---|---|---|
| Priméa | Vert tendre, ambre | Blanc des premières ruines |
| Secondil | Gris-vert marais, boue | Or de forge (ateliers) |
| Terrae Trois | Rouge brique, cuivre | Bannières multicolores |
| Quatrelle | Blé, brun | Bleu des fermes |
| Cinquepont | Bleu d'eau, argent | Lac reflets |
| Sixvallon | Vert profond, gris roche | Feuilles sombres |
| Huitbrume | Gris, indigo | Blanches brumes |
| Neuville | Pierre sombre, rouille | Ors déchus |
| Dixverne | Sable, ocre rouge | Turquoise des oasis minérales |
| Onzécime | Vert noir, brun mousse | Cyan des gardiens |
| Cinquantia | Marbre, laiton | Gemmes des enchères |
| Zones secrètes | Voir registre Divins / Abîme | — |

## 4. Silhouettes (lisibilité)

- **Créatures** : 3 masses lisibles (tête, corps, membres) ; un trait signature (les oreilles des Vorpaux, le noyau des Golems).
- **PNJ** : silhouettes distinctes par métier (le forgeron : épaules larges + tablier clair ; l'archiviste : cape + livres).
- **Entités** : à part — elles violent la silhouette (taille, nombre de membres, lumière inversée).
- **Objets interactifs** : un léger liseré de lumière chaude (visible, non diégétique par choix assumé ? **non** — les objets interactifs se lisent par la forme et l'usure, pas par un liseré).

## 5. Animation

- **Le poids passe par l'animation** : les frappes lourdes ont un « vent » (swing), les esquives un « glissé ».
- **Télégraphie** : voir `BESTIARY.md` §3 — chaque attaque majeure a une **pose d'annonce** de 400–700 ms.
- **Aucune animation « flottante »** : tout corps a une masse visible (sauf spectres, volontairement).
- **PNJ** : micro-variations (hochements, regards) — l'animation sert l'« humanité » (voir `NPC.md`).

## 6. Contraintes de performance VR

| Contrainte | Réponse artistique |
|---|---|
| **Taux de rafraîchissement** | Budget draw calls par chunk ; occlusion généreuse |
| **Résolution effective** | Foveated rendering (VRS) : les bords sont flous, le centre net — les détails critiques au centre |
| **Texture** | Petites textures + matériaux procéduraux (bois, pierre) ; pas de photoréalisme parfait |
| **LOD** | Silhouettes d'abord : le LOD1 garde la silhouette signature |
| **Éclairage** | Baked + lumière dynamique limitée (torches, sorts) |
| **Transparences** | Éviter les doubles faces ; brume en billboards |
| **FM (asynchronous spacewarp)** | Dessiner « assez bien » en dégradé : pas de scintillement, pas de moiré |

- **Cible de confort** : 90 fps natif (PSVR2 : 120 Hz avec reprojection), motion-to-photon < 20 ms.
- **Mode allongé** : la même direction artistique est calibrée pour la rotation 90° (horizons, repères verticaux).

## 7. Direction des assets (cahier des charges)

1. **Chaque asset a une intention** : forme → fonction → émotion (l'ordre compte).
2. **Tout se dessine en silhouette d'abord** : si une créature n'est pas lisible en ombre chinoise, elle est refaite.
3. **Les armes racontent** : l'usure, le style du forgeron, l'Ère (voir `ECONOMY.md`).
4. **Zéro asset « décoratif » inutile** : tout objet est potentiellement interactif (physique, voir `COMBAT.md`).

## 8. Contrat d'implémentation (rappel moteur)

| Besoin | Module moteur |
|---|---|
| Rendu (Vulkan, VRS, occlusion) | `renderer/` |
| Animation pondérée + télégraphie | `renderer/` (skeleton, blend trees) |
| Éclairage baked + dynamique limité | `renderer/` |
| Streaming d'assets par chunk | `world/` + `renderer/` |
