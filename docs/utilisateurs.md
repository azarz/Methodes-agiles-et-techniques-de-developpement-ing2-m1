S'enregistrer sur Gitlab ([http://gitlab-ing2.ensg.eu/](http://gitlab-ing2.ensg.eu/))

### Actions récurrentes

* Faire des demandes d'évolutions ou de correction : bien détaillées (un titre court mais explicite, une description précise), bien découpées (pas un ticket contenant un paquet d'évolutions ou corrections) via des tickets sur le projet Gitlab [:material-help:aide](gitlab/issues.md#creation-de-ticket)
* Dans les ticket : rédiger les critères d'acceptation utilisateur. Il s'agit des action à réaliser pour tester le bon fonctionnement du ticket. Très important car parmet de constituer le cahier de recette.
* Contrôler la version en préproduction et valider les évolutions
* Contrôler la version en production lors de demandes de corrections

#### Exemple de critère d'acceptation
Pour la recherche d’un ouvrage sur le site d’une médiathèque. Le ticket, dont le titre est « Consulter la fiche d’un ouvrage » se décrit comme :

  En tant qu’abonné de la médiathèque
  Je recherche un ouvrage en spécifiant son auteur, son titre ou sa référence
  Afin que l’emprunter ou de le réserver

Critères d’acceptation sous forme de liste :

  1. Résultat unique, afficher l’ouvrage : auteur/titre/reference
  2. Pas de résultat, inviter l’abonné à une nouvelle recherche
  3. Plusieurs résultats, afficher la liste des ouvrages triés par auteur
