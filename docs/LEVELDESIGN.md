# LEVELDESIGN — Méthodologie de construction des zones

> Comment une Terre passe du lore au terrain jouable : lecture, lisibilité VR, points d'intérêt, budget technique. Ce document est la **méthode**, `WORLD.md` est le **catalogue** et `CONTENT.md` le **chiffrage**.

> **Statut** : Validé v0.1 · **Version** : 0.1 · **MAJ** : 2026-08-11 · **Owner** : Design · **Dépend de** : WORLD.md, ART.md, CONTENT.md, BESTIARY.md

## 1. Principes

1. **La silhouette d'abord** — une zone se conçoit en ombre chinoise (voir `ART.md`).
2. **Lire sans HUD** — le terrain, la lumière et le son guident ; jamais de marqueur.
3. **Une Terre = une identité** — biome, culture, humeur, faune : tout se tient (voir `LORE.md`).
4. **Le vide est un espace** — les zones respirent ; la densité est un outil, pas un remplissage.
5. **Toujours jouable allongé** — le mode 90° est un cas de design, pas une option (voir `CONTROLS.md`).

## 2. Processus en 7 étapes

| Étape | Livrable | Question |
|---|---|---|
| 1. **Concept** | Intent sheet (1 page) | Quelle est l'humeur ? Quelle promesse de jeu ? |
| 2. **Silhouette** | Croquis ombre chinoise | Se lit-elle sans couleur ni détail ? |
| 3. **Vue depuis les repères** | Vue 90° allongé + debout | Les repères se trouvent-ils à l'horizon ? |
| 4. **Points d'intérêt** | Liste POI + connexions | Que voit-on de loin ? Que cache-t-on ? |
| 5. **Boucle locale** | Cheminement A→B→A | Le joueur revient-il sans se perdre ? |
| 6. **Contenu** | Placement faune/PNJ/ressources | Densité conforme à `CONTENT.md` ? |
| 7. **Budget** | Feuille de budget | Draw calls, mémoire, streaming OK ? |

## 3. Lecture de zone (sans HUD)

- **Trois plans de lecture** : loin (silhouettes, lueurs), moyen (formes, portes), proche (détails interactifs).
- **Langage visuel** (voir `ART.md`) : les objets interactifs se lisent par l'usure et la forme ; les lueurs signalent le rare.
- **Langage sonore** (voir `AUDIO.md`) : chaque POI a une signature (forge = marteau, ruines Divins = harmoniques).
- **Pistes** : traces, éclats, lumière — jamais de flèche.

## 4. Structure type d'une Terre

```
[Terre]
├── Ville principale (hub : forges, auberge, gardes, tableaux LFG)
├── 2–4 villages (quêtes locales, points de respawn — voir DEATH.md)
├── 3–5 zones de chasse (faune, ressources)
├── 1 donjon (progression ou événement)
├── 1 boss de zone (rotation)
├── Points d'intérêt secrets (regard + son)
└── 1 porte vers la Terre suivante (séquencement par niveau)
```

## 5. Contraintes VR et mode allongé

| Contrainte | Règle de design |
|---|---|
| **Fovéation (VRS)** | Les éléments critiques (PNJ, portes, faune) jamais en bord de champ — les cadrer par la scénographie |
| **Hauteur de vue allongée** | La vue 90° voit l'horizon et le ciel : les repères doivent exister à hauteur d'horizon |
| **Verticalité** | Utilisée avec parcimonie — les escaliers en VR allongée sont fatigants ; les rampes et plateformes dominent |
| **Téléportation/rotation** | Pas de téléportation dans le monde (cohérence) ; rotations douces, vignettage optionnel (voir `ACCESSIBILITY.md`) |
| **Confort** | Pas de mouvement brusque imposé (séismes, chutes) sans signal d'annonce |

## 6. Budget technique par zone (cible)

| Paramètre | Budget |
|---|---|
| Draw calls visibles (pointe) | ≤ 300 (voir `ART.md` §6) |
| Maillage actif | ≤ 1 500 objets visibles |
| PNJ nommés actifs par zone | ≤ 40 |
| PNJ foule par zone | ≤ 60 (simplifiés) |
| Streaming | Chunks 128 m, préchargement à l'horizon |

## 7. Tests de zone (avant intégration)

1. **Test silhouette** : la zone en noir et blanc reste lisible.
2. **Test repère** : un joueur qui sort de la ville retrouve son chemin sans carte.
3. **Test densité** : conforme au population feel (`SERVERWORLD.md` §3).
4. **Test allongé** : la boucle complète se joue couchée.
5. **Test budget** : tolérances (`BALANCE.md` §7) respectées en pointe.

## 8. Contrat d'implémentation (rappel moteur)

| Besoin | Module moteur |
|---|---|
| Éditeur de zones (outillage) | `world/` (édition) |
| Streaming par chunks | `world/` + `renderer/` |
| Budget draw calls / occlusion | `renderer/` |
| Placement data-driven (faune, PNJ, ressources) | `game/` (fichiers de données) |
