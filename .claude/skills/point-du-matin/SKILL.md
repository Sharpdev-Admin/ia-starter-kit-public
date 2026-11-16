---
name: point-du-matin
description: >
  Use this skill when the owner starts the day or asks what is on their plate: "point du matin",
  "qu'est-ce que j'ai aujourd'hui", "par quoi je commence", "fais-moi le point", "quoi de neuf
  depuis hier". Produces one short page: today's sessions and appointments, requests waiting for
  a reply, people to follow up today, deadlines of the week. Reads fiches and dossiers only;
  writes nothing to the mailbox and sends nothing.
allowed-tools: [Read, Glob, Grep, Bash, Agent, AskUserQuestion]
---

# /point-du-matin — one page to start the day

Read `contexte/activites.md`, `contexte/planning.md` and `contexte/niveau-de-confiance.md` first.

## Step 1 — Gather, cheapest source first

1. **Today's agenda.** If a calendar connector is available, read today and tomorrow. Otherwise
   take the day's rows from `contexte/planning.md` and say the agenda is not connected.
2. **Waiting for a reply.** Fiches in `ressources/` with `reponse_attendue: oui` and
   `statut: a-traiter`. Those with `statut: en-cours` have a draft waiting: list them apart as
   « brouillon prêt à relire », with the drafts in `tasks/relances/` not yet handled. Read the
   front matter and "En deux lignes" only, never the originals.
3. **Follow-ups due.** Prospects per the « Essais sans suite » rule of `/suivi-membres` Part B
   (a prospect with no `prochaine_relance` is not skipped),
   and `dossiers/membres/` with `statut: actif` and `resiliation: non` for `echeance` or
   `fin_engagement` within 14 days, or `derniere_venue` older than 21 days. Same rules as
   `/suivi-membres` Part B; a member `en pause` or with a résiliation asked is never listed.
4. **This week.** Rows of `contexte/planning.md` "Fermetures et périodes particulières" in the
   next 7 days, and fiches with `sens: a-payer`, `statut: a-traiter` (amount and due date).
5. **Unprocessed inbox.** Count the files in `_inbox/` other than `README.md`.
6. **New mail.** Only if a mailbox connector is available: count unread messages since the last
   run. Do not qualify them here; propose `/trier-mails`.

If there are more than 30 fiches to scan, delegate the scan to one Haiku agent that returns the
table rows; do not load the fiches in the main session.

## Step 2 — Write the page in the chat, in French

```
# Point du <jour date>

## Aujourd'hui
<heure — activité — lieu — nombre d'inscrits si connu>

## Brouillons prêts à relire (<n>)
<qui — quoi>

## À répondre (<n>)
<qui — quoi en une ligne — depuis combien de jours>

## À relancer (<n>)
<qui — pourquoi (essai sans suite / absent / abonnement qui se termine le …)>

## Cette semaine
<échéances : paiement fournisseur, événement, fermeture>

## Ce que je te propose de faire en premier
<une seule action, la plus utile>
```

Each line names the dossier or fiche path it comes from. A section with nothing says "rien".
Never pad: a morning with nothing waiting is a three-line page.

## Guardrails

- Nothing is sent, labelled or modified by this skill.
- Dates are computed with `date` in Bash, never guessed.
- If `dossiers/` holds fewer than five fiches, say that the follow-up lists are incomplete
  because the member list has not been loaded yet, and propose dropping an export in `_inbox/`.
