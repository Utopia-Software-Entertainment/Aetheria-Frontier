# UI — Interface diégétique

> Aetheria n'a pas de HUD : l'interface vit **dans le monde** (diégétique). Ce document définit comment l'information et les interactions existent sans jamais casser l'immersion. Complète `CONTROLS.md` (canaux) et `AUDIO.md` (feedback sonore).

> **Statut** : Validé v0.1 · **Version** : 0.1 · **MAJ** : 2026-08-11 · **Owner** : UX · **Dépend de** : CONTROLS.md, AUDIO.md

## 1. Principes

1. **Tout est diégétique** — inventaire, carte, journal : des objets du monde, pas des panneaux.
2. **Le son est la moitié du HUD** — l'état (santé, recharge, menace) se lit aux oreilles.
3. **L'attention est une ressource** — une seule information dominante à la fois.
4. **Aucun élément flottant** — pas de jauge, pas de marqueur, pas d'icône hors-monde.

## 2. Inventaire : le Sac

- **Représentation physique** : un sac à dos virtuel, ouvert devant soi (regard + voix).
- **Navigation** : regard sur un objet → la voix le nomme (« couteau de marais ») → « Aetheria, prendre ».
- **Objets** : rendus en 3D réels (taille, matériau, usure visibles) — pas d'icônes plates.
- **Limite** : poids réel (influence la marche, la frappe) — pas d'inventaire infini.
- **Tri** : par voix (« trier par matériau »), par geste (jeter par-dessus l'épaule).

## 3. Carte : le Parchemin

- **Carte partielle** : se dessine au fur et à mesure de l'exploration (traits, encres).
- **Les cartes se vendent et s'achètent** (voir `ECONOMY.md`) — la carte complète n'existe pas.
- **Utilisation** : déplié devant soi (regard), plié en main.
- **Pas de position GPS** : le joueur se situe par les repères du monde (le son, la lumière, les PNJ).
- **Notes** : le joueur y dicte ses annotations (« Aetheria, note sur la carte : grotte cachée derrière la cascade »).

## 4. Journal : le Carnet

- **Minimal par principe** : pas de liste de quêtes automatique.
- **Notes dictées** : le joueur écrit ses propres notes vocales (anti-spoiler, anti-télégraphie).
- **Mémoire du monde** : les PNJ peuvent rappeler des événements (« tu m'avais promis… ») — le carnet reste personnel.
- **Croquis** : le carnet peut contenir des croquis (regard + geste) pour les indices visuels.

## 5. Menus vocaux

- **Mot-clé universel** : « Aetheria » + commande.
- Menus : « Aetheria, sac », « Aetheria, carte », « Aetheria, carnet », « Aetheria, amis », « Aetheria, réglages ».
- **Confirmation par son** : un « clic » neutre confirme ; un « gloussement » signale l'échec.
- **Menus contextuels** : « Aetheria, que voit-il ? » → le monde répond (identification d'un objet/PNJ par la voix).
- **Toujours annulable** : « Aetheria, retour ».

## 6. Information d'état (le HUD invisible)

| État | Canal dominant | Comment |
|---|---|---|
| **Santé** | Son + haptique | Souffle, battement, dégradation sonore des impacts |
| **Focus (EEG)** | Haptique léger | Vibration continue = flux stable |
| **Recharge de sort** | Son | La lame gravée « chante » quand chargée |
| **Menace directionnelle** | Audio spatial | D'où vient le danger (voir `AUDIO.md`) |
| **Ressources** | Monde | Les stocks se voient (sac, atelier) |
| **Réputation** | PNJ | La façon dont on est traité |

- **Pas de jauge chiffrée** : l'approximation est voulue — elle crée le doute et le mystère.

## 7. Interactions avec le monde

- **Identification** : regarder + voix (« qu'est-ce que c'est ? ») → le monde nomme (jamais de tag).
- **Inventaire du monde** : les objets posés sont réels (une épée plantée reste une épée).
- **PNJ** : dialogue engagé par le regard, poursuivi par la voix.
- **Notifications** : uniquement audio/haptique (rumeurs, événements) — jamais de popup.

## 8. Contrat d'implémentation (rappel moteur)

| Besoin | Module moteur |
|---|---|
| Rendu 3D des interfaces (sac, carte, carnet) | `renderer/` (pas de UI 2D) |
| Reconnaissance vocale des commandes | `voice/` (Whisper) |
| Synthèse des confirmations | `audio/` (FMOD) |
| État d'interface partagé serveur (inventaire) | `network/` (autorité) |
