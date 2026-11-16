# Palier B — Une alerte sur ton téléphone à chaque réservation

> **État : spécification.** Le modèle de scénario Make à importer n'est pas encore construit ni
> testé. Ne suis pas cette fiche seul tant que ce bandeau est là.

**Résultat :** quand quelqu'un réserve ou annule, tu reçois dans la minute un message Telegram :
prénom, créneau, téléphone.

**Pourquoi celle-ci en premier :** si elle tombe en panne, tu ne perds rien. Le mail de Cal.com
continue d'arriver. Elle n'écrit à aucun membre.

## Ce qu'il faut

| Compte | Coût | Sert à |
|---|---|---|
| Cal.com (palier A) | 0 € | envoie l'événement « réservation créée » ou « annulée » |
| Make | 0 € : l'offre gratuite autorise deux scénarios actifs | reçoit l'événement et fabrique le message |
| Telegram | 0 € | t'affiche le message |

## Le scénario (identique pour réservation et annulation)

1. Webhook Make : reçoit l'appel de Cal.com.
2. Contrôle : la signature est la bonne et le type d'événement est celui attendu ; sinon arrêt.
3. Mise en forme : prénom, date et heure en clair (fuseau Europe/Bruxelles ou Paris), téléphone.
4. Telegram : envoi du message dans ta conversation avec ton robot.

## Ce que tu auras à régler (et rien d'autre)

- l'adresse du webhook Make, à coller dans l'écran « Webhooks » du type d'événement Cal.com ;
- le secret de signature, la même valeur dans Cal.com et dans Make, **Cal.com d'abord** ;
- ton robot Telegram (créé avec BotFather) et l'identifiant de ta conversation.

Aucune de ces valeurs ne s'écrit dans la conversation avec Claude ni dans un fichier hors de
`secrets/`.

## Les pannes connues (relevées sur une installation réelle)

| Symptôme | Cause | Quoi faire |
|---|---|---|
| Plus aucune alerte, d'un coup | le scénario s'est désactivé après des erreurs répétées | rouvrir Make, lire la dernière erreur, réactiver |
| Alerte pour une réservation qui n'existe pas | signature non activée : n'importe qui connaissant l'adresse peut appeler | activer le secret de signature |
| Heure décalée d'une ou deux heures | fuseau horaire non réglé dans la mise en forme | fixer le fuseau dans le scénario |

## Reste à faire avant de retirer le bandeau

- [ ] construire les deux scénarios dans un compte Make de démonstration ;
- [ ] les exporter et vérifier qu'un import dans un compte vierge ne demande que les trois
      réglages ci-dessus ;
- [ ] faire suivre cette fiche par une personne qui n'a jamais ouvert Make, et chronométrer ;
- [ ] ajouter les captures d'écran de chaque étape.
