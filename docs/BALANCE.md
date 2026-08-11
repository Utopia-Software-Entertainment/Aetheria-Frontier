# BALANCE — Bible d'équilibrage

> Les valeurs de design d'Aetheria, centralisées. **Aucune valeur n'est définitive** : tout est calibré en playtest (voir §8). Ce document est la référence commune entre design et implémentation.

> **Statut** : Brouillon · **Version** : 0.1 · **MAJ** : 2026-08-11 · **Owner** : Équilibrage · **Dépend de** : SYSTEMS.md, COMBAT.md, ECONOMY.md

## 1. Statistiques de personnage

| Stat | Rôle | Source |
|---|---|---|
| **STR** | Dégâts physiques | Niveau, équipement |
| **DEX** | Précision, vitesse d'armes | Niveau, équipement |
| **AGI** | Esquive, mouvement | Niveau, équipement |
| **TEC** | Gravure, sorts, artisanat | Niveau, équipement |
| **VIT** | Vitalité, seuils d'équipement | Équipement surtout |

- **Seuil d'exemple** : armes à commande vocale exigeant VIT 400+ (voir `SYSTEMS.md`).
- **Dégâts** = (stat × multiplicateur d'arme) × modificateurs (critique, buffs, débuffs, élément) — voir `SYSTEMS.md`.

## 2. Courbes (valeurs cibles)

| Courbe | Cible | Détail |
|---|---|---|
| **Niveau** | 1 → 70 | XP exponentielle douce ; 50 % du temps vers les niveaux 55–70 |
| **Durée de vie moyenne** | 6 mois pour le « contenu maximal » | Sans rush |
| **Dégâts d'une frappe** | 10–15 % de PV d'un monstre même niveau | Combat de 30–60 s en solo |
| **PV de base** | 100 + 15/niveau | VIT ajoute des seuils de survie, pas des PV directs |
| **Critique parfait** | ×2.5 | Fenêtre 120 ms, point vital + élan |
| **Kai (renforcement)** | +6 % par niveau | 15 niveaux max, coût explosif après 10 (voir `SYSTEMS.md`) |

## 3. Temps (valeurs cibles)

| Action | Durée |
|---|---|
| **Fenêtre de critique** | 120 ms |
| **Verrouillage du regard** | 0,4 s |
| **Dé-clic du regard** | 1,5 s |
| **Télégraphie d'attaque majeure** | 400–700 ms (voir `BESTIARY.md`) |
| **Respawn joueur** | 10 s (voir `DEATH.md`) |
| **Respawn monstre commun** | 2–5 min |
| **Respawn monstre rare** | 1–7 jours |
| **Respawn boss de zone** | 1–2 semaines |
| **Réinitialisation Ctharnide** | 7 jours (voir `BOSSES.md`) |
| **Jour/nuit** | 4 h réelles |

## 4. Économie (valeurs cibles)

| Paramètre | Valeur |
|---|---|
| **Taxe d'enchère** | 5 % |
| **Drops d'or** | Faibles ; la richesse vient du travail (voir `ECONOMY.md`) |
| **Coût de réparation** | 3 % de la valeur par 10 % de durabilité manquante |
| **Prix d'un livre rare** | Ordre de grandeur : 100 M Mahni (référence d'histoire, voir `CLANS.md`) |
| **Génération d'objets** | Un seul exemplaire mondial pour les uniques d'Entités |

## 5. PvP (valeurs cibles)

| Paramètre | Valeur |
|---|---|
| **Marque PK** | Attaque d'un non-consentant → marque 24 h (réduite par rédemption) |
| **Immunité débutant** | 10 premiers niveaux (voir `PVP.md`) |
| **Perte PK à la mort** | +50 % vs pénalité normale (voir `DEATH.md`) |
| **Fenêtre de résurrection d'allié** | 60 s |

## 6. Grille de groupe

| Taille | Contenu | Niveau conseillé |
|---|---|---|
| 1–2 | Exploration, quêtes de tranche de vie | Tous |
| 2–4 | Donjons courts, escouade | +0–5 du donjon |
| 5–8 | Donjons complets, événements | +5 |
| 9–16 | Raids, sièges | +10 (avec préparation) |
| 16–32 | Entités, guerres de guilde | Scénarios EX requis pour les Entités |

## 7. Tolérances techniques (contrat de qualité)

| Paramètre | Cible | Pire acceptable |
|---|---|---|
| **Fréquence physique** | 120 Hz fixe | 90 Hz |
| **Motion-to-photon** | < 20 ms | < 25 ms |
| **FPS natif** | 90 fps | 72 fps + reprojection |
| **Latence du regard** | < 40 ms | < 60 ms |
| **Latence de transcription vocale** | < 200 ms | < 400 ms |
| **CCU v0** | 500 | 300 (shard) |

## 8. Processus d'équilibrage

1. **Playtests réguliers** : chaque playtest mesure 3 indicateurs (temps de combat, % de morts, satisfaction).
2. **Pass accessibilité** : chaque playtest inclut l'audit (voir `ACCESSIBILITY.md` §5).
3. **Une variable à la fois** : les changements de balance sont isolés et datés.
4. **Journal de balance** : ce document est versionné ; chaque entrée modifiée est datée.
5. **Données anonymisées** : télémétrie serveur (dégâts réels, durées) comparée aux cibles.

## 9. Décisions de balance ouvertes (à trancher en playtest)

- Courbe exacte de l'élan → multiplicateur (plafond pour éviter les lésions réelles).
- Impact réel du poids d'inventaire sur la frappe.
- Seuil exact de VIT pour les armes vocales.
- Durée des arcs narratifs (voir `NARRATIVE.md`).
- Valeur exacte de la taxe d'enchère vs volume de transactions.
