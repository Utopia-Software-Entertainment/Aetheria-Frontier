# ACHIEVEMENTS — Titres, Marques et méta-progression

> Comment Aetheria se souvient de toi. Pas de popup « succès débloqué » : la reconnaissance vit dans le monde — les PNJ, les titres et les Marques. Complète `NPC.md` (mémoire) et `DEATH.md` (conséquences).

> **Statut** : Brouillon · **Version** : 0.1 · **MAJ** : 2026-08-11 · **Owner** : Narration · **Dépend de** : NPC.md, DEATH.md, BOSSES.md

## 1. Principes

1. **La méta-progression est diégétique** — titres, Marques et réputation s'affichent dans le monde, jamais en popup.
2. **Le passé se lit sur le personnage** — on devine l'histoire d'un joueur à sa tenue, son titre, sa voix.
3. **Les Marques sont des choix** — elles viennent de la confrontation, pas de la réussite automatique.
4. **Pas de liste exhaustive** — un joueur ne voit jamais « tous les succès possibles ».

## 2. Titres

| Titre | Obtention | Effet social |
|---|---|---|
| **Éclaireur** | Création de personnage | Neutre |
| **Tueur de Vésémon** | 1re victoire d'une Entité (shard) | Les PNJ s'en souviennent, les clans recrutent |
| **Marqué de Lycaon** | Survivre à Lycaon | Crainte + suspicion (voir `BOSSES.md`) |
| **Chroniqueur** | Découvrir 10 récits cachés | Accès aux archives |
| **Artisan reconnu** | 10 objets légendaires | Les forgerons négocient avec vous |
| **Titre de guilde** | Rang clan | Affiché près du nom (diégétique) |
| **Titres d'événement** | Victoires d'événements | Valables une saison |

- **Port du titre** : choisi par le joueur, visible près du nom (voir `UI.md`) — les PNJ l'utilisent dans le dialogue.
- **Titres liés aux Entités** : un seul porteur par titre de victoire (l'unicité se partage entre les membres du groupe victorieux).

## 3. Marques (malédictions et honneurs)

| Marque | Source | Effet |
|---|---|---|
| **Marque de Lycaon** | Survie vs Lycaon | Restrictions d'équipement, réactions PNJ (voir `BOSSES.md`) |
| **Marque de la Bleue** | Corruption subie | Teinte, PNJ méfiants, accès Ruluath |
| **Marque de Rédemption** | Réparation (Saints, Anciens) | Efface une Marque, trace de l'acte |
| **Marque de PK** | Attaque non consentie | Crâne près du nom, primes (voir `PVP.md`) |

- **Une Marque n'est jamais un trophée** : c'est un changement de vie, souvent réversible mais jamais sans trace.

## 4. Mémoire du monde (la vraie récompense)

- **Le monde se souvient par les PNJ** : un PNJ peut dire « je t'ai vu affronter Lycaon » des mois après l'événement (mémoire longue, voir `NPC.md`).
- **Les actes reconnus** (premières victoires, grandes trahisons) entrent dans les **journaux de ville** — lus par les PNJ, cités par les rumeurs.
- **Héritage** : les noms des groupes victorieux d'Entités sont gravés (monuments, plaques) — la seule « liste » que le jeu affiche.

## 5. Ce qui n'existe PAS

- Pas de fenêtre de succès (popup), pas de score global.
- Pas de succès de farm (« tuez 1000 gobelins »).
- Pas de succès payants (voir `MONETIZATION.md`).
- Pas de liste complète consultable.

## 6. Contrat d'implémentation (rappel moteur)

| Besoin | Module moteur |
|---|---|
| Titres, Marques, réputation persistants | `network/` (base de données) |
| Reconnaissance dans les dialogues PNJ | `game/` + `voice/` |
| Journaux de ville (mémoire mondiale) | `game/` (serveur) |
| Affichage diégétique (noms, plaques) | `renderer/` |
