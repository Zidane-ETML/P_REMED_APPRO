# Planar

Une application Web pour planifier les arbitrages dans des championnats sportifs.

Tout sport, pratiqué à un niveau de compétition, qu'il soit requièrent la présence d'un ou plusieurs arbitres pour diriger les matchs.
Il est courant que les clubs impliqués dans les compétitions, fournissent des arbitres pour arbitrer les matchs, d'autres clubs naturellement.
L'organisation des matchs est de la présence du ou des arbitres, un challenge de taille auquel l'application Planard s'attaque.

## Concepts

1. Un match est caractérisé par un état, qui est un parmi:
   - **Brouillon**: Il est dans le système, mais il n'est visible et éditable que par la fédération
   - **Ouvert**: Il est visible pour les arbitres et il reste des places d'arbitrage à prendre
   - **Planifié**: Les arbitres sont connus, le match est prêt pour être joué
   - **Terminé**: Le match a été joué et arbitré
   - **Raté**: Le match n'a pas été validé en raison d'un problème d'arbitre
   - **Annulé**: Le match n'a pas eu lieu (ou n'aura pas lieu), mais pas pour un problème d'arbitre
   - **Déplacé**: Le match était planifié, mais sa date, heure ou lieu a changé. Les arbitres doivent confirmer ou se désinscrire
   - **Attente** de validation
  
2. Le **nombre brut** de matchs qu'un club doit arbitrer est égal au nombre de matchs que chaque équipe du club joue multiplié par le nombre d'arbitre par match et divisé par deux, le résultat est arrondi vers le haut.
   - Exemple : le VBC Pétaouchnok a cinq équipes:
        1. Juniors U18, qui joue 18 matches et où il faut 1 arbitre par match
        2. Juniors U21, qui joue 22 matches et où il faut 2 arbitres par match
        3. Féminine 1ère ligue, qui joue 24 matches et où il faut 4 arbitres par match
        4. Masculine 2ème ligue, qui joue 18 matches et où il faut 3 arbitres par match
        5. Vétérans, qui joue 18 matches et où il faut 1 arbitre par match
   
      VBC Pétaouchnok doit donc arbitrer: ((18 * 1) + (22 * 2) + (24 * 4) + (18 * 3) + (18 * 1)) / 2 = 105 matches

3. Le **quota** de matchs est le nombre brut modifié en fonction des responsabilités que les clubs assument dans la fédération (ou pas).  
   Ainsi, dans l'exemple ci-dessus, si le caissier de la fédération est associée au VBC Pétaouchnok, ce dernier bénéficie d'une remise de 5 matches et son quota de match se monte dès lors à 100.  
   Les matches soustraits aux clubs sont répartis le plus uniformément possible sur les autres clubs.

4. Chaque arbitre a un nombre de **matchs dûs**, c'est-à-dire le nombre de matchs qu'il doit encore arbitrer dans la saison. 
   Ce nombre n'est pas contrôlé par la fédération, mais par le club, responsable de répartir ses arbitrages parmi ses arbitres.

5. Lorsqu'un club a atteint son quota de matchs (planifiés ou terminés), ses arbitres peuvent continuer à s'inscrire pour des matchs, mais ils doivent le faire pour le compte d'un autre club. On parle alors de **délégation d'arbitrage**.  
   Les délégations d'arbitrage sont payantes. Le club qui délègue paye l'autre club 50.- (TBD), lequel décide selon son règlement de rétribuer l'arbitre ou pas.  
   Les délégations doivent être validées par le club qui délègue.  
   Le nombre de délégations qu'un club peut prendre (=facturer) est limité.
    >Exemple:  
    >Rodrigo arbitre pour le VBC Pétaouchnok, qui a rempli son quota et qui peut encore prendre des délégations.  
    >Il s'inscrit au nom du VBC Chaudeville pour arbitrer un match qui n'implique ni le VBC Chaudeville, ni le VBC Pétaouchnok.  
    >Le VBC Chaudeville, en manque d'arbitres, accepte la délégation.  
    >On dira alors que le VBC Chaudeville a délégué l'arbitrage d'un match au VBC Pétaouchnok.  
    >Rodrigo arbitre le match  
    >En fin de saison, le VBC Chaudeville verse 50.- au VBC Pétaouchnok, lequel - sympa - reverse 20.- à Rodrigo

   Ce concept a pour buts:
   - Ne pas laisser de match sans arbitre: s'il reste des matchs ouverts que les clubs qui n'ont pas leur quota ne peuvent pas arbitrer, les autres seront intéressés à les prendre
   - Eviter qu'un club ou arbitre prenne trop d'arbitrage, privant les autres clubs de la possibilité de remplir leur quota
   - Si chaque club arbitre son quota de matchs, tous les matchs sont arbitrés et aucun club ne débourse un franc supplémentaire.
   - Motiver les clubs à former des arbitres, cela peut leur rapporter
   - Permettre aux clubs qui n'arrivent pas à trouver des arbitres de (plus ou moins) choisir où va l'argent des délégations qu'ils payent

6. La fédération qui utilise Planar organise plusieurs championnats de niveau différents. Pour arbitrer un match dans une compétition d'un certain niveau, il faut également que l'arbitre et un niveau adéquat.

## Données

Un championnat est caractérisé par :
 - Un titre
 - Un niveau
 - Un nombre maxi maximum d'équipe
 - Une date de début une date de fin
 - Le nombre d'arbitre(s) requis à chacun de ses matchs

Chaque match est caractérisé par :
- Un numéro
- Une équipe recevante
- Une équipe visiteuse
- Une date
- Une heure
- Un lieu

Chaque match est associé à un championnat.  
Zéro, un ou plusieurs arbitres sont associés à un match

Un club est caractérisé par :
 - Un nom
 - Le nombre maximum de délégation qu'elle peut effectuer

Un ou plusieurs utilisateurs de Planar sont associés au club en temps que représentant.

Une équipe est caractérisée par :
  - Un nom
  - Un niveau

Elle est associée à un club  
Elle est associée (inscrite) à zéro ou un championnat

Un utilisateur de Planar est caractérisé par :
- Prénom
- Nom
- Année de naissance
- Numéro de téléphone

Chaque utilisateur est lié à un seul club au maximum.  
Un utilisateur sans club a forcément le rôle Admin

Un arbitre est un utilisateur caractérisé en plus par :
- Numéro de licence
- Niveau
- Le nombre de matchs qu'il doit arbitrer (dûs)

Les rôles connus sont :
- Admin
- Arbitre
- Représentant de club

## Fonctionnalités

### Gérer les clubs
En tant que fédération, je veux gérer la liste des clubs affiliés

### Gérer les championnats
En tant que fédération, je veux gérer la liste des championnats que j'organise  
En tant que fédération, je veux inscrire/désinscrire une équipe à un championnat  
En tant que fédération, je veux saisir la liste de tous les matchs d'un championnat  
En tant que fédération, je veux définir le nombre d'arbitres (et leur niveau) nécessaires pour les matchs de chaque championnat  

### Gérer les équipes
En tant que responsable d'un club, je veux pouvoir gérer la liste des équipes de mon club  

### Gérer les utilisateurs
En tant que fédération, je veux pouvoir gérer la liste des arbitres  
En tant que fédération, je veux assigner un ou plusieurs rôles à un utilisateur de planar  

### Générer les quotas des clubs
En tant que fédération, je veux définir les fonctions qui comptent pour des arbitrages  
En tant que fédération, je veux effectuer le calcul des quotas après avoir créé tous mes championnats

### Répartir les arbitrages d'un club
En tant que responsable de club, je veux définir le nombre de match à arbitrer pour chacun de mes arbitres, afin de m'assurer que le quota de mon club est atteignable  

### Gérer les inscriptions d'arbitrage aux matchs
En tant qu'arbitre, je veux voir la liste des matchs que je pourrais arbitrer  
  - En fonction des matchs disponibles, de mon club, du nombre de matchs déjà arbitrés par mon club et de mon niveau  

En tant qu'arbitre, je veux m'inscrire pour un match  
En tant qu'arbitre, je veux m'inscrire pour un match au nom d'un autre club  
En tant que responsable de club, je veux accepter ou rejeter une demande de délégation d'arbitrage  

### Faire le point de la situation
En tant qu'arbitre, je veux voir l'état de ma saison en cours
  - Tous les matchs qui me concernent
  - Mon nombre de matchs dûs
  - Le status de mon club  
  
En tant que représentant de club, je veux voir les matchs qui ont été - ou vont être - arbitrés par des arbitres de mon club  
En tant que fédération, je veux une vue calendrier pour un championnat, pour avoir une vue d'ensemble des manques d'arbitre éventuel
  - Chaque match est colorisé en fonction de son état
