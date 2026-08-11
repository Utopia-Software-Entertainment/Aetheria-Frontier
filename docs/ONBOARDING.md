# ONBOARDING — Entrée dans Aetheria

> Apprendre à jouer **sans HUD et sans manette** est le défi n°1 d'Aetheria. Ce document définit le parcours d'entrée : calibration, zone tutoriel, apprentissage des canaux. Complète `CONTROLS.md` (mapping) et `ACCESSIBILITY.md` (réglages).

## 1. Principes

1. **L'apprentissage est une aventure** — le tutoriel est intégré au monde (Priméa), jamais un menu.
2. **Une compétence à la fois** — chaque canal est introduit seul, puis combiné.
3. **L'échec est bienveillant** — dans la zone de départ, pas de pénalité de mort (voir `DEATH.md`).
4. **La calibration précède tout** — on ne joue pas avant d'être « branché ».
5. **Zéro jargon hors-monde** — les consignes sont dites par les PNJ, dans la langue du monde.

## 2. Phase 0 — Calibration (première connexion)

| Canal | Calibration | Durée cible |
|---|---|---|
| **Regard** | Points de suivi, zone de confort, sensibilité | 2 min |
| **Voix** | Mot-clé personnel (« Aetheria » ou autre), langue, sensibilité | 3 min |
| **EEG/EMG** | Baseline de repos, seuils de focus, muscles (mâchoire, sourcils, main) | 4 min |
| **Micro-sticks** | Profil d'amplitude, mode assis/allongé | 2 min |
| **Corps** | Amplitude de frappe, hauteur, mode allongé (rotation 90°) | 3 min |

- Résultat : un **profil de joueur** stocké localement (et côté compte), rechargeable.
- En cas d'échec de calibration d'un canal : bascule automatique sur les canaux restants (voir `ACCESSIBILITY.md`).

## 3. Phase 1 — Le réveil (Priméa)

Le joueur « se réveille » dans le monde sans explication d'écran :

1. **Regard** : un PNJ (le vieux garde) se présente ; le joueur doit le regarder pour « engager » le dialogue.
2. **Voix** : le garde demande une réponse (« dis-moi ton nom ») — première commande vocale.
3. **Mouvement** : micro-sticks pour marcher vers la place.
4. **Frappe** : un mannequin d'entraînement — la première frappe à élan est expliquée par le garde (« frappe avec le corps, pas avec le doigt »).
5. **EEG/EMG** : l'état de flux est introduit comme « calme ton esprit » devant un feu.

## 4. Phase 2 — Premiers combats

- **Monstres de niveau 1** (ronces, jeunes Vorpaux) avec **points vitaux visuellement clairs** (lueur, taille).
- Apprentissage du **critique parfait** : timing (fenêtre 120 ms) montré par le son (voir `AUDIO.md`).
- Introduction de la **garde directionnelle** (bouclier qui suit le regard).
- Première **commande de sort** vocale sur une arme gravée de base.
- **Mort bienveillante** : retour au sanctuaire de Priméa, aucune perte, explication des règles de mort (voir `DEATH.md`).

## 5. Phase 3 — Le monde s'ouvre

- Quête d'introduction (voir `QUESTS.md`) : aider le forgeron de Secondil → première découverte d'objets uniques.
- **Journal minimal** : le joueur dicte ses notes (« Aetheria, note : la dame cherche son frère »).
- **Carte partielle** : s'ouvre en explorant (voir `UI.md`).
- **Premier PNJ à vie propre** : suivre le forgeron qui quitte la ville — introduction à l'autonomie des PNJ.

## 6. Zone tutoriel : le Pont de Priméa

| Élément | Compétence |
|---|---|
| Mannequins | Frappes, élans, critiques |
| Cibles mobiles | Ciblage au regard, verrouillage |
| Mur de torches | Commande vocale (allumer/éteindre) |
| Pont suspendu | Équilibre, micro-sticks, profondeur |
| La Vieille Écho | Dialogue : comprendre une PNJ autonome (elle raconte une histoire qui change) |

- La zone est **réutilisable** : elle sert de terrain d'entraînement permanent (retour possible à tout moment).

## 7. Mesures de réussite (onboarding)

- **Temps jusqu'à la première commande vocale réussie** : < 3 min.
- **Temps jusqu'au premier combat complet** : < 10 min.
- **Abandon à la calibration** : < 5 % (sinon → simplifier la calibration).
- **Retour volontaire dans la zone tutoriel** : signe de confort, pas d'échec.

## 8. Contrat d'implémentation (rappel moteur)

| Besoin | Module moteur |
|---|---|
| Calibration multi-capteurs + profils | `core/` (config) + `input/` |
| Tutoriel scripté dans le monde | `game/` (scénarios) |
| Feedback d'apprentissage (audio/haptique) | `audio/` + `vr/` |
| Télémétrie d'onboarding | `network/` (stats serveur, anonymisées) |
