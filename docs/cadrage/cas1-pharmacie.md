# Fiche de cadrage : Ordonnances incomplètes en pharmacie

> Remplir chaque rubrique en une à trois phrases. Les rubriques marquées (obligatoire) sont vérifiées par `pytest`.

## Besoin en une phrase (obligatoire)

Signaler automatiquement, avant la délivrance, les ordonnances auxquelles il manque une mention obligatoire (identité du patient, date, posologie, signature ou identifiant du prescripteur, etc.).

## Utilisateur final (obligatoire)

Le pharmacien et son équipe au comptoir, qui voient une alerte précise (« posologie absente ») avant de délivrer le médicament.

## Approche retenue (obligatoire)

Cocher une seule case :

- [x] Règles métier
- [ ] Machine learning
- [ ] RAG
- [ ] Modèle génératif seul

## Justification (obligatoire, citer au moins deux critères de la grille : (a) données étiquetées, (b) vérifiabilité, (c) coût par requête, (d) conséquence d'une erreur)

(a) Au départ, aucune ordonnance n'est étiquetée « complète » ou « incomplète » : un modèle de machine learning n'aurait rien pour apprendre. (b) La liste des champs obligatoires est connue, stable et fixée par la réglementation : un contrôle par règles est explicable, le pharmacien voit exactement quelle mention manque et peut la vérifier. (d) Une ordonnance validée à tort peut conduire à une erreur de délivrance aux conséquences graves pour le patient, ce qui impose un outil prévisible et auditable.

## Données nécessaires et leur origine (obligatoire)

Une liste des mentions obligatoires validée par un pharmacien responsable (texte réglementaire) ; pour les tests, des ordonnances fictives ou entièrement anonymisées, rédigées à la main ou fournies par la pharmacie après suppression de toute donnée d'identification. Aucune donnée réelle de patient dans le cadre du cours.

## Métrique de succès et seuil d'acceptation (obligatoire)

Rappel sur la classe « ordonnance incomplète » : seuil d'acceptation de 0,98 sur un jeu de test d'ordonnances fictives où les manques ont été placés volontairement, avec zéro champ obligatoire manquant non détecté sur les cas critiques (posologie, patient). La précision est secondaire : une fausse alerte coûte quelques secondes, un oubli non détecté coûte cher.

## Conséquence d'une erreur et validation humaine prévue (obligatoire)

Une ordonnance incomplète validée à tort peut provoquer un mauvais dosage ou une délivrance non conforme, avec un risque pour la santé du patient. L'outil ne fait donc qu'alerter : la décision finale de délivrer reste toujours au pharmacien, qui contrôle chaque ordonnance, alerte ou non.

## Risques éthiques ou de confidentialité (obligatoire)

Les ordonnances sont des données de santé, parmi les plus sensibles : traitement local, hébergement conforme à la réglementation sur les données de santé, accès restreint et journalisé, pas d'envoi à un service tiers, minimisation des données conservées. Aucune donnée réelle n'est utilisée dans le cours ; il faut aussi éviter que l'alerte donne au pharmacien une fausse confiance quand elle ne se déclenche pas.

## Approche écartée et pourquoi (facultatif)

Machine learning : écarté pour l'instant faute de jeu étiqueté. Il pourrait être envisagé plus tard, une fois constitué un corpus annoté par des pharmaciens (par exemple pour lire des ordonnances manuscrites), en gardant les règles et la validation humaine comme garde-fou. Génératif seul : écarté car il pourrait « deviner » une mention absente ou en inventer une.
