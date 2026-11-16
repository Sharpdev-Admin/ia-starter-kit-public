# Principes — douze règles pour travailler avec Claude

Ces règles sont aussi écrites, en anglais, dans `CLAUDE.md`, le fichier que Claude lit à chaque
session. Tu n'as pas à les retenir : Claude les applique. Elles sont ici pour que tu saches
pourquoi il se comporte ainsi.

## 1. Rien ne se perd

Chaque fois que tu recadres Claude, chaque recette qui marche, chaque réponse que tu as corrigée
est sauvegardée dans ce dossier. Sinon tu répètes quinze fois la même chose à un stagiaire qui
oublie.

## 2. Ce dossier est un bac à sable

Tu commences avec un seul dossier, celui-ci. Tu peux le jeter et recommencer. Si tu as plusieurs
activités, tu les sépareras plus tard, quand tu sauras ce qui est commun.

## 3. Tu déposes, Claude range

`_inbox/` reçoit tout ce qui est brut : mails, PDF, captures d'écran d'Instagram ou de WhatsApp,
exports de ton logiciel de réservation. Tu ne ranges rien toi-même.

## 4. Tout devient une fiche courte avant d'être traité

Un mail ou un PDF devient d'abord une fiche de quelques lignes. Claude la lit avec son modèle le
moins coûteux. Ensuite il relit la fiche, pas le document d'origine. C'est ce qui évite d'épuiser
ton abonnement à relire quinze fois le même PDF.

## 5. Une fiche par document, une fiche par personne, sans copie

La fiche d'un membre renvoie vers ses documents, elle ne les recopie pas. Pour répondre à « quels
membres ont une blessure au genou ? », Claude parcourt les fiches.

## 6. La confiance se gagne par paliers

| Niveau | Claude peut | Claude ne peut pas |
|---|---|---|
| 1 | trier, ranger, créer des fiches, te faire un rapport | écrire une réponse |
| 2 | préparer des brouillons sans destinataire | envoyer |
| 3 | préparer des brouillons avec le destinataire ; tu cliques « Envoyer » | envoyer |
| 4 | envoyer, pour les catégories que tu as listées | envoyer autre chose, supprimer |

Toi seul décides d'un changement de niveau : tu le dis à Claude, il répète ce qui va changer,
attend ton oui et le note dans `contexte/niveau-de-confiance.md`. Il ne te le propose jamais.

## 7. Des employés spécialisés, pas un chef d'orchestre

Claude utilise plusieurs petits assistants : un qui lit les mails, un qui rédige les réponses, un
qui prépare les séances. Quatre petits assistants vont plus vite qu'un gros qui fait tout.

## 8. Tu dis quoi obtenir, pas comment

Donne le résultat attendu, le contexte et les limites. Laisse Claude trouver la méthode.

## 9. Claude apprend ta façon de répondre

Pendant les premières semaines, il compare ce que tu envoies avec ce qu'il aurait écrit. Quand tu
modifies un brouillon, il cherche pourquoi et note la leçon.

## 10. Une recette se suit en entier

Si Claude saute des étapes trois fois et se trompe la quatrième, tu repars de zéro. Si une
recette est mauvaise, on la corrige, on ne la contourne pas.

## 11. Fin de session : « EOS »

Tu écris `EOS`. Claude liste ce qu'il a fait, ce que tu as corrigé, et te propose les leçons une
par une. Il ne garde que celles que tu approuves.

## 12. Rien d'irréversible sans toi

Envoyer un message, supprimer un fichier, annuler une réservation, publier : Claude prépare et te
demande. Il ne t'écrit jamais « donne-moi ton mot de passe » : il t'indique quel fichier créer
dans `secrets/`.
