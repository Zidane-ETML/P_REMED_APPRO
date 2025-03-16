# Suivi des activités

## 31.1

- Feedback XCL
    - J'ai besoin de savoir si vous avez eu NA dans un module de pratique et si oui lequel
    - Je choisis un sujet par défaut: le démineur (voir sur Marketplace), dans lequel les objectifs minimaux à atteindre sont:
        1. La grille de 10x10 s'affiche et je peux déplacer le curseur de case en case sans sortir avec les flèches du clavier
        2. Il y a 5 mines cachées. Quand je fais ENTER dans une case, elle devient verte s'il n'y a pas de mine à cet endroit, rouge dans le cas contraire
        3. L'utilisateur peut choisir le nombre de mines cachées. Le programme les place aléatoirement, en assurant que deux mines ne se trouvent pas dans la même case
        4. L'utilisateur peut choisir la taille de la grille 
    - Si ce sujet vous convient: faites un contrat avec (de remédiation ou d'approfondissement)
    - S'il ne vous convient pas, proposez-moi un sujet et rédigez un autre contrat
    - Dans un cas comme dans l'autre, vous devez avoir un contrat signé avant la pause de 14h45
    
- Journal de travail
    - Nous avons trouver un projet pour la remdédiation
    - J'ai fait le contrat de remédiation et l'a fait validé et signer
    - Vous m'avez expliqué le projet plus en détail 
    - J'ai commencer à rédiger un cahier des charges et vous m'aviez dit qu'il ne fallait pas faire ça
    - J'ai commencer à revoir la theorie du MCD/MLD, normalisation
    - J'ai installer DrawIO et commencer à me familiariser avec

## 7.2

- Feedback XCL
    - Indiquez les durées des tâches dans votre journal de travail svp
    - J'ai uploadé les fichers de données en format Excel dans le repo. A analyser

- Journal de travail
    - ...

## 14.2



- Journal de travail
    - On a eu un problème avec Github on a passé 20 min à le résoudre
    - Ajout des cardinalitées
    - Ajout Associations
    - MCD terminé à faire valider

## 28.2

- Feedback XCL
    - Journal de travail: faites apparaître la durée des tâches
    - Le MCD semble bon à première vue, il faut que je le regarde de plus près
    - Mais vous pouvez déjà commencer à faire le document final demandé

- Journal de travail
    - Commencement du MLD (30min)
    - MCD validé par mr.Carrel (10min)
    - Revoir la théorie "passage MCD -> MLD" (30min)
    - Mettre des flèches (10min)
    - Ajout de foreign_key (20min)
    - ajout de 2 association "jouer" -> "jouer à domicile" , "jouer à l'exterieur" (10min)


## 7.3

- Feedback XCL
    - Temps de travail: 3périodes = 135 min, temps dans le journal = 110 min. La différence est un peu trop grande
    - J'avais demandé de faire un bilan des objectifs, il n'a pas été fait
    - Le MLD devrait être de préférence en anglais
    - Demande spécifique de ma part: appliquez la convention très largement répandue suivante: 
        - La clé primaire de toutes les tables est un champ `id` (numérique autoincrémental)
        - Les clés étrangères se terminent par `_id`
    - Exemple d'utilisation SQL : `select * from user inner join group on user.group_id = group.id`
    - Cette convention est attendue par bon nombre de framework. Elle n'est donc pas contraire aux conventions ETML, qui autorisent de suivre une convention propre à une technologie
    - Nommage de commits: il est nécessaire maintenant d'améliorer ce point car il est insuffisant à ce stade

- Journal de travail
    - Explication de mr Carrel(10min)
    - Faire le bilan des objectifs(10min)
    - commit avec le bon nommage(5min)
    - Changement de convention pour les clé étrangères et primaires(15min)
    - Traduire toutes les tables et attributs en anglais(30min)
    - Revu avec mr Carrel et validation/finalisation du MLD(15min)
    - Commencement de la présentation(50min)

## 14.3

- Feedback XCL
    - Le MCD s'adresse à quelqu'un de non technique. Il vous faut éviter les termes informatiques et utiliser un langage le plus naturel possible. C'est le MLD qui montre comment les informations du MCD sont traduites en termes techniques. Formulez vos explications comme si vous vous adressiez à un ami qui est arbitre.
    - Journal et status OK

- Journal de travail
    - prise en compte du Feedback(5min)
    - Dernière consignes de mr Carrel(10min)
    - Ajout de la partie explication du MLD en anglais(20min)
    - Changement des explications du MCD(45min)
    - Ajout du script de base de données(15min)
 
# Conclusion

Le résultat est plutôt bon. Les points suivants de votre document devraient être amélioré pour qu'ils soit parfait.

- Commencer par une explication du problème que l'application veut résoudre. Il s'agit de ce qu'on appelle le "contexte métier".
- Il reste encore quelques erreurs dans le MLD, ce qui fait que le script généré est incorrect. Typiquement, les champs `homeTeam` et `awayTeam` ne sont pas les noms des équipes, mais des références sur la table `teams`. Gardez ça à l'esprit lorsque vous aborderez le sujet des clés étrangères dans un cours de base de données.
- Ce document est destiné à être intégré dans un rapport de projet. Il faudrait donc mentionner le fait que le script présenté a été généré par une IA sur la base des descriptions des champs du MLD.

Votre projet est validé. Rappelez-vous surtout que le MCD s'adresse plutôt aux personnes du métier de l'application et le MLD aux personnes de l'informatique. C'est pour ça que l'un est rédigé en français et l'autre anglais. Les explications que vous avez rajoutées sont bonnes, faites la même chose à l'avenir lorsque vous aurez des projets dans lesquels il vous faut documenter un modèle de données.
