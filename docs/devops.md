S'enregistrer sur Gitlab ([http://gitlab-ing2.ensg.eu/](http://gitlab-ing2.ensg.eu/))

Sur son poste, réinitaliser le proxy pour git :
```bash
git config --global http.proxy ""
```

## Étape 1 : initialisation

- Cloner le projet
- Créer une nouvelle branche `feature/continuous-integration`
- Créer à la racine du projet un fichier `.gitlab-ci.yml`

## Étape 2 : test de la CI

Dans le fichier `.gitlab-ci.yml`, créer un job test :
```yaml
test-ci:       # nom du job d'intégration continue
  when: manual # quand le job doit-il être exectué ? ici : manuellement
  script:      # ensemble de commandes exécutées par le job
    - echo "Bonjour tout le monde !" # affiche "Bonjour tout le monde !"
```
Faire un commit intégrant ces changements sur la branche `feature/continuous-integration`, puis créer une Merge Request (MR) sur `main` via l'interface Gitlab.

Une fois la MR mergée, tester le fonctionnement du job dans l'interface `CI/CD` en le lançant manuellement. [:material-help:aide](gitlab/ci.md#acceder-a-linterface-dintegration-continue)

## Étape 3 : intégration continue automatique de main sur la préprod

Dans le fichier `.gitlab-ci.yml`, ajouter un job de déploiement en préprod automatique pour chaque commit sur `main` :

**Pensez à remplacer ici "VOTRE_PROJET" par le nom voulu du site. L'url sera en préproduction http://preprod-ing2.ensg.eu/VOTRE_PROJET**
```yaml
deploiement_preprod: # nom du job d'intégration continue
  script: # ensemble de commandes exécutées par le job
    - sshpass -p "ci-agent" ssh ci-agent@172.31.42.89 "mkdir -p /var/www/html/VOTRE_PROJET" # crée le dossier s'il n'existe pas sur la machine de préprod
    - sshpass -p "ci-agent" scp -r ./* ci-agent@172.31.42.89:/var/www/html/VOTRE_PROJET     # copie le contenu du dépôt git dans le dossier créé
  only:
    - main # le job est exécuté uniquement à chaque commit sur la branche main
```
Faire un commit intégrant ces changements sur la branche `feature/continuous-integration`, puis créer une Merge Request (MR) sur `main` via l'interface Gitlab. [:material-help:aide](gitlab/mr.md#creer-une-merge-request)

Une fois la MR mergée, tester le fonctionnement du job dans l'interface `CI/CD` au prochain merge de MR des développeurs sur `main`. [:material-help:aide](gitlab/ci.md#acceder-a-linterface-dintegration-continue)

## Étape 4 : intégration manuelle de main sur la prod

Dans le fichier `.gitlab-ci.yml`, ajouter un job de déploiement en prod manuel :

**Pensez à remplacer ici "VOTRE_PROJET" par le nom voulu du site. L'url sera, en préproduction http://production-ing2.ensg.eu/VOTRE_SITE**
```yaml
deploiement_prod:
  when: manual
  script:
    - sshpass -p "ci-agent" ssh ci-agent@172.31.42.86 "mkdir -p /var/www/html/VOTRE_PROJET"
    - sshpass -p "ci-agent" scp -r ./* ci-agent@172.31.42.86:/var/www/html/VOTRE_PROJET
```
Faire un commit intégrant ces changements sur la branche `feature/continuous-integration`, puis créer une Merge Request (MR) sur `main` via l'interface Gitlab. [:material-help:aide](gitlab/mr.md#creer-une-merge-request)

Une fois la MR mergée, suite à la demande par le ou la Product Owner (PO), lancer un déploiement en production manuel. En tester le bon fonctionnement conjointement avec le ou la chef·fe d'équipe MOE. [:material-help:aide](gitlab/ci.md#acceder-a-linterface-dintegration-continue)

## Étape 5 : intégration automatique de main sur la prod

Dans le fichier `.gitlab-ci.yml`, modifer le job de déploiement en prod pour le rendre automatique et basé sur les tags :

**Pensez à remplacer ici "VOTRE_PROJET" par le nom voulu du site. L'url sera en production http://production-ing2.ensg.eu/VOTRE_PROJET**
```yaml
deploiement_prod:
  script:
    - sshpass -p "ci-agent" ssh ci-agent@172.31.42.86 "mkdir -p /var/www/html/VOTRE_PROJET"
    - sshpass -p "ci-agent" scp -r ./* ci-agent@172.31.42.86:/var/www/html/VOTRE_PROJET
  only:
    variables:
      - $CI_COMMIT_TAG =~ /^v\d+.\d+.\d+$/ # le job est exécuté uniquement à chaque commit dont le tag correspond à un nom du type v(nombre).(nombre).(nombre)
```

Faire un commit intégrant ces changements sur la branche `feature/continuous-integration`, puis créer une Merge Request (MR) sur `main` via l'interface Gitlab. [:material-help:aide](gitlab/mr.md#creer-une-merge-request)

Une fois la MR mergée, suite à la demande par le ou la Product Owner (PO), vérifier que le job s'exécute bien à la création du tag par le ou la chef·fe d'équipe MOE. [:material-help:aide](gitlab/ci.md#acceder-a-linterface-dintegration-continue)
