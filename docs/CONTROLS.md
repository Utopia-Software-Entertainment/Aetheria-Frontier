# CONTROLS — Commandes sans manette

> Le cœur de la promesse Aetheria : **aucune manette**. Toutes les commandes passent par le corps, le regard, la voix et l'esprit. Ce document définit le mapping de chaque canal, le mode allongé et les courbes d'accessibilité.

## 1. Principes

1. **Chaque canal a un rôle naturel** — le regard cible, la voix commande, le corps frappe, l'attention module.
2. **Pas de conflit de canaux** — une action n'est jamais assignée à deux canaux simultanés par défaut.
3. **Tout est calibré** — chaque joueur a son propre profil (taille, voix, regard) ; calibration initiale obligatoire.
4. **Accessibilité par défaut** — réglages fins disponibles pour chaque canal (voir §6).
5. **Le retour est physique** — haptique, son spatial, souffle : on *ressent* la commande, on ne la lit pas.

## 2. Canaux d'entrée

| Canal | Matériel | Rôle principal | Rôle secondaire |
|---|---|---|---|
| **Regard** | Eye-tracking (PSVR2, Somnium) | Ciblage, sélection, points vitaux | Navigation de menus, lecture (tête/yeux) |
| **Voix** | Micro casque + Whisper | Commandes, sorts vocaux, dialogue PNJ | Menus vocaux, dictée, macros vocales |
| **Cerveau (EEG)** | OpenBCI | « État de flux » : focus, concentration | Détection de détente, régénération |
| **Muscles (EMG)** | OpenBCI | Contraction → actions déclenchées | Tenue, charge, blocage |
| **Micro-sticks** | Sticks gyroscopiques | Déplacement grossier, orientation | Mouvement continu doux |
| **Corps** | Tracking optique / inertiel | Frappes, esquives, élans | Gestes de dialogue, interaction |

## 3. Mapping détaillé

### 3.1 Ciblage (regard)
- **Regard fixe (0,4 s)** → sélectionner la cible.
- **Regard + maintien** → verrouillage de cible.
- **Points vitaux** : la zone regardée devient la zone visée — toucher l'œil d'un golem ≠ toucher son genou.
- **Dé-clic** : détourner le regard 1,5 s décroche la cible (pas de verrou « collant »).

### 3.2 Commandes vocales (Whisper)
- **Préfixe universel** : « Aetheria » (ou mot-clé personnel) + commande — évite les faux positifs.
- Exemples : « Aetheria, tirer », « Aetheria, grandir » (armes cristal), « Aetheria, sort de feu ».
- **Menus vocaux** : « Aetheria, inventaire », « Aetheria, carte », « Aetheria, quitter ».
- **Dialogue PNJ** : la parole du joueur est transcrite et interprétée (voir `NPC.md`).
- **Macros vocales personnalisées** : enregistrées en calibration.
- Whisper tourne en local (embarqué) : aucune donnée vocale ne quitte la machine.

### 3.3 État de flux (EEG)
- **Focus** (concentration soutenue) : débloque les **critiques** et réduit le recul.
- **Détente** : régénération accélérée, respiration contrôlée.
- **Surcharge** (attention épuisée) : le jeu impose un temps de repos — anti-grind, bien-être.
- L'EEG **ne contrôle jamais** une action directe : il module, il ne déclenche pas.

### 3.4 Contractions (EMG)
- **Contraction brève** → action assignée (blocage, esquive).
- **Contraction soutenue** → charge, tenue, port d'objet.
- Chaque action EMG est calibrée par muscle (mâchoire, sourcils, main) et par seuil.

### 3.5 Micro-sticks
- **Déplacement continu** : direction + vitesse (plus on pousse, plus on va vite).
- **Rotation** : tête virtuelle si tracking limité.
- **Mode assis vs allongé** : profils de stick séparés.

### 3.6 Corps (frappes)
- **Frappe** : mouvement réel (bras, poing) → détection d'élan → application physique (voir `COMBAT.md`).
- **Esquive** : déplacement réel du buste/tête hors de la trajectoire.
- **Interaction** : geste d'ouverture (main tendue, poignée).

## 4. Mode allongé (recumbent)

- **Rotation du monde à 90°** : le plan du jeu devient vertical devant les yeux — le joueur regarde « droit devant ».
- **Axe du regard** : le regard vers le haut = « avant » du monde ; les micro-sticks gèrent le strafe.
- **Frappes** : bras levés devant soi (espace réduit), amplitudes calibrées plus courtes.
- **Voice-first** : le mode allongé privilégie la voix et le regard pour toutes les actions lentes.
- **Fatigue** : le jeu surveille la position et rappelle le repos.

## 5. Profils et calibration

1. **Calibration du regard** (points de suivi, zone de confort).
2. **Calibration vocale** (mot-clé, sensibilité, langue).
3. **Calibration EEG/EMG** (baseline de repos, seuils de focus, muscles).
4. **Profil de mouvement** (amplitude, vitesse, mode allongé ou assis).
5. Profils stockés côté joueur, chargés au démarrage.

## 6. Accessibilité

- **Sous-titres vocaux** : toutes les commandes et dialogues transcrits.
- **Rythme de parole** : vitesse de transcription réglable.
- **Seuils EMG/EEG** : sensibilité réglable (jusqu'à désactivation).
- **Temps de verrouillage** : réglable (regard lent vs rapide).
- **Dysarthrie / voix faible** : mode « commandes simples », tolérance élargie.
- **Photosensibilité** : réduction du contraste et du mouvement en option.

## 7. Contrat d'implémentation (moteur)

| Besoin | Module moteur |
|---|---|
| Suivi du regard (fréquence ≥ 60 Hz, latence < 40 ms) | `vr/` (OpenXR eye-tracking) |
| Transcription vocale locale | `voice/` (Whisper.cpp) |
| Acquisition EEG/EMG (stream continu) | `neural/` (LibLSL, OpenBCI) |
| Tracking corps/micro-sticks | `vr/` + `input/` |
| Haptique et retour audio | `audio/` (FMOD) |
| Calibration + profils | `core/` (config) |
