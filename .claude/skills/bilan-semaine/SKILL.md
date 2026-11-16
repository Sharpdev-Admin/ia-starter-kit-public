---
name: bilan-semaine
description: >
  Use this skill when the owner wants the figures and the state of the business: "bilan de la
  semaine", "bilan du mois", "où j'en suis", "combien de nouveaux", "combien d'essais ont
  signé", "qu'est-ce qui reste à encaisser", "qu'est-ce que je dois payer". Counts from the
  dossiers and fiches — new prospects, trials done, sign-ups, departures, memberships ending,
  amounts to collect and to pay — compares with the previous period, and names the one thing
  worth acting on. States what it could not count.
allowed-tools: [Read, Write, Bash, Glob, Grep, Agent]
---

# /bilan-semaine — figures the owner can trust

## Step 1 — Period

Default: the last seven days ending yesterday. « bilan du mois » means the last full calendar
month. Compute the dates with `date`.

## Step 2 — Count, with a script

Counting is done by a command over front matter, never by reading and estimating.

**Period figures** — recounted on the previous period for comparison:

| Figure | How |
|---|---|
| Nouveaux prospects | `dossiers/prospects/*` with `premiere_demande` in the period |
| Essais faits | prospects **and members** with `essai_le` in the period |
| Inscriptions | `dossiers/membres/*` with `debut` in the period |
| Départs | members with `parti_le` in the period |

**State figures** — compared with the previous saved bilan in `tasks/bilans/`; if there is
none, write « pas de bilan précédent »:

| Figure | How |
|---|---|
| Membres actifs | members with `statut: actif` |
| Résiliations demandées | members with `resiliation` other than `non` |
| Fins à venir | `echeance` or `fin_engagement` within 30 days |
| À encaisser | sum of `montant` over fiches typed `facture`/`paiement`, `sens: a-encaisser`, `statut: a-traiter` |
| À payer | same with `sens: a-payer`, each with its due date |
| Demandes sans réponse | fiches with `reponse_attendue: oui`, `statut: a-traiter`, and `date` more than 2 days before today |

**Essai → inscription**, over the last 60 days: members with `debut` and `essai_le` both in the
window, out of all dossiers with `essai_le` in the window. Give the two counts. Give a
percentage only when the second count is 5 or more and the first does not exceed it.

## Step 3 — Say what is not counted

Before the figures, list what this bilan cannot see: payments made outside the fiches, people
who never got a dossier, attendance if no export was loaded since `<date of last export fiche>`,
trials of members whose dossier has no `essai_le`.

## Step 4 — Write

Save to `tasks/bilans/<AAAA-MM-JJ>_bilan.md` and show in the chat: the table (figure, this
period, previous), three lines of reading, and **one** proposed action. Each figure can be
expanded on request into the list of names behind it. Then commit (`Bilan (AAAA-MM-JJ)`).

## Guardrails

- No figure without the command that produced it; keep the commands in the saved file.
- Amounts are never rounded or estimated; a fiche whose `montant` is `inconnu` is listed by
  name, not counted as zero.
- No health information and no member's remark in a bilan.
