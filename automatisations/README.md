# automatisations/ — le mode avancé

> À ouvrir quand les étapes 1 à 3 du guide tournent depuis au moins un mois. Une automatisation
> agit **sans toi** : si elle est mal réglée, elle envoie de mauvais messages à tes membres sans
> que tu le voies. Claude, lui, te montre toujours un brouillon avant.

## La différence avec le reste du kit

| | Claude (le reste du kit) | Automatisation |
|---|---|---|
| Quand ça agit | quand tu le demandes | tout seul, à chaque événement |
| Qui valide | toi, à chaque fois | personne |
| Si ça se trompe | tu le vois dans le brouillon | tu l'apprends par un membre |
| Mise en place | une heure | une demi-journée à deux jours |

## Les paliers, dans l'ordre

| Palier | Ce que tu obtiens | Outils | Coût mensuel | Difficulté | État |
|---|---|---|---|---|---|
| A. Réservation en ligne | Une page où un prospect réserve son essai, limite de places, annulation, mail de confirmation | Cal.com | 0 € avec l'offre gratuite | faible : aucun branchement | prêt — `A_reservation-en-ligne.md` |
| B. Alerte sur ton téléphone | Un message Telegram à chaque réservation ou annulation | Cal.com, Make, Telegram | 0 € : deux scénarios, dans la limite de l'offre gratuite de Make | moyenne : trois comptes, une adresse à coller | spécifié, **modèle à construire et tester** — `B_alerte-telephone.md` |
| C. Journal des inscriptions | Chaque réservation ajoute une ligne dans un tableur | + Excel ou Google Sheets | offre payante de Make, environ 10 € (à revérifier sur le site de Make) | élevée | à faire avec un accompagnement |
| D. Après la séance | Remerciement, demande d'avis Google, relance d'un absent | + outil d'envoi de mails | idem | élevée | non construit |
| E. Paiement | Abonnement ou carte payés en ligne, suivi des impayés | + Stripe | frais de Stripe non chiffrés | élevée et sensible | non construit — ne pas tenter seul |

Fais A. Vis avec pendant deux semaines. Ne passe à B que si tu rates des réservations faute de
les voir à temps. C, D et E se font avec quelqu'un qui en a déjà monté.

## Ce que Claude fait et ne fait pas ici

- Il te guide écran par écran pour A et B, et vérifie avec toi que ça marche.
- Il ne te demande jamais de coller une clé ou une adresse de webhook dans la conversation : il
  te dit dans quel écran la copier et où la coller.
- Il ne met rien en service à ta place : c'est toi qui actives.

## Avant d'activer une automatisation : cinq questions

1. Que se passe-t-il si elle se déclenche deux fois ?
2. Que se passe-t-il si elle ne se déclenche pas ? Comment je le saurai ?
3. Quel message un membre peut-il recevoir, mot pour mot ?
4. Comment je l'arrête en dix secondes ?
5. Ai-je fait un essai complet avec une fausse réservation à mon nom ?
