# BOSSCONCEPTS — Concepts de combat par Entité

> Les idées de combat propres à chaque Entité : phases, mécaniques liées aux canaux (regard, voix, inertie), environnement, Marques. **Les conditions de déclenchement des Scénarios EX restent secrètes** — ce doc décrit le combat, pas le chemin pour y arriver. Complète `BOSSES.md` (règles générales) et `COMBAT.md` (système).

> **Statut** : Validé v0.2 · **Version** : 0.2 · **MAJ** : 2026-08-11 · **Owner** : Combat · **Dépend de** : BOSSES.md, COMBAT.md, CONTROLS.md · **Complété par** : BOSSDOSSIERS.md (dossiers complets de tous les boss : forces, faiblesses, IA)

## 1. Principes

1. **Chaque Entité exploite un canal en priorité** (regard, voix, inertie, ou combinaison).
2. **Chaque Entité a une mécanique de lecture** (télégraphie) et une mécanique de **rupture** (elle peut tricher).
3. **Les phases changent les règles** — jamais un simple « plus de dégâts ».
4. **Environnement = arme** — l'arène participe autant que les joueurs.
5. **La Marque est le souvenir du combat** — chaque victoire ou survie change la vie.

## 2. Lycaon, le Tueur de Nuits

- **Canal principal** : regard (il vous regarde, vous le regardez).
- **Environnement** : plaines lunaires, nuit permanente de l'arène.
- **Lecture** : sa pose d'annonce est sa silhouette contre la lune — il télégraphie par ombres.
- **Mécanique signature — Les Doubles** : il crée des doubles d'ombre (voir `BOSSES.md`) ; distinguer le vrai exige de **tenir le regard** du vrai (fixation longue) sans être aveuglé par les faux.
- **Mécanique de rupture** : il **rompt le regard** — les joueurs qui clignent ou détournent les yeux perdent le verrouillage.
- **Phases** :
  1. *La Meute* — doubles à distance, il observe (test de lecture).
  2. *La Chasse* — poursuite ; l'inertie de fuite du joueur compte (esquives réelles).
  3. *La Lune* — le vrai Lycaon attaque de face, fenêtre de critique sur la gorge.
- **Marque** : Marque de Lycaon (voir `BOSSES.md`) — restrictions d'équipement, PNJ méfiants.

## 3. Vésémon, le Gardien des Tombes

- **Canal principal** : inertie et précision (esquives et frappes justes).
- **Environnement** : nécropole des Divins, sol meuble, tombes qui s'ouvrent.
- **Verrou de niveau 50** (voir `BOSSES.md`) — les stats élevées ne protègent pas.
- **Lecture** : chaque attaque majeure a un **trait lumineux** (armure robotique) — la pose d'annonce est géométrique.
- **Mécanique signature — Le Deuil** : phases où l'Entité **s'arrête et se souvient** (lié au scénario « De l'autre côté du deuil ») — les joueurs doivent **résister à attaquer** (discipline, pas de DPS).
- **Mécanique de rupture** : les attaques ignorent les gardes parfaites au-delà d'un compteur de « colère » — changer de rythme obligatoire.
- **Phases** :
  1. *Le Veilleur* — défense mécanique, attaques prévisibles (apprentissage).
  2. *Le Gardien* — verrou de niveau, tombes actives, esquives requises.
  3. *Le Deuil* — fenêtre de vulnérabilité par non-action ; le groupe qui respecte le silence gagne.
- **Marque** : aucune connue — la première victoire a effacé la Marque par rédemption collective.

## 4. Ctharnide de l'Abîme

- **Canal principal** : voix (commande de gravité) et regard (orientation).
- **Environnement** : monde **renversé** (océan au-dessus) — l'orientation verticale est un défi.
- **Lecture** : ses tentacules télégraphient dans l'eau (réverbération sonore, voir `AUDIO.md`).
- **Mécanique signature — Le Monde à l'Envers** : la gravité s'inverse par phases ; les joueurs s'orientent par la voix (« Aetheria, haut ») et le regard.
- **Mécanique de rupture** : l'océan **étouffe les commandes vocales** (mufflé) — articuler fort ou utiliser le geste.
- **Réinitialisable** : chaque victoire fait évoluer l'histoire mondiale (sceau, voir `BOSSES.md`).
- **Phases** :
  1. *Le Sceau* — tentacules en défense, apprendre la lecture sonore.
  2. *L'Abîme* — gravité inversée, combats « tête en bas ».
  3. *Le Silence* — commandes vocales compromises, recours au geste et au regard.
- **Marque** : Marque de la Bleue (si touché par la corruption).

## 5. Siegwurm, le Maître des Cieux (concept)

- **Canal principal** : regard (ciblage des parties) + voix (commandes de tempête ?).
- **Environnement** : stratosphère, plateformes volantes (habitat d'Aurora Kamuy).
- **Idée de phase** : le dragon est **hors de portée** la moitié du temps — seuls les points vitaux visibles par le regard (yeux, gorge, noyau) sont atteignables.
- **Ouvert** : mécanique de rupture à concevoir (voir `BOSSES.md` — faiblesses théoriques).

## 6. Orchestre de l'Écho Funèbre (concept)

- **Canal principal** : audio (voir `AUDIO.md`) — le combat se mène aux oreilles.
- **Environnement** : salle de concert des Divins, instruments animés.
- **Idée de phase** : l'Entité **joue** ; les joueurs esquivent la musique (indices sonores = attaques) ; le silence est la vulnérabilité.
- **Ouvert** : à définir avec le design audio.

## 7. Goldhuneenay, l'Inépuisable (concept)

- **Canal principal** : inertie — le colosse ne se bat pas contre la force, mais contre l'**endurance**.
- **Environnement** : champ de bataille doré, bras multiples.
- **Idée de phase** : laisser l'Entité **s'épuiser elle-même** (elle régénère par le combat) ; les esquives comptent plus que les frappes.
- **Ouvert** : à définir.

## 8. La Septième (inconnue)

- **Rien n'est défini** — ni nom, ni forme, ni mécanique (voir `BOSSES.md`).
- Contrainte de design : sa mécanique doit être **la plus surprenante** — réservée à la fin de service.

## 9. Contrat d'implémentation (rappel moteur)

| Besoin | Module moteur |
|---|---|
| Arènes d'Entité (streaming, occlusion) | `world/` + `renderer/` |
| Télégraphie et poses d'annonce | `renderer/` (animation) |
| Règles spéciales (verrous, triche divine) | `game/` (serveur autoritatif) |
| Audio signature par Entité | `audio/` |
