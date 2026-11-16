# Guide de démarrage — six semaines, une tâche à la fois

Ne cherche pas le système parfait. Choisis la tâche répétitive qui te prend le plus de temps,
mets-la en place, et étends ensuite.

## Vue d'ensemble

| Étape | Durée | Ce que fait Claude | Ce que tu fais | Niveau de confiance |
|---|---|---|---|---|
| 0. Installation | 1 heure | Te pose des questions, remplit `contexte/` | Tu réponds, tu branches ta boîte mail et ton agenda | — |
| 1. Observation | 2 semaines | Trie les demandes, crée les fiches, te donne le point du matin | Tu réponds toi-même, comme d'habitude | 1 |
| 2. Brouillons | 1 à 2 semaines | Prépare les réponses aux prospects et les relances | Tu relis, corriges, envoies | 2 puis 3 |
| 3. Production | en continu | Prépare séances, publications, bilan de la semaine | Tu valides, tu recadres | 3 |
| 4. Mode avancé | quand le reste tourne | Réservation en ligne, rappels, alertes sur ton téléphone | Tu décides quelles catégories partent seules | 3 à 4 |

## Étape 0 — Installation (une heure)

1. Fais les six points du `README.md`.
2. Colle `PROMPT-INSTALLATION.md` dans ta première session. Claude remplit avec toi :
   `contexte/activites.md`, `contexte/offre-et-tarifs.md`, `contexte/planning.md`,
   `contexte/style-de-reponse.md` et `contexte/niveau-de-confiance.md`.
3. Dépose dans `_inbox/` ce que tu as déjà : ta grille tarifaire, ton règlement, la liste de tes
   membres exportée de ton logiciel (un fichier Excel ou CSV suffit), quelques réponses types.
   Dis : « traite l'inbox ».
4. Termine par `EOS`.

Si tu n'arrives pas à brancher ta boîte mail, ce n'est pas bloquant : dépose les messages à
traiter dans `_inbox/` (un copier-coller du texte ou une capture d'écran suffit).

## Étape 1 — Observation (deux semaines)

Objectif : Claude apprend tes demandes et ta façon d'y répondre, sans rien envoyer.

- Chaque matin : « point du matin ». Tu reçois tes rendez-vous du jour, les demandes en attente
  et les relances à faire.
- Deux ou trois fois par semaine : « trie mes mails ».
- Les messages Instagram et WhatsApp : fais une capture d'écran, dépose-la dans `_inbox/`.
- Une fois par semaine : « regarde comment j'ai répondu cette semaine et note ma façon de faire ».

## Étape 2 — Brouillons (une à deux semaines)

Objectif : Claude rédige, tu décides.

- Dans `contexte/niveau-de-confiance.md`, passe la catégorie « demande d'essai » au niveau 2,
  puis 3.
- « réponds à ce prospect » : Claude prépare la réponse avec tes vrais créneaux et tarifs.
- « qui je dois relancer ? » : Claude liste les essais sans suite, les membres absents depuis
  trois semaines et les abonnements qui se terminent, avec un brouillon pour chacun.
- Quand tu modifies un brouillon avant de l'envoyer, dis : « compare ton brouillon et ce que j'ai
  envoyé ». La leçon est notée.

## Étape 3 — Production (en continu)

- « prépare une séance pour le groupe du mardi » ou « pour Julie, reprise après entorse ». Claude
  s'appuie sur `contexte/methode.md` (ta méthode, tes exercices) et sur le dossier du membre.
- « prépare mes posts de la semaine ». Claude part de ce qui s'est passé au club et te propose
  trois à cinq publications. Tu ajoutes tes photos et tu publies toi-même.
- Le vendredi : « bilan de la semaine ».
- Pour un contenu important (page d'offre, règlement, programme payant) : « fais relire par un
  panel ». Plusieurs relecteurs fictifs notent le texte jusqu'à ce qu'il soit bon.

## Étape 4 — Mode avancé

Ouvre `automatisations/README.md` quand les étapes 1 à 3 tournent depuis au moins un mois. Tu y
trouveras, dans l'ordre : la réservation en ligne sans rien programmer, puis les rappels et
alertes automatiques. Ne commence pas par là : une automatisation mal réglée envoie de mauvais
messages à tes membres sans que tu le voies.

## Les pièges

- **Vouloir tout brancher le premier jour.** Une tâche, puis la suivante.
- **Expliquer comment faire.** Dis ce que tu veux obtenir.
- **Corriger sans le dire.** Si tu modifies un brouillon en silence, Claude refera la même erreur.
- **Laisser `contexte/offre-et-tarifs.md` vieillir.** Claude répond avec ce fichier. Quand un
  tarif ou un horaire change, dis-le-lui le jour même.
- **Noter trop d'informations de santé.** Seulement ce qui sert à adapter les séances.
