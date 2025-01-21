S'enregistrer sur Gitlab ([http://gitlab-ing2.ensg.eu/](http://gitlab-ing2.ensg.eu/))

Sur son poste, réinitaliser le proxy pour git :
```bash
git config --global http.proxy ""
```

### Actions d'évolution

Faire ses développements d'évolution sur une branche `feature/[nom de l'évolution]`, tester sur son ordinateur. Une fois finalisée, faire une demande de fusion (ou merge request `MR`) sur `main` via l'interface Gitlab, et assigner le ticket correspondant à l'évolution au chef d'équipe MOE. [:material-help:aide MR](gitlab/mr.md#creer-une-merge-request) [:material-help:aide ticket](gitlab/issues.md#changer-lassignation-dun-ticket)

### Actions de correction

Faire ses développements d'évolution sur une branche `fix/[nom de la correction]`, tester sur son ordinateur. Une fois finalisée, faire une demande de fusion (ou merge request `MR`) sur `main` via l'interface Gitlab, et assigner le ticket correspondant à l'évolution au chef d'équipe MOE. [:material-help:aide MR](gitlab/mr.md#creer-une-merge-request) [:material-help:aide ticket](gitlab/issues.md#changer-lassignation-dun-ticket)
