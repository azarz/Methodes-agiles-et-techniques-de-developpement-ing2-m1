S'enregistrer sur Gitlab ([http://gitlab-ing2.ensg.eu/](http://gitlab-ing2.ensg.eu/))

### Actions initiales

- Créer le dépôt du projet. [:material-help:aide](gitlab/project.md#creation-du-projet)
- Ajouter tous les développeurs, le devops et le product owner dans le projet (avec les rôles adéquats) [:material-help:aide](gitlab/project.md#ajout-de-membres)
- Mise en place du board Kanban sur le projet (Projet > Issues > Board) : créer un board avec comme colonnes : à faire, en cours, à tester, terminé

Sur son poste, réinitaliser le proxy pour git :
```bash
git config --global http.proxy ""
```

### Actions récurrentes

#### Validation des merge requests

Lorque les développeurs soumettent une merge request (MR) sur `main`, valider le fonctionnement sur son ordinateur et réaliser la fusion sur `main`. Supprimer la branche qui a été fusionnée.
[:material-help:aide](gitlab/mr.md#accepter-une-merge-request)

#### Création de versions de production

Sur demande du Product Owner, tagger la version déployée de préproduction (dernier commit sur `main`) `vX.Y.Z` (ex: `v0.0.1`). Attention à bien tagguer la version demandée par le PO (des MR ont pu être fusionnées sur main entre temps...). [:material-help:aide](gitlab/tag.md#creation-de-tag)

#### Attribution des tickets

* Attribuer les tickets créés par les utilisateurs aux développeurs ciblés pour le développement. [:material-help:aide](gitlab/issues.md#changer-lassignation-dun-ticket)
* Inspecter et mettre à jour le board (Kanban) du projet -> Projet > Issues > Board

##### Cycle d'assignation d'un ticket :

- L'utilisateur crée le ticket et l'assigne au PO
- Le PO assigne le ticket au chef d'équipe MOE
- Le chef d'équipe MOE assigne le ticket au membre d'équipe ciblé pour le développement
- Une fois le dévelopement fait et la MR faite, le membre d'équipe assigne le ticket au chef d'équipe.
- Une fois la MR mergée, le chef d'équipe assigne au PO pour vérification du traitement du ticket.
- Le PO assigne éventuellement au client qui a créé le ticket pour qu'il fasse lui-même la vérification.

#### Discussion avec le PO

Au cours des réunions inter-sprints, planifier les tâches avec le PO et éventuellement demander des éclaircissements sur les tickets posant problème à l'équipe.
