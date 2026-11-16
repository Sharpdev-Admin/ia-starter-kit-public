---
type: <mail | message | document | facture | paiement | export | transcript | note | examen | autre>
date: <AAAA-MM-JJ — date de la source, pas du traitement>
source: <expéditeur, auteur, ou outil d'origine>
activite: <nom de l'activité concernée, tel qu'écrit dans contexte/activites.md>
personnes: [<slug du dossier>, ...]   # les dossiers/ concernés, par leur slug
original: <chemin relatif vers l'original, ou "non conservé", ou URL drive>
traite_le: <AAAA-MM-JJ — date où Claude a produit cette fiche>
categorie: <telle qu'écrite dans contexte/activites.md, ou "sans objet">
reponse_attendue: <oui | non | incertain>
urgence: <basse | normale | haute>
sens: <a-payer | a-encaisser | sans objet>   # pour une facture ou un paiement
montant: <nombre avec devise, ou "inconnu", ou "sans objet">
statut: <a-traiter | en-cours | fait | archive>   # a-traiter seulement si j'ai quelque chose à faire
---

# <Titre court et parlant>

## En deux lignes

<De quoi il s'agit, pour quelqu'un qui n'ouvrira pas l'original. 200 caractères maximum.>

## Faits clés

- <montant, date, référence, nom, échéance… une ligne par fait vérifiable>
- <…>

## Ce qui est demandé / à faire

- <la demande explicite, s'il y en a une, et pour qui>

## Contenu

<Pour un mail : le corps du message, nettoyé des signatures et citations répétées.
Pour un document : un résumé fidèle, section par section, avec les chiffres.
Pour une pièce jointe : son résumé ici, pas un lien vers un PDF à rouvrir.>

## Liens

- Dossier : `../../dossiers/<type>/<slug>.md` (fiche dans son dossier) ou `../dossiers/<type>/<slug>.md` (fiche seule)
- Fiches liées : `<chemin>`
