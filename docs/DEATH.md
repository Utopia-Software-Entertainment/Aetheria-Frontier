# DEATH — Mort du joueur et respawn

> La mort dans Aetheria est une **expérience**, pas une punition. Elle a des coûts, des lieux, des rituels — et le monde s'en souvient. Complète `WORLD.md` (respawn des monstres) et `PVP.md` (pertes en PK).

## 1. Principes

1. **La mort coûte quelque chose** — mais jamais l'équipement entier, jamais le personnage.
2. **La mort raconte** — chaque mort a un lieu de retour, un rituel, une raison.
3. **Pas de punition à répétition** — une série de morts dégrade la pénalité (le monde « se fatigue » de punir).
4. **La mort est un choix parfois** — certains rituels exigent de mourir (scénarios EX, Marques).

## 2. Processus de mort

1. **Chute** : le joueur perd connaissance (fondu sensoriel : son qui s'éteint, haptique qui cesse).
2. **Le Voile** : espace bref entre deux mondes — le joueur voit « l'écho » de sa dernière action (pas un écran).
3. **Choix de retour** : ressusciter au dernier **sanctuaire** touché, ou (si dispo) être ranimé par un allié.
4. **Rituel de retour** : le monde « recoud » le joueur — lumière, son, quelques secondes d'invulnérabilité douce.

## 3. Points de respawn

| Type | Localisation | Règle |
|---|---|---|
| **Sanctuaire** | Villes, lieux sacrés | Point par défaut ; touché automatiquement en passant |
| **Feu de camp** | Extérieur, zones de progression | Touché volontairement (3 s de chant) |
| **Rituel de guilde** | Maison de guilde | Réservé aux membres |
| **Cimetière éloigné** | Pour les PK marqués | Loin de la zone de mort (voir `PVP.md`) |

## 4. Pénalités

| Pénalité | Détail | Exceptions |
|---|---|---|
| **Durabilité d'équipement** | L'équipement porté perd de la solidité (réparable) | Aucune (sauf reliques, voir plus bas) |
| **Ressources** | Une part des ressources de base (pas des objets uniques) est perdue | Zone tutoriel : aucune |
| **Rien d'irremplaçable** | Les objets uniques, Marques et quêtes ne sont jamais détruits par la mort | — |
| **Réputation** | Mort en PvP : réputation inchangée (l'attaquant est puni, pas la victime) | Voir `PVP.md` |

- **Série de morts** : après 3 morts consécutives au même obstacle, la pénalité de durabilité s'annule et le jeu propose (par un PNJ, jamais par un menu) une autre approche.

## 5. Résurrection

| Moyen | Source | Détail |
|---|---|---|
| **Rituel d'allié** | Compétence d'un coéquipier (Chevalier) | Fenêtre de 60 s après la chute |
| **Objet de résurrection** | Rare (artisanat, reliques) | Usage unique, coûteux |
| **Sainte** | PNJ (voir `LORE.md`) | Service payant, relationnel |
| **Sanctuaire** | Toujours disponible | La solution par défaut |

- Les objets de résurrection sont **rares** : ils se gagnent, pas s'achètent (voir `ECONOMY.md`).

## 6. La mort comme outil narratif

- **Marques** : survivre (ou mourir) contre une Entité peut marquer le joueur (voir `BOSSES.md`).
- **Scénarios EX** : certains déclencheurs exigent de mourir dans un lieu précis (jamais documenté).
- **Rituels** : des quêtes demandent une « mort volontaire » — le monde s'en souvient (mémoire des PNJ).

## 7. Anti-frustration

- **Zone tutoriel** : aucune pénalité (voir `ONBOARDING.md`).
- **Délai de réapparition** : court (10 s), pas d'attente punitive.
- **Confiance** : jamais de « perte d'expérience » — la progression du personnage est définitive.
- **Sécurité émotionnelle** : le fondu du Voile est doux (pas d'écran rouge, pas de « VOUS ÊTES MORT »).

## 8. Contrat d'implémentation (rappel moteur)

| Besoin | Module moteur |
|---|---|
| État de mort/résurrection autoritatif | `network/` + `game/` (serveur) |
| Points de respawn (sanctuaires, feux) | `world/` |
| Durabilité et réparation | `game/` (persistance) |
| Fondu sensoriel (audio/haptique) | `audio/` + `vr/` |
