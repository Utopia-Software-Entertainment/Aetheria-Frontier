# SERVICE — Service, modération et communauté

> L'humain derrière le monde : les GMs, la modération, le support et les événements communautaires. Le service est **invisible** tant que tout va bien. Complète `SOCIAL.md` §6 (modération en jeu) et `MONETIZATION.md` (règles de service).

> **Statut** : Validé v0.2 · **Version** : 0.2 · **MAJ** : 2026-08-11 · **Owner** : Studio · **Dépend de** : SOCIAL.md, MONETIZATION.md, CLANS.md

## 1. Principes

1. **Le service est discret** — jamais de GM visible en robe de soirée ; les interventions se font par des personnages du monde.
2. **La sanction est silencieuse** — pas d'annonce publique, pas de honte affichée (voir `SOCIAL.md`).
3. **L'humain intervient où l'auto échoue** — l'automatique gère le volume, l'humain juge le contexte.
4. **La communauté est un contenu** — événements, concours, saisons : le studio anime, les joueurs jouent.

## 2. GMs (gardien du monde)

| Fonction | Fréquence | Modalité |
|---|---|---|
| **Gestion des conflits** | À la demande | Personnages « Anciens » ou « Émissaires » |
| **Événements scénarisés** | Hebdo/mensuel | Incarnations de PNJ d'histoire |
| **Chasses aux bugs** | Continu | Rapports de glitches, reconstruction |
| **Respect des règles** | Continu | Sanctions, voir §4 |

- **Les GMs n'ont jamais de pouvoir sur l'économie** (pas d'injection d'objets, pas de réparation de perte).
- **Une perte due à un bug est reconstruite** (objet, argent) — jamais « désolé, on ne peut rien faire ».

## 3. Signalement et support

| Canal | Usage | SLA cible |
|---|---|---|
| **« Aetheria, signaler »** (voix) | Harcèlement, abus, triche | Réponse auto immédiate (liste noire) |
| **Signalement humain** (site) | Cas complexes, captures | < 48 h |
| **Support** (site/email) | Compte, facturation, pertes | < 72 h |
| **Signalements en jeu** (PNJ Ancien) | Conflits interjoueurs | Arbitrage sous 7 jours |

- **Le joueur signale par la voix ou le geste, jamais par un menu** (voir `CONTROLS.md`).
- **Rapport de clarté** : chaque sanction humaine est expliquée au sanctionné (privé, dans sa langue).

## 4. Échelle de sanctions

| Niveau | Sanction | Auto / Humain |
|---|---|---|
| 0 | Avertissement invisible (limitation discrète) | Auto |
| 1 | Limitation de canaux (voix, textes) | Auto + revue |
| 2 | Exclusion temporaire (24 h → 7 j) | Humain |
| 3 | Bannissement de compte | Humain + revue |
| 4 | Bannissement d'appareil (triche matérielle) | Humain + juridique si fraude |

- **Récidive** : toute sanction de niveau 2+ est suivie d'une **trace** (voir `ACHIEVEMENTS.md` — rien de public).

## 5. Événements communautaires

| Type | Cadence | Exemple |
|---|---|---|
| **Concours d'artisanat** | Mensuel | Meilleure arme nommée (jugée par PNJ + joueurs) |
| **Chasse aux trésors** | Saisonnier | Pistes disséminées par rumeurs |
| **Tournois de clan** | Trimestriel | Arènes de Cinquantia |
| **Premières victoires** | Événementiel | Suivi des premières Entités vaincues (journaux) |
| **Saisons narrées** | Trimestriel | Arcs de la machine à états (voir `NARRATIVE.md`) |

- Les événements communautaires sont **jouables dans le monde** (diégétiques), jamais en dehors.

## 6. Contrat d'implémentation (rappel moteur)

| Besoin | Module moteur |
|---|---|
| Outillage GM (personnages, actions) | `game/` (serveur) + `network/` |
| File de signalements et SLA | `network/` (serveur) |
| Sanctions progressives persistantes | `network/` (base de données) |
| Reconstruction de pertes (logs) | `network/` (journaux serveur) |
