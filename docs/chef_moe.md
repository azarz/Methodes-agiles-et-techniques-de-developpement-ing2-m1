S'enregistrer sur Gitlab ([http://gitlab-ing2.ensg.eu/](http://gitlab-ing2.ensg.eu/))

### Actions initiales

- Créer le dépôt du projet. [:material-help:aide](gitlab/project.md#creation-du-projet)
- Ajouter tous les développeurs et développeuses, les devops et le product owner dans le projet (avec les rôles adéquats) [:material-help:aide](gitlab/project.md#ajout-de-membres)
- Mise en place du board Kanban sur le projet (Projet > Issues > Board) : créer un board avec comme colonnes : à faire, en cours, à tester, terminé

Sur son poste, réinitaliser le proxy pour git :
```bash
git config --global http.proxy ""
```

### Actions récurrentes

#### Validation des merge requests

Lorque les développeurs et développeuses soumettent une merge request (MR) sur `main`, valider le fonctionnement sur son ordinateur et réaliser la fusion sur `main`. Supprimer la branche qui a été fusionnée.
[:material-help:aide](gitlab/mr.md#accepter-une-merge-request)

#### Création de versions de production

Sur demande par le ou la Product Owner, tagger la version déployée de préproduction (dernier commit sur `main`) `vX.Y.Z` (ex: `v0.0.1`). Attention à bien tagguer la version demandée par le ou la PO (des MR ont pu être fusionnées sur main entre temps...). [:material-help:aide](gitlab/tag.md#creation-de-tag)

#### Attribution des tickets

* Attribuer les tickets créés par les utilisateurs aux développeurs ciblés pour le développement. [:material-help:aide](gitlab/issues.md#changer-lassignation-dun-ticket)
* Inspecter et mettre à jour le board (Kanban) du projet -> Projet > Issues > Board

##### Cycle d'assignation d'un ticket :

- L'utilisateurice crée le ticket et l'assigne au/à la PO
- Le ou la PO assigne le ticket au/à la chef·fe d'équipe MOE
- Le ou la chef·fe d'équipe MOE assigne le ticket au membre d'équipe ciblé pour le développement
- Une fois le dévelopement fait et la MR faite, le membre d'équipe assigne le ticket au/à la chef·fe d'équipe.
- Une fois la MR mergée, le ou la chef·fe d'équipe assigne au/à la PO pour vérification du traitement du ticket.
- Le ou la PO assigne éventuellement au client qui a créé le ticket pour qu'il ou elle fasse la vérification.

#### Discussion avec le PO

Au cours des réunions inter-sprints, planifier les tâches avec le ou la PO et éventuellement demander des éclaircissements sur les tickets posant problème à l'équipe.
