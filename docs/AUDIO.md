# AUDIO — Design audio

> L'audio est **le** canal d'information d'Aetheria : sans HUD, le monde se lit par les oreilles. L'audio porte aussi la voix des PNJ et la compréhension vocale du joueur.

## 1. Principes

1. **L'audio est le HUD** — direction des menaces, santé, recharge : tout passe par le son spatial.
2. **Chaque chose a une voix** — chaque créature, matériau, sort a une signature sonore reconnaissable en 50 ms.
3. **La voix est du contenu** — les PNJ parlent ; le joueur parle ; Whisper écoute (local, jamais de streaming).
4. **Le silence est un design** — les moments sans musique portent le mystère.

## 2. Spatialisation

- **Audio positionnel 3D** complet (HRTF + distance + occlusion) : une menace approche, elle se déplace derrière le joueur, le son le dit.
- **Indices de direction** : la menace à 2 h se distingue de celle à 10 h sans virage de tête.
- **Occlusion matérielle** : un mur épais étouffe ; une porte entrouverte laisse filtrer.
- **Zéro jauge** : la santé se lit au souffle, au battement, aux dégâts entendus.

## 3. Signature sonore

| Élément | Principe | Exemple |
|---|---|---|
| **Créatures** | Un thème par famille + variation individuelle | Le golem « sonne pierre » ; sa variante blindée « sonne fer » |
| **Armes** | Matériau + état (émoussé, affûté, gravé) | La lame gravée chante quand elle est chargée |
| **Sorts** | Élément (feu crépitant, eau profonde, terre sourde, vent sifflant) | Un sort de feu s'entend avant de se voir |
| **PNJ** | Voix uniques (timbre, débit, tic) | Le forgeron rauque, l'archiviste feutré |
| **Entités** | Prégagées, au-delà du « naturel » | Lycaon : silence qui précède le hurlement |

## 4. Voix des PNJ et du joueur

### 4.1 PNJ
- **Synthèse vocale** : timbres variés, aucun PNJ ne sonne comme un autre.
- **Dialogues contextuels** : ton variable selon la relation et l'humeur (voir `NPC.md`).
- **Langue du monde** : des mots inventés + langue du joueur — pas de babil générique.

### 4.2 Joueur
- **Reconnaissance vocale locale** (Whisper.cpp) : commandes, dictée, dialogue avec PNJ.
- **Rétroaction de commande** : une commande vocale réussie est confirmée par un « clic » sonore neutre — jamais par un texte flottant.
- **Vocalisation du personnage** : cris, effort, souffle — le corps virtuel « sonne » le mouvement réel.

## 5. Musique

- **Musique dynamique** : couches par état (exploration calme, combat, tension, Entité).
- **Thèmes par Terre** : variation d'instruments par région (luth à Cinquepont, orgue de pierre à Neuville).
- **Pas de musique pendant le dialogue** — la parole est prioritaire.
- **Entités** : thème unique et personnel, impossible à confondre.

## 6. Accessibilité auditive

- **Sous-titres vocaux** : toutes les paroles transcrites (taille et position réglables).
- **Indicateurs visuels alternatifs** : lueurs, vibrations (haptique) pour les indices sonores critiques.
- **Réduction de l'audiodynamique** : compression réglable (fatigue, sensibilité).
- **Modes de spatialisation** : stéréo large / casque / haut-parleurs.

## 7. Contrat d'implémentation (rappel moteur)

| Besoin | Module moteur |
|---|---|
| Audio spatial 3D + occlusion + HRTF | `audio/` (FMOD) |
| Synthèse vocale PNJ | `audio/` + `voice/` |
| Reconnaissance vocale locale | `voice/` (Whisper.cpp) |
| Musique dynamique (couches, transitions) | `audio/` |
| Haptique synchronisée au son | `audio/` + `vr/` |
