# Keycloak MySQL+OpenShift

Extends the keycloak-mysql docker image to use OpenShift

## docker-compose Usage

### Build Docker Image

   docker-compose build

### Start Mysql

   docker-compose up -d mysql

### Start Keycloak

   docker-compose up

## Log into keycloak

   http://localhost:8080 (user: root, password: password)

## Docker Usage

### Start a MySQL instance

First start a MySQL instance using the MySQL docker image:

    docker run --name mysql -e MYSQL_DATABASE=keycloak -e MYSQL_USER=keycloak -e MYSQL_PASSWORD=password -e MYSQL_ROOT_PASSWORD=root_password -d mysql

### Start a Keycloak instance

Start a Keycloak instance and connect to the MySQL instance:

    docker run --name keycloak --link mysql:mysql jboss/keycloak-mysql

### Environment variables

When starting the Keycloak instance you can pass a number of environment variables to configure how it connects to MySQL. For example:

    docker run --name keycloak --link mysql:mysql -e MYSQL_DATABASE=keycloak -e MYSQL_USER=keycloak -e MYSQL_PASSWORD=password jboss/keycloak-mysql

#### MYSQL_DATABASE

Specify name of MySQL database (optional, default is `keycloak`).

#### MYSQL_USER

Specify user for MySQL database (optional, default is `keycloak`).

#### MYSQL_PASSWORD

Specify password for MySQL database (optional, default is `keycloak`).
