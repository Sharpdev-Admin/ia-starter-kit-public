---
name: creer-seance
description: >
  Use this skill when the owner wants a training session, a class plan or a multi-week cycle
  prepared: "prépare une séance", "fais-moi le cours de mardi", "un programme de 6 semaines
  pour…", "séance de reprise pour…", "adapte la séance pour quelqu'un qui a mal au genou",
  "idées d'échauffement". Builds the session from the owner's own method and exercise list, and
  from the member's dossier when it is for one person. Flags every contraindication at the top.
  Gives no medical advice.
allowed-tools: [Read, Write, Edit, Glob, Grep, Agent, AskUserQuestion]
---

# /creer-seance — a session the owner could have written

Read `contexte/methode.md` first. If it is nearly empty, say so and offer two routes: the owner
drops three past sessions in `_inbox/` (best), or answers four questions (structure, duration,
equipment, audience). Do not invent a method.

## Step 1 — Frame the request (one question batch at most)

Establish, from the request and the dossiers, asking only what is missing: who it is for (group
or `dossiers/membres/<slug>.md`), objective, duration, place and equipment, level, and for a
cycle the number of weeks and sessions per week.

Establish the **date of the session** (compute it with `date` from « jeudi », « mardi
prochain »); it names the file.

For a named member, read the dossier section "À savoir avant une séance". Anything there goes
in the "Attention" block of the session, and every exercise listed in `methode.md` as "À éviter
si" for that condition is excluded. If that leaves nothing for the objective, the agent will
say so: put the choice to the owner (another objective, or an exercise they name) instead of
accepting a gap silently.

For a group, you do not know who will come. Scan "À savoir avant une séance" in
`dossiers/membres/` for members whose formula gives access to that class. The "Attention" block
lists what is known, by first name, and says how many of those dossiers have that section
still empty. « rien de particulier » is written only when every such dossier is filled and
says so.

## Step 2 — Write the session

Delegate the writing to the `concepteur-seance` agent with: the method file, the framing, the
dossier path if any, and the output path: `seances/collectif/<date of session>_<cours>.md` for
a group, `seances/individuel/<date of session>_<slug>.md` for one person, or
`seances/<collectif|individuel>/<AAAA-MM>_<cycle>/semaine-<n>.md` for a cycle. Individual
sessions carry a health note: nothing outside `/creer-seance` reads `seances/individuel/`.

Session format:

```
# <Titre> — <date> — <durée>

**Pour :** <groupe ou membre>   **Objectif :** <…>   **Matériel :** <…>

## Attention
<contre-indications et adaptations, ou « rien de particulier »>

## Échauffement (<min>)
## Corps de séance (<min>)
| Bloc | Exercice | Séries × répétitions ou durée | Récupération | Variante facile | Variante difficile |
## Retour au calme (<min>)

## À observer
<deux ou trois points à regarder pendant la séance>
```

A cycle adds `seances/<cycle>/README.md` with the weekly progression in one table.

## Step 3 — Check before handing over

Re-read the file: block durations add up to the requested length and each block's doses fit
in its minutes; every exercise comes from `methode.md` or is marked « nouveau — à valider »;
nothing contradicts the "Attention" block. Tell the owner how many exercises are « nouveau »,
how many doses are « proposées », and whether the objective is held in full.

## Step 4 — Learn

When the owner changes the session, update `contexte/methode.md` (exercise table, progression
rules) after proposing the change. Add the session to the member's dossier table.

## Limits

- No diagnosis, no rehabilitation protocol, no nutrition prescription. For pain or a medical
  condition, the session says « à voir avec un professionnel de santé » and stays conservative.
- No promise of results in the text.
