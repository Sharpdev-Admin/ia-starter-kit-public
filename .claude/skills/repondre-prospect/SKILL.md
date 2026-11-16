---
name: repondre-prospect
description: >
  Use this skill when someone who is not yet a member asks for information, a price or a trial
  session, whatever the channel: "réponds à ce prospect", "quelqu'un demande un essai", "réponds
  à cette demande d'info", "j'ai reçu ce message sur Instagram", "il veut connaître les tarifs".
  Qualifies the request, creates or updates the prospect dossier, and prepares the reply with the
  owner's real prices and time slots, in the owner's style. Draft only; the trust ladder decides
  where the draft lands. Never confirms a booking and never quotes a price that is not in
  `contexte/offre-et-tarifs.md`.
allowed-tools: [Read, Write, Edit, Bash, Glob, Grep, Agent, AskUserQuestion]
---

# /repondre-prospect — from a first message to a reply ready to send

Read `contexte/offre-et-tarifs.md`, `contexte/planning.md`, `contexte/style-de-reponse.md` and
`contexte/niveau-de-confiance.md` (category "Demande d'essai ou d'information") first.

## Step 1 — Get the message into a fiche

The message may be an e-mail, a screenshot of Instagram or WhatsApp in `_inbox/`, a pasted text
or a dictated note. Whatever it is, it becomes a fiche in `ressources/` first (the fiche step of
`/ingest-inbox`). For a screenshot, the fiche "Contenu" holds the transcribed text of the
message, word for word.

## Step 2 — Prospect dossier

Look for an existing dossier (`grep -ril` on the name, the address and the account in
`dossiers/`). If the person is already a member, stop and say so: this is not a prospect.
Otherwise create or update `dossiers/prospects/<slug>.md` from
`dossiers/_template-fiche-prospect.md`: what they are looking for, origin, `etape`, and
`prochaine_relance` set three days ahead.

## Step 3 — Build the answer from the owner's facts

List what the prospect asked, then answer each point **only** from `contexte/`:

| Asked | Source | Rule |
|---|---|---|
| price, formula, way of paying | `offre-et-tarifs.md` | a formula or condition not listed is unknown, not refused |
| trial session | `offre-et-tarifs.md` "Séance d'essai" | — |
| a class on a given day or time | `planning.md` "Semaine type" | a day or hour absent from the table is a fact: « je n'ai pas de cours le vendredi », followed by what exists |
| a trial slot | `planning.md` "Créneaux pour une séance d'essai" only | if the prospect wants to try a class that is not a trial slot, propose the trial slots and put the point to the owner |
| level, health, injury | — | see below |

**Health.** Whatever the prospect reports, the reply does not name the condition back, gives
no opinion on whether the practice is advised, and promises no adaptation. It uses one
sentence, in the owner's words if `style-de-reponse.md` has one, else: « Pour ça, le mieux est
d'en parler avec un professionnel de santé ; dis-m'en un mot avant la séance. » The detail goes
to the prospect dossier under "À savoir avant une séance", not into the fiche.

**Unknowns.** Before drafting, put every point with no source to the owner in one batch of
questions (four at most), each quoting the prospect's sentence. Write the answers into the
right `contexte/` file so the next reply has them. A point still open is written
`[À VÉRIFIER : …]` in the draft — this form only — and the draft is reported as **not ready to
send**.

Propose two slots at most, worded as proposals (« je peux te proposer… »), never as a confirmed
booking. A calendar or mail tool is used only if `contexte/activites.md` lists it as connected;
if one is available in the session and not listed, say so and ask.

## Step 4 — Draft, by trust level

Spawn `email-reply-drafter` with the fiche, the dossier and the facts of Step 3. Tell it the
channel: for Instagram or WhatsApp there is no `objet` and no `destinataire`, the text is three
or four short lines, and the first name is used only if the person gave it (an account name is
not a first name). Match the prospect's own tu or vous unless `style-de-reponse.md` says
otherwise for prospects.

| Level | Where the draft goes |
|---|---|
| 1 | no draft: report the gist and what the reply should say |
| 2 | `ressources/<date>_<slug>/brouillon.md`, or a mailbox draft without recipient |
| 3 | mailbox draft with recipient pre-filled |
| 4 | sent only if this category is listed at level 4 |

For Instagram or WhatsApp the draft is always a file, shown in the chat in a code block so the
owner can copy it from a phone.

## Step 5 — Close the loop and report

- Fiche: `statut: en-cours` (a draft exists; it leaves « À répondre »). When the owner says it
  was sent: `statut: fait`.
- Prospect dossier: `etape: réponse envoyée` once sent, `prochaine_relance` seven days ahead, a
  row in "Échanges".
- Report: who, what they want, what was answered, each `[À VÉRIFIER]` left, whether the draft is
  ready to send, when the follow-up is due. Re-read the draft first: every price, slot and
  condition must be traceable to a line of `contexte/`.

## When the owner edits the draft

Ask for the sent version (or read it from the `sent` folder), diff, and record the pattern in
`contexte/style-de-reponse.md` after proposing it.
