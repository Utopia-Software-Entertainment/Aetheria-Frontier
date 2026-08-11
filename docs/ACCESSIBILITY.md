# ACCESSIBILITY — Accessibilité

> Aetheria doit être jouable par le plus grand nombre, sans trahir la promesse « sans manette ». Ce document **consolide** les réglages éparpillés (CONTROLS, AUDIO, UI, ONBOARDING) en une référence unique.

> **Statut** : Brouillon · **Version** : 0.1 · **MAJ** : 2026-08-11 · **Owner** : UX · **Dépend de** : CONTROLS.md, AUDIO.md, UI.md

## 1. Philosophie

1. **L'accessibilité est un réglage, pas un mode** — chaque option s'ajuste indépendamment.
2. **La promesse tient** — les canaux alternatifs remplacent le canal principal, ils ne le « cassent » pas.
3. **Aucune gêne médicale ignorée** — photosensibilité, vertige, fatigue, troubles de la voix.

## 2. Registre des options

### 2.1 Vision
| Option | Défaut | Plage |
|---|---|---|
| **Réduction du mouvement** | Off | Légère → Totale (flous de mouvement, secousses) |
| **Réduction du contraste** | Off | Léger → Fort (photosensibilité) |
| **Lueurs et flashes** | Standard | Réduits → Aucun |
| **Taille des sous-titres** | Moyenne | Petite → Très grande |
| **Position des sous-titres** | Bas | Bas → Haut |
| **Sous-titres avec fond** | Oui | On/Off |

### 2.2 Audition
| Option | Défaut | Détail |
|---|---|---|
| **Sous-titres vocaux** | On | Toutes les paroles transcrites (voir `UI.md`) |
| **Indicateurs visuels alternatifs** | On | Lueurs/vibrations pour les indices sonores critiques (voir `AUDIO.md` §6) |
| **Compression audio** | Off | Réduit les écarts forts/doux |
| **Mode mono** | Off | Fusion des canaux (perte auditive unilatérale) |

### 2.3 Voix (reconnaissance)
| Option | Détail |
|---|---|
| **Rythme de parole** | Vitesse de transcription réglable |
| **Tolérance élargie** | Mode « commandes simples » (dysarthrie, voix faible) |
| **Langue du mot-clé** | Le mot-clé se dit dans la langue du joueur |
| **Délai de confirmation** | Allonger la fenêtre avant action |

### 2.4 Corps et capteurs
| Option | Détail |
|---|---|
| **Seuils EMG/EEG** | Sensibilité réglable jusqu'à désactivation d'un canal |
| **Amplitude de frappe** | Réduire la distance de mouvement requise |
| **Temps de verrouillage du regard** | Lent (fatigue) → Rapide |
| **Saisie par maintien** | Remplacer les gestes par des commandes vocales |
| **Mode assis/allongé** | Profils séparés (voir `CONTROLS.md` §4) |

### 2.5 Cognitif
| Option | Détail |
|---|---|
| **Rappels contextuels** | Les PNJ rappellent les engagements (« tu m'avais promis… ») |
| **Guide vocal du monde** | Décrire l'environnement à la demande (« Aetheria, décris ») |
| **Rythme du tutoriel** | Ralentir ou accélérer (voir `ONBOARDING.md`) |
| **Journal guidé** | Notes suggérées (au lieu de la dictée libre) |

## 3. Dégradation gracieuse (si un canal échoue)

| Canal défaillant | Repli |
|---|---|
| **Regard** | Sélection par micro-stick + voix |
| **Voix** | Gestes + micro-sticks (toutes les commandes ont un équivalent gestuel) |
| **EEG/EMG** | Désactivation ; le focus devient passif (aucun gameplay bloqué) |
| **Corps (frappe)** | Commandes vocales de combat (« Aetheria, frappe forte ») |
| **Haptique** | Retour visuel/audio équivalent |

## 4. Confort VR

- **Fovéation obligatoire** : réduction du risque de vertige (voir `ART.md` §6).
- **Vignettage dynamique** : en option, pendant les mouvements rapides.
- **Pause sensorielle** : le joueur peut « fermer les yeux » (fondu audio) à tout moment.
- **Mesures de temps** : rappels de repos (voir `CONTROLS.md` §4 — fatigue allongé).

## 5. Tests d'accessibilité (process)

- **Audit au playtest** : chaque playtest inclut un pass accessibilité (voir `BALANCE.md` §8).
- **Personas de test** : 5 profils (photo-sensible, malentendant, dysarthrie, moteur limité, novice VR).
- **Rapport public** : les options accessibles sont documentées pour les joueurs.

## 6. Contrat d'implémentation (rappel moteur)

| Besoin | Module moteur |
|---|---|
| Options persistantes par profil joueur | `core/` (config) |
| Rendu adapté (contraste, vignette, fovéation) | `renderer/` |
| Sous-titres et transparences audio | `audio/` |
| Équivalents gestuels des commandes vocales | `input/` + `voice/` |
