# NPC — PNJ autonomes

> Inspiration : dans *Shangri-La Frontier* (© Katarina / Kodansha), les PNJ mènent des vies qui leur appartiennent — un forgeron voyage sans prévenir, une femme cherche quelque chose qui ne concerne pas le joueur, un roi se retire. C'est la philosophie que nous transposons dans Aetheria.

> **Statut** : Validé v0.2 · **Version** : 0.2 · **MAJ** : 2026-08-11 · **Owner** : Narration · **Dépend de** : LORE.md, WORLD.md

## Philosophie

Chez nous, un PNJ n'est **jamais un panneau de quête ambulant** :

- Chaque PNJ a des actions qui lui sont propres, une routine, des lieux, des goûts.
- Chaque PNJ interagit avec les **autres PNJ** : alliances, rivalités, amitiés, affaires — qui évoluent même quand aucun joueur n'est là.
- Chaque PNJ interagit avec les **joueurs** de façon personnalisée : il se souvient, juge, aide, refuse, trahit.
- **On ne doit jamais sentir la mécanique** : ni icône au-dessus de la tête, ni boucle de dialogue figée, ni phrase « de stock » répétée, ni attente désincarnée devant un point de spawn.

## Principes

1. **Le monde tourne sans les joueurs** : si personne ne se connecte, la vie des PNJ continue (chronique des événements au retour).
2. **Chaque PNJ a un agenda** : horaire, lieux, activités — pas de présence permanente à un endroit.
3. **Chaque PNJ a des relations** : graphe dynamique PNJ↔PNJ qui peut changer l'état du monde (un artisan qui part, une ville qui ferme sa forge).
4. **Chaque PNJ a une mémoire** : bienfaits, affronts, secrets partagés — sur le long terme.
5. **Chaque PNJ juge le joueur** : origine, réputation, Marques, actes passés — le traitement varie sans jamais l'afficher.
6. **Chaque PNJ peut refuser** : refuser de parler, de vendre, d'aider — et le dire en restant poli ou non.

## Types de PNJ

### Métiers
- **Forgerons** : chacun son style, son sens du nommage, son propre catalogue et ses exigences (matériaux, allégeance). Certains exigent des droits de priorité de clan.
- **Saints** : capables de lever des Marques — service rare, cher, et personnalisé.
- **Marchands, aubergistes, gardes, archivistes** : routines commerciales, rumeurs, informations.

### Factions
- Officiers d'institutions (Forge Magique, Archives royales), gardes — avec des loyautés qui peuvent diverger de leur institution.
- Archivistes de la Bibliothèque : vendent l'information, jamais gratuitement.

### À vie propre
- Figures liées à l'histoire du monde (l'ancien roi forgeron disparu, la femme aux vêtements d'une autre époque, la gardienne du sceau).
- Ils se déplacent, voyagent, changent de rôle — sans annonce, sans quête prétexte.

## Conception de l'autonomie

### Horloge mondiale
- Agenda par PNJ (heures, jours, saisons du monde).
- Simulation allégée hors-champ ; événements résumés dans les journaux des villes (et pour le joueur à la connexion).

### Graphe de relations
- Relations PNJ↔PNJ et PNJ↔joueur avec valeur, historique et humeur.
- Les conflits peuvent déclencher des événements mondiaux (fermeture d'une boutique, expulsion d'un membre de clan, guerre de factions).

### Mémoire et langage
- Référentiel de souvenirs : qui a aidé, qui a trahi, qui porte une Marque.
- Dialogues générés selon contexte (relation, événements récents, lieu, heure) — jamais de réplique littéralement identique deux fois.
- Variation humaine : hésitations, humour, fatigue, priorités personnelles.

### Anti-« effet IA »
- Pas de télégraphie : l'intention passe par l'animation, le ton, le comportement — pas par des jauges ni des marqueurs.
- Pas de « il n'a pas de quête pour toi ».
- Comportements qui semblent contradictoires à tort (un PNJ occupé qui ignore le joueur, un artisan qui refuse d'un travail en cours).
- La technologie (modèle embarqué ou distant, Whisper pour la voix) doit rester invisible : le joueur ne doit jamais deviner qu'il parle à un modèle.

## Règles d'or

1. Un PNJ peut être **aidé, trahi ou ignoré** — et il s'en souvient.
2. Un PNJ a des **objectifs personnels** qui n'impliquent aucun joueur.
3. Un PNJ ne dit jamais « je n'ai rien pour toi » ; il a toujours une vie en cours.
4. Deux PNJ ne se croisent jamais sans possibilité d'interaction entre eux.

## Implémentation (à trancher dans synapse-engine)

- Approche à valider : règles locales (machines à états + horloge + graphe) vs modèle de langage embarqué/distante vs hybride.
- La voix des PNJ passe par notre pipeline (synthèse + Whisper pour la compréhension du joueur).
- La simulation hors-champ s'exécute côté serveur (voir architecture réseau du moteur), coût budgété par PNJ actif.
