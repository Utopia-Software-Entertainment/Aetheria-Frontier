# BOSSDOSSIERS — Dossiers de combat complets (forces, faiblesses, IA)

> Le dossier complet de **chaque combat de boss** d'Aetheria : forces, faiblesses, résistances, compétences, comportement IA. Document de production — les joueurs n'ont accès à rien de tout cela en jeu (tout doit se **découvrir** : télégraphie, lore, observation). Complète `BOSSES.md` (règles générales) et `BOSSCONCEPTS.md` (concepts d'Entité).

> **Statut** : Brouillon · **Version** : 0.1 · **MAJ** : 2026-08-11 · **Owner** : Combat · **Dépend de** : BOSSES.md, BOSSCONCEPTS.md, BESTIARY.md, COMBAT.md, CONTROLS.md

## 0. Cadre commun

### 0.1 Champs d'un dossier

| Champ | Contenu |
|---|---|
| **Type** | Entité / Unique / Donjon / Zone / Bonus |
| **Terre** | Localisation (voir `WORLD.md`) |
| **Niveau cible** | Tranche de niveau recommandée |
| **Échelle** | 1–3 / 3–8 / 8+ / raid 16–32 |
| **Respawn** | Règle de réapparition (voir `WORLD.md` §3) |
| **Canal** | Canal de contrôle enseigné (regard, voix, inertie, EEG) |
| **Forces** | Ce pour quoi le boss est dangereux |
| **Faiblesses** | Ce que le joueur peut exploiter — toujours **lisibles** (visuel, son, comportement) |
| **Résistances / Immunités** | Éléments et dégâts inefficaces |
| **Compétences** | Actions avec leur **télégraphie** (le signal qui l'annonce) |
| **IA** | Machine à états, priorités, réactions aux canaux, anti-exploit |
| **Environnement** | L'arène et ses dangers — l'environnement est une arme |
| **Récompenses** | Loot signature (voir `LOOT.md`) |
| **Marque** | Malédiction en cas de survie/échec (voir `ACHIEVEMENTS.md`) |

### 0.2 Cadre IA commun (tous les boss)

- **Architecture** : *Utility AI* sur le serveur (`game/`, autoritatif) — chaque état a une utilité calculée (distance, menaces, cooldowns, phase) ; les comportements s'exécutent dans `ecs/`.
- **FSM de base** : `VEILLE → ENGAGE → COMBAT (phases) → RUPTURE/ENRAGE → RETRAITE` (boss de zone) ou `MORT` (uniques, Entités). Boss de zone : RETRAITE → recolonisation ailleurs (rotation d'emplacement).
- **Télégraphie obligatoire** : toute attaque majeure est annoncée par un signal de `BESTIARY.md` §3 (posture, souffle, lueur, silence) avec une fenêtre minimale annonce→impact (≥ 1,2 s pour les attaques de zone ; ≥ 700 ms pour les frappes simples). **Jamais de dégâts téléportés.**
- **Variation** : pas de rotation fixe — paramètres randomisés (délais, enchaînements, choix d'objectif) pour interdire le pattern « par cœur » (voir `COMBAT.md` §6).
- **Anti-exploit** : détection d'inputs impossibles (système), verrous de niveau, immunités de phase, marquage anti-farm. Les Entités « trichent » (métadonnées de combat).
- **Réaction aux canaux** : chaque boss est *sensible* à au moins un canal (il peut le contrer) et *vulnérable* à un autre — c'est la leçon de combat qu'il enseigne.

---

## 1. Les Sept Entités (7)

> Règles générales : `BOSSES.md`. Concepts : `BOSSCONCEPTS.md`. **Aucune faiblesse exploitable hors Scénario Unique EX.**

### 1.1 Lycaon, le Tueur de Nuits

| Champ | Détail |
|---|---|
| **Type** | Entité · **Terre** : plaines lunaires (arène nocturne) · **Niveau cible** : 60+ · **Échelle** : raid 16–32 |
| **Respawn** | Aucun · **Canal** : **regard** (il vous regarde, vous le regardez) |
| **Forces** | Vitesse surnaturelle ; crée des **doubles d'ombre** ; rompt le regard (clignement ou détour → perte du verrouillage) ; meute d'ombres de soutien |
| **Faiblesses** | La **gorge** pendant la phase *La Lune* (fenêtre de critique) ; le **vrai** Lycaon doit soutenir le regard du joueur (fixation longue) ; ses doubles se dissipent si personne ne les regarde |
| **Résistances / Immunités** | Immunisé tant que le Scénario EX n'est pas actif ; immunité aux sorts (Marque) ; esquive « au radar » inefficace — il faut le **voir** |
| **Compétences** | **Bond de meute** (posture basse + souffle) ; **Hurlement** (silence soudain → les doubles s'activent) ; **Griffe lunaire** (lueur argentée = balayage de zone) ; **Regard de plomb** (fixation → paralysie progressive) |
| **IA** | États : `La Meute` (distance, doubles, il observe) → `La Chasse` (poursuite, l'inertie du joueur compte) → `La Lune` (attaque frontale, gorge exposée en fenêtre). Priorités : maintenir le contact visuel (menace maximale = regard soutenu) ; punir les clignements ; défendre la position de lune. Anti-exploit : lecture du regard réel (eye-tracking) — le faux-verrouillage par OCR est détecté. |
| **Environnement** | Nuit permanente ; la lune est la source de lumière — les ombres allongent les doubles ; terrain dégagé (aucune cache) |
| **Récompenses** | Matériaux de lune, trophée « Le Tueur de Nuits », réputation mondiale |
| **Marque** | **Marque de Lycaon** (voir `BOSSES.md`) — restrictions d'équipement, PNJ méfiants, immunité aux sorts |

### 1.2 Vésémon, le Gardien des Tombes *(détruite — documentée)*

| Champ | Détail |
|---|---|
| **Type** | Entité (**1re vaincue**) · **Terre** : nécropole des Divins · **Niveau cible** : verrou **50** · **Échelle** : 3–8 |
| **Respawn** | Aucun (scénario consommé pour le serveur) · **Canal** : **inertie + discipline** |
| **Forces** | Armure robotique de l'Ère des Divins ; **verrou de niveau 50** (les stats supérieures sont neutralisées) ; compteur de « colère » qui ignore les gardes parfaites ; tombes actives |
| **Faiblesses** | Phases de **Deuil** : il s'arrête et se souvient — **ne pas attaquer** (la non-action est la victoire) ; traits lumineux géométriques annonçant chaque attaque majeure |
| **Résistances / Immunités** | Immunisé au burst (tout dégât pendant le Deuil nourrit la colère) ; parades parfaites ignorées au-delà du compteur |
| **Compétences** | **Lame de deuil** (trait lumineux vertical) ; **Éveil des tombes** (le sol s'ouvre — réverbération sonore) ; **Murmure du gardien** (grondement grave = attaque de zone) |
| **IA** | États : `Le Veilleur` (défense mécanique, patterns prévisibles — apprentissage) → `Le Gardien` (verrou actif, tombes, esquives requises) → `Le Deuil` (vulnérabilité par non-action ; la colère monte si les joueurs frappent). Priorités : punir le spam (dégradation des enchaînements), récompenser la discipline. Anti-exploit : les attaques enregistrent la fréquence des frappes (anti-macro). |
| **Environnement** | Nécropole : sol meuble (tombes qui s'ouvrent), stèles comme obstacles esquivables |
| **Récompenses** | Accès à l'**Inventaire** (dimension d'armes des Divins), réputation mondiale |
| **Marque** | Aucune connue — la victoire collective a effacé la Marque par rédemption |

### 1.3 Ctharnide de l'Abîme

| Champ | Détail |
|---|---|
| **Type** | Entité (**réinitialisable**) · **Terre** : abîme scellé de la Grande Bleue · **Niveau cible** : 55+ · **Échelle** : raid 16–32 |
| **Respawn** | Oui — chaque victoire fait évoluer l'histoire mondiale (sceau) · **Canal** : **voix + regard** |
| **Forces** | Monde **renversé** (océan au-dessus) ; tentacules multi-zones ; l'océan **étouffe les commandes vocales** (mufflé) ; corruption |
| **Faiblesses** | Les tentacules **télégraphient dans l'eau** (réverbération sonore, `AUDIO.md`) ; le sceau le canalise (structure vulnérable) ; phases où la gravité revient brièvement à la normale |
| **Résistances / Immunités** | Immunisé aux dégâts quand le monde est renversé sauf pendant les fenêtres de sceau ; résistant à l'eau |
| **Compétences** | **Étreinte de l'abîme** (réverbération croissante = tentacule imminent) ; **Inversion** (gravité inversée — s'orienter par la voix et le regard) ; **Chant de la Bleue** (silence soudain → corruption de zone) |
| **IA** | États : `Le Sceau` (tentacules en défense, apprendre la lecture sonore) → `L'Abîme` (gravité inversée, combats « tête en bas ») → `Le Silence` (voix compromises, recours au geste et au regard). Priorités : désorienter (inversions fréquentes), isoler les vocaux, protéger le sceau. Anti-exploit : la réinitialisation est *coûteuse* pour les joueurs (Marque à chaque échec). |
| **Environnement** | Océan inversé ; colonnes du sceau comme repères de gravité ; eau corruptrice |
| **Récompenses** | Matériau **eau** (habitat de la Trinité), reliques du sceau, évolution de l'histoire mondiale |
| **Marque** | **Marque de la Bleue** (si touché par la corruption) |

### 1.4 Siegwurm, le Maître des Cieux

| Champ | Détail |
|---|---|
| **Type** | Entité · **Terre** : stratosphère, plateformes volantes · **Niveau cible** : 60+ · **Échelle** : raid 16–32 |
| **Respawn** | Aucun · **Canal** : **regard** (ciblage des parties) + voix (contrée) |
| **Forces** | **Hors de portée la moitié du temps** (vol) ; tempêtes qui étouffent les commandes vocales ; écailles anciennes résistantes (habitat d'Aurora Kamuy) ; harcèlement aérien |
| **Faiblesses** | Points vitaux **visibles au regard** pendant le vol stationnaire : yeux, gorge, noyau ; **gorge exposée** pendant la descente en piqué ; les plateformes créent des angles morts où il doit reprendre de l'altitude |
| **Résistances / Immunités** | Immunisé aux dégâts de mêlée au sol ; très résistant au feu ; le vent réduit les dégâts de projectiles |
| **Compétences** | **Piqué foudroyant** (sifflement du vent + descente — fenêtre de gorge) ; **Tempête de griffes** (grondement grave, balayage de plateforme) ; **Rugissement** (lueur dorée dans la gorge = souffle de zone) ; **Chasse des cieux** (disparaît du champ, réapparaît dans un angle mort) |
| **IA** | États : `Le Cercle` (reconnaissance — test de lecture des parties) → `La Tempête` (harcèlement, vent qui étouffe la voix) → `La Descente` (piqués frénétiques sous 25 %, fenêtres de gorge plus larges mais plus dangereuses). Priorités : garder la distance, punir le vocal pendant la Tempête, défendre ses parties quand le regard les fixe. Anti-exploit : le ciblage de partie exige un regard **soutenu** (anti-tap). |
| **Environnement** | Plateformes volantes instables, courant d'air (chutes), stratus comme cache |
| **Récompenses** | Matériau **vent** rare, plume du maître, trophée « Le Maître des Cieux » |
| **Marque** | **Marque de Siegwurm** — vertige persistant : la visée au regard est floue en périphérie jusqu'à levée |

### 1.5 Orchestre de l'Écho Funèbre

| Champ | Détail |
|---|---|
| **Type** | Entité · **Terre** : salle de concert des Divins · **Niveau cible** : 60+ · **Échelle** : raid 16–32 |
| **Respawn** | Aucun · **Canal** : **audio** (voir `ACCESSIBILITY.md` — jamais son exclusif : chaque indice sonore a un double visuel/vibratoire) |
| **Forces** | Attaques **rythmées par la musique** (difficiles à lire pour l'œil) ; instruments animés (adds) ; la partition complexifie au fil du combat |
| **Faiblesses** | **Le silence** : quand la musique s'arrête, l'Orchestre est vulnérable — briser un instrument réduit la partition ; les joueurs peuvent **casser la mesure** (interrompre un instrument au bon moment = fenêtre) |
| **Résistances / Immunités** | Immunisé pendant les mouvements *fortissimo* ; résistant aux dégâts continus (la musique « absorbe ») |
| **Compétences** | **Crescendo** (le volume monte = attaque de zone imminente — doublé d'une lueur) ; **Fugue** (les instruments se déplacent — réverbération localisée) ; **Requiem** (silence soudain → les instruments explosent) ; **Baton du chef** (geste du chef = onde de choc) |
| **IA** | États : `Ouverture` (partition simple, apprendre la lecture) → `Fugue` (instruments animés, mouvements parallèles) → `Finale` (tout le registre, cassures de mesure). Priorités : maintenir la cohésion de l'orchestre (les instruments se réparent), punir les attaques hors tempo (contre-temps), cibler les joueurs qui cassent la partition. Anti-exploit : le rythme est *server-side* (pas de prédiction audio). |
| **Environnement** | Salle de concert : gradins (cache), instruments géants destructibles, réverbération modifiée par les débris |
| **Récompenses** | Partitions des Divins (gravures sonores), relique « Clé de la dernière note » |
| **Marque** | **Marque de l'Écho** — le rythme du monde se perçoit décalé : les fenêtres de timing des critiques sont décalées jusqu'à levée |

### 1.6 Goldhuneenay, l'Inépuisable

| Champ | Détail |
|---|---|
| **Type** | Entité · **Terre** : champ de bataille doré · **Niveau cible** : 60+ · **Échelle** : raid 16–32 |
| **Respawn** | Aucun · **Canal** : **inertie / endurance** |
| **Forces** | Bras multiples (frappes en rafale) ; **régénère par le combat** (chaque dégât reçu nourrit son corps doré) ; le DPS pur la renforce |
| **Faiblesses** | **S'épuise elle-même** : les esquives prolongées (mouvement réel, `COMBAT.md` §1.2) vident sa réserve ; **articulations des bras** (points vitaux) exposées pendant les rafales ; après chaque cycle complet de bras, une fenêtre d'épuisement s'ouvre |
| **Résistances / Immunités** | Immunisée aux dégâts quand elle est « saturée » (réserve pleine) ; très résistante au feu |
| **Compétences** | **Cercle des Bras** (chaque bras frappe en séquence — posture basse + souffle avant le cycle) ; **Régénération dorée** (lueur ambre = absorption) ; **Frappe du champ** (le sol doré s'illumine = explosion différée) ; **Épuisement** (état de vulnérabilité — les bras retombent) |
| **IA** | États : `Contemplation` (régénère, attire le groupe — le DPS l'alimente) → `Cercle des Bras` (rafales cycliques, punit les attaquants statiques) → `Épuisement` (fenêtre ouverte après N esquives). Priorités : punir le DPS sans mouvement, récompenser l'endurance réelle, cibler les joueurs immobiles. Anti-exploit : la détection d'élan (tracking) est server-side. |
| **Environnement** | Champ doré : le sol réagit aux pas (zones de charge), piliers de trophées (caches) |
| **Récompenses** | Or des Divins, « Amulette de l'Inépuisable » |
| **Marque** | **Marque de l'Inépuisable** — la fatigue s'accumule plus vite (l'endurance réelle est comptée plus sévèrement) jusqu'à levée |

### 1.7 La Septième *(SECRET — contenu interne, jamais diffusé en jeu)*

| Champ | Détail |
|---|---|
| **Type** | Entité finale · **Terre** : la Septième (Terre Effacée — lien à définir) · **Niveau cible** : 70+ · **Échelle** : raid 16–32 |
| **Respawn** | Aucun · **Canal** : **tous** (elle contredit chaque leçon des six premières) |
| **Forces** | **Miroir** : elle copie en temps réel les compétences et patterns du groupe (elle lit les métadonnées de combat, comme les Entités « trichent » — elle triche *mieux*) ; aucune forme fixe ; les factions de chercheurs ne l'ont jamais identifiée |
| **Faiblesses** | Elle **imite, elle n'invente pas** : un mouvement improvisé (jamais répété par le groupe) la désynchronise ; ses copies sont **légèrement décalées** (télégraphie toujours honnête, contrairement aux originaux) ; le groupe qui change radicalement de rythme brise son modèle |
| **Résistances / Immunités** | Immunisée aux stratégies déjà utilisées contre les six autres Entités (elle les connaît toutes) ; immunités de phase non documentées |
| **Compétences** | **Copie** (reprend la dernière compétence majeure du groupe) ; **Reflet** (double du joueur le plus dangereux) ; **Effacement** (silence soudain → disparition de zones de l'arène) ; **Contradiction** (elle annule la règle d'une Entité vaincue — ex. inverse le verrou de Vésémon) |
| **IA** | États : `Apprentissage` (observe, teste — aucun dégât direct) → `Miroir` (rejoue les patterns copiés avec un léger décalage) → `Imparfaite` (désynchronisation quand le groupe improvise — fenêtre finale). Priorités : imiter, anticiper, punir la répétition. Anti-exploit : lecture des métadonnées de combat du serveur (fréquence, timing, choix) — les macros et rotations figées sont ses munitions. |
| **Environnement** | Arène de la Terre Effacée : géométrie instable (morceaux du monde qui s'effacent et reviennent) |
| **Récompenses** | Le secret de la Terre Effacée, relique ultime, fin de l'arc des Sept |
| **Marque** | **Marque du Miroir** — les PNJ ne reconnaissent plus le marqué (identité brouillée) tant qu'elle n'est pas levée |

---

## 2. Monstres uniques (5)

> Non-respawnables (`WORLD.md` §3). Supérieurs aux boss de zone, inférieurs aux Entités.

### 2.1 Jinryong, le Dragon Véritable

| Champ | Détail |
|---|---|
| **Type** | Unique · **Terre** : Onzécime (accès secret) · **Niveau cible** : 65+ · **Échelle** : 8+ |
| **Forces** | Sommet de la hiérarchie draconique ; écailles anciennes (résistances visibles) ; feu de l'Ère des Divins ; intelligence (il **juge** le groupe avant de se battre) |
| **Faiblesses** | **Cœur de l'Ère des Divins** : unique point vital, exposé uniquement quand il accepte le duel ; il **ne ment jamais** — ses télégraphies sont toujours exactes (les honnêtes le respectent, l'utiliser) ; trois épreuves préliminaires affaiblissent ses écailles |
| **Résistances / Immunités** | Très résistant à tout ; immunisé au burst tant que le cœur est scellé |
| **Compétences** | **Souffle des Divins** (lueur blanche dans la gorge = cône) ; **Ruée du jugement** (posture basse + souffle — charge à travers le groupe) ; **Ailes du crépuscule** (battement = onde de zone) ; **Test de la harde** (invocation de draconiques subordonnés) |
| **IA** | États : `Jugement` (trois épreuves : regard, inertie, endurance — échec = combat plus dur) → `Le Duel` (le cœur s'ouvre, il se bat frontalement) → `La Colère du Véritable` (sous 25 %, les annonces restent honnêtes mais les fenêtres raccourcissent). Priorités : tester, punir la lâcheté (fuite = enrage), honorer la justesse. Anti-exploit : verrou de niveau et annonces exactes (aucune triche — c'est son honneur). |
| **Environnement** | Sanctuaire d'Onzécime : pilier central (cache), sol volcanique par zones |
| **Récompenses** | **Cœur de dragon** (matériau ultime de forge), écailles anciennes, titre « Le Véritable » |
| **Marque** | Aucune (il ne marque pas — il juge) |

### 2.2 Aurora Kamuy

| Champ | Détail |
|---|---|
| **Type** | Unique · **Terre** : stratosphère (habitat de Siegwurm) · **Niveau cible** : 55+ · **Échelle** : 3–8 |
| **Forces** | Rapace de tempête géant ; vitesse extrême ; rafales qui déstabilisent ; hors de portée (vol) |
| **Faiblesses** | **Noyau d'air** visible pendant sa descente en spirale ; **l'écho des commandes vocales le désoriente** (le vent porte la voix — les commandes bien articulées le font dévier de sa trajectoire) |
| **Résistances / Immunités** | Très résistant au vent ; immunisé aux projectiles à faible vélocité (le vent les dévie) |
| **Compétences** | **Spirale de chasse** (sifflement descendant = noyau exposé) ; **Rafale déchirante** (grondement grave = balayage aérien) ; **Plumes de tempête** (pluie de plumes — lueur scintillante) |
| **IA** | États : `Le Cercle haut` (repérage) → `La Spirale` (descente — fenêtre au noyau) → `La Tempête` (rafales rapprochées sous 25 %). Priorités : garder l'altitude, cibler les joueurs statiques, fuir les commandes vocales claires. |
| **Environnement** | Plateformes de nuages, courants ascendants |
| **Récompenses** | Matériau **vent** (voir `SYSTEMS.md` — éléments), plume du Kamuy |

### 2.3 La Trinité

| Champ | Détail |
|---|---|
| **Type** | Unique · **Terre** : profondeurs marines (habitat de Ctharnide) · **Niveau cible** : 55+ · **Échelle** : 8+ |
| **Forces** | **Trois têtes** (trois personnalités, trois angles d'attaque) ; coordination parfaite tant qu'elles s'entendent ; champ d'eau |
| **Faiblesses** | **Désaccord interne** : les têtes se contredisent (fenêtres de chaos) ; la lumière des profondeurs les divise ; chaque tête morte réduit la coordination — mais les deux restantes compensent |
| **Résistances / Immunités** | Très résistante à l'eau ; immunisée aux attaques qui ne touchent qu'une tête en phase d'accord |
| **Compétences** | **Chœur** (les trois têtes attaquent en même temps — réverbération triple) ; **Discorde** (les têtes se disputent — fenêtre de vulnérabilité) ; **Chant des fonds** (silence soudain → enlacement de zone) |
| **IA** | **Trois FSM séparées** avec blackboard partagé : chaque tête a sa cible et son style (griffes, chant, enlacement) ; un compteur d'accord décide Chœur vs Discorde (l'isolement d'une tête fait monter la discorde). Priorités : maintenir l'accord, punir la séparation du groupe. |
| **Environnement** | Abysses : courants, piliers de corail (caches), zones sans lumière |
| **Récompenses** | Matériau **eau**, écaille de la Trinité |

### 2.4 Serpent du Lac de Vie

| Champ | Détail |
|---|---|
| **Type** | Unique (gardien des Ruines de Fer) · **Terre** : Priméa (Ruines de Fer) · **Niveau cible** : élevé pour son niveau de zone (entraînement de groupe) · **Échelle** : 3–8 |
| **Forces** | Enlacement (immobilisation) ; champ d'eau ; contrôle de zone par les vagues ; taille colossale |
| **Faiblesses** | **Écho et lumière** (famille des Profondes, `BESTIARY.md`) ; les **piliers de l'arène** brisent son enroulement ; sa tête est exposée en émergence |
| **Résistances / Immunités** | Résistant à l'eau ; résistant tant qu'il est immergé |
| **Compétences** | **Émergence** (l'onde précède la tête — esquiver au signal sonore) ; **Enlacement** (le corps s'enroule — lueur sous l'eau = zone d'étreinte) ; **Vague écrasante** (grondement grave = vague de zone) |
| **IA** | États : `Immersion` (insaisissable, frappe par vagues) → `Émergence` (tête exposée — fenêtre) → `Enroulement` (contrôle de zone, il se sert des piliers). Priorités : isoler un joueur, briser les piliers (il les évite), se retirer si le groupe reste uni. |
| **Environnement** | Ruines inondées : piliers, eau montante/descendante (rythme de l'arène) |
| **Récompenses** | Écaille du Lac de Vie, matériau d'eau, réputation « Briseur de gardien » |

### 2.5 Colosse du Bunker

| Champ | Détail |
|---|---|
| **Type** | Unique · **Terre** : Onzécime (approches de Cinquantia) · **Niveau cible** : 60+ · **Échelle** : 8+ (test d'équipe) |
| **Forces** | Golem de siège antique ; **5 points vitaux (noyaux)** — chacun doit être détruit dans l'ordre visible ; dégâts massifs lents ; tank absolu |
| **Faiblesses** | Les **noyaux** (5) s'éteignent un à un ; il **frappe après l'impact** (la frappe est lente — l'esquive se lit dans l'armure, famille des Golems) ; chaque noyau détruit l'immobilise brièvement |
| **Résistances / Immunités** | Très résistant aux dégâts directs (hors noyaux) ; immunisé aux contrôles tant que ≥ 3 noyaux sont actifs |
| **Compétences** | **Frappe de siège** (le bras se lève lentement = zone de choc) ; **Barrage de débris** (les plaques de l'armure se détachent — projectiles) ; **Rage de noyau** (chaque noyau détruit déclenche une onde de choc) |
| **IA** | États : `Verrouillage` (sélectionne un noyau, concentre les attaques) → `Frappe lente` (cycle bras) → `Sursaut` (onde à chaque noyau détruit). Priorités : défendre le noyau actif, punir le corps-à-corps statique, alterner les cibles. |
| **Environnement** | Bunker : murs coulissants (caches, pièges), gravats (terrain) |
| **Récompenses** | Plans de golem, plaque de bunker (matériau de forge), titre « Démolisseur » |

---

## 3. Boss de donjon de progression (5)

> Instances 1–8 joueurs (`WORLD.md` §2). Chaque donjon a sa « clé de compréhension ».

### 3.1 Serpent du Lac de Vie — Ruines de Fer de la Divinité
> Voir dossier complet **2.4** — donjon d'entraînement de groupe, aucun changement de combat.

### 3.2 Gobelin Furax — Fosse des Brèches

| Champ | Détail |
|---|---|
| **Type** | Donjon (aussi boss de zone Secondil) · **Niveau cible** : 10–20 · **Échelle** : 3–8 |
| **Forces** | **Meute** (subordonnés gobelins) ; charges coordonnées ; rage en fin de vie |
| **Faiblesses** | **Leadership** : si Furax est à terre, la meute fuit ; **dos exposé** après la charge (les charges sont télégraphiées — posture basse + souffle) ; l'**eau des marais** ralentit sa charge |
| **Résistances / Immunités** | Résistant aux coups sourds (armure de fortune) |
| **Compétences** | **Charge de meute** (posture basse + souffle — ligne de charge) ; **Cri de ralliement** (couinement aigu = la meute converge) ; **Fureur verte** (sous 30 %, attaques plus rapides, télégraphie raccourcie) |
| **IA** | États : `Patrouille` → `Chasse en meute` (les subordonnés encerclent — FSM propres avec un blackboard partagé) → `Fureur` (sous 30 %). Priorités : encercler, protéger le chef, fuir si le chef tombe. Anti-exploit : les gobelins ignorent les aggro « à distance » (le regard seul ne suffit pas — il faut s'engager). |
| **Environnement** | Marais : eau (ralentit la charge), passerelles (les gobelins tombent), minerais gris |
| **Récompenses** | Clé de la fosse, crocs de Furax, plans d'armes |

### 3.3 Colosse de Cristal — Grotte de la Forêt Prismatique

| Champ | Détail |
|---|---|
| **Type** | Donjon (aussi boss de zone Terrae Trois) · **Niveau cible** : 15–25 · **Échelle** : 3–8 |
| **Forces** | **Réverbère les attaques magiques** (les retourne au lanceur) ; carapace cristalline (dégâts physiques réduits) ; les cristaux réfléchissent la lumière (éblouissement) |
| **Faiblesses** | **Articulations de cristal sombre** (points vitaux) ; **la couleur annonce l'élément** (lueur rouge = feu, bleue = eau — esquive par vision, `BESTIARY.md`) ; les cristaux du plafond peuvent être **réorientés** par le joueur pour focaliser la lumière |
| **Résistances / Immunités** | Réfléchit les projectiles magiques ; réduit les dégâts physiques directs |
| **Compétences** | **Prisme** (lueur = attaque élémentaire) ; **Éclat de cristal** (l'armure se fragmente — projectiles) ; **Réverbération** (renvoie le dernier sort reçu) |
| **IA** | États : `Caméléon` (choisit une couleur/élément, annonce par lueur) → `Fragmentation` (perd des plaques, devient plus rapide) → `Éclat final` (sous 25 %, réverbère tout). Priorités : s'adapter au groupe, punir le spam élémentaire. |
| **Environnement** | Grotte prismatique : cristaux réorientables, effets de lumière (esquive par vision), miroirs de roche |
| **Récompenses** | Cristal de forge, essence élémentaire |

### 3.4 Dragon Usurpateur — Barrows de Lumière

| Champ | Détail |
|---|---|
| **Type** | Donjon/zone (Quatrelle) — **pas un unique** (voir `BOSSES.md`) · **Niveau cible** : 20–30 · **Échelle** : 3–8 |
| **Forces** | Feu ; vol court ; fureur territoriale ; a pris la place d'un ancien gardien (l'identité réelle reste secrète) |
| **Faiblesses** | **Usurpateur** : son aile est blessée (posture d'envol asymétrique — point vital) ; il **hait la lumière** des Barrows (les rayons l'aveuglent = fenêtres) ; ses écailles ne sont pas anciennes (résistances visibles limitées) |
| **Résistances / Immunités** | Résistant au feu ; faible aux gravures de lumière |
| **Compétences** | **Souffle usurpé** (lueur rouge dans la gorge = cône de feu) ; **Piqué du nid** (sifflement = descente) ; **Fureur territoriale** (rugissement = zone, il défend son nid) |
| **IA** | États : `Survol` (cycle vol/sol, harcèlement) → `Défense du nid` (il retourne au nid — fenêtre quand il est aveuglé par les rayons) → `Désespoir` (sous 25 %, vole moins, se bat au sol). Priorités : garder la distance, défendre le nid, éviter la lumière. |
| **Environnement** | Barrows : rayons de lumière (fenêtres), tumulus (caches), le nid (sac à butin) |
| **Récompenses** | Écaille d'usurpateur, œuf vide (artefact), matériau feu |

### 3.5 Gardien du Sceau — Fond des Abysses *(nouveau — à intégrer à `CONTENT.md`)*

| Champ | Détail |
|---|---|
| **Type** | Donjon (progression 5) · **Terre** : abysses (accès lié au sceau de la Grande Bleue) · **Niveau cible** : 50–55 · **Échelle** : 3–8 |
| **Forces** | Unité d'opération magique des Divins **corrompue par la Grande Bleue** ; armure antique (résistante) ; **contamine les joueurs** (accumulation de corruption) ; canalise le sceau |
| **Faiblesses** | **La corruption se voit** (points sombres sur l'armure — points vitaux) ; la **lumière des gravures/Saints** la gêne (famille des Créatures de la Bleue, `BESTIARY.md`) ; elle est **canalisée par le sceau** — couper la canalisation l'affaiblit |
| **Résistances / Immunités** | Résistante à l'eau et au feu ; immunisée tant que la canalisation du sceau est active |
| **Compétences** | **Pulse du sceau** (lueur abyssale = dégâts de zone rythmés) ; **Invocation de moignons** (créatures corrompues — couinement = apparition) ; **Étreinte de la Bleue** (silence soudain → corruption de zone) ; **Canalisation** (état défensif lié au sceau — interrompre au bon moment) |
| **IA** | États : `Canalisation` (défense, invocation de moignons) → `Coupure` (le sceau est interrompu — fenêtre) → `Déluge` (sous 25 %, corruption massive, fin de canalisation). Priorités : maintenir la canalisation, corrompre les joueurs, se replier sur le sceau. |
| **Environnement** | Abysses : le sceau (structure), eau montante, moignons corrompus |
| **Récompenses** | **Accès au sceau** (portail vers Ctharnide), relique corrompue, matériau d'abîme |
| **Marque** | Accumulation de corruption — la **Marque de la Bleue** au-delà d'un seuil (voir 1.3) |

---

## 4. Boss de zone (12)

> Respawn hebdomadaire, rotation d'emplacement (`WORLD.md` §3). 1 par Terre. Les dossiers marqués **réf** sont les mêmes combats que leur version donjon/unique — seule la règle de respawn change.

### 4.1 Gardien des Premières Forges — Priméa

| Champ | Détail |
|---|---|
| **Type** | Zone · **Niveau cible** : 1–10 · **Échelle** : 3–8 |
| **Forces** | Golem-forgeron antique ; marteau de zone ; étincelles ; l'enclume centrale (il s'en sert comme bouclier) |
| **Faiblesses** | **Cycle forge/attaque lisible** : quand il forge, son **noyau est exposé** (dos) ; l'enclume peut être détruite (il perd son bouclier) ; frappe après l'impact (lent — famille des Golems) |
| **Résistances / Immunités** | Très résistant aux coups sourds ; faible au froid (étincelles = feu) |
| **Compétences** | **Marteau de forge** (bras levé lentement = zone de choc) ; **Pluie d'étincelles** (lueur rouge = zone différée) ; **Retour à l'enclume** (il court s'abriter — fenêtre de noyau) |
| **IA** | États : `Forge` (vulnérable, cycle fixe) → `Attaque` (frappe, puis retour) → `Fureur` (sous 30 %, forge plus vite). Priorités : protéger l'enclume, punir les approches frontales. |
| **Environnement** | Forges actives : braises, enclume, chaînes (pièges) |
| **Récompenses** | Plans de forge, minerai de Priméa |

### 4.2 Gobelin Furax — Secondil
> **Réf.** dossier 3.2 (même combat, respawn hebdo + rotation d'emplacement dans la Fosse).

### 4.3 Colosse de Cristal — Terrae Trois
> **Réf.** dossier 3.3.

### 4.4 Dragon Usurpateur — Quatrelle
> **Réf.** dossier 3.4.

### 4.5 Serpent du Lac de Vie — Cinquepont
> **Réf.** dossier 2.4 (version zone — rotation d'emplacement sur les lacs).

### 4.6 Seigneur des Vallées — Sixvallon

| Champ | Détail |
|---|---|
| **Type** | Zone · **Niveau cible** : 30–40 · **Échelle** : 3–8 |
| **Forces** | Titan de la harde (grand cervidé blindé) ; **charge en ligne** (dévastatrice, traverse l'arène) ; appelle la harde (adds) ; terrain accidenté à son avantage |
| **Faiblesses** | **Flancs exposés après la charge** (demi-tour lent) ; **cornes cassables** (2 impacts de gravure → il perd sa charge) ; la harde fuit s'il tombe |
| **Résistances / Immunités** | Résistant de face ; très résistant au froid |
| **Compétences** | **Charge des vallées** (posture basse + souffle — ligne) ; **Appel de la harde** (grondement grave → adds) ; **Piétinement** (le sol tremble = zone rythmée) |
| **IA** | États : `Pâture` (patrouille) → `Charge` (ligne, demi-tour lent) → `Défense de la harde` (protège les adds, enrage si la harde tombe). Priorités : traverser le groupe, protéger la harde, punir l'approche frontale. |
| **Environnement** | Vallées : pentes (la charge profite du dénivelé), rochers (caches), la harde |
| **Récompenses** | Corne de titan, viande de chasse (économie), trophée |

### 4.7 Roi des Brumes — Huitbrume

| Champ | Détail |
|---|---|
| **Type** | Zone · **Niveau cible** : 40–50 · **Échelle** : 3–8 |
| **Forces** | Spectre-roi (famille des Spectres, `BESTIARY.md`) ; **immatériel** (dégâts physiques réduits) ; se déplace dans la brume (disparition/réapparition) ; la brume cache ses attaques |
| **Faiblesses** | **Craint le son** (les commandes vocales puissantes le blessent — sa couronne émet un écho de localisation) ; la **brume se dissipe** si le groupe reste groupé (elle est « hantée » par l'isolement) |
| **Résistances / Immunités** | Immatériel (physique réduit) ; immunisé aux critiques au-delà d'une distance de brume |
| **Compétences** | **Disparition** (silence soudain → il se déplace dans la brume) ; **Hurlement de couronne** (grondement grave = zone) ; **Étreinte des brumes** (la brume se referme = ralentissement) |
| **IA** | États : `Hantise` (disparaît/réapparaît autour d'un isolé) → `Hurlement` (zone) → `Couronne exposée` (sous 30 %, il ne peut plus disparaître). Priorités : cibler les isolés, rester dans la brume, fuir le son. |
| **Environnement** | Brumes éternelles : visibilité réduite, échos (localisation sonore), lisières |
| **Récompenses** | Essence de brume, couronne du roi (artefact), matériau de gravure sonore |

### 4.8 Gardien Déchu — Neuville

| Champ | Détail |
|---|---|
| **Type** | Zone · **Niveau cible** : 45–55 · **Échelle** : 3–8 |
| **Forces** | Ancien garde des Divins déchu ; **dueliste** (parades parfaites, ripostes) ; épée antique (gravée) ; combat d'honneur |
| **Faiblesses** | **Armure fissurée** (points visibles — les fissures brillent) ; **son honneur** : se laisse provoquer en duel (un joueur seul en mêlée le fixe — les autres frappent pendant le duel) ; les ripostes sont lisibles (posture géométrique, comme Vésémon) |
| **Résistances / Immunités** | Résistant aux sorts (gravure antique) ; parade parfaite des projectiles de face |
| **Compétences** | **Riposte** (posture géométrique → contre-attaque) ; **Épée de justice** (trait lumineux vertical — balayage) ; **Serment brisé** (sous 30 %, il perd sa discipline — attaques enchaînées) |
| **IA** | États : `Duel` (accepte le duel, ignore les autres si provoqué) → `Justice` (ripostes) → `Déchéance` (sous 30 %, plus de parades — rage). Priorités : duel, riposte, punir les projectiles frontaux. |
| **Environnement** | Ruines urbaines : rues étroites (duels), fissures lumineuses (indices) |
| **Récompenses** | Épée antique fissurée (forge), gravure de justice, titre « Honoré » |

### 4.9 Ver des Sables Dorés — Dixverne

| Champ | Détail |
|---|---|
| **Type** | Zone · **Niveau cible** : 50–60 · **Échelle** : 3–8 |
| **Forces** | Ver géant ; **souterrain** (impossible à cibler sous le sable) ; sables mouvants ; attaques en émergence |
| **Faiblesses** | **Les ondes de sable télégraphient l'émergence** (lire le sol) ; **gorge exposée** pendant l'émergence ; les rochers du désert brisent son tunnel (il doit contourner) |
| **Résistances / Immunités** | Immunisé tant qu'il est sous terre ; très résistant au feu (sable) ; faible à l'eau |
| **Compétences** | **Plongée** (les ondes annoncent la direction) ; **Émergence** (gorge exposée — fenêtre) ; **Sables mouvants** (le sol s'enfonce = zone de contrôle) ; **Fouet de sable** (la queue — lueur de poussière) |
| **IA** | États : `Souterrain` (déplacements, ondes) → `Émergence` (fenêtre, puis repli rapide) → `Désespoir de surface` (sous 25 %, reste en surface — rage). Priorités : rester sous terre, surprendre, fuir les rochers. |
| **Environnement** | Désert doré : dunes (ondes lisibles), rochers (barrières), mines (caches) |
| **Récompenses** | Carapace de ver, essence de sable doré, minerai |

### 4.10 Colosse du Bunker — Onzécime
> **Réf.** dossier 2.5 (version zone — rotation d'emplacement).

### 4.11 Champion de l'Arène — Cinquantia

| Champ | Détail |
|---|---|
| **Type** | Zone · **Niveau cible** : 60–70 · **Échelle** : 3–8 (arène publique) |
| **Forces** | Gladiateur de l'élite ; **apprend les patterns du joueur** (contre-attaque après observation) ; trois styles (épée, hache, lances) ; la foule l'excite |
| **Faiblesses** | **Le bluff fonctionne** : la foule réagit à ses feintes (les vraies feintes sont décelables par la réaction du public) ; **styles figés** : il change de style à 50 % (fenêtre de transition) ; la foule se retourne contre lui s'il triche (il perd des bonus) |
| **Résistances / Immunités** | Résistant à distance (bouclier de parade) |
| **Compétences** | **Contre-attaque** (il enregistre la dernière séquence du joueur — posture d'observation) ; **Changement de style** (transition lisible — fenêtre) ; **Appel du public** (la foule lance des projectiles aux deux camps — les deux) |
| **IA** | États : `Observation` (parade, analyse — la fréquence des attaques du joueur est enregistrée) → `Contre` (rejoue les patterns observés) → `Cœur de gladiateur` (sous 30 %, tout le registre). Priorités : analyser, contre-attaquer, faire durer le spectacle. Anti-exploit : l'IA lit les fréquences d'inputs (anti-macro — les rotations figées sont punies). |
| **Environnement** | Arène : foule (réactions, projectiles), portes de sortie (pièges), sable |
| **Récompenses** | Titre « Champion », armes d'arène, faveurs de l'élite |

### 4.12 La Gardienne Effacée — Septième *(Terre Effacée)*

| Champ | Détail |
|---|---|
| **Type** | Zone (Terre secrète, 65–75+) · **Niveau cible** : 65+ · **Échelle** : 8+ |
| **Forces** | Gardienne de la Terre Effacée ; **efface les buffs et les repères** (la carte s'efface autour d'elle) ; contrôle par le regard ; les joueurs « oubliés » sont désorientés (repères supprimés) |
| **Faiblesses** | **Elle cible par le regard** : si personne ne la regarde, elle **« s'efface »** (perd sa cible — fenêtre) ; sa mémoire est courte (elle ne se souvient pas des joueurs hors de son champ) ; le silence la perturbe (les commandes silencieuses passent sous son radar) |
| **Résistances / Immunités** | Résistante aux buffs (elle les efface) ; immunisée aux attaques depuis son angle mort |
| **Compétences** | **Effacement** (silence soudain → suppression de zone — carte, buffs) ; **Regard de la Gardienne** (fixation → désorientation) ; **Retour du souvenir** (elle « se souvient » — invoque des reflets de la Terre) |
| **IA** | États : `Veille` (scanne le regard des joueurs) → `Effacement` (cible le regard soutenu, efface les repères) → `Oubli` (perte de cible si personne ne la regarde — fenêtre). Priorités : fixer le regard, isoler, se perdre pour re-surprendre. |
| **Environnement** | Terre Effacée : géographie instable (repères disparaissent), échos de la Septième |
| **Récompenses** | Fragment de la Terre Effacée, entrée vers les mystères de la Septième |

---

## 5. Scénario bonus : Faux Lycaon

| Champ | Détail |
|---|---|
| **Type** | Bonus (Scénario Unique bonus — voir `BOSSES.md`) · **Niveau cible** : variable (mime la menace) · **Échelle** : 3–8 |
| **Forces** | Imite Lycaon (doubles, hurlement, bond) — assez pour tromper les groupes pressés ; récompense de niveau Entité si démasqué et vaincu |
| **Faiblesses** | **Imitation imparfaite** : son **ombre est trop parfaite** (le vrai Lycaon a une ombre vivante) ; il **cligne des yeux** (le vrai ne cligne jamais) ; ses patterns **se répètent en boucle** (contrairement au vrai, il n'adapte rien) |
| **Résistances / Immunités** | Aucune immunité de phase (pas de triche divine — c'est un imposteur) |
| **Compétences** | **Faux bond** (posture basse + souffle — charge) ; **Faux hurlement** (pas de doubles — juste du bruit) ; **Boucle** (répète sa dernière séquence — à exploiter) |
| **IA** | États : `Imitation` (rejoue un script appris de Lycaon) → `Défaut` (répète la boucle quand il est déstabilisé) → `Révélation` (démasqué, il panique — patterns erratiques). Priorités : imiter, masquer la boucle, fuir le regard soutenu (contrairement au vrai, il craint la fixation). |
| **Environnement** | Arène de la lune (copie) |
| **Récompenses** | Trophée « Chasseur d'imposteurs », matériaux de lune, réputation |

---

## 6. Contrat d'implémentation (rappel moteur)

| Besoin | Module moteur |
|---|---|
| IA des boss (utility AI, FSM, blackboard) — autoritatif | `game/` (serveur) |
| Comportements, senseurs (regard, sons, zones) | `ecs/` |
| Télégraphie et poses d'annonce | `renderer/` (animation) |
| Arènes, rotation d'emplacement, streaming | `world/` + `renderer/` |
| Règles spéciales (verrous, triche divine, Marques) | `game/` (serveur) |
| Lecture des canaux (regard, voix, inertie) pour l'IA | `input/` + `vr/` (signaux → serveur) |
| Audio signature par boss (télégraphie sonore) | `audio/` |
