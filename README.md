# Claude Starter Kit — édition sport

Un dossier prêt à l'emploi qui sert de « cerveau » à Claude pour gérer ton activité sportive :
club, salle, studio, coaching individuel ou en petit groupe. Tu l'installes une fois, puis Claude
le nourrit lui-même au fil des semaines.

Tu n'as pas besoin de savoir coder. Tu parles à Claude en français, comme à un stagiaire.

## Ce que le kit fait pour toi

| Ton quotidien | Ce que Claude fait | Comment tu le demandes |
|---|---|---|
| Les demandes arrivent par mail, formulaire, Instagram, WhatsApp | Trie, résume, te dit ce qui est urgent | « trie mes mails » |
| Un prospect demande une séance d'essai | Prépare la réponse dans ton style, avec tes vrais tarifs et créneaux | « réponds à ce prospect » |
| Tu ne sais plus qui relancer | Liste les essais sans suite, les membres absents, les abonnements qui se terminent | « qui je dois relancer ? » |
| Le lundi matin, tu ne sais pas par où commencer | Te donne le point du jour : rendez-vous, relances, échéances | « point du matin » |
| Tu dois préparer une séance ou un cycle | Construit la séance à partir de ta méthode et du dossier du membre | « prépare une séance pour… » |
| Tu n'as pas le temps de publier | Écrit les publications de la semaine à partir de ce qui s'est vraiment passé au club | « prépare mes posts de la semaine » |
| Tu ne regardes jamais tes chiffres | Fait le bilan : nouveaux, départs, essais convertis, à encaisser | « bilan de la semaine » |
| Tu réexpliques toujours la même chose | Retient chaque correction | « EOS » en fin de session |

## Les trois règles du kit

1. **Rien de ce que tu apprends à Claude n'est perdu.** Chaque correction et chaque recette qui
   marche est sauvegardée dans ce dossier.
2. **La confiance se gagne par paliers.** D'abord Claude trie. Puis il rédige des brouillons que
   tu envoies toi-même. Il n'envoie quelque chose que si tu le décides, catégorie par catégorie.
3. **On commence petit.** Une seule tâche, celle qui te prend le plus de temps. On étend ensuite.

## Installation (environ une heure)

1. Prends un abonnement Claude Pro : https://claude.ai/upgrade
2. Crée un compte GitHub gratuit : https://github.com/signup
3. Copie le kit : ouvre https://github.com/Sharpdev-Admin/ia-starter-kit-public, clique
   « Use this template », puis « Create a new
   repository », et choisis **Private**. N'utilise pas « Fork » : une copie faite avec « Fork »
   est publique, et tes mails et tes fiches membres seraient visibles par tout le monde.
4. Ouvre https://claude.ai/code, autorise GitHub et choisis ta copie du kit.
5. Colle le texte de `PROMPT-INSTALLATION.md` comme premier message. Claude te pose une vingtaine
   de questions et se configure.
6. Facultatif, plus tard : brancher ta boîte mail et ton agenda
   (https://claude.ai/settings/connectors). Pour commencer, tu joins simplement les messages à
   traiter dans la conversation.

Ensuite, suis `GUIDE-DEMARRAGE.md` : il donne le plan semaine par semaine.

## Ce qu'il y a dans le dossier

| Dossier ou fichier | À quoi ça sert |
|---|---|
| `GUIDE-DEMARRAGE.md` | Le plan sur six semaines. Commence par là. |
| `PRINCIPES.md` | Les règles de fonctionnement, expliquées. |
| `contexte/` | Qui tu es, ton offre, tes tarifs, ton planning, ta façon de répondre, l'autonomie accordée à Claude. Rempli avec Claude à l'installation. |
| `_inbox/` | Tu y déposes tout ce qui est brut : mails, PDF, captures d'écran, exports. Claude range. |
| `ressources/` | Une fiche courte par mail ou document reçu. |
| `dossiers/` | Une fiche par membre, prospect, fournisseur ou partenaire. |
| `seances/` | Les séances et cycles que Claude prépare avec toi. |
| `contenus/` | Les publications et messages préparés, semaine par semaine. |
| `automatisations/` | Le mode avancé : réservation en ligne, rappels, alertes. À ouvrir quand le reste tourne. |
| `tasks/lessons.md` | Ce que Claude a appris de tes corrections. |
| `secrets/` | Tes identifiants. Ce dossier n'est jamais envoyé sur GitHub. |

## Données de tes membres — à lire avant d'installer

Ce dossier contient des informations personnelles : noms, coordonnées, historique. Il passe par
deux services, GitHub et Claude. Cinq règles :

1. **Ce kit est fait pour une activité sportive.** Si tu es soignant, psychologue ou avocat, ne
   l'utilise pas pour des données de patients ou de clients : le secret professionnel ne le
   permet pas en l'état.
2. **Ta copie reste privée**, avec la double authentification activée sur GitHub.
3. **Coupe le réglage d'entraînement de Claude** avant de commencer :
   https://claude.ai/settings/data-privacy-controls — désactive l'utilisation de tes
   conversations pour améliorer le modèle.
4. **Santé : le moins possible.** Tu ne notes qu'une consigne utile à la séance (« pas de
   saut »), jamais un diagnostic, et seulement si la personne t'a donné son accord par écrit.
   Rien sur un mineur sans l'accord de son responsable légal.
5. **Effacer n'est pas immédiat.** Quand un membre te demande de supprimer ses données, dis à
   Claude « supprime le dossier de … » : il te montre ce qu'il retire et attend ton accord. Les
   fichiers disparaissent, mais l'historique du dépôt garde les anciennes versions : pour un
   effacement complet, demande à la personne qui t'accompagne de purger l'historique.

Préviens tes membres par écrit que tu utilises ces outils. Ce kit ne remplace pas l'avis d'un
juriste sur tes obligations.
