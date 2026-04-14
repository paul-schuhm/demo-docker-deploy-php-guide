# docker-php-sample

A simple PHP web application example for [Docker's PHP Language Guide](https://docs.docker.com/language/php/).

## Prérequis

- Docker
- Disposer d'un compte sur Docker Inc (Hub, Scout);
- Disposer d'un compte gratuit sur Sonarcloud (SonarQube);
- [Suivre le guide initial](https://docs.docker.com/language/php/) ;

## Variations apportées

- Ajout d'un script de pre-commit (pré-CI, en local : tests et lint). Pour l'installer : `cp pre-commit .git/hooks`
- Ajout d'un step analyse par SonarQube (SonarCloud). Pour cela :
  - Ajouter un secret `SONAR_TOKEN` Github Actions sur le dépôt Github ;
  - Créer un fichier `sonar-project.properties` à la racine du dépôt avec les données sur votre projet SonarCloud :

~~~
sonar.organization=
sonar.projectKey=
sonar.sources=
~~~

- Ajout d'un step analyse de l'image par Docker Scout;
- CD : déploiement de l'artefact

## Points à améliorer

- Refactoriser le fichier de CI en plusieurs fichiers ;
- Test runner container pour lancer une série de tests d'intégration (black box) de l'image de prod (plutot que de le faire depuis les steps de la CI directement comme ici)

## Liens utiles

- [Events that trigger workflows](https://docs.github.com/en/actions/reference/workflows-and-actions/events-that-trigger-workflows), documentation de Github Actions
- [Scan your code with SonarQube](https://github.com/marketplace/actions/official-sonarqube-scan), documentation officielle de Github Actions
- [Adding analysis to GitHub Actions workflow](https://docs.sonarsource.com/sonarqube-server/devops-platform-integration/github-integration/adding-analysis-to-github-actions-workflow)
- [act](https://github.com/nektos/act), test les Github Action localement avant de les executer sur Github
- [actionlint](https://github.com/rhysd/actionlint), analyseur statique des fichiers de Github Actions
