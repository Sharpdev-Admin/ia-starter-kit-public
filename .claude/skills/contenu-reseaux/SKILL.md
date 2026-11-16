---
name: contenu-reseaux
description: >
  Use this skill when the owner wants social media posts, a newsletter or an announcement
  prepared: "prépare mes posts de la semaine", "un post pour annoncer le stage", "idée de reel",
  "la newsletter du mois", "une story pour les places qui restent", "j'ai rien publié depuis
  trois semaines". Starts from what actually happened at the club (sessions, events, member
  milestones the owner approved), writes three to five pieces in the owner's voice, and
  describes the photo or video to shoot. Publishes nothing.
allowed-tools: [Read, Write, Edit, Bash, Glob, Grep, Agent, AskUserQuestion]
---

# /contenu-reseaux — a week of posts from real material

Read `contexte/activites.md`, `contexte/offre-et-tarifs.md`, `contexte/planning.md` and
`contexte/style-de-reponse.md` first, and `contexte/ligne-editoriale.md` if it exists.

## Step 1 — Collect real material

- Group sessions of the week in `seances/collectif/`, without their "Attention" block. Never
  `seances/individuel/`, never a dossier's health section.
- Events, closures, new slots in `contexte/planning.md`.
- Fiches of the last 14 days in `ressources/` typed `note` (the owner's dictated notes are the
  best source). What a note says about a prospect or a member's follow-up is not material.
- Places left, an offer ending, a new formula in `offre-et-tarifs.md`.

If there is nothing, ask the owner one question: « Qu'est-ce qui s'est passé de bien au club
cette semaine ? » and work from the answer. Never invent an anecdote, a testimonial, a result, or a feeling
attributed to the owner.

## Step 2 — Plan the week

Propose three to five pieces, each with a purpose, and get the owner's yes before writing:

| Purpose | Example |
|---|---|
| montrer | what a session looks like |
| expliquer | one tip, one exercise, one mistake |
| rassurer | what a first session is like |
| vendre | places left, trial, new slot — one of these per week at most |
| remercier | the group, a partner |

## Step 3 — Write

Spawn `redacteur-reseaux` once per piece, with the material, the purpose and the output path
`contenus/<AAAA>-S<semaine>/<n>_<slug>.md`. Each file holds: channel and format, the hook, the
text, a call to action, and **« Image à prévoir »** — what to photograph or film, framing, who
must have agreed to appear.

## Step 4 — Check

- Any member named or recognisable: read `accord_citation` in their dossier. Being quoted and
  being shown in a photo are two agreements. If the dossier records the one needed, the file
  says « accord noté le <date> »; if only a note mentions it, « accord à confirmer (ta note du
  <date>) » and propose recording it; otherwise « accord de <prénom> à obtenir ». A minor is
  never named.
- No health claim, no before/after, no promised result.
- Every price, date, place and slot is traceable to `contexte/`. A figure that comes only from
  a note (places left, attendance) is kept and flagged at the top of the file: « d'après ta
  note du <date> — à confirmer avant de publier ».
- Until `contexte/ligne-editoriale.md` exists, the voice comes from
  `contexte/style-de-reponse.md`; say so on the first run.

For an important piece (a paid programme launch, a page of the site), propose `/panel-relecture`.

## Step 5 — Hand over

List the pieces with the day proposed for each. The owner publishes. If the owner corrects the
tone, record it in `contexte/ligne-editoriale.md` (create it on the first correction).
