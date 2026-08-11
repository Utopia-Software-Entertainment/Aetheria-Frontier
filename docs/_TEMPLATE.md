# TEMPLATE — Modèle de document

> Chaque document du repo suit ce gabarit. Copier le bloc méta en tête de fichier et respecter la structure. Les **statuts** évoluent : Brouillon → En revue → Validé.

## Bloc méta (à copier après le titre)

```markdown
> **Statut** : Validé v0.1 · **Version** : 0.1 · **MAJ** : 2026-08-11 · **Owner** : <rôle>
> **Dépend de** : <liste des docs lus en amont>
```

Rôles d'owner : Design · Narration · Systèmes · Combat · Social · Économie · UX · Audio · Art · Équilibrage · Studio.

## Structure type

1. **Titre** : `# NOM — Sujet`
2. **Bloc méta** (ci-dessus).
3. **Intro** : une phrase `>` qui situe le doc dans l'ensemble (ce qu'il complète, ce qui le complète).
4. **Principes** : 3–6 principes numérotés, non négociables, écrits en une ligne chacun.
5. **Sections détaillées** : tables et règles. Une idée = une ligne. Jamais de prose décorative.
6. **Décisions ouvertes** (si pertinent) : ce qui reste à trancher en playtest.
7. **Contrat d'implémentation** : table `| Besoin | Module moteur |` (rappels `renderer/`, `audio/`, `game/`, `network/`, `world/`, `ecs/`, `input/`, `voice/`, `physics/`, `core/`).

## Règles de rédaction

- Chaque valeur chiffrée est une **cible à valider en playtest** (voir `CONTENT.md`, `BALANCE.md`).
- Les noms propres sont des **créations originales** (transpositions de travail à remplacer).
- Le mystère est un contenu : ne jamais documenter les conditions de déclenchement des Scénarios EX.
- Les références croisées utilisent les noms de fichiers (`BESTIARY.md`, `CONTROLS.md`…).
- Termes définis dans `GLOSSARY.md` — y ajouter tout nouveau terme.
