# Fiche de cadrage : Priorisation des avis négatifs

> Remplir chaque rubrique en une à trois phrases. Les rubriques marquées (obligatoire) sont vérifiées par `pytest`.

## Besoin en une phrase (obligatoire)

Repérer automatiquement parmi des milliers d'avis clients ceux qui sont négatifs afin que l'équipe du site e-commerce traite en premier les plus urgents.

## Utilisateur final (obligatoire)

L'équipe du service client et de la qualité du site e-commerce, qui reçoit une liste d'avis triée par priorité au lieu de tout lire.

## Approche retenue (obligatoire)

Cocher une seule case :

- [ ] Règles métier
- [x] Machine learning
- [ ] RAG
- [ ] Modèle génératif seul

## Justification (obligatoire, citer au moins deux critères de la grille : (a) données étiquetées, (b) vérifiabilité, (c) coût par requête, (d) conséquence d'une erreur)

(a) Les avis s'étiquettent facilement : on peut partir de la note en étoiles puis faire relire un échantillon à la main, et les données existent déjà en grand nombre. (c) Des milliers d'avis par jour : un classifieur classique coûte presque rien par requête, alors qu'un modèle génératif coûterait à chaque appel. (d) Un avis mal classé a une conséquence faible : il sera simplement lu un peu plus tard ou trop tôt par l'équipe.

## Données nécessaires et leur origine (obligatoire)

Les avis clients du site (texte et note en étoiles), exportés depuis la base du site ; un échantillon étiqueté positif, neutre ou négatif par relecture humaine pour corriger les cas où la note ne correspond pas au texte. Un petit exemple se trouve dans data/sample_reviews.csv.

## Métrique de succès et seuil d'acceptation (obligatoire)

Rappel sur la classe négative, avec un seuil d'acceptation de 0,90 sur un jeu de test tenu à l'écart : il vaut mieux relire quelques avis de trop que de manquer un avis négatif. On suivra aussi le F1 macro comme mesure d'ensemble.

## Conséquence d'une erreur et validation humaine prévue (obligatoire)

Un avis négatif manqué est lu en retard, ce qui peut retarder la réponse au client ; un avis positif classé négatif fait perdre quelques minutes. L'impact est faible : l'équipe garde la main, peut reclasser un avis en un clic, et ces corrections alimentent le réentraînement. Un échantillon est relu chaque semaine.

## Risques éthiques ou de confidentialité (obligatoire)

Les avis peuvent contenir des noms, adresses e-mail ou numéros de commande : les supprimer avant l'entraînement et ne pas stocker de données personnelles inutiles. Attention aux biais (langues, argot, ironie mal comprise) et à l'usage des scores : ils servent à prioriser, jamais à sanctionner un client ou à masquer des avis.

## Approche écartée et pourquoi (facultatif)

Règles par mots-clés : écartées car trop fragiles (ironie, négations, formulations imprévues). Modèle génératif seul : écarté pour son coût à chaque avis et parce qu'on ne peut pas mesurer simplement son rappel.
