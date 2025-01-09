S'enregistrer sur Gitlab ([http://gitlab-ing2.ensg.eu/](http://gitlab-ing2.ensg.eu/))

### Actions initiales

- Créer le dépôt du projet. [:material-help:aide](gitlab/project/#creation-du-projet)
- Ajouter tous les développeurs, le devops et le product owner dans le projet (avec les rôles adéquats) [:material-help:aide](gitlab/project/#ajout-de-membres)

### Actions récurrentes

#### Validation des merge requests

Lorque les développeurs soumettent une merge request (MR) sur `main`, valider le fonctionnement sur son ordinateur et réaliser la fusion sur `main`. Supprimer la branche qui a été fusionnée.
[:material-help:aide](gitlab/mr/#accepter-une-merge-request)

#### Création de versions de production

Sur demande du Product Owner, tagger la version déployée de préproduction (dernier commit sur `main`) `vX.Y.Z` (ex: `v0.0.1`). Attention à bien tagguer la version demandée par le PO (des MR ont pu être fusionnées sur main entre temps...). [:material-help:aide](gitlab/tag/#creation-de-tag)

#### Attribution des tickets

Attribuer les tickets créés par les utilisateurs aux développeurs ciblés pour le développement. [:material-help:aide](gitlab/issues/#changer-lassignation-dun-ticket)

#### Discussion avec le PO

Au cours des réunions inter-sprints, planifier les tâches avec le PO et éventuellement demander des éclaircissements sur les tickets posant problème à l'équipe.
