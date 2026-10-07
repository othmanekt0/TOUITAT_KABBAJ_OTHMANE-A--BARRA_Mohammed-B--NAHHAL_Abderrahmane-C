# Fiche de cadrage : Questions sur le règlement intérieur

> Remplir chaque rubrique en une à trois phrases. Les rubriques marquées (obligatoire) sont vérifiées par `pytest`.

## Besoin en une phrase (obligatoire)

Permettre aux élèves, étudiants et parents de poser en langage naturel une question sur le règlement intérieur de l'école et d'obtenir une réponse qui cite l'article concerné.

## Utilisateur final (obligatoire)

Les élèves, les étudiants et les parents, ainsi que l'administration qui répond aujourd'hui à ces questions à la main.

## Approche retenue (obligatoire)

Cocher une seule case :

- [ ] Règles métier
- [ ] Machine learning
- [x] RAG
- [ ] Modèle génératif seul

## Justification (obligatoire, citer au moins deux critères de la grille : (a) données étiquetées, (b) vérifiabilité, (c) coût par requête, (d) conséquence d'une erreur)

(b) La réponse doit être vérifiable : elle doit citer l'article et le passage officiel du règlement, que l'utilisateur peut relire. Un modèle génératif seul inventerait des règles ou des articles qui n'existent pas. (a) Il n'existe pas de questions étiquetées au départ, ce qui écarte le machine learning supervisé, alors que les documents du règlement existent déjà et peuvent être indexés. (c) Quelques dizaines de questions par jour : le coût par appel d'un modèle reste acceptable.

## Données nécessaires et leur origine (obligatoire)

Le règlement intérieur officiel de l'école (PDF ou document source), découpé par article et indexé avec sa version et sa date ; un jeu d'une vingtaine de questions rédigées avec l'administration, accompagnées de l'article attendu, pour évaluer le système.

## Métrique de succès et seuil d'acceptation (obligatoire)

Taux de réponses correctes avec citation exacte de l'article sur un jeu de 20 questions : seuil d'acceptation de 90 % (18 sur 20). Chaque réponse sans source ou hors règlement doit répondre « je ne sais pas, contactez l'administration ».

## Conséquence d'une erreur et validation humaine prévue (obligatoire)

Une réponse fausse peut faire croire à un élève qu'une règle l'autorise ou l'oblige à tort, et mener à une sanction ou à un conflit avec l'école ; la gravité est moyenne. La réponse affiche toujours l'article cité avec un lien vers le texte officiel, précise qu'elle est indicative, et les cas sensibles (sanctions, litiges) sont renvoyés à l'administration.

## Risques éthiques ou de confidentialité (obligatoire)

Le règlement est un document public, mais les questions peuvent révéler des situations personnelles (sanction, santé, famille) : ne pas conserver l'identité de l'utilisateur, ne pas enregistrer les questions au-delà de ce qui sert à l'amélioration, et informer clairement qu'il s'agit d'un assistant automatique. Prévoir la mise à jour de l'index à chaque nouvelle version du règlement.

## Approche écartée et pourquoi (facultatif)

Modèle génératif seul : écarté parce qu'il invente des articles et ne peut pas être vérifié. Règles métier : écartées car les questions sont trop variées pour des mots-clés, et le règlement change d'une année à l'autre.
