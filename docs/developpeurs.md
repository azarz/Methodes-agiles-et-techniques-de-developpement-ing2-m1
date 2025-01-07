# Développeurs et chef d'équipe

S'enregistrer sur Gitlab (http://gitlab-ing2.ensg.eu/)

## Chef d'équipe

### Actions initiales

- Créer le dépôt du projet.
- Ajouter tous les développeurs, le devops et le product owner dans le projet (avec les rôles adéquats)

### Actions récurrentes

#### Validation des merge requests

Lorque les développeurs soumettent une merge request (MR) sur `main`, valider le fonctionnement sur son ordinateur et réaliser la fusion sur `main`, en utilisant la méthode "Squash". Supprimer la branche qui a été fusionnée.

#### Évolution

Sur demande du Product Owner, tagger la version déployée de préproduction (dernier commit sur `main`) `vX.Y.Z` (ex: `v0.0.1`). Attention à bien tagguer la version demandée par le PO (des MR ont pu être fusionnées sur main entre temps...).

#### Chef d'équipe

Attribuer les tickets créés par les utilisateurs aux développeurs ciblés pour le développement.

#### Discussion avec le PO

Au cours des réunions inter-sprints, planifier les tâches avec le PO et éventuellement demander des éclaircissements sur les tickets posant problème à l'équipe.

## Développeurs

### Actions d'évolution

Faire ses développements d'évolution sur une branche `feature/[nom de l'évolution]`, tester sur son ordinateur. Une fois finalisée, faire une demande de fusion (ou merge request `MR`) sur `main` via l'interface Gitlab.

### Actions de correction

Faire ses développements d'évolution sur une branche `fix/[nom de la correction]`, tester sur son ordinateur. Une fois finalisée, faire une demande de fusion (ou merge request `MR`) sur `main` via l'interface Gitlab.
