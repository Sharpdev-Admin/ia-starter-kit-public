---
name: suivi-membres
description: >
  Use this skill when the owner wants to know who needs attention or to keep the member list up
  to date: "qui je dois relancer", "qui ne vient plus", "quels abonnements se terminent", "les
  essais sans suite", "mets à jour mes membres", "j'ai déposé l'export des présences". Loads a
  member or attendance export into the dossiers, then lists who to contact — trials with no
  follow-up, members absent for three weeks, memberships ending within two weeks, amounts to
  collect — with one prepared message per person when the trust level allows drafts. Never sends.
allowed-tools: [Read, Write, Edit, Bash, Glob, Grep, Agent, AskUserQuestion]
---

# /suivi-membres — keep the list current, surface who to contact

Read `contexte/offre-et-tarifs.md`, `contexte/style-de-reponse.md` and
`contexte/niveau-de-confiance.md` first.

## Part A — Load an export

1. Find spreadsheet or CSV exports in `_inbox/`, **and** fiches in `ressources/` typed `export`
   with `statut: a-traiter` (an export already filed by `/ingest-inbox` and not yet loaded).
   Print the header row and the first and last data rows before anything else, and tell the
   owner which column you read as name, contact, formula, start, end, last attendance **and
   remark**. Dates are converted to `AAAA-MM-JJ`. If a column is ambiguous, ask once.
2. For each row, create or update `dossiers/membres/<slug>.md` from
   `dossiers/_template-fiche-membre.md`. Update front matter fields only; never overwrite the
   free-text sections of an existing dossier. Rules per row:
   - A new dossier gets `statut: actif` unless the remark says otherwise.
   - **A remark is never dropped.** « pause » → `statut: en pause`, with the period stated in a row of "En cours". « résiliation », « arrêt »,
     « ne renouvelle pas » → `resiliation: demandée le <date of the export>` and a row in "En
     cours". A pain or a condition → "À savoir avant une séance" only. « essai le … » →
     `essai_le`. Anything else → listed to the owner in the report.
   - An empty last attendance → `derniere_venue: jamais`.
   - A formula with a commitment period in `contexte/offre-et-tarifs.md` and no end date:
     `echeance: sans` and `fin_engagement: <debut + period>`.
   - Two rows with the same name and the same contact are one person: the second is skipped with
     the reason « doublon ». Same name, different contact: ask the owner once.
   - A row whose person exists in `dossiers/prospects/`: move that dossier to `membres/`, keep
     its history and its `essai_le`, and count it as an inscription.
3. A person present in `dossiers/membres/` with `statut: actif` and absent from a full member
   export is **listed** for the owner, not changed: the owner says whether they left. When they
   did, set `statut: parti` and `parti_le`.
4. File the export: if it is still in `_inbox/`, write its fiche at
   `ressources/<date>_export-<kind>/fiche.md` (type `export`). The fiche holds the counts, never
   the rows. The original goes to `secrets/originaux/` (it holds contacts and possibly health
   remarks; that folder is not sent to GitHub). Set the fiche `statut: fait`.
5. Report counts: rows read = created + updated + unchanged + skipped, each skipped row with
   its reason. The sum must hold; if it does not, say so before anything else.

For more than 40 rows, write a small script rather than editing by hand, run it on three rows
first, show the result, then run it on the rest.

## Part B — The lists

Compute today's date with `date`. Scan front matter only. Bounds are inclusive.

| List | Rule | Trust category |
|---|---|---|
| Essais sans suite | prospect with `etape: essai fait` or `réponse envoyée`, and either `prochaine_relance` ≤ today, or `prochaine_relance` empty and the last row of "Échanges" older than 3 days | Demande d'essai ou d'information |
| Absents | member `statut: actif`, `resiliation: non`, `derniere_venue` more than 21 days ago | Relance de membre |
| Jamais venus | member `statut: actif`, `derniere_venue: jamais`, `debut` more than 7 days ago | Relance de membre |
| Fins d'abonnement | member `statut: actif`, `resiliation: non`, `echeance` or `fin_engagement` between today and today + 14 days; an `echeance` already past is listed as « échéance dépassée » | Relance de membre |
| À encaisser | fiches typed `facture` or `paiement` with `sens: a-encaisser` and `statut: a-traiter`; amounts from the `montant` field | Paiement, facture, attestation |

Under the "Fins d'abonnement" table, name in one line the next deadline beyond the threshold.

Then a separate table **« À ne pas relancer »**, so the owner sees who was left out and why:
members `en pause`, members with a `resiliation` asked (with their end date), prospects with
`relances_faites: 2` or more.

Thresholds can be overridden by a line in `contexte/activites.md` "Règles de tri".

Present one table per list: who, the fact that triggered it (with the date), the last exchange,
the suggested message in one line.

## Part C — Messages, by trust level

Each list follows its own trust category (table above); when in doubt, the lowest. At level 1,
stop at the tables. From level 2, spawn `email-reply-drafter` once per person, with the dossier,
the reason, the trust level and the output path `tasks/relances/<AAAA-MM-JJ>_<slug>.md`. Tell it
there is no message to answer (`repond_a: aucun (relance)`, no « Re: » subject). Show each draft
in the chat in a code block.

The message is short and personal. It mentions one concrete fact from the dossier other than
the absence itself (formula, card validity, a session, a goal); with no such fact it says
nothing specific and the draft notes « aucun fait personnel disponible ». It never guilt-trips.
Health information is never quoted.

After the owner has handled a person: for a prospect, set `prochaine_relance` and add one to
`relances_faites`; for a member, add a row to "Historique des échanges".

## Guardrails

- No message is sent by this skill below level 4 for the list's category.
- Nobody in « À ne pas relancer » gets a draft.
- Then `git add` the new and changed files and commit (`Suivi membres (AAAA-MM-JJ)`). Do not
  push unless the session is ending.
