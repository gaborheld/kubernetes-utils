# kubernetes-utils

Example configuration files for kubernetes deployment.

### Features

* PostgreSQL as a StatefulSet
* volume for data
* headless service
* setup of multiple databases at startup
* dedicated users and passwords for each databases

### Database Configuration

Add the following values to the `app-postgresql` ConfigMap. These will be added as environment variables to the pod and used by the setup script to create the databases.

| env variable name | usage | example |
|---|---|---|
| POSTGRES_USER | superuser name (standard configuration) | POSTGRES_USER=admin |
| POSTGRES_PASSWORD | superuser password (standard configuration) | POSTGRES_PASSWORD=adminpassword |
| POSTGRES_DATABASES | database reference names, comma-separated | POSTGRES_DATABASES=cms,keycloak,audit |
| POSTGRES_DB_*refname* | database name | POSTGRES_DB_CMS=app_cms |
| POSTGRES_USER_*refname* | user name | POSTGRES_DB_CMS=cms_user |
| POSTGRES_PASSWORD_*refname* | user password (should be added as a Secret) | POSTGRES_PASSWORD_CMS=mypassword |

You can define as many databases as you want.

Credits: https://github.com/mrts/docker-postgresql-multiple-databases

